研发效能度量模块将各系统信息如任务、项目、质量、发布、代码等进行数据ETL，通过多种维度数据融合对研发效能度量进行可视化报表展示，通过定义的指标集对关切据进行分析，促进组织的敏捷转型，和团队执行的持续优化。![img](http://devops-minio.jdcloud.com/doc-image/All-Image/agile_practices.assets/clip_image002.jpg)

## 管理视角仪表盘

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/agile_practices.assets/clip_image004.jpg)

## 研发视角仪表盘

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/agile_practices.assets/clip_image006.jpg)

## 深度洞察

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/agile_practices.assets/clip_image008.jpg)

## 下钻分析

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/agile_practices.assets/clip_image010.jpg)

## 需求可视化报表

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/agile_practices.assets/clip_image006.jpg)

## 代码可视化报表

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/agile_practices.assets/clip_image012.jpg)

## 测试可视化报表

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/agile_practices.assets/clip_image014.jpg)

## 部署可视化报表

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/agile_practices.assets/clip_image016.jpg)

## 项目可视化报表

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/agile_practices.assets/clip_image018.jpg)

## 自定义报表分析

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/agile_practices.assets/clip_image020.jpg)

## 图例说明

### 卡片状态累积流图

?> 累积流图(Cumulative Flow Diagram – CFD图) 是一种能让你快速了解项目或产品工作概况的图表

总体来说你能得到两个方面的数据价值：

1. 在CFD图中你可以找到工作状态的特定信息：例如有多少工作已经完成、正在进行或待办，工作进展如何等最基本的项目信息。
2. 帮助你发现团队可能面临的各种问题和流动瓶颈，从而适当改善团队工作过程方式。



> 一个简单的CFD图

