
# 部署StorageClass

StorageClass为Kubernetes集群提供了描述存储类别（class）的方法，包含provisioner、parameters、volumeBindingMode 和 reclaimPolicy等字段，当 class 需要动态分配持久化存储时会使用到。  
京东云为Kubernetes集群提供了CSI插件，将provisioner定义为京东云CSI插件，可以使用京东云云硬盘为Kubernetes集群提供持久化存储。目前，在Kubernetes集群中，默认提供三种storageclass:

```
kubectl get storageclass

NAME                PROVISIONER                 AGE
default (default)   zbs.csi.jdcloud.com         39d
jdcloud-hdd         zbs.csi.jdcloud.com         39d
jdcloud-ssd         zbs.csi.jdcloud.com         39d

```
您也可以创建自定义的Storageclass：
```
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: csi-ssdio
parameters:
  fstype: ext4
  type: ssd.io1
provisioner: zbs.csi.jdcloud.com
reclaimPolicy: Delete
volumeBindingMode: WaitForFirstConsumer
```
**参数说明：**  
1、provisioner：zbs.csi.jdcloud.com，且不可修改，标识使用京东云云硬盘Provisioner插件创建。

2、type：可以选择以下3种云硬盘类型

|StorageClass type | 云硬盘类型   |容量范围  |步长|
| ------ | ------ | ------ |------ |
|hdd.std1	|容量型hdd | [20-16000]GiB  |10GiB|
|ssd.gp1	|通用型ssd | [20-16000]GiB  |10GiB|
|ssd.io1	|性能型ssd | [20-16000]GiB  |10GiB|

2、reclaimPolicy：由 storage class 动态创建的 Persistent Volume 会在的 reclaimPolicy 字段中指定回收策略，可以是 Delete 或者 Retain。如果 storageClass 对象被创建时没有指定 reclaimPolicy ，它将默认为 Delete。

3、parameters  
  - type：设置参数值为hdd.std1 ssd.gp1或ssd.io1，分别对应京东云的容量型hdd，通用型ssd和性能型ssd云盘；
  - fstype：设置文件系统类型，可选参数值为xfs和ext4，如未指定fstype，将使用ext4作为默认的文件系统类型；例如：fstype=ext4；
  - volumeBindingMode：可选参数包括WaitForFirstConsumer和Immediate，默认值为Immediate。


4、您可在创建持久化存储声明（ Persistent Volume Claim）时，通过storageClassName字段关联某一指定的storageclass资源，根据storageClass定义动态创建并绑定一个持久化存储（Persistent Volume）或直接绑定具有相同storageClassName且参数符合要求的持久化存储（Persistent Volume）；更多详情参考[部署CSI持久化存储](./Deploy-PV-New.md)  ；

5、更多storageClass参数说明，参考[Kubernetes 参数说明文档](https://kubernetes.io/docs/concepts/storage/storage-classes/)。 
