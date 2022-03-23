# describeProgress


## 描述
查询 Clickhouse 集群进度

## 请求方式
GET

## 请求地址
https://clickhouse.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/progress

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**backendProgress**|Integer|False| |是否获取创建域名进度，0不需要，1需要|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeprogress#result)| |
|**requestId**|String| |

<div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**instanceReadyDomain**|Integer|就绪的域名个数|
|**instanceTotalDomain**|Integer|总域名个数|
|**instanceReadyNode**|Integer|就绪的节点个数|
|**instanceTotalNode**|Integer|总节点个数|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
