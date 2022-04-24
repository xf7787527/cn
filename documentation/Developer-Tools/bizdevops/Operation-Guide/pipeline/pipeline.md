京东云流水线是一款提供持续集成、持续交付能力的产品。通过可视化、可定制的自动交付流水线，确保产品发布不同阶段的一致性和稳定性。基于容器技术和京东云基础服务架构，提供稳定和安全的构建，单元/自动化测试，弹性Kubernetes、VM及ECS环境部署的开发者工具服务，满足应用程序快速可靠的交付和更新。

## 创建流水线

1. 为了更方便快捷的创建流水线，Pipeline系统设计了多种创建流水线的入口：

   - 点击左侧栏空间名称后的 “+” 号新建流水线，空间可选择。

   - 点击左侧栏空间，进入流水线页面（凭证、成员、设置页面亦同），点击右上角 “创建流水线” 按钮新建流水线。

   - 点击左侧栏空间，进入流水线页面，点击流水线后方的复制流水线按钮，即可进入创建流水线页面，默认复制当前流水线（可选择）。

   ![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline.assets/newPipe.jpeg)

2. 用户在创建流水线时，可以选择创建空白流水线，或根据已有的流水线直接复制流水线配置来创建流水线

## 流水线详情

### 流水线配置


在左侧树中，选择要编辑配置的流水线，进行配置设置，如下图：

  ![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline.assets/pipeline_edit.jpeg)

进入配置页面，用户可以使用两种方式进行配置，普通的视图配置和yaml文件配置；针对yaml文件的配置方式，即直接在yaml文件中修改参数即可，所以我们在文档中着重介绍以视图的方式进行配置流水线。

  ![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline.assets/pipeline_edit1.png)

#### 配置开始触发项

   开始触发项中主要包含流水线的宏定义，变量设置，触发类型，通知，高级设置；
   ![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline.assets/trigger.png)

1. **宏定义**

   流水线的宏定义，输入宏的名称和值，以便在阶段（stage）和任务（step）使用。

   填写宏的名称和值后，系统自动保存，点击”删除“按钮，即可删除当前填写的宏信息；如下图：

     ![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline.assets/trigger1.png)

2. **变量**

变量的设置是以key-value的形式展示，是引用variable的时使用的变量，例如${{var.pacakge_name}}表示这是variable package_name的值， variable 变量在stage或者step中可以通过set来改变。

