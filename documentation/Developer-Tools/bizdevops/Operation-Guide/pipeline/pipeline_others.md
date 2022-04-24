## variable

  在yaml file中使用变量的是: ${% raw %}{{name}}{% endraw %}  根据不同使用场景，变量分为如下几部分：

### 在模板中出现的变量

1. parameters： 表示模板中的paramters的值，格式为`${% raw %}{{parameters.PARAMETER_NAME}}{% endraw %}`
2. env: 在模板中的output中使用，表示在模板中step的输出，格式为`${% raw %}{{env.STEP_NAME.STEP_OUTPUT}}{% endraw %}`
3. var: 在yaml config 中显示使用variables定义的变量 格式为`${% raw %}{{vars.VARNAME}}{% endraw %}`

### 在pipeline定义中的变量

在pipeline中有各种类型的变量，不同类型的变量通过名称中不同的类型前缀来区分，不同类型的变量如下（下面所说的变量名都不包含前缀）：

#### 宏定义

没有类型前缀，直接用名字的变量是macro变量，它在运行前就会被替换成变量值。
例如:宏定义变量名称为：MACRO_NAME,引用时写法：`${% raw %}{{MARCRO_NAME}}{% endraw %}`

#### 变量

var变量是引用variable的时使用的变量，例如`${% raw %}{{var.package_name}}{% endraw %}`表示这是variable package_name的值， variable 变量在stage或者step中可以通过set来改变

#### 自定义参数

手工触发时，支持自定义参数，
例如，自定义参数名为PARAM1，引用时写法：`${% raw %}{{out._predefine.PARAM1}}{% endraw %}`

#### env 变量

env 变量表示的是在执行过程中各个step的输出，它的变量名是分段的， 不同段之间用"."分割，不同的阶段可用的变量不太一样，下面详细解释一下：

1. 变量名只有一段，比如 `${% raw %}{{env.commit_id}}{% endraw %}`；这个变量只能在step内，定义的在执行步骤完成后的后续操作才能够使用，表示的是执行步骤输出的结果，现阶段只有set步骤内可用

2. 变量名两段，例如 `${% raw %}{{evn.download.commit_id}}{% endraw %}`, 两段的第一段是step名称，第二段是step输出的变量名。这个变量只能在第一段的step（例子里的是download_code）所在的stage内使用，并且使用时，第一段的step必须已经执行完毕。

3. 变量名三段，例如`${% raw %}{{env.dist.download_code.commit_id}}{% endraw %}`, 第一段是stage名，第二段是step名，第三段是step输出的变量名， 这个是在第一段的stage（例子里是dist）后面的stage里使用的变量。


#### out 变量

out变量是引用stage的output输出变量时所用到的，例如`${% raw %}{{out.dist.output_key}}{% endraw %}`, 这个变量除了类型前缀为必须有两段，第一段是stage名称，第二段是stage输出变量的名称

#### cred 变量

cred变量是引用credentials时所使用的变量，它的变量名有两段，第一段是credential的名称，第二段现在只能为username或者password，分别表示credential的username或password,引用凭证时的格式为：

password 类型的引用：

   `${% raw %}{{cred.CredId.username}}{% endraw %}`

   `${% raw %}{{cred.CredId.password}}{% endraw %}`

file 类型的引用：

   `${% raw %}{{cred.CredId.path}}{% endraw %}`


#### result 变量

result变量是每个步骤状态的输出，格式是result.stagename.stepname.status,用户可以在后续的步骤中引用此变量，做流程上的判断处理。引用格式：


   `${% raw %}{{result.stagename.stepname.status}}{% endraw %}`

变量值可以在后续步骤的概览页面查看。


### 系统环境变量

系统环境变量是在pipeline build是提供的runtime环境变量，引用方式为${PARAM_NAME}
包含两类：

#### 运行实时信息相关：

```
1. BUILD_ID : 当前build的id
2. BUILD_NUM : 当前build的在pipeline中的build num
3. PIPELINE_NAME : pipeline 名称
4. PIPELINE_ID: pipeline Id
5. GROUP: pipeline 所属的group 名称
6. TRIGGER_USER: 触发build的user（event触发的为触发gitlab event的user）
7. STAGE_NAME: 当前运行的stage的名称
8. STAGE_DISPLAY_NAME : 当前运行的stage的显示名称
9. PIPELINE_URL : pipeline在ui中的网页的链接
10. BUILD_URL: build 在ui的网页链接
11. WORKSPACE: 当前stage运行的工作目录，通常用作拼接绝对路径
```

#### gitlab event相关：

