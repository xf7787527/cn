# 从Spark导入

本文介绍如何通过Spark程序导入数据至分析型云数据库ClickHouse。

#### 前提条件

- 已将云主机的IP地址添加到分析型云数据库ClickHouse的白名单中。

- 已创建与导入数据结构类型对应的云数据库ClickHouse表。

  

#### 操作步骤

1. 准备Spark程序目录结构。

   ```
    find .
   .
   ./build.sbt
   ./src
   ./src/main
   ./src/main/scala
   ./src/main/scala/com
   ./src/main/scala/com/spark
   ./src/main/scala/com/spark/test
   ./src/main/scala/com/spark/test/WriteToCk.scala
   ```

   

2. 编辑build.sbt配置文件并添加依赖。

   ```
   name := "Simple Project"
   
   version := "1.0"
   
   scalaVersion := "2.12.10"
   
   libraryDependencies += "org.apache.spark" %% "spark-sql" % "3.0.0"
   
   libraryDependencies += "ru.yandex.clickhouse" % "clickhouse-jdbc" % "0.2.4"
   ```

   

3. 创建WriteToCk.scala数据并写入程序文件。

```
package com.spark.test

import java.util
import java.util.Properties

import org.apache.spark.sql.execution.datasources.jdbc.JDBCOptions
import org.apache.spark.SparkConf
import org.apache.spark.sql.{SaveMode, SparkSession}
import org.apache.spark.storage.StorageLevel

object WriteToCk {
  val properties = new Properties()
  properties.put("driver", "ru.yandex.clickhouse.ClickHouseDriver")
  properties.put("user", "<yourUserName>")
  properties.put("password", "<yourPassword>")
  properties.put("batchsize","100000")
  properties.put("socket_timeout","300000")
  properties.put("numPartitions","8")
  properties.put("rewriteBatchedStatements","true")

  val url = "jdbc:clickhouse://<yourUrl>:8123/default"
  val table = "<yourTableName>"

  def main(args: Array[String]): Unit = {
    val sc = new SparkConf()
    sc.set("spark.driver.memory", "1G")
    sc.set("spark.driver.cores", "4")
    sc.set("spark.executor.memory", "1G")
    sc.set("spark.executor.cores", "2")

    val session = SparkSession.builder().master("local[*]").config(sc).appName("write-to-ck").getOrCreate()

    val df = session.read.format("csv")
      .option("header", "true")
      .option("sep", ",")
      .option("inferSchema", "true")
      .load("<yourFilePath>")
      .selectExpr(
        "colName1",
        "colName2",
        "colName3",
         ...
      )
      .persist(StorageLevel.MEMORY_ONLY_SER_2)
    println(s"read done")

    df.write.mode(SaveMode.Append).option(JDBCOptions.JDBC_BATCH_INSERT_SIZE, 100000).jdbc(url, table, properties)
    println(s"write done")

    df.unpersist(true)
  }
}
```

参数说明如下：

| 参数                       | 说明                                           |
| -------------------------- | ---------------------------------------------- |
| yourUserName               | 云数据库ClickHouse中创建的数据库账号。         |
| yourPassword               | 数据库账号的密码。                             |
| yourUrl                    | 数据库连接地址。                               |
| yourTableName              | 分析型云数据库ClickHouse中创建的表名。         |
| yourFilePath               | 导入数据文件的存储路径，包含文件地址和文件名。 |
| colName1,colName2,colName3 | 分析型云数据库ClickHouse中创建的列名。         |

4. 编译打包。

   ```
   sbt package
   ```

5. 运行。

```
${SPARK_HOME}/bin/spark-submit  --class "com.spark.test.WriteToCk"  --master local[4] --conf "spark.driver.extraClassPath=${HOME}/.m2/repository/ru/yandex/clickhouse/clickhouse-jdbc/0.2.4/clickhouse-jdbc-0.2.4.jar" --conf "spark.executor.extraClassPath=${HOME}/.m2/repository/ru/yandex/clickhouse/clickhouse-jdbc/0.2.4/clickhouse-jdbc-0.2.4.jar" target/scala-2.12/simple-project_2.12-1.0.jar
```

