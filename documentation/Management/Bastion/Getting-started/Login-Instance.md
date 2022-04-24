# 主机运维
当管理员在堡垒机实例中完成资产、用户、运维规则配置后，堡垒机用户可以通过web浏览器方式或终端方式访问已授权主机，进行运维操作。本文将指导运维人员完成运维配置和登录。

## web 浏览器运维

### 操作步骤

1、 IAM子用户可以通过堡垒机控制台页面的，管理 按钮 跳进堡垒机实例。也可以通过在浏览器中输入堡垒机域名，输入用户名和密码，点击“登录”，登录运维堡垒机；

![](/image/Bastion/domain.png) 

![](/image/Bastion/login-ins.png) 

2、 如果用户开启了MFA认证，需要输入MFA安全码，点击“提交”

![](/image/Bastion/mfa.png) 

3、 登录以后，在左侧导航栏选择“主机运维”或者“主机组运维”
![](/image/Bastion/operate22.png) 
 
4、主机运维

4.1	点击“主机运维”，进入主机运维页面，页面显示出所有可运维主机

4.2 选择要运维的主机，点击Linux/Windows账户的下拉框，选择账户，点击“登录”

![](/image/Bastion/operate2.png) 

如果选择的账户是自动登录的，直接登录到主机进行运维操作；

![](/image/Bastion/operate3.png) 

如果选择的账户是手动登录的，页面会提示输入密码，输入密码后按Enter键即可登录到主机进行运维操作。

![](/image/Bastion/operate4.png) 

## SSH 客户端运维

运维人员需要在本地主机安装支持 SSH 协议的工具，如 Xshell、SecureCRT、PuTTY 等。以Xshell为例，介绍SSH协议的运维登录流程。

### 操作步骤

1、 打开Xshell，在连接设置中输入运维堡垒机的ip和端口号（默认22）

![](/image/Bastion/ssh1.png) 

2、 在用户身份验证中输入运维堡垒机的用户名和密码

![](/image/Bastion/ssh2.png) 

3、 点击“连接”，连接运维堡垒机

4、 成功登录运维堡垒机后，进入资产管理界面，界面展示了可运维的主机和主机组（红色为主机组，绿色为主机）

![](/image/Bastion/ssh3.png) 

5、 选择要运维的主机或主机组，输入前面的数字，按Enter键即可显示可以登录主机的账户

![](/image/Bastion/ssh4.png) 

![](/image/Bastion/ssh5.png) 

6、 选择一个账户，输入前面的数字，即可用该账户登录到目标主机进行运维操作

![](/image/Bastion/ssh6.png) 

![](/image/Bastion/ssh7.png) 


