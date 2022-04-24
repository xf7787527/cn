# deleteBandwidthPackage


## 描述
删除共享带宽包

## 接口说明

- 当共享带宽包内有公网IP存在时、包年包月类型的共享带宽包未到期时、按用量计费的共享带宽包使用时长未满一个完整的自然月时均不支持删除共享带宽包


## 请求方式
DELETE

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/bandwidthPackages/{bandwidthPackageId}

|名称|类型|是否必需|示例值|描述|
|---|---|---|---|---|
|**regionId**|String|True| cn-north-1 | 地域ID，可参考[地域可用区](https://docs.jdcloud.com/cn/virtual-private-cloud/region-az)Region ID |
|**bandwidthPackageId**|String|True| bwp-xxxxxx |共享带宽包ID|

## 请求参数
无


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

- 请求示例：删除共享带宽包bwp-1njs5vuoh7

DELETE

```
/v1/regions/cn-north-1/bandwidthPackages/bwp-1njs5vuoh7

```

## 返回示例
```
{
    "requestId": "43ff1b64-2235-4a5d-80c8-3735aca0387c"
}
```
