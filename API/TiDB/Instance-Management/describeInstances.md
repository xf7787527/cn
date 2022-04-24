# describeInstances


## 描述
查询实例列表

## 请求方式
GET

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/instances:describeInstances

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,∞)。pageNumber为-1时，返回所有数据页码；超过总页数时，显示最后一页;|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为100，取值范围：[10,100]，用于查询列表的接口|
|**filters**|[Filter[]](describeinstances#filter)|False| |过滤参数，多个过滤参数之间的关系为“与”(and)<br>支持以下属性的过滤：<br>instanceId, 支持operator选项：eq,ne<br>instanceName, 支持operator选项：eq,ne,like<br>instanceStatus, 支持operator选项：eq,ne<br>|
|**tagFilters**|[TagFilter[]](describeinstances#tagfilter)|False| |资源标签|

### <div id="tagfilter">TagFilter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**key**|String|True| |Tag键|
|**values**|String[]|True| |Tag值|
### <div id="filter">Filter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeinstances#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**instances**|[Instance[]](describeinstances#instance)| |
|**totalCount**|Number| |
### <div id="instance">Instance</div>
|名称|类型|描述|
|---|---|---|
|**instanceId**|String|实例ID|
|**instanceName**|String|实例名称|
|**engineVersion**|String|实例引擎版本|
|**minorVersion**|String|实例引擎版本的详细版本号|
|**totalNodeNum**|Integer|集群中节点的总数|
|**totalCPU**|Integer|整个集群总的CPU核数|
|**totalMemoryGB**|Integer|整个集群总的内存大小，单位GB|
|**totalStorageGB**|Integer|整个集群总的存储空间大小，单位GB|
|**regionId**|String|地域ID|
|**azId**|String[]|可用区ID，目前仅支持单可用区|
|**vpcId**|String|VPC的ID|
|**subnetId**|String|子网的ID|
|**instanceStatus**|String|实例状态，参见[枚举参数定义](../Enum-Definitions/Enum-Definitions.md)|
|**createTime**|String|实例创建时间, UTC 时间格式|
|**charge**|[Charge](describeinstances#charge)|计费配置|
|**tags**|[Tag[]](describeinstances#tag)|标签信息|
### <div id="tag">Tag</div>
|名称|类型|描述|
|---|---|---|
|**key**|String|标签键|
|**value**|String|标签值|
### <div id="charge">Charge</div>
|名称|类型|描述|
|---|---|---|
|**chargeMode**|String|支付模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration|
|**chargeStatus**|String|费用支付状态，取值为：normal、overdue、arrear，normal表示正常，overdue表示已到期，arrear表示欠费|
|**chargeStartTime**|String|计费开始时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|
|**chargeExpiredTime**|String|过期时间，预付费资源的到期时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ，后付费资源此字段内容为空|
|**chargeRetireTime**|String|预期释放时间，资源的预期释放时间，预付费/后付费资源均有此值，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
