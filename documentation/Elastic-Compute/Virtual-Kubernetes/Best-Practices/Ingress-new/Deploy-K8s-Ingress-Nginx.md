
# Kubernetes ingress-nginx部署及使用示例
Ingress 是从Kubernetes集群外部访问集群内部服务的入口，概念示意可参考下方说明。你可以在Ingress配置中提供外部可访问的URL、负载均衡、SSL、基于名称的虚拟主机等。用户通过POST Ingress资源到API server的方式来请求ingress。 

  ```
   internet
        |
   [ Ingress ]
   --|-----|--
   [ Services ]
  ```
Ingress controller负责实现Ingress。Ingress controller在Kubernetes集群中默认不会自动启用，您可以在一个pod中部署任意类型的自定义Ingress Controller。

Kubernetes ingress-nginx是社区提供的基于nginx开发的ingress controller。本文将以此为例，说明如何通过ingress访问dashboard及其他服务。更多详细配置请参考[Kubernetes ingress-nginx](https://github.com/kubernetes/ingress-nginx)。

一、安装Kubernetes ingress-nginx
1. 从github安装部署文件：

```

kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/nginx-0.30.0/deploy/static/mandatory.yaml
```

    **说明**：本文所有例子均在1.16版本的集群上测试运行，如集群版本不同，个别配置项可能需要微调。
2. 安装fix.yaml,避免controller不断报错；

```
apiVersion: v1
kind: Service
metadata:
  name: ingress-nginx
  namespace: ingress-nginx
spec:
  type: ClusterIP
  ports:
  - name: http
    port: 80
    targetPort: 80
    protocol: TCP
  - name: https
    port: 443
    targetPort: 443
    protocol: TCP
  selector:
    app: ingress-nginx
```

3. 执行如下命令，确定部署ingress-nginx controller的Deployment运行正常：

```

kubectl get deployments  -n ingress-nginx

NAME                      DESIRED   CURRENT   UP-TO-DATE   AVAILABLE   AGE
nginx-ingress-controller   1         1         1            1           24d
```
4. 通过Service LoadBalancer的方式将ingress controller暴露到公网：

```

apiVersion: v1
kind: Service
metadata:
  labels:
    app.kubernetes.io/name: ingress-nginx
    app.kubernetes.io/part-of: ingress-nginx
  name: nginx-ingress-controller
  namespace: ingress-nginx
spec:
  externalTrafficPolicy: Cluster
  ports:
  - port: 80
    protocol: TCP
    targetPort: 80
    name: http
  - port: 443
    protocol: TCP
    targetPort: 443
    name: https
  selector:
    app.kubernetes.io/name: ingress-nginx
    app.kubernetes.io/part-of: ingress-nginx
  type: LoadBalancer
```


```

kubectl create -f X.yaml        # 请使用对应的Yaml文件名称替换X.yaml
```
5. 等待一段时间，确定Service已经配置完成，并获取Service上配置的External IP字段

```

kubectl get svc -n nginx-ingress

NAME                        TYPE           CLUSTER-IP    EXTERNAL-IP    PORT(S)                      AGE
nginx-ingress-controller   LoadBalancer   10.X.XX.231   114.67.127.227   80:30494/TCP,443:30467/TCP   24d

说明：Service的External IP将作为nginx-ingress controller的VIP，为集群中使用ingress controller的Ingress提供公网访问入口
```

二、通过ingress访问Kubernetes Dashboard
1. 确认Kubernetes Dashboard已经安装,如果未安装参考[访问Dashboard](../Connect-Dashboard.md)
```
kubectl get service -n kube-system

NAME                   TYPE           CLUSTER-IP    EXTERNAL-IP                  PORT(S)         AGE
kubernetes-dashboard   ClusterIP      10.0.123.87    <none>                      443:31382/TCP   5d23h
```
   
2. 在kube-system名字空间下配置Dashboard所需的ingress规则
```
apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  annotations:
    nginx.ingress.kubernetes.io/backend-protocol: HTTPS
  name: dashboard
  namespace: kube-system
spec:
  rules:
  - host: kubernetes-dashboard.jdcloud
    http:
      paths:
      - backend:
          serviceName: kubernetes-dashboard
          servicePort: 443
        path: /
```
    **说明**：示例中的host kubernetes-dashboard.jdcloud 需要替换成用户自己host，此示例中host对应解析的IP为第一章节第5步中，service nginx-ingress-controller暴露出来的公网IP 114.67.127.227。

3. 访问dashboard
   在浏览器打开 https://kubernetes-dashboard.jdcloud 
   
三、通过ingress访问nginx
1. 创建一个测试nginx pod
```
kubectl create namespace test
kubectl run test-nginx --image=nginx --restart=Never --port=80 -n test
kubectl expose pod -n test test-nginx --port=80 --target-port=80 --type=ClusterIP
```
2. 创建对应的ingress规则
```
apiVersion: networking.k8s.io/v1beta1
kind: Ingress
metadata:
 name: ingress-test
 namespace: test
 annotations:
   kubernetes.io/ingress.class: "nginx"
spec:
 rules:
 - host: k8s-ingress-nginx-controller-test.jdcloud
   http:
     paths:
     - path: /
       backend:
         serviceName: test-nginx
         servicePort: 80
```
    **说明**：示例中的host k8s-ingress-nginx-controller-test.jdcloud 需要替换成用户自己host，此示例中host对应解析的IP为第一章节第5步中，service nginx-ingress-controller暴露出来的公网IP 114.67.127.227。
    
3. 测试验证
在浏览器中打开 http://k8s-ingress-nginx-controller-test.jdcloud  或 https://k8s-ingress-nginx-controller-test.jdcloud


 
