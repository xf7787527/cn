# deleteBackup


## 描述
删除TiDB的备份，仅允许删除用户生成的备份，系统自动备份不允许删除。

## 请求方式
DELETE

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/backups/{backupId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**backupId**|String|True| |备份ID|

## 请求参数
无


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**202**|OK|
