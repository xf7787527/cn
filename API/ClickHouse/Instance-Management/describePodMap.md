# describePodMap


## 描述
查看实例当前的备份备份策略。

## 请求方式
GET

## 请求地址
https://clickhouse.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:describePodMap

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describepodmap#result)| |
|**requestId**|String| |

<div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**podIds**|String[]|POD ID的列表|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
