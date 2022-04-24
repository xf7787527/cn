
## 登录引擎

创建图计算引擎后，点击登录引擎，进入命令行输入页面。可使用以下命令行进行算法调用。

![1645344687416](https://github.com/jdcloudcom/cn/blob/cn-joygraph/image/Elastic-Compute/Graph-Compute/1644734972967.png)

![1645517215032](https://github.com/jdcloudcom/cn/blob/cn-joygraph/image/Elastic-Compute/Graph-Compute/1645517215032.png)

## 上传数据文件

图计算前，需将顶点中的主键和边中的src,dst字段从业务值转换为编码值

#### 1、生成编码映射表

在进行此前处理前请保证加工顶点表和边表符合下面格式

图计算要求顶点表格式为:

| 字段（名称自定义 | 类型(类型不限) | 注释     |
| :--------------- | :------------- | :------- |
| Key              | String         | 顶点值   |
| vtype            | String         | 顶点类型 |
| Prop1            | String         | 属性1    |
| OtherProp        | String         | 其他属性 |

图计算要求边表格式为:

| 字段（名称自定义） | 类型(类型不限) | 含义     |
| :----------------- | :------------- | :------- |
| Src                | String         | 源顶点   |
| dst                | String         | 目的顶点 |
| etype              | String         | 边类型   |
| Prop1              | String         | 属性1    |
| OtherProp          | String         | 其他属性 |

#### 2、输入数据

输入包括一个或多个无权图文件输入，需要将文件格式为文本文件或二进制文件。可通过页面中的 上传数据文件 功能将准备好的数据文件上传。默认上传路径为 /data

- 输入文件以边为单位，每行表示一个边数据，包含起始顶点id（src）和终点顶点id（dst），类型均为整数，用空格隔开。输入文件每行格式示例

```
      0 1
```

  该行数据表示一条从顶点0指向顶点1的边。

- 二进制文件输入

  当输入为二进制文件时，src和dst均用40bit的整数表示；每个边数据大小为80bit。

- 平台在 /openjoygraph/build/joyEngine/data 中内置了以下三个测试文件，可用于初步测试使用。

![1645517088185](https://github.com/jdcloudcom/cn/blob/cn-joygraph/image/Elastic-Compute/Graph-Compute/1645517088185.png)



## 图算法

平台共内置了13个图算法

包括传统图算法：lpa、wcc、sssp、apsp、louvain，

图深度学习算法：line、deepwalk、node2vec、metapath2vec、gcn、 unsupervised_graphsage、supervised_graphsage、gat

### 传统图算法

- 传统图算法执行文件均在/openjoygraph/build/joyEngine/bin下，执行命令为：

```
  cd /openjoygraph/build/joyEngine
  ./bin/对应算法文件 

  查看执行结果：
  第①步 cd /openjoygraph/build/joyEngine/output/算法名(如lpa、wcc)
  第②步 ls 
  会返回如下内容：
  part-r-0.txt   part-r-11.txt  part-r-14.txt  part-r-17.txt  part-r-2.txt   part-r-22.txt  part-r-25.txt  part-r-28.txt  part-r-30.txt  part-r-5.txt  part-r-8.txt
  part-r-1.txt   part-r-12.txt  part-r-15.txt  part-r-18.txt  part-r-20.txt  part-r-23.txt  part-r-26.txt  part-r-29.txt  part-r-31.txt  part-r-6.txt  part-r-9.txt
  part-r-10.txt  part-r-13.txt  part-r-16.txt  part-r-19.txt  part-r-21.txt  part-r-24.txt  part-r-27.txt  part-r-3.txt   part-r-4.txt   part-r-7.txt
  第③步 cat 具体的文件名即可 ，如cat part-r-24.txt
```

#### 1.lpa算法
  - 执行命令：
    - 第①步 cd /openjoygraph/build/joyEngine
    - 第②步 ./bin/lpa -i ./data/facebook_combined.txt -o ./output/lpa/ -n 20
```
参数说明：
./data/facebook_combined.txt：数据文件路径
./output/lpa/：结果文件输出路径
20：迭代计算次数
```

#### 2.wcc算法
  - 执行命令：
    - 第①步 cd /openjoygraph/build/joyEngine
    - 第②步 ./bin/wcc -i ./data/facebook_combined.txt -o ./output/wcc/
```
参数说明：
./data/facebook_combined.txt：数据文件路径
./output/wcc/：结果文件输出路径
```

#### 3.sssp算法
  - 执行命令：
    - 第①步 cd /openjoygraph/build/joyEngine
    - 第②步 ./bin/sssp -i ./data/facebook_combined.txt -o  ./output/sssp/ -r 1
```
参数说明：
./data/facebook_combined.txt ：数据文件路径
./output/lpa/：结果文件输出路径
1：root顶点，0和正整数，取值范围为:顶点数值区间
```

#### 4.apsp算法
  - 执行命令：
    - 第①步 cd /openjoygraph/build/joyEngine
    - 第②步 ./bin/apsp -i ./data/facebook_combined.txt -o ./output/apsp/
```
参数说明：
./data/facebook_combined.txt：数据文件路径
./output/apsp/：结果文件输出路径
```

==此算法执行时间较长==

#### 5.louvain算法
  - 执行命令：
    - 第①步 cd /openjoygraph/build/joyEngine
    - 第②步 ./bin/louvain -i ./data/facebook_combined.txt -o ./output/louvain/ -n 20 -w true 
```
参数说明：
./data/facebook_combined.txt：数据文件路径
./output/louvain/：结果文件输出路
20：计算轮数。louvain算法第一阶段计算，每轮计算增益度一直都在增加，则最多计算iteration轮
true：true: 输入的边文件是有向图;false: 输入的边文件是无向图
```

### 图深度学习算法

#### 执行命令及参数

  - 执行命令：
    - 第①步 cd /openjoygraph
    - 第②步 rm -rf /data/line
    - 第③步
      ``` 
      python -m joyTf --model line  --mode train --max_id 67179 --meta_file_dir /openjoygraph/data/supervised_data/Reddit/reddit_meta_file.json --node_dir /openjoygraph/data/supervised_data/Reddit/node_ids.txt --edge_dir /openjoygraph/data/supervised_data/Reddit/edge_ids.txt --checkpoint_dir /data/line/checkpoint --num_epochs 1  ...
      ```
```
执行命令：

参数说明：
line：line、deepwalk、node2vec、metapath2vec、gcn、 unsupervised_graphsage、supervised_graphsage、gat 代表选择相应的算法

如果使用metapath2vec算法，第三步的执行命令应更换为：
python -m joyTf --model metapath2vec --mode train --max_id 44905 --meta_file_dir /openjoygraph/build/joyEngine/data/metafile.json --node_dir /openjoygraph/build/joyEngine/data/node.txt --edge_dir /openjoygraph/build/joyEngine/data/edge.txt --checkpoint_dir /data/line/checkpoint --num_epochs 1 --meta_path [0-0],[0-0-0] --path_weight 0.6,0.5
如果使用unsupervised_graphsage算法，第三步的执行命令应更换为：
python -m joyTf --model unsupervised_graphsage  --mode train --max_id 67179 --meta_file_dir /openjoygraph/build/joyEngine/data/metafile.json  --node_dir /openjoygraph/build/joyEngine/data/node.txt --edge_dir /openjoygraph/build/joyEngine/data/edge.txt --checkpoint_dir /data/line/checkpoint --num_epochs 1 
其他算法只需替换mode中的值即可

train：运行模式，默认"train"，可选“evaluate”和“save_embedding”
max_id：对应顶点数据文件中的最大ID： max_id=node_num-1
meta_file_dir：metafile文件路径，metafile格式说明见下文
node_dir：顶点数据文件路径
edge_dir：编数据文件位置
checkpoint_dir ：中间运算结果保存路径
num_epochs：训练轮数，默认5。如果不知道合适的epoch，num_epochs可以先设置的小一点，从1开始设置，逐渐提高。
```

#### metafile格式

最简单的metafile.json文件格式如下

```
{
    "v_type_nums":1,
    "v_nums":44906,
    "e_type_nums":1,
    "e_nums":562575,
    "is_directed":true,
    "v_descs":{
        "0":{
            "type_name":"type0",
            "type_v_nums":44906,
            "labeled":0,
            "enum_nums":0,
            "numerical_nums":0,
            "features":{}
        }
    }
}
v_type_nums：几种类型的顶点
v_nums：顶点总数，要和node_dir文件中的行数相对应
e_type_nums：几种边
e_nums：边总数，要和edge_dir文件中的行数相对应
is_directed：是否有向图
type_name：自定义名称
type_v_nums：顶点总数，要和node_dir文件中的行数相对应
labeled：目前测试固定取0
enum_nums：目前测试固定取0
numerical_nums：目前测试固定取0
features：目前测试固定为空
```

#### checkpoint文件注意点

如果之前传参数有错误需要重新跑，需要将checkpoint文件夹中的中间运算结果文件全部删除，
否则会继续断点续跑，之前产生的错误数据会影响到新的运算结果。