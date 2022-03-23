# describeDomainNames


## 描述
获取某个实例下的所有节点对应的域名信息。

## 请求方式
GET

## 请求地址
https://clickhouse.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:describeDomainNames

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describedomainnames#result)| |
|**requestId**|String| |

<div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**shards**|[Shards[]](describedomainnames#shards)|分片信息|
|**shardNum**|Integer|分片数量|
|**replicaNum**|Integer|副本数|
|**publicDomainName**|String|实例公网域名|
|**internalDomainName**|String|实例内网域名|
<div id="shards">Shards</div>
|名称|类型|描述|
|---|---|---|
|**index**|String|分片名|
|**replicaDomainNames**|String[]|各个副本域名|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