3. **触发方式**

   **手动触发**

   需要用户手动点击构建来触发流水线的运行；若选择手动触发时，需要用户自定义触发参数，参数以key-value的形式定义，点击“新增”可以定义多个触发参数。

     触发参数的引用方式： `${% raw %} {{out._predefine.KEY} }{% endraw %}`

   ```yaml
   yaml 示例
   trigger:
   type: manual
   parameters:
      branch: master #定义触发时要提供的参数branch， 默认是master
      deploy_env: test
   ```

    **事件触发**

    当有开发人员在代码库 push 或 merge 代码时，会自动触发对应流水线的运行。选择不同的触发方式需要配置的参数也不同。 若选择事件触发时，流水线的配置里，仓库信息必须填写

   ![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline.assets/trigger_type.png)

    若选择事件触发时，需要填写代码库地址，分支信息，以及触发事件（push、merge）。其中，包含分支是指该流水线适用的分支；排除分支是指该流水线适用于除了 “排除分支” 以外的所有分支。

      **分支**：区分为包含分支和排除分支。

      * 包含分支: 包含分支是指该流水线适用的分支， 只有event的分支（push event是push的对象分支，merge event指merge的target分支）符合定义的表达式，才会运行pipeline，允许配置多个分支，用 ','分割 

      * 排除分支：排除分支是指该流水线适用于除了 “排除分支” 以外的所有分支，当配置了包含分支，排除分支不会生效，允许配置多个分支，用 ','分割 

      * **branch filter 配置规则**：branch filter的includes或excludes中配置的branch表达式，要求匹配整个name字符串，不是它的一部分。在表达式详解如下

      ```
      '*'                                          匹配0或多个非/的字符
      '?'                                          匹配1个非/的字符
      '[' [ '^' ] { character-range } ']'   字符组（必须非空）(支持三种格式[abc],[^abc],[a-c])
      c                                           匹配字符c（c != '*', '?', '\\', '['）
      '\\' c                                      匹配字符c(可上面c的区别是 可以支持字符 * ? \\ [的匹配)
      ```

   **触发事件**：分为push或者merge（open，update，merge）两种事件；当选择merge时需要勾选merge的动作：

      * open：表示创建merge时进行触发

      * update：表示更新merge时进行触发

      * *merge：表示merge后进行触发

   ```yaml
   yaml 示例
   trigger:
   type: event
   triggerEvents:
         - merge
      mergeActions:
         - open
         - update
      branches:
         include:
         - release/*
         - test[1-8]
         exclude: []
   ```

   如上面yaml示例中的release/* 会匹配所有以 release/开头的branch， test[1-8]会匹配test1, test2... test8
   **定时触发**

   在某个或者一些列的时间触发job，定义格式和linux crontab一致，详见：[cron格式](https://linuxtools-rst.readthedocs.io/zh_CN/latest/tool/crontab.html#id4)

   ```yaml
   yaml 示例
   trigger:
   type: cron
   cron: '*/5 * * * *' #每5分钟执行一次
   ```

   **参数共用：**配置了事件触发的流水线，可以直接使用:事件变量作为参数。例如：gitlabBranch作为下载代码或者jone编译的分支，如果分支变量同时想作为自定义参数在手工触发时使用，可以直接在自定义参数中使用gitlabBranch这个变量。
   自定义参数中分支的设置

   ![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline.assets/gitlabBranch_manual.png)

   jone编译中分支的设置（download_code引用方法一样）

   ![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline.assets/gitlabBranch_event.png)

4. **高级设置**

   * 超时时长：超过设置的时长后将终止pipeline, 默认超时时长为5小时；

   * 回写代码库：事件触发的流水线在勾选后可以在代码库页面看到流水线状态的更新, 该功能只有事件触发时可设置。

   * 执行方式：支持流水线的串行操作；默认选中。


#### 阶段（Stage）的配置

   阶段是流水线操作中的一个单独可以rerun的单元。可以在某个阶段设置多个任务。

   **阶段名称**：是该条流水线的唯一标识（关键字），在输出参数的引用中，将需要配置该字段；

   **展示名称**：为了更好的将流水线展示给用户清晰，容易理解的名字，用户可以命名展示在流水线上的名称，方便理解。

   **暂停点**：当勾选后，在该阶段执行完毕，需要手动触发下一阶段的任务执行。

   **归档文件**：填写需要归档的文件路径，以换行符分割

   **高级设置**：

   * 超时时长：和配置开始项的使用类似。若stage的配置时长超过了流水线的整体配置时长（开始配置项中设置），则以整体配置为准；

   * 允许忽略错误：勾选后将忽略执行过程中发生的任何错误。

   * 定义输出参数：阶段的输出参数是以key-value的形式展示，定义输出参数，是选择该阶段（stage）下的任务（step）重新定义名称以及输出值。

   > [说明：]
   >
   > 1. 输出参数的定义：参数名称由用户自己定义，名称可用于stage之间传参，然后选择该stage下的step，最后选择step对应的output，点击添加按钮，即可添加输出参数。
   > 2. 可添加多个输出参数。
   > 3. stage之间参数传递格式：${{out.STAGENAME.STAGEOUTPUT}}。

   * 测试环境执行：需要勾选在测试环境执行，由于测试环境（192网段）是和线上网段隔离，如果无测试环境网络权限，需要想网络组申请相应的网络权限

![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline.assets/stage_config.png)

#### 任务（Step）的配置

   任务是各种操作函数的集合，一个stage下可以包含多个step。
   在

   点击stage下方的 “+” 即可新增step，用户在配置step时，可以选择系统自带的step模板，也可以选择自定义的step模板使用：

   * **选择系统step模板**。点击要配置的step，右侧抽屉式弹出step配置页面，在系统模板里选择模板，点击模板进入step编辑页面，填写相应的参数信息，保存即可配置step。
   * **选择已经自定义好的step模板**。已经自定义好的模板可以在空间模板管理页面进行查看。点击要配置的step，右侧抽屉式弹出step配置页面，在自定义模板里选择需要的模板，点击模板进入step编辑页面，填写相应的参数信息，保存即可配置step。引用之前step的输出变量使用${{env.STEPNAME.OUTPUTNAME}}

用户可以在step编辑页面点击 “查看源码” 查看模板源码（模板源码仅能查看），通过复制模板源码可以更方便的在模板管理页面新建模板。在模板管理页面新增、编辑step模板

   ![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline.assets/step.png)


### 执行流水线

流水线配置完成后，点击“保存并运行”按钮，即可在保存流水线的同时运行流水线，自动跳转到执行页面。流水线的执行页面展示了流水线运行的实时状态，以及流水线运行的相关信息，包括该流水线的运行历史、执行人、执行时间。

流水线执行时，不同颜色的stage节点表示不同的执行状态。灰色表示未执行的stage节点，绿色表示执行成功的stage节点，红色表示执行失败的stage节点，黑色表示执行暂停的stage节点，而执行中的stage节点以灰色旋转状态显示。

![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline.assets/build.png)

流水线的执行方式主要有构建、重新构建，除此之外，系统还提供了中断、暂停、重试等与执行相关的操作。下面将详细介绍。

1. 构建（build）

   点击 “构建” 按钮，可执行流水线，在执行页面可以查看实时日志，以及历史构建的执行详情。为了更方便的执行流水线，系统提供了多种构建流水线的入口：

   - 进入流水线编辑页面，点击右上角 “构建” 按钮执行流水线，页面自动跳转到执行页面。

   - 左侧栏点击流水线进入构建历史页面，点击右上角 “构建” 按钮执行流水线，构建历史列表自动更新，点击最新构建历史可进入执行页面。

   - 在流水线执行页面，点击右上角 “构建” 按钮，执行流水线。

   ![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline.assets/builds.png)

2. 重新构建（rebuild）

   重新构建是指根据当前版本的配置进行构建，若流水线配置已改变，重新构建时会提示用户配置已修改，将重新构建最新版本配置的流水线。重新构建流水线的入口：

   - 左侧栏点击流水线进入构建历史页面，点击要重新执行的流水线版本后的 “重新构建” 按钮，构建历史列表会自动更新，点击最新构建历史可进入执行页面。
   - 在流水线执行页面，点击右上角 “重新构建” 按钮，执行流水线。

   ![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline.assets/rebuild.png)

3. 暂停与继续（pause、continue）

   流水线可以在配置stage时设置暂停点，若设置暂停，则流水线执行完该stage会自动暂停执行，只有点击 “继续” 才会继续执行，而点击 “取消” 则会停止执行。

   ![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline.assets/pause_build.png)

4. 中断（abort）

   流水线在执行过程中可以手动点击 “中断” 按钮，停止执行流水线。中断流水线的入口如下：

   - 在执行页面，点击构建执行流水线后，右上角会显示 “中断” 按钮，点击即可中断执行。
   - 在构建历史页面，正在执行的流水线后会显示 “中断” 按钮，点击即可中断执行。
   - 若流水线暂停执行，可以通过执行页面或构建历史页面的 “中断” 按钮，停止执行。

   ![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline.assets/abort_build.png)

   ![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline.assets/abort.png)

5. 重试（rebuild from stage）

   流水线每个执行结束的stage节点下会出现 “重试” 按钮，点击 “重试” 可以重新执行该stage。

   ![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline.assets/rebuild_from_stage.png)



### 查看构建日志

在执行页面点击stage可以查看流水线的构建日志，日志以stage下每一个step节点分开展示。流水线正在执行时，默认根据流水线的执行进度，展示当前执行stage节点的日志信息，默认是展开日志状态，点击可关闭日志。同时，用户可以手动点击stage节点查看节点日志内容。

用户也可以选择历史构建版本，查看历史执行的日志信息。

![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline.assets/log.png)

### 查看构建历史

构建历史页面展示了流水线执行的详细信息，包括执行状态、构建版本、开始时间、持续时间，以及触发人。在构建历史页面，可以直接构建或重新构建流水线。点击某一执行历史，可跳转到执行页面查看该次构建的执行详情。查看构建历史的入口：

- 在左侧栏，点击流水线可直接进入构建历史页面查看流水线的执行历史。
- 点击空间，进入空间下流水线管理页面，点击流水线可查看构建历史。
- 在执行页面的左上角构建历史里，直接选择某一执行历史查看其详情。
- 在执行页面，点击右上角 “构建列表” 可进入构建历史页面。

![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline.assets/history.png)

## 流水线成员管理

1. 点击左侧栏流水线名称后的设置按钮，进入该流水线的成员管理页面（也可以通过空间流水线页面的流水线设置按钮进入）。成员管理页面展示了该空间下的成员信息。

   流水线的权限高于空间权限，权限设置与空间权限类似

   ![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline.assets/pmember.png)

## 流水线设置

点击左侧栏流水线，进入该流水线的成员管理页面，然后点击 “设置” ，进入流水线设置页面（也可以通过空间流水线页面的流水线设置按钮进入）。在流水线设置页面，可以转移和删除该流水线，**注意，只有Owner权限的用户可以进行转移和删除操作。**

转移流水线：流水线的Owner可以将流水线负责人转移给流水线的任何一个成员，转移完成后，原Owner用户还是该流水线的成员，并且权限自动变更为“admin”权限。

删除流水线：**Owner权限的用户可以删除该流水线，此操作不可逆。**

![image](http://devops-minio.jdcloud.com/doc-image/All-Image/pipeline.assets/pipe_setting.png)