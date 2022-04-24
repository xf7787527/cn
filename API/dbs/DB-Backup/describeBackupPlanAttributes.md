# describeBackupPlanAttributes


## 描述
查询备份计划详细信息

## 请求方式
GET

## 请求地址
https://dbs.jdcloud-api.com/v2/regions/{regionId}/backupPlans/{backupPlanId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》]|
|**backupPlanId**|String|True| |备份计划ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describebackupplanattributes#result)| |
|**requestId**|[String](describebackupplanattributes#result)|请求id|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**backupPlanAttributes**|[BackupPlanAttributes](describebackupplanattributes#backupplanattributes)| |
### <div id="backupplanattributes">BackupPlanAttributes</div>
|名称|类型|描述|
|---|---|---|
|**backupPlanName**|String|备份计划名称|
|**backupPlanId**|String|备份计划Id|
|**backupPlanStatus**|String|备份计划状态|
|**errorMessages**|String|备份计划状态原因，仅状态为ERROR时返回；其他状态时返回空字符串|
|**sourceEngine**|String|源实例引擎类型|
|**servicePackage**|String|DBS服务包类型是枚举值， dbs.common.package 表示基础服务包，不含备份流量|
|**createTime**|String|备份计划创建时间, UTC 时间格式|
|**charge**|[Charge](describebackupplanattributes#charge)|计费信息|
|**backupType**|String|备份方式|
|**enableBackupLogs**|Boolean|是否开启日志备份；true：开启；false：关闭|
|**logBackupRetentionPeriod**|Integer|日志备份保存天数，支持7-3650 天，默认7天|
|**fullBackupRetentionPeriod**|Integer|全量备份保存天数，支持7-3650 天，默认7天|
|**fullBackupSchedule**|[BackupSchedule](describebackupplanattributes#backupschedule)|全量备份的备份周期|
|**sourceEndpoint**|[SourceEndpoint](describebackupplanattributes#sourceendpoint)|备份目标的详细信息|
|**backupObjects**|[BackupObjects](describebackupplanattributes#backupobjects)|逻辑备份中要备份的对象的信息，物理备份无须该信息|
### <div id="backupobjects">BackupObjects</div>
|名称|类型|描述|
|---|---|---|
|**database**|String|数据库名称|
|**objects**|String[]|表名, 如果不填或者为空，表示对整个数据库进行备份|
### <div id="sourceendpoint">SourceEndpoint</div>
|名称|类型|描述|
|---|---|---|
|**networkType**|String|源数据库的网络类型 PublicAccess 和 RDS|
|**port**|Integer|源数据库的端口|
|**backupAgentId**|String|备份代理的ID，仅初始化时可设置，设置完成并开始备份后，不可修改|
|**accountName**|String|源数据库的账号|
|**password**|String|源数据库的密码|
|**engineRelatedConfig**|[EngineRelatedConfig](describebackupplanattributes#enginerelatedconfig)|不同数据库引擎独有的配置参数|
### <div id="enginerelatedconfig">EngineRelatedConfig</div>
|名称|类型|描述|
|---|---|---|
|**myconfPath**|String|MySQL数据库配置文件路径|
### <div id="backupschedule">BackupSchedule</div>
|名称|类型|描述|
|---|---|---|
|**period**|String|周期类型，目前仅支持weekly|
|**days**|Integer[]|进行全量备份的日期, 备份周期为 weekly 时可以取 0-6 分别对应的是周日到周六|
|**startTime**|String|全量备份的开始时间，精确到分,UTC时间格式，例如：23:30Z|
### <div id="charge">Charge</div>
|名称|类型|描述|
|---|---|---|
|**chargeMode**|String|计费模式枚举值prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration|
|**chargeStatus**|String|计费状态，取值为 normal表示正常，overdue表示预付费已到期，arrear表示欠费|
|**chargeStartTime**|String|计费开始时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|
|**chargeExpiredTime**|String|过期时间，预付费资源的到期时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ，后付费资源此字段内容为空|
|**chargeRetireTime**|String|预期释放时间，资源的预期释放时间，预付费/后付费资源均有此值，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
