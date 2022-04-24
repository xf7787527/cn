
# 部署Service（新版本）
从1.14-jcs.1版本开始，Service支持新版本LoadBalancer，新版本中不仅支持应用负载均衡(alb),网络负载均衡(nlb)以及分布式网络负载均衡(DNLB)，还支持丰富的配置项，同时还可以复用已创建的LoadBalancer，为用户提供了极大地灵活性。  

**说明** 用户仍然可以使用老的service配置文件，新版本集群可以兼容。另外文章中尽量举例详细说明参数的配置，实际使用时用户只要填一个必填项指定lb类型，其他annotation参数都不需要指定即可轻松使用service服务


**Kubernetes Service**   
- Kubernetes Service定义了这样一种抽象：一个 Pod 的逻辑分组，一种可以访问它们的策略-通常称为微服务。这一组 Pod 能够被 Service 访问到，通常是通过 Label Selector（查看下面了解，为什么可能需要没有 selector 的 Service）实现的。一个 Service 在 Kubernetes 中是一个REST对象，和Pod类似.像所有的 REST 对象一样， Service 定义可以基于 POST 方式，请求 apiserver 创建新的实例。  

**京东云Kubernetes集成负载均衡服务，支持创建LoadBalance类型的Service，为应用提供安全、可靠的网络。**  
- 创建的负载均衡会占用本地域的应用负载均衡配额，需要保证有足够配额。 
- 一个service port 对应一组负载均衡监听器和后端服务器；
- 如多组service port关联相同的nodeport，则监听器将关联到相同的后端服务；
- 如需基于IPv6地址提供服务，请在集群创建时选择“自定义模式”，创建IPv4/IPv6双栈VPC和子网，并将LoadBalance放置在支持IPv6的双栈子网内。

**service.beta.kubernetes.io/jdcloud-load-balancer-spec** 
- 此annotation可以指定，也可以不指定，如果不指定，行为与原有的service的插件一致，默认创建ALB实例
- 用于定义JD LB的各项参数，支持变更
- 注：listener与port按顺序一一对应

