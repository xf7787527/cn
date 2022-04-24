# 数据库备份服务 DBS


## 简介
数据库备份服务


### 版本
v2


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**createBackupPlan**|POST|创建备份计划|
|**createLogicalBackup**|POST|手动触发逻辑备份|
|**createPhysicalBackup**|POST|手动触发物理备份|
|**deleteBackup**|DELETE|删除手动触发生成的备份文件|
|**deleteBackupPlan**|DELETE|删除备份计划|
|**describeBackupPlanAttributes**|GET|查询备份计划详细信息|
|**describeBackupPlans**|GET|查询备份计划概要|
