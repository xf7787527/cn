## 镜像部署的应用

镜像部署的应用是将镜像，部署到分组绑定的集群上

### 应用成员

在应用详情菜单中，应用负责人可管理该应用的成员

#### 成员管理

![image-20220413165535735](http://devops-minio.jdcloud.com/doc-image/All-Image/app-image.assets/image-20220413165535735.png)

输入成员名称，选择角色即可添加

![image-20220413165549159](http://devops-minio.jdcloud.com/doc-image/All-Image/app-image.assets/image-20220413165549159.png)

#### 角色与权限说明

应用下的所有成员有应用的管理权限和发布权限

### 制品列表

![image-20220413172351825](http://devops-minio.jdcloud.com/doc-image/All-Image/app-image.assets/image-20220413172351825.png)

### 负载均衡

支持负载均衡的增删改查功能，主要包含三种负载均衡：LB，NodePort ，ClusterIP；负载均衡功能对应k8s的service，属于集群内的负载均衡

![image-20220413172121474](http://devops-minio.jdcloud.com/doc-image/All-Image/app-image.assets/image-20220413172121474.png)

新增负载时，需要填写负载名称，类型，以及端口信息，并关联分组

![image-20220413172208826](http://devops-minio.jdcloud.com/doc-image/All-Image/app-image.assets/image-20220413172208826.png)

### 发布历史

发布历史菜单，默认查看最新发布的任务，也可查看全部的发布历史

![image-20220413172409631](http://devops-minio.jdcloud.com/doc-image/All-Image/app-image.assets/image-20220413172409631.png)

#### 新建发布任务

在发布历史页面，点击发布，即可创建部署任务

![image-20220413172549544](http://devops-minio.jdcloud.com/doc-image/All-Image/app-image.assets/image-20220413172549544.png)

点击部署后，即可进入部署详情页面

#### 任务详情

在发布历史页面，可查看每一次部署的详细信息。可以查看cpu、内存的发布前后的版本流量监控信息，以及容器部署的状态

![image-20220413181633395](http://devops-minio.jdcloud.com/doc-image/All-Image/app-image.assets/image-20220413181633395.png)

点击部署配置，可查看本次部署的部署配置

![image-20220413173030118](http://devops-minio.jdcloud.com/doc-image/All-Image/app-image.assets/image-20220413173030118.png)

点击pod中查看事件，即可查看该pod的事件和状态

![image-20220413173114881](http://devops-minio.jdcloud.com/doc-image/All-Image/app-image.assets/image-20220413173114881.png)

### 分组管理

分组表示应用部署环境的子组

例如：应用部署到生产环境有3个集群，一次部署一个集群，那么一个集群就可以配置成一个分组

#### 分组列表

分组操作说明：

* 部署：点击部署，即可进入创建部署任务界面，将会在新建部署任务时进行详细说明

* 运行信息：点击运行信息即可进入运行状态，查看该分组下pod的运行状态

* Yaml文件：点击查看该分组yaml文件

* 编辑分组：编辑分组的基本信息

* 删除分组：将会删除该分组，建议将该分组下的服务停止后再进行删除

![image-20220413173228319](http://devops-minio.jdcloud.com/doc-image/All-Image/app-image.assets/image-20220413173228319.png)

#### 创建分组

分组信息包含当前环境的部署模板

1. 进入创建分组界面，填写相应的配置信息

- 基本信息：分组名称，环境和关联的集群等信息

* 容器设置：填写该分组的镜像信息（镜像信息在发起部署时，可变更）；容器数量和规格参数，填写启动命令和参数

* 部署策略：用户可选择滚动部署，多批次部署两种部署方式

* 健康检查：用户可以使用健康检查，支持httpGet，Container Command，和TCP Socket三种方式

* 生命周期：启动前，启动后的httpget和command方式

* Gpu的配置：选择gpu类型和gpu个数

2. 点击保存&下一步，即可配置负载均衡（k8s的service资源），如不需要，可点击跳过即可
3. 在分组配置界面，可添加该分组的配置文件以及环境变量，对于应用管理中的配置文件会自动继承，如果配置文件是模版类型，则需要在分组创建中填入占位符

![image-20220413174125471](http://devops-minio.jdcloud.com/doc-image/All-Image/app-image.assets/image-20220413174125471.png)

![image-20220413174238262](http://devops-minio.jdcloud.com/doc-image/All-Image/app-image.assets/image-20220413174238262.png)

#### 分组配置

在分组配置界面，可查看分组的基本配置，点击编辑即可更新分组的配置

##### 编辑分组基本配置

在基本配置界面，点击编辑即可变更分组的基本配置

![image-20220413174810056](http://devops-minio.jdcloud.com/doc-image/All-Image/app-image.assets/image-20220413174810056.png)

##### 分组配置文件的管理

在分组配置文件中，默认继承应用配置文件，同时可以添加分组配置文件

![image-20220413175200884](http://devops-minio.jdcloud.com/doc-image/All-Image/app-image.assets/image-20220413175200884.png)

分组配置发生变化时，可查看对比变更

![image-20220413175227604](http://devops-minio.jdcloud.com/doc-image/All-Image/app-image.assets/image-20220413175227604.png)

![image-20220413175353855](http://devops-minio.jdcloud.com/doc-image/All-Image/app-image.assets/image-20220413175353855.png)

#### 运行状态

在运行状态界面，可查看分组的运行信息，分组支持切换，查看其他分组的运行状态

![image-20220413175507403](http://devops-minio.jdcloud.com/doc-image/All-Image/app-image.assets/image-20220413175507403.png)

在运行状态界面，可以重启该分组下所有pod的服务，以及调整该分组的副本信息

##### 容器状态

默认显示“容器状态”tab，可以查看该分组下所有pod的状态与详细信息

![image-20220413180428229](http://devops-minio.jdcloud.com/doc-image/All-Image/app-image.assets/image-20220413180428229.png)

状态和事件：pod运行时发生的事件

YAML文件：pod的详细yaml配置

驱逐：删除并重新拉起新的pod

查看日志：点击容器右侧是日志操作，即可查看容器的日志信息，在查看日志界面，可对日志进行日志的实时更新或手动更新，也可以下载日志

登录终端：点击容器右侧是终端操作，即可登录到容器内，进行相关操作部署信息

##### 部署信息

当前tab页可查看该次部署任务的部署信息

 ![image-20220413180622616](http://devops-minio.jdcloud.com/doc-image/All-Image/app-image.assets/image-20220413180622616.png)

##### 部署历史

在部署历史tab页，可以查到该分组下部署记录，点击“详情”可以查看到对应部署信息

![image-20220413180712285](http://devops-minio.jdcloud.com/doc-image/All-Image/app-image.assets/image-20220413180712285.png)

点“回滚到此版本”，该分组下pod上的服务将重新部署该版本配置

### 应用关联的集群信息

当前应用下，点击资源管理-k8s集群，可查看该应用关联的集群信息

 ![image-20220413180926292](http://devops-minio.jdcloud.com/doc-image/All-Image/app-image.assets/image-20220413180926292.png)

点击关联集群，填写集群名称，和授权码，即可将集群关联到该应用下

![image-20220413180940394](http://devops-minio.jdcloud.com/doc-image/All-Image/app-image.assets/image-20220413180940394.png)