# 版本说明  
  
## Kubernetes 社区版本  
- Kubernetes 社区版本以x.y.z标识，其中x表示Major版本，y表示Minor版本，z表示Patch版本，版本说明如下：Major版本一般表示不具有兼容性的API变更；Minor版本表示功能变更，一般向后兼容；Patch版本表示向后兼容的Bug修复
- 京东云基于Kubernetes社区版本提供京东云的Kubernetes集群版本，版本以x.y.z-jcs.N标识 ，每一个Minor版本提供2-3个稳定的Patch版本，京东云将根据确定上线支持的Patch版本，但不保证Patch版本的连续性。-jcs.N后缀标识京东云基于某一Patch版本提供的特殊分支，包含安全更新、Bug修复或功能升级等，由京东云保证版本可用性。
  
## 京东云支持的Kubernetes版本  
  
### 1.18  
#### 版本说明:  
- 1.18社区版与2020年3月26日正式发布，该版本是京东云容器服务Kubernetes支持的版本

#### 社区版支持的新特性说明：  

- Kubernetes拓扑管理器（Topology Manager ） 升级到Beta版 ！

  拓扑管理器功能 是1.18版中Kubernetes的beta版本功能，它可以使CPU和设备（如SR-IOV VFs）实现NUMA，这将使你的工作负载在针对低延迟而优化的环境中运行。在引入拓扑管理器之前，
  CPU和设备 管理器会做出彼此独立的资源分配决策，那么可能会导致在多套接字（ multi-socket ）系统上分配不良，从而导致关键型应用程序的性能下降。

- Serverside Apply引入Beta 2版本

  Server-side Apply 在1.16中被升级为Beta，在1.18中引入Beta 2版本。这个新版本将跟踪和管理所有新Kubernetes对象的字段更改，从而使你知道更改了什么资源以及何时更改的。

- 使用IngressClass扩展Ingress，并用IngressClass替换不推荐使用的注释

  在Kubernetes 1.18中，Ingress有两个重要的补充：一个新pathType字段和一个新IngressClass资源。该pathType字段允许指定路径应如何匹配。除了默认ImplementationSpecific类型外，
  还有new Exact和Prefixpath类型。

  该IngressClass资源用于描述Kubernetes集群中的Ingress类型。入口可以通过ingressClassName在入口上使用新字段来指定与它们关联的类。这个新资源和字段替换了不建议使用的
  kubernetes.io/ingress.class注释。

- SIG-CLI引入kubectl debug命令

  SIG-CLI一直在争论是否需要调试实用程序。随着临时容器(ephemeral containers)的发展，开发人员越来越需要更多类似kubectl exec的命令。该kubectl debug命令的添加（它是Alpha版本
  ，但 欢迎你提供反馈），使开发人员可以轻松地在集群中调试其Pod。我们认为这种增加是无价的。此命令允许创建一个临时容器，该容器在要检查的Pod旁边运行，并且还附加到控制台以进行交互式
  故障排除。

- Alpha版本引入Windows CSI

  随着Kubernetes 1.18的发布，用于Windows的CSI代理的Alpha版本也已发布。CSI代理使非特权（预先批准）的容器能够在Windows上执行特权存储操作。现在，可以利用CSI代理在Windows中支持
  CSI驱动程序。

### 1.16 
#### 版本说明:  
- 1.16社区版与2019年9月18日正式发布，该版本是京东云容器服务Kubernetes支持的版本

#### 社区版支持的新特性说明： 
- Custom resources：CRD 是对 Kubernetes 的扩展，用以服务于新的资源类型，自 1.7 版本以来，CRD 已经在 Beta 版中可用。在 1.16 版本中，CRD 正式步入通用可用性（GA）。

- Admission webhook：Admission webhooks 作为 Kubernetes 扩展机制被广泛使用，并且自 1.9 版本以来已经在 Beta 版中可用。在 1.16 版本中，Admission webhook 也正式步入通用可用性（GA）。

- Overhauled metrics：Kubernetes 广泛使用一个全局 metrics registry 来注册要公开的 metrics。通过实现 metrics registry，metrics 可以以更透明的方式注册。而在这之前，Kubernetes metrics 被排除在任何稳定性需求之外。

- Volume Extension：新版本有大量和 Volume 及 Volume 修改相关的增强。CSI 规范中对 Volume 调整的支持正在转向 Beta 版，它允许任何 CSI spec Volume plugin 都可以调整大小。
