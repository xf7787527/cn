## 包部署的应用

包部署的应用是将部署包，部署到分组绑定的主机上

### 应用成员

在应用详情菜单中，应用负责人可管理该应用的成员

#### 成员管理

![image-20220413165535735](http://devops-minio.jdcloud.com/doc-image/All-Image/app-package.assets/image-20220413165535735.png)

新增成员：输入成员名称，选择角色即可添加
![image-20220413165549159](http://devops-minio.jdcloud.com/doc-image/All-Image/app-package.assets/image-20220413165549159.png)

#### 角色与权限说明

|              | 运维 | 开发 | 测试 | 应用负责人 |
| ------------ | ---- | ---- | ---- | ---------- |
| 应用更新     |      |      |      | ✔          |
| 应用查询     | ✔    | ✔    | ✔    | ✔          |
| 配置文件更新 | ✔    | ✔    | ✔    | ✔          |
| 配置文件查询 | ✔    | ✔    | ✔    | ✔          |
| 分组更新     | ✔    |      |      | ✔          |
| 分组查询     | ✔    | ✔    | ✔    | ✔          |
| 主机更新     | ✔    |      |      |            |
| 主机查询     | ✔    |      |      | ✔          |
| 实例更新     | ✔    | ✔    | ✔    | ✔          |
| 实例查询     | ✔    |      |      | ✔          |
| 部署任务更新 | ✔    | ✔    | ✔    | ✔          |
| 部署任务查询 | ✔    | ✔    |      | ✔          |
| dev环境      | ✔    |      | ✔    | ✔          |
| uat环境      | ✔    |      | ✔    | ✔          |
| sit环境      | ✔    |      | ✔    | ✔          |
| product环境  | ✔    |      |      |            |

### 部署任务

部署任务表示部署历史

#### 任务列表

可以查看每次部署任务部署状态和对应的详情，支持按制品名称、操作人搜索

部署状态说明：如果执行时因为脚本问题引发异常，则整个部署任务都会失败

![image-20220413181716736](http://devops-minio.jdcloud.com/doc-image/All-Image/app-package.assets/image-20220413181716736.png)

​                               

#### 任务详情

点击ID进入到任务详情，可以查看到本次部署的情况和日志

![image-20220413182027422](http://devops-minio.jdcloud.com/doc-image/All-Image/app-package.assets/image-20220413182027422.png)

#### 任务创建

![image-20220413182358028](http://devops-minio.jdcloud.com/doc-image/All-Image/app-package.assets/image-20220413182358028.png)

1. 任务创建时需要设置：

- 部署的环境和分组
- 输入部署制品的地址（一般是对象存储制品的地址）
- 部署策略：暂时只支持滚动部署

**并发度计算规则**

部署一批机器的个数 =（总机器数*并发度）进行向下取整，最小为1，最终不够的进行全部部署

例如：如果是10台机器，并发度为30%，则一批进行3台机器部署，部署3次后，第四次部署1台机器

2. 点击“部署”，跳转到部署列表 

### 实例列表

实例列表可以根据IP和分组进行筛选，实例操作可以进行批量重新部署、重启、启动、停止，单实力支持删除

![image-20220413195841121](http://devops-minio.jdcloud.com/doc-image/All-Image/app-package.assets/image-20220413195841121.png)

### 分组管理

#### 分组列表

分组列表支持按名称搜索，每个分组配置可以查看详情、查看运行状态、管理主机、删除

![image-20220413201854670](http://devops-minio.jdcloud.com/doc-image/All-Image/app-package.assets/image-20220413201854670.png)

##### 查看详情

详情中可以查看分组的基本信息、分组配置、分组机器

###### 基本信息

![image-20220413202130127](http://devops-minio.jdcloud.com/doc-image/All-Image/app-package.assets/image-20220413202130127.png)

###### 分组配置

分组配置中如果对某个文件修改，支持查看修改的历史版本，并进行比对

![image-20220413202257732](http://devops-minio.jdcloud.com/doc-image/All-Image/app-package.assets/image-20220413202257732.png)

分组配置发生变化时，可查看对比变更

![image-20220413175227604](http://devops-minio.jdcloud.com/doc-image/All-Image/app-package.assets/image-20220413175227604-9855072.png)

###### 分组机器

以分组为粒度部署时，分组关联主机可以通过当前页面管理

![image-20220413202310973](http://devops-minio.jdcloud.com/doc-image/All-Image/app-package.assets/image-20220413202310973.png)

![image-20220413210520639](http://devops-minio.jdcloud.com/doc-image/All-Image/app-package.assets/image-20220413210520639.png)

##### 查看运行状态

运行状态中可以看到当前分组下部署的实例信息、部署信息、部署历史

![image-20220413202459985](http://devops-minio.jdcloud.com/doc-image/All-Image/app-package.assets/image-20220413202459985.png)

![image-20220413202548387](http://devops-minio.jdcloud.com/doc-image/All-Image/app-package.assets/image-20220413202548387.png)

![image-20220413202556975](http://devops-minio.jdcloud.com/doc-image/All-Image/app-package.assets/image-20220413202556975.png)

##### 添加主机

同分组详情中添加主机

##### 删除

删除是一个敏感操作，需要输入分组名称做校验

![image-20220413202348587](http://devops-minio.jdcloud.com/doc-image/All-Image/app-package.assets/image-20220413202348587.png)

#### 创建分组

创建分组时需要提前准备脚本：启动脚本、检查脚本、停止脚本

部署路径可以在高级配置中进行配置，表示包会部署在部署路径下

![image-20220413170529702](http://devops-minio.jdcloud.com/doc-image/All-Image/app-package.assets/image-20220413170529702.png)

点击“保存 & 下一步”后会跳到分组配置，在这里可以设置当前分组的文件和环境变量，配置文件默认会继承应用管理中的配置文件。分组部署时会将配置文件分发到分组包含的全部机器中，同时注入机器的环境变量

![image-20220413201804283](http://devops-minio.jdcloud.com/doc-image/All-Image/app-package.assets/image-20220413201804283.png)

### 应用高级配置

在高级配置中，可以设置应用的部署路径

![image-20220413201927966](http://devops-minio.jdcloud.com/doc-image/All-Image/app-package.assets/image-20220413201927966.png)

