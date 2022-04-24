# 产品概述

视频介绍：

{{video}}[ src="//starlink.s3.cn-north-1.jdcloud-oss.com/help/starlink_introduction.mp4"  poster="//starlink.s3.cn-north-1.jdcloud-oss.com/help/poster.png" width="700" ]

## 产品介绍
星链是一个函数服务平台，面向事件处理、服务前端的后端(BFF)、服务流程编排等应用场景，以可视化、组件化方式低代码开发函数服务，以声明式进行Serverless部署，帮助您快速交付场景化业务研发需求，它的特色可以用三个关键词概括：低代码、微服务和Serverless。

### 低代码 
星链是一个低代码函数服务平台，提供了简单灵活的编程模型，用VMS（可视化微服务）概念表示一个微服务，通过触发器、函数、连接器概念简化微服务开发，内外依赖组件化、配置化，使开发人员可以聚焦业务逻辑。提供了低代码Cloud Web IDE，通过可视化微服务编排，参数映射自动提示等提高开发效率。

星链提供了独特的业务组件库功能，除了提供系统公共组件，星链还支持自定义团队组件，支持用户在VMS内自定义连接器，自定义连接器的方法，支持导出到团队组件库，支持拖拽式导入团队组件和系统公共组件。

除了提升研发工作的抽象层次，提升效率，星链充分考虑灵活性，完整支持代码功能，且支持多语言，目前支持Java/JavaScript/Groovy，更多语言支持在规划中，支持在线代码函数编写，支持在线调试。

与大多低代码平台是黑盒子不同，星链开发的VMS保存在Git仓库上，源码是完全可见的，用户可以克隆到本地开发，可以使用本地IDE如IDEA/VS Code开发，支持引入第三方标准类库，而且，代码提交后，在Cloud Web IDE上也完全兼容可见。

### 微服务

星链低代码面向的是后端微服务开发和编排，目前不包含前端界面快速开发，也不会自动创建和管理数据模型。

常见的低代码平台开发的功能主要面向后台管理，而星链开发的微服务除了可以服务内部后台管理外，更多的是To C场景，这是因为星链是无状态内存执行，相比业界大多基于数据库或消息系统的编排引擎，延时低，更适合服务编排，目前已广泛应用于面向C端用户的高并发、低延时场景，在京东内部历经618、双十一性能和稳定性考验。

### Serverless

在星链中开发、测试、部署，不需要准备服务器计算资源，按需直接使用即可。

星链支持一键在线构建打包，构建时自动打标签，可以实时查看构建日志，可以下载构建完成的包，可以查看构建历史。

为了管控上线质量，星链集成上线审批流程，对于上线正式版本，需要经过测试和管理员两级审批。

星链支持声明式部署，在部署时，不需要关注服务器细节，只需要说明部署的集群分组、需要部署的实例个数、部署的版本即可，系统自动调度，在部署状态中可以查看是否满足部署期望，部署的细节等。星链复用计算引擎资源，没有冷启动，热加载，部署快。

星链支持部署环境隔离，区分测试、预发、生产三个不同环境，每个环境分别部署。

星链支持部署态加密环境变量，针对数据库密码等敏感变量，可以在部署配置中再填写，且可以指定加密存储，原文不存储在任何地方，确保安全。

## 更多文档

- 产品简介
  - [核心概念](../Introduction/Core-Concepts.md)
  - [产品优势](../Introduction/Benefits.md)
  - [产品功能](../Introduction/Features.md)
  - [限制说明](../Introduction/Restrictions.md)
  - [产品定价](../Pricing/Billing-Overview.md)
          
- 入门指南
  - [登录](../Getting-Started/Getting-started.md)
  - [新建团队](../Getting-Started/Create-Team.md)
  - [新建VMS](../Getting-Started/Create-VMS.md)
  - [开发VMS](../Getting-Started/Dev-VMS.md)
  - [部署VMS](../Getting-Started/Deploy-VMS.md)
- Demo示例
  - [Hello World](../Demo/HelloWorld.md)
  - [Java示例](../Demo/Java.md)
  - [Groovy示例](../Demo/Groovy.md)
  - [JavaScript示例](../Demo/JavaScript.md)
  - [出行防疫政策API示例](../Demo/HelloHealth.md)
  - [AI服务示例](../Demo/HelloAI.md)
- 开发VMS
  - [开发触发器](../Operation-Guide/Dev/Trigger.md)
  - [开发连接器](../Operation-Guide/Dev/Connector.md)
  - [开发函数](../Operation-Guide/Dev/Function.md)
  - [BPMN流程编排](../Operation-Guide/Dev/BPMN.md)
  - [组件库](../Operation-Guide/Dev/Component.md)
  - [表达式语法](../Operation-Guide/Dev/Expression.md)
  - [环境变量](../Operation-Guide/Dev/Env.md)
  - [Git操作](../Operation-Guide/Dev/SDK.md)
  - [平台SDK](../Operation-Guide/Dev/Git.md)
- 部署VMS
  - [构建](../Operation-Guide/Deploy/Build.md)
  - [发布审批](../Operation-Guide/Deploy/Process.md)
  - [部署](../Operation-Guide/Deploy/Deploy.md)
  - [监控报警](../Operation-Guide/Deploy/Monitor.md)
- 管理
  - [团队管理](../Operation-Guide/Management/Team.md)
  - [VMS管理](../Operation-Guide/Management/VMS.md)
  - [组件管理](../Operation-Guide/Management/ComponentManagement.md)  
  
