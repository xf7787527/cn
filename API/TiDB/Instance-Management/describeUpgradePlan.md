# describeUpgradePlan


## 描述
查询TiDB数据库的升级计划

## 请求方式
GET

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:describeUpgradePlan

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeupgradeplan#result)| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**newVersion**|String|升级后的新版本|
|**upgradeTime**|String|计划开始升级的时间|
|**status**|String|任务状态 - 未开始 - 进行中 - 失败|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
