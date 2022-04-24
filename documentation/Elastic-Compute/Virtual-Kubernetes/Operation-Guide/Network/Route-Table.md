# 集群网络--路由表
京东智联云托管K8S服务将为集群内不同子网绑定路由表，保证集群内可正常访问。
## 普通模式
将会生成三张路由表，命名规则如clusterid-node-rt-0、clusterid-pod-rt-0及clusterid-nat-rt-0，分别绑定至工作节点组子网、Pod子网及Service-LB子网。其中：
### 工作节点子网路由表
* 规则一：去往管理节点CIDR的VPC Peering路由
* 规则二：去往NAT实例的路由（普通模式下会默认在Service-LB子网内创建NAT实例）
* 规则三：local路由
### Pod子网路由表
* 规则一：去往管理节点CIDR的VPC Peering路由
* 规则二：去往NAT实例的路由（普通模式下会默认在Service-LB子网内创建NAT实例）
* 规则三：local路由
### Service-LB子网路由表
* 规则一：Internet路由
* 规则二：local路由
## 自定义模式
当客户在2020年9月28日之后创建K8S集群时若网络配置选择自定义模式，京东智联云K8S服务将同普通模式一样为您所选的工作节点组子网、Pod子网及Service-LB子网创建对应路由表，并绑定至对应子网。命名规则如clusterid-node-rt-0、clusterid-pod-rt-0及clusterid-nat-rt-0，分别绑定至工作节点组子网、Pod子网及Service-LB子网。
### 工作节点子网路由表
* 规则一：去往管理节点CIDR的VPC Peering路由
* 规则二：去往NAT实例/NAT网关的路由（若选择打开NAT则将有此条路由）
   * 创建集群时若选择已创建的NAT网关，则指向NAT网关
   * 创建集群时若选择自动创建，则指向NAT实例
* 规则三：local路由
### Pod子网路由表
* 规则一：去往管理节点CIDR的VPC Peering路由
* 规则二：去往NAT实例/NAT网关的路由（若选择打开NAT则将有此条路由）
   * 创建集群时若选择已创建的NAT网关，则指向NAT网关
   * 创建集群时若选择自动创建，则指向NAT实例
* 规则三：local路由
### Service-LB子网路由表
* 规则一：Internet路由
* 规则二：local路由
