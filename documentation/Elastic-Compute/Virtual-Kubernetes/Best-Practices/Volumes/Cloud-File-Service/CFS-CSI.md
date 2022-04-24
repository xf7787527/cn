# 通过CSI插件和静态PV的方式使用京东云文件服务

京东云Kubernetes集群1.14和1.16版本都使用CSI作为默认的存储插件，CSI详细介绍请参见[CSI](https://kubernetes.io/blog/2019/01/15/container-storage-interface-ga/)。PV是Kubernetes集群中的资源，是Volume类的卷插件，用于描述持久化存储数据卷，具有独立于使用PV的Pod的生命周期。[京东云文件服务](https://docs.jdcloud.com/cn/cloud-file-service/product-overview)支持NFS协议，因此可以在Kubernetes集群中使用nfs类型的PV定义。

PV支持两种配置方式：

* 静态：由集群管理员创建，具有capacity、accessMode、类型等实际存储细节，可直接被使用；

* 动态：当静态创建的PV都不匹配用户定义的PersistentVolumeClaim 时，集群会尝试动态地为 PVC 创建Volume。Volume的配置基于 StorageClasses定义；PVC将根据storageClassName字段发现PV。

本文将提供在Kubernetes集群中安装NFS CSI插件并用静态配置PV的方式使用京东云文件服务的操作步骤和应用示例。

**专有名词**：

* PV：Persistent Volume，描述持久化存储数据卷；

* PVC：Persistent Volume Claim，描述持久化存储卷请求声明；

* SC: Storage Class, 提供描述存储“class（类）”的方法，为PVC提供动态创建/绑定PV的存储配置；与PVC具有相同StorageClassName的PV才可以被绑定到PVC；
  
## 一、创建CFS文件存储

1. 您需要首先创建一个[CFS文件存储](https://docs.jdcloud.com/cn/cloud-file-service/creating-file-system)，建议您在Kubernetes集群的Node子网中创建文件存储；

2. 文件存储支持通过挂载目标的IP地址挂载文件存储，您可以在文件存储详情页查询挂载目标的IP地址，详情参考[文件存储信息](https://docs.jdcloud.com/cn/cloud-file-service/file-system-detail)。

## 二、连接到集群

 Kubernetes 命令行客户端 kubectl可以让您从客户端计算机连接到 Kubernetes 集群，实现应用部署。详情参考使用Kubectl客户端[连接到Kubernetes集群](https://docs.jdcloud.com/cn/jcs-for-kubernetes/connect-to-cluster)。

## 三、在集群中使用CFS文件存储定义NFS类型的PV


1.安装nfs csi驱动
csi-attacher-rbac.yaml
```
# This YAML file contains RBAC API objects that are necessary to run external
# CSI attacher for nfs flex adapter

apiVersion: v1
kind: ServiceAccount
metadata:
  name: csi-attacher

---
kind: ClusterRole
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: external-attacher-runner
rules:
  - apiGroups: [""]
    resources: ["persistentvolumes"]
    verbs: ["get", "list", "watch", "update"]
  - apiGroups: [""]
    resources: ["nodes"]
    verbs: ["get", "list", "watch"]
  - apiGroups: ["storage.k8s.io"]
    resources: ["volumeattachments"]
    verbs: ["get", "list", "watch", "update"]

---
kind: ClusterRoleBinding
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: csi-attacher-role
subjects:
  - kind: ServiceAccount
    name: csi-attacher
    namespace: default
roleRef:
  kind: ClusterRole
  name: external-attacher-runner
  apiGroup: rbac.authorization.k8s.io
```
b.csi-nodeplugin-rbac.yaml
```
# This YAML defines all API objects to create RBAC roles for CSI node plugin
apiVersion: v1
kind: ServiceAccount
metadata:
  name: csi-nodeplugin

---
kind: ClusterRole
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: csi-nodeplugin
rules:
  - apiGroups: [""]
    resources: ["persistentvolumes"]
    verbs: ["get", "list", "watch", "update"]
  - apiGroups: [""]
    resources: ["nodes"]
    verbs: ["get", "list", "watch", "update"]
  - apiGroups: ["storage.k8s.io"]
    resources: ["volumeattachments"]
    verbs: ["get", "list", "watch", "update"]
---
kind: ClusterRoleBinding
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: csi-nodeplugin
subjects:
  - kind: ServiceAccount
    name: csi-nodeplugin
    namespace: default
roleRef:
  kind: ClusterRole
  name: csi-nodeplugin
  apiGroup: rbac.authorization.k8s.io
```
c.csi-attacher-nfsplugin.yaml
```
# This YAML file contains attacher & csi driver API objects that are necessary
# to run external CSI attacher for nfs

kind: Service
apiVersion: v1
metadata:
  name: csi-attacher-nfsplugin
  labels:
    app: csi-attacher-nfsplugin
spec:
  selector:
    app: csi-attacher-nfsplugin
  ports:
    - name: dummy
      port: 12345

---
kind: StatefulSet
apiVersion: apps/v1beta1
metadata:
  name: csi-attacher-nfsplugin
spec:
  serviceName: "csi-attacher"
  replicas: 1
  template:
    metadata:
      labels:
        app: csi-attacher-nfsplugin
    spec:
      serviceAccount: csi-attacher
      containers:
        - name: csi-attacher
          image: quay.io/k8scsi/csi-attacher:v1.0.1
          args:
            - "--v=5"
            - "--csi-address=$(ADDRESS)"
          env:
            - name: ADDRESS
              value: /csi/csi.sock
          imagePullPolicy: "IfNotPresent"
          volumeMounts:
            - name: socket-dir
              mountPath: /csi

        - name: nfs
          image: quay.io/k8scsi/nfsplugin:canary
          args :
            - "--nodeid=$(NODE_ID)"
            - "--endpoint=$(CSI_ENDPOINT)"
          env:
            - name: NODE_ID
              valueFrom:
                fieldRef:
                  fieldPath: spec.nodeName
            - name: CSI_ENDPOINT
              value: unix://plugin/csi.sock
          imagePullPolicy: "IfNotPresent"
          volumeMounts:
            - name: socket-dir
              mountPath: /plugin
      volumes:
        - name: socket-dir
          emptyDir:
```

d.csi-nodeplugin-nfsplugin.yaml
```
# This YAML file contains driver-registrar & csi driver nodeplugin API objects
# that are necessary to run CSI nodeplugin for nfs
kind: DaemonSet
apiVersion: apps/v1beta2
metadata:
  name: csi-nodeplugin-nfsplugin
spec:
  selector:
    matchLabels:
      app: csi-nodeplugin-nfsplugin
  template:
    metadata:
      labels:
        app: csi-nodeplugin-nfsplugin
    spec:
      serviceAccount: csi-nodeplugin
      hostNetwork: true
      containers:
        - name: node-driver-registrar
          image: quay.io/k8scsi/csi-node-driver-registrar:v1.0.2
          lifecycle:
            preStop:
              exec:
                command: ["/bin/sh", "-c", "rm -rf /registration/csi-nfsplugin /registration/csi-nfsplugin-reg.sock"]
          args:
            - --v=5
            - --csi-address=/plugin/csi.sock
            - --kubelet-registration-path=/var/lib/kubelet/plugins/csi-nfsplugin/csi.sock
          env:
            - name: KUBE_NODE_NAME
              valueFrom:
                fieldRef:
                  fieldPath: spec.nodeName
          volumeMounts:
            - name: plugin-dir
              mountPath: /plugin
            - name: registration-dir
              mountPath: /registration
        - name: nfs
          securityContext:
            privileged: true
            capabilities:
              add: ["SYS_ADMIN"]
            allowPrivilegeEscalation: true
          image: quay.io/k8scsi/nfsplugin:canary
          args :
            - "--nodeid=$(NODE_ID)"
            - "--endpoint=$(CSI_ENDPOINT)"
          env:
            - name: NODE_ID
              valueFrom:
                fieldRef:
                  fieldPath: spec.nodeName
            - name: CSI_ENDPOINT
              value: unix://plugin/csi.sock
          imagePullPolicy: "IfNotPresent"
          volumeMounts:
            - name: plugin-dir
              mountPath: /plugin
            - name: pods-mount-dir
              mountPath: /var/lib/kubelet/pods
              mountPropagation: "Bidirectional"
      volumes:
        - name: plugin-dir
          hostPath:
            path: /var/lib/kubelet/plugins/csi-nfsplugin
            type: DirectoryOrCreate
        - name: pods-mount-dir
          hostPath:
            path: /var/lib/kubelet/pods
            type: Directory
        - hostPath:
            path: /var/lib/kubelet/plugins_registry
            type: Directory
          name: registration-dir
```


2. 新建一个NFS类型的PV，PV YAML文件说明如下：

```
apiVersion: v1
kind: PersistentVolume
metadata:
  name: data-nfsplugin
  labels:
    name: data-nfsplugin
spec:
  accessModes:
  - ReadWriteMany
  capacity:
    storage: 10Gi
  storageClassName: ""    #storageClassName值为空，必填项
  csi:
    driver: csi-nfsplugin
    volumeHandle: data-id
    volumeAttributes: 
      server: 10.0.0.5    #请使用文件存储的挂载目标IP地址替换
      share: /cfs         #请使用挂载目标支持的目录替换，默认挂载到/cfs目录

```   


3. 定义一个PVC，将上一步创建的PV绑定到该PVC，PVC YAML文件说明如下：

```
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: data-nfsplugin
spec:
  accessModes:
  - ReadWriteMany
  storageClassName: ""     #storageClassName值为空，必填项
  resources:
    requests:
      storage: 10Gi
  selector:
    matchExpressions:
    - key: name
      operator: In
      values: ["data-nfsplugin"]

```


4. 验证PVC与PV的绑定状态：

```
kubectl get pvc
NAME                        STATUS        VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   AGE
data-nfsplugin              Bound         data-nfsplugin                             10Gi       RWX                           8m2s

```

5. 创建一个Pod，将Bound状态的PVC挂载到Pod。Pod Yaml文件说明如下：

```
apiVersion: v1
kind: Pod
metadata:
  name: nginx1 
spec:
  containers:
  - image: maersk/nginx
    imagePullPolicy: Always
    name: nginx
    ports:
    - containerPort: 80
      protocol: TCP
    volumeMounts:
      - mountPath: /var/www
        name: data-nfsplugin 
  volumes:
  - name: data-nfsplugin
    persistentVolumeClaim:
      claimName: data-nfsplugin

```  


6. 访问nfs文件

```
kubectl exec -it nginx1 /bin/sh
cd /var/www

```

