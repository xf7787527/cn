# describeDataMigration


## 描述
查询 TiDB 数据迁移任务的信息

## 请求方式
GET

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/migration

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**queryStartTime**|String|False| |查询迁移任务的起始时间，结束时间为当前时间。按任务开始时间查询，默认查询7天（包含当天）|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describedatamigration#result)| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**migrationTasks**|[MigrationTask[]](describedatamigration#migrationtask)| |
### <div id="migrationtask">MigrationTask</div>
|名称|类型|描述|
|---|---|---|
|**taskId**|String|迁移任务ID|
|**migrationType**|String|迁移任务类型，大小写不敏感，FULL_IMPORT:全量数据导入|
|**status**|String|任务状态|
|**startTime**|String|任务开始时间|
|**endTime**|String|任务结束时间|
|**duration**|Integer|任务持续时间，单位分钟|
|**fileName**|String|迁移的数据文件名，包含bucket的全路径，例如dbbak/my_erp/erp.tar.gz|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
