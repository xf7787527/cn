# createBackup


## 描述
创建一个实例全量备份，可以对整个实例所有的数据库进行全量备份。同一时间点，只能有一个正在运行的备份任务

## 请求方式
POST

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/backups

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |实例ID，唯一标识一个实例|
|**backupSpec**|[BackupSpec](createbackup#backupspec)|True| |备份创建信息|

### <div id="backupspec">BackupSpec</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**backupName**|String|True| |备份名称最长支持64个英文字符或等长的中文字符|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](createbackup#result)| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**backupId**|String|备份ID|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
