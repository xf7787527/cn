## 从团队空间提缺陷、提测

用户日常都在团队空间维护卡片，填写卡片任务等，因此系统提供了从团队空间直接提缺陷、提测的功能

首先，请团队空间管理员，在团队空间->设置开启插件：

![模版关联](http://devops-minio.jdcloud.com/doc-image/All-Image/test_with_teamspace.assets/module_团队空间关联模板.gif)

选择默认模版，则以系统字段提测或提缺陷，用户可选择其他任何模版进行关联，关联后，卡片提测或提缺陷，则已模版中的字段为准

关联后，空间除backlog迭代外，其余迭代内的所有卡片，均可以直接提测或提缺陷

![提缺陷提测](http://devops-minio.jdcloud.com/doc-image/All-Image/test_with_teamspace.assets/module_团队空间-可新增缺陷或新增提测.gif)

点击提测或提缺陷后，会自动打开新增提测和新增缺陷的页面，并自动填充空间、迭代、卡片等信息

