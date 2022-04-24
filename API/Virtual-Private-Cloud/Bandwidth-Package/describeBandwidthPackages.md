# describeBandwidthPackages


## 描述

查询共享带宽包列表

## 接口说明

- 使用 `filters` 过滤器进行条件筛选，每个 `filter` 之间的关系为逻辑与（AND）的关系。

- 如果使用子帐号查询，只会查询到该子帐号有权限的云主机实例。关于资源权限请参考 [IAM概述](https://docs.jdcloud.com/cn/iam/product-overview)。

- 单次查询最大可查询100条共享带宽包数据。

- 尽量一次调用接口查询多条数据，不建议使用该批量查询接口一次查询一条数据，如果使用不当导致查询过于密集，可能导致网关触发限流。

- 由于该接口为 `GET` 方式请求，最终参数会转换为 `URL` 上的参数，但是 `HTTP` 协议下的 `GET` 请求参数长度是有大小限制的，使用者需要注意参数超长的问题。


## 请求方式
GET

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/bandwidthPackages/

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| cn-north-1 |地域ID，可参考[地域可用区](https://docs.jdcloud.com/cn/virtual-private-cloud/region-az)|

## 请求参数
|名称|类型|是否必需|示例值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False|1|页码, 默认为1, 取值范围：[1,∞), 页码超过总页数时, 显示最后一页|
|**pageSize**|Integer|False|20|分页大小，默认为20，取值范围为[10,100]|
|**filters**|[Filter[]](describebandwidthpackages#filter)|False| |bwpIds - 共享带宽包ID，支持多个进行精确搜索<br>name - 共享带宽包名称，支持单个进行精确搜索<br>|
|**tags**|[TagFilter[]](describebandwidthpackages#tagfilter)|False| |Tag筛选条件|
|**resourceGroupIds**|String[]|False| |资源组筛选条件|

### <div id="tagfilter">TagFilter</div>
|名称|类型|是否必需| 示例值 |描述|
|---|---|---|---|---|
|**key**|String|False| 标签 |Tag键|
|**values**|String[]|False| 值 |Tag值|
### <div id="filter">Filter</div>
|名称|类型|是否必需| 示例值   |描述|
|---|---|---|---|---|
|**name**|String|True| bwp-test |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describebandwidthpackages#result)|返回结果|
|**requestId**|String|请求ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**bandwidthPackages**|[BandwidthPackage[]](describebandwidthpackages#bandwidthpackage)|共享带宽包资源信息列表|
|**totalCount**|Integer|总数量|
### <div id="bandwidthpackage">BandwidthPackage</div>
|名称|类型|描述|
|---|---|---|
|**bandwidthPackageId**|String|共享带宽包ID|
|**bandwidthPackageName**|String|名称|
|**description**|String|描述|
|**bandwidthMbps**|Integer|共享带宽包带宽上限，取值范围200-5000，单位为Mbps，按用量计费模式的保底带宽 = 共享带宽包带宽上限 * 20%|
|**provider**|String|线路信息|
|**charge**|[Charge](describebandwidthpackages#charge)|计费配置|
|**createdTime**|String|创建时间，时间格式为UTC|
|**ipCount**|Integer|共享带宽包内加入公网IP个数|
|**guaranteedRatio**|Integer|按用量计费模式的保底带宽百分比，-1代表无效值 ，目前保底带宽百分比为20%|
|**guaranteedBandwidth**|Number|按用量计费模式的保底带宽，-1代表无效值，保底带宽 = 共享带宽包带宽上限 * 20%|
|**adminStatus**|String|是否欠费停服，UP正常，DOWN停服|
|**tags**|[Tag[]](describebandwidthpackages#tag)|Tag信息|
|**resourceGroupId**|String|资源所属资源组ID|
### <div id="tag">Tag</div>
|名称|类型|描述|
|---|---|---|
|**key**|String|Tag键|
|**value**|String|Tag值|
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

- 请求示例：查询共享带宽包列表

GET

```
/v1/regions/cn-north-1/bandwidthPackages/?pageNumber=1&pageSize=10&filters.1.name=bwpIds&filters.1.values.1=bwp-1njs5vuoh7

```

## 返回示例
```
{
    "requestId": "cf064915-fb92-422b-b9ed-91aa17ec6647", 
    "result": {
        "bandwidthPackages": [
            {
                "adminStatus": "UP", 
                "bandwidthMbps": 200, 
                "bandwidthPackageId": "bwp-1njs5vuoh7", 
                "bandwidthPackageName": "bwp1", 
                "charge": {
                    "chargeExpiredTime": "", 
                    "chargeMode": "postpaid_by_usage", 
                    "chargeRetireTime": "", 
                    "chargeStartTime": "2022-03-03 20:08:39", 
                    "chargeStatus": "normal"
                }, 
                "createdTime": "2022-03-03T12:08:06Z", 
                "description": "bwp for example", 
                "guaranteedBandwidth": 40.2, 
                "guaranteedRatio": 20, 
                "ipCount": 1, 
                "provider": "bgp", 
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
        ], 
        "totalCount": 1
    }
}
```
