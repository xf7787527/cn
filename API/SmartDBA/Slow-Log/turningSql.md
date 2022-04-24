# turningSql


## 描述
SQL优化

## 请求方式
POST

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/tuningSql

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceGid**|String|True| |实例ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**database**|String|False| |数据库名|
|**sql**|String|False| |SQL语句|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](turningsql#result)| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**tuningAdvice**|[TuningAdvice](turningsql#tuningadvice)|优化结果|
### <div id="TuningAdvice">TuningAdvice</div>
|名称|类型|描述|
|---|---|---|
|**indexAdvice**|String|优化建议|
|**details**|String|诊断情况|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