从gitlab webhook中获取的信息变量, event 信息详情见[event](https://docs.gitlab.com/ee/user/project/integrations/webhook_events.html)

##### push 

```
1. gitlabBranch： push 的git branch
2. gitlabEventType： event类型，对于push event来说是push
3. gitlabUserName： push的gitlab user名字
4. gitlabRepoName： git的repo名字
5. gitlabRepoHomepage： gitlab repo的http url
6. gitlabProjectName： git的project 名字
7. gitlabNamespace： repo的namespace
8. gitlabRepoSshUrl： git ssh下载url
9. gitlabRepoHttpUrl： gitlab http下载url
10. gitlabBefore： push之前的commitId
11. gitlabAfter： push之后的commitId
12. gitlabProjectId：git repo的project id
```

##### merge

```
1. gitlabEventType：event类型，对于merge event来说是merge
2. gitlabBranch: merge request. 的branch， 等于gitlabTargetBranch
3. gitlabActionType： merge request的操作类型，有四种：open， update， merge， close
4. gitlabUserName: 操作merge request的gitlab user名字
5. gitlabSourceBranch：merge的源branch
6. gitlabSourceRepoHomepage：merge的源branch 的homepage url
7. gitlabSourceRepoName： merge的源repo名称
8. gitlabSourceNamespace：merge的源repo的namespace
9. gitlabSourceRepoSshUrl：merge的源repo的ssh下载url
10. gitlabSourceRepoHttpUrl: merge的源repo的http下载url
11. gitlabTargetBranch: merge的目标branch
12. gitlabTargetRepoHomepage：merge的目标branch 的homepage url
13. gitlabTargetRepoName：merge的目标repo名字
14. gitlabTargetNamespace：merge的目标repo的namespace
15. gitlabTargetRepoSshUrl： merge的目标repo的ssh下载url
16. gitlabTargetRepoHttpUrl： merge的目标repo的http下载url
17. gitlabLastCommitId： merge的最后commit id
18. gitlabMergeRequestTitle： merge request的title
19. gitlabMergeRequestDescription： merge request的描述
20. gitlabMergeRequestId： merge request 的request id
21. gitlabMergeRequestIid：merge request的Iid
22. gitlabMergeRequestState： merge request的状态
23. gitlabMergedByUser： 创建merge request的user
24. gitlabMergeRequestAssignee： merege request 的reviewer
```



### 权限矩阵 

<p>主要展示JPipe 角色权限和访问级别的权限，以方便查阅。</p>

#### 权限设置

   Pipeline系统的成员权限目前有Owner、Admin、Runner、Editor、Reader五个，同时适用于空间和流水线，设置如下：

|        功能        | Reader | Runner | 空间Editor | 流水线Editor | 空间Admin | 流水线Admin | 空间Owner | 流水线Owner |
| :----------------: | :----: | :----: | :--------: | :----------: | :-------: | :---------: | :-------: | :---------: |
|      浏览配置      |   √    |   √    |     √      |      √       |     √     |      √      |     √     |      √      |
|      运行历史      |   √    |   √    |     √      |      √       |     √     |      √      |     √     |      √      |
|      运行日志      |   √    |   √    |     √      |      √       |     √     |      √      |     √     |      √      |
|     运行流水线     |        |   √    |     √      |      √       |     √     |      √      |     √     |      √      |
|     创建流水线     |        |        |     √      |              |     √     |             |     √     |             |
|     编辑流水线     |        |        |     √      |      √       |     √     |      √      |     √     |      √      |
|     禁用流水线     |        |        |     √      |      √       |     √     |      √      |     √     |      √      |
|      导入镜像      |        |        |     √      |      √       |     √     |      √      |     √     |      √      |
|      创建凭证      |        |        |     √      |              |     √     |             |     √     |             |
|      编辑凭证      |        |        |   √自己    |              |   √所有   |             |   √所有   |             |
|   创建自定义步骤   |        |        |            |              |     √     |             |     √     |             |
|   编辑自定义步骤   |        |        |            |              |     √     |             |     √     |             |
| 创建空间（coding） |        |        |     √      |              |     √     |             |     √     |             |
|  创建空间（自由）  |        |        |            |              |     √     |             |     √     |             |
| 重命名空间（自由） |        |        |            |              |           |             |     √     |             |
|      创建视图      |        |        |            |              |     √     |             |     √     |             |
|      编辑视图      |        |        |            |              |     √     |             |     √     |             |
|      管理成员      |        |        |            |              |   √空间   |   √流水线   |   √空间   |   √流水线   |
|   变更空间owner    |        |        |            |              |           |             |     √     |             |
|      删除镜像      |        |        |            |              |     √     |             |     √     |             |
|      删除空间      |        |        |            |              |           |             |     √     |             |
|     删除流水线     |        |        |            |              |           |             |           |      √      |
|  变更流水线owner   |        |        |            |              |           |             |           |      √      |


   **注意，流水线的权限高于空间的权限，若流水线权限为空，则流水线权限会继承空间权限**。

#### coding关联空间：

   映射关系如下：

| coding角色 | 流水线角色 |
| :--------: | :--------: |
|   Guest    |   Runner   |
| Developer  |   Editor   |
|   Admin    |   Admin    |
|   Owner    |   Owner    |