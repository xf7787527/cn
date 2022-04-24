# removeBandwidthPackageIP


## 描述

从共享带宽包内移除公网IP

## 接口说明

-  弹性公网IP从共享带宽包中移除后，恢复原有的计费模式和带宽上限。

-  共享带宽包是否计费与共享带宽包中有无弹性公网IP无关，如共享带宽包中无弹性公网IP资源时请及时删除资源，避免产生额外费用


## 请求方式
POST

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/bandwidthPackages/{bandwidthPackageId}:removeBandwidthPackageIP

|名称|类型|是否必需|示例值|描述|
|---|---|---|---|---|
|**regionId**|String|True| cn-north-1 |地域 ID，可参考[地域可用区](https://docs.jdcloud.com/cn/virtual-private-cloud/region-az)|
|**bandwidthPackageId**|String|True| bwp-xxxx |共享带宽包 ID|

## 请求参数
|名称|类型|是否必需|示例值|描述|
|---|---|---|---|---|
|**bandwidthPackageIPSpecs**|[RemoveBandwidthPackageIPSpec[]](removebandwidthpackageip#removebandwidthpackageipspec)|True| |公网IP列表|

### <div id="removebandwidthpackageipspec">RemoveBandwidthPackageIPSpec</div>
|名称|类型|是否必需|示例值|描述|
|---|---|---|---|---|
|**publicIpId**|String|False| fip-xxxxx |已加入共享带宽包的公网IP的ID，对于弹性公网IP为elasticIpId|

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

- 请求示例：从共享带宽包（bwp-1njs5vuoh7）中移除公网 IP（fip-nghz3aixxb）

POST

```
/v1/regions/cn-north-1/bandwidthPackages/bwp-1njs5vuoh7:removeBandwidthPackageIP
    {
        "bandwidthPackageIPSpecs": [
            {
                "publicIpId": "fip-nghz3aixxb"
            }
        ]
    }

```

## 返回示例
```
{
    "requestId": "a785c44b-8595-4df0-9d81-33cfe88f0d9f"
}
```
