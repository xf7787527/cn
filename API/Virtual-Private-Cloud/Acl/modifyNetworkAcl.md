# modifyNetworkAcl


## 描述
修改networkAcl接口

## 请求方式
PATCH

## 请求地址
https://vpc.jdcloud-api.com/v1/regions/{regionId}/networkAcls/{networkAclId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|
|**networkAclId**|String|True| |networkAclId ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**networkAclName**|String|False| |networkAcl名称,只允许输入中文、数字、大小写字母、英文下划线“_”及中划线“-”，不允许为空且不超过32字符|
|**description**|String|False| |描述,允许输入UTF-8编码下的全部字符，不超过256字符|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID|


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**404**|Not found|
|**500**|Internal error|

## 请求示例

调用方法、签名算法及公共请求参数请参考[京东云OpenAPI公共说明](https://docs.jdcloud.com/common-declaration/api/introduction)。

- 请求示例：将id为acl-axne0jaf0z的acl名称修改为“测试acl1”


PATCH
```
  /v1/regions/cn-north-1/networkAcls/acl-axne0jaf0z
    {
          "networkAclName":"测试acl1"
      }

```

## 返回示例
```
{
    "requestId": "c45prpfm8evoi69tqtc9nf6o1p2knsmw"
}
```
