## 仓库管理

### 新建仓库

#### 新建仓库


1. 您在使用Coding平台时，为了更方便的创建代码仓库，有以下几个创建入口：

   * 在Coding首页，点击菜单栏右上方的➕，选择**新建仓库**，进入新建仓库页面，仓库的命名空间默认为个人群组（用户ERP）。

   * 在Coding首页，左侧仓库列表，点击**新建**按钮，进入新建仓库页面，仓库的命名空间默认为个人群组（用户ERP）。
     ![](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/new_repo.jpg)

   * 选择一个群组，在群组空间内，点击**新建仓库**按钮，进入新建仓库页面，仓库的命名空间默认为当前群组。

     ![](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/new_repo1.jpg)

2. 在新建仓库页签，选择**命名空间**，填写**仓库名称**，**仓库中文名称**，**仓库描述** *（可选）*，**语言** *（默认: JAVA）*，以及选择相应的**访问级别**，点击**创建**按钮，仓库创建完成。

>[说明:]
>1. 仓库名称：是仓库中的唯一标识，创建仓库后，将不能修改。命名规则：可由字母（不区分大小写）、数字、点、中划线，下划线随机组合，且必须以字母或数字开头、结尾。
>2. 仓库负责人：默认将创建者设置为仓库的owner，并赋予master权限。
>3. 访问级别：根据代码仓库的实际情况设置访问级别。

   ![](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/new_repo2.jpg)

#### 导入仓库

如果您已经在gitlab有自己的代码仓库，想切换到Coding平台管理您的代码，请按照以下步骤操作：

1.  在Coding首页，点击菜单栏右上方的➕，选择**导入仓库**，进入导入仓库页面。
    ![](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/new_repo4.jpg)

2.  在新建仓库页签，输入Gitlab中的仓库地址，选择**命名空间**，填写**仓库名称**，**仓库中文名称**，**仓库描述** *（可选）*，**语言** *（默认: JAVA）*，以及选择相应的**访问级别**，点击**创建**按钮，仓库创建完成。

>[仓库导入的注意事项]
>
>1. 操作导入的人员，必须是Gitlab仓库中的成员，导入Coding后，默认将该操作人设置为该仓库的Owner。
>2. 支持自动导入成员和成员权限。

   ![](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/new_repo5.jpg)

## 仓库文件


进入仓库**代码**页，即可查看文件列表及每个文件的最新提交备注。你还可通过切换分支或tag的方式查看不同分支或tag的文件列表。


>[功能提示]
>
>1. 提交、分支、标签、成员下的颜色条代表仓库语言的分布，点击颜色条即可查看哦。
>2. 文件列表第一行信息为：最新提交人、提交备注及commit id。
>3. 文件树模式浏览：文件将以树状结构呈现于左侧，方便查找文件，并和文件列表中的文件连动。
>4. 在线编辑功能：直接在该仓库，在线新建，编辑，删除文件。

   ![](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/files_list.jpg)

### 新建文件

1. 选择某个代码仓库，点击进去仓库的**代码**页，点击**新建文件**，进入新建文件页面。

2. 在新建文件页面，填写**文件名称**，以及**文件内容**（文件内容的主题样式，可根据自己的喜好选择），**修改文件的备注记录**。

   * 文件命名规范：可由字母（不区分大小写）、数字、点、中划线，下划线随机组合，且必须以字母或数字开头、结尾。
   * 文件长度限制：大于2个字符，小于50个字符。
   * 文件内容的主题样式：有多种样式，可根据自己的喜好选择，默认是Default样式。

3. 选择提交的方式。点击**Commit changes**，即可将该文件提交到所选择的分支。

   提交方式有两种：

   * 直接提交到当前分支。
   * 提交文件的同时，基于当前分支创建新分支，并将该文件提交到新分支上。
     新分支默认的命名规则：当前登录账号-patch-1；比如：miaoguangying-patch-1。可根据需求自行修改分支名称。

![](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/files_new.jpg)

### 编辑文件

