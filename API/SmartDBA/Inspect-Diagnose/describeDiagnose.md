# describeDiagnose


## 描述
获取诊断记录

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/diagnoses/{diagnoseId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceGid**|String|True| |RDS 实例ID，唯一标识一个RDS实例|
|**diagnoseId**|String|True| |诊断任务id|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describediagnose#result)| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**status**|String|巡检状态描述，取值 complete 或者 fail。如遇到云监控或者RDS服务异常，会出现fail。可提示用户诊断失败，请稍后重试。|
|**data**|[DiagnoseDetail](describediagnose#diagnosedetail)| |
### <div id="DiagnoseDetail">DiagnoseDetail</div>
|名称|类型|描述|
|---|---|---|
|**message**|String|诊断结果一句话描述|
|**score**|[DiagnoseScore](describediagnose#diagnosescore)| |
|**general**|[DiagnoseGeneral](describediagnose#diagnosegeneral)| |
|**metrics**|[DiagnoseMetric](describediagnose#diagnosemetric)| |
### <div id="DiagnoseMetric">DiagnoseMetric</div>
|名称|类型|描述|
|---|---|---|
|**data**|[DiagnoseMetricItem[]](describediagnose#diagnosemetricitem)|实时性能、慢查询、会话等信息|
### <div id="DiagnoseMetricItem">DiagnoseMetricItem</div>
|名称|类型|描述|
|---|---|---|
|**name**|String|名称|
|**result**|String|诊断结果，正常or异常|
|**message**|String|诊断缘由|
|**rows**|String[]|诊断明细|
### <div id="DiagnoseGeneral">DiagnoseGeneral</div>
|名称|类型|描述|
|---|---|---|
|**data**|[DiagnoseGeneralItem[]](describediagnose#diagnosegeneralitem)|可用性、可靠性、可维护性等信息|
### <div id="DiagnoseGeneralItem">DiagnoseGeneralItem</div>
|名称|类型|描述|
|---|---|---|
|**name**|String|名称|
|**result**|String|诊断结果，正常or异常|
|**message**|String|诊断缘由|
### <div id="DiagnoseScore">DiagnoseScore</div>
|名称|类型|描述|
|---|---|---|
|**time**|String|诊断时间|
|**score**|Integer|分值|
|**message**|String|一共发现N个问题|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
