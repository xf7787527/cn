# describeParameters


## 描述
查看ClickHouse实例的配置参数。

## 请求方式
GET

## 请求地址
https://clickhouse.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/parameters

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|
|**instanceId**|String|True| |实例ID，唯一标识一个实例|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeparameters#result)| |
|**requestId**|[String](describeparameters#result)|请求id|
### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**parameters**|[InstanceParameter[]](describeparameters#instanceparameter)|参数列表|
### <div id="instanceparameter">InstanceParameter</div>
|名称|类型|描述|
|---|---|---|
|**name**|String|参数名称|
|**description**|String|参数的描述|
|**currentValue**|String|参数的当前值，但不一定生效，需要视该参数生效是否需要重启|
|**defaultValue**|String|参数默认值|
|**needRestart**|Boolean|是否需要重启|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
