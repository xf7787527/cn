# 需求管理

**什么是需求？**

需求是以用户的角度做一个简单的功能阐述。基础格式如下：

- 作为某个角色
- 我想要做某些事情
- 以便于达到什么目的

**功能概述**

需求管理主要负责从需求提出、到需求处理，最终需求交付及验证的全生命周期的管理，通过需求有效管理，能提升业务人员与产研人员的需求沟通效率，并能及时反馈需求进展情况。发现需求交付瓶颈，帮助团队改善协作方式。

**功能架构** 

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/clip_image002.jpg)

l 流程操作：需求提出、需求审批、需求开始沟通、需求受理、需求拆分、需求处理、需求验收、收益验证。

l 其他操作：需求关联、需求权限、需求自定义、成本分摊、需求分组。

## 管理需求池

### 查看需求

行云可支持按个人、部门和需求分组的维度查看

![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/manage1.png)

部门最多可看到本人一级部门的所有需求。  

![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/manage2.png)    



> **需求列表排序**

行云支持对需求列表按 `需求编号` 和 `优先级` 进行排序。

![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/manage3.jpg)

> **需求列表字段设置**

行云支持自定义设置需求列表显示字段。点击需求列表右上角标志，即可设置列表显示字段。

![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/manage4.jpg) ![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/manage5.jpg)

> **需求列表筛选**

行云支持对需求列表多维度筛选。

![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/manage6.png)

点击需求列表中的`高级筛选`，弹出条件筛选框：

![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/manage7.png)

可常用搜索条件另存为常用条件，在`我的查询器`内一键快速查询。

![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/manage8.png)

### 导出需求列表

行云支持导出需求列表。点击需求列表右上角标志，设置列表导出字段，即可导出相应需求列表EXCEL.

![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/manage9.jpg)

![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/manage10.jpg)



## 创建一条需求

在`需求管理`中点击需求管理页面右上角的`新增需求`,进入需求创建页。

![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/creatdemand1.png)

依次填写完毕,点击提交或者保存草稿。

![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/creatdemand2.png)

需求填写页信息分为三类：基本信息、预期收益和其他信息。填写字段说明如下：

| 信息类别     | 字段名称                                                     | 限制                                       | 填写说明   |
| ------------ | ------------------------------------------------------------ | ------------------------------------------ | ---------- |
| 基本信息     | 需求名                                                       | 必填                                       | 3-80个字符 |
| 需求描述     | 作为一个<角色>，我想要<做什么>，以便于<达到什么目的>         |                                            |            |
| 受理人       | 输入erp/姓名，可直接下拉选择                                 |                                            |            |
| 需求来源     | 分为：业务需求、产品需求、研发需求；3选1                     |                                            |            |
| 需求方       | 需求提出人和成本分摊部门及分摊比例，该信息会同步至项目管理中（注：通过行云传递到项目空间的需求，必须有成本分摊信息） 当需求未被受理时，都可以更改分摊比例和分摊部门 |                                            |            |
| 标签         | 非必填                                                       | 可为需求设置标签，便于后期筛选、导出和查看 |            |
| 添加文档     | 可上传最大20M的文档                                          |                                            |            |
| 链接         | 可提供参考链接                                               |                                            |            |
| 预期收益     | 现状                                                         | 100字以内                                  |            |
| ROI          | 包含:预期收益、上线后预计收益时间                            |                                            |            |
| 其他信息     | 期望上线时间                                                 | 可直接选择                                 |            |
| 涉及研发平台 | 包含：APP、PC、M端、WQ、通天塔、提报系统、商城中台研发、商城搜索与大数据业务部、平台生态部、物流研发部等 |                                            |            |
| 业务优先级   | 分为：事业群战略、事业部重点、业务部重点、创新类、其他（默认）；N选1 |                                            |            |
| 需求类型     | 分为：配置类、入口类、BUG类、联调类、体验优化、日常需求、Top3需求、活动类；N选1 |                                            |            |
| 保密需求     | 可勾选。当需求类型选择活动类时，默认勾选此项                 |                                            |            |
| 紧急需求     | 可勾选。                                                     |                                            |            |
| 关注人       | 关注人将会收到该需求后续处理的通知和提醒。例如，你可以填写自己的leader，以便让其了解你的工作进展而无需人工询问和催促。 |                                            |            |
| 加入需求分组 | 可选择已有分组名称或新建分组，将相关的需求集合至某个需求分组中，节约项目经理统筹时间。 |                                            |            |



