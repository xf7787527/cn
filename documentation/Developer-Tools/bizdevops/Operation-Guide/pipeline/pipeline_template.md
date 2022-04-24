## 系统模板

### 源

#### download code

下载coding.geely.com的代码库；属于系统内置模板。

 - git_repo：代码库地址，支持https和ssh格式，地址格式要与使用的凭证类型匹配
 - local_dir： 本地的相对目录
 - branch：代码库分支。下载代码的branch，
   * 若不为空时：使用流水线所配置的branch，
   * 若为空时，将以如下逻辑确定下载的branch:

     1. 如果是手动触发或定时触发的pipeline，branch的值为master
     2. 如果与开始项中事件触发配置的git_repo不一致，branch的值为master
     3. 如果是push event触发的pipeline，branch为push的branch
     4. 如果是merge event触发的pipeline，branch为merge 的targe branch

 - credential_id：下载使用的凭证关键字
 - 使用erp密码进行下载：

![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline_template.assets/erp_download.png)

 - 使用sshkey进行下载：

![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline_template.assets/ssh_download.png)

### 构建

#### go build

go build模板主要用于golang的构建，使用go的内建构建工具；属于系统内置模板；用户只需要填写以下参数即可。

- version ：选择构建所需要的`golang`的版本
- go_path： 定义`GOPATH`的目录。
  说明：Go 中的工作空间由环境变量`GOPATH`定义。定义完成后，所编写的任何代码都将写在工作区内。Go 将搜索`GOPATH`目录中的任何包。
- working_dir：构建前设置的当前工作目录。
- args： 构建命令`go`后面的命令参数。

#### java build

用于java构建，使用maven等构建工具；属于系统内置模板，用户无法查看源码

 - version：选择构建所需要的`jdk`版本
 - build_tool：选择构建工具以及其版本
 - working_dir： 构建前设置的当前工作目录
 - args： 构建工具命令后面的命令参数

![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline_template.assets/java_build.png)

#### nodejs build

用于nodejs构建，使用npm作为构建工具；属于系统内置模板，用户无法查看源码

 - version：node的版本
 - working_dir：构建前设置的当前工作目录
 - args： 构建工具npm命令后面的命令参数

#### docker_build_batch

批量构建docker镜像，这个keyword会根据提供的base_dir，从base_dir开始，遍历改路径下的所有文件夹，如果文件夹下面有dockerfile和target文件，会以该文件夹为context， dockerfile为构建配置，target里的内容为destination构建镜像，父文件夹永远在子文件夹前面构建，因而子文件夹引用的父文件夹对应的镜像都是最新的。

- base_dir:遍历开始的文件夹路径，必填
- username:上传镜像的目标镜像仓库认证使用的用户名，必填。
  由于username，password配置只有一套，要求在一个文件夹下面的target对应的registry的验证用户名和密码是一致的
- password:上传镜像的目标镜像仓库认证使用的密码，必填
- schema:构建镜像的存储的registry的传输协议，http或者https，默认是https

#### docker_build_kaniko

使用kaniko构建docker镜像，kaniko工具详见：https://github.com/GoogleContainerTools/kaniko

- context:构建上下文路径，是指在该路径下执行镜像构建，必填
- dockerfile:构建镜像所需要的dockerfile配置，必填
- destination:构建的镜像目的名称和tag，包含host，镜像名和tag，例如：harbor.geely.com/production/centos7.5-sh:latest，必填
- username:上传镜像的目标镜像仓库认证使用的用户名，必填
- password:上传镜像的目标镜像仓库认证使用的密码，必填
- schema:构建镜像的存储的registry的传输协议，http或者https，默认是https

### 工具

#### sh

sh属于系统内置模板，用户可以在参数设置中自行编写cmd命令，即可执行shell脚本；

 - 输入参数 cmd：用户执行命令，在此处填写自定义脚本

 - 输出参数 stdout：用户无需填写，系统将默认填充参数： `${% raw %} {{env.name.stdout}} {% endraw %}`   其中，name是表示该step在本stage中的唯一key。

**例子1：使用sh获取变量**

将此模板放到下载代码步骤后面，可以用shell命令获取代码信息，作为其他环节的参数使用，在cmd中输入如下命令:

```
TIME=`date +%Y%m%d%H%M%S`
BRANCH=`git symbolic-ref --short -q HEAD`
COMMIT_ID=`git rev-parse --short HEAD`
echo -e "${BRANCH}-${COMMIT_ID}-${TIME}\c"
```

![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline_template.assets/shell-example1.png)

执行的结果是“分支名-commit_id-时间戳"组成的字符串，在其他环节使用时直接引用该步骤的输出（output）变量即可。

在镜像构建环节引用:

![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline_template.assets/shell-example.png)


**例子2：在sh步骤输出自定义变量**

sh步骤中可以将自定义的环境变量输出供后续的步骤引用：
环境变量输出要采用export的方式:

![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline_template.assets/sh_export.png)

其他步骤可以引用被export出来的环境变量

![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline_template.assets/sh_export1.png)


#### trigger jenkins

触发某个jenkins的job执行，用于和私有jenkins服务联动

 - host：jenkins服务的host
 - user：触发的用户名
 - token：jenkins job的token, 建议创建凭证，通过凭证非明文使用
 - url_path：jenkins job的URL PATH
 - args：jenkins job的参数, JSON dict，没有空格

**例子：触发jenkins任务**

触发这样一个用分组管理，支持参数化构建的jenkins任务

![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline_template.assets/jenkins2.png)

配置如下：

![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline_template.assets/jenkins1.png)

#### helm_push

将指定目录的文件制作成chart包，上传至helm仓库

- repo:chart仓库地址，例如：http://mychart.repo.com:8099
- credential_id:chart仓库的认证信息（用户名，密码）
- path:打包路径,如果从根目录开始，则写为：./

此环节一般与下载代码环节配合使用，在同一个阶段内，先执行下载代码步骤，然后运行helm_push步骤将代码库的文件打包上传。

## 测试

单元测试关卡：支持java（maven）、Golang、NodeJS等多种语言的的单元测试关卡设置。

### Maven单元测试

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline_template.assets/clip_image002.jpg)

### Go单元测试

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline_template.assets/clip_image004.jpg)

### Nodejs单元测试

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline_template.assets/clip_image006.jpg)

### 覆盖率卡点支持（Cobertura覆盖率和jacoco覆盖率）

#### Cobertura覆盖率卡点

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline_template.assets/clip_image008.jpg)

#### jacoco覆盖率测量

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline_template.assets/clip_image010.jpg)

 