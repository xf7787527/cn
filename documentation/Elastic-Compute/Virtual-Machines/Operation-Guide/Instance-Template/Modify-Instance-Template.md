# 修改实例模板

## 前提条件及限制
* 不支持修改实例模板的地域属性，例如实例模板的地域为华南-广州，不可将其地域修改为华北-北京；
* 已绑定高可用组的实例模板不支持修改私有网络。

## 操作步骤
1. 访问 [实例模板控制台](https://cns-console.jdcloud.com/host/launchtemplate/list)，即进入实例模板列表页面。或访问 [京东云控制台](https://console.jdcloud.com) 点击顶部导航栏 **弹性计算-云主机-实例模板** 进入实例模板列表页。
2. 选择地域。
3. 在实例模板列表页选择需要修改的实例模板，点击操作栏的更多-修改实例模板按钮，或点击实例模板名称进入详情页后点击操作-修改实例模板按钮。
4. 若实例模板未绑定高可用组，则支持修改除地域外的所有配置项，配置项可参考 [Linux入门指南-确定配置项](https://docs.jdcloud.com/virtual-machines/select-configuration-linux) 或 [Windows入门指南-确定配置项](https://docs.jdcloud.com/virtual-machines/select-configuration-windows) 进行选择和填写。

>注意：
>* 实例模板服务免费，页面价格显示的是基于此实例模板创建实例的预估费用，实际资源费用请以创建实例时的价格显示为准；
>* 云硬盘“随实例释放”功能和云盘系统盘实例“停机不计费”功能，均仅针对按配置计费实例生效，因此如您在实例模板中开启了此类功能，但使用模板创建了包年包月实例，则参数将不生效。



## 相关参考

[修改实例模板](https://docs.jdcloud.com/cn/virtual-machines/api/updateinstancetemplate?content=API)

[Linux入门指南-确定配置项](https://docs.jdcloud.com/virtual-machines/select-configuration-linux)
 
[Windows入门指南-确定配置项](https://docs.jdcloud.com/virtual-machines/select-configuration-windows)

[实例停机不计费](../Instance/uncharged_for_stopped_vm.md)
