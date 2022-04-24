# describeBackupPlans


## 描述
查询备份计划概要

## 请求方式
GET

## 请求地址
https://dbs.jdcloud-api.com/v2/regions/{regionId}/backupPlans

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》]|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,∞)。pageNumber为-1时，返回所有数据页码；超过总页数时，显示最后一页|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为10，取值范围：[10,100]，且为10的整数倍|
|**filters**|[Filter[]](describebackupplans#filter)|False| |过滤参数，多个过滤参数之间的关系为“与”(and)<br>支持以下属性的过滤：<br>instanceId, 支持operator选项：eq<br>|

### <div id="filter">Filter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describebackupplans#result)| |
|**requestId**|[String](describebackupplans#result)|请求id|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**totalCount**|Integer| |
|**backupPlans**|[BackupPlan[]](describebackupplans#backupplan)| |
### <div id="backupplan">BackupPlan</div>
|名称|类型|描述|
|---|---|---|
|**backupPlanName**|String|备份计划名称|
|**backupPlanId**|String|备份计划Id|
|**backupPlanStatus**|String|备份计划状态|
|**sourceEngine**|String|源实例引擎类型|
|**createTime**|String|备份计划创建时间, UTC 时间格式|
|**charge**|[Charge](describebackupplans#charge)|计费信息|
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
