# 云数据库SQL Server
产品线监控数据的servicecode：sqlserver。监控数据获取时，tags中的role赋值为M。

metric | 中文名称 | 英文名称 | 单位 | 说明
---|--- |--- |---|---
database.sqlserver.kvm.cpu.util | CPU使用率 |CPU Usage | % | 
database.sqlserver.kvm.memory.usage|内存使用率| Memory Usage | % |
database.sqlserver.kvm.disk1.used | 磁盘使用量| Used  Disk | MB | 
database.sqlserver.kvm.disk1.usedpercent | 硬盘使用率 | Disk Usage | % | 
database.sqlserver.kvm.network.bytes.incoming|网络入速率|Network Inbound Rate| Kbps |
database.sqlserver.kvm.network.bytes.outgoing|网络出速率|Network Outbound Rate|Kbps |
database.sqlserver.kvm.disk1.counts.read|硬盘读IO|Disk Read Throughput| 次/秒|
database.sqlserver.kvm.disk1.counts.write|硬盘写IO|Disk Read Throughput| 次/秒|
database.sqlserver.CheckPoint|每秒检查点写入Page数|CheckPoint Write Page Per Second|个|
database.sqlserver.Logins|每秒登录次数|Log In Per Second|次|
database.sqlserver.FullScans|每秒全表扫描次数|Table Scan Per Second|次|
database.sqlserver.QPS|平均每秒SQL执行次数|SQL Execution Per Second|次|
database.sqlserver.SQLCompilations|每秒SQL编译数|SQL Compilation Per Second|次|
database.sqlserver.LockTimeout|每秒锁超时次数|Lock Timeout Per Second|次|
database.sqlserver.Deadlock|每秒死锁次数|Lock Dead Per Second|次|
database.sqlserver.LockWaits|每秒锁等待次数|Lock Wait Per Second|次|
database.sqlserver.TPS|每秒事务数|TPS|个|
database.sqlserver.BufferHit|缓存命中率|Buffer Hits|%|
database.sqlserver.ConnectCount|总连接数|Connections|个|
database.sqlserver.kvm.disk1.currentdiskqueuelength|磁盘队列长度|Disk QueueLength|个|
database.sqlserver.BlockProcess|阻塞进程数|Processes Blocked|个|

# 云数据库MySQL

产品线servicecode为 database ，主备实例和只读实例分属于不同的指标组（groupcode），查询监控数要求如下：

* 主备实例：所属groupcode为database，监控数据获取时，tags中的role赋值为M。
* 只读实例：所属groupcode为db_ro，监控数据获取时，tags中的role赋值为M。
* 单实例：所属groupcode为mysql_standalone，监控数据获取时，tags中的role赋值为M。 

监控指标数据如下：