1. 选择某个代码仓库，点击进去仓库的**代码**页，选择要修改的文件，点击该文件，进入该文件的详情页面。
2. 在文件的详情页面，点击**编辑**按钮，进入文件的编辑界面
3. 在文件编辑页面，更改**文件内容**（文件内容的主题样式，可根据自己的喜好选择），填写**修改文件的备注记录**。
4. 选择提交的方式。点击**Commit changes**，即可将该文件提交到所选择的分支。

### 删除文件

1. 选择某个代码仓库，点击进去仓库的**代码**页，选择要修改的文件，点击该文件，进入该文件的详情页面。
2. 在文件的详情页面，点击**删除**按钮，进入文件的编辑界面
3. 在文件删除页面，填写**修改文件的备注记录**。选择提交的方式。点击**Commit changes**，即可将该文件提交到所选择的分支。

### 在线编辑文件的权限规则

1. 必须是该仓库的成员，且是Owner，Master，Developer三个角色中的其中一种。
2. 如果该分支设置了保护分支，则必须是保护分支的成员。

## 提交历史

1. 进入仓库**Code**页，点击仓库描述及标签下方的**commits或提交**按钮。
   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/WX20190305-145041@2x.png)

2. 即可查看整个仓库的提交历史。在提交历史页，您可以切换分支来查看不同分支的提交历史。
   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/WX20190305-140946@2x.png)

3. 同时，针对某一提交历史，您还可复制commit-id，点击commit-id进入提交历史文件对比页。
   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/WX20190305-143040@2x.png)
4. 除此之外，你还可点击右侧的***< >***按钮，进入对应的commit-id的文件列表页。
   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/WX20190305-143731@2x.png)

## 分支列表

1. 进入仓库**Code**页，点击仓库描述及标签下方的**branches或分支**按钮。
   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/WX20190305-145232@2x.png)
2. 即可查看整个仓库的分支列表。概述中包括仓库的默认分支、活跃分支及陈旧分支。
   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/WX20190305-141019@2x.png)

3. 点击**活跃分支**，即可查看三个月内有过提交的所有活跃分支。
   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/WX20190305-141036@2x.png)
4. 点击**陈旧分支**，即可查看三个月内没有提交的所有活跃分支。
   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/WX20190305-141052@2x.png)

## 成员列表

1. 进入仓库**Code**页，点击仓库描述及标签下方的**members或成员**按钮。
   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/WX20190305-151243@2x.png)

2. 即可查看整个仓库的成员基本信息及其角色。
   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/WX20190305-151259@2x.png)

## 派生仓库

1. 进入仓库，点击仓库上方的**Fork或派生**按钮。
   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/WX20190513-155537@2x.png)

2. 填写Fork原因即可。
   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/WX20190513-155634@2x.png)

3. 您还可进入Fork Request按钮，进入Fork列表页
   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/WX20190513-155826@2x.png)

4. Fork列表页包含我的申请和待我处理的fork请求。
   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/WX20190513-160027@2x.png)

## 文件写保护

支持界面上对“文件”的锁定功能，被锁定文件处于写保护状态，特定成员才可以操作，从而达到保护文件的目的。

>权限设定：仓库**Master/Owner权限**的成员可以锁定/取消锁定文件，编辑/删除已锁定的文件。

* **“锁定”**文件
  * 仓库 - 代码，选择想要锁定的“文件”，点击“锁定”。
  * 被锁定的文件，有🔒标识；无权限成员编辑/删除图标不可见。
    ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/lock-file.png)

  * 鼠标悬停，查看”文件“详细锁定信息。
    ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/lockedfiles.png)
* **”取消锁定“**文件
  * 仓库 - code，选择想要解锁的文件，点击“取消锁定”。
  * 无权限成员“取消锁定”按钮不可见。
    ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/unlock-file.png)
* **查看仓库中已锁定的文件列表**
  * 仓库 - 设置 - 安全策略：“文件写保护“中列出了仓库中所有的锁定文件。
  * 同时可以“取消锁定”文件，被“取消锁定”的文件，将从此列表中删除。
    ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/settings-lock.png)
* **命令行修改锁定文件**，如果权限不足(Master以下成员)，将提示错误不能提交：  ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/lock-command.png)

