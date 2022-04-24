
# 删除集群

**操作说明**

 1. 删除集群将移除所有集群相关的资源、集群中所有工作节点组以及工作节点组中的工作节点，已部署的应用将被彻底删除；自行创建的公网IP及未设置自动删除的Kubernetes持久化存储会继续保留，如不需保留，请前往对应页面删除，以免产生额外费用。  
 2. 删除成功后，状态会变成已删除，并在控制台展示信息保留15分钟。  

**删除集群步骤：**

 1. 打开控制台，选择[弹性计算>>Kubernetes集群>>集群服务>>集群](https://cns-console.jdcloud.com/host/kubernetes/list);  
 2. 选择需要删除的集群服务，点击右侧【删除】按钮；  
  ![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/JCS-for-Kubernetes/删除Kubernetes集群.png)
 3. 在弹出的删除Kubernetes集群弹窗中，点击【确定】则触发删除Kubernetes集群。
