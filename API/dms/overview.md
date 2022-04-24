# 数据管理DMS


## 简介
数据管理DMS


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**addPersonalSql**|POST|收藏sql|
|**consoleExplain**|POST|执行计划|
|**consoleGeneralData**|POST|生成数据|
|**consoleSql**|POST|执行sql语句|
|**createTableBatch**|POST|批量建表|
|**databaseList**|POST|获取数据库实例的库列表|
|**deletePersonalSql**|POST|删除收藏sql|
|**downloadExportFile**|GET|表结构数据导出文件下载|
|**exportData**|POST|数据导出|
|**exportStruct**|POST|表结构导出|
|**formatSql**|POST|sql格式化|
|**generalAlterTableSql**|POST|生成修改表结构语句sql|
|**generalCreateTableSql**|POST|生成建表语句sql|
|**getCreateTableBatchSql**|POST|获取批量建表sql|
|**getDmsDomain**|GET|获取Dms域名|
|**getExportDataId**|POST|获取数据导出Id|
|**getExportId**|POST|生成表结构数据导出下载Id|
|**historyImportData**|POST|获取当前实例用户查询导入数据sql历史|
|**historySql**|POST|获取当前实例用户查询sql历史|
|**importDdlDml**|POST|sql导入|
|**login**|POST|rds，drds登录实例|
|**logout**|POST|退出登录|
|**open**|POST|打开实例|
|**openTable**|POST|执行sql语句|
|**queryInstance**|POST|查询用户实例|
|**queryPersonalSqls**|POST|获取当前实例用户收藏sql|
|**sqlTableInfo**|POST|获取sql中建表语句，表中列信息|
|**tableInfo**|POST|获取表元数据|
|**tableList**|POST|获取数据库中的表列表|
|**updatePersonalSql**|POST|更新收藏sql|
