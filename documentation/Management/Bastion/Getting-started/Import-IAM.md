# 导入京东云IAM子用户
在使用堡垒机进行主机运维前，管理员需要在堡垒机实例中创建堡垒机用户。本文将指导管理员在堡垒机实例中导入京东云IAM子用户作为堡垒机用户。除了导入京东云IAM子用户作为堡垒机用户以外，您还可以手动添加或批量导入用户作为堡垒机用户。更多信息，请参见 [用户管理](../Operation-Guide/Administrator/Users/Users.md)。

## 前提条件
* 已经创建IAM子用户。关于创建IAM子用户的具体操作，请参见 [创建IAM用户](../../IAM/Identity-Management/Sub-User.md)。
* 要导入的子账号拥有堡垒机关联权限。

  堡垒机用户权限分为管理员和普通用户两种，对应京东云访问控制的系统权限策略分别是JDCloudBastionHostFullAccess和JDCloudBastionHostOperateOnlyAccess。
  
  京东云主账号登录超级管理员权限，可以查看和管理所有数据。子账号权限由主账号分配，可被分配管理员权限或者普通用户权限。从权限最小的角度，一般建议您为子账号分配普通用户权限，在堡垒机实例中分配运维规则。

  关于为子账号授权的具体操作，请参见为 [给子用户授予策略](../../IAM/Identity-Management/Sub-User.md)。

## 操作步骤

1、完成IAM子账号授权之后，通过堡垒机控制台登录堡垒机实例

2、进入用户—用户管理页面，单击“导入IAM子用户”

![](/image/Bastion/import-iam.png) 

3、在导入IAM子账号对话框中，勾选要导入到实例中的IAM子账号，并单击“确定”按钮
成功将京东云子账号导入到指定的堡垒机实例。
![](/image/Bastion/import-iam1.png) 

