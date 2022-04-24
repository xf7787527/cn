# describeDiagnoseList


## 描述
获取当前实例的所有诊断记录

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/diagnoses

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceGid**|String|True| |RDS 实例ID，唯一标识一个RDS实例|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageIndex**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,∞)。pageIndex 为-1时，返回所有数据页码；|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为10，取值范围：[1,100]，用于查询列表的接口|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describediagnoselist#result)| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**totalCount**|Integer|总数|
|**data**|[DiagnoseDetail[]](describediagnoselist#diagnosedetail)|列表|
### <div id="DiagnoseDetail">DiagnoseDetail</div>
|名称|类型|描述|
|---|---|---|
|**message**|String|诊断结果一句话描述|
|**score**|[DiagnoseScore](describediagnoselist#diagnosescore)| |
|**general**|[DiagnoseGeneral](describediagnoselist#diagnosegeneral)| |
|**metrics**|[DiagnoseMetric](describediagnoselist#diagnosemetric)| |
### <div id="DiagnoseMetric">DiagnoseMetric</div>
|名称|类型|描述|
|---|---|---|
|**data**|[DiagnoseMetricItem[]](describediagnoselist#diagnosemetricitem)|实时性能、慢查询、会话等信息|
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
|**data**|[DiagnoseGeneralItem[]](describediagnoselist#diagnosegeneralitem)|可用性、可靠性、可维护性等信息|
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
