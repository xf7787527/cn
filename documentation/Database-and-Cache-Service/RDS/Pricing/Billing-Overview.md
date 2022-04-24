# 计费概述

## 计费项

| 计费项                 | 计费方式及价格                                               |
| ---------------------- | ------------------------------------------------------------ |
| 实例（主备、灾备实例） | <ul><li>计费方式：提供包年包月或按配置计费，具体信息请查看[计费方式](billing-overview#pricing)。</li><li>价格：购买实例的价格与所选地域、规格、存储等配置相关，具体价格信息请查看[实例收费标准](billing-overview#charge)。</li> |
| 只读实例               | <ul><li>计费方式：提供包年包月或按配置计费。</li><li>价格：具体价格信息请查看[实例收费标准](billing-overview#charge)。</li> |
| 存储空间               | <ul><li>计费方式：提供包年包月或按配置计费。</li><li>价格：存储空间的价格与所选存储类型相关，具体价格信息请前往[购买页面](https://rds-console.jdcloud.com/rds/create?regionId=cn-north-1)查看。</li> |
| 根据备份创建新的实例   | <ul><li>计费方式：提供包年包月或按配置计费。</li><li>价格：与新购一个实例收费相同，具体价格信息请查看[实例收费标准](billing-overview#charge)。</li> |
| 备份空间               | 暂不收费                                                     |
| SQL审计                | 暂不收费                                                     |
| 数据库代理             | 暂不收费                                                     |

## <div id="pricing">计费方式</div>

云数据库RDS支持两种计费方式

* **包年包月**（预付费模式）

  适合长期需求，相比按量计费模式，价格更为实惠，且购买时长越长，折扣越多。

* **按配置计费**（后付费模式）

  适合短期需求，用完可立即释放实例，节省成本。

## <div id="charge">实例收费标准</div>
云数据库 RDS 实例的收费标准依据实例的规格和存储空间两个维度，并且不同的实例类型收费标准也是不一样的，详情请查看
- [MySQL 价格总览](./Price-Overview/MySQL-Price.md)
- [Percona 价格总览](./Price-Overview/Percona-Price.md)
- [MariaDB 价格总览](./Price-Overview/MariaDB-Price.md)
- [PostgreSQL 价格总览](./Price-Overview/PostgreSQL-Price.md)
- [SQL Server 价格总览](./Price-Overview/SQL-Server-Price.md)


## 实例到期/欠费说明
以下是云数据库 RDS 实例欠费或者到期的保留政策。

|计费类型|实例到期/欠费处理逻辑|
|---|---|
|包年包月|实例到期后，会被标记为到期状态，数据库服务不可用，如 7 天内未续费，则 7 天后会被删除，同时实例对应的备份文件也会被删除，实例数据不能恢复。|
|按配置|实例欠费后，会被标记为欠费状态，数据库服务不可用，如 7 天后仍欠费，则会被删除，同时实例对应的备份文件也会被删除，实例数据不能恢复。|

云数据库 RDS 实例在到期或欠费后会有消息提醒，请注意查收，及时续费，以免数据被删除无法找回。
计费与通知相关信息，详情请查看：

- [预付费计费说明](../../../Finance/Billing/Billing-method/Prepay.md)
- [后付费计费说明](../../../Finance/Billing/Billing-method/Postpay.md) 
