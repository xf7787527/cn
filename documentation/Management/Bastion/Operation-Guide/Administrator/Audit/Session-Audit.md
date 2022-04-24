# 会话审计

会话审计专注于事后审计，记录运维人员对主机操作过程中产生的所有会话日志。管理员可通过审计会话定位故障及追溯故障根源。会话支持在线播放以及下载离线播放两种查看方式。


会话审计支持通过时间段、主机IP、来源IP、协议类型等条件进行筛选。支持命令查询，可回放执行过程。


**历史会话**

1、 进入【审计】-【会话审计】-【历史会话】可以查看最近一个月，时间跨度不超过7天的会话审计日志。

   ![](/image/Bastion/historyAudit.png) 

2、 在历史会话页，单击播放即可通过web方式回放会话审计。

3、 在历史会话页，单击下载可下载会话原文件，并通过离线播放器查看

4、 在历史会话页，可以通过时间段、主机IP、来源IP、协议类型等条件定位检索日志

**命令查询**

命令查询模块，可以根据命令全局检索，并查看命令对应的会话详情。

1、 进入【审计】-【会话审计】-【命令查询】页。

  ![](/image/Bastion/mingAudit.png) 

2、 单击详情，列表中的 向右箭头，可以查看命令对应的会话记录

 ![](/image/Bastion/mingAudit2.png) 

3、 在命令查询页，可以通过时间段、主机IP、来源IP、操作类型、内容等条件定位命令执行日志

## 离线播放器

离线播放器用于离线查看下载的会话审计日志。

Mac 系统下载地址：https://open-tools.s3.cn-north-1.jdcloud-oss.com/release/bastion/darwin/20191219/BastionPlayer.tar.gz


Windows 系统下载地址：https://open-tools.s3.cn-north-1.jdcloud-oss.com/release/bastion/win64/20191219/BastionPlayer.tar.gz
