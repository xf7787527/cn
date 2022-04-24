# 云主机


## 简介
云主机实例、镜像、SSH密钥、实例模板、实例规格类型、配额相关的接口。


### 版本
v1


## 云主机实例
|API|请求方式|功能描述|
|---|---|---|
|[**createInstances**](https://docs.jdcloud.com/cn/virtual-machines/api/createinstances?content=API)|POST|创建云主机。<br>|
|[**startInstance**](https://docs.jdcloud.com/cn/virtual-machines/api/startinstance?content=API)|POST|启动云主机。<br>|
|[**stopInstance**](https://docs.jdcloud.com/cn/virtual-machines/api/stopinstance?content=API)|POST|停止云主机。<br>|
|[**rebootInstance**](https://docs.jdcloud.com/cn/virtual-machines/api/rebootinstance?content=API)|POST|重启云主机。<br>|
|[**modifyInstancePassword**](https://docs.jdcloud.com/cn/virtual-machines/api/modifyinstancepassword?content=API)|POST|修改云主机密码。<br>|
|[**deleteInstance**](https://docs.jdcloud.com/cn/virtual-machines/api/deleteinstance?content=API)|DELETE|删除一台按配置计费、或包年包月已到期的云主机。<br>|
|[**rebuildInstance**](https://docs.jdcloud.com/cn/virtual-machines/api/rebuildinstance?content=API)|POST|为云主机重置系统。<br>|
|[**resizeInstance**](https://docs.jdcloud.com/cn/virtual-machines/api/resizeinstance?content=API)|POST|为云主机变更实例规格。<br>|
|[**describeInstance**](https://docs.jdcloud.com/cn/virtual-machines/api/describeinstance?content=API)|GET|查询一台云主机的详细信息，包括云主机ID、名称、实例规格等。<br>|
|[**describeInstances**](https://docs.jdcloud.com/cn/virtual-machines/api/describeinstances?content=API)|GET|批量查询云主机的详细信息，包括云主机ID、名称、实例规格等。<br>|
|[**modifyInstanceAttribute**](https://docs.jdcloud.com/cn/virtual-machines/api/modifyinstanceattribute?content=API)|POST|修改云主机部分信息，包括云主机名称、描述、自定义元数据等。<br>|
|[**describeInstanceStatus**](https://docs.jdcloud.com/cn/virtual-machines/api/describeinstancestatus?content=API)|GET|批量查询云主机状态。<br>|
|[**describeInstancesCustomData**](https://docs.jdcloud.com/cn/virtual-machines/api/describeinstancescustomdata?content=API)|GET|批量查询云主机用户自定义元数据。<br>|
|[**describeInstanceVncUrl**](https://docs.jdcloud.com/cn/virtual-machines/api/describeinstancevncurl?content=API)|GET|获取云主机VNC，用于连接管理云主机。<br>|
|[**attachDisk**](https://docs.jdcloud.com/cn/virtual-machines/api/attachdisk?content=API)|POST|为云主机挂载云硬盘。<br>|
|[**detachDisk**](https://docs.jdcloud.com/cn/virtual-machines/api/detachdisk?content=API)|POST|为云主机缷载云硬盘。<br>|
|[**modifyInstanceDiskAttribute**](https://docs.jdcloud.com/cn/virtual-machines/api/modifyinstancediskattribute?content=API)|POST|修改云主机挂载的云硬盘属性。<br>|
|[**attachNetworkInterface**](https://docs.jdcloud.com/cn/virtual-machines/api/attachnetworkinterface?content=API)|POST|为云主机绑定弹性网卡。<br>|
|[**detachNetworkInterface**](https://docs.jdcloud.com/cn/virtual-machines/api/detachnetworkinterface?content=API)|POST|为云主机缷载弹性网卡。<br>|
|[**associateElasticIp**](https://docs.jdcloud.com/cn/virtual-machines/api/associateelasticip?content=API)|POST|为云主机绑定弹性公网IP。<br>
|[**disassociateElasticIp**](https://docs.jdcloud.com/cn/virtual-machines/api/disassociateelasticip?content=API)|POST|为云主机解绑弹性公网IP。<br>|
|[**modifyInstanceNetworkAttribute**](https://docs.jdcloud.com/cn/virtual-machines/api/modifyinstancenetworkattribute?content=API)|POST|修改云主机弹性网卡属性，包括弹性网卡ID、是否随云主机一起删除。<br>|
|[**modifyInstanceVpcAttribute**](https://docs.jdcloud.com/cn/virtual-machines/api/modifyinstancevpcattribute?content=API)|POST|修改云主机的子网或内网IP地址。<br>|
|[**modifyInstancePlacement**](https://docs.jdcloud.com/cn/virtual-machines/api/modifyinstanceplacement?content=API)|POST|存量云主机加入高可用组，或者云主机从一个高可用组移动到另一个高可用组。<br>|

## 镜像
|API|请求方式|功能描述|
|---|---|---|
|[**createImage**](https://docs.jdcloud.com/cn/virtual-machines/api/createimage?content=API)|POST|为云主机创建私有镜像。<br>|
|[**deleteImage**](https://docs.jdcloud.com/cn/virtual-machines/api/deleteimage?content=API)|DELETE|删除私有镜像。<br>|
|[**copyImages**](https://docs.jdcloud.com/cn/virtual-machines/api/copyimages?content=API)|POST|复制私有镜像，将私有镜像复制到其它地域下。<br>|
|[**importImage**](https://docs.jdcloud.com/cn/virtual-machines/api/importimage?content=API)|POST|导入私有镜像。<br>|
|[**exportImage**](https://docs.jdcloud.com/cn/virtual-machines/api/exportimage?content=API)|POST|导出私有镜像。<br>|
|[**shareImage**](https://docs.jdcloud.com/cn/virtual-machines/api/shareimage?content=API)|POST|共享私有镜像。<br>|
|[**unShareImage**](https://docs.jdcloud.com/cn/virtual-machines/api/unshareimage?content=API)|POST|取消共享私有镜像。<br>|
|[**convertImage**](https://docs.jdcloud.com/cn/virtual-machines/api/convertimage?content=API)|POST|镜像类型转换。<br>|
|[**describeImage**](https://docs.jdcloud.com/cn/virtual-machines/api/describeimage?content=API)|GET|查询镜像信息，包括镜像名称、ID等。<br>|
|[**describeImages**](https://docs.jdcloud.com/cn/virtual-machines/api/describeimages?content=API)|GET|批量查询镜像信息，包括镜像名称、ID等。<br>|
|[**describeImageMembers**](https://docs.jdcloud.com/cn/virtual-machines/api/describeimagemembers?content=API)|GET|查询私有镜像共享帐户信息。<br>|
|[**imageTasks**](https://docs.jdcloud.com/cn/virtual-machines/api/imagetasks?content=API)|GET|查询镜像导入导出任务信息。<br>|
|[**describeImageConstraints**](https://docs.jdcloud.com/cn/virtual-machines/api/describeimageconstraints?content=API)|GET|查询单个镜像的云主机实例规格限制信息。<br>|
|[**describeImageConstraintsBatch**](https://docs.jdcloud.com/cn/virtual-machines/api/describeimageconstraintsbatch?content=API)|GET|批量查询镜像的云主机实例规格限制信息。<br>|
|[**modifyImageAttribute**](https://docs.jdcloud.com/cn/virtual-machines/api/modifyimageattribute?content=API)|POST|修改镜像信息，包括镜像名称、描述等。<br>|

## SSH密钥
|API|请求方式|功能描述|
|---|---|---|
|[**createKeypair**](https://docs.jdcloud.com/cn/virtual-machines/api/createkeypair?content=API)|POST|创建SSH密钥对。<br>|
|[**deleteKeypair**](https://docs.jdcloud.com/cn/virtual-machines/api/deletekeypair?content=API)|DELETE|删除SSH密钥对。<br>|
|[**attachKeypair**](https://docs.jdcloud.com/cn/virtual-machines/api/attachkeypair?content=API)|POST|为云主机绑定密钥。<br>|
|[**detachKeypair**](https://docs.jdcloud.com/cn/virtual-machines/api/detachkeypair?content=API)|POST|为云主机解绑密钥。<br>|
|[**importKeypair**](https://docs.jdcloud.com/cn/virtual-machines/api/importkeypair?content=API)|POST|导入密钥对。<br>|
|[**describeKeypairs**](https://docs.jdcloud.com/cn/virtual-machines/api/describekeypairs?content=API)|GET|批量查询密钥对。<br>|

## 实例模板
|API|请求方式|功能描述|
|---|---|---|
|[**createInstanceTemplate**](https://docs.jdcloud.com/cn/virtual-machines/api/createinstancetemplate?content=API)|POST|创建实例模板。<br>|
|[**deleteInstanceTemplate**](https://docs.jdcloud.com/cn/virtual-machines/api/deleteinstancetemplate?content=API)|DELETE|删除实例模板。<br>|
|[**describeInstanceTemplate**](https://docs.jdcloud.com/cn/virtual-machines/api/describeinstancetemplate?content=API)|GET|查询单个实例模板信息，包括实例模板ID、名称、描述、详细配置等。<br>|
|[**describeInstanceTemplates**](https://docs.jdcloud.com/cn/virtual-machines/api/describeinstancetemplates?content=API)|GET|批量查询实例模板信息，包括实例模板ID、名称、描述、详细配置等。<br>|
|[**describeInstanceTemplatesCustomdata**](https://docs.jdcloud.com/cn/virtual-machines/api/describeinstancetemplatescustomdata?content=API)|GET|查询实例模板配置的自定义数据，包括自定义脚本和自定义元数据。<br>|
|[**verifyInstanceTemplate**](https://docs.jdcloud.com/cn/virtual-machines/api/verifyinstancetemplate?content=API)|GET|校验实例模板的有效性。<br>|
|[**updateInstanceTemplate**](https://docs.jdcloud.com/cn/virtual-machines/api/updateinstancetemplate?content=API)|PATCH|修改实例模板的信息，包括实例规格、镜像ID、实例密码等。<br>|

## 实例规格类型
|API|请求方式|功能描述|
|---|---|---|
|[**describeInstanceTypes**](https://docs.jdcloud.com/cn/virtual-machines/api/describeinstancetypes?content=API)|GET|查询实例规格信息，包括实例规格族、实例规格代数、实例规格等。<br>|

## 配额
|API|请求方式|功能描述|
|---|---|---|
|[**describeQuotas**](https://docs.jdcloud.com/cn/virtual-machines/api/describequotas?content=API)|GET|查询配额。<br>|
