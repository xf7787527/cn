### 产品全景视图

![image-20220215183415591](http://devops-minio.jdcloud.com/doc-image/All-Image/Basic-Infrastructure.assets/image-20220215183415591.png)

### 功能架构 

![image-20220207174019358](http://devops-minio.jdcloud.com/doc-image/All-Image/Basic-Infrastructure.assets/image-20220207174019358.png)

### 技术架构

![73963B942EB5E2B9902EEA91BB6ABA44](http://devops-minio.jdcloud.com/doc-image/All-Image/Basic-Infrastructure.assets/clip_image001.jpg)

架构整体分为三层。最底层是存储层，主要由存储服务以及各中间件组成。中间层是以spring cloud技术栈为核心的微服务落地，包括网关、注册中心、RPC、熔断限流、鉴权、流程、调度等核心组件。插件框架是基于spring自研的微内核业务插件框架，主要用于业务快速定制开发。最上层是微前端架构落地，支持vue和react，同时支持手机端H5以及Hybrid客户端。

### 基础服务

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/Basic-Infrastructure.assets/clip_image002.jpg)

**权限服务**

实现了对不同的人访问资源进行权限的控制，避免因权限控制缺失或操作不当引发的风险问题，如操作错误，隐私数据泄露等问题。目前权限服务支持RBAC和ACL这两种。RBAC模型，基于角色的访问控制（Role-Based Access Control)。实现了包括用户/群组/组织结构/角色/权限的控制，其中用户和角色是多对多的关系，角色和权限也是多对多的关系。用户是发起操作的主体，按类型分可分为2B和2C用户,可以是后台管理系统的用户，可以是OA系统的内部员工，也可以是面向C端的用户。角色起到了桥梁的作用，连接了用户和权限的关系，每个角色可以关联多个权限，同时一个用户关联多个角色，那么这个用户就有了多个角色的多个权限。

权限是用户可以访问的资源，主要包括页面权限，操作权限，数据权限，具体说明如下。

**页面权限**: 即用户登录系统可以看到的页面，由菜单控制，菜单包括一级菜单和二级菜单，只要用户有一级和二级菜单的权限，那么用户就可以访问页面。

**操作权限**: 即页面的功能按钮包括查看、新增、修改、删除等。

**数据权限**: 数据权限就是用户在同一页面看到的数据是不同的。目前组织架构级别的权限，是权限服务的亮点，包含组织层级的继承、包含等权限关系的控制。

**网关服务**

平台整体采用的是微服务架构，各个服务之间的鉴权、安全、服务调度、限流、熔断、统一交由网关来处理。网关技术实现采用的是spring cloud gateway 。在原生网关服务之上，实现了SSO统一认证，结合权限服务实现了API统一认证和鉴权。元数据服务实现了人员和组织架构相关的查找、自动补齐等功能。
