## 敏捷实践类问题

**Q：团队空间、卡片、迭代由谁来创建？**

目前，行云没有设计创建权限，人人均可创建。可根据团队协作分工，自行拟定创建人，设定管理员、成员、访客。

**Q：团队空间以什么维度来建立？**

通常意义来说，团队空间以产品或组件的小组来建立较为合适，实际应用中可以根据实际工作来划分。因相同产品或组件的需求在同一团队空间将更好归档、管理，因此不建议按职能部门划分。

**Q：如果人员异动/离职后，相应需求怎么办？**

我们正在开发人员异动交接功能，之后有相关人员异动，需求也可一并追踪。目前暂行解决办法是通过研发同学提供的接口来变更。

**Q： 需求拆分的规则是怎样的？**

1、主要由产品经理在需求受理后拆分，建议拆分到可执行可分配的需求，已经拆分过的需求（父需求）不能再分配到团队空间，只有末级节点的需求可以分配到团队空间，在拆分中应给予产品经理一定的自由度和拆分的确认。

2、处理中的需求，即已经打入到团队空间的需求，不能再进行拆分。

行云系统会将项目工时按照每日每天每人每个项目一条数据进行汇聚后推送给PMP对应的项目下的系统创建任务内，需求工时不在PMP的现有模块中展示（PMP没有承接此类工时的模块），但是此类工时可以在资源视图的工时填报率中展示，不过资源视图仅部分管理人员有权限可以查看和下载基础信息。

## 代码库

### 异常类常见问题

**Q：仓库首次下载代码时，账号密码认证失败**

原因：未设置个人http password

解决办法：

1. 代码库-个人设置-设置-Http Password进行设置



**Q：Fatal: cannot do a partial commit during a merge**

原因： git认为你有部分代码没有做好提交的准备，比如没有添加

解决办法：

1. 提交全部 git commit -a
2. 如果不想提交全部,那么可以通过添加-i选项 git commit file/to/path -i -m "merge"
   上述情况一般出现在解决本地working copy冲突时出现, 本地文件修改(手工merge)完成后,要添加并提交,使得本地版本处于clean的状态. 这样以后git pull就不再会报错.

**Q：Fatal：Authentication failed for ‘{coding服务域名}/app/xxxxxx.git/’**

原因：本地保存了Git旧认证信息，导致认证失败

解决办法：

1. 检查本地Git认证设置
2. 删除旧认证信息
3. 重新操作git clone

**Q：error: The requested URL returned error: 406 Not Acceptable while accessing** 

原因： Linux系统需要记住git的login信息。

解决办法：

请优先升级一下git，升级后如果问题未解决则参考下面的方法：

​	保存用户登录信息(此方法在本地保存明码的erp账号信息，请慎重选择)

​	在本地编辑   ~/.netrc 文件，添加如下配置信息:

​		machine {coding服务域名}

​		login 用户

​		password 密码
可参考：http://blog.csdn.net/zhaozhi406/article/details/30506153


**Q：GIT LFS PUSH报错**

原因： GIT-LFS安装版本过高(>=2.5.x)

解决办法：将GIT-LFS降级安装2.4.x或2.3.x，然后重新push

下载地址: 

- v2.4.2 https://github.com/git-lfs/git-lfs/releases/tag/v2.4.2
- v2.3.4 https://github.com/git-lfs/git-lfs/releases/tag/v2.3.4

**Q：Git Clone中出现fatal: pack has bad object at offset 238223516: inflate returned -5？**

原因： inflate returned -5 表示zlib解压时发生Z_BUF_ERROR，并不代表代码库包损坏

解决办法：

```
使用Git Fetch命令分段下载代码库
git clone 代码库地址.git --depth 1 -b 分支名(默认为master)
cd 代码库目录
git fetch --unshallow
# 当前已经下载master分支全部commits
# 如想切换其他分支，按如下操作
git config remote.origin.fetch "+refs/heads/*:refs/remotes/origin/*"
git fetch origin
# 至此已经完整下载代码库全部commits
# 切换其他分支
git checkout 目标分支/TAG
如果以上命令并没有解决你的问题，请联系代码库管理员，进行一次GC整理（注：代码库过大可能会导致GC时间较长，此方法并不推荐）
```

**Q：已经将代码push完成了，但其他同事pull该分支的时候，发现无法获取到当前的commit版本**

原因： 评审策略中对该分支设置了强制代码评审，如果评审未完成，则不会合入到该分支。所以本地无法通过CommitID获取到指定版本

解决办法： 使用git fetch命令获取指定版本，命令如下: `git fetch origin +refs/reviews/*:refs/remotes/origin/reviews/*`

**Q：SSL certificate problem:unable to get local issuer certificate**

解决办法：

```
本地输入此命令即可
git config --global http.sslverify "false"
```

**Q：为什么提交的commit，在本地查询的author信息不是用户本人的信息？**

原因： 由于IDEA对changelist的处理方式的问题：历史change list，里面metadata保存的是其他用户的信息，导致本地commit，会记录metadata中保存的用户信息。

解决办法： 本地使用`git reflog --all`查看历史信息，查找matadata中其他用户信息的change list，并删除即可。

### 操作类常见问题

**Q：如何创建合并请求（代码评审）？**

1、进入仓库合并请求页，点击搜索框右侧的新建合并请求按钮。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/FAQ.assets/WX20190305-152115@2x.png)

2、即可进入新建合并请求页，选择要合并的源分支和目标分支，当源分支与目标分支无差异时，无法创建合并请求。

```
温馨提示：
	代码合并一般都是从源分支合并到目标分支哦。
```

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/FAQ.assets/WX20190305-152214@2x.png)

3、当源分支与目标分支有差异时，即可创建合并请求。同时展示两个分支之间的提交差异和文件差异列表。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/FAQ.assets/WX20190305-152232@2x.png)

4、点击创建合并请求按钮，填写评审标题及内容，即创建成功

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/FAQ.assets/WX20190305-152249@2x.png)

**Q：如何修改代码访问级别？**

进入某一仓库，点击设置按钮，点击左侧通用设置菜单，即可修改访问级别

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/FAQ.assets/WX20190307-154333@2x.png)

**Q：如何自定义评审组人员？**

进入某一仓库，点击设置-评审规则-评审组成员-进行设置。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/FAQ.assets/WX20190307-154650@2x.png)

**Q：如何设置保护分支及可push人员？**

1、进入仓库，点击设置按钮，点击左侧的安全策略菜单，即进入安全策略设置页面。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/FAQ.assets/WX20190307-104649@2x.png)

2、增加保护分支，在分支名输入框和可push人员输入框分别输入分支名和可push人员，点击添加按钮，即可添加保护分支。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/FAQ.assets/WX20190307-104700@2x.png)

**Q：如何自定义评审策略？**

a. 进入仓库，点击设置按钮，点击左侧的评审规则菜单，即进入评审规则设置页面。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/FAQ.assets/WX20190306-114003@2x-20220217112339864.png)

2、点击自定义评审策略按钮，填写相关信息，即可自定义评审策略。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/FAQ.assets/WX20190306-114735@2x.png)

**Q：如何清理磁盘空间？**

进入仓库，点击设置按钮，点击左侧的高级设置菜单，点击存储库GC按钮，即可清理磁盘空间。

**Q：如何使用Git LFS模式上传大文件**

安装步骤
https://github.com/git-lfs/git-lfs/wiki/Installation
Window Installer JBox内网分流地址:  http://3.cn/2AqSkAM
使用教程
https://github.com/git-lfs/git-lfs/wiki/Tutorial

