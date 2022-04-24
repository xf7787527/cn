# describeInstanceAttributes


## 描述
查询 TiDB 实例的详细信息

## 请求方式
GET

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}

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

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**tidbInstanceAttributes**|[TidbInstanceAttribute](describeinstanceattributes#tidbinstanceattribute)| |
### <div id="tidbinstanceattribute">TidbInstanceAttribute</div>
|名称|类型|描述|
|---|---|---|
|**instanceId**|String|实例ID|
|**instanceName**|String|实例名称|
|**engineVersion**|String|实例引擎版本|
|**minorVersion**|String|实例引擎版本的详细版本号|
|**totalNodeNum**|Integer|集群中节点的总数|
|**tidbNodeSpec**|[NodeSpec](describeinstanceattributes#nodespec)|TiDB节点规格和数目|
|**tikvNodeSpec**|[NodeSpec](describeinstanceattributes#nodespec)|TiKV节点规格和数目|
|**pdNodeSpec**|[NodeSpec](describeinstanceattributes#nodespec)|PD节点规格和数目|
|**monitorNodeSpec**|[NodeSpec](describeinstanceattributes#nodespec)|Monitor节点规格，只能有1个Monitor节点|
|**tiflashNodeSpec**|[NodeSpec](describeinstanceattributes#nodespec)|TiFlash节点规格和数目|
|**ticdcNodeSpec**|[NodeSpec](describeinstanceattributes#nodespec)|Ticdc节点规格和数目|
|**totalCPU**|Integer|整个集群总的CPU核数|
|**totalMemoryGB**|Integer|整个集群总的内存大小，单位GB|
|**totalStorageGB**|Integer|整个集群总的存储空间大小，单位GB|
|**regionId**|String|地域ID|
|**azId**|String[]|可用区ID，目前仅支持单可用区|
|**vpcId**|String|VPC的ID|
|**subnetId**|String|子网的ID|
|**internalDomainName**|String|TiDB内网域名|
|**publicDomainName**|String|TiDB公网域名|
|**monitorInternalDomainName**|String|TiDB监控的内网域名|
|**monitorPublicDomainName**|String|TiDB监控的公网域名|
|**pdInternalDomainName**|String|PD的内网域名|
|**pdPublicDomainName**|String|PD的公网域名|
|**dmsInternalDomainName**|String|DMS的内网域名|
|**dmsPublicDomainName**|String|DMS的公网域名|
|**instancePort**|String|应用访问端口|
|**monitorPort**|String|TiDB监控的端口|
|**pdPort**|String|PD的端口|
|**dmsPort**|String|DMS的端口|
|**instanceStatus**|String|实例状态，参见[枚举参数定义](../Enum-Definitions/Enum-Definitions.md)|
|**createTime**|String|实例创建时间, UTC 时间格式|
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
### <div id="nodespec">NodeSpec</div>
|名称|类型|描述|
|---|---|---|
|**nodeType**|String|节点类型：tidb、tikv、pd、monitor|
|**nodeNum**|Integer|节点数|
|**nodeClass**|String|节点的规格代码|
|**cpu**|Integer|cpu核数|
|**memoryGB**|Integer|内存大小，单位GB|
|**storageType**|String|存储类型|
|**storageGB**|Integer|存储空间，单位GB|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
