
# 连接集群

 **安装kubectl客户端**

Kubernetes 命令行客户端 kubectl可以让您从客户端计算机连接到 Kubernetes 集群，实现应用部署。

## 1.kubectl版本 

kubectl版本可以集群版本一致，或者集群版本+1。集群版本为1.16.4时，推荐下载的Kubectl版本为1.16.4；

## 2.安装和设置 kubectl 客户端


京东云提供了1.16.4版本的kubectl客户端，您可以直接下载使用，详情参考如下命令：

```
wget https://jke-download-cn-north-1.oss.cn-north-1.jcloudcs.com/rpm/kubectl-1.16.4.12-8d683d98.x86_64.rpm
rpm2cpio kubectl-1.16.4.12-8d683d98.x86_64.rpm | cpio -div
cp ./usr/bin/kubectl /usr/bin/
```
具体其他系统安装，还请参考[官方文档](https://kubernetes.io/docs/tasks/tools/install-kubectl/)

## 3.配置集群凭据

凭据在Kubernetes集群-集群服务-集群-详情页-kubectl客户端配置，将凭据复制到本机$HOME/.kube/config；配置完成后，您即可以使用 kubectl 从本地计算机访问 Kubernetes 集群。
例：Centos 7.4 64位系统下，执行以下命令：
```
mkdir -p ~/.kube
touch ~/.kube/config
vi ~/.kube/config
```
保存凭据完成，执行以下命令验证：  
`kubectl version`  
出现以下内容，即为配置成功：  
```
Client Version: version.Info{Major:"1", Minor:"16", GitVersion:"v1.16.4", GitCommit:"224be7bdce5a9dd0c2fd0d46b83865648e2fe0ba", GitTreeState:"clean", BuildDate:"2019-12-11T12:47:40Z", GoVersion:"go1.12.12", Compiler:"gc", Platform:"linux/amd64"}
Server Version: version.Info{Major:"1", Minor:"16+", GitVersion:"v1.16.4-12.8d683d9", GitCommit:"8d683d982b20a8f28a62ad502db0f352e50f621c", GitTreeState:"clean", BuildDate:"2019-12-30T09:24:27Z", GoVersion:"go1.12.12", Compiler:"gc", Platform:"linux/amd64"}
```
