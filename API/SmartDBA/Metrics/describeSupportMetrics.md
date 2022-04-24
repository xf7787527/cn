# describeSupportMetrics


## 描述
查询支持自定义的监控指标

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/supportMetrics

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**panelType**|String|True| |展示类型，取值为： real_time 表示实时监控页面支持的自定义类型, monitor 表示性能趋势页面支持的类型, market 表示监控大盘|
|**dbType**|String|True| |数据库库类型，目前只支持MySQL|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describesupportmetrics#result)| |
|**requestId**|String|请求id|


### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**sys**|[SupportMetric[]](describesupportmetrics#supportmetric)|资源监控|
|**server**|[SupportMetric[]](describesupportmetrics#supportmetric)|MySQL server 监控|
### <div id="SupportMetric">SupportMetric</div>
|名称|类型|描述|
|---|---|---|
|**id**|String|指标对应的id，用来修改监控项传递给后端使用的参数|
|**name**|String|监控项中文名|
|**metric**|String|指标项英文名，用来从后端获取具体指标结果的参数|
|**calculateUnit**|String|单位|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
