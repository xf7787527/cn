# createDataMigration


## 描述
查询 TiDB 数据迁移任务的信息

## 请求方式
POST

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/migration

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**migrationType**|String|True| |迁移任务类型，支持以下类型（大小写不敏感）：-FULL_IMPORT:全量数据导入|
|**importTask**|[FullImportTask](createdatamigration#fullimporttask)|True| |使用 TiDB Lightning 进行的数据迁移任务|

### <div id="fullimporttask">FullImportTask</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ossLink**|String|True| |用户上传到对象存储OSS上的备份文件的路径。|
|**dataSizeGB**|Integer|True| |未压缩的整个数据文件或数据目录的大小,单位GB|

## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**202**|OK|
