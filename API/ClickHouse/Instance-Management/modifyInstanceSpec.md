# modifyInstanceSpec


## 描述
Clickhouse实例变配

## 请求方式
POST

## 请求地址
https://clickhouse.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:modifyInstanceSpec

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**chNodeClass**|String|False| |clickhouse实例规格|
|**zkNodeClass**|String|False| |zookeeper实例规格|
|**chNodeStorageGB**|Integer|False| |clickhouse实例磁盘大小(GB)|
|**monitorNodeClass**|String|False| |监控实例规格|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](modifyinstancespec#result)| |
|**requestId**|String| |
### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**instanceId**|String| |
|**orderId**|String| |
|**buyId**|String| |

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
