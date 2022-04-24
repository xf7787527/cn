## 个人空间

个人空间主要是从登录者的维度进行查看：

  >* 个人最近一年贡献值,贡献日历；
  >* 自从加入 Coding以来的主要贡献活动；
  >* 个人参与或负责的仓库，群组；
  >* 对个人的权限（包括仓库，群组权限，以及SSH key，API token）的管理。

### 总览

首页 - 右上角头像 - 进入 您的个人首页 即可。

#### 常用仓库

按照个人在仓库中的贡献时间统计。

  >* 列出常用的仓库top 4;
  >* 显示仓库的名称，描述和语言类型;
  >* 如果点击查看更多，可以显示所有您参与或负责的仓库。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/personal.assets/personal_common_repo.png)

#### 贡献日历

按照contributions统计显示最近一年的贡献数据，每个空格代表一天。
**贡献值统计包含6类数据：**

  >* 首次登陆Coding平台
  >* 新建仓库；之后被删除的不计入。
  >* 加入/新建群组；之后群组被删除的不计入。
  >* 提交的commits；之后提交commits的仓库被删除的不计入。
  >* 开启的MR；如果第一天新建MR，第二天合并；则在第一天更新MR的状态；第二天不重复计算开启MR的数据。
  >* 参与的评审，并给出评审意见（通过/拒绝）的计入，只有comments的不计入。

左上角显示近一年贡献总数据；鼠标悬停，显示当天日期和当天贡献数据；点击左下角 **“查看如何计算贡献值”**, 了解贡献值计算详情。
![img](http://devops-minio.jdcloud.com/doc-image/All-Image/personal.assets/personal_contribution_calendar.png)

#### 贡献活动

记录自从登陆Coding平台以来所有的贡献数据；并与贡献日历实现联动。

  >* 默认按照月份分类聚合当月数据。
  >* 点击"查看更多活动记录“，显示更早一个月数据。
  >* 如果点击贡献日历上某天，则详细显示当天贡献数据。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/personal.assets/personal_calendar_activity.png)

## 个人仓库列表

登录Coding系统，在菜单栏，点击右上角的个人头像，选择**您的仓库** 即可进入个人的仓库列表页。

**过滤条件以及排序方式**

| 访问类型                                                     | 过滤条件                                      | 排序方式                                                     |
| ------------------------------------------------------------ | --------------------------------------------- | ------------------------------------------------------------ |
| <ul><li>全部(默认)</li><li> 私有</li><li> 公开</li><li> 默认</li><li> 派生</li><li> 个人</li></ul> | <ul><li>负责的(默认)</li><li>参与的</li></ul> | <ul><li>按更新时间降序(默认)</li><li>按更新时间升序</li><li>按名称字母序升序</li><li>按名称字母序降序</li></ul> |

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/personal.assets/personal_repo.jpg)

## 个人群组列表

登录Coding系统，在菜单栏，点击右上角的个人头像，选择**您的群组** 即可进入个人的群组列表页。

**过滤条件以及排序方式**

| 访问类型                                                     | 过滤条件                                      | 排序方式                                                     |
| ------------------------------------------------------------ | --------------------------------------------- | ------------------------------------------------------------ |
| <ul><li>全部(默认)</li><li> 私有</li><li> 公开</li><li> 默认</li><li> 派生</li><li> 个人</li></ul> | <ul><li>负责的(默认)</li><li>参与的</li></ul> | <ul><li>按更新时间降序(默认)</li><li>按更新时间升序</li><li>按名称字母序升序</li><li>按名称字母序降序</li></ul> |

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/personal.assets/personal_team.jpg)

## 个人设置

登录Coding系统，在菜单栏，点击右上角的个人头像，选择**设置** 即可进入个人的设置界面。

### SSH密钥

使用SSH协议，您可以连接和验证远程服务器和服务。使用SSH密钥，您可以在每次访问时无需提供用户名或密码即可连接到Coding。

#### 检查已有的SSH密钥

在生成新的SSH密钥之前，可以先检查一下是否可以使用已有的ssh密钥。

