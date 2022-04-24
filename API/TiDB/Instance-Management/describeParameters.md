# describeParameters


## 描述
查看TiDB实例的配置参数

## 请求方式
GET

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/parameters

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeparameters#result)| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**parameters**|[DescribeParam[]](describeparameters#describeparam)| |
### <div id="describeparam">DescribeParam</div>
|名称|类型|描述|
|---|---|---|
|**name**|String|参数名称|
|**description**|String|参数的描述|
|**nodeType**|String|参数的节点类型，包括TiKV,TiDB,PD,TiFlash|
|**defaultValue**|String|参数的默认数值|
|**currentValue**|String|参数的当前值|
|**needRestart**|Boolean|参数修改是否需要重启生效，大小写敏感 -true:参数需要重启才能生效 -false:参数无需重启生效|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
