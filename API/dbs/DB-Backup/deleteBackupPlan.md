# deleteBackupPlan


## 描述
删除备份计划

## 请求方式
DELETE

## 请求地址
https://dbs.jdcloud-api.com/v2/regions/{regionId}/backupPlans/{backupPlanId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》]|
|**backupPlanId**|String|True| |备份计划ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求id|


## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
