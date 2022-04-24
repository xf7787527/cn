# describeBackups


## 描述
查看该实例下所有备份的详细信息

## 请求方式
GET

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/backups

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |实例ID，唯一标识一个实例|
|**pageNumber**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,∞)。pageNumber为-1时，返回所有数据页码；超过总页数时，显示最后一页。|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为10，取值范围：[10,100]，且为10的整数倍。|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describebackups#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**backups**|[Backup[]](describebackups#backup)| |
|**totalCount**|Integer|总记录数|
### <div id="backup">Backup</div>
|名称|类型|描述|
|---|---|---|
|**backupId**|String|备份ID|
|**backupName**|String|备份名称，最长支持64个英文字符或等长的中文字符|
|**instanceId**|String|备份所属实例ID|
|**backupStatus**|String|备份状态|
|**backupStartTime**|String|备份开始时间|
|**backupEndTime**|String|备份结束时间|
|**backupType**|String|备份类型|
|**backupMode**|String|备份模式|
|**backupSizeByte**|Long|整个备份集大小，单位：Byte|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