```
version: "v1"                                            # 【版本号】只支持"v1"
loadBalancerId: "alb-xxxxxx"                             # 重用已有的LB，此参数指定以后，只有listeners,nodeSelector的设置会生效,其他的设置会被忽略，如果listener端口重复会报错
loadBalancerType: "alb(default)/nlb/dnlb"                # 【必填项】要创建的JD LB的类型,创建后不支持变更
securityGroupIds: ["sg-xxxxxxxx1","sg-xxxxxxxx2"]        # 可选项，如不指定则绑定默认安全组，变更会触发SG的绑定解绑，最后一个SG不能解绑
internal: true/false(default)                            # true表示LB实例不会绑定公网IP，只内部使用；false表示为外部服务，会绑定公网IP。修改可能会触发IP的创建，绑定或者解绑，不会自动删除
elasticIp:                                               # 默认创建按配置收费
  elasticIpId: "fip-xxxxxxxxxxx"                         # 创建时不为空则不会创建新的FIP，更换LB绑定的公网IP，如果IP已经被其他资源绑定则报错
  bandwidthMbps: 100                                     # 默认5M带宽，变更会触发扩容缩容，但是包年包月的IP不支持此参数
  provider: "bgp/no_bgp"                                 # 公网IP的类型
  reclaimPolicy: "delete/retain(default)"                # LB的公网IP的回收策略，delete：跟随LB一起删除（包年包月的IP不支持），retain：LB删除时保留IP
listeners:                                               # 每个port对应的LB的listener的配置,数量必须和ports的数量一致 
  - protocal: "Http"                                     # 修改可能触发删除重建，导致服务短暂中断，listener的协议,alb:Tcp,Http,Https,Tls;nlb:Tcp;dnlb:Tcp
    connectionIdleTimeSeconds: 1800                      # 连接超时时间，alb/nlb有效
    backend:                                             # 关于JD LB的backend的通用配置
      proxyProtocol: false                               # 【alb Tcp协议】获取真实ip, 取值为False(不获取)或者True(获取,支持Proxy Protocol v1版本)，默认为False(Optional)
      connectionDrainingSeconds: 300                     # 【nlb】移除target前，连接的最大保持时间，默认300s，取值范围[0-3600] (Optional)
      sessionStickyTimeout: 300                          # 【nlb】会话保持超时时间，sessionStickiness开启时生效，默认300s, 取值范围[1-3600] (Optional)
      sessionStickiness: false                           # 后端服务的后端保持, 取值为false(不开启)或者true(开启)，默认为false【alb Http协议，RoundRobin算法】支持基于cookie的会话保持【nlb】支持基于报文源目的IP的会话保持 (Optional)
      algorithm: "IpHash/LeastConn/RoundRobin(default)"  # 调度算法, 取值范围为[IpHash, RoundRobin,和LeastConn]（取值范围的含义分别为：源Ip hash，加权轮询和加权最小连接），默认为RoundRobin（加权轮询） (Optional)，nlb：；dnlb：；alb
      httpCookieExpireSeconds: 0                         # 【alb Http协议】cookie的过期时间,sessionStickiness开启时生效，取值范围为[0-86400], 默认为0（表示cookie与浏览器同生命周期） (Optional)
      httpForwardedProtocol: false                       # 【alb Http协议】获取负载均衡的协议, 取值为False(不获取)或True(获取), 默认为False (Optional)
      httpForwardedPort: false                           # 【alb Http协议】获取负载均衡的端口, 取值为False(不获取)或True(获取), 默认为False (Optional) 
      httpForwardedHost: false                           # 【alb Http协议】获取负载均衡的host信息, 取值为False(不获取)或True(获取), 默认为False (Optional)
      httpForwardedVip: false                            # 【alb Http协议】获取负载均衡的vip, 取值为False(不获取)或True(获取), 默认为False (Optional)
    healthCheckSpec:                                     # 健康检查的配置 
      protocol: "http"                                   # 健康检查协议, 【alb、nlb】取值为Http, Tcp【dnlb】取值为Tcp
      port: 80                                           # 检查端口, 取值范围为[0,65535], 默认为0，默认端口为每个后端实例接收负载均衡流量的端口 (Optional)
      healthyThresholdCount: 3                           # 健康阀值，取值范围为[1,5]，默认为3 (Optional)
      unhealthyThresholdCount: 3                         # 不健康阀值，取值范围为[1,5], 默认为3 (Optional)
      checkTimeoutSeconds: 3                             # 响应超时时间, 取值范围为[2,60]，默认为3s (Optional)
      intervalSeconds: 5                                 # 健康检查间隔, 范围为[5,300], 默认为5s (Optional)
      httpPath: "/"                                      # 检查路径, 健康检查的目标路径，必须以"/"开头，长度不超过1000字符,不支持双引号'”',允许输入具体的文件路径，默认为根目录, 当protocol为http时，必填, 仅支持HTTP协议 (Optional)
      httpCode: ["2xx","3xx","4xx"]                      # 检查来自后端目标服务器的成功响应时，要使用的HTTP状态码。您可以指定单个数值（例如："200"，取值范围200-499）、一段连续数值（例如："201-205"，取值范围范围200-499，且前面的参数小于后面）和一类连续数值缩写（例如："3xx"，等价于"300-399"，取值范围2xx、3xx和4xx）。多个数值之间通过","分割（例如："200,202-207,302,4xx"）。目前仅支持2xx、3xx、4xx。仅支持HTTP协议，默认为[2xx、3xx] (Optional)
  - protocol: "https"
    certificateId: "cert19070379d79dd76c11b679"          # alb有效，如果协议为https或者tls，则必须指定，证书id可从jd console上取得
    connectionIdleTimeSeconds: 1800
    backend: 
      connectionDrainingSeconds: 300
      sessionStickyTimeout: 300
      sessionStickiness: false
      algorithm: "IpHash/LeastConn/RoundRobin(default)"
    healthCheckSpec: 
      healthyThresholdCount: 3
      unhealthyThresholdCount: 3
      checkTimeoutSeconds: 3
      intervalSeconds: 5
nodeSelector: "key1=value,key2 in (aaa,bbb,ccc)"         # key是node的lable里的key，value是node的lable里的value，可手工指定哪些node绑定到LB的后端，在集群规模比较大的时候，不需要将所有node都绑定到LB后端，减少由于集群的伸缩而造成的LB后端的频繁变化

```
## 创建ALB service
1、创建LoadBalancer alb类型的service，命名为alb-service.yaml文件定义如下：
```
kind: Service
apiVersion: v1
metadata:
  name: alb-service
  labels:
    run: myapp
  annotations:
    service.beta.kubernetes.io/jdcloud-load-balancer-spec: |
      version: "v1"  
      loadBalancerType: alb
      internal: false
      elasticIp:
        bandwidthMbps: 10
        provider: "bgp"
        reclaimPolicy: "delete"
      listeners:
        - protocol: "http"
          connectionIdleTimeSeconds: 600
          backend:
            sessionStickiness: true
            algorithm: "IpHash"
          healthCheckSpec:
            protocol: "http"                   #healthcheck部分不要指定port，K8s分配nodeport后，健康检查会默认还是用nodeport端口。如果用户分配了专门的nodeport用来提供探活服务，则可以指定port
            healthyThresholdCount: 3
            unhealthyThresholdCount: 3
            checkTimeoutSeconds: 3
            intervalSeconds: 5
            httpPath: "/"
            httpCode: ["2xx","3xx","4xx"]
        - protocol: "http"
          connectionIdleTimeSeconds: 1800
          backend:
            proxyProtocol: false
            sessionStickiness: false
            algorithm: "LeastConn"
            httpCookieExpireSeconds: 0
            httpForwardedProtocol: false
            httpForwardedPort: false
            httpForwardedHost: false
            httpForwardedVip: false
        - protocol: "tcp"
          connectionIdleTimeSeconds: 600
          backend:
            algorithm: "IpHash"
            proxyProtocol: false
spec:
  ports:
    - name: http1
      protocol: TCP
      port: 8080
      targetPort: 80
      nodePort: 30790
    - name: http2
      protocol: TCP
      port: 8081
      targetPort: 80
    - name: tcp
      port: 8082
      targetPort: 80
  type: LoadBalancer
  selector:
     run: myapp
```

