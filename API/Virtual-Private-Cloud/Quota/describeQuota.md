# describeQuota


## 描述
查询配额信息，支持查询VPC、子网、安全组、安全组规则、ACL、ACL规则、路由表、静态路由、传播路由、弹性网卡、VPC　Peering、弹性公网IP、共享带宽包（按用量）、共享带宽包中EIP、NAT网关等资源的配额。

## 请求方式
GET

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/quotas/

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|示例值|描述|
|---|---|---|---|---|
|**type**|String|True| vpc |资源类型，取值范围：vpc、elastic_ip、subnet、security_group、vpcpeering、network_interface（配额只统计辅助网卡）、acl、aclRule、routeTable、staticRoute、propagatedRoute、securityGroupRule、network_interface_cidr、bwpByUsage、bandwidthPackageIp、natGateway|
|**parentResourceId**|String|False| |type为vpc、elastic_ip、network_interface、bwpByUsage、natGateway不设置, type为subnet、security_group、vpcpeering、acl、routeTable设置为vpcId, type为aclRule设置为aclId, type为staticRoute、propagatedRoute设置为routeTableId, type为securityGroupRule为securityGroupId, type为network_interface_cidr设置为networkInterfaceId，type为bandwidthPackageIp设置为bandwidthPackageId|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describequota#result)|返回结果|
|**requestId**|String|请求ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**quota**|Object| |

## 请求示例

GET

调用方法、签名算法及公共请求参数请参考[京东云OpenAPI公共说明](https://docs.jdcloud.com/common-declaration/api/introduction)。

查询ACL （acl-xx78ixhv5z）的规则配额

```
v1/regions/cn-south-1/quotas?type=aclRule&parentResourceId=acl-xx78ixhv5z

```

## 返回示例

```
{
    "requestId": "521b6ff3-40d8-484f-afb6-b762f6103436",
    "result": {
        "quota": {
            "type": "aclRule",
            "parentResourceId": "acl-xx78ixhv5z",
            "maxLimit": 100,
            "count": 22
        }
    }
}
```



## 返回码

|HTTP状态码|错误码|描述|
|---|---|---|
|**200**|OK|                                                        |
|**400**|INVALID_ARGUMENT| 参数配置错误                                           |
|**401**|Authentication failed|用户权限认证失败|
|**404**| Not found             | 资源不存在                                             |
|**500**|INTERNAL| 系统内部错误，请稍后重试。如果多次尝试失败，请提交工单 |
|**503**|Service unavailable|服务不可用，请稍后重试。如果多次尝试失败，请提交工单|