以`Merge Request`为例，从新建合并请求，查阅合并请求的列表，代码评审，以及最终合并代码进行详细的说明。


## 标签/发行版

目前Coding支持Web页面创建/删除“标签”与“发行版”；同时支持展示通过命令行创建的标签。

### 标签

进入仓库**Code**页，点击**标签**按钮
![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/tag.png)
即可进入“标签”页面
![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/tag-2.png)

**支持**：

* 新建标签：
  * 新建标签命名规范参考：[git check ref format](https://git-scm.com/docs/git-check-ref-format)
  * 标签描述不多于255个字符
    ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/tag-new.png)

  * 支持基于分支/标签/commits新建标签
    ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/tag-new-base.png)

* 从已存在标签创建发行版:
  ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/release-from-tag.png)
    * 添加描述
    * 上传附件
    * 如果暂不支持用于生产环境，可以标记为Pre-release
      ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/release-from-tag-2.png)

* 删除已存在标签:
  ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/tag-delete.png)

### 发行版

进入仓库**Code**页，点击**发行版**按钮
![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/release.png)
即可进入“发行版”页面
![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/release-2.png)

**支持**：

* 创建发行版：
  * 可以选择已存在的标签创建发行版；也可以选择新的名称，创建标签同时创建发行版
  * 添加详细描述
  * 添加附件
  * 如果勾选"这是一个预发行版“，则标记为Pre-release；否则通过Commit时间和发行版创建时间标记 Latest-release
    ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/release-new.png)

* 编辑/删除发行版：
  * 编辑发行版：更新描述，附件，标题等
  * 删除发行版：删除发行版不会删除对应的标签
    ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/release-delete.png)

## 统计视图

>[算法说明]
>本次统计提数使用最新算法
>
>1. 提交过滤 - 忽略所有Merge节点。

>		Merge节点不包含实际有效提交代码，仅作为分支合并点; 且Merge节点在统计时，易引起Commit重复计算,	故排除此节点

>2. 人员匹配 - 按照代码库中所有实际提交（Commit）中提取到的作者（Author）的姓名和邮箱进行人员匹配

>		Commit中的Author信息，优先进行姓名到ERP的精确匹配;如ERP不匹配，再次进行Email到公司Email地址的精确匹配

>		如实际提交中的作者信息不规范，无法匹配到具体人员,此种情况，我们按照当次Push操作人进行统计

### 总览视图

进入仓库，点击**统计按钮**，即可查看仓库总览数据（评审数、代码库大小、语言分布情况等）。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/WX20190305-182403@2x.png)

### 提交视图

进入仓库，点击**统计按钮**，点击左侧**Commits**菜单，即可查看仓库commits、文件数、代码行数变化趋势图。同时还可选择时间范围确定数据范围。![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/WX20190305-182428@2x.png)

### 评审视图


进入仓库，点击**统计按钮**，点击左侧**Reviews**菜单，即可查看仓库评审数、评审人员数据变化趋势图。同时还可选择时间范围确定数据范围。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/WX20190305-182443@2x.png)

### 贡献者视图

进入仓库，点击**统计按钮**，点击左侧**Contributors**菜单，即可查看仓库贡献者数据变化趋势图。同时还可选择时间范围和贡献类型确定数据范围。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/WX20190305-182501@2x.png)

### 活动视图

进入仓库，点击**统计按钮**，点击左侧**活动**菜单，即可查看仓库近期活动(推送、合并、评审、团队)。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/WX20190305-182525@2x.png)

## 仓库设置

### 通用设置

1. 进入仓库，点击**设置**按钮，点击左侧的**通用设置**菜单，即进入通用设置页面。

>[关于访问级别的说明]

> 默认：所有人均可查找、浏览及派生代码库，您设定的成员可维护代码。

> 公开：所有人均可查找，浏览，派生，下载代码库。

> 私有：仓库只能由仓库成员访问,必须明确授予每个用户访问权限。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/WX20190306-111410@2x.png)

### 仓库成员

1. 进入仓库，点击**设置**按钮，点击左侧的**仓库成员**菜单，即进入仓库成员管理页面。

