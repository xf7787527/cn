# modifyInstancePlacement


## 描述

存量主机加入高可用组，或者主机从一个高可用组移动到另一个高可用组。

详细操作说明请参考帮助文档：[调整高可用组](https://docs.jdcloud.com/cn/virtual-machines/modify-instance-ag)、[手动添加实例](https://docs.jdcloud.com/cn/availability-group/add-instance-manually)

## 接口说明

- 仅支持运行中和已停止状态的实例调整高可用组，且仅支持已停止状态的实例强制均衡调整高可用组。
- 不支持专有宿主机上的实例、裸金属实例调整高可用组。
- 除GPU、vGPU（以P开头）外的一代机暂不支持调整高可用组。
- 与高可用组关联实例模板的VPC相同的实例才可加入该高可用组。
- 与高可用组可用区匹配的实例才可加入该高可用组。
- 本地系统盘实例不支持强制均衡调整高可用组。
- 若本地数据盘强制均衡调整高可用组，需确认清除本地盘数据。


## 请求方式
POST

## 请求地址
https://vm.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:modifyInstancePlacement

|名称|类型|是否必需|示例值|描述|
|---|---|---|---|---|
|**regionId**|String|是|cn-north-1 |地域ID。|
|**instanceId**|String|是|i-eumm****d6 |云主机ID。|

## 请求参数
|名称|类型|是否必需|示例值|描述|
|---|---|---|---|---|
|**agId**|String|是|ag-hmtg****t2 |高可用组Id|
|**balance**|Boolean|否|false |是否强制均衡，默认 false<br>|
|**clearLocalDisk**|Boolean|否|false |是否确认清除本地盘数据，默认 false；该字段仅在本地数据盘强制迁移调整高可用组时生效，此值需填true<br>|


## 返回参数
|名称|类型|示例值|描述|
|---|---|---|
|**requestId**|String|c2hmmaan8w06w19qcdfuic4w03f7ft2d|请求ID。|




## 请求示例
POST
```
```
/v1/regions/cn-north-1/instances/i-eumm****d6:modifyInstancePlacement
{
    "agId" : "ag-2a***s2abc",
    "balance" : false,
    "clearLocalDisk" : false,
}
```

```

## 返回示例
```
{
    "requestId": "a0633f72670e59f8c6db36b1ee257011"
}
```

## 返回码
|HTTP状态码|错误码|描述|错误解析|
|---|---|---|---|
|**200**||OK||
|**400**|INVALID_ARGUMENT|Invalid region|地域参数异常。|
|**400**|FAILED_PRECONDITION|Doesn't support dedicated host when modifying AvailableGroup|专有宿主机上的实例不支持调整高可用组。|
|**400**|FAILED_PRECONDITION|Instance type of 'xxx' is not supported when modifying AvailableGroup|该实例类型暂不支持调整高可用组。|
|**400**|FAILED_PRECONDITION|Doesn't support local system when you want to fore balance|本地系统盘实例不支持强制均衡。|
|**400**|FAILED_PRECONDITION|Doesn't support different vpc_id. Instance's vpc_id is 'xxx' when AvaliableGroup's vpc_id is 'xxx'|该实例与该高可用组关联的实例模板VPC不同。|
|**400**|FAILED_PRECONDITION|Doesn't support different AvailabilityZone. Instance's is 'xxx' when AvaliableGroup's is 'xxx'.|该实例与该高可用组可用区不匹配。|
|**400**|FAILED_PRECONDITION|Doesn't support state as 'xxx',please stop the instance first|当前主机状态为'xxx'，不支持强制均衡，需要将云主机实例关机再操作。|
|**400**|FAILED_PRECONDITION|Doesn't support state as 'xxx', state as stopped or running is expected|仅支持运行中和已停止状态的实例。|
|**400**|FAILED_PRECONDITION|Local_data disk of instance 'xxx' need to be clear when you want to fore balance|请确认清除本地盘数据。|
|**404**|NOT_FOUND|Instance 'xx' not found.|云主机实例不存在。|
|**500**|INTERNAL|Internal server error|系统内部错误，请稍后重试。如果多次尝试失败，请提交工单。|
|**500**|UNKNOWN|Unknown server error|服务暂时不可用，请稍后重试。如果多次尝试失败，请提交工单。|
