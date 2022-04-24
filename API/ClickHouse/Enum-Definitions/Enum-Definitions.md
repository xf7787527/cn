# 枚举类型定义

## engineVersion 引擎版本

| 取值       | 说明                       |
| ---------- | -------------------------- |
| 19.17.4.11 | ClickHouse 19.17.4.11 版本 |
| 20.3.18.10 | ClickHouse 20.3.18.10 版本 |
| 20.8.2.3   | ClickHouse  20.8.2.3 版本  |

## instanceStatus 实例状态

| 取值     | 说明   |
| -------- | ------ |
| BUILDING | 创建中 |
| RUNNING  | 运行   |


## accountStatus 账号状态

| 取值              | 说明       |
| ----------------- | ---------- |
| BUILDING          | 创建中     |
| RUNNING           | 运行       |
| DELETING          | 删除中     |
| PASSWORDUPDATING  | 重置密码中 |
| PRIVILEGEUPDATING | 权限修改中 |

## privilege 账号访问权限

| 取值 | 说明 |
| ---- | ---- |
| ro   | 只读 |
| rw   | 读写 |

## instanceStorageType 存储类型 
| 取值    | 说明    |
| ------- | ------- |
| EBS_SSD | SSD云盘 |