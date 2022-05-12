# 产品动态
## 2022年

| 功能名称 | 功能描述 | 发布时间 | 相关文档|
| :---------------| :--------------|:------------|:--------
|主机联合搜索优化|支持将空格、tab自动识别为多值分隔符","提高搜索效率，优化用户体验。|2022-04|
|内存优化增强型上线|基于Intel® 第二代傲腾持久内存（BPS），提供高性价比的内存介质。|2022-03|[实例规格类型](https://docs.jdcloud.com/cn/virtual-machines/instance-type-family#user-content-7)
|存量主机支持加入高可用组|通过调整实例所属高可用组功能，可以将一台未加入高可用组的实例添加到高可用组，或者将一台已加入一个高可用组的实例更换到另一个高可用组。|2022-03|[调整高可用组](https://docs.jdcloud.com/cn/virtual-machines/modify-instance-ag)
|云主机支持资源组管理|支持根据资源组ID进行实例资源筛选，列表页可对资源的资源组进行单个或批量变更。|2022-03|[资源组概述](https://docs.jdcloud.com/cn/virtual-machines/resource-group-introduction)
|扩展指标功能上线|可通过官方提供的配置文件样本，配置支持的扩展指标，上报至云监控自定义监控。|2022-01|[自动镜像策略](https://docs.jdcloud.com/cn/virtual-machines/monitoring-overview)
|云主机在线迁移服务上线|在不停机的情况下，将物理服务器或虚拟服务器上的系统、服务程序等从京东云外的环境同步至京东云云主机实例。|2022-01|[在线迁移服务](https://docs.jdcloud.com/cn/virtual-machines/online-migration-overview)

## 2021年

| 功能名称 | 功能描述 | 发布时间 | 相关文档|
| :---------------| :--------------|:------------|:--------
|自动镜像策略上线|支持使用自动镜像策略为实例设置周期性的备份任务，免去定期手动制作私有镜像的运维工作。|2021-11|[自动镜像策略](https://docs.jdcloud.com/cn/virtual-machines/autoimagepolicy)
|新版实例模板创建页灰度上线|新版本在流程引导、配置分类、页面资源搜索加载、信息展示等方面进行了整体优化，在视觉和交互方面同样做了全面提升。|2021-12|[创建实例模板](https://docs.jdcloud.com/cn/virtual-machines/create-instance-template)
|修改实例模板功能上线|支持修改实例模板信息，包括地域、镜像、实例规格、磁盘信息、网络等。|2021-11|[修改实例模板](https://docs.jdcloud.com/cn/virtual-machines/modify-instance-template)
|新版创建页灰度上线|新版本在流程引导、配置分类、页面资源搜索加载、信息展示等方面进行了整体优化，在视觉和交互方面同样做了全面提升。|2021-08|[新版创建页](https://cns-console.jdcloud.com/compute/vm/create)
|突发性能型规格上线|突发性能型实例是一种通过积分机制提供并约束CPU使用的实例规格，适用于平时CPU使用率较低，偶发使用率突增的入门级或轻量级计算场景。|2021-08|[突发性能型实例](https://docs.jdcloud.com/cn/virtual-machines/burst-instance-overview)
|私有镜像导出控制台入口上线|私有镜像导出功能提供控制台操作入口，方便用户操作，功能目前为灰度，如需使用请工单提交申请。|2021-07|[私有镜像导出](https://docs.jdcloud.com/virtual-machines/export-private-image)
|Windows Server 2019 数据中心版 64位 中文版 镜像发布|全地域支持	Windows Server 2019 数据中心版 64位 中文版 镜像，丰富操作系统类型。|2021-07|[镜像类型](https://docs.jdcloud.com/cn/virtual-machines/image-type)
|Ubuntu 20.04 镜像发布|全地域支持Ubuntu 20.04 镜像，丰富操作系统类型。|2021-06|[镜像类型](https://docs.jdcloud.com/cn/virtual-machines/image-type)
|修改云主机私有网络配置功能上线|若创建实例时选错VPC/子网或在与其他网络环境打通时存在IP地址冲突，可通过修改网络配置功能调整实例的内网IP地址，进而实现网络的重新规划。|2021-04|[修改私有网络配置](https://docs.jdcloud.com/cn/virtual-machines/modify-vpc-attribute)|
|实例抵扣券调整配置功能上线|无资源预留型抵扣券支持调整规格族和计算力，资源预留型抵扣券支持调整可用区、规格和数量。|2021-04|[调整实例抵扣券配置](https://docs.jdcloud.com/cn/virtual-machines/resize-instancevoucher)
|资源预留型实例抵扣券产品上线|实例抵扣券是计算实例的另一种付费购买方式，以接近包年包月计费的价格按月/年预付费购买抵扣券后，用于按配置计费的计算实例（云主机实例、容器实例、POD实例）费用抵扣。|2021-04|[实例抵扣券](https://docs.jdcloud.com/cn/virtual-machines/instancevoucher-overview)
|云主机事件服务上线|云主机事件是对接云事件服务，提供的一类系统事件通知功能。事件是针对资源生命周期中平台底层基础设施维护、资源重要属性变更等所发送的一类统一格式的通知。基于事件用户可及时获知资源动态，完善云上业务的自动化运维和监控流程。|2021-03|[事件服务](https://docs.jdcloud.com/cn/virtual-machines/event-overview)
|云主机元数据查询功能上线|实例元数据（metadata）是云主机实例的基本信息，包括实例id、内/外网IP地址等，用户可在云主机内通过访问元数据服务来查看实例的元数据，以便于针对某些元数据进行实例内部的配置或与外部应用的连接。|2021-01 |[实例元数据](https://docs.jdcloud.com/cn/virtual-machines/instance-metadata)
| CentOS 8.2 镜像发布|全地域支持CentOS 8.2 镜像，丰富操作系统类型。|2021-01|[镜像类型](https://docs.jdcloud.com/cn/virtual-machines/image-type)

## 2020年

| 功能名称 | 功能描述 | 发布时间 | 相关文档|
| :---------------| :--------------|:------------|:--------
|元数据metadata查询功能上线|实例元数据是云主机实例的基本信息，包括实例id、内/外网IP地址等，用户可在云主机内通过访问元数据服务来查看实例的元数据，以便于针对某些元数据进行实例内部的配置或与外部应用的连接	|2020-12|[实例元数据](https://docs.jdcloud.com/cn/virtual-machines/instance-metadata)
|云主机支持SSH密钥绑定/解绑|支持云主机创建后按需绑定/解绑SSH密钥|2020-12|[绑定密钥](https://docs.jdcloud.com/cn/virtual-machines/bind-keypair)
|自动镜像任务策略上线|可通过自动镜像策略为用户的云主机设置周期性的主机备份任务，此功能可免去用户定期手动为云主机制作镜像的工作，也可避免由于人为疏忽造成的疏漏。|2020-07|[自动镜像策略](https://docs.jdcloud.com/cn/virtual-machines/autoimagepolicy)
|云主机创建时设置云盘快照策略|创建云主机时，用户可根据备份需要，在存储模块中为每块云盘指定快照策略，系统会根据策略自动定期备份用户云盘|2020-07|[创建实例](https://docs.jdcloud.com/cn/virtual-machines/create-instance)
|删除镜像支持删除关联快照|删除私有镜像时，可以选择将镜像关联快照一同删除。|2020-06|[删除镜像](https://docs.jdcloud.com/cn/virtual-machines/delete-private-image)
|无资源预留型实例抵扣券产品上线|实例抵扣券是计算实例的另一种付费购买方式，以接近包年包月计费的价格按月/年预付费购买抵扣券后，用于按配置计费的计算实例（云主机实例、容器实例、POD实例）费用抵扣。|2020-04|[实例抵扣券](https://docs.jdcloud.com/cn/virtual-machines/instancevoucher-overview)
|停机不计费上线|计费方式为按配置且系统盘为云盘的云主机，在停机时可设置为计算资源不计费模式，节省用户开销。|2020-04|[停机不计费](https://docs.jdcloud.com/cn/virtual-machines/uncharged_for_stopped_vm)
|计算优化密集型上线|新增cpu内存比为1:1的计算优化-密集型规格族|2020-04|[实例规格类型](https://docs.jdcloud.com/cn/virtual-machines/instance-type-family)
|第二代共享型云主机上线|提供高性价比的云主机，采用非绑定CPU调度模式，每个vCPU会被分配到任何空闲的超线程核上，不同实例的vCPU可以互相争抢物理CPU资源。	|2020-03|[实例规格类型](https://docs.jdcloud.com/cn/virtual-machines/instance-type-family)
|云主机支持角色（role）创建与使用|可以使用角色对云主机实例进行访问、创建、使用等权限控制管理。	|2020-02|[角色管理](https://docs.jdcloud.com/cn/iam/role-overview)
|GPU虚拟化云主机上线|提供vComputeServer和Quadro vDWS 两种Nvidia虚拟化类型GPU；提供1/2、1/4、1/6三种虚拟化规格的P40卡主机规格|2020-02|[实例规格类型](https://docs.jdcloud.com/cn/virtual-machines/instance-type-family)
|私有镜像导出|支持将用户的私有镜像，以QCOW2的格式导出至与镜像同地域的指定的OSS Bucket中。|2020-01|[镜像导出](https://docs.jdcloud.com/cn/virtual-machines/export-private-image)
|华南-广州地域开放新可用区|华南-广州地域开放新可用区|2020-01|[地域及可用区](https://docs.jdcloud.com/cn/virtual-machines/regions-and-availabilityzones)
|第三代云主机上线|第三代云主机基于京东定制化的第二代英特尔®至强®可扩展处理器 Cascade Lake Gold 6267及Mellanox CX-5智能网卡开发。提供更高性能。|2020-01|[实例规格类型](https://docs.jdcloud.com/cn/virtual-machines/instance-type-family)
|云主机新增监控指标|新增二十余项监控指标。采集粒度更细，支持磁盘、网卡、GPU卡维度相关指标的监控和报警，同时新增平均负载、TCP链接等实例整体指标。|2020-01|[监控](https://docs.jdcloud.com/cn/virtual-machines/monitoring-overview)

## 2019年
| 功能名称 | 功能描述 | 发布时间 | 相关文档|
| :---------------| :--------------|:------------|:--------
|云主机创建支持配置自动续费|云主机控制台创建支持配置自动续费，续费时长同购买时长|2019-12|[创建实例](https://docs.jdcloud.com/cn/virtual-machines/create-instance)
|云盘系统盘主机支持开机状态制作私有镜像|云盘系统盘主机支持开机状态制作私有镜像，无需中断业务|2019=12|[制作私有镜像](https://docs.jdcloud.com/cn/virtual-machines/create-private-image)
| Ubuntu 16.04 镜像发布|全地域支持Ubuntu 18.04 镜像，丰富操作系统类型。|2019-12|[镜像类型](https://docs.jdcloud.com/cn/virtual-machines/image-type)
|存储优化型实例上线|满足自建数据库及大数据集群需求|2019-11|[实例规格类型](https://docs.jdcloud.com/cn/virtual-machines/instance-type-family)
|云主机支持批量编辑标签|支持在云主机列表页批量对至多100台云主机批量编辑，方便用户批量管理资源支持对至多100台云主机批量编辑。|2019-08|[编辑标签](https://docs.jdcloud.com/cn/virtual-machines/edit-tag)
|支持通过镜像ID及实例规格搜索资源|支持通过镜像ID及实例规格搜索云主机资源|2019-08|[查找实例](https://docs.jdcloud.com/cn/virtual-machines/search-instance)
| CentOS 6.6 镜像发布|全地域支持CentOS 6.6 镜像，丰富操作系统类型。|2017-04|[镜像类型](https://docs.jdcloud.com/cn/virtual-machines/image-type)
|私有镜像导入|1. 用户可将本地或其他云环境下所用服务器的系统盘以镜像的形式保存并导入到京东云环境使用；2. 支持RAW、VHD、QCOW2、VMDK四种格式的镜像文件导入，同时提供详尽的镜像制作、格式转换、系统组件安装说明文档；3. 仅支持OpenAPI导入镜像，不提供控制台操作入口|2019-07|[私有镜像导入](https://docs.jdcloud.com/cn/virtual-machines/import-private-image)
|上海地域上线第三可用区|上海地域上线第三可用区|2019-06|[地域及可用区](https://docs.jdcloud.com/cn/virtual-machines/regions-and-availabilityzones)
|实例模版上线|实例模板是京东云提供的创建实例的配置信息模板，包括镜像、实例规格、系统盘及数据盘类型和容量、私有网络及子网配置、安全组及登录信息等。实例模板可用于创建实例或用于配置高可用组，创建高可用组时必须指定实例模板。使用实例模板创建实例时无需重新指定实例模板已包括的参数，缩短部署时间。|2019-05|[实例模版](https://docs.jdcloud.com/cn/virtual-machines/instance-template-overview)
|支持自定义数据|在云主机创建时，用户可以将可执行脚本以指定的数据格式传入实例，实现对实例启动行为的自定义（诸如：下载安装指定软件、开启服务、修改系统配置等）|2019-03|[自定义数据](https://docs.jdcloud.com/cn/virtual-machines/userdata)

## 2018年
| 功能名称 | 功能描述 | 发布时间 | 相关文档|
| :---------------| :--------------|:------------|:--------|
|云主机支持挂载加密云硬盘（公测中）|支持在二代实例规格云主机创建时指定创建并挂载加密云硬盘（空盘支持指定加密属性，基于快照创建则继承快照加密属性）；支持为已经创建的二代实例规格云主机挂载加密云硬盘。公测资格可提交工单申请。|2018-12|[云硬盘加密](https://docs.jdcloud.com/cn/virtual-machines/encryption-of-cloud-disk)|
|新增密钥删除功能|通过控制台创建或导入的SSH公钥支持删除。删除后不影响已用密钥的云主机SSH登录，但如该密钥已被实例模板引用则删除后会导致模板不可用；同时密钥详情中增加公钥指纹信息。|2018-12|[删除密钥](https://docs.jdcloud.com/cn/virtual-machines/delete-keypair)
|云主机支持云硬盘做系统盘|支持使用云硬盘作为用户云主机的系统盘，支持根据需要设置容量 ，同时支持增量快照、跨区复制等功能。|2018-12|[存储概述](https://docs.jdcloud.com/cn/virtual-machines/strorage-overview)
|华东-宿迁上线第二代高频计算云主机|第二代高频计算云主机，适用于高性能Web前端服务器、高性能科学和工程应用及MMO游戏、视频编码等对计算能力有更高要求的场景。|2018-10|[实例规格类型](https://docs.jdcloud.com/cn/virtual-machines/instance-type-family)
|云主机支持自定义列表|控制台云主机列表页支持用户自定义展示信息项，可在多种云主机信息中选择重点关注的信息展示。|2018-06|[查看实例信息](https://docs.jdcloud.com/cn/virtual-machines/query-instance-info)
|云主机支持标签功能|在云主机创建后可为其绑定具有全局属性的标签，可根据标签对云主机进行搜索、筛选，方便用户在云主机数量较多时根据标签快速定位资源。|2018-06|[标签](https://docs.jdcloud.com/cn/virtual-machines/tag-overview)
|Windows Server KMS 服务上线|Windows Server操作系统支持KMS（Key management Service）激活，Windows Server云主机正版激活不再依赖公网网络，在未绑定公网IP的情况下依然可以完成激活。|2018-06|
| Windows Server 2016 镜像发布|全地域支持Windows Server 2016  镜像，丰富操作系统类型。|2018-06|[镜像类型](https://docs.jdcloud.com/cn/virtual-machines/image-type)
|云主机第二代云主机上线|京东云第二代云主机采用最新一代英特尔®至强®可扩展处理器，与上一代产品相比，该处理器综合性能显著提升，每个时钟周期的浮点计算性能提升至原来的2倍，可显著提高工作负载速度。|2018-05|[实例规格类型](https://docs.jdcloud.com/cn/virtual-machines/instance-type-family)
|云主机创建支持基于快照创建数据盘|创建云主机时，支持选择已有快照创建云硬盘并与主机挂载；如所选私有镜像包含数据盘快照信息，会自动按镜像中信息配置数据盘，并支持调整。|2018-03|[创建实例](https://docs.jdcloud.com/cn/virtual-machines/create-instance)
|制作镜像功能升级|制作私有镜像时，除默认对系统盘制作镜像外，支持选择主机当前挂载的部分云硬盘为其制作快照，并在私有镜像中记录数据盘快照的信息，基于此类镜像可快速创建具有相同数据盘配置情况的实例。|2018-03|[制作私有镜像](https://docs.jdcloud.com/cn/virtual-machines/create-private-image)
|多计费方式均支持升/降配|按配置：调整配置后将按照新规格计费，调整前规格会立即出账结算；包年包月：若调配后规格价格低于调配前规格价格，将延长云主机到期时间；若高于调配前规格价格，需要支付当前时间至到期前的差价。|2018-03||[调整配置](https://docs.jdcloud.com/cn/virtual-machines/resize-instance)
|云主机支持指定内网IP创建|指定内网IP功能针对的是云主机主网卡的主内网IP，云主机创建时，内网IP地址可选择由系统自动分配，也可在子网可用IP地址中指定。|2018-03|[创建实例](https://docs.jdcloud.com/cn/virtual-machines/create-instance)
| CentOS 6.9/7.4 镜像发布|全地域支持CentOS 6.9/7.4 镜像，丰富操作系统类型。|2018-02|[镜像类型](https://docs.jdcloud.com/cn/virtual-machines/image-type)
## 2017年
| 功能名称 | 功能描述 | 发布时间 | 相关文档
| :---------------| :--------------|:------------|:--------
|云主机三方镜像发布|云主机新建、重置系统时可直接选择镜像市场中的三方镜像。|2017-12|[镜像类型](https://docs.jdcloud.com/cn/virtual-machines/image-type)
|部分官方CentOS镜像增加epel源|官方CentOS 6.X /7.X系列镜像增加epel源，通过yum命令可直接从epel上获取软件包。|2017-12|[镜像类型](https://docs.jdcloud.com/cn/virtual-machines/image-type)
|云主机单网卡多IP功能发布|云主机支持分配/释放辅助内网IP，且辅助内网IP可绑定弹性公网IP。|2017-12|[分配辅助内网IP](https://docs.jdcloud.com/cn/virtual-machines/assign-secondary-ips)
|上海数据中心盛大开服|上海数据中心采用国际Tier3+建设标准；拥有覆盖主流运营商的优质BPG网络；配备最新一代Intel Xeon CPU；提供7*24小专业服务；可用性达99.995%。|2017-12|[地域及可用区](https://docs.jdcloud.com/cn/virtual-machines/regions-and-availabilityzones)
|弹性计算全线产品支持不同可用区部署|京东云的多可用区基于不同数据中心所构建，是真正意义上电力、网络等物理设施完全隔离的多可用区，可承受机房级别的故障，进一步提升高可用、高可靠。|2017-12|[地域及可用区](https://docs.jdcloud.com/cn/virtual-machines/regions-and-availabilityzones)
|按配置云主机结算周期调整|按配置计费云主机结算周期由原一天调整为一小时，整点结算|2017-09|[计费规则](https://docs.jdcloud.com/cn/virtual-machines/billing-rules)
|云主机购买支持在线支付|控制台购买预付费云主机，在支付环节支持选择在线支付，同时支持选择代金券、余额、在线支付等多种支付方式进行混合支付|2017-09|
|云主机计费模式调整|按配置计费云主机新购、调整配置时，取消原有“预扣24小时费用”规则，调整为先使用后付费模式，只需保证下单时账户余额满足门槛要求即可创建资源。|2017-10|[计费规则](https://docs.jdcloud.com/cn/virtual-machines/billing-rules)
|云主机导出资源列表|支持一键导出云主机列表资源信息，筛选所需内容。|2017-09|
|云主机搜索|支持针对云主机名称及云主机内网IP进行搜索，快速定位所需资源。|2017-06|[查找实例](https://docs.jdcloud.com/cn/virtual-machines/search-instance)
|GPU服务器正式开放申请|GPU服务器基于GPU提供更加高效的计算服务，适用于人工智能、图像处理、深度学习、科学计算等多领域场景。实时高速，提供卓越的并行计算及浮点计算能力。|2017-06|[实例规格类型](https://docs.jdcloud.com/cn/virtual-machines/instance-type-family)
|公网IP支持按使用流量计费|京东云针对业务场景对网络带宽需求整体利用低但变化较大的情况，如平时带宽使用较低但间歇性的出现网络访问高峰的场景，支持用户购买按实际使用流量计费的公网IP。您可根据您的实际业务情况选择合理的计费模式。|2017-05|[公网IP计费规则](https://docs.jdcloud.com/cn/elastic-ip/price-overview)
|海量内存云主机上线|云主机产品线新增海量内存规格：76核1532GB，搭配Intel最新一代处理器，独享底层计算资源，满足对内存容量、内存操作和数据计算速率有较高要求和依赖的应用部署 。|2017-05|[实例规格类型](https://docs.jdcloud.com/cn/virtual-machines/instance-type-family)
| Ubuntu 16.04 镜像发布|全地域支持Ubuntu 16.04 镜像，丰富操作系统类型。|2017-05|[镜像类型](https://docs.jdcloud.com/cn/virtual-machines/image-type)
|京东云内网源正式上线|京东云内网源大幅提升云主机的软件安装效率，降低软件安装成本。|2017-04|
|京东云内网NTP时间服务正式上线|内网NTP为云主机提供内网时间同步，免去用户手动搭建成本。|2017-04|
| CentOS 6.6 镜像发布|全地域支持CentOS 6.6 镜像，丰富操作系统类型。|2017-04|[镜像类型](https://docs.jdcloud.com/cn/virtual-machines/image-type)
|云主机永久降价，降幅高达54%|京东云云主机、云硬盘及弹性公网IP统一降价，最大让利用户。全地域包年包月价格全面下调，最高降价26%。|2017-04|[价格总览](https://docs.jdcloud.com/cn/virtual-machines/price-overview)
| CentOS 7.3 镜像发布|全地域支持CentOS 7.3 镜像，丰富操作系统类型。|2017-04|[镜像类型](https://docs.jdcloud.com/cn/virtual-machines/image-type)
|CentOS 7.2 镜像发布|全地域支持CentOS 7.2 镜像，丰富操作系统类型。|2017-04|[镜像类型](https://docs.jdcloud.com/cn/virtual-machines/image-type)
| 云主机监控支持多监控周期|云主机监控使用户可实时掌握机器运行情况及性能监控指标，多种监控周期长度使用户观测到最长30天的监控信息，获知云主机历史运行状态。| 2017-04 |[监控](https://docs.jdcloud.com/cn/virtual-machines/monitoring-overview)
| CentOS 5.8 镜像发布|全地域支持CentOS 5.8 镜像，丰富操作系统类型。|2017-04|[镜像类型](https://docs.jdcloud.com/cn/virtual-machines/image-type)
| CentOS 7.1 镜像发布|全地域支持CentOS 7.1 镜像，丰富操作系统类型。|2017-04|[镜像类型](https://docs.jdcloud.com/cn/virtual-machines/image-type)
|云主机支持更换镜像及重置系统|重置系统操作可以使云主机恢复至刚启动的状态，是在云主机实例需要操作系统升级或遭遇软件故障时的一种升级或恢复手段。可以选择重置至 Linux 类型系统或者重置至 Windows 类型系统。|2017-04|[重置系统](https://docs.jdcloud.com/cn/virtual-machines/rebuild-instance)
| 包年包月资源支持升级配置|支持用户在购买包年包月云主机计费周期内对CPU及内存进行升级，轻松应对业务扩增。 |2017-04|[调整配置](https://docs.jdcloud.com/cn/virtual-machines/resize-instance)
|安全组上线|安全组是一种分布式、有状态的虚拟防火墙，作用于云主机的网络出口，具备检测和过滤云主机上下行的数据包的功能。使用安全组可以完成云主机网络访问控制，包括云主机之间的东西向流量和云主机与公网通信的南北向流量。|2017-04|[安全组](https://docs.jdcloud.com/cn/virtual-machines/security-group-overview)
| 支持变更按配置计费为成包年包月计费 | 用户前期可购买按配置计费云主机进行测试，根据自身业务规模测试适合的云主机规格，之后即可转为包年包月计费模式，以获得最高性价比。 | 2017-04        |[变更计费类型](https://docs.jdcloud.com/cn/virtual-machines/change-chargemode)
## 2016年
| 功能名称 | 功能描述 | 发布时间 | 相关文档
| :---------------| :--------------|:------------|:--------
| 云主机正式上线             | 云主机是京东云提供的一种云计算基础服务单元，提供处理能力可弹性伸缩的计算服务。包含CPU、内存、操作系统、磁盘、网络、安全等全部所需资源，每种资源都提供多种规格，以满足不同业务的个性化需求。 | 2016-04        |[云主机](https://docs.jdcloud.com/cn/virtual-machines/product-overview)


 
