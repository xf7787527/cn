# modifyBackupPolicy


## 描述
修改TiDB实例备份策略。

## 请求方式
POST

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:modifyBackupPolicy

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**startWindow**|String|False| |自动备份开始时间窗口,例如：00:00-01:00，表示0点到1点开始进行数据库自动备份，备份完成时间则跟实例大小有关，不一定在这个时间范围中该参数只能是以下取值:00:00-01:0001:00-02:00......23:00-24:00|
|**backupPeriod**|String|False| |自动备份的周期，多个取值用英文逗号分隔，支持以下参数，不区分大小写:- Monday：周一 - Tuesday：周二 - Wednesday：周三 - Thursday：周四 - Friday：周五- Saturday：周六- Sunday：周日 例如定义周一和周三备份，则输入为Monday,Wednesday|
|**autoIncBackup**|Boolean|False| |是否开启自动增量备份。 开启后会在没有全量备份的日期自动进行一次增量备份|


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
