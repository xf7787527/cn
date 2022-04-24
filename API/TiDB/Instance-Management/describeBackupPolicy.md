# describeBackupPolicy


## 描述
查看实例当前的备份备份策略。

## 请求方式
GET

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:describeBackupPolicy

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describebackuppolicy#result)| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**startWindow**|String|自动备份开始时间窗口，范围00:00-23:59，时间范围差不得小于30分钟。<br>例如：00:00-01:00，表示0点到1点开始进行数据库自动备份，备份完成时间则跟实例大小有关，不保证在这个时间范围中完成<br>|
|**retentionPeriod**|Integer|自动备份保留周期，单位天,缺省为7天，范围7-730|
|**backupPeriod**|String|自动备份的周期，多个取值用英文逗号分隔，支持以下参数，不区分大小写：<br>- Monday：周一<br>- Tuesday：周二<br>- Wednesday：周三<br>- Thursday：周四<br>- Friday：周五<br>- Saturday：周六<br>- Sunday：周日<br>例如定义周一和周三备份，则输入为Monday,Wednesday<br>|
|**autoIncBackup**|Boolean|是否开启自动增量备份|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