| database.docker.cpu.util | CPU使用率 | CPU Usage | % |  |
|---|---|---|---|---|
| database.docker.memory.pused | 内存使用率 | Memory Usage | % |  |
| database.docker.disk1.used.kb | 硬盘空间总使用量 | Used Disk | MB |  |
| database.docker.network.incoming | 网络接收流量 | Network Inbound Traffic | Kbps |  |
| database.docker.network.outgoing | 网络发送流量 | Network Outbound Traffic | Kbps |  |
| database.DBMonitor.ByteIO.Input | 实例每秒输入流量 | Instance In Traffic | bps |  |
| database.DBMonitor.ByteIO.Output | 实例每秒输出流量 | Instance Out Traffic | bps |  |
| database.DBMonitor.QPSTPS.QPS | 每秒SQL语句执行次数 | SQL Execution Per Second | 次 |  |
| database.DBMonitor.QPSTPS.TPS | 每秒事务数 | TPS | 个 |  |
| database.DBMonitor.ConnectCount | 当前总连接数 | Connections | 个 |  |
| database.DBMonitor.ConnectCount.Running | 当前活跃连接数 | Current Active Connections | 个 |  |
| database.DBMonitor.TempTable.Count | 临时表数量 | Temporary Tables | 个 |  |
| database.DBMonitor.InnodbBuffer.ReadHitRatio | InnoDB缓存池读命中率 | InnoDB BufferPool Hits | % |  |
| database.DBMonitor.InnodbBuffer.Usage | InnoDB缓存池使用率 | InnoDB BufferPool Usage | % |  |
| database.DBMonitor.InnodbBuffer.DirtyPagePercent | InnoDB缓存池脏块率 | InnoDB BufferPool DirtyBlock | % |  |
| database.DBMonitor.InnodbBytesRW.Read | InnoDB每秒读取量 | InnoDB ReadThroughput Per Second | Bytes |  |
| database.DBMonitor.InnodbBytesRW.Write | InnoDB每秒写入量 | InnoDB WriteThroughput Per Second | Bytes |  |
| database.DBMonitor.InnodbTimesRW.Read | InnoDB每秒向缓冲池的读次数 | InnoDB BufferPool Read Per Second | 次 |  |
| database.DBMonitor.InnodbTimesRW.Write | InnoDB每秒向缓冲池的写次数 | InnoDB BufferPool Write Per Second | 次 |  |
| database.DBMonitor.InnodbLog.Write | InnoDB日志每秒物理写次数 | InnoDB Log Physical Write Per Second | 次 |  |
| database.DBMonitor.InnodbOSLog.Fsyncs | InnoDB日志每秒完成的fsync写数量 | InnoDB Log Fsync Write Per Second | 个 |  |
| database.DBMonitor.CommitTimes.ComSelect | Select | Select | 次/每秒 |  |
| database.DBMonitor.CommitTimes.ComInsert | Insert | Insert | 次/每秒 |  |
| database.DBMonitor.CommitTimes.ComUpdate | Update | Update | 次/每秒 |  |
| database.DBMonitor.CommitTimes.ComDelete | Delete | Delete | 次/每秒 |  |
| database.DBMonitor.CommitTimes.ComReplace | Replace | Replace | 次/每秒 |  |
| database.DBMonitor.CommitTimes.ComReplaceSelect | Replace_Select | Replace_Select | 次/每秒 |  |
| database.DBMonitor.CommitTimes.ComInsertSelect | Insert_Select | Insert_Select | 次/每秒 |  |
| database.DBMonitor.Stored.Userdata | 用户数据使用量 | Used UserData | MB |  |
| database.DBMonitor.Stored.Sysdata | 系统数据使用量 | Used SystemData | MB |  |
| database.DBMonitor.Stored.Logdata | 日志文件使用量 | Used LogFiles | MB |  |
| database.docker.disk.iops.read | 读IOPS | Read IOPS | 次/秒 |  |
| database.docker.disk.iops.write | 写IOPS | Write IOPS | 次/秒 |  |
| database.DBMonitor.Innodb.table_locks_immediate | 表锁次数 | Table locks immediate | 次/秒 |  |
| database.DBMonitor.Innodb.table_locks_waited | 等待表锁次数 | Table locks waited | 次/秒 |  |
| database.DBMonitor.Innodb.innodb_row_lock_waits | InnoDB等待行锁次数 | InnoDB row lock waits | 次/秒 |  |
| database.DBMonitor.Innodb.innodb_row_lock_time_avg | InnoDB平均获取行锁时间 | InnoDB row lock time avg | 毫秒 |  |
| database.DBMonitor.slowlog_count | 慢查询 | Slow query | 次 |  |
| database.DBMonitor.Seconds_Behind_Master | 只读延迟 | Readonly latency | 秒 | 仅只读实例可用 |
| database.DBMonitor.Stored.TmpSpace | 临时表空间使用量 | Temporary Tablespace | MB |  |
| database.DBMonitor.Stored.ShareSpace | 共享表空间使用量 | Shared Tablespace | MB |  |
| database.container.net.tcp.retrans_segs | TCP包重传数 | TCP包重传数 | 次/秒 |  |
| database.container.disk.io.util | 磁盘繁忙 | Disk IO util | % |  |
| database.DBMonitor.InnodbRows.Write | InnoDB每秒插入行数 | InnoDB Rows Insert Per Second | 行/秒 |  |
| database.DBMonitor.InnodbRows.Delete | InnoDB每秒删除行数 | InnoDB Rows Delete Per Second | 行/秒 |  |
| database.DBMonitor.InnodbRows.Update | InnoDB每秒修改行数 | InnoDB Rows Update Per Second | 行/秒 |  |
| database.DBMonitor.InnodbRows.Read | InnoDB每秒读取行数 | InnoDB Rows Read Per Second | 行/秒 |


# 云数据库Percona
产品线servicecode为percona，主备实例和只读实例分属于不同的指标组（groupcode），查询监控数要求如下：

* 主备实例：所属groupcode为percona，监控数据获取时，tags中的role赋值为M。
* 只读实例：所属groupcode为percona_ro，监控数据获取时，tags中的role赋值为M。
* 单实例：所属groupcode为percona_standalone，监控数据获取时，tags中的role赋值为M。 

