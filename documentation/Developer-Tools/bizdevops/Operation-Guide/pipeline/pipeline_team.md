## 创建空间

在新建空间界面，可以选择是否关联coding平台。

> [说明：]
>
> 1. 关联coding平台：空间名称就是coding的group，成员继承coding的group成员。
> 2. 不关联coding平台：空间名称支持重命名，成员由空间的admin管理。

![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline_team.assets/newFolder.png)

## 流水线管理

流水线页面默认展示用户参与的流水线。

流水线页面展示了空间下流水线的详细信息，包括流水线名称、创建时间、最新构建时间以及流水线的负责人。如下图：

   ![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline_team.assets/folder_pipe.jpeg)

在流水线界面，可以通过快捷按钮，对流水线进行不同的操作：

1. 新建流水线：可通过右上角的”创建流水线“按钮，创建该空间下的流水线。

2. 查看空间下所有流水线：可通过右上角开关切换到该空间下所有的流水线。

   > 针对流水线的展示方式进行说明：
   >
   > 1. 若当前用户是空间成员，则展示空间下所有流水线
   > 2. 若通过全局搜索进入流水线页面，则右上角开关默认打开状态，展示该空间下的所有流水线
   > 3. 流水线按照最新构建时间进行倒序排列

3. 查看流水线的构建历史：点击流水线名称，可以进入该流水线的构建历史详情页面，查看流水线的构建历史详情。

4. 编辑流水线：选择某条流水线，点击操作中的编辑图标，即可进入该条流水线的编辑页面。

5. 复制流水线：选择某条流水线，点击操作中的复制图标，即可进入新建流水线页面，并且自动将当前流水线的配置作为新建流水线的配置。

6. 查看详情：选择某条流水线，点击操作中的详情图标，即可查看该条流水线的详情信息。

7. 配置流水线：选择某条流水线，点击操作中的设置图标，默认跳转到该条流水线的成员管理界面，可在构建历史，成员，以及设置进行页签切换。

8. 收藏：将该条流水线收到到自己的文件夹中，点击左侧菜单栏中的收藏图标即可查看到所收藏的流水线。

9. 启用/禁用：用户可以对该条流水线，启动或者禁用操作。

### 自定义步骤

#### 创建自定义步骤

空间的管理员可以创建自定义步骤，在自定义步骤里可以定义此步骤的输入变量，输出变量，执行命令和命令运行使用的镜像。
![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline_team.assets/create_custom_step.png)

#### 运行状态卡片

用户可以在自定义步骤中export环境变量来指定运行状态卡片的展示内容

- JPIPE_VIEW_TYPE 指定卡片的展示类型
- JPIPE_VIEW_DATA 指定卡片展示的数据内容

JPIPE_VIEW_DATA的数据结构如下：

![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline_team.assets/view_data_struct.png)

##### key:value类型展示

```
export JPIPE_VIEW_TYPE=kv
export JPIPE_VIEW_DATA='[{"key":{"value":"报告","color": "'"green"'"},"value":{"value":"'"单元测试"'","color": "'"red"'",  "link": "'"https://www.geely.com"'", "float_value":"'"单元测试"'"}},{"key":{"value":"报告1"}, "value":{"value":"'"单元测试"'", "link": "'"https://www.geely.com"'", "float_value":"'"单元测试"'"}},{"key":{"value":"报告3"}, "value":{"value":"'"单元测试"'","link":"'"https://www.geely.com"'","float_value":"'"单元测试"'"}}]'
```

效果如下图：

![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline_team.assets/view_data_kv.png)

##### table类型展示

```
export JPIPE_VIEW_TYPE=table
export JPIPE_VIEW_DATA='[[{"value":"'"覆盖率 "'"}],[{"value":"'"10%"'","color":"'"red"'"},{"value":"'"20%"'","color":"'"green"'"},{"value":"'"500"'","color":"'"orange"'"}],[{"value":"'"行"'","color":"'"red"'"},{"value":"'"分支"'","color":"'"green"'"},{"value":"'"方法"'","color":"'"orange"'"}],[{"value":"'"测试报告"'","link": "'"https://geely.com"'"}]]'
```

效果如下图：

![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline_team.assets/view_data_table1.png)


#### 设置为公开

流水线支持与其他团队的业务共建，合作团队可以将自己空间下的自定义步骤设置为公开，这样所有其他流水线用户都可以引用。

![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline_team.assets/public1.png)

注意：步骤设置为公开后就不能改为私有了，用户引用该步骤会随着步骤的版本自动更新,在自定义步骤页面能查看版本更新和发布公告，发布公告能单独更新。

![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline_team.assets/public2.jpg)

## 凭证管理

点击左侧栏空间名称后的凭证按钮，进入该空间的凭证管理页面。凭证管理页面展示了该空间下的凭证信息，包括凭证关键字、名称、密码、更新时间、创建时间以及凭证描述。

   ![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline_team.assets/new_credential.jpeg)

针对凭证的管理，需要有该空间的admin权限，可以进行凭证的新增、编辑，更新密码和删除操作。

1. 新增：点击左下角的 “新增” 按钮或右上角 “新增凭证” 按钮，填写关键字、名称、密码和描述，点击后面的保存按钮，即可新增凭证。

2. 更新基本信息：选择要更新的凭证，点击该凭证后方的编辑按钮，可以修改凭证的名称、描述，修改完成后点击保存，即可更新凭证信息。

凭证关键字是凭证的唯一key，一旦创建不可修改，使用过程，凭证关键字可以替代账号密码。

3. 更新密码：选择要更新的凭证，点击该凭证的“更新密码”按钮，即可更新该凭证的密码。

2. 删除：选择要删除的凭证，点击该凭证后方的删除按钮，即可删除该条凭证信息。

**引用凭证时的格式为**

password 类型的引用：

   `${% raw %}{{cred.CredId.username}}{% endraw %}`

   `${% raw %}{{cred.CredId.password}}{% endraw %}`

file 类型的引用：

   `${% raw %}{{cred.CredId.path}}{% endraw %}`

## 空间成员管理

1. 点击左侧栏空间名称后的成员按钮，进入该空间的成员管理页面。成员管理页面展示了该空间下的成员信息。

   ![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline_team.assets/member.png)

