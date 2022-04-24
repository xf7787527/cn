# describeSystemInfo


## 描述
获取当前实例系统信息

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/systemInfo

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceGid**|String|True| |RDS 实例ID，唯一标识一个RDS实例|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describesysteminfo#result)| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**bufferPoolInfo**|[BufferPoolInfo](describesysteminfo#bufferpoolinfo)|Buffer Pool信息|
|**connectionInfo**|[ConnectionInfo](describesysteminfo#connectioninfo)|连接信息|
|**serverInfo**|[ServerInfo](describesysteminfo#serverinfo)|Server信息|
### <div id="ServerInfo">ServerInfo</div>
|名称|类型|描述|
|---|---|---|
|**version**|String|版本信息|
|**uptime**|String|实例已运行时长|
### <div id="ConnectionInfo">ConnectionInfo</div>
|名称|类型|描述|
|---|---|---|
|**max**|Integer|连接数上限|
|**running**|Integer|活跃连接数|
|**connected**|Integer|当前连接数|
### <div id="BufferPoolInfo">BufferPoolInfo</div>
|名称|类型|描述|
|---|---|---|
|**dirtyPagePct**|Float|脏页比例，如 0.999923456|
|**freePagePct**|Float|空闲页比例，如 0.999923456|
|**totalPages**|Integer|buffer pool 总页数|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
