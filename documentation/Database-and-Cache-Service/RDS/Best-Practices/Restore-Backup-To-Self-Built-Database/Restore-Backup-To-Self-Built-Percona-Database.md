# 将备份文件恢复到自建数据库

您可以将云数据库 Percona 实例的备份数据恢复到自建数据库中。

## 注意事项
* 自建数据库版本需要和备份文件的源数据库版本一致。
* 备份的解压软件只支持在 Linux 下执行。
* 解压工具的系统软件依赖：tee，python 版本 >= 2.7。
* 当前系统已经安装 percona xtrabackup, 如果没有安装，请参考 [官方手册](https://www.percona.com/doc/percona-xtrabackup/2.4/index.html)。
     - MySQL版本为8.0时，需要xtrabackup >= 8.0.14；
     - MySQL版本为5.6、5.7时，需要xtrabackup >= 2.4.8；
     - MariaDB版本为10.2时，需要xtrabackup >= 2.4.8；
     - Percona版本为5.7时，需要xtrabackup >= 2.4.9；

## 操作说明
1. 安装环境依赖，见注意事项DB。
2. 下载备份的解压工具，[点击下载](http://jddb-common-public.oss.cn-north-1.jcloudcs.com/general_mysql_backup_extract_tool.zip)，并解压，工具名 `mysql_backup_extract.py`，使用示例如下
    
    ```Python
     # 增加解压工具文件可执行权限
     chmod mysql_backup_extract.py +x
    
     # 查看帮助手册
     python mysql_backup_extract.py -h
     
     # 解压云数据库 Percona 实例的备份数据
     python mysql_backup_extract.py  -v 5.7 -f ./backup.xbstream
    ```
3. 下载备份文件

    ```SQL
    wget -c '<数据备份下载地址>' -O <自定义备份文件名>.xbstream

    -c：启动断点续传
    -O：将下载的结果保存为指定的文件，注意文件的后者必须是 .xbstream
    ```

4. 解压备份数据，解压后的文件会保存在当前目录的子目录 tmp_snapshot 中，假设当前目录为 $HOME。

    ```Python
     python mysql_backup_extract.py -v 5.7 -f <自定义备份文件名>.xbstream
    
     -v 参数可以不指定，默认：5.7，具体 -v 后面可以跟什么变量可以通过 -h 查看帮助手册得知。
    ```

5. 恢复解压好的备份文件。工具中包含多个配置文件，根据实际的实例类型及版本进行使用,对应关系见下方表格。  

    |实例类型及版本|选择配置文件|
    |---|---|
    |MySQL 5.5、5.6、5.7|mysql-5.cnf|
    |MySQL 8.0|mysql-8.cnf|
    |MariaDB|mariadb-10.2.cnf|
    |Percona|percona-7.cnf|  


    ```Python
     xtrabackup --defaults-file=$HOME/percona-7.cnf --parallel=1 --prepare --target-dir=$HOME/tmp_snapshot
    ```   
    
    当看到 ***innobackupex completed OK!*** 时， 表明执行成功，你就可以继续下一步操作了。

6. 修改文件属主，并确定文件所属为 MySQL 用户

   ```Python
   chown -R mysql:mysql $HOME/tmp_snapshot
   ```

7. 启动 Percona 进程。

   ```Python
   mysqld_safe --defaults-file=$HOME/percona-7.cnf --user=mysql --datadir=$HOME/tmp_snapshot &
   ```

8. 登录 Percona 数据库

   ```SQL
   mysql -uroot -p
   ```

- 密码默认为空， 直接回车即可。
