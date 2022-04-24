# getTopResourceByMetric


## 描述
最近5分钟(或历史某点5分钟)，top5的资源

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/getTopResource

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**metric**|String|True| |监控指标|
|**endTime**|String|True| |查询时间，格式为：2021-11-11T15:04:05Z|
|**dbType**|String|False| |数据库类型，默认MySQL|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](gettopresourcebymetric#result)| |
|**requestId**|String|请求id|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[MetricResourceModel[]](gettopresourcebymetric#metricresourcemodel)|列表|
### <div id="MetricResourceModel">MetricResourceModel</div>
|名称|类型|描述|
|---|---|---|
|**instanceId**|String|实例id|
|**instanceName**|String|实例名称|
|**engineVersion**|String|数据库版本, 如:MySQL 5.7|
|**instanceClass**|String|实例规格|
|**value**|String|值|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