2、执行kubectl创建命令，创建一个service；其中使用相应的yaml文件名称替换  
`kubectl create -f myservice.yaml`  

3、创建一组nginx pod，mynginx.yaml文件定义如下：
```
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: my-nginx
spec:
  selector:
    matchLabels:
      run: myapp
  replicas: 2
  template:
    metadata:
      labels:
        run: myapp
    spec:
      containers:
      - name: my-nginx
        image: nginx
        ports:
        - containerPort: 80
```

4、执行kubectl创建命令，创建一个deployment；其中使用相应的yaml文件名称替换
```
kubectl create -f mynginx.yaml
```
5、查看已创建成功的deployment，执行以下命令：
`kubectl get deployment my-nginx`
返回结果如下：
```
NAME       DESIRED   CURRENT   UP-TO-DATE   AVAILABLE   AGE
my-nginx   2         2         2            2           4m
```
6、查看相应的pod运行状态，  
`kubectl get pods -l run=myapp -o wide`  
返回结果如下：  
```
NAME                        READY     STATUS    RESTARTS   AGE       IP            NODE
my-nginx-864b5bfdc7-6297s   1/1       Running   0          23m       172.16.0.10   k8s-node-vmtwjb-0vy9nuo0ym
my-nginx-864b5bfdc7-lr7gq   1/1       Running   0          23m       172.16.0.42   k8s-node-vm25q1-0vy9nuo0ym
```
7、查看service详情：  
`kubectl describe service myservice`    
```
Selector:                 run=myapp
Type:                     LoadBalancer
IP:                       10.0.253.58
LoadBalancer Ingress:     114.67.110.200, 10.0.240.11
Port:                     https  8080/TCP
TargetPort:               80/TCP
NodePort:                 https  30789/TCP
Endpoints:                10.0.192.15:80,10.0.192.5:80
Port:                     http  8081/TCP
TargetPort:               80/TCP
NodePort:                 http  31353/TCP
Endpoints:                10.0.192.15:80,10.0.192.5:80
Port:                     tcp  8082/TCP
TargetPort:               80/TCP
NodePort:                 tcp  32477/TCP
Endpoints:                10.0.192.15:80,10.0.192.5:80
Port:                     tls  8083/TCP
TargetPort:               80/TCP
NodePort:                 tls  32761/TCP
Endpoints:                10.0.192.15:80,10.0.192.5:80
Session Affinity:         None
External Traffic Policy:  Local
HealthCheck NodePort:     31614
Events:
  Type     Reason                      Age                From                Message
  ----     ------                      ----               ----                -------
  Normal   EnsuringLoadBalancer        11m (x9 over 26m)  service-controller  Ensuring load balancer
  Normal   EnsuredLoadBalancer         10m                service-controller  Ensured load balancer

```  
**注：LoadBalancer Ingress:114.67.110.200为外部公网IP，"Ensured load balancer"代表load balancer创建成功**  

8、在浏览器中输入与service关联的LoadBalance公网IP及端口，看到如下页面，即表明nginx服务正常。也可以通过curl命令来验证   
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/JCS-for-Kubernetes/nginx.jpg)

## 创建NLB service
1、创建LoadBalancer nlb类型的service，命名为nlbservice.yaml文件定义如下：
```
apiVersion: v1
kind: Service
metadata:
  labels:
    app: nlb
  name: nlb
  annotations:
    service.beta.kubernetes.io/jdcloud-load-balancer-spec: |
      version: "v1"
      loadBalancerType: nlb
      internal: false
      listeners:
        - protocol: "tcp"
          connectionIdleTimeSeconds: 1800
          backend:
            connectionDrainingSeconds: 300
            sessionStickyTimeout: 300
            algorithm: "IpHash"
spec:
  ports:
  - name: tcp
    port: 8085
    protocol: TCP
    targetPort: 80
  selector:
    run: myapp
  type: LoadBalancer
status:
  loadBalancer: {}

```

2、测试和验证的步骤和alb service一致

## 创建DNLB service
1、创建LoadBalancer nlb类型的service，命名为dnlbservice.yaml文件定义如下：
```
apiVersion: v1
kind: Service
metadata:
  labels:
    app: dnlb
  name: dnlb
  annotations:
    service.beta.kubernetes.io/jdcloud-load-balancer-spec: |
      version: "v1"
      loadBalancerType: dnlb
      internal: false
      listeners:
        - protocol: "tcp"
          connectionIdleTimeSeconds: 1800
          backend:
            algorithm: "IpHash"
spec:
  ports:
  - name: tcp
    port: 8086
    protocol: TCP
    targetPort: 80
  selector:
    run: myapp
  type: LoadBalancer
status:
  loadBalancer: {}

```

2、测试和验证的步骤和alb service一致


