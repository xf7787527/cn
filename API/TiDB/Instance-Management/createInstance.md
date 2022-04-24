# createInstance


## 描述
创建一个TiDB实例

## 请求方式
POST

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/instances

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceSpec**|[TidbInstanceSpec](createinstance#tidbinstancespec)|True| |新建实例规格|

### <div id="tidbinstancespec">TidbInstanceSpec</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceName**|String|True| |实例名|
|**engineVersion**|String|False| |TiDB引擎版本|
|**tidbNodeSpec**|[NodeSpec](createinstance#nodespec)|True| |TiDB节点规格和数目|
|**tikvNodeSpec**|[NodeSpec](createinstance#nodespec)|True| |TiKV节点规格和数目|
|**pdNodeSpec**|[NodeSpec](createinstance#nodespec)|True| |PD节点规格和数目|
|**monitorNodeSpec**|[NodeSpec](createinstance#nodespec)|True| |Monitor节点规格，只能有1个Monitor节点|
|**tiflashNodeSpec**|[NodeSpec](createinstance#nodespec)|False| |TiFlash节点规格和数目|
|**ticdcNodeSpec**|[NodeSpec](createinstance#nodespec)|False| |Ticdc节点规格和数目|
|**azId**|String[]|True| |可用区ID，目前仅支持单可用区部署|
|**vpcId**|String|True| |VPC的ID|
|**subnetId**|String|True| |子网ID|
|**chargeSpec**|[ChargeSpec](createinstance#chargespec)|True| |计费规格，包括计费类型，计费周期等|
|**tagSpec**|[Tag[]](createinstance#tag)|False| |标签信息|
### <div id="tag">Tag</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**key**|String|False| |标签键|
|**value**|String|False| |标签值|
### <div id="chargespec">ChargeSpec</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**chargeMode**|String|False|postpaid_by_duration|计费模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration.请参阅具体产品线帮助文档确认该产品线支持的计费类型|
|**chargeUnit**|String|False| |预付费计费单位，预付费必填，当chargeMode为prepaid_by_duration时有效，取值为：month、year，默认为month|
|**chargeDuration**|Integer|False| |预付费计费时长，预付费必填，当chargeMode取值为prepaid_by_duration时有效。当chargeUnit为month时取值为：1~9，当chargeUnit为year时取值为：1、2、3|
|**autoRenew**|Boolean|False| |True=：OPEN——开通自动续费、False=CLOSE—— 不开通自动续费，默认为CLOSE|
|**buyScenario**|String|False| |产品线统一活动凭证JSON字符串，需要BASE64编码，目前要求编码前格式为 {"activity":{"activityType":必填字段, "activityIdentifier":必填字段}}|
### <div id="nodespec">NodeSpec</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**nodeType**|String|True| |节点类型：tidb、tikv、pd、monitor|
|**nodeNum**|Integer|True| |节点数|
|**nodeClass**|String|True| |节点的规格代码|
|**cpu**|Integer|False| |cpu核数|
|**memoryGB**|Integer|False| |内存大小，单位GB|
|**storageType**|String|True| |存储类型|
|**storageGB**|Integer|True| |存储空间，单位GB|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](createinstance#result)| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**instanceId**|String| |
|**orderId**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
