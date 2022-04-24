# createPhysicalBackup


## 描述
手动触发物理备份

## 请求方式
POST

## 请求地址
https://dbs.jdcloud-api.com/v2/regions/{regionId}/backupPlans/{backupPlanId}:createPhysicalBackup

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》]|
|**backupPlanId**|String|True| |备份计划ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|String| |
|**requestId**|String|请求id|


## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
