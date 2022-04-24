# describeBandwidthPackage


## 描述

共享带宽包资源信息详情

## 接口说明

- 该接口与查询共享带宽包列表返回的信息一致。

- 只需要查询单个共享带宽包详细信息的时候可以调用该接口。


## 请求方式
GET

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/bandwidthPackages/{bandwidthPackageId}

|名称|类型|是否必需| 示例值     |描述|
|---|---|---|---|---|
|**regionId**|String|True| cn-north-1 |地域ID，可参考[地域可用区](https://docs.jdcloud.com/cn/virtual-private-cloud/region-az)|
|**bandwidthPackageId**|String|True| bwp-xxxxx |共享带宽包ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describebandwidthpackage#result)|返回结果|
|**requestId**|String|请求ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**bandwidthPackage**|[BandwidthPackage](describebandwidthpackage#bandwidthpackage)|共享带宽包资源信息|
### <div id="bandwidthpackage">BandwidthPackage</div>
|名称|类型|描述|
|---|---|---|
|**bandwidthPackageId**|String|共享带宽包ID|
|**bandwidthPackageName**|String|名称|
|**description**|String|描述|
|**bandwidthMbps**|Integer|共享带宽包带宽上限，取值范围200-5000，单位为Mbps，按用量计费模式的保底带宽 = 共享带宽包带宽上限 * 20%|
|**provider**|String|线路信息|
|**charge**|[Charge](describebandwidthpackage#charge)|计费配置|
|**createdTime**|String|创建时间，时间格式为UTC|
|**publicIps**|[BwpIp[]](describebandwidthpackage#bwpip)|共享带宽包内公网IP信息|
|**ipCount**|Integer|共享带宽包内加入公网IP个数|
|**guaranteedRatio**|Integer|按用量计费模式的保底带宽百分比，-1代表无效值 ，目前保底带宽百分比为20%|
|**guaranteedBandwidth**|Number|按用量计费模式的保底带宽，-1代表无效值，保底带宽 = 共享带宽包带宽上限 * 20%|
|**adminStatus**|String|是否欠费停服，UP正常，DOWN停服|
|**tags**|[Tag[]](describebandwidthpackage#tag)|Tag信息|
|**resourceGroupId**|String|资源所属资源组ID|
### <div id="tag">Tag</div>
|名称|类型|描述|
|---|---|---|
|**key**|String|Tag键|
|**value**|String|Tag值|
### <div id="bwpip">BwpIp</div>
|名称|类型|描述|
|---|---|---|
|**publicIpId**|String|公网IP实例ID|
|**addedTime**|String|公网IP加入共享带宽包的时间，时间格式为UTC|
|**bandwidthMbps**|Integer|单个公网IP带宽上限，大小不能超过共享带宽包的带宽上限，单位为Mbps，支持0和-1，0表示禁止流量通过，-1表示关闭单个公网IP带宽限速|
### <div id="charge">Charge</div>
|名称|类型|描述|
|---|---|---|
|**chargeMode**|String|支付模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration|
|**chargeStatus**|String|费用支付状态，取值为：normal、overdue、arrear，normal表示正常，overdue表示已到期，arrear表示欠费|
|**chargeStartTime**|String|计费开始时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|
|**chargeExpiredTime**|String|过期时间，预付费资源的到期时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ，后付费资源此字段内容为空|
|**chargeRetireTime**|String|预期释放时间，资源的预期释放时间，预付费/后付费资源均有此值，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|

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

- 请求示例：查看共享带宽包 bwp-1njs5vuoh7 的资源详情

GET

```
/v1/regions/cn-north-1/bandwidthPackages/bwp-1njs5vuoh7

```

## 返回示例
```
{
    "requestId": "cf064915-fb92-422b-b9ed-91aa17ec6647", 
    "result": {
        "bandwidthPackage": {
            "adminStatus": "UP", 
            "bandwidthMbps": 200, 
            "bandwidthPackageId": "bwp-1njs5vuoh7", 
            "bandwidthPackageName": "bwp-example-1", 
            "charge": {
                "chargeExpiredTime": "", 
                "chargeMode": "postpaid_by_usage", 
                "chargeRetireTime": "", 
                "chargeStartTime": "2022-03-03 20:08:39", 
                "chargeStatus": "normal"
            }, 
            "createdTime": "2022-03-03T12:08:06Z", 
            "description": "", 
            "guaranteedBandwidth": 40, 
            "guaranteedRatio": 20, 
            "ipCount": 1, 
            "provider": "bgp", 
            "publicIps": [
                {
                    "addedTime": "2022-04-13T09:09:19Z", 
                    "bandwidthMbps": 1, 
                    "publicIpId": "fip-nghz3aixxb"
                }
            ], 
            "resourceGroupId": "rg-default", 
            "tags": [
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
    }
}
```
