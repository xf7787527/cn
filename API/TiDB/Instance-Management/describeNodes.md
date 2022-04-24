# describeNodes


## 描述
获取某个实例下的节点信息

## 请求方式
GET

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/nodes

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,∞)。pageNumber为-1时，返回所有数据页码；超过总页数时，显示最后一页;|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为50，取值范围：[50,100]，用于查询列表的接口|
|**sorts**|[Sort[]](describenodes#sort)|False| |cpuUtil - CPU使用率<br>memeryUtil - 内存使用率<br>diskUsage - 磁盘使用率<br>|
|**filters**|[Filter[]](describenodes#filter)|False| |nodeType, 支持operator选项：eq,ne<br>nodeStatus, 支持operator选项：eq ne<br>|

### <div id="filter">Filter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|
### <div id="sort">Sort</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|False| |排序条件的名称|
|**direction**|String|False| |排序条件的方向|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describenodes#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**nodes**|[TiDBNode[]](describenodes#tidbnode)| |
|**totalCount**|Number|总记录数|
### <div id="tidbnode">TiDBNode</div>
|名称|类型|描述|
|---|---|---|
|**nodeId**|String|节点ID|
|**nodeType**|String|节点类型，支持,tidb,tikv,pd,tiflash,monitor|
|**nodeStatus**|String|节点状态|
|**cpuUtil**|Float|CPU 使用百分比，例如0.832表示CPU使用率为83.2%|
|**memeryUtil**|Float|内存使用百分比，例如0.832表示内存使用率为83.2%|
|**diskUsage**|Float|存储使用百分比，例如0.832表示存储使用率为83.2%|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
