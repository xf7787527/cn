# 团队空间

敏捷模式项目空间为自组织团队提供了协同工作空间，成员可以在空间内围绕敏捷看板以敏捷迭代的形式开展工作。看板内支持多来源的多种工作项例如：需求、缺陷、任务的展示和流转，最大程度可视化研发活动中的价值流、风险、阻塞。看板支持多种自定义流程规则控制，包括需求评审控制、需求变更控制等，以达到团队内的工作项流转规则多样化、透明化、可管控、可灵活配置。

在迭代维度上，敏捷模式项目空间支持看板模式和列表模式，成员能够在可自定义样式的列表中通过高级筛选器快速浏览工作项，也能够在可自定义状态的看板中查看工作项流转情况。此外，成员可以在迭代报表中通过各种专业的数据图表直观查看到整体迭代的工作项交付情况。

在空间维度上，敏捷模式项目空间支持成员通过人力资源日历和饱和度视图对空间资源进行查看、管理。另外，项目空间提供了多种空间维度的数据图表，便于团队空间管理员对空间研发情况进行监管。

产品架构如下：

![image-20220216115012884](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/image-20220216115012884.png)

## 团队空间管理

### 信息展示

#### 空间基本信息

空间基本信息展示空间名称、类型、项目名称、插件等数据。

**![img](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/clip_image002.jpg)**

#### 空间数据展示

空间数据展示了一些空间内工作项的关键指标，和各个阶段下的工作项数量。

**![img](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/clip_image004.jpg)**

#### 团队空间动态

成员可以在空间动态中以不同维度：项目空间、迭代、工作项、任务查看到所有成员在空间内的操作，实现动态可追溯。

**![img](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/clip_image006.jpg)**

### 创建团队空间

进入`团队空间`模块，点击`创建新团队空间`，填写相应字段，即可创建一个团队空间。

![image-20220309111926835](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/image-20220309111926835-16468099626731.png)

创建好的团队空间如图

![image-20220309112124480](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/image-20220309112124480.png)

对于有些团队空间众多的角色，可以收藏一些常关注的团队空间。点击`收藏`按钮，空间名称下方将变为`已收藏`。进入`我的收藏`即可查看。

![image-20220309112339829](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/image-20220309112339829.png)

### 团队空间配置

#### 基本信息管理

用于维护项目空间基本信息。支持对`空间标识`、`空间名称`、`空间描述`、`默认项目`、`版本数据源`进行修改，点击`编辑`按钮即可。

点击`删除空间`，可直接删除空间。

当团队空间关联了项目，则此团队空间下的卡片将默认与团队空间关联的项目一致，卡片关联的项目可以再次更改。

![image-20220309151432378](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/image-20220309151432378.png)

#### 关联项目管理

空间可以切换关联项目，支持变更项目时，同样团队的成员继续执行新项目的场景。

![image-20220309151547252](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/image-20220309151547252.png)

#### 人员管理

实现 管理员-成员-游客 多层级的自组织团队成员管理。

![image-20220309151631546](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/image-20220309151631546.png)

默认对各身份的权限如下：

`游客`：仅可游览

`成员`：可编辑，无团队空间设置权限，仅可查看公共卡片和有自己参与的保密卡片

`管理员`：可编辑，有团队空间设置权限，可查看所有卡片，可以对所有卡片、人员进行设置

#### 卡片类型、状态管理

支持定义团队空间启用的卡片项类型。

卡片类型包括：产品需求、研发需求、任务、BUG

> 产品需求：是指通过“业务需求”模块进入的到团队空间的需求，一般是由业务同学提报的需求

> 研发需求：是指团队空间中同学自己提出的需求，通常有产品经理自己探索的需求、bugfix等

> 任务、Bug：是不同于 产品需求、研发需求的，通常由空间成员自行提出的事项

!> **<font color=#FF6347>需要注意：</font>**
1、团队空间内增加产品需求与研发需求是为满足轻量团队，无须需求管理
2、对于重流程管控团队，建议将产品需求与研发需求显示关闭，以避免和需求管理模块中的需求类型混淆

默认显示`任务`和`BUG`，且不可取消显示；可选是否显示`产品需求`和`研发需求`。
在实际应用中，根据团队线下管理模式，自由选择相应显示字段。

![image-20220309151707254](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/image-20220309151707254.png)

行云支持对卡片状态的自定义设置，并可以随意更改名称，以适应不同业务场景的需要。同时支持选择状态是否显示，隐藏后看板视图将不显示对应状态列。但完成状态不支持删除和隐藏，仅支持改名，挂起状态不可做修改。

!> **<font color=#FF6347>需要注意：</font>**

1. 状态自定义是在固定的阶段中进行大排序，顺序不可变更，大的阶段按顺序为「准备」「评审」「就绪」「设计」「开发」「测试」「发布」「完成」「挂起」
2. 可通过新增状态功能进行状态新增，每个阶段中最多允许5个自定义的状态，同阶段中可进行顺序的拖拽。

![image-20220309140927075](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/image-20220309140927075.png)

