# 实例规格类型

实例是京东云为您业务提供计算服务的最小单位，不同实例通过其规格类型及具体规格来标识相应的计算、内存、存储及网络能力。同时，您创建实例时指定的实例类型决定了实例的硬件配置，您可基于需要部署运行的应用类型及规模选择适当的实例规格类型及具体规格。

以下为当前京东云在售的实例规格类型信息，不同地域可售卖实例类型及规格不完全相同，请以实例创建页面所显示为准。具体在售实例规格类型根据不同应用场景可以分为：

* 通用型：[通用共享型](instance-type-family#user-content-1)、[通用标准型](instance-type-family#user-content-2)
* 计算优化型：[计算优化共享型](instance-type-family#user-content-9)、[计算优化密集型](instance-type-family#user-content-11)、[计算优化标准型](instance-type-family#user-content-3)
* 内存优化型：[内存优化标准型](instance-type-family#user-content-4)、[内存优化增强型](instance-type-family#user-content-17)
* 突发性能型：[突发性能型](instance-type-family#user-content-12)
* 高频计算型：[高频计算通用型](instance-type-family#user-content-5)
* 存储优化型：[存储优化IO型](instance-type-family#user-content-7)、[存储优化大数据型](instance-type-family#user-content-8)
* GPU型：[GPU标准型](instance-type-family#user-content-6)、[GPU虚拟化型](instance-type-family#user-content-10)
* 裸金属：[标准型](instance-type-family#user-content-13)、[存储优化IO型](instance-type-family#user-content-14)、[安全增强内存优化型](instance-type-family#user-content-15)

## 通用型
通用型当前提供通用共享型及通用标准型，为您提供均衡的计算及内存资源，可满足大部分业务场景下的需求。其中通用标准型中每一个vCPU都对应一个处理器的超线程核，其vCPU与内存比为1:4。

### 通用共享型

<div id="user-content-1"></div>

通用共享型实例采用非绑定CPU调度模式，每个vCPU会被分配到任何空闲的超线程核上，不同实例的vCPU可以互相争抢物理CPU资源。通用共享型实例拥有高性价比的优点，但由于需要对资源进行争抢，在性能上可能会受到不同程度的影响。


**规格类型特点：**

* vCPU与内存比为1:1、1:2或1:4，提供多种处理器内存配比。
* 处理器： 
	* 第二代：2.4 GHz主频的Intel Xeon Gold 6148（Skylake）处理器
	* 第一代：2.1 GHz主频的Intel Xeon E5-2683 v4（Broadwell）处理器
* 支持以下类型云硬盘：
	* 通用型SSD云盘
	* 性能型SSD云盘
	* 容量型HDD云盘
* 适用场景：
	* 访问量较小的个人网站初级阶段
	* 微服务
	* 测试环境

**实例规格**

第二代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|g.s2.micro|1|1|2|1
|g.s2.small|1|2|2|1
|g.s2.medium|1|4|2|1
|g.s2.large|2|8|2|2
|g.s2.xlarge|4|16|4|4
|g.s2.2xlarge|8|32|4|4

第一代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|g.s1.micro|1|1|2|1
|g.s1.small|1|2|2|1

### 通用标准型

<div id="user-content-2"></div>

**规格类型特点:**

* vCPU与内存比为1:4（g.n1.xlarge_m规格除外）
* 处理器：
	* 第四代：2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器，基于京刚架构将虚拟化和管理开销卸载至自研专用硬件，大幅提升存储网络性能
	* 第三代：2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器  
	* 第二代：
	  * 2.4 GHz主频的Intel Xeon Gold 6148（Skylake）处理器 或 2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器  
	  * 2.6 GHz主频的AMD EPYC ROME 处理器
	* 第一代：2.1 GHz主频的Intel Xeon E5-2683 v4（Broadwell）处理器
* 支持以下类型云硬盘：
	* 通用型SSD云盘
	* 性能型SSD云盘
	* 容量型HDD云盘
* 镜像使用限制：
	* 3代及以上Intel系列，AMD系列仅支持云盘系统盘镜像
* 适用场景：
	* 各种类型和规模的企业级应用
	* 中小型数据系统、缓存、搜索集群
	* 数据分析和计算
	* 计算集群、依赖内存的数据处理

**实例规格**

第四代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|g.n4.medium|1|4|2|1
|g.n4.large|2|8|2|2
|g.n4.xlarge|4|16|4|4
|g.n4.2xlarge|8|32|4|8
|g.n4.3xlarge|12|48|8|8
|g.n4.4xlarge|16|64|8|8
|g.n4.6xlarge|24|96|8|16
|g.n4.8xlarge|32|128|8|16
|g.n4.12xlarge|48|192|8|16
|g.n4.16xlarge|64|256|8|32
|g.n4.24xlarge|96|352|16|32

第三代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|g.n3.medium|1|4|2|1
|g.n3.large|2|8|2|2
|g.n3.xlarge|4|16|4|4
|g.n3.2xlarge|8|32|4|4
|g.n3.3xlarge|12|48|8|4
|g.n3.4xlarge|16|64|8|4
|g.n3.6xlarge|24|96|8|4
|g.n3.8xlarge|32|128|8|4
|g.n3.12xlarge|48|192|8|4
|g.n3.16xlarge|64|256|8|4
|g.n3.18xlarge|72|288|8|4

第二代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|g.n2.medium|1|4|2|1
|g.n2.large|2|8|2|2
|g.n2.xlarge|4|16|4|4
|g.n2.2xlarge|8|32|4|4
|g.n2.4xlarge|16|64|8|4
|g.n2.8xlarge|32|128|8|4
|g.n2.16xlarge|64|256|8|4
|g.n2.18xlarge|72|288|8|4

<div id="user-content-13"></div>

第二代（AMD规格）
实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|g.n2a.large|2|8|2|2
|g.n2a.xlarge|4|16|4|4
|g.n2a.2xlarge|8|32|4|4
|g.n2a.4xlarge|16|64|8|4
|g.n2a.8xlarge|32|128|8|4
|g.n2a.16xlarge|64|256|8|4
|g.n2a.32xlarge|128|512|8|4


第一代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数|备注
:---|:---|:---|:---|:---|:---
g.n1.medium|1|4|2|1 | |
g.n1.large|2|8|2|2 | |
g.n1.xlarge_m	|4|12|4|4|*
g.n1.xlarge|4|16|4|4 | |	
g.n1.2xlarge|8|32|4|4 | |	
g.n1.4xlarge|16|64|8|4 |	|
g.n1.8xlarge|32|128|8|4 |	 |

## 计算优化型
计算优化型当前提供计算优化共享型及计算优化标准型，其中计算优化标准型可满足每一个vCPU都对应一个Intel Xeon处理器的超线程核，为您提供高性能的计算资源。
### 计算优化共享型

<div id="user-content-9"></div>

计算优化共享型实例采用非绑定CPU调度模式，每个vCPU会被分配到任何空闲的超线程核上，不同实例的vCPU可以互相争抢物理CPU资源。计算优化共享型实例拥有高性价比的优点，但由于需要对资源进行争抢，在性能上可能会受到不同程度的影响。

**规格类型特点：**

* vCPU与内存比约为1:2
* 处理器：2.4 GHz主频的Intel Xeon Gold 6148 （Skylake）处理器
* 支持以下类型云硬盘：
	* 通用型SSD云盘
	* 性能型SSD云盘
	* 容量型HDD云盘
* 镜像使用限制：
	* 3代及以上Intel系列，AMD系列仅支持云盘系统盘镜像
* 适用场景：
	* 小规模机器学习、数据分析
	* 小规模爬虫
	* 小规模批量计算

**实例规格**

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡对列数
:---|:---|:---|:---|:---
|c.s2.large|2|4|2|2
|c.s2.xlarge|4|8|4|4
|c.s2.2xlarge|8|16|4|4

### 计算优化密集型

<div id="user-content-11"></div>

**规格类型特点：**

* vCPU与内存比约为1:1
* 处理器：
	* 第四代：2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器，基于京刚架构将虚拟化和管理开销卸载至自研专用硬件，大幅提升存储网络性能
	* 第二代：2.4 GHz主频的Intel Xeon Gold 6148 （Skylake）处理器 或 2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器  
* 支持以下类型云硬盘：
	* 通用型SSD云盘
	* 性能型SSD云盘
	* 容量型HDD云盘
* 适用场景：
	* 批处理工作负载
	* Web前端服务器
	* 大型多人在线游戏（MMO）前端
	* 数据分析、批量计算、视频编码
	* 高性能科学和工程应用

**实例规格**

第四代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|c.c4.large|2|2|2|2
|c.c4.xlarge|4|4|4|4
|c.c4.2xlarge|8|8|4|4
|c.c4.3xlarge|12|12|8|4
|c.c4.4xlarge|16|16|8|4

第二代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|c.c2.large|2|2|2|2
|c.c2.xlarge|4|4|4|4
|c.c2.2xlarge|8|8|4|4
|c.c2.3xlarge|12|12|8|4
|c.c2.4xlarge|16|16|8|4

### 计算优化标准型

<div id="user-content-3"></div>

**规格类型特点：**

* vCPU与内存比约为1:2
* 处理器：
	* 第四代：2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器，基于京刚架构将虚拟化和管理开销卸载至自研专用硬件，大幅提升存储网络性能
	* 第三代：2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器
	* 第二代：
	  * 2.4 GHz主频的Intel Xeon Gold 6148 （Skylake）处理器 或 2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器  
	  * 2.6 GHz主频的AMD EPYC ROME 处理器
	* 第一代：2.1 GHz主频的Intel Xeon E5-2683 v4（Broadwell）处理器
* 支持以下类型云硬盘：
	* 通用型SSD云盘
	* 性能型SSD云盘
	* 容量型HDD云盘
* 适用场景：
	* 批处理工作负载
	* Web前端服务器
	* 大型多人在线游戏（MMO）前端
	* 数据分析、批量计算、视频编码
	* 高性能科学和工程应用

**实例规格**

第四代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|c.n4.large|2|4|2|2
|c.n4.xlarge|4|8|4|4
|c.n4.2xlarge|8|16|4|8
|c.n4.3xlarge|12|24|8|8
|c.n4.4xlarge|16|32|8|8
|c.n4.6xlarge|24|48|8|16
|c.n4.8xlarge|32|64|8|16
|c.n4.12xlarge|48|96|8|16
|c.n4.16xlarge|64|128|8|32
|c.n4.24xlarge|96|192|16|32

第三代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|c.n3.large|2|4|2|2
|c.n3.xlarge|4|8|4|4
|c.n3.2xlarge|8|16|4|4
|c.n3.3xlarge|12|24|8|4
|c.n3.4xlarge|16|32|8|4
|c.n3.6xlarge|24|48|8|4
|c.n3.8xlarge|32|64|8|4
|c.n3.12xlarge|48|96|8|4
|c.n3.16xlarge|64|128|8|4
|c.n3.22xlarge|88|176|8|4

第二代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|c.n2.large|2|4|2|2
|c.n2.xlarge|4|8|4|4
|c.n2.2xlarge|8|16|4|4
|c.n2.4xlarge|16|32|8|4
|c.n2.8xlarge|32|64|8|4
|c.n2.16xlarge|64|128|8|4
|c.n2.18xlarge	|72|144|8|4

第二代（AMD）

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|c.n2a.large|2|4|2|2
|c.n2a.xlarge|4|8|4|4
|c.n2a.2xlarge|8|16|4|4
|c.n2a.4xlarge|16|32|8|4
|c.n2a.8xlarge|32|64|8|4
|c.n2a.16xlarge|64|128|8|4
|c.n2a.32xlarge	|128|256|8|4

第一代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数|备注
:---|:---|:---|:---|:---|:---
|c.n1.large|2|4|2|2 | |	
|c.n1.xlarge_m	|4|4|4|4|	*
|c.n1.xlarge|4|8|4|4| |
|c.n1.2xlarge_s|8|8|4|4|*
|c.n1.2xlarge_m|8|12|4|4|*
|c.n1.2xlarge|8|16|4|4 |	|
|c.n1.4xlarge_m|16|16|8|4|*
|c.n1.4xlarge|16|32|8|4 |	|
|c.n1.8xlarge|32|64|8|4 | |


## 内存优化型
内存优化型当前提供内存优化标准型和内存优化增强型，适用于存在大量内存操作、查找和计算的应用。每一个vCPU都对应一个Intel Xeon处理器的超线程核。

<div id="user-content-4"></div>

### 内存优化标准型

**规格类型特点：**

* vCPU与内存比约为1:8
* 处理器：
	* 第四代：2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器，基于京刚架构将虚拟化和管理开销卸载至自研专用硬件，大幅提升存储网络性能
	* 第三代：2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器 
	* 第二代：
	  * 2.4 GHz主频的Intel Xeon Gold 6148 （Skylake）处理器  或 2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器  
	  * 2.6 GHz主频的AMD EPYC ROME 处理器
	* 第一代：2.1 GHz主频的Intel Xeon E5-2683 v4（Broadwell）处理器
* 支持以下类型云硬盘：
	* 通用型SSD云盘
	* 性能型SSD云盘
	* 容量型HDD云盘
* 镜像使用限制：
	* 3代及以上Intel系列，AMD系列仅支持云盘系统盘镜像
* 适用场景：
	* 高性能数据库、内存数据库
	* 数据分析与挖掘、分布式内存缓存
	* Hadoop、Spark群集以及其他企业大内存需求应用

**实例规格**

第四代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|m.n4.large|2|16|2|2
|m.n4.xlarge|4|32|4|4
|m.n4.2xlarge|8|64|4|8
|m.n4.3xlarge|12|96|8|8
|m.n4.4xlarge|16|128|8|8
|m.n4.6xlarge|24|192|8|16
|m.n4.8xlarge|32|256|16|16

第三代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|m.n3.large|2|16|2|2
|m.n3.xlarge|4|32|4|4
|m.n3.2xlarge|8|64|4|4
|m.n3.3xlarge|12|96|8|4
|m.n3.4xlarge|16|128|8|4
|m.n3.6xlarge|24|192|8|4
|m.n3.8xlarge|32|256|8|4
|m.n3.16xlarge|64|512|8|4

第二代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|m.n2.large|2|16|2|2
|m.n2.xlarge|4|32|4|4
|m.n2.2xlarge|8|64|4|4
|m.n2.4xlarge|16|128|8|4
|m.n2.8xlarge|32|256|8|4
|m.n2.16xlarge|64|512|8|4
|m.n2.18xlarge|72|576|8|4

第二代（AMD）

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|m.n2a.large|2|16|2|2
|m.n2a.xlarge|4|32|4|4
|m.n2a.2xlarge|8|64|4|4
|m.n2a.4xlarge|16|128|8|4
|m.n2a.8xlarge|32|256|8|4
|m.n2a.16xlarge|64|512|8|4

第一代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数|备注
:---|:---|:---|:---|:---|:---
|m.n1.small| 1 | 8 | 2|1 | *
|m.n1.medium|2	|12|2|2|*
|m.n1.large|2|16|2|2 | |
|m.n1.xlarge|4|32|4|4 | |
|m.n1.2xlarge|8|64|4|4  | |
|m.n1.4xlarge|16|128|8|4 | |

<div id="user-content-17"></div>

### 内存优化增强型

**规格类型特点：**

* vCPU与内存比约为1:17
* 基于Intel® 第二代傲腾持久内存（BPS），提供高性价比的内存介质。
* 本规格族提供的内存混合了普通内存与傲腾持久内存，建议您在搭建业务前进行充分测试。
* 处理器：
	* 2.6 GHz主频的Intel Xeon Gold（Icelake）处理器
* 支持以下类型云硬盘：
	* 通用型SSD云盘
	* 性能型SSD云盘
	* 容量型HDD云盘
* 系统盘使用限制：
	* 仅支持云硬盘系统盘
* 适用场景：
	* 高性能数据库、内存数据库，如Redis
	* 数据分析与挖掘、分布式内存缓存
	* Hadoop、Spark群集以及其他企业大内存需求应用

**实例规格**

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
|:---|:---|:---|:---|:---
|m.e3.large|2|34|2|2
|m.e3.xlarge|4|68|4|4
|m.e3.2xlarge|8|136|4|4
|m.e3.4xlarge|16|272|8|4
|m.e3.8xlarge|32|544|8|4
|m.e3.16xlarge|64|1088|8|4
|m.e3.31xlarge|124|2108|8|4




## 突发性能型

突发性能型实例是一种通过积分机制约束CPU使用率的实例规格，适用于平时CPU使用率较低，偶发使用率突增的入门级或轻量级计算场景。突发型实例提供了在一定时间区间内动态分配计算力的能力，闲时积累忙时消耗，相对于普通实例规格，更为经济。[突发性能型规格介绍](https://docs.jdcloud.com/virtual-machines/Burst-Instance-Overview)

**规格类型特点：**

* 基于规格和基准性能提供算力，允许一定时间范围内算力的累积，通过积分体现实例算力的消耗和积累情况。
* 处理器：
    * 第二代：2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器  
* 支持以下类型云硬盘：
    * 通用型SSD云盘
    * 性能型SSD云盘
    * 容量型HDD云盘
* 系统盘使用限制：
    * 仅支持云硬盘系统盘
* 适用场景：
    * 微服务、轻负载应用
    * 代码库、Web服务、开发测试环境

**实例规格**

第二代

实例规格|vCPU（核）|内存（GB）|基准性能 |网卡数|单网卡队列数 |每小时可获积分 | 积分余额上限
|:---|:---|:---|:--- |:---|:---|:---|:---
|t.e2.small|2|1|10% |2|1 |12 |288
|t.e2.large|2|2|20% |2|1 | 24 |576
|t.c2.large|2|4|20% |2|1 | 24 |576
|t.g2.large|2|8|30% |2|1 | 36|864
|t.e2.xlarge|4|4|30% |2|1 | 72 |1728
|t.c2.xlarge|4|8|30% |2|1 | 72 |1728
|t.g2.xlarge|4|16|40% |2|1| 96 | 2304
|t.e2.2xlarge|8|8|30% |2|1 | 144| 3456
|t.c2.2xlarge|8|16|30% |2|1 | 144| 3456
|t.g2.2xlarge|8|32|40% |2|1| 192|4608


## 高频计算型

高频计算型当前提供高频计算通用型，为您提供高性能的计算资源。每一个vCPU都对应一个Intel Xeon处理器的超线程核。

<div id="user-content-5"></div>

### 高频计算通用型

**规格类型特点：**

* vCPU与内存比为1:4
* 计算性能稳定，处理器主频高
* 处理器：
	* 第二代：3.2 GHz主频的Intel Xeon Gold 6146（Skylake）处理器
	* 第一代：3.2 GHz主频的Intel Xeon E5-2667 v4（Broadwell）处理器
* 支持以下类型云硬盘：
	* 通用型SSD云盘
	* 性能型SSD云盘
	* 容量型HDD云盘
* 适用场景：
	* 高性能Web前端服务器
	* 高性能科学和工程应用
	* MMO游戏、视频编码

**实例规格**

第二代：

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|h.g2.large|2|8|2|2
|h.g2.xlarge|4|16|4|4
|h.g2.2xlarge|8|32|4|4
|h.g2.4xlarge|16|64|8|4
|h.g2.8xlarge|32|128|8|4

第一代：

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|h.g1.large|2|8|2|2
|h.g1.xlarge|4|16|4|4
|h.g1.2xlarge|8|32|4|4
|h.g1.4xlarge|16|64|8|4
|h.g1.6xlarge|24|96|8|4

## 存储优化型

存储优化型当前提供存储优化IO型及存储优化大数据型，为您提供高性能的本地存储资源。每一个vCPU都对应一个Intel Xeon处理器的超线程核。

<div id="user-content-7"></div>

### 存储优化IO型

**规格类型特点：**

* vCPU与内存比为1:4
* 提供低时延高IO的本地存储
* 处理器：
	* 第三代：2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器  
	* 第二代：2.4 GHz主频的Intel Xeon Gold 6148（Skylake）处理器
	* 第一代：2.1 GHz主频的Intel Xeon E5-2683 v4（Broadwell）处理器
* 支持本地数据盘（临时存储），并支持以下类型云硬盘。请注意 **本地数据盘为临时存储盘，有丢失数据的风险（比如发生迁移或宿主机宕机等情况），不适用于应用层没有数据冗余架构的使用场景， 建议您使用云硬盘存储重要数据。** 
	* 通用型SSD云盘
	* 性能型SSD云盘
	* 容量型HDD云盘
* 适用场景：
	* 高性能关系数据库
	* NoSQL数据库
	* ElasticSearch等场景

**实例规格**


第三代：

实例规格|vCPU（核）|内存（GiB）|本地数据盘（临时存储 GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---|:---
|s.i3.2xlarge|8|32|1 x 1862 NVMe SSD|4|4
|s.i3.4xlarge|16|64|2 x 1862 NVMe SSD|8|4
|s.i3.6xlarge|24|96|3 x 1862 NVMe SSD|8|4
|s.i3.8xlarge|32|128|4 x 1862 NVMe SSD|8|4
|s.i3.12xlarge|48|192|6 x 1862 NVMe SSD|8|4
|s.i3.16xlarge|64|256|8 x 1862 NVMe SSD|8|4
|s.i3.22xlarge|88|352|8 x 1862 NVMe SSD|8|4


第一代：

实例规格|vCPU（核）|内存（GiB）|本地数据盘（临时存储 GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---|:---
|s.i1.xlarge|4|16|1 x 894 SSD|4|4
|s.i1.2xlarge|8|32|2 x 894 SSD|4|4
|s.i1.4xlarge|16|64|4 x 894 SSD|8|4
|s.i1.8xlarge|32|128|8 x 894 SSD|8|4
|s.i1.14xlarge|56|224|14 x 894 SSD|8|4

<div id="user-content-8"></div>

### 存储优化大数据型

**规格类型特点：**

* vCPU与内存比约为1:4
* 提供低时延高容量及高吞吐的本地存储
* 处理器：
	* 第二代：2.1 GHz主频的Intel Xeon Silver 4116（Skylake）处理器
	* 第一代：2.2 GHz主频的Intel Xeon E5-2650 v4（Broadwell）处理器
* 支持本地数据盘（临时存储），并支持以下类型云硬盘。请注意 **本地数据盘为临时存储盘，有丢失数据的风险（比如发生迁移或宿主机宕机等情况），不适用于应用层没有数据冗余架构的使用场景， 建议您使用云硬盘存储重要数据。** 
	* 通用型SSD云盘
	* 性能型SSD云盘
	* 容量型HDD云盘
* 适用场景：
	* Hadoop MapReduce、HDFS、Hive、HBase
	* 其他海量数据存储区及计算的业务场景

**实例规格**

第二代：

实例规格|vCPU（核）|内存（GiB）|本地数据盘（临时存储 GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---|:---
|s.d2.xlarge|4|22|1 x 9313 HDD|4|4
|s.d2.2xlarge|8|44|2 x 9313 HDD|4|4
|s.d2.4xlarge|16|88|4 x 9313 HDD|8|4
|s.d2.8xlarge|32|176|8 x 9313 HDD|8|4
|s.d2.10xlarge|40|220|12 x 9313 HDD|8|4

第一代：

实例规格|vCPU（核）|内存（GiB）|本地数据盘（临时存储 GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---|:---
|s.d1.xlarge|4|22|1 x 5587 HDD|4|4
|s.d1.2xlarge|8|44|2 x 5587 HDD|4|4
|s.d1.4xlarge|16|88|4 x 5587 HDD|8|4
|s.d1.8xlarge|32|176|8 x 5587 HDD|8|4
|s.d1.10xlarge|40|220|12 x 5587 HDD|8|4

## GPU型

GPU型当前提供GPU标准型和GPU虚拟化型。GPU虚拟化型规格目前在华北部分可用区邀测中，如有购买需求请提交工单。

<div id="user-content-6"></div>

### GPU标准型

**规格类型特点：**

* vCPU与内存比接近1:4
* 异构计算
* GPU：
	* Nvidia Tesla P40 
	* Nvidia Tesla V100
* 处理器：
	* 2.1 GHz主频的Intel Xeon E5-2683 v4（Broadwell）处理器（P40）
	* 2.2 GHz主频的Intel Xeon E5-2650 v4（Broadwell）处理器（V100）
* 支持本地数据盘（临时存储），并支持以下类型云硬盘。请注意 **本地数据盘为临时存储盘，有丢失数据的风险（比如发生迁移或宿主机宕机等情况），不适用于应用层没有数据冗余架构的使用场景， 建议您使用云硬盘存储重要数据。** 
	* 通用型SSD云盘
	* 性能型SSD云盘
	* 容量型HDD云盘
* 适用场景：
	* 科学计算
	* 机器学习
	* 图形渲染 

**实例规格**

第一代：

实例规格|vCPU（核）|内存（GiB）|GPU    |本地数据盘（临时存储，GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---|:---|:---
|p.n1p40.3xlarge|12|48|1 x Nvidia Tesla P40|1 x 894 SSD|8|4
|p.n1p40.7xlarge|28|110|2 x Nvidia Tesla P40|2 x 894 SSD|8|4
|p.n1p40.14xlarge|56|220|4 x Nvidia Tesla P40|4 x 894 SSD|8|4
|p.n1p40h.3xlarge|12|48|1 x Nvidia Tesla P40|1 x 1117 HDD|8|4
|p.n1p40h.7xlarge|28|110|2 x Nvidia Tesla P40|2 x 1117 HDD|8|4
|p.n1p40h.14xlarge|56|220|4 x Nvidia Tesla P40|4 x 1117 HDD|8|4
|p.n1v100.2xlarge|8|44|1 x Nvidia Tesla V100|1 x 5587 HDD|4|4
|p.n1v100.5xlarge|20|110|2 x Nvidia Tesla V100|2 x 5587 HDD|8|4
|p.n1v100.10xlarge|40|220|4 x Nvidia Tesla V100|4 x 5587 HDD|8|4

<div id="user-content-10"></div>

### GPU虚拟化型

**规格类型特点：**

* 异构计算
* GPU类型及规格：
	* 1* 1/6 Nvidia Tesla P40 （显存4 GiB）
	* 1* 1/4 Nvidia Tesla P40 （显存6 GiB）
	* 1* 1/2 Nvidia Tesla P40 （显存12 GiB）
* 处理器：
	* 2.1 GHz主频的Intel Xeon E5-2683 v4（Broadwell）处理器
	* 2.2 GHz主频的Intel Xeon E5-2650 v4（Broadwell）处理器
	* 2.4 GHz主频的Intel Xeon E5-2680 v4（Broadwell）处理器
* 虚拟化类型：
	* C模式
	* Q模式
* 适用场景：
	* 科学计算、机器学习（C模式）
	* 图形渲染、游戏（Q模式） 

**实例规格**

第一代-C模式：

实例规格|vCPU（核）|内存（GiB）|GPU    |显存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---|:---|:---
|p.c1p40g.large|2|8|1 x 1/6 Nvidia Tesla P40|4|2|2
|p.c1p40m.large|2|14|1 x 1/4 Nvidia Tesla P40|6|2|2
|p.c1p40g.xlarge|4|14|1 x 1/4 Nvidia Tesla P40|6|4|4
|p.c1p40g.3large|6|28|1 x 1/2 Nvidia Tesla P40|12|4|4

第一代-Q模式：

实例规格|vCPU（核）|内存（GiB）|GPU|显存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---|:---|:---
|p.q1p40g.large|2|8|1 x 1/6 Nvidia Tesla P40|4|2|2
|p.q1p40m.large|2|14|1 x 1/4 Nvidia Tesla P40|6|2|2
|p.q1p40g.xlarge|4|14|1 x 1/4 Nvidia Tesla P40|6|4|4
|p.q1p40g.3large|6|28|1 x 1/2 Nvidia Tesla P40|12|4|4

## 裸金属

裸金属是基于京东云新一代自研硬件卸载虚拟化技术架构所提供的实例规格，同时兼顾物理机性能及虚拟机灵活性，无额外虚拟化损耗，支持嵌套虚拟化。[裸金属实例介绍](https://docs.jdcloud.com/cn/virtual-machines/bare-metal-overview)。

<div id="user-content-13"></div>

### 通用型
**规格类型特点：**

* 处理器：
	* 2.4 GHz主频的Intel Xeon Gold 6148（Skylake）处理器
* 支持以下类型云硬盘：
	* 通用型SSD云盘
	* 性能型SSD云盘
	* 容量型HDD云盘
* 系统盘使用限制：
	* 仅支持云硬盘系统盘
* 适用场景：
	* 各种类型和规模的企业级应用
	* 中大型数据库系统、缓存、搜索集群
	* 高性能科学及工程应用
	* 高网络包收发场景，如视频、直播、游戏等

**实例规格**

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
|:---|:---|:---|:---|:---
|g.n2.metal|80|384|8|8

<div id="user-content-14"></div>

### 存储优化IO型
**规格类型特点：**

* 处理器：
	* 第三代：2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器
	* 第二代：2.4 GHz主频的Intel Xeon Gold 6148（Skylake）处理器
* 支持以下类型云硬盘：
	* 通用型SSD云盘
	* 性能型SSD云盘
	* 容量型HDD云盘
* 系统盘使用限制：
	* 仅支持云硬盘系统盘
* 适用场景：
	* NoSQL数据库（如：MongoDB等）
	* OLTP、高性能关系型数据库
	* Elasticsearch等低时延I/O密集型应用

**实例规格**

实例规格|vCPU（核）|内存（GiB）|本地数据盘（临时存储 GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---|:---
|s.i3f.metal|96|384|1 x 1862 NVMe SSD|1|4
|s.i2.metal|80|384|1 x 1862 NVMe SSD|8|4

<div id="user-content-15"></div>

### 安全增强内存优化型
**规格类型特点：**

* 基于京东云最新一代虚拟化架构-京刚，将虚拟化和管理开销卸载至自研专用硬件，大幅提升存储网络性能。
* 支持Intel® SGX加密计算，保障关键代码和数据的机密性与完整性。
* 处理器：
	* 2.6 GHz主频的Intel Xeon Gold（Icelake）处理器
* 支持以下类型云硬盘：
	* 通用型SSD云盘
	* 性能型SSD云盘
	* 容量型HDD云盘
* 系统盘使用限制：
	* 仅支持云硬盘系统盘
* 适用场景：
	* 各种类型和规模的企业级应用
	* 机密计算、数据加密、区块链场景
	* 高安全可信要求场景，如：金融、政府等
	* 多方计算中共享机密数据

**实例规格**

实例规格|vCPU（核）|内存（GiB）|含机密内存（GiB）|网卡数|单网卡队列数
|:---|:---|:---|:---|:---|:---
|m.n4ft.metal|128|1024|512|16|32

请注意：

* 标 * 规格表示不支持以该规格新建云主机，且不支持您将当前云主机调整至该规格，但不影响您现有该规格云主机的使用；
* 可购买规格还请以控制台为准；
* 在购买实例后，您可根据业务规模变更情况对实例进行配置修改，详细请参见[调整配置](../Operation-Guide/Instance/Resize-Instance.md)。

## 相关参考

[调整配置](../Operation-Guide/Instance/Resize-Instance.md)
