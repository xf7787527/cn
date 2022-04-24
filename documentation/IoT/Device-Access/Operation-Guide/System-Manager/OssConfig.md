对象存储配置

支持自定义配置对象存储服务，平台可通过安全通道向设备提供访问的安全凭证

## 创建对象存储对象

在物管平台左侧导航栏选择**系统配置-对象存储配置**，在页面右上方创建对象存储，进行创建。

![创建配置](../../../../../image/IoT/Device-Access/System-Manager/Create.png)

![创建配置2](../../../../../image/IoT/Device-Access/System-Manager/Create2.png)

- EndPoint：OSS访问域名，必填项。
- Bucket：存储空间，必填项。
- AccesKeyId | AccessKeySecret：用户访问对象存储服务的身份标识, 可登录京东云-用户中心进行创建，必填项。
- 描述：对象存储配置的描述，非必填项。

## 编辑对象存储对象

在对象存储配置页面点击要编辑的配置对应的编辑按钮，进入配置编辑页面，可修改EndPoint、Bucket、AccesKeyId、AccessKeySecret、描述等信息。 
![编辑配置](../../../../../image/IoT/Device-Access/System-Manager/Edit.png)

修改完成后可点击测试按钮进行测试，平台根据安全凭证访问修改后的对象存储地址是否可用，点击保存按钮完成修改。

## 删除对象存储对象

在对象存储配置页面点击要删除的配置对应的删除按钮，弹出确认删除框，点击删除。

![删除配置](../../../../../image/IoT/Device-Access/System-Manager/Delete.png)
