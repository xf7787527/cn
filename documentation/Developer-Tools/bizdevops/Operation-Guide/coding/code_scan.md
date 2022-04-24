## 代码扫描

### 开启代码扫描

仓库Master及以上权限成员可以开启代码扫描

  * 仓库-代码质量，直接进入首次配置页面

  * 选择“默认扫描分支”和“扫描引擎”，点击"保存配置“；代码扫描开启成功

  * 配置保存完成后，自动开启首次静态代码扫描

    ![](http://devops-minio.jdcloud.com/doc-image/All-Image/code_scan.assets/scan_create.png)

### 代码扫描高级配置

>仓库Master及以上权限成员可以进行代码扫描高级配置

代码扫描开启后，点击 “仓库-代码质量-设置”，支持更多高级配置：
    ![](http://devops-minio.jdcloud.com/doc-image/All-Image/code_scan.assets/scan_config.png)

#### 通用配置

* “通用配置”页面与首次“开启代码扫描”界面相同，用于配置扫描分支和选择扫描引擎。

#### 排除目录&文件

>默认的，所有仓库的扫描会排除如下目录和文件(如果存在)

```
    config/
    db/
    dist
    features/
    **/node_modules/
    script/
    **/spec/
    **/test/
    **/tests/
    **/vendor/
    **/*_test.go
    **/*.d.ts
```

**用户自定义不希望被扫描的目录和文件：**

* 以行为单位，每一行匹配一个排除模式
* 支持正则表达式的匹配规则

![](http://devops-minio.jdcloud.com/doc-image/All-Image/code_scan.assets/scan_exclude.png)

#### 自定义扫描参数

目前有10种扫描参数支持用户自定义，如下图所示：

* 自定义参数的开启/关闭
* 自定义参数的阈值

![](http://devops-minio.jdcloud.com/doc-image/All-Image/code_scan.assets/scan_parameter.png)

#### 定时扫描开启&关闭

代码扫描配置完成后，定时扫描默认关闭，支持手动开启：

* 开启后，会自动触发每日定时扫描
* 每日定时扫描时间：默认为当前开启时间

![](http://devops-minio.jdcloud.com/doc-image/All-Image/code_scan.assets/scan_timer.png)



### 增量代码扫描


如果仓库已经配置代码扫描，以下两种情况可触发增量代码扫描：

* 创建”合并请求“
* 更新“合并请求”

增量扫描结果会返回至代码评审页面，协助代码评审。

* 合并请求的“对话”页面可以查看总体扫描情况
  ![](http://devops-minio.jdcloud.com/doc-image/All-Image/code_scan.assets/scan_mr_diag.png)
* 合并请求的”代码检查“页面可以查看详细扫描结果
  ![](http://devops-minio.jdcloud.com/doc-image/All-Image/code_scan.assets/scan_mr_detail.png)

如果增量代码扫描失败，两个渠道“查看日志”或“重启扫描”

>增量扫描失败时，仓库developer及以上权限成员可以“重启扫描”

* “代码检查”页面可 重启扫描
* “对话”页面可 重启扫描
  ![](http://devops-minio.jdcloud.com/doc-image/All-Image/code_scan.assets/scan_restart_check.png)



### 静态代码扫描

静态代码扫描是Coding提供的重要功能，通过对仓库的全量扫描以及统一的评级标准，让大家快速了解仓库的总体情况。

点击 “代码质量”，进入代码扫描主页面

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/code_scan.assets/scan_static.png)

#### 总览

显示最近一次静态扫描的总体情况，包括：

* 可维护性评级
* 被扫描文件数量
* 文件评级分布
* Issues严重等级分布
* issues类别统计

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/code_scan.assets/scan_static_overview-20220210145940885.png)

#### issues

显示最近一次静态扫描发现的所有issues，以文件为维度显示；支持按照以下条件过滤：

* issue类别
* 严重级别
* 扫描引擎
  ![](http://devops-minio.jdcloud.com/doc-image/All-Image/code_scan.assets/scan_static_issues.png)

#### 文件

显示最近一次扫描中有issue的文件，支持按照以下条件排序：

* 文件（默认）
* 代码行数
* 可维护性评级
* 修复时间

同时可以按照文件名或路径搜索：

* 文件名：必须输入完整的文件名；比如 download.rb
* 路径：以‘/’为分界，输入完整路径段查询；比如：maven-central
  ![](http://devops-minio.jdcloud.com/doc-image/All-Image/code_scan.assets/scan_static_file.png)

点击指定文件，查看该文件issues详情，支持根据条件筛选issue：

* 扫描引擎
* issue严重级别
* issue类别
  ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/code_scan.assets/scan_static_issues-4475894.png)

扫描记录

* 启动扫描：点击“立即扫描”，开启新的扫描任务
* 显示当前仓库所有的静态扫描记录
  * 扫描成功：显示扫描时间
  * 扫描失败：查看扫描日志
    ![](http://devops-minio.jdcloud.com/doc-image/All-Image/code_scan.assets/scan_static_history.png)

#### 趋势

默认显示30天内的扫描结果趋势，包括：

* 技术债(率)趋势
* 代码行数趋势
  如果当天有多次扫描，只显示最后一次扫描结果
    ![](http://devops-minio.jdcloud.com/doc-image/All-Image/code_scan.assets/scan_static_trends.png)

#### 术语

* **可维护性评级**：根据仓库的技术债率，对仓库在可维护性方面的评级；可维护性是从代码重复率、复杂度和结构问题等几个方面考量，由默认引擎提供相应数据

* 技术债率：技术债率 = 技术债时间/ (每一行代码开发所需要的时间 * LOC)

  * 技术债时间：仓库中所有技术债issue预估的修复时间累计，技术债issues由默认引擎扫描得出；
  * 每一行代码开发所需要的时间：默认设置为15分钟
  * LOC：该仓库中被扫描文件的总代码行数，不包含空行与注释行

   根据技术债率对仓库进行评级，评级标准：

   * A级：<=5%
   * B级：(5% , 10%]
   * C级: (10% , 20%]
   * D级: (20% , 50%]
   * E级: >50%

   计算方法和评级标准的更多信息，请参考：

   * [The SQALE Method for Evaluating Technical Debt](https://dl.acm.org/doi/pdf/10.5555/2666036.2666042)
   * [Maintainability Rating in SonarQube](https://docs.sonarqube.org/latest/user-guide/metric-definitions/)

* 默认引擎：Coding扫描平台的默认引擎为Duplication与Structure，技术债issues由此引擎扫描提供

  * Duplication：重复代码块

  * Structure：复杂度、结构相关问题

    默认引擎支持语言如下：

    * Ruby
    * Python
    * PHP
    * JavaScript
    * Java
    * TypeScript
    * GoLang
    * Swift
    * Scala
    * Kotlin
    * C#

* **文件评级**：根据文件中技术债issue的累计修复时长，对文件从A～E做评级；每个技术债issue的预计修复时间由默认引擎提供

* **issue严重等级**分为五级：

  * Info
  * Minor
  * Major
  * Critical
  * Blocker

## 依赖分析

开发过程中使用依赖包很常见，避免重复造轮子，可以共享劳动成果加快开发速度。但是我们使用的三方开源依赖包，往往存在一些安全隐患。
为了让团队更加了解使用的开源依赖包以及存在的安全问题，Coding提供了依赖分析和漏洞分析的功能：

- 了解当前仓库都使用了哪些依赖包；
- 了解依赖包中的已知漏洞；

依赖分析功能包含**3**个重点的部分：

- **我依赖的**
- **依赖我的**
- **安全漏洞**

**开启**

- 仓库如果开启了代码扫描，就同时默认开启“依赖分析”和“安全漏洞”扫描；

**触发机制**

- 检测到仓库中的manifest文件更新(例如：Java语言中的Pom.xml)时，会触发依赖分析和安全漏洞扫描。

### 安全漏洞


**安全漏洞分级**根据 NVD 国家漏洞数据库CVSS 分数评估制定，将漏洞分为如下4个严重级别：

- Critical
- High
- Medium
- Low

**目前支持语言**

- Java
- Go

**安全漏洞展示** 在"代码质量 - 依赖分析 - 安全漏洞“页面，根据依赖包展示漏洞信息：

- 可根据不同条件排序，根据不同manifest文件筛选 ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/code_scan.assets/security_1.png)


