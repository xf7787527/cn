# describeInstanceAttributes


## 描述
查询 Clickhouse 实例的详细信息

## 请求方式
GET

## 请求地址
https://clickhouse.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeinstanceattributes#result)| |
|**requestId**|String| |
### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**clickhouseInstanceAttributes**|[ClickhouseInstanceAttributes](describeinstanceattributes#clickhouseinstanceattributes)| |
### <div id="clickhouseinstanceattributes">ClickhouseInstanceAttributes</div>
|名称|类型|描述|
|---|---|---|
|**instanceId**|String|实例ID|
|**instanceName**|String|实例名称|
|**engineVersion**|String|实例引擎版本|
|**replicaNum**|Integer|实例副本数|
|**shardNum**|Integer|实例分片数|
|**chNodeClass**|String|规格|
|**chNodeStorageType**|String|存储类型|
|**chNodeStorageGB**|Integer|节点存储空间|
|**chNodeCPU**|Integer|CPU核数|
|**chNodeMemoryGB**|Integer|内存单位GB|
|**zkNodeClass**|String|zk节点规格|
|**zkNodeNum**|Integer|zk节点数目|
|**zkNodeCPU**|Integer|CPU核数|
|**zkNodeMemoryGB**|Integer|内存单位GB|
|**zkNodeStorageGB**|Integer|zk节点存储空间|
|**monitorNodeClass**|String|monitor节点规格|
|**monitorNodeNum**|Integer|monitor节点数目|
|**monitorNodeCPU**|Integer|CPU核数|
|**monitorNodeMemoryGB**|Integer|内存单位GB|
|**monitorNodeStorageGB**|Integer|monitor节点存储空间|
|**totalCPU**|Integer|总CPU核数|
|**totalMemoryGB**|Integer|总内存单位GB|
|**totalStorageGB**|Integer|总节点存储空间|
|**regionId**|String|地域ID|
|**azId**|String[]|可用区ID，目前仅支持单可用区|
|**vpcId**|String|VPC的ID|
|**subnetId**|String|子网的ID|
|**internalDomainName**|String|Clickhouse内网域名|
|**publicDomainName**|String|Clickhouse公网域名|
|**monitorInternalDomainName**|String|ClickhouseDB监控服务的内网域名|
|**monitorPublicDomainName**|String|ClickhouseDB监控服务的公网域名|
|**monitorPort**|String|ClickhouseDB监控服务端口|
|**tcpPort**|String|tcp端口|
|**httpPort**|String|http端口|
|**instanceStatus**|String|实例状态，参见[枚举参数定义](../Enum-Definitions/Enum-Definitions.md)|
|**createTime**|String|实例创建时间, UTC 时间格式|
|**supersetInternalDomainName**|String| |
|**supersetPublicDomainName**|String| |
|**supersetPort**|String| |
|**aeStatus**|Integer| |
|**charge**|[Charge](describeinstanceattributes#charge)|计费配置|
|**tags**|[Tag[]](describeinstanceattributes#tag)|标签信息|
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
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
