## 使用常用 nGQL（CRUD 命令）

本文介绍 Nebula Graph 查询语言的基础语法，包括用于 Schema 创建和常用增删改查操作的语句。

####  图空间和 Schema

一个 Nebula Graph 实例由一个或多个图空间组成。每个图空间都是物理隔离的，用户可以在同一个实例中使用不同的图空间存储不同的数据集。

![Nebula Graph and graph spaces](https://docs-cdn.nebula-graph.com.cn/docs-2.0/2.quick-start/nebula-graph-instance-and-graph-spaces.png)

为了在图空间中插入数据，需要为图数据库定义一个 Schema。 Schema 是由如下几部分组成。

| 组成部分            | 说明                                               |
| :------------------ | :------------------------------------------------- |
| 点（Vertex）        | 表示现实世界中的实体。一个点可以有一个或多个标签。 |
| 标签（Tag）         | 点的类型，定义了一组描述点类型的属性。             |
| 边（Edge）          | 表示两个点之间**有方向**的关系。                   |
| 边类型（Edge type） | 边的类型，定义了一组描述边的类型的属性。           |



####  检查 Nebula Graph 集群的机器状态

!!! Note

    首先建议检查机器状态，确保所有的 Storage 服务连接到了 Meta 服务。执行命令`SHOW HOSTS`查看机器状态。

```ngql
nebula> SHOW HOSTS;
+-------------+-----------+-----------+--------------+----------------------+------------------------+
| Host        | Port      | Status    | Leader count | Leader distribution  | Partition distribution |
+-------------+-----------+-----------+--------------+----------------------+------------------------+
| "storaged0" | 9779      | "ONLINE"  | 0            | "No valid partition" | "No valid partition"   |
| "storaged1" | 9779      | "ONLINE"  | 0            | "No valid partition" | "No valid partition"   |
| "storaged2" | 9779      | "ONLINE"  | 0            | "No valid partition" | "No valid partition"   |
| "Total"     | __EMPTY__ | __EMPTY__ | 0            | __EMPTY__            | __EMPTY__              |
+-------------+-----------+-----------+--------------+----------------------+------------------------+
```

在返回结果中，查看**Status**列，可以看到所有 Storage 服务都在线。

#### 异步实现创建和修改

!!! caution

    Nebula Graph 中执行如下创建和修改操作，是异步实现的。要在**下一个**心跳周期之后才能生效，否则访问会报错。为确保数据同步，后续操作能顺利进行，请等待 2 个心跳周期（20 秒）。

- `CREATE SPACE`
- `CREATE TAG`
- `CREATE EDGE`
- `ALTER TAG`
- `ALTER EDGE`
- `CREATE TAG INDEX`
- `CREATE EDGE INDEX`

!!! Note

    默认心跳周期是 10 秒。

####  创建和选择图空间

- 创建图空间

    ```ngql
    CREATE SPACE [IF NOT EXISTS] <graph_space_name> (
    [partition_num = <partition_number>,]
    [replica_factor = <replica_number>,]
    vid_type = {FIXED_STRING(<N>) | INT64}
    )
    [COMMENT = '<comment>'];
    ```

    <!-- `charset`和`collate`当前只有一个可选值，忽略。
    charset = <charset>
        collate = <collate>
    -->
    
- 列出创建成功的图空间

    ```ngql
    nebula> SHOW SPACES;
    ```

- 选择数据库

    ```ngql
    USE <graph_space_name>;
    ```

#### 示例

1. 执行如下语句创建名为`basketballplayer`的图空间。

    ```ngql
    nebula> CREATE SPACE basketballplayer(partition_num=15, replica_factor=1, vid_type=fixed_string(30));
    ```

2. 执行命令`SHOW HOSTS`检查分片的分布情况，确保平衡分布。

    ```ngql
    nebula> SHOW HOSTS;
    +-------------+-----------+-----------+--------------+----------------------------------+------------------------+
    | Host        | Port      | Status    | Leader count | Leader distribution              | Partition distribution |
    +-------------+-----------+-----------+--------------+----------------------------------+------------------------+
    | "storaged0" | 9779      | "ONLINE"  | 5            | "basketballplayer:5"             | "basketballplayer:5"   |
    | "storaged1" | 9779      | "ONLINE"  | 5            | "basketballplayer:5"             | "basketballplayer:5"   |
    | "storaged2" | 9779      | "ONLINE"  | 5            | "basketballplayer:5"             | "basketballplayer:5"   |
    | "Total"     |           |           | 15           | "basketballplayer:15"            | "basketballplayer:15"  |
    +-------------+-----------+-----------+--------------+----------------------------------+------------------------+
    ```

    如果** Leader distribution **分布不均匀，请执行命令`BALANCE LEADER`重新分配。

3. 选择图空间`basketballplayer`。

    ```ngql
    nebula[(none)]> USE basketballplayer;
    ```

    用户可以执行命令`SHOW SPACES`查看创建的图空间。

    ```ngql
    nebula> SHOW SPACES;
    +--------------------+
    | Name               |
    +--------------------+
    | "basketballplayer" |
    +--------------------+
    ```

#### 创建 Tag 和 Edge type
```ngql
CREATE {TAG | EDGE} {<tag_name> | <edge_type>}(<property_name> <data_type>
[, <property_name> <data_type> ...])
[COMMENT = '<comment>'];
```

#### 示例

创建 Tag:`player`和`team`，以及 Edge type:`follow`和`serve`。说明如下表。

| 名称   | 类型      | 属性                             |
| :----- | :-------- | :------------------------------- |
| player | Tag       | name (string), age (int)         |
| team   | Tag       | name (string)                    |
| follow | Edge type | degree (int)                     |
| serve  | Edge type | start_year (int), end_year (int) |

```ngql
nebula> CREATE TAG player(name string, age int);

nebula> CREATE TAG team(name string);

nebula> CREATE EDGE follow(degree int);

nebula> CREATE EDGE serve(start_year int, end_year int);
```

#### 插入点和边

用户可以使用`INSERT`语句，基于现有的 Tag 插入点，或者基于现有的 Edge type 插入边。
- 插入点

    ```ngql
    INSERT VERTEX [IF NOT EXISTS] <tag_name> (<property_name>[, <property_name>...])
    [, <tag_name> (<property_name>[, <property_name>...]), ...]
    {VALUES | VALUE} <vid>: (<property_value>[, <property_value>...])
    [, <vid>: (<property_value>[, <property_value>...];
    ```

    `VID`是 Vertex ID 的缩写，`VID`在一个图空间中是唯一的。

- 插入边

    ```ngql
    INSERT EDGE [IF NOT EXISTS] <edge_type> (<property_name>[, <property_name>...])
    {VALUES | VALUE} <src_vid> -> <dst_vid>[@<rank>] : (<property_value>[, <property_value>...])
    [, <src_vid> -> <dst_vid>[@<rank>] : (<property_name>[, <property_name>...]), ...];
    ```


#### 示例

- 插入代表球员和球队的点。

    ```ngql
    nebula> INSERT VERTEX player(name, age) VALUES "player100":("Tim Duncan", 42);

    nebula> INSERT VERTEX player(name, age) VALUES "player101":("Tony Parker", 36);

    nebula> INSERT VERTEX player(name, age) VALUES "player102":("LaMarcus Aldridge", 33);

    nebula> INSERT VERTEX team(name) VALUES "team203":("Trail Blazers"), "team204":("Spurs");
    ```

- 插入代表球员和球队之间关系的边。

    ```ngql
    nebula> INSERT EDGE follow(degree) VALUES "player101" -> "player100":(95);

    nebula> INSERT EDGE follow(degree) VALUES "player101" -> "player102":(90);

    nebula> INSERT EDGE follow(degree) VALUES "player102" -> "player100":(75);

    nebula> INSERT EDGE serve(start_year, end_year) VALUES "player101" -> "team204":(1999, 2018),"player102" -> "team203":(2006,  2015);
    ```

#### 查询数据

- GO 语句可以根据指定的条件遍历数据库。`GO`语句从一个或多个点开始，沿着一条或多条边遍历，返回`YIELD`子句中指定的信息。

- Fetch 语句可以获得点或边的属性。

- LookUP 语句是基于索引的，和`WHERE`子句一起使用，查找符合特定条件的数据。

- Match 语句是查询图数据最常用的，可以灵活的描述各种图模式，但是它依赖索引去匹配 Nebula Graph 中的数据模型，性能也还需要调优。
- `GO`

    ```ngql
    GO [[<M> TO] <N> STEPS ] FROM <vertex_list>
    OVER <edge_type_list> [{REVERSELY | BIDIRECT}]
    [ WHERE <conditions> ]
    [YIELD [DISTINCT] <return_list>]
    [{SAMPLE <sample_list> | LIMIT <limit_list>}]
    [| GROUP BY {col_name | expr | position} YIELD <col_name>]
    [| ORDER BY <expression> [{ASC | DESC}]]
    [| LIMIT [<offset>,] <number_rows>];
    ```

- `FETCH`

  - 查询 Tag 属性

    ```ngql
    FETCH PROP ON {<tag_name>[, tag_name ...] | *}
    <vid> [, vid ...]
    [YIELD <return_list> [AS <alias>]];
    ```

  - 查询边属性

    ```ngql
    FETCH PROP ON <edge_type> <src_vid> -> <dst_vid>[@<rank>] [, <src_vid> -> <dst_vid> ...]
    [YIELD <output>];
    ```

- `LOOKUP`

    ```ngql
    LOOKUP ON {<vertex_tag> | <edge_type>}
    [WHERE <expression> [AND <expression> ...]]
    [YIELD <return_list> [AS <alias>]];
    ```

- `MATCH`

    ```nGQL
    MATCH <pattern> [<WHERE clause>] RETURN <output>;
    ```

#### `GO`语句示例

- 从 VID 为`player101`的球员开始，沿着边`follow`找到连接的球员。

    ```ngql
    nebula> GO FROM "player101" OVER follow;
    +-------------+
    | follow._dst |
    +-------------+
    | "player100" |
    | "player102" |
    +-------------+
    ```

- 从 VID 为`player101`的球员开始，沿着边`follow`查找年龄大于或等于 35 岁的球员，并返回他们的姓名和年龄，同时重命名对应的列。

    ```ngql
    nebula> GO FROM "player101" OVER follow WHERE $$.player.age >= 35 \
            YIELD properties($$).name AS Teammate, properties($$).age AS Age;
    +--------------+-----+
    | Teammate     | Age |
    +--------------+-----+
    | "Tim Duncan" | 42  |
    +--------------+-----+
    ```

    | 子句/符号 | 说明                           |
    | :-------- | :----------------------------- |
    | `YIELD`   | 指定该查询需要返回的值或结果。 |
    | `$$`      | 表示边的终点。                 |
    | `\`       | 表示换行继续输入。             |

- 从 VID 为`player101`的球员开始，沿着边`follow`查找连接的球员，然后检索这些球员的球队。为了合并这两个查询请求，可以使用管道符或临时变量。

  - 使用管道符

    ```ngql
    nebula> GO FROM "player101" OVER follow YIELD dst(edge) AS id | \
            GO FROM $-.id OVER serve YIELD properties($$).name AS Team, \
            properties($^).name AS Player;
    +-----------------+---------------------+
    | Team            | Player              |
    +-----------------+---------------------+
    | "Trail Blazers" | "LaMarcus Aldridge" |
    +-----------------+---------------------+
    ```

    | 子句/符号 | 说明                                                       |
    | :-------- | :--------------------------------------------------------- |
    | `$^`      | 表示边的起点。                                             |
    | `|`       | 组合多个查询的管道符，将前一个查询的结果集用于后一个查询。 |
    | `$-`      | 表示管道符前面的查询输出的结果集。                         |

  - 使用临时变量

    !!! Note

        当复合语句作为一个整体提交给服务器时，其中的临时变量会在语句结束时被释放。

    ```ngql
    nebula> $var = GO FROM "player101" OVER follow YIELD dst(edge) AS id; \
            GO FROM $var.id OVER serve YIELD properties($$).name AS Team, \
            properties($^).name AS Player;
    +-----------------+---------------------+
    | Team            | Player              |
    +-----------------+---------------------+
    | "Trail Blazers" | "LaMarcus Aldridge" |
    +-----------------+---------------------+
    ```

### `FETCH`语句示例

查询 VID 为`player100`的球员的属性。

```ngql
nebula> FETCH PROP ON player "player100";
+----------------------------------------------------+
| vertices_                                          |
+----------------------------------------------------+
| ("player100" :player{age: 42, name: "Tim Duncan"}) |
+----------------------------------------------------+
```

!!! Note

    `LOOKUP`和`MATCH`的示例在下文的索引部分查看。

## 修改点和边

用户可以使用`UPDATE`语句或`UPSERT`语句修改现有数据。

`UPSERT`是`UPDATE`和`INSERT`的结合体。当使用`UPSERT`更新一个点或边，如果它不存在，数据库会自动插入一个新的点或边。

!!! Note

    每个 partition 内部，`UPSERT` 操作是一个串行操作，所以执行速度比执行 `INSERT` 或 `UPDATE` 慢很多。其仅在多个 partition 之间有并发。

### nGQL 语法

- `UPDATE`点

    ```ngql
    UPDATE VERTEX <vid> SET <properties to be updated>
    [WHEN <condition>] [YIELD <columns>];
    ```

- `UPDATE`边

    ```ngql
    UPDATE EDGE <source vid> -> <destination vid> [@rank] OF <edge_type>
    SET <properties to be updated> [WHEN <condition>] [YIELD <columns to be output>];
    ```

- `UPSERT`点或边

    ```ngql
    UPSERT {VERTEX <vid> | EDGE <edge_type>} SET <update_columns>
    [WHEN <condition>] [YIELD <columns>];
    ```

#### 示例

- 用`UPDATE`修改 VID 为`player100`的球员的`name`属性，然后用`FETCH`语句检查结果。

    ```ngql
    nebula> UPDATE VERTEX "player100" SET player.name = "Tim";

    nebula> FETCH PROP ON player "player100";
    +---------------------------------------------+
    | vertices_                                   |
    +---------------------------------------------+
    | ("player100" :player{age: 42, name: "Tim"}) |
    +---------------------------------------------+
    ```

- 用`UPDATE`修改某条边的`degree`属性，然后用`FETCH`检查结果。

    ```ngql
    nebula> UPDATE EDGE "player101" -> "player100" OF follow SET degree = 96;

    nebula> FETCH PROP ON follow "player101" -> "player100";
    +----------------------------------------------------+
    | edges_                                             |
    +----------------------------------------------------+
    | [:follow "player101"->"player100" @0 {degree: 96}] |
    +----------------------------------------------------+
    ```

- 用`INSERT`插入一个 VID 为`player111`的点，然后用`UPSERT`更新它。

    ```ngql
    nebula> INSERT VERTEX player(name,age) values "player111":("David West", 38);

    nebula> UPSERT VERTEX "player111" SET player.name = "David", player.age = $^.player.age + 11 \
            WHEN $^.player.name == "David West" AND $^.player.age > 20 \
            YIELD $^.player.name AS Name, $^.player.age AS Age;
    +---------+-----+
    | Name    | Age |
    +---------+-----+
    | "David" | 49  |
    +---------+-----+
    ```

####  删除点和边

- 删除点

    ```ngql
    DELETE VERTEX <vid1>[, <vid2>...]
    ```

- 删除边

    ```ngql
    DELETE EDGE <edge_type> <src_vid> -> <dst_vid>[@<rank>]
    [, <src_vid> -> <dst_vid>...]
    ```

#### 示例

- 删除点

    ```ngql
    nebula> DELETE VERTEX "player111", "team203";
    ```

- 删除边

    ```ngql
    nebula> DELETE EDGE follow "player101" -> "team204";
    ```

#### 索引

用户可以通过CREATE INDEX语句为 Tag 和 Edge type 增加索引。

!!! caution "使用索引必读"

    `MATCH`和`LOOKUP`语句的执行都依赖索引，但是索引会导致写性能大幅降低（降低 90%甚至更多）。请不要随意在生产环境中使用索引，除非很清楚使用索引对业务的影响。
    
    必须为“已写入但未构建索引”的数据重建索引，否则无法在`MATCH`和`LOOKUP`语句中返回这些数据。

- 创建索引

    ```ngql
    CREATE {TAG | EDGE} INDEX [IF NOT EXISTS] <index_name>
    ON {<tag_name> | <edge_name>} ([<prop_name_list>]) [COMMENT = '<comment>'];
    ```

- 重建索引

    ```ngql
    REBUILD {TAG | EDGE} INDEX <index_name>;
    ```

!!! Note

    为没有指定长度的变量属性创建索引时，需要指定索引长度。在 utf-8 编码中，一个中文字符占 3 字节，请根据变量属性长度设置合适的索引长度。例如 10 个中文字符，索引长度需要为 30。

#### 基于索引的`LOOKUP`和`MATCH`示例

确保`LOOKUP`或`MATCH`有一个索引可用。如果没有，请先创建索引。

找到 Tag 为`player`的点的信息，它的`name`属性值为`Tony Parker`。

```nGQL
// 为 name 属性创建索引 player_index_1。
nebula> CREATE TAG INDEX player_index_1 ON player(name(20));

// 重建索引确保能对已存在数据生效。
nebula> REBUILD TAG INDEX player_index_1
+------------+
| New Job Id |
+------------+
| 31         |
+------------+

// 使用 LOOKUP 语句检索点的属性。
nebula> LOOKUP ON player WHERE player.name == "Tony Parker" \
        YIELD properties(vertex).name AS name, properties(vertex).age AS age;
+-------------+---------------+-----+
| VertexID    | name          | age |
+-------------+---------------+-----+
| "player101" | "Tony Parker" | 36  |
+-------------+---------------+-----+

// 使用 MATCH 语句检索点的属性。
nebula> MATCH (v:player{name:"Tony Parker"}) RETURN v;
+-----------------------------------------------------+
| v                                                   |
+-----------------------------------------------------+
| ("player101" :player{age: 36, name: "Tony Parker"}) |
+-----------------------------------------------------+
```