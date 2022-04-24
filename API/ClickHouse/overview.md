# 分布式数据库Clickhouse


## 简介
分布式数据库Clickhouse


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**addWhiteListGroup**|POST|增加白名单分组。|
|**azs**|GET|获取当前用户可用的可用区|
|**createAccount**|POST|创建一个Clickhouse账号|
|**createInstance**|POST|创建一个Clickhouse实例|
|**deleteAccount**|DELETE|删除一个Clickhouse实例|
|**deleteInstance**|DELETE|删除一个Clickhouse实例|
|**deleteWhiteListGroup**|DELETE|删除白名单分组。|
|**describeAccounts**|GET|查询 Clickhouse account列表信息|
|**describeAuditResult**|GET|查询 Clickhouse audit列表信息|
|**describeDefaultConfig**|GET|查询 Clickhouse 推荐规格|
|**describeDomainNames**|GET|获取某个实例下的所有节点对应的域名信息。|
|**describeInstanceAttributes**|GET|查询 Clickhouse 实例的详细信息|
|**describeInstances**|GET|查询实例列表|
|**describeNodeClasses**|GET|查询 node 可用规格|
|**describeNodes**|GET|查询 Clickhouse 节点信息|
|**describeParameters**|GET|查看Clickhouse实例的配置参数。|
|**describePodMap**|GET|查看实例当前的备份备份策略。|
|**describeProgress**|GET|查询 Clickhouse 集群进度|
|**describeSlowlogResult**|GET|查询 Clickhouse audit列表信息|
|**describeWhiteList**|GET|查看实例当前白名单。白名单是允许访问当前实例的IP/IP段列表，缺省情况下，白名单对本VPC开放。如果用户开启了外网访问的功能，还需要对外网的IP配置白名单。|
|**disableInternetAccess**|POST|关闭实例的外网访问功能。|
|**enableInternetAccess**|POST|开启实例的外网访问功能。|
|**internalDescribeInstance**|GET|内部查询实例状态|
|**modifyInstanceName**|POST|修改实例名称。|
|**modifyInstanceSpec**|POST|Clickhouse实例变配|
|**modifyParameters**|PUT|提交并修改实例的配置参数。 参数修改后，需要重启才能生效。|
|**modifyPrivilege**|POST|修改账号权限|
|**modifyWhiteList**|PUT|修改允许访问实例的IP白名单。白名单是允许访问当前实例的IP/IP段列表，缺省情况下，白名单对本VPC开放。如果用户开启了外网访问的功能，还需要对外网的IP配置白名单。|
|**orderableInstanceType**|GET|获取当前用户售罄信息|
|**resetPassword**|POST|重置数据库账号密码|
|**selectDetailList**|GET|根据实例的的id，获取实例相关信息。|
|**upgradeEngineVersion**|POST|集群版本升级。|
