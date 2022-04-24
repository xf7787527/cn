# 通过JDBC方式连接ClickHouse

本文通过代码示例说明如何通过JDBC方式连接ClickHouse进行应用开发。

## 操作步骤

1. 使用Eclipse或其他IDE工具创建Maven项目并引入ClickHouse驱动依赖包。

```
<dependency>
   <groupId>ru.yandex.clickhouse</groupId>
   <artifactId>clickhouse-jdbc</artifactId>
   <version>0.2.4</version>
</dependency>
```



2. 编写应用程序代码。

   以下代码演示了如何使用JDBC驱动连接实例，使用过程需修改实例连接串和端口参数。如果应用和ClickHouse实例在同一个VPC环境，请使用实例VPC地址，如果不在相同的VPC环境则需使用实例外网地址。

```
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.sql.Timestamp;
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;

public class Main4 {
  private static final String DATE_FORMAT = "yyyy-MM-dd HH:mm:ss";
  private static final SimpleDateFormat SIMPLE_DATE_FORMAT = new SimpleDateFormat(DATE_FORMAT);

  public static void main(String[] args) throws ClassNotFoundException, SQLException, InterruptedException, ParseException {
    String url = "your url";
    String username = "your username";
    String password = "your password";

    Class.forName("ru.yandex.clickhouse.ClickHouseDriver");
    String connectionStr = "jdbc:clickhouse://" + url + ":8123";

    try (Connection connection = DriverManager.getConnection(connectionStr, username, password);
         Statement stmt = connection.createStatement()) {

      {
        String createTableDDL = "create table test_table on cluster default " +
            "(id UInt32, " +
            "dt_str String, " +
            "dt_col DateTime) " +
            "engine=ReplicatedMergeTree('/clickhouse/tables/{database}/{table}/{shard}', '{replica}')" +
            "partition by toYYYYMM(dt_col)" +
            "order by (id)" +
            "primary key (id)" +
            "sample by (id)" +
            "settings index_granularity = 8192;";
        stmt.execute(createTableDDL);
        System.out.println("create local table done.");
      }
      {
        String createTableDDL = "create table test_dist on cluster default " +
            "as default.test_table " +
            "engine=Distributed(default, default, test_table, rand());";
        stmt.execute(createTableDDL);
        System.out.println("create distributed table done");
      }

      System.out.println("write 100000 rows...");
      long startTime = System.currentTimeMillis();

      // Write 10 batch
      for (int batch = 0; batch < 10; batch++) {
        StringBuilder sb = new StringBuilder();

        // Build one batch
        sb.append("insert into test_dist values(" + (batch * 10000) + ", '2020-02-19 16:00:00', '2020-02-19 16:00:00')");
        for (int row = 1; row < 10000; row++) {
          sb.append(", (" + (batch * 10000 + row) + ", '2020-02-19 16:00:00', '2020-02-19 16:00:00')");
        }

        // Write one batch: 10000 rows
        stmt.execute(sb.toString());
      }

      long endTime = System.currentTimeMillis();
      System.out.println("total time cost to write 10W rows: " + (endTime - startTime) + "ms");

      Thread.sleep(2 * 1000);

      System.out.println("Select count(id)...");
      try (ResultSet rs = stmt.executeQuery("select count(id) from test_dist");) {
        while (rs.next()) {
          int count = rs.getInt(1);
          System.out.println("id count: " + count);
        }
      }

      try (ResultSet rs = stmt.executeQuery("select id, dt_str, dt_col from test_dist limit 10");) {
        while (rs.next()) {
          int id = rs.getInt(1);
          String dateStr = rs.getString(2);
          Timestamp time = rs.getTimestamp(3);

          String defaultDate = SIMPLE_DATE_FORMAT.format(new Date(time.getTime()));
          System.out.println("id: " + id
              + ", date_str:" + dateStr
              + ", date_col:" + defaultDate);
        }
      }
    }
  }
}
```