>1. 仓库成员角色说明：
>
>* Master：可以添加tag、管理分支、仓库设置、克隆、提交、拉取代码。
>* Developer：可以克隆、提交、拉取代码。
>* Visitor：只能浏览代码。
>
>2. 仓库成员角色与群组成员角色的关系：当用户在群组和仓库中同时增加了角色权限，则以仓库中的设置为准。


![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/WX20190306-112113@2x.png)

2. 增加成员，在erp输入框和角色输入框分别输入erp和角色，点击添加按钮，即可添加仓库成员。
   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/WX20190307-105806@2x.png)
3. 修改成员角色，点击成员列表右侧角色下拉列表，即可修改成员角色。
   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/WX20190307-105816@2x.png)
4. 删除仓库成员，点击成员列表右侧移除按钮，即可删除仓库成员。
   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/WX20190307-105856@2x.png)

## 评审规则

进入仓库，点击**设置**按钮，点击左侧的**评审规则**菜单，即进入评审规则设置页面，可以设置该仓库的评审组，以及评审策略。

**评审组设置**

在评审人员输入框输入评审人员erp，然后点击添加按钮即可将该人员加入评审组。

>[关于评审组成员设置的说明]
>只有评审组的成员为常用评审成员，每次创建评审时评审成员都可进行评审。除此之外，如您需要临时添加评审人员，可在创建评审时自定义评审人员。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/WX20190306-114003@2x.png)

**评审策略设置**

针对所有分支，Coding平台提供了默认评审策略，以及自定义评审策略，可根据需求设置相应的评审策略。

>[关于评审策略的设置说明]
>
>1. 分支名：可输入某个分支名或分支通配符表达式（必填），默认策略的分支名不可修改。

>2. 通过策略：评审通过的最小人数（必填，默认为1）

>3. 自评策略：勾选后，将允许自评（根据SOX审计要求，建议不要勾选）

>4. 评审组成员策略：开启后，将允许在评审发起时，进行中，添加评审组成员，默认不开启。

>5. 合并策略：开启后，评审通过将自动合并代码，如果未开启，则需要由目标分支操作权限的成员进行手动合并，默认开启

>6. 补充提交策略：开启后，在评审合并前，**允许补充提交**并**重置评审状态**。
>   **新仓库默认开启此选项**；已有的仓库默认不开启，如需要请手动开启。<br>
>
>   <ul><li> 如果是合并触发的评审，当有新的提交merged到此评审的源分支时，则该提交会被自动包含到此评审中。 </li>
>   <li>如果是push触发的评审，则再次push的提交也会默认被包含到此评审中。</li></ul>

>7. 强制评审策略：开启后，push到该分支就要强制创建评审记录。

* 默认策略对全局所有分支生效；

* 自定义策略只对特定的分支生效。如您需要自定义评审策略，也可基于某一分支设置评审策略。（自定义策略的优先级高于默认策略）

  点击右上角**自定义评审策略**,填写分支名，填写通过策略的人数，并设置自评策略、评审组成员策略，合并策略，强制评审策略。

  ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/setting_ Review.jpg)

### 补充提交

**如何开启**
如需要手动开启“补充提交”功能，请参考：

 >[步骤]
 >
 >1. 进入仓库 --> 设置 --> 评审规则 --> 评审策略 --> 配置
 >2. 开启“补充提交”策略，如下图所示：
 >   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/commit-amend-2.png)

**功能说明**

* 评审合并前，允许新的commit自动加入当前评审；不论当前评审是由：
  * `git push` 触发的；
  * 不同分支合并触发的。
* 重置当前评审状态(通过/拒绝)，保留所有评论历史。

>[图示说明]
>目的：合并dev分支到master分支。
>
>* 生成的Merge request包含commit A/B，之后又提交commit C作为bug fix；

* **补充提交**功能可将commits C自动包含到已存在的MR中；
* 同时重置此MR的评审状态，需要重新评审此MR。
  ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/commit-amend-1.png)


**效果演示**

* “补充提交”选项开启后，新的commits会自动加入当前未合并的评审；
  参考下图：

  ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/commit-amend-3.png)

