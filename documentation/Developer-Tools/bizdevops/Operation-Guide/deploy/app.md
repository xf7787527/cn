## 应用管理

### 应用列表

点击应用列表，即可查看我负责的，我参与的以及全部的应用列表

![image-20220413160623180](http://devops-minio.jdcloud.com/doc-image/All-Image/app.assets/image-20220413160623180.png)

### 应用创建

#### 创建应用-镜像部署

在应用列表，点击右上角的新增应用，进入创建应用界面

1. 填写应用基本信息，部署类型支持镜像部署和包部署

![image-20220413165347570](http://devops-minio.jdcloud.com/doc-image/All-Image/app.assets/image-20220413165347570.png)

点击保存&下一步，将会存储当前表单信息，并进入下一步，若直接点击保存按钮，则直接创建应用并关闭新建页面

2.关联代码库

![image-20220413165424418](http://devops-minio.jdcloud.com/doc-image/All-Image/app.assets/image-20220413165424418.png)

3. 点击保存&下一步，进入导入资源界面，可以关联相应的集群信息；填写集群名称和集群授权码，即可将集群关联到该应用下。关于集群授权码的获取，可联系集群负责人获取授权码

![image-20220413165439079](http://devops-minio.jdcloud.com/doc-image/All-Image/app.assets/image-20220413165439079.png)

如需要添加集群，可以进入集群管理见面进行添加集群

4. 点击下一步，添加标签和域名

![image-20220413165452958](http://devops-minio.jdcloud.com/doc-image/All-Image/app.assets/image-20220413165452958.png)

5. 点击完成，跳转到应用列表
6. 点击应用名称，可以查看应用详情

![image-20220413161619080](http://devops-minio.jdcloud.com/doc-image/All-Image/app.assets/image-20220413161619080.png)

#### 创建应用-包部署

1. 填写表单，包部署的应用创建时需要有负责人和运维人员角色添加

![image-20220413162727784](http://devops-minio.jdcloud.com/doc-image/All-Image/app.assets/image-20220413162727784.png)

2. 点击保存，跳转到应用列表
3. 点击应用名称，可以查看应用详情

![image-20220413161746713](http://devops-minio.jdcloud.com/doc-image/All-Image/app.assets/image-20220413161746713.png)

### 配置文件管理

点击应用管理-配置文件，即可配置应用维度的配置文件，配置文件根据编写方式分为两种：

* 常规配置文件：按照正常的配置文件输入即可。

* 配置模板：若用户在配置文件中设置了占位符{{ }}，则系统将任务该配置文件为模板文件，在分组配置中需要对占位符进行赋值。比如：name={{key}},则在分组下需要将{{key}}占位符key赋值后，方可使用。

配置文件配置好后，在配置分组时可以直接继承

#### 配置文件列表

应用下的配置文件，可进行查看该配置的详细信息、更新历史、编辑、删除该配置。

![image-20220413164810993](http://devops-minio.jdcloud.com/doc-image/All-Image/app.assets/image-20220413164810993.png)

#### 新增配置文件

点击“+新增配置”按钮，即可进入新增配置文件页面，填写配置文件名称，以及内容，点击保存，即可将配置文件保存在应用配置文件列表。
新增配置时，可以设置相对路径或绝对路径

* 绝对路径：默认是“/”开头，设置的路径不会随高级配置中设置的部署路径变化。比如，`/export/app/poc-test.properties`

* 相对路径：在应用高级配置中的部署路径的基础上，再进行设置配置的路径。比如，高级配置中设置的部署路径为`/sys/`，则设置的配置文件为`/sys/export/app/poc-test.properties

#### 查看详情

在查看详情页面，可直接进入编辑页面，在编辑页面，只可编辑配置文件的内容。

![image-20220413164835857](http://devops-minio.jdcloud.com/doc-image/All-Image/app.assets/image-20220413164835857.png)
