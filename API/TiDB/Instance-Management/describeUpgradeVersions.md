# describeUpgradeVersions


## 描述
获取TiDB数据库可升级到的版本

## 请求方式
GET

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:describeUpgradeVersions

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeupgradeversions#result)| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**versions**|String[]|当前实例的数据库可升级到的版本，比如4.0.8。 目前仅支持升级到指定的一个版本，暂不提供多个版本让用户选择|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