1. 打开你的终端窗口。
2. 输入`ls -al ~/.ssh`查看已有SSH密钥：

```
$ ls -al ~/.ssh
```

3. 检查目录列表是否存在已有的公共SSH密钥。一般情况下，公钥的文件名是以下之一：
   * id_dsa.pub
   * id_ecdsa.pub
   * id_ed25519.pub
   * id_rsa.pub

#### 生成SSH密钥

1. 打开你的终端窗口。

2. 使用以下命令，将会以你的邮箱作为标签创建一个新的SSH密钥。

```
$ ssh-keygen -t rsa -b 4096 -C "工作邮箱，比如：zhansan@xxx.com"
> Generating public/private rsa key pair.
```

3. 当系统提示您“输入要保存密钥的文件”时，按Enter键。将接受默认文件位置。如下：

```
> Enter a file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]
```

4. 在提示符下，输入安全密码，即可生成一个新的ssh密钥。

```
> Enter passphrase (empty for no passphrase): [Type a passphrase]
> Enter same passphrase again: [Type passphrase again]
```

#### 添加SSH密钥到Coding

1. 复制SSH密钥。如果您的SSH密钥文件的名称与示例代码的名称不同，请修改文件名以匹配您当前的设置。复制密钥时，请勿添加任何换行符或空格。

   macOS:

   ```
   $ pbcopy < ~/.ssh/id_rsa.pub
   ```

   GNU/Linux (requires the xclip package):

   ```
   xclip -sel clip < ~/.ssh/id_rsa.pub
   ```

   Windows Command Line:

   ```
   type %userprofile%\.ssh\id_rsa.pub | clip
   ```

   Git Bash on Windows / Windows PowerShell:

   ```
   cat ~/.ssh/id_rsa.pub | clip
   ```

   >如果命令行复制不起作用，您可以找到隐藏.ssh文件夹，使用文本编辑器中打开id_rsa.pub文件，复制内容。

2. 在个人设置界面，点击左侧**SSH Keys**页签，进入**SSH Keys**页面，管理你的SSH密钥。

 如果您还未添加SSH密钥，可以点击**新建SSH Key**按钮，填写密钥标题和key值，添加SSH密钥。如下图：
![img](http://devops-minio.jdcloud.com/doc-image/All-Image/personal.assets/ssh_new.jpg)

#### 验证SSH的连通性

测试连接时，您需要使用密码验证此操作，密码是您之前创建的SSH密钥密码。

1. 打开你的终端窗口。
2. 使用以下命令：

```
$ ssh -vT {coding服务域名}
# Attempts to ssh to Coding
```

可能会常出现以下提示信息：

```
> debug1: Authentication succeeded (publickey).
> Authenticated to {coding服务域名}.
> debug1: channel 0: new [client-session]
> debug1: Entering interactive session.
> debug1: pledge: network
> debug1: Sending environment.
> debug1: Sending env LANG = zh_CN.UTF-8
> shell request failed on channel 0
```

>[说明:]
>表示使用ssh的方式，连通性已经验证通过:
>`Authenticated to {coding服务域名}.`
>由于server端限制了`shell request`的操作，故会看到如下报错信息（**可忽略该报错信息**）：
>`shell request failed on channel 0 `

### 个人API Token

 在个人设置界面，点击左侧**API Tokens**页签，进入**个人API Token**页面，管理你的API Tokens，你可以在该界面新增创建新的API Token，也可以将原有的Token删除。

>[说明:]
>
>1. 你生成的API Token 可以用来访问Coding Open API。
>2. API Token的访问权限与你的账号权限一致。
>3. 生成Token后，确保已保存该Token值，否则页面刷新后，将无法获取该Token值。

如果您还未添加API Token密钥，可以点击**生成API Token**按钮，填写标题，生成新的API Token。如下图：

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/personal.assets/api_token_new.jpg)

### 个人 Http Password

 在个人设置界面，点击左侧 **Http Password** 页签，管理你的仓库密码，用来下载和提交代码。

>![image-20220304143903112](http://devops-minio.jdcloud.com/doc-image/All-Image/personal.assets/image-20220304143903112.png)

