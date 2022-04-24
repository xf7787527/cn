# checkTableTypes


## 描述
查询支持诊断的类型

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/checkTableTypes

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceGid**|String|True| |实例ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](checktabletypes#result)| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[Table[]](checktabletypes#table)|数据|
### <div id="Table">Table</div>
|名称|类型|描述|
|---|---|---|
|**typeId**|Long|诊断类型id|
|**title**|String|诊断名称|
|**message**|String|问题与建议|
|**note**|String|其他信息提示，如："mysql 5.5 5.6 mariadb不支持"|
|**formHeader**|[Point[]](checktabletypes#point)|受影响表 表头|
|**count**|Long|问题数量|
### <div id="Point">Point</div>
|名称|类型|描述|
|---|---|---|
|**row**|String|列英文名|
|**rowName**|String|列中文名|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
