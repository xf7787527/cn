# 分布式数据库TiDB


## 简介
分布式数据库TiDB


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**addWhiteListGroup**|POST|增加白名单分组。|
|**createAccount**|POST|创建数据库账号，用户可以使用客户端，应用程序等通过该账号和密码登录数据库实例。|
|**createBackup**|POST|创建一个实例全量备份，可以对整个实例所有的数据库进行全量备份。同一时间点，只能有一个正在运行的备份任务|
|**createDataMigration**|POST|查询 TiDB 数据迁移任务的信息|
|**createInstance**|POST|创建一个TiDB实例|
|**createInstanceFromBackup**|POST|根据源实例全量备份创建一个新实例|
|**deleteBackup**|DELETE|删除TiDB的备份，仅允许删除用户生成的备份，系统自动备份不允许删除。|
|**deleteInstance**|DELETE|删除一个TiDB实例|
|**deleteWhiteListGroup**|DELETE|删除白名单分组。|
|**describeAccounts**|GET|查看某个实例下的账号信息|
|**describeAvailableZones**|GET|获取可用区|
|**describeBackupPolicy**|GET|查看实例当前的备份备份策略。|
|**describeBackups**|GET|查看该实例下所有备份的详细信息|
|**describeDataMigration**|GET|查询 TiDB 数据迁移任务的信息|
|**describeInstanceAttributes**|GET|查询 TiDB 实例的详细信息|
|**describeInstanceClasses**|GET|规格获取接口|
|**describeInstances**|GET|查询实例列表|
|**describeNodes**|GET|获取某个实例下的节点信息|
|**describeOrderableInstanceType**|GET|获取当前用户售罄信息|
|**describeParameters**|GET|查看TiDB实例的配置参数|
|**describeUpgradePlan**|GET|查询TiDB数据库的升级计划|
|**describeUpgradeVersions**|GET|获取TiDB数据库可升级到的版本|
|**describeVersions**|GET|获取TiDB产品提供的所有版本|
|**describeWhiteList**|GET|查看实例当前白名单。白名单是允许访问当前实例的IP/IP段列表，缺省情况下，白名单对本VPC开放。如果用户开启了外网访问的功能，还需要对外网的IP配置白名单。|
|**modifyBackupPolicy**|POST|修改TiDB实例备份策略。|
|**modifyInstanceName**|POST|修改实例名称，可支持中文，实例名的具体规则可参见帮助中心文档|
|**modifyInstanceSpec**|POST|修改实例规格，包含节点的水平扩容与垂直扩容|
|**modifyNodeNum**|POST|增加实例的节点数量。|
|**modifyParameters**|PUT|修改TiDB实例的配置参数。部分参数修改后，需要重启才能生效，具体可以参考PingCAP的相关文档|
|**modifyWhiteList**|PUT|修改允许访问实例的IP白名单。白名单是允许访问当前实例的IP/IP段列表，缺省情况下，白名单对本VPC开放。如果用户开启了外网访问的功能，还需要对外网的IP配置白名单。|
|**rebootPod**|POST|重启实例的pod|
|**resetPassword**|POST|创建数据库账号，用户可以使用客户端，应用程序等通过该账号和密码登录RDS数据库实例。|
|**upgradeEngineVersion**|POST|升级TiDB引擎版本，例如从4.0.6 升级到4.0.8. 目前支持小版本的升级，可升级到平台支持的最新的小版本|
|**verifyFilefromOSS**|POST|校验需要导入的备份文件在OSS上是否存在，需要的读取权限是否具备|
