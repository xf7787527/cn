# createBandwidthPackage


## 描述
指定地域创建共享带宽包实例。

## 接口说明

- 需要接口完成实名认证、支付方式确认、计费类型选择等准备工作。

- 各地域下包年包月和按配置计费的共享带宽包不受配额限制，按用量计费的共享带宽包可创建数量受配额限制，创建前请通过 [DescribeQuotas](https://docs.jdcloud.com/cn/virtual-private-cloud/api/describequotas) 确认配额，如须提升请[提交工单](https://ticket.jdcloud.com/applyorder/submit)或联系京东云客服。

- 通过本接口创建包年包月资源时将自动从账户扣款（代金券优先），如需使用第三方支付方式请通过控制台创建。

- 按用量计费模式需提工单申请使用权限，默认支持增强95消峰计费。


## 请求方式
POST

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/bandwidthPackages/

|名称|类型|是否必需|示例值|描述|
|---|---|---|---|---|
|**regionId**|String|True| cn-north-1 |地域ID，可参考[地域可用区](https://docs.jdcloud.com/cn/virtual-private-cloud/region-az)Region ID|

## 请求参数
|名称|类型|是否必需|示例值|描述|
|---|---|---|---|---|
|**name**|String|True| bwp-test |名称，只支持中文、数字、大小写字母、英文下划线“_”及中划线“-”，且长度不超过32个字符|
|**description**|String|False| 这是描述 |描述，长度不超过256个字符|
|**bandwidthMbps**|Integer|True| 200 |共享带宽包带宽上限，取值范围200-5000，单位为Mbps，按用量计费类型的保底带宽 = 共享带宽包带宽上限 * 20%|
|**provider**|String|False| bgp |线路信息，默认bgp，目前只支持中心节点的BGP线路|
|**chargeSpec**|[ChargeSpec](createbandwidthpackage#chargespec)|False| prepaid_by_duration |计费配置。支持包年包月、按配置、按用量计费模式|
|**userTags**|[Tag[]](createbandwidthpackage#tag)|False| |用户标签|
|**resourceGroupId**|String|False| |资源所属资源组ID|

### <div id="tag">Tag</div>
|名称|类型|是否必需|示例值|描述|
|---|---|---|---|---|
|**key**|String|True| 标签 |Tag键|
|**value**|String|True| 值 |Tag值|
### <div id="chargespec">ChargeSpec</div>
|名称|类型|是否必需| 示例值               |描述|
|---|---|---|---|---|
|**chargeMode**|String|False|postpaid_by_duration|计费模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration.请参阅具体产品线帮助文档确认该产品线支持的计费类型|
|**chargeUnit**|String|False| month |预付费计费单位，预付费必填，当chargeMode为prepaid_by_duration时有效，取值为：month、year，默认为month|
|**chargeDuration**|Integer|False| 1 |预付费计费时长，预付费必填，当chargeMode取值为prepaid_by_duration时有效。当chargeUnit为month时取值为：1~9，当chargeUnit为year时取值为：1、2、3|
|**autoRenew**|Boolean|False| CLOSE |True=：OPEN——开通自动续费、False=CLOSE—— 不开通自动续费，默认为CLOSE|
|**buyScenario**|String|False| |统一活动凭证。此参数暂未启用，无须指定且指定无效。|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](createbandwidthpackage#result)|返回结果|
|**requestId**|[String](createbandwidthpackage#result)|请求id|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**bandwidthPackageId**|String|共享带宽包ID|
|**requestId**|String|请求ID|

## 返回码
| HTTP状态码 | 错误码                         | 描述                                                       |
| ---------- | ------------------------------ | ---------------------------------------------------------- |
| **200**    | ok                             |                                                            |
| **400**    | Invalid param 'xxx'            | 参数配置错误                                               |
| **401**    | Unauthenticated user pin 'xxx' | 用户认证鉴权失败                                           |
| **500**    | Unknown server error           | 系统内部错误，请稍后重试。如果多次尝试失败，请提交工单。   |
| **503**    | Service unavailable            | 服务暂时不可用，请稍后重试。如果多次尝试失败，请提交工单。 |

## 请求示例

调用方法、签名算法及公共请求参数请参考[京东云OpenAPI公共说明](https://docs.jdcloud.com/common-declaration/api/introduction)。

- 请求示例：创建共享带宽包

POST

```
/v1/regions/cn-north-1/bandwidthPackages
    {
        "name":"bwp-example-1",
        "bandwidthMbps":200,
        "description":"",
        "provider": "bgp",
        "resourceGroupId": "rg-default",
        "userTags":[
            {
                "key": "key1",
                "value": "value1"
            },
            {
                "key": "key2",
                "value": "value2"
            }
        ]
    }

```

## 返回示例
```
{
    "bandwidthPackageId": "bwp-1njs5vuoh7", 
    "requestId": "cf064915-fb92-422b-b9ed-91aa17ec6647"
}
```
