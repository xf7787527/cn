# modifyBandwidthPackage


## 描述

修改共享带宽包信息，包括带宽上限及共享带宽包名称、描述信息。

## 接口说明

- 如共享带宽包中的弹性公网 IP 有单独限速。共享带宽包的带宽上限值不能低于其包含任一弹性公网IP的带宽上限值。

- 欠费或到期的共享带宽包资源不支持修改带宽上限。


## 请求方式
PATCH

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/bandwidthPackages/{bandwidthPackageId}

|名称|类型|是否必需| 示例值 |描述|
|---|---|---|---|---|
|**regionId**|String|True| cn-north-1 |地域ID，可参考[地域可用区](https://docs.jdcloud.com/cn/virtual-private-cloud/region-az)|
|**bandwidthPackageId**|String|True| bwp-xxxxxx |共享带宽包ID|

## 请求参数
|名称|类型|是否必需|示例值|描述|
|---|---|---|---|---|
|**bandwidthMbps**|Integer|False| 200 |共享带宽包带宽上限，取值范围200-5000，单位为Mbps，且不能低于共享带宽包内公网IP带宽上限|
|**name**|String|False| bwp-test |名称，只支持中文、数字、大小写字母、英文下划线“_”及中划线“-”，且长度不超过32个字符|
|**description**|String|False| 这是描述 |描述，长度不超过256个字符|


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

- 请求示例：修改共享带宽包 bwp-1njs5vuoh7

PATCH

```
/v1/regions/cn-north-1/bandwidthPackages/bandwidthPackages/bwp-1njs5vuoh7
    {
        "bandwidthMbps": 201,
        "name": "bwp1",
        "description": "bwp for example"
    }

```

## 返回示例
```
{
    "requestId": "5a98a34a-2246-4ad3-8b35-064ef8f04e4d"
}
```
