# 限制说明
## 配额限制

| 配额         | 限制                                                         |
| ------------ | ------------------------------------------------------------ |
| 只读实例     | 最多创建8个只读实例                                          |
| 标签         | 标签键唯一，最大设置10个。详细信息请参考[资源标签简介](../../Operation-Guide/Tag/Tag-Introduction.md) |
| 实例备份     | <ul><li>自动备份：每天自动备份，备份保留7天</li><li>手动备份：每个地域最多支持5个</li><li>binlog：默认保留24h</li></ul> |
| 日志保留天数 | <ul><li>错误日志：7天</li><li>慢日志统计：7天</li><li>慢日志明细：7天</li></ul> |

## 使用限制

| 操作       | 说明                                                         |
| ---------- | ------------------------------------------------------------ |
| 变配       | 配置调整过程中，RDS 实例可正常使用，调整完成后，会有一个短暂的闪断，需保证应用应用服务有数据库重连机制。 |
| 版本升级   | 版本升级的过程中，主备实例的会先升级备机，然后进行切换，因此会有一个闪断，应用需重连。 |
| 迁移可用区 | 迁移时用户可正常连接到数据库实例，并读写数据。 迁移完成后，有一个短暂的闪断，应用需重连。 |
| 备份       | 主备切换和重启实例会中断当前正在进行的备份操作，要尽量避免在备份进行时进行这两个操作。 |



## 功能限制

### 数据库版本升级
* 现在不支持数据库版本的升级。例如 MySQL 5.6 升级到 MySQL 5.7。

### 实例恢复
* 针对已经删除的实例，不支持恢复。

### 创建实例
* 针对单地域的实例数是有限制的，一个地域默认最多支持 5 个实例，如果有更多实例需求，请提交工单。

### 数据库库名保留关键字
```
add、admin、administrator、all、alter、and、any、as、asc、aurora、authorization、backup、begin、between、break、browse、bulk、bulkadmin、by、cascade、case、check、checkpoint、close、clustered、coalesce、collate、column、commit、compute、constraint、contains、containstable、continue、convert、create、cross、current、current_date、current_time、current_timestamp、current_user、cursor、database、dbcc、dbcreator、deallocate、declare、default、delete、deny、desc、disk、diskadmin、distinct、distributed、distribution、double、drop、dummy、dump、eagleye、else、end、errlvl、escape、except、exec、execute、exists、exit、false、fetch、file、fillfactor、for、foreign、freetext、freetexttable、from、full、function、goto、grant、group、guest、having、holdlock、identity、identity_insert、identitycol、if、in、index、inner、insert、intersect、into、is、join、key、kill、left、like、lineno、load、master、model、msdb、mssqld、mssqlsystemresource、national、nocheck、nonclustered、not、null、nullif、of、off、offsets、on、open、opendatasource、openquery、openrowset、openxml、option、or、order、outer、over、percent、plan、precision、primary、print、proc、procedure、processadmin、public、raiserror、read、readtext、reconfigure、references、replication、restore、restrict、return、revoke、right、rollback、root、rowcount、rowguidcol、rule、sa、save、schema、securityadmin、select、serveradmin、session_user、set、setupadmin、setuser、shutdown、some、statistics、sysadmin、system_user、table、tempdb、textsize、then、to、top、tran、transaction、trigger、true、truncate、tsequal、union、unique、update、updatetext、use、user、values、varying、view、waitfor、when、where、while、with、writetexttest、analyze、asensitive、before、bigint、binary、blob、both、call、change、char、character、condition、connection、databases、day_hour、day_microsecond、day_minute、day_second、dec、decimal、delayed、describe、deterministic、distinctrow、div、dual、each、elseif、enclosed、escaped、explain、、float、float4、float8、force、fulltext、high_priority、hour_microsecond、hour_minute、hour_second、ignore、infile、information_schema、inout、insensitive、int、int1、int2、int3、int4、int8、integer、interval、iterate、keys、label、leading、leave、limit、linear、lines、localtime、localtimestamp、lock、long、longblob、longtext、loop、low_priority、match、mediumblob、mediumint、mediumtext、middleint、minute_microsecond、minute_second、mod、modifies、mysql、natural、no_write_to_binlog、numeric、optimize、optionally、out、outfile、percona、purge、raid0、range、reads、real、regexp、release、rename、repeat、replace、replicator、require、rlike、schemas、second_microsecond、sensitive、separator、show、smallint、spatial、specific、sql、sql_big_result、sql_calc_found_rows、sql_small_result、sqlexception、sqlstate、sqlwarning、ssl、starting、straight_join、terminated、tinyblob、tinyint、tinytext、trailing、、undo、unlock、unsigned、usage、using、utc_date、utc_time、utc_timestamp、varbinary、varchar、varcharacter、write、x509、xor、xtrabak、year_month、zerofill、performance_schema、sys、os_admin、replicater、monitor

```

### 数据库账号保留关键字
```
add、admin、all、alter、analyze、and、as、asc、asensitive、aurora、before、between、bigint、binary、blob、both、by、call、cascade、case、change、char、character、check、collate、column、condition、connection、constraint、continue、convert、create、cross、current_date、current_time、current_timestamp、current_user、cursor、database、databases、day_hour、day_microsecond、day_minute、day_second、dec、decimal、declare、default、delayed、delete、desc、describe、deterministic、distinct、distinctrow、div、double、drop、dual、each、eagleye、else、elseif、enclosed、escaped、exists、exit、explain、false、fetch、float、float4、float8、for、force、foreign、from、fulltext、goto、grant、group、guest、having、high_priority、hour_microsecond、hour_minute、hour_second、if、ignore、in、index、infile、inner、inout、insensitive、insert、int、int1、int2、int3、int4、int8、integer、interval、into、is、iterate、jcloud_yunding_db_push、jcloudv_push_ro、jcloudv_push_rw、jddbaclholder、join、key、keys、kill、label、leading、leave、left、like、limit、linear、lines、load、localtime、localtimestamp、lock、long、longblob、longtext、loop、low_priority、match、mediumblob、mediumint、mediumtext、middleint、minute_microsecond、minute_second、mod、modifies、monitor、mysql、natural、no_write_to_binlog、not、null、numeric、on、optimize、option、optionally、or、order、os_admin、out、outer、outfile、percona、precision、primary、procedure、purge、raid0、range、read、reads、real、references、regexp、release、rename、repeat、replace、replicater、replicator、require、restrict、return、revoke、right、rlike、schema、schemas、second_microsecond、select、sensitive、separator、set、show、smallint、spatial、specific、sql、sql_big_result、sql_calc_found_rows、sql_small_result、sqlexception、sqlstate、sqlwarning、ssl、starting、straight_join、table、terminated、test、then、tinyblob、tinyint、tinytext、to、trailing、trigger、true、undo、union、unique、unlock、unsigned、update、usage、use、using、utc_date、utc_time、utc_timestamp、values、varbinary、varchar、varcharacter、varying、when、where、while、with、write、x509、xor、xtrabak、year_month、zerofill、information_schema

```
