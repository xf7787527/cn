# describeExposeType


## 描述
查询k8s集群支持的集群外访问方式

## 请求方式
GET

## 请求地址
https://clickhouse.jdcloud-api.com/v1/regions/{regionId}/vpcs/{vpcId}:describeExposeType

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**vpcId**|String|True| |vpcId|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeexposetype#result)| |
|**requestId**|String| |

<div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**exposeType**|String[]| |

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