#### 成员权限管理

支持针对各种成员角色，对迭代和工作项进行操作权限的配置管理。管理员可修改

![image-20220309140832635](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/image-20220309140832635.png)

#### 个性化流程管理

项目空间内支持评审流程约束、需求变更流程约束、工时填报流程约束等多种流程约束。

![image-20220309152107322](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/image-20220309152107322.png)

#### 插件管理

支持根据团队自身情况，选择对应的插件集成到空间中。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/clip_image016.jpg)

#### 卡片自定义

团队空间管理员有权根据部门管理员在系统设置-->扩展表单设置里创建的模版自定义扩展字段，保存后扩展字段会在团队空间的卡片内生效。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/clip_image018.jpg)

#### 卡片流程自定义

支持团队空间管理员按照角色、用户自定义卡片在不同状态之间的流转规则，流转规则对空间内所有卡片生效，便于团队进行流程管理。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/clip_image020.jpg)

#### 角色职责设置

行云支持对团队成员进行角色职责设置，团队成员可在卡片处理人中选择角色（非必填，当选择后系统自动记忆保存，下次将自动带出），方便管理者按角色进行统计分析。

![image-20220309140953082](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/image-20220309140953082.png)

#### 不同团队空间简易切换

<img src="http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/image-20220216144557779.png" alt="image-20220216144557779" style="zoom:50%;" />

###

## 迭代计划跟踪

### 迭代管理

敏捷开发模式中，提倡以迭代式开发的方式开发产品，这可以帮助团队及时改进产品和把控项目进度。
一次迭代可能发布某个或某几个功能特性，一次迭代过程即包含这些新功能所需的所有开发任务以及其他任务。

在行云，我们可以通过迭代来跟踪研发进度，让项目管理更加有序和高效。

迭代计划区分布在团队空间的，此区域内含创建好的迭代计划，未加入迭代计划的卡片默认会在backlog中显示。
从`需求管理`模块内分配至团队空间的需求也将以卡片的形式出现在未计划中。

### 创建一条迭代

进入团队空间内，点击左侧`新建迭代`，可以创建一个迭代计划。

![image-20220216143506745](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/image-20220216143506745.png)

### 管理迭代

支持编辑迭代信息，对迭代进行归档和删除。可在迭代视图快速查看迭代的相关信息。包括各类工作项信息、迭代时间和剩余工作量。

<img src="http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/clip_image002-4993494.jpg" alt="img/" style="zoom:50%;" />

迭代结束后，可以进行迭代`归档`操作，归档时，若有未完成卡片，可以选择将卡片恢转移到未计划。

若迭代不再使用，也可以进行`删除`操作。删除时，若有未完成卡片，可以选择将卡片恢转移到未计划。

### 查看迭代信息

支持按看板、列表、报表查看迭代

看板查看：可以进行卡片筛选

<img src="http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/image-20220216150036291.png" alt="image-20220216150036291" style="zoom:50%;" />

列表查看：

勾选`跨迭代查询`，可以跨迭代查询卡片，可以查看当前团队空间下所有卡片

###

### 为迭代添加卡片

创建好迭代后，便可为迭代添加卡片了。

#### **创建方法一**

左侧选中新建的`迭代`，点击看板页面右上角`创建卡片`，填写必要字段后即可生成一张迭代内的卡片。

卡片创建页面如下图：

![image-20220309152203572](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/image-20220309152203572.png)

![demand](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/卡片详情.jpg)

![](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/新建卡片.jpg)

![demand](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/卡任务.jpg)




填写字段说明如下：

