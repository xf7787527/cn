# getWafInstance


## 描述
获取实例ID及相关信息列表

## 请求方式
GET

## 请求地址
https://waf.jdcloud-api.com/v1/regions/{regionId}/user:getWafInstance

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**idc**|String|False| |所属地区， 模糊匹配|
|**pageNumber**|Integer|False|1|页码|
|**pageSize**|Integer|False|10|分页大小|
|**filters**|[Filter[]](getwafinstance#filter)|False| |wafInstanceId - 实例id|
|**sourceIds**|String|False| |资源id 多个时，以逗号,分隔。|
|**content-language**|String|True| |语言，"en":英文，"zh":中文|

### <div id="filter">Filter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](getwafinstance#result)| |
|**requestId**|String|此次请求的ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**total**|Integer|总个数。|
|**instanceIdCfg**|[InstanceIdCfg[]](getwafinstance#instanceidcfg)|实例ID及相关信息列表|
### <div id="instanceidcfg">InstanceIdCfg</div>
|名称|类型|描述|
|---|---|---|
|**instanceId**|String|实例id|
|**nickName**|String|实例id别称|
|**packageType**|Integer|套餐类型 0:内测版，1:高级版， 2:企业版 3:旗舰版|
|**region**|String|地域信息|
|**sourceId**|String|资源ID，续费,标签用|
|**domainPackages**|Integer|额外的域名扩展包|
|**extraBitsLimit**|Integer|额外的qps扩展包，单位为M|
|**startTime**|String|创建时间|
|**releaseingTime**|String|资源预计释放时间，仅过期且未释放时有效|
|**status**|Integer|资源的计费状态，1-服务中，2-过期停服，3-过期释放|
|**valid**|Integer|资源的可用状态，1-可用，其他不可用|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