监控指标数据如下：

| metric | 指标中文名称 | 指标英文名称 | 单位 | 说明 |
|---|---|---|---|---|
| database.docker.cpu.util | CPU使用率 | CPU Usage | % |  |
| database.docker.memory.pused | 内存使用率 | Memory Usage | % |  |
| database.docker.disk1.used.kb | 硬盘空间总使用量 | Used Disk | MB |  |
| database.docker.network.incoming | 网络接收流量 | Network Inbound Traffic | Kbps |  |
| database.docker.network.outgoing | 网络发送流量 | Network Outbound Traffic | Kbps |  |
| database.DBMonitor.ByteIO.Input | 实例每秒输入流量 | Instance In Traffic | bps |  |
| database.DBMonitor.ByteIO.Output | 实例每秒输出流量 | Instance Out Traffic | bps |  |
| database.DBMonitor.QPSTPS.QPS | 每秒SQL语句执行次数 | SQL Execution Per Second | 次 |  |
| database.DBMonitor.QPSTPS.TPS | 每秒事务数 | TPS | 个 |  |
| database.DBMonitor.ConnectCount | 当前总连接数 | Connections | 个 |  |
| database.DBMonitor.ConnectCount.Running | 当前活跃连接数 | Current Active Connections | 个 |  |
| database.DBMonitor.TempTable.Count | 临时表数量 | Temporary Tables | 个 |  |
| database.DBMonitor.InnodbBuffer.ReadHitRatio | InnoDB缓存池读命中率 | InnoDB BufferPool Hits | % |  |
| database.DBMonitor.InnodbBuffer.Usage | InnoDB缓存池使用率 | InnoDB BufferPool Usage | % |  |
| database.DBMonitor.InnodbBuffer.DirtyPagePercent | InnoDB缓存池脏块率 | InnoDB BufferPool DirtyBlock | % |  |
| database.DBMonitor.InnodbBytesRW.Read | InnoDB每秒读取量 | InnoDB ReadThroughput Per Second | Bytes |  |
| database.DBMonitor.InnodbBytesRW.Write | InnoDB每秒写入量 | InnoDB WriteThroughput Per Second | Bytes |  |
| database.DBMonitor.InnodbTimesRW.Read | InnoDB每秒向缓冲池的读次数 | InnoDB BufferPool Read Per Second | 次 |  |
| database.DBMonitor.InnodbTimesRW.Write | InnoDB每秒向缓冲池的写次数 | InnoDB BufferPool Write Per Second | 次 |  |
| database.DBMonitor.InnodbLog.Write | InnoDB日志每秒物理写次数 | InnoDB Log Physical Write Per Second | 次 |  |
| database.DBMonitor.InnodbOSLog.Fsyncs | InnoDB日志每秒完成的fsync写数量 | InnoDB Log Fsync Write Per Second | 个 |  |
| database.DBMonitor.CommitTimes.ComSelect | Select | Select | 次/每秒 |  |
| database.DBMonitor.CommitTimes.ComInsert | Insert | Insert | 次/每秒 |  |
| database.DBMonitor.CommitTimes.ComUpdate | Update | Update | 次/每秒 |  |
| database.DBMonitor.CommitTimes.ComDelete | Delete | Delete | 次/每秒 |  |
| database.DBMonitor.CommitTimes.ComReplace | Replace | Replace | 次/每秒 |  |
| database.DBMonitor.CommitTimes.ComReplaceSelect | Replace_Select | Replace_Select | 次/每秒 |  |
| database.DBMonitor.CommitTimes.ComInsertSelect | Insert_Select | Insert_Select | 次/每秒 |  |
| database.DBMonitor.Stored.Userdata | 用户数据使用量 | Used UserData | MB |  |
| database.DBMonitor.Stored.Sysdata | 系统数据使用量 | Used SystemData | MB |  |
| database.DBMonitor.Stored.Logdata | 日志文件使用量 | Used LogFiles | MB |  |
| database.docker.disk.iops.read | 读IOPS | Read IOPS | 次/秒 |  |
| database.docker.disk.iops.write | 写IOPS | Write IOPS | 次/秒 |  |
| database.DBMonitor.Innodb.table_locks_immediate | 表锁次数 | Table locks immediate | 次/秒 |  |
| database.DBMonitor.Innodb.table_locks_waited | 等待表锁次数 | Table locks waited | 次/秒 |  |
| database.DBMonitor.Innodb.innodb_row_lock_waits | InnoDB等待行锁次数 | InnoDB row lock waits | 次/秒 |  |
| database.DBMonitor.Innodb.innodb_row_lock_time_avg | InnoDB平均获取行锁时间 | InnoDB row lock time avg | 毫秒 |  |
| database.DBMonitor.slowlog_count | 慢查询 | Slow query | 次 |  |
| database.DBMonitor.Seconds_Behind_Master | 只读延迟 | Readonly latency | 秒 | 仅只读实例可用 |
| database.DBMonitor.Stored.TmpSpace | 临时表空间使用量 | Temporary Tablespace | MB |  |
| database.DBMonitor.Stored.ShareSpace | 共享表空间使用量 | Shared Tablespace | MB |  |
| database.container.net.tcp.retrans_segs | TCP包重传数 | TCP包重传数 | 次/秒 |  |
| database.container.disk.io.util | 磁盘繁忙 | Disk IO util | % |