<table><tbody>
     <tr>
         <th bgcolor="Gainsboro" nowrap>信息类别</th>
         <th bgcolor="Gainsboro">字段名称</th>
         <th bgcolor="Gainsboro"> 限制 </th>
         <th bgcolor="Gainsboro">填写说明</th>
    </tr>
    <tr>
         <th rowspan="16" align="center" >基本信息</th>
         <td align="center" >标题</td>
         <td rowspan="4" align="center" nowrap>必填</td>
         <td>3-80个字符</td>
    </tr>
    <tr>
         <td align="center" nowrap>团队空间</td>
         <td>不可更改</td>
    </tr>
    <tr>
         <td align="center" >卡片类型</td>
         <td>分为：产品需求、研发需求、BUG、任务</td>
    </tr>
    <tr>
         <td align="center">状态</td>
         <td>定义了卡片的进程，这个状态由团队成员手工更新。
         我们建议，每次任务有变化时候，及时更新状态，这样需求方可以及时了解到开发的进度。若有父子关系情况下，所有子变为同一状态时，父卡片默认会变为该状态。 </td>
    </tr>
    <tr>
         <td align="center" >开始日期</td>
         <td rowspan="8" nowrap>非必填</td>
         <td>卡片开始日期</td>
    </tr>
    <tr>
         <td align="center" >截止日期</td>
         <td>卡片结束日期</td>
    </tr>
    <tr>
         <td align="center" >故事点</th>
         <td>scrum方法论中，用于估算卡片规模。</td>
    </tr>
    <tr>
         <td align="center" >所属迭代</td>
         <td>该卡片归属的迭代。默认为此刻选中的新建迭代，也可下拉选择</td>
    </tr>
    <tr>
         <td align="center" nowrap>优先级</th>
         <td>P0,P1,P2,P3,下拉选择</td>
    </tr>
    <tr>
         <td align="center" nowrap>标签</td>
         <td>可为卡片设置标签，方便日后筛选查看和导出管理</td>
    </tr>
    <tr>
         <td align="center" >“处理人” 现已改为“卡任务”</td>
         <td>是指：当前卡片都有哪些人员参与，及其负责范围和对应的工时。可依次在处理人框内选择团队成员，填写职责并预估剩余工时。</td>
    </tr>
    <tr>
         <td align="center" >是否完成</td>
         <td>可勾选。表明此卡任务是否完成。</td>
    </tr>
    <tr>
         <td align="center" >负责内容</td>
         <td rowspan="4" nowrap align="center">必填</td>
         <td>一旦填写了处理人，则此项将为必填项。默认为`个人任务`</td>
    </tr>
    <tr>
         <td align="center" >起止日期</td>
         <td>一旦填写了处理人，则此项将为必填项。默认为填写日的日期</td>
    </tr>
    <tr>
         <td align="center" >计划工时</td>
         <td>一旦填写了处理人，则此项将为必填项。默认为8小时</td>
    </tr>
    <tr>
         <td align="center" >剩余工时</td>
         <td>一旦填写了处理人，则此项将为必填项。默认为8小时</td>
    </tr>
    <tr>
         <th rowspan="10" align="center" >更多信息</th>
         <td align="center" >详情</td>
         <td rowspan="10" nowrap>非必填</td>
         <td>输入卡片详细描述，3-1000字。支持富文本编辑。</td>
    </tr>
    <tr>
         <td align="center" >产品附件</td>
         <td>产品所需相关附件，如PRD等</td>
    </tr>
    <tr>
         <td align="center" >设计附件</td>
         <td>设计内容附件</td>
    </tr>
    <tr>
         <td align="center" >研发附件</td>
         <td>研发所需相关附件，如接口文档等</td>
    </tr>
    <tr>
         <td align="center" >链接</td>
         <td>点击可添加外部网站参考链接，须写明链接名称和链接地址。如CF链接地址</td>
    </tr>
    <tr>
         <td align="center" >是否保密</td>
         <td> 勾选此项，该卡片将成为保密卡片，仅限处理人和团队空间管理员可见。看板界面上该卡片会有保密标识。</td>
    </tr>
    <tr>
         <td align="center" >是否评审</td>
         <td> 若团队空间设置中开启了评审约束，将在新建卡片时看到是否评审勾选项，一旦创建成功则该卡片将需要进行强制评审，不能跳跃状态到评审就绪或之后的状态</td>
    </tr>
    <tr>
         <td align="center" >关联应用</td>
         <td> 可与JONE中的应用相关联。</td>
   </tr>
    <tr>
         <td align="center" >关联项目</td>
         <td> 可与PMP中的项目进行关联。</td>
    </tr>
    <tr>
         <td align="center" nowrap >置顶</td>
         <td> 勾选后将在待开发列中置顶。</td>
    </tr>
#### 创建方法二：

直接在看板界面上各状态列内点击`添加新卡片`，输入内容（3-80字），选择卡片类型即可。

如需保密，可直接勾选。如下图所示：

![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/sprint4.jpg)

若有详情内容需要补充，点击卡片，进入卡片内容详情页进行补充即可。

卡片默认不关联项目，由研发人员在详情中选择关联的项目。

!> **<font color=#FF6347>需要注意：</font>** 关联了项目的卡片且项目管理中被审核通过才能填报工时

### 迭代卡片管理

#### 卡片状态修改

看板状态下，支持卡片任意拖拽更新进度

#### 删除卡片

列表视图下，点击一个卡片上的`删除`按钮，删除该卡片。若卡片有父子关系，则直接将该卡片下全部子进行删除。



## 人力资源日历

人力资源日历是行云的特色功能—— 一个轻量类project小工具，帮助敏捷教练、研发Leader灵活安排团队成员任务。

### 人力资源日历

支持查看指定时间内的空间成员处理的工作项。便于管理者对成员进行任务的指配和调整。拥有权限的成员可以在日历中快速新建工作项。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/clip_image002-4995203.jpg)

### 人力资源饱和度视图

人力资源饱和度视图支持查看指定时间内的空间成员的任务饱和度。便于管理者对任意成员进行工作的调度，以及随时查看自组织团队内各个成员的工作情况，为管理者提供人员管理的有力工具。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/clip_image004-4995203.jpg)

点击团队成员名字后面的加号，在任务分配框内填写相关信息，即可为该成员分配任务。

![image-20220309152743229](http://devops-minio.jdcloud.com/doc-image/All-Image/space.assets/image-20220309152743229.png)