## 安全策略

### 保护分支

1. 进入仓库，点击**设置**按钮，点击左侧的**安全策略**菜单，即进入“保护分支”设置页面。

>[关于保护分支的说明]
>
>* 针对某一保护分支，只有可push成员才能提交代码到改保护分支。
>* 目前任何人不可以删除被保护分支；并且不允许force push。

![](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/protected-branch-1.png)

2. 增加保护分支，在分支名输入框和可push人员输入框分别输入分支名和可push人员，点击添加按钮，即可添加保护分支。
   ![](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/protected-branch-2.png)
3. 删除保护分支，点击保护分支列表右侧的"取消保护"按钮，即可删除保护分支。
   ![](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/protected-branch-3.png)

### 文件写保护

进入仓库，点击**设置**按钮，点击左侧的**安全策略**菜单，即进入“文件写保护”列表页面。

>[文件写保护的说明]
>
>* 被锁定的文件处于写保护状态，只有Master及以上权限成员可以 编辑/删除/解除锁定。

1. 列出本仓库所有被锁定的文件
2. 点击"取消锁定"按钮，即可解除文件锁定并从列表中删除
   ![](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/settings-lock-4463703.png)

## push rules

进入仓库，点击**设置**按钮，点击左侧的**Push Rules**菜单，即进入设置页面。

>[关于Push Rules的说明]

* Push Rules仅仅在使用‘git push’命令或者在Web UI提交代码时触发

* Push Rules默认disable，规则一旦enable，对该仓库所有分支生效

  ![](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/push-rule-1.png)

### Commit提交人信息检查

* 对于新建仓库，此选项默认开启

* 要求Committer信息与当前操作用户信息(ERP/email)保持一致

* 如‘git push’时遇到如下问题：
  ![](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/push-rule-commiter-error-2.png)

  ![](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/push-rule-commiter-error.png)

* **修复方法：**

  1. 更新本地 $HOME/.gitconfig 文件，确保user/email信息正确;：

     ```
     [user]
      name = <ERP 或者 中文名>
      email = <邮箱>
     ```

     例如：
     ![](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/push-rule-commiter-example.png)
       **更新完成后，查看配置信息确保准确无误：**
  ```
    git config --list
  ```

  2. 使用git命令修改“commit message”同时重置当前Commit的user/email：
     `$ git commit --amend --reset-author`

  3. 使用`git log`确认当前commit的Author信息已经重置
  4. 更复杂场景请咨询：咚咚群（81323027）

### 提交信息格式检查

支持两种方式定义提交信息的格式：

* 约定式提交规则：是Coding一直在支持的一种格式
* 自定义规则：允许用户根据需要自己定义提交规则，‘git push’时或者Web UI提交时检查“Commit message”是否符合当前规则，不符合规则拒绝提交

![](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/push-rule-message.png)

### 禁止提交Secret文件

* Coding预定义了保密文件名单（如SSH私钥和其他包含保密的文件），我们不提倡此类文件提交至代码托管平台
* 您可以通过“禁止提交Secret文件”选项，阻止此类文件提交至当前代码库

![](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/push-rule-secret.png)


* ** 预定义的保密文件名单如下：**

```
#####################
# AWS CLI credential blobs
#####################
.aws/credentials
aws/credentials
homefolder/aws/credentials

#####################
# Private RSA SSH keys
#####################
/ssh/id_rsa
/.ssh/personal_rsa
/config/server_rsa
id_rsa
.id_rsa

#####################
# Private DSA SSH keys
#####################
/ssh/id_dsa
/.ssh/personal_dsa
/config/server_dsa
id_dsa
.id_dsa

#####################
# Private ed25519 SSH keys
#####################
/ssh/id_ed25519
/.ssh/personal_ed25519
/config/server_ed25519
id_ed25519
.id_ed25519

#####################
# Private ECDSA SSH keys
#####################
/ssh/id_ecdsa
/.ssh/personal_ecdsa
/config/server_ecdsa
id_ecdsa
.id_ecdsa

#####################
# Any file with .pem or .key extensions
#####################
*.pem
*.key

#####################
# Any file ending with _history or .history extension
#####################
pry.history
bash_history

```

