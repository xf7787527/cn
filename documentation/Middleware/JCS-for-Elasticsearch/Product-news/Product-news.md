# 产品动态

## 2022年
| 功能名称 | 功能描述 | 发布时间 | 相关文档|
| :---------------| :--------------|:------------|:--------|
|资源组管理|资源组是京东云资源分组管理的工具，支持对云资源进行逻辑分组。通过使用资源组，可实现多项目或多应用场景下的资源分组管理问题。|2022-03|[资源组管理](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/resource-group-introduction)|
|同义词配置|支持将符合规则的同义词文件上传至京东云Elasticsearch集群中，该文件会作用于集群的同义词库，您可以使用更新后的词库搜索数据。|2022-02|[同义词配置](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/synonymdic)|

## 2021年
| 功能名称 | 功能描述 | 发布时间 | 相关文档|
| :---------------| :--------------|:------------|:--------|
|用户数据鉴权|自研认证鉴权功能，支持多用户和角色管理，支持索引级别的鉴权。|2021-09|[用户鉴权](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/auth_introduction)|
|支持本地盘变配|支持本地盘类型实例垂直变配。|2021-06|[变更配置](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/change-es)|
|跨可用区部署|多可用区部署可以提升集群的容灾能力。ES集群可以选择跨双可用区部署或者三可用区部署，集群的数据节点会均匀的分布到您选择的多个多用区中，所部署的数据节点支持可用区感知功能，可使数据的副本分布到多个可用区中，保证单个可用区仅有一份副本，当单个可用区出现故障时，剩余可用区仍然可以不间断的提供服务。|2021-06|[跨可用区部署](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/multiaz-es)|
|智能运维|提供集群、节点、索引等十余个诊断项的健康检测功能。通过智能运维，您可以探测集群潜在风险。同时智能运维系统还会自动归纳集群诊断结果，帮助您掌握集群最新态势，提取关键信息，让开发更便捷|2021-03|[智能运维](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/health_check_introduction)|
|版本6.8/7.9|支持Elasticsearch 版本6.8/7.9。|2021-02|[创建集群](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/create-es)|

## 2020年
| 功能名称 | 功能描述 | 发布时间 | 相关文档|
| :---------------| :--------------|:------------|:--------|
|高级配置|用户可通过集群管理页面修改elasticsearch.yml文件的某些配置，可用于用户进行集群调优。|2020-09|[高级配置](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/configure)|
|周期创建索引|周期创建索引功可以帮助用户实现索引从创建到删除的全生命周期过程的管理。|2020-09|[周期创建索引](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/index)|
|支持本地SSD盘|存储类型支持本地SSD盘。|2020-06|[创建集群](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/create-es)|
|集群重启|支持实例级别重启和节点级别重启两种类型，以及重启和强制重启两种方式，可用于快速解决部分集群问题。|2020-05|[集群重启](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/reboot)|
|数据节点数量缩容|在开启专有主节点的情况下，支持缩减数据节点数量。|2020-05|[变更配置](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/change-es)|
|版本7.x|支持Elasticsearch 版本7.5。|2020-03|[创建集群](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/create-es)|
|实例列表支持导出|集群管理页面支持实例列表导出，便于用户查看当前资源。|2020-01|[查看集群](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/view-es)|
|华南-广州区域|云搜索Elasticsearch正式华南-广州区域。|2020-01||

## 2019年
| 功能名称 | 功能描述 | 发布时间 | 相关文档|
| :---------------| :--------------|:------------|:--------|
|HEAD插件|云搜索Elasticsearch集群实例默认提供Head，用于搜索、查看存放在Elasticsearch索引中的数据。|2019-12|[HEAD插件](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/head)|
|报警模板|报警模板能够帮助用户快速创建和更新报警规则。报警模板分为默认报警模板和自定义报警模板，以便用户设置触发条件时可选择自定义的方式之外，也可以选择模板的方式。|2019-10|[告警规则](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/monitor_rules)|
|支持云盘|存储类型支持性能型SSD云盘、通用型SSD云盘和容量型HDD云盘。|2019-06|[创建集群](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/create-es)|
|版本6.x|支持Elasticsearch 版本6.5/6.7。|2019-04|[创建集群](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/create-es)|
|协调节点|支持设置协调节点来提升集群性能，可以在创建集群或变更配置时创建协调节点。|2019-04|[协调节点](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/coordination_node)|
|拼音插件|支持拼音插件analysis-pinyin。|2019-04|[插件支持](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/ik)|
|专有主节点|支持设置专用主节点来提高集群的稳定性，可以在创建集群或变更配置时创建专有主节点。|2019-03|[专有主节点](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/dedicated-master)|
|数据备份|支持自动备份与恢复、手动备份与恢复，以保证集群数据的可靠性。。|2019-03|[数据备份](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/creatsnapshot)|
|华东-上海区域|云搜索Elasticsearch正式华东-上海区域。|2019-03||
|自定义词库|IK分词插件支持主词库和停用词次数（热更新）。|2019-02|[自定义词库](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/dic)|
|数据备份|支持自动备份与恢复、手动备份与恢复，以保证集群数据的可靠性。|2019-02|[数据备份](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/creatsnapshot)|
|访问控制IAM|访问控制IAM的核心功能主要是用户身份管理与资源访问控制。用户可以通过使用IAM创建、管理子用户，并控制这些子用户访问京东云资源的操作权限。|2019-01|[访问控制](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/control)|
|日志查询|提供通过京东云日志服务提供Elasticsearch日志的查询和展示，日志类型包括主日志、搜索慢日志、索引慢日志、GC日志的查询和展示。|2019-01|[日志查询](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/eslog)|

## 2018年
| 功能名称 | 功能描述 | 发布时间 | 相关文档|
| :---------------| :--------------|:------------|:--------|
|云搜索Elasticsearch正式上线|云搜索Elasticsearch正式上线华北-北京区域。京东云搜索Elasticsearch是基于开源Elasticsearch的分布式全文搜索服务，产品能够提供高可用、易扩展以及近实时的搜索能力，致力于海量数据存储搜索和实时日志分析，旨在为用户提供更稳定、实时、可靠的云搜索服务。|2018-12|[云搜索Elasticsearch](https://docs.jdcloud.com/cn/jcs-for-elasticsearch/product-overview)|
