# 实例FAQ

## 购买相关问题

### 实例购买时的各种参数如何选择？
配置参数详细说明请参考 [Linux系统-确定配置项](https://docs.jdcloud.com/virtual-machines/select-configuration-linux) 和 [Windows系统确定配置项](https://docs.jdcloud.com/virtual-machines/select-configuration-windows)。

### 不同实例规格有什么差别？
不同实例通过其规格分类及具体规格来标识相应的计算、内存、存储及网络能力，同类型实例规格内提供不同代系的规格，不同代系间处理器型号、底层服务器及组网方式或有不同，一般同系列机器代系越高性能越好。详细规格信息可见[实例规格类型](https://docs.jdcloud.com/cn/virtual-machines/instance-type-family),实例规格间主要有如下差异：

### 不同地域下同一种实例规格价格一样么？
不同地域下同一种实例规格价格可能不同，您可查阅 [价格总览](https://docs.jdcloud.com/cn/virtual-machines/price-overview) ，最终价格请以实际创建时页面显示的价格为准。

### 包年包月和按配置两种计费类型有何差别？
- 包年包月为预付费方式，您需提前支付数月或数年的费用，目前购买时间段支持1个月~9个月、1年、2年及3年；费用在您创建实例时一次性扣除；
- 按配置计费为后付费方式，根据实例的实例规格按其实际使用时长计费，统计时间精确到秒，可根据业务需要随时创建和释放资源，无需预先扣除费用，但须确保账户内有足够金额用以支付。<br>

详细区别请参考 [计费规则](https://docs.jdcloud.com/cn/virtual-machines/billing-rules)。

### 按配置计费实例购买后如果使用不足1小时如何收费？
按配置计费实例按秒计费，正常使用情况下每整点时刻进行费用结算；如删除实例则按实际使用时长精确到秒计费。

### 购买实例时需要的规格售罄了怎么办？
- 更换配置接近的其他可售实例规格
- 更换可用区或地域
- 若以上方式无法满足需求，请提交工单或联系客服咨询恢复可售时间

### 实例购买后未创建成功，是否会收取费用？
不会收取费用，对于包年包月计费的云主机已付款项会原渠道返还，对于按配置计费的云主机由于是后付费模式，创建失败不会产生收取费用。

### 一次性购买多台实例如何获知是否全部创建成功？
建议通过系统事件获知，订阅云主机异常事件中的"实例创建失败"事件，若有实例创建失败，系统会发信息至您指定的事件目的地。详细请参考 [实例事件](https://docs.jdcloud.com/virtual-machines/event-overview)。


## 实例使用问题

### 实例购买后能否调整地域和可用区？
不可调整，但您可通过制作镜像在目标可用区或地域创建新的实例，制作镜像详细内容可见[基于实例创建私有镜像](https://docs.jdcloud.com/cn/virtual-machines/create-private-image)；若您需跨地域创建实例，需将制作好的镜像复制到目标地域，具体内容可见[复制镜像](https://docs.jdcloud.com/cn/virtual-machines/copy-image)。

### 是否支持为实例添加声卡？
不支持。

### 购买实例后如何备案域名？
如您购买了京东云服务器（有效期必须为3个月以上的包年/包月类型），且域名有使用备案的需求，即可使用备案服务备案域名，备案相关内容参见[备案介绍](https://docs.jdcloud.com/cn/icp-license-service/introduction)。

### 实例到期或欠费后会如何处理？
当包年包月实例到期或按配置计费实例欠费后，京东云会停止该实例的服务，将其置为已停止状态，停止后实例将保留7天，7天后若未续费或充值平账实例将被删除；若您需重启动该部分实例，可见文档[重启动到期／欠费实例](https://docs.jdcloud.com/cn/virtual-machines/restart-overdue-or-arrear-instance)

### 按配置实例欠费后还会继续产生费用么？
不会。在实例欠费系统强制停机后，将不会继续产生使用费用，同时在充值偿还欠款前实例将无法开机。须注意的是，若实例的停机不计费策略选为“是”，则欠费实停机后，其vCPU、内存、GPU将被释放，本地数据盘数据将被清空。

### 如何测试实例性能？
Linux实例测试方法可见[Linux实例基准性能测试方法](https://docs.jdcloud.com/cn/virtual-machines/product-overview)，主要介绍如何对Linux实例进行CPU、内存的基准性能测试。

### 实例能否防御网络攻击？
京东云为您提供高达2G的DDoS基础防护，该服务免费使用，当您购买云内公网IP之后，京东云将免费为您开通；DDOS基础防护服务支持多种DDoS攻击防御：对流量特征进行精确识别，能够有效抵御SYN Flood、UDP Flood、ACK Flood、ICMP Flood等各种常见DDoS攻击。
京东云还提供了提升DDoS攻击防护能力的DDOS防护包，该服务提供最大50G的防御能力，保障您的业务稳定；您可根据自身需求，在基础防护免费2G带宽的基础上平滑升级。

### Windows Server实例是否需要单独激活？
不需要。若您的Windows Server实例通过京东云提供的官方镜像创建，则无需单独激活，实例启动后将自动激活并定期续约。

### 是否支持自定义实例用户名？
不支持。Linux系统默认为“root”，Windows系统默认为“Administrator”。

### 如何查看实例及相关资源的数量和配额？
可通过 [控制台概览页](https://console.jdcloud.com/overview) 查看各地域下资源的配额及数量。

### 内存优化增强型实例有什么特点？
内存优化增强型提供的内存混合了普通内存与傲腾持久内存，配备高至2T的大容量内存，且价格相对普通内存更低，具有较高的性价比；但其访问速度会低于普通内存，建议您在正式搭建业务前进行充分测试。该规格族的傲腾内存仅支持作为内存使用，不支持配置为本地盘。

### 内存优化增强型实例的内存具有持久性吗？
该规则族的内存暂不具备持久性，后续将上线具备持久化能力的规格族，敬请期待。

### 内存优化增强型实例的傲腾内存支持自主配置为内存或本地盘吗
不支持。该规格族的傲腾内存仅支持作为内存使用，且无需您二次配置。

### 内存优化增强型实例对操作系统有要求吗？
无要求。


## GPU实例问题

### GPU实例支持哪些监控指标，如何查看？
除实例基础监控外，GPU实例提供：功耗、温度、核心使用量、编码器使用率、解码器使用率、内存使用率和内存使用量几项指标，更多监控项内容详见 [监控概述](https://docs.jdcloud.com/cn/virtual-machines/monitoring-overview)。
实例监控数据查询可在实例详情页或云监控侧查看，详见 [获取监控数据](https://docs.jdcloud.com/cn/virtual-machines/get-monitor-data)。

### GPU实例支持配置停机不计费么？
支持。若您的GPU实例计费方式为按配置计费且系统盘为云硬盘，则支持配置停机不计费；选择停机不计费并成功停止后的实例，其vCPU、内存、GPU资源将释放，本地数据盘数据将被清空，实例计费将暂停，但实例关联的资源如云硬盘、弹性公网IP仍然计费。

### GPU实例可以保持GPU配置调整CPU或内存么？
不可以，GPU实例规格中GPU与CPU、内存、本地存储为固定搭配，请综合考虑选择适合您业务的GPU实例规格。

### GPU实例驱动如何安装？
您在京东云购买的GPU实例均未安装GPU驱动。
- 直通型GPU规格，可根据实例的操作系统版本、GPU卡类型、语言要求等前往GPU卡厂商官方网站下载对应驱动安装，安装方法请参考 [GPU实例下载并安装GPU驱动](https://docs.jdcloud.com/cn/virtual-machines/gpu-vm)。
- 虚拟化型GPU规格，请参考 [vGPU实例使用说明](https://docs.jdcloud.com/cn/virtual-machines/vgpu-vm) 根据镜像类型使用京东云提供的驱动。
### 虚拟化型GPU实例是否提供license？
不提供。虚拟化型(vGPU)规格须根据虚拟化模式购买不同类型的License，并自行搭建License Server，详细说明请参考 [vGPU实例使用说明](https://docs.jdcloud.com/cn/virtual-machines/vgpu-vm)。

## 存储优化型实例问题

### 存储优化型实例支持配置停机不计费么？
支持。若您的存储优化型实例计费方式为按配置计费且系统盘为云硬盘，则支持配置停机不计费；选择停机不计费并成功停止后的实例，其vCPU、内存、资源将释放，本地数据盘数据将被清空，实例计费将暂停，但实例关联的资源如云硬盘、弹性公网IP仍然计费。

### 存储优化型实例本地盘数据是否支持备份？
不支持。本地数据盘不支持制作快照，故无法备份。本地数据盘为临时存储盘，有丢失数据的风险（比如发生迁移或宿主机宕机等情况），不适用于应用层没有数据冗余架构的使用场景，建议您使用云硬盘存储重要数据并定期备份。

### 存储优化型实例本地数据盘是否提供监控？
提供，对本地数据盘的监控项为磁盘读/写吞吐量和磁盘读/写IOPS；监控项详细内容参见[监控概述](https://docs.jdcloud.com/cn/virtual-machines/monitoring-overview)。


## 相关参考

[镜像FAQ](https://docs.jdcloud.com/cn/virtual-machines/image-faq)

[存储FAQ](https://docs.jdcloud.com/cn/virtual-machines/storage-faq)

[网络FAQ](https://docs.jdcloud.com/cn/virtual-machines/network-faq)