# 云数据库MariaDB

产品线servicecode为mariadb，主备实例和只读实例分属于不同的指标组（groupcode），查询监控数要求如下：

* 主备实例：所属groupcode为mariadb，监控数据获取时，tags中的role赋值为M。
* 只读实例：所属groupcode为mariadb_ro，监控数据获取时，tags中的role赋值为M。
* 单实例：所属groupcode为mariadb_standalone，监控数据获取时，tags中的role赋值为M。


监控指标数据如下：

| metric | 指标中文名称 | 指标英文名称 | 单位 | 说明 |
|---|---|---|---|---|
| database.DBMonitor.ByteIO.Input | 实例每秒输入流量 | Instance In Traffic | bps |  |
| database.DBMonitor.ByteIO.Output | 实例每秒输出流量 | Instance Out Traffic | bps |  |
| database.DBMonitor.QPSTPS.QPS | 每秒SQL语句执行次数 | SQL Execution Per Second | 次 |  |
| database.DBMonitor.QPSTPS.TPS | 每秒事务数 | TPS | 个 |  |
| database.DBMonitor.ConnectCount | 当前总连接数 | Connections | 个 |  |
| database.DBMonitor.ConnectCount.Running | 当前活跃连接数 | Current Active Connections | 个 |  |
| database.DBMonitor.TempTable.Count | 临时表数量 | Temporary Tables | 个 |  |
| database.DBMonitor.InnodbBuffer.ReadHitRatio | InnoDB缓存池读命中率 | InnoDB BufferPool Hits | % |  |
| database.DBMonitor.InnodbBuffer.Usage | InnoDB缓存池使用率 | InnoDB BufferPool Usage | % |  |
| database.DBMonitor.InnodbBuffer.DirtyPagePercent | InnoDB缓存池脏块率 | InnoDB BufferPool DirtyBlock | % |  |
| database.DBMonitor.InnodbBytesRW.Read | InnoDB每秒读取量 | InnoDB ReadThroughput Per Second | Bytes |  |
| database.DBMonitor.InnodbBytesRW.Write | InnoDB每秒写入量 | InnoDB WriteThroughput Per Second | Bytes |  |
| database.DBMonitor.InnodbTimesRW.Read | InnoDB每秒向缓冲池的读次数 | InnoDB BufferPool Read Per Second | 次 |  |
| database.DBMonitor.InnodbTimesRW.Write | InnoDB每秒向缓冲池的写次数 | InnoDB BufferPool Write Per Second | 次 |  |
| database.DBMonitor.InnodbOSLog.Fsyncs | InnoDB日志每秒完成的fsync写数量 | InnoDB Log Fsync Write Per Second | 个 |  |
| database.DBMonitor.InnodbLog.Write | InnoDB日志每秒物理写次数 | InnoDB Log Physical Write Per Second | 次 |  |
| database.DBMonitor.CommitTimes.ComSelect | Select | Select | 次/每秒 |  |
| database.DBMonitor.CommitTimes.ComInsert | Insert | Insert | 次/每秒 |  |
| database.DBMonitor.CommitTimes.ComUpdate | Update | Update | 次/每秒 |  |
| database.DBMonitor.CommitTimes.ComDelete | Delete | Delete | 次/每秒 |  |
| database.DBMonitor.CommitTimes.ComReplace | Replace | Replace | 次/每秒 |  |
| database.DBMonitor.CommitTimes.ComReplaceSelect | Replace_Select | Replace_Select | 次/每秒 |  |
| database.DBMonitor.CommitTimes.ComInsertSelect | Insert_Select | Insert_Select | 次/每秒 |  |
| database.docker.cpu.util | CPU使用率 | CPU Usage | % |  |
| database.docker.memory.pused | 内存使用率 | Memory Usage | % |  |
| database.docker.network.incoming | 网络接收流量 | Network Inbound Traffic | Kbps |  |
| database.docker.network.outgoing | 网络发送流量 | Network Outbound Traffic | Kbps |  |
| database.docker.disk1.used.kb | 硬盘空间总使用量 | Used Disk | MB |  |
| database.DBMonitor.Stored.Userdata | 用户数据使用量 | Used UserData | MB |  |
| database.DBMonitor.Stored.Sysdata | 系统数据使用量 | Used SystemData | MB |  |
| database.DBMonitor.Stored.Logdata | 日志文件使用量 | Used LogFiles | MB |  |
| database.docker.disk.iops.read | 读IOPS | Read IOPS | 次/秒 |  |
| database.docker.disk.iops.write | 写IOPS | Write IOPS | 次/秒 |  |
| database.DBMonitor.Innodb.table_locks_immediate | 表锁次数 | Table locks immediate | 次/秒 |  |
| database.DBMonitor.Innodb.table_locks_waited | 等待表锁次数 | Table locks waited | 次/秒 |  |
| database.DBMonitor.Innodb.innodb_row_lock_waits | InnoDB等待行锁次数 | InnoDB row lock waits | 次/秒 |  |
| database.DBMonitor.Innodb.innodb_row_lock_time_avg | InnoDB平均获取行锁时间 | InnoDB row lock time avg | 毫秒 |  |
| database.DBMonitor.slowlog_count | 慢查询 | Slow query | 次 |  |
| database.DBMonitor.Seconds_Behind_Master | 只读延迟 | Readonly latency | 秒 | 仅只读实例可用 |
| database.DBMonitor.Stored.TmpSpace | 临时表空间使用量 | Temporary Tablespace | MB |  |
| database.DBMonitor.Stored.ShareSpace | 共享表空间使用量 | Shared Tablespace | MB |  |
| database.container.net.tcp.retrans_segs | TCP包重传数 | TCP包重传数 | 次/秒 |  |
| database.container.disk.io.util | 磁盘繁忙 | Disk IO util | % |  |



