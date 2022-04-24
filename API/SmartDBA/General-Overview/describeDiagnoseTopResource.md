# describeDiagnoseTopResource


## 描述
获取一键诊断分数最低的top5

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/diagnoseTopResource

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**endTime**|String|True| |查询时间，格式为：2021-11-11T15:04:05Z|
|**dbType**|String|False| |数据库类型，默认MySQL|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describediagnosetopresource#result)| |
|**requestId**|String|请求id|


### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[InspectTopResource[]](describediagnosetopresource#inspecttopresource)|列表|
### <div id="InspectTopResource">InspectTopResource</div>
|名称|类型|描述|
|---|---|---|
|**score**|Long|诊断分值|
|**instanceId**|String|实例id|
|**instanceName**|String|实例名称|
|**instanceClass**|String|实例规格|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