### Webhook

Webhooks允许在发生特定事件时通知外部服务。 当指定的事件发生时，我们会向您提供的每个网址发送一个POST请求。

进入某个仓库，点击**设置**按钮，点击左侧的**Webhooks**菜单，即进入Webhooks页面。你可以管理所添加的webhook信息。
![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/webhook.png)

**添加webhook**

1. 如果你还没有添加webhook，根据提示添加即可，点击**添加Webhook**按钮，进入Webhook新增界面。

2. 在Webhook新增界面，填写**PayLoad URL**，**Token**，**触发条件**，点击**确认**即可。字段说明如下：

   * **PayLoad URL**：第三方应用的Web URL<br>
   * **Token**：第三方应用验证的密钥<br>
   * **触发条件**：触发条件有三种方式：push，tag_push，merge_request。

   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/repo.assets/setting_webhook.jpg)

3. 添加完成后，该条webhook默认开启。

**开启或关闭Webhook**

在Webhooks界面的列表中，选中你要开启或关闭的Webhook，滑动左侧的开关，即可开启或关闭该条webhook。

**配置webhook**

在Webhooks界面的列表中，点击某一条webhook右侧的**配置**按钮，修改**PayLoad URL**，**Token**，**触发条件**，点击**确认**即可。字段说明如下：

  * **PayLoad URL**：第三方应用的Web URL<br>
  * **Token**：第三方应用验证的密钥<br>
  * **触发条件**：触发条件有三种方式：push，tag_push，merge_request。

**删除Webhook**

在Webhooks界面的列表中，点击某一条webhook右侧的**移除**按钮，即可删除该条webhook。

## 高级设置

>[操作权限]
>Master ：仅可以变更默认分支，以及仓库GC操作。

>Owner ：仓库的所有设置，均可操作。

1. 进入仓库，点击**设置**按钮，点击左侧的**高级设置**菜单，即进入高级设置页面。
2. 在高级设置界面，可以对您的仓库进行如下操作：变更默认分支、变更仓库负责人、转移仓库空间、仓库GC、删除仓库。

### 变更默认分支

高级设置中，选择您要设置的分支，点击**确认更改**按钮，在弹出框中，点击**确认**，即可完成仓库默认分支的设置。

>修改默认分支后，所有请求和代码提交都将根据该分支自动进行。

### 变更仓库负责人

高级设置中，选择您要转移的仓库负责人，点击**确认更改**按钮，在弹出框中，再次输入仓库名称，点击**确认**，即可完成仓库负责人的变更操作。

>[说明:]
>
>1. 您只能将仓库转移给一位成员，非成员无法转移。

>2. 转移操作一旦完成，您将无法取消。

>3. 转移操作完成后，您将被赋予"Master"权限。

### 转移仓库空间

高级设置中，选择您要转移的群组空间，点击**确认更改**按钮，在弹出框中，再次输入仓库名称，点击**确认**，即可完成仓库的转移操作。

>[注意]
>
>1. 您只能将仓库转移到您管理的群组。

>2. 您需要将本地仓库地址重定向到新URL。操作方法：`git remote set-url origin NEW_URL`

### 仓库GC

高级设置中，点击**仓库GC**按钮，在弹出框中，点击**确认**，即可完成仓库GC操作。

>[说明:]
>
>1. 根据仓库大小不同，GC过程耗时可能需要几秒到数十分钟。**GC操作不可逆！**

>2. 操作过程可能会遇到504超时，请不用担心，GC任务会在后台继续运行。

>3. GC任务完成后，可能会造成仓库变大，这是因为系统在GC时对仓库做了备份，此备份系统会在一段时间后自动清理。

### 删除仓库

高级设置中，点击**删除仓库**，在弹出框中，再次输入仓库名称，点击**确认**，即可完成仓库的删除操作。

>[删除操作无法恢复！]
>删除仓库将会连同其相关的所有数据（包括 issues, Merge Request等）一起删除。

