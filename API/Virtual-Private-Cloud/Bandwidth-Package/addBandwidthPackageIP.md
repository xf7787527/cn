# addBandwidthPackageIP


## 描述

向共享带宽包内添加弹性公网 IP。

## 接口说明 

- 确保已有至少一个共享带宽包资源。

- 添加弹性公网IP前，需确保弹性公网IP所在地域与共享带宽包地域和线路相同，弹性公网IP的计费模式为按配置或按用量计费，且未加入其他的共享带宽包资源。

- 已欠费的、包年包月的公网IP不能加入共享带宽包。

- 一个公网IP同时只能加入一个共享带宽包。

- 共享带宽包中可添加的弹性公网IP受配额限制，添加前请通过 [DescribeQuotas](https://docs.jdcloud.com/cn/virtual-private-cloud/api/describequotas) 确认配额，如须提升请[提交工单](https://ticket.jdcloud.com/applyorder/submit)或联系京东云客服。

- 弹性公网IP加入共享带宽包后，弹性公网 IP 会原有的计费和带宽上限暂时失效，已共享带宽包进行计费，带宽上限默认为共享带宽包的带宽上限，可通过[modifyBandwidthPackageIpBandwidth](https://docs.jdcloud.com/cn/virtual-private-cloud/api/modifybandwidthpackageIpbandwidth)进行修改。

- 共享带宽包欠费或到期停服后不支持添加弹性公网IP。


## 请求方式
POST

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/bandwidthPackages/{bandwidthPackageId}:addBandwidthPackageIP

|名称|类型|是否必需|示例值|描述|
|---|---|---|---|---|
|**regionId**|String|True| cn-north-1 |地域ID，可参考[地域可用区](https://docs.jdcloud.com/cn/virtual-private-cloud/region-az)Region ID|
|**bandwidthPackageId**|String|True| bwp-xxxx |共享带宽包ID|

## 请求参数
|名称|类型|是否必需|示例值|描述|
|---|---|---|---|---|
|**bandwidthPackageIPSpecs**|[AddBandwidthPackageIPSpec[]](addbandwidthpackageip#addbandwidthpackageipspec)|True| |Ip列表|

### <div id="addbandwidthpackageipspec">AddBandwidthPackageIPSpec</div>
|名称|类型|是否必需|示例值|描述|
|---|---|---|---|---|
|**publicIpId**|String|True| fip-xxxxx |公网IP ID，当加入弹性公网IP时，为elasticIpId。有如下限制：已欠费的公网IP不能加入共享带宽包；包年包月的公网IP不能加入共享带宽包；一个公网IP同时只能加入一个公网带宽包；公网IP和共享带宽包的地域不同或者线路不同时，公网IP不能加入对应共享带宽包；一个共享带宽包默认可加入20个公网IP|
|**bandwidthMbps**|Integer|False| 200 |单个公网IP带宽上限，大小不能超过共享带宽包的带宽上限，单位为Mbps，可取值0或-1，0表示禁止流量通过， -1表示关闭单个公网IP带宽限速，默认值为-1，表示公网IP加入共享带宽包后带宽上限默认为共享带宽包的带宽上限|

## 返回参数
|名称|类型|描述|
|---|---|---|
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

- 请求示例：向共享带宽包 bwp-1njs5vuoh7 中新增弹性公网 IP

POST

```
/v1/regions/cn-north-1/bandwidthPackages/bwp-1njs5vuoh7:addBandwidthPackageIP
    {
        "bandwidthPackageIPSpecs": [
            {
                "publicIpId": "fip-nghz3aixxb",
                "bandwidthMbps": 1
            }
        ]
    }

```

## 返回示例
```
{
    "requestId": "b0169617-114e-4051-bca2-f91c8631da73"
}
```