!> **关于成本分摊 ：填在需求方一栏**   1、在涉及到一个需求对应多个需求方部门时需要线下沟通确认后，可在行云中创建需求时录入   2、若该需求只是一个部门提出的，则由该需求方部门全部承担，即分摊比例为100%   3、原则上行云鼓励需求提出人为真正提需求的人和部门，但有些部门情况比较特殊，提出人不一定是对应的提需求的人，也允许代替需求方填写需求信息，在填写需求方时需要填入真正成本需要分摊的部门   4、当需求未被受理即在已受理之前，都可以更改分摊比例和分摊部门

## 需求工作流

?>  **通过工作流，规范需求管理流程。**

需求在流转过程中会出现不同状态，在行云中分为`需求状态`和`需求阶段`,需求方可以通过状态知晓需求目前进度。

`需求状态`指的是该需求在`需求管理`模块中的操作状态。  `需求阶段`指的是该需求在整个需求生命周期中的所处阶段（从需求提交到需求最终验收的整个环节），由系统自动计算汇总得出。  `需求状态`和`需求阶段`的关系如下：



| 需求状态 | 草稿 | 待受理 | 已受理 | 处理中      | 待验收      | 验收未通过  | 完成        | 驳回        | 取消        |             |             |        |            |      |      |      |
| -------- | ---- | ------ | ------ | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ------ | ---------- | ---- | ---- | ---- |
| 需求阶段 | 草稿 | 待受理 | 已受理 | 处理中-准备 | 处理中-评审 | 处理中-就绪 | 处理中-设计 | 处理中-开发 | 处理中-测试 | 处理中-发布 | 处理中-完成 | 待验收 | 验收未通过 | 完成 | 驳回 | 取消 |



### 需求转出

若收到一个需求不属于你的处理范围，可以选择`转出`给其他人进行处理。

如果需求的当前处理人即将异动或离职，需要进行工作交接，可以将手头需求`转出`给同事继续处理。

点击`转出`按钮，在弹窗内输入需要转给的同事ERP，点击提交便将需求成功转出。

![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/transferdemand1.jpg)



### 需求受理

需求被提报后，受理方需要进行`受理`操作，表示这个需求被确认接收了。`受理`操作表示：当前操作人确认了这个需求是可以做的，体现的是对客户的一种“承诺”。

![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/acceptdemand1.jpg)



### 需求拆分

当一个需求需要多个团队空间参与交付时，或者一个需求规模过大不满足线下约定的可以开始研发的规则（例如下述invest原则*）时，可支持将一个大粒度需求，如产品线需求，项目级需求分级为多个小粒度的需求，需求拆分支持无限级拆分，原则建议按一定规则拆分到小粒度需求，即可将需求处理到团队空间进行研发，系统支持按树形结构进行分层展示。

*invest原则：

1. 独立（尽可能的）：故事之间的依赖性尽可能小
2. 可协商：不用定太死，要讨论的内容需要注明
3. 有价值
4. 可估算：确保团队对需求有了解
5. 足够小：一个迭代内能够做完，不跨迭代
6. 可测试：定义清楚需求怎么样才算完成

<img src="http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/image-20220216111424196.png" alt="image-20220216111424196" style="zoom:50%;" />

点击`拆分`后，显示拆分需求详情页面： ![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/split1.jpg)

![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/split2.jpg)

依次填写好后，生成子需求，于是得到子需求列表。 

拆分的子需求将继承父需求的成本分摊比例，且不在拆分的需求中体现，只在父需求上体现。  

下图为拥有两个子需求的页面： ![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/split3.jpg)

当有两个以上子需求，且状态各不相同时，父需求的`需求阶段`以最靠前的子需求为准。   

如上图所示：子需求2的`需求阶段`为待开发，子需求3为处理中，则父需求的需求状态显示处理中。

!> **需要注意：** 父需求操作会影响子需求:   父需求取消后子需求联动取消，   已分配到团队空间的需求，将以中横线标识需求已取消，方便团队成员识别。   父需求发起验收后子需求联动发起验收。   父需求验收通过后子需求联动验收通过。



### 需求分组

点击需求名称右侧的`加入分组`即可将该条需求添加至相应分组，也可临时新建分组，组名支持最多20个中文或者40个英文。需求分组可以删除和修改名称。

![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/group01.png)

需求加入某一分组后，可以重复加入其它组，也可以`移出分组`

![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/group02.png)

需求分组支持分享，生成链接发送给需要关注的人，点开链接即可关注该分组和保存该分组。

![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/group04.png)

![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/group03.png)

`关注分组`后，该分组将出现在`关注分组`里；`保存分组`后，该分组将出现在`我的分组`里

![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/group05.png)





### 需求处理

