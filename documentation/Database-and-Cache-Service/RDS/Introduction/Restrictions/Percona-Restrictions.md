# 限制说明
## 配额限制

| 配额         | 限制                                                         |
| ------------ | ------------------------------------------------------------ |
| 只读实例     | 最多创建8个只读实例                                          |
| 标签         | 标签键唯一，最大设置10个。详细信息请参考[资源标签简介](../../Operation-Guide/Tag/Tag-Introduction.md) |
| 实例备份     | <ul><li>自动备份：每天自动备份，备份保留90天</li><li>手动备份：每个地域最多支持5个</li><li>binlog：默认保留24h</li></ul> |
| 日志保留天数 | <ul><li>错误日志：7天</li><li>慢日志统计：7天</li><li>慢日志明细：7天</li></ul> |

## 使用限制

| 操作       | 说明                                                         |
| ---------- | ------------------------------------------------------------ |
| 变配       | 配置调整过程中，RDS 实例可正常使用，调整完成后，会有一个短暂的闪断，需保证应用应用服务有数据库重连机制。 |
| 版本升级   | 版本升级的过程中，主备实例的会先升级备机，然后进行切换，因此会有一个闪断，应用需重连。 |
| 迁移可用区 | 迁移时用户可正常连接到数据库实例，并读写数据。 迁移完成后，有一个短暂的闪断，应用需重连。 |
| 备份       | 主备切换和重启实例会中断当前正在进行的备份操作，要尽量避免在备份进行时进行这两个操作。 |

## 功能限制

### 实例恢复
* 针对已经删除的实例，不支持恢复。

### 创建实例
* 针对单地域的实例数是有限制的，一个地域默认最多支持 5 个实例，如果有更多实例需求，请提交工单。

### 数据库库名保留关键字
```
mysql，information_schema，performance_schema，sys，percona, admin, aurora, replicator, xtrabak, root, mysql, test, eagleye, information_schema, guest, add, analyze, asc, between, blob, call, change, check, condition, continue, cross, current_timestamp, database, day_microsecond, dec, default, desc, distinct, double, each, enclosed, exit, fetch, float8, foreign, goto, having, hour_minute, ignore, infile, insensitiv, int1, int4, interval, iterate, keys, leading, like, lines, localtimestamp, longblob, low_priority, mediumint, minute_microsecond, modifies, no_write_to_binlog, on, optionally, out, precision, purge, read, references, rename, require, revoke, schema, select, set, spatial, sqlexception, sql_big_result, ssl, table, tinyblob, to, true, unique, update, using, utc_timestamp, varchar, when, with, xor, all, and, asensitive, bigint, both, cascade, char, collate, connection, convert, current_date, current_user, databases, day_minute, decimal, delayed, describe, distinctrow, drop, else, escaped, explain, float, for, from, grant, high_priority, hour_second, in, inner, insert, int2, int8, into, join, kill, leave, limit, load, lock, longtext, match, mediumtext, minute_second, natural, null, optimize, or, outer, primary, raid0, reads, regexp, repeat, restrict, right, schemas, sensitive, show, specific, sqlstate, sql_calc_found_rows, starting, terminated, tinyint, trailing, undo, unlock, usage, utc_date, values, varcharacter, where, write, year_month, alter, as, before, binary, by, case, character, column, constraint, create, current_time, cursor, day_hour, day_second, declare, delete, deterministic, div, dual, elseif, exists, false, float4, force, fulltext, group, hour_microsecond, if, index, inout, int, int3, integer, is, key, label, left, linear, localtime, long, loop, mediumblob, middleint, mod, not, numeric, option, order, outfile, procedure, range, real, release, replace, return, rlike, second_microsecond, separator, smallint, sql, sqlwarning, sql_small_result, straight_join, then, tinytext, trigger, union, unsigned, use, utc_time, varbinary, varying, while, x509, zerofill, jcloud_yunding_db_push, jcloudv_push_rw, jcloudv_push_ro, jddb_percona
```

### 数据库账号保留关键字
```
root，admin，os_admin，replicater，monitor，percona, admin, aurora, replicator, xtrabak, root, mysql, test, eagleye, information_schema, guest, add, analyze, asc, between, blob, call, change, check, condition, continue, cross, current_timestamp, database, day_microsecond, dec, default, desc, distinct, double, each, enclosed, exit, fetch, float8, foreign, goto, having, hour_minute, ignore, infile, insensitiv, int1, int4, interval, iterate, keys, leading, like, lines, localtimestamp, longblob, low_priority, mediumint, minute_microsecond, modifies, no_write_to_binlog, on, optionally, out, precision, purge, read, references, rename, require, revoke, schema, select, set, spatial, sqlexception, sql_big_result, ssl, table, tinyblob, to, true, unique, update, using, utc_timestamp, varchar, when, with, xor, all, and, asensitive, bigint, both, cascade, char, collate, connection, convert, current_date, current_user, databases, day_minute, decimal, delayed, describe, distinctrow, drop, else, escaped, explain, float, for, from, grant, high_priority, hour_second, in, inner, insert, int2, int8, into, join, kill, leave, limit, load, lock, longtext, match, mediumtext, minute_second, natural, null, optimize, or, outer, primary, raid0, reads, regexp, repeat, restrict, right, schemas, sensitive, show, specific, sqlstate, sql_calc_found_rows, starting, terminated, tinyint, trailing, undo, unlock, usage, utc_date, values, varcharacter, where, write, year_month, alter, as, before, binary, by, case, character, column, constraint, create, current_time, cursor, day_hour, day_second, declare, delete, deterministic, div, dual, elseif, exists, false, float4, force, fulltext, group, hour_microsecond, if, index, inout, int, int3, integer, is, key, label, left, linear, localtime, long, loop, mediumblob, middleint, mod, not, numeric, option, order, outfile, procedure, range, real, release, replace, return, rlike, second_microsecond, separator, smallint, sql, sqlwarning, sql_small_result, straight_join, then, tinytext, trigger, union, unsigned, use, utc_time, varbinary, varying, while, x509, zerofill, jcloud_yunding_db_push, jcloudv_push_rw, jcloudv_push_ro, jddbaclholder
```
