# createElasticIps


## 描述
创建一个或者多个弹性公网IP

## 请求方式
POST

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/elasticIps/

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**maxCount**|Integer|True| |购买弹性ip数量；取值范围：[1,100]|
|**elasticIpAddress**|String|False| |指定弹性ip地址进行创建，当申请创建多个弹性ip时，必须为空|
|**elasticIpSpec**|[ElasticIpSpec](createElasticIps#user-content-elasticipspec)|True| |弹性ip规格|
|**userTags**|[Tag[]](createElasticIps#user-content-tag)|False| |用户标签|
|**ipType**|String|False| |弹性ip类型，取值：standard(标准公网IP)，edge(边缘公网IP)，默认为standard|

### <div id="user-content-tag">Tag</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**key**|String|True| |Tag键|
|**value**|String|True| |Tag值|
### <div id="user-content-elasticipspec">ElasticIpSpec</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**bandwidthMbps**|Integer|True| |弹性公网IP的限速（单位：Mbps），取值范围为[1-200]|
|**provider**|String|True| |IP线路信息。当IP类型为标准公网IP时，取值为bgp或no_bgp，cn-north-1：bgp；cn-south-1：bgp；cn-east-1：bgp；cn-east-2：bgp。当IP类型为边缘公网IP时，其值可通过调用describeEdgeIpProviders、获取不同边缘节点的边缘公网IP线路信息|
|**chargeSpec**|[ChargeSpec](createElasticIps#user-content-chargespec)|False| |计费配置。边缘公网IP支持包年包月、按配置；标准公网IP支持包年包月、按配置、按流量|
### <div id="user-content-chargespec">ChargeSpec</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**chargeMode**|String|False|postpaid_by_duration|计费模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration.请参阅具体产品线帮助文档确认该产品线支持的计费类型|
|**chargeUnit**|String|False| |预付费计费单位，预付费必填，当chargeMode为prepaid_by_duration时有效，取值为：month、year，默认为month|
|**chargeDuration**|Integer|False| |预付费计费时长，预付费必填，当chargeMode取值为prepaid_by_duration时有效。当chargeUnit为month时取值为：1~9，当chargeUnit为year时取值为：1、2、3|
|**autoRenew**|Boolean|False| |True=：OPEN——开通自动续费、False=CLOSE—— 不开通自动续费，默认为CLOSE|
|**buyScenario**|String|False| |统一活动凭证。此参数暂未启用，无须指定且指定无效。|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](createElasticIps#user-content-result)|返回结果|

### <div id="user-content-result">Result</div>
|名称|类型|描述|
|---|---|---|
|**elasticIpIds**|String[]|弹性公网IP ID列表|
|**requestId**|String|请求ID|

## 返回码
|返回码|描述|
|---|---|
|**200**|Successful operation|
|**400**|Invalid param 'xxx'|
|**401**|Unauthenticated user pin 'xxx'|
|**500**|Unknown server error|
|**503**|Service unavailable|

## 请求示例

调用方法、签名算法及公共请求参数请参考[京东云OpenAPI公共说明](https://docs.jdcloud.com/common-declaration/api/introduction)。

- 请求示例: 创建一个弹性公网ip

POST
```
  /v1/regions/cn-north-1/elasticIps/
    {
           "maxCount":1,
           "elasticIpSpec":{
               "bandwidthMbps":1,
               "provider" :"bgp"
           }
       }

```

## 返回示例
```
{
    "requestId": "67174ffe-c056-491d-935d-6b4f7c33b4d9", 
    "result": {
        "elasticIpIds": [
            "fip-xcgb8fva97"
        ]
    }
}
```