系统支持将拆分到最末端的需求处理到对应的研发团队的需求backlog或者直接处理到迭代，也可以根据需要直接进行处理（不需要分配研发）。

具体来讲，`处理`支持两种处理方式：

- 如果一个需求需要多个开发协作处理，那么可以 选择`分配至团队空间`。比如：一个需求有UI制作、JAVA开发以及测试工作项需要协作处理。
- 如果一个需求 只需要进行简单的处理，或者不涉及开发工作，那么可以`直接处理`。比如：需求的预研工作或者配置管理的一些工作等。

需求在`受理`后便可进行`处理`操作。点击`处理`按钮： 

![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/work.jpg)



!> **需要注意：** 在`分配至团队空间`时候，需要提前在`团队空间`模块中建立自己的团队空间。一个需求初分配至`团队空间`时，将出现在`团队空间`的未计划里。另外，父需求不能再分配到团队空间，只能将末级节点的需求分配到团队空间，即“拆了不能分配”；已分配到团队空间的需求，则不能再被拆分，即“分配了不能拆”

### 需求变更

团队在执行需求过程中，经常会遇到需求变更，对于需求变更可能会需要走单独的确认流程或者再次执行需求评审过程。在团队空间中空间管理员根据团队整体要求进行配置需求变更约束。默认情况下团队空间中不体现变更流程，仅在用户变更需求相关字段后，将变更信息记录到操作历史中。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/clip_image002-4982146.jpg)

### 需求审批

系统支持在需求提出时配置审批流程，或者在发起验收时配置审批流程，目前支持串行审批流程。可在系统设置中进行配置。

![image-20220216113711118](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/image-20220216113711118.png)

### 需求撤回

需求提交以后，可以进行撤回，但 **前提** 是：**该需求尚未被 受理方 `受理`（即 状态为`待受理`时）**

![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/revoke.jpg)

### 重新分配

当把需求误分配到其他团队空间，点击`重新分配`可以再次进行分配团队空间。再次分配后，原先的卡片将被自动删除，不影响工时填报。

### 需求验收

当需求完成的时候，受理方可以`发起验收`操作。

![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/check.jpg)

提出需求的同学，可以对需求进行`通过`、`不通过`的验收操作。

![demand1](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/check2.jpg)

点击`通过`，则需求状态变成了`完成`，表示需求处理完毕；

如果对需求处理结果不满意，可以选择`不通过`，这样，需求状态就变为了`处理中`，这个需求会被继续完善处理。

## 收益验证

针对需求完成后，对需求是否达成ROI进行评价，评价等级包括：低于预期、达成预期、高于预期。验证后的收益支持查看和再次修改。

![image-20220216113922674](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/image-20220216113922674.png)

## 需求设置

### 需求权限

对于一些部门，由于业务要求，可以由专门的接口人进行提报需求，或者部门指定的人进行需求受理。均可以在系统设置中配置提出人或受理人白名单。进入系统设置中可以设定

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/clip_image002-4983005.jpg)

### 需求自定义

#### 扩展字段配置

支持的控件如文本输入框、开关控件、日期控件、下拉选择控件、数字输入框，用户可以拖动到预览区域进行配置查看，针对每个控件可以设置额外的提示文字、默认值、占位文字、是否只读等。用户根据业务要求，向管理员申请权限配置。如下图所示：

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/clip_image008.jpg)

#### 需求模板字段配置

部门管理员可以在此配置部门人员受理的需求需要完善的必填信息。通过该配置，把控提交给该部门的需求相关内容。该功能支持按照不同来源的需求进行需求的必填项配置，以及扩展字段的必填项配置和显示配置。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/clip_image012.jpg)

 

#### 需求白名单配置

部门管理员可以在此配置部门拥有提交或者受理需求权限的人员。在部门有需求接口人制度时，可以开启此功能来统一需求的进出口径。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/clip_image014.jpg)

#### 需求子流程配置

该功能支持部门管理员在部门内人员需求提交或者验收之后，需求流转到部门专属审批人进行审批。在部门需要指定人员进行需求审核时，可以开启此功能。

提交子流程生效范围：如需求提交人属于配置的部门，则在需求提交后触发该流程。

验收子流程生效范围：如需求提交人属于配置的部门，则在需求发起验收后触发该流程。

成本分摊子流程生效范围：如需求的成本分摊部门属于配置的部门，则在需求提交后触发该流程。

 

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/clip_image016.jpg)

 

#### 需求自动验收配置

管理员可以按照部门配置需求超期自动验收和研发需求自动验收功能。避免出现过多被忘记验收的需求，保证需求交付周期的准确统计。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/demand.assets/clip_image018.jpg)