![累积流图示例 ](http://devops-minio.jdcloud.com/doc-image/All-Image/agile_practices.assets/累积流图示例.jpg "累积流图示例")

横轴：代表迭代的周期，一般以2周为一个迭代

纵轴：代表卡片数量

色块：代表不同卡片状态下的卡片数量累积情况。

平均周期时间（LeadTime）：反映一种状态到另一种状态的平均周期时间，如从需求分析到需求完成的平均周期时间。

在制品数量（WIP）：某个时刻下未完成的卡片数量。



> 不同CFD图的案例分析

* **案例1：在制品持续堆积**

![在制品持续堆积 ](http://devops-minio.jdcloud.com/doc-image/All-Image/agile_practices.assets/在制品持续堆积.jpeg "在制品持续堆积")

案例分析：

`图中“进入开发线”与“进入测试线”之间的高度，以及“进入测试线”和“完成线”之间的高度都在持续增长，说明开发环节、和测试环节的在制品在持续堆积。为什么出现这样的现象呢？需要结合看团队的看板，并且与团队一起分析才能知道原因。但是肯定一点：团队没有设置在制品限制，任由在制品持续堆积。`


* **案例2：批次性交付**

![批次性交付 ](http://devops-minio.jdcloud.com/doc-image/All-Image/agile_practices.assets/批次性交付.jpeg "批次性交付")

案例分析：

`图中，“完成线”呈阶梯式上升，像爬楼梯一样。可以判断出这个团队采取了固定的发布节奏，每到发布的时候，累积流图就上了一层楼梯，发布之前，“完成线”是平的。然后，观察“进入Backlog线”，也是呈现台阶状，而且与“完成线”上台阶的节奏一致。可见该团队的Backlog填充节奏与交付节奏保持高度一致。再次，观察“进入测试线”与“完成线”之间的高度越来越高，但是我们无法判断出是由于“测试进行”列的在制品堆积，还是由于测试完成后发布工作碰到了问题，导致测试完了不能发布所造成。因此，需要在看板上将测试环节、发布环节细化，才能判断出问题所在。`


* **案例3：集体停滞**

![集体停滞 ](http://devops-minio.jdcloud.com/doc-image/All-Image/agile_practices.assets/集体停滞.jpeg "集体停滞")

案例分析：

`上图中，在很长一段时间内，“进入开发线”、“进入测试线”、和“完成线”都是平的，可见这段时间内没有任何工作项流入开发，也没有任何工作项完成。怎么会这样呢？`

`常见的原因有以下几种可能性：`

    1. 这段时间是法定假日
    
    2. 团队整体调走去其他项目
    
    3. 运维有故障，团队所有人去帮助运维解决故障

`到底什么原因，需要引导团队分析。`


* **案例4：某个环节无法启动**

![无法启动 ](http://devops-minio.jdcloud.com/doc-image/All-Image/agile_practices.assets/某个环节无法启动.jpeg "无法启动")

案例分析：

`图中“完成线”与“进入测试线”在一段时间内是平的，由于“进入测试线”比“进入完成”线先平了一段时间，所以貌似是由于测试无法开始，导致无法完成。可以判断出，测试环节遇到了阻碍导致测试工作无法开始。同时，“进入开发线”持续攀升。由此可以判断出，开发人员在测试环节遇到阻碍的时候，没有去帮助解除阻碍，反而继续拉动工作项开发，导致开发环节的在制品持续堆积。`


* **案例5：吞吐率不稳定**

![吞吐率不稳定 ](http://devops-minio.jdcloud.com/doc-image/All-Image/agile_practices.assets/吞吐率不稳定.jpeg "吞吐率不稳定")

案例分析：

`上图中，“进入开发线”的斜率稳定，而“完成线”与“进入测试”线的斜率陡然上升。可见，开发和测试的吞吐率突然大幅度提升。要记住：团队的效率不会忽然上升，一定发生了重大变化。`

`常见的可能性是：`

    1. 团队忘记了更新看板。某一天，忽然想起来了，于是大量卡片完成。
    
    2. 团队刚接受了需求拆分的培训，开始尝试将大需求拆小，导致交付的数量上升。
    
    3. 团队迫于管理层的进度压力，拼命赶工，一段时间内集中完成大量需求。这样做一定是有副作用的，过一段时间，团队的吞吐率不仅会下降，反而会花更多的时间修改前段时间赶工埋下的雷。


* **案例6：Scrum团队**

![scrum团队 ](http://devops-minio.jdcloud.com/doc-image/All-Image/agile_practices.assets/scrum团队.jpeg "scrum团队")

案例分析：

`图中，从原点到结束，所有线”汇集到一点，这说明：在最后一天，团队的看板上是空的。此外，“进入Backlog”线是平的，即：在这段时间内，没有新需求进入到Backlog里。这是典型的Scrum团队的特征。此外，仔细观察可以发现，在前半段时间，开发环节的在制品持续堆积，而测试环节的在制品较少；而后，测试环节的在制品开始多起来，而开发环节的在制品开始减少。可见这个Scrum 团队需要改进Sprint周期的工作流，避免大批量开发，让工作平衡流动。`


* **案例7：中途抛弃需求**

案例分析：

`正常的情况下，所有的线都是向上走的。如果有线向下走，一定是有工作项抛弃的情况。图中，除了“进入完成线”，每条线都向下走，而向下的高度相同，可见是测试列抛弃了工作项，从而“进入开发线”和“进入完成线”都同时向下走。这种情况团队要回顾：为什么工作项在启动研发后抛弃？这种浪费如何避免？`


---


### 卡片状态停留时长散点图

?> 停留时长散点图(Control-Chart) 是一种用于回顾计算每个已完成卡片在某一个状态（或多个状态上）花费的时长，并将结果映射到时间线上，通过数据来衡量团队过程改进的表现能力。

> 一个简单的散点图

![散点图 ](http://devops-minio.jdcloud.com/doc-image/All-Image/agile_practices.assets/停留时长散点图.jpg "散点图")

横轴：代表迭代的周期，一般以2周为一个迭代。

纵轴：代表停留时长数。

选择项：用户可以随意指定想要统计的状态下停留时长（默认全选，可以勾选自己感兴趣状态下的停留时长）。

蓝色小点：代表截止到今天已经完成的卡片及在所选择状态下曾经停留时长的汇总。

绿色折线：代表每天已完成卡片停留时长均值的趋势。

黑色直线：代表整个迭代的停留时长均线，会随着卡片的完成自动调整均线数值。

`建议：在迭代结束时或者在迭代回顾会上来一起分析并作为下次迭代启动的数据参考，也可以结合累积流图一起分析找到团队的工作瓶颈`