# 云数据库PostgreSQL
产品线servicecode为pg，主备实例和只读实例分属于不同的指标组（groupcode），查询监控数要求如下：
- 主备实例：所属groupcode为pg，监控数据获取时，tags中的role赋值为M。
- 只读实例：所属groupcode为pg_ro，监控数据获取时，tags中的role赋值为M。

监控指标数据如下：  

metric | 中文名称 | 英文名称 | 单位 | 说明
---|--- |--- |---|--- 
database.DBMonitor.ConnectCount|当前总连接数| Connections|个|
database.DBMonitor.ConnectCount.Running|当前活跃连接数|Current Active Connections|个|
database.docker.memory.pused| 内存使用率 | Memory Usage | % |
database.docker.cpu.util | CPU使用率 | CPU Usage | % | 
database.DBMonitor.Stored.Userdata|用户数据使用量|Used UserData|KB|
database.DBMonitor.Stored.Logdata|日志文件使用量|Used LogFiles|KB|
database.docker.disk1.usage|硬盘空间使用率|Disk Usage|%|
database.docker.disk.iops.read|读IOPS|Read IOPS|次/秒|
database.docker.disk.iops.write|写IOPS|Write IOPS|次/秒|
database.docker.network.bytes.incoming|每秒输入流量|Network Inbound Traffic|bps
database.docker.network.bytes.outgoing|每秒输出流量|Network Outbound Traffic|bps
database.DBMonitor.Rows.Fetched|扫描行数|Rows Fetched|行/秒|
database.DBMonitor.Rows.Returned|返回行数|Rows Returned|行/秒|
database.DBMonitor.Lock.AccessShare|访问共享锁|ACCESS SHARE|个|
database.DBMonitor.Lock.RowShare|行共享锁|ROW SHARE|个|
database.DBMonitor.Lock.RowExclusive|行唯一锁|ROW EXCLUSIVE|个|
database.DBMonitor.Lock.ShareUpdateExclusive|共享更新唯一锁|SHARE UPDATE EXCLUSIVE|个|
database.DBMonitor.Lock.Share|共享锁|SHARE|个|
database.DBMonitor.Lock.ShareRowExclusive|共享行唯一锁|SHARE ROW EXCLUSIVE| 个|
database.DBMonitor.Lock.Exclusive|唯一锁|EXCLUSIVE|个|
