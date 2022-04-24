# Issues

## 关联行云团队空间及Workflow设置

>[说明:]仓库Master及以上权限成员可以行云团队空间

  * 仓库-设置-Issues，进入配置页面；
  * 点击 “关联团队空间”
  * 显示当前登陆用户有权限的行云团队空间，选择团队空间并确认;
  * 每个仓库只能关联唯一的行云团队空间；
    ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/issue.assets/link_teamspace.png)

  * 支持更新或者解除已关联的团队空间;
  * 更新团队空间后，旧团队空间数据将不再展示到Issues页面；
    ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/issue.assets/update_teamspace.png)

  * 设置issues流转workflow：团队空间关联后，Coding设置了默认的issues状态流转workflow(用户可更新);
    * 关联“敏捷模式”团队空间，默认的：
      - Commit中关联的卡片自动流转为“开发阶段”第一个状态；
      - MR中关联的卡片可流转为“测试阶段”第一个状态
    * 关联“通用模式”管队空间，默认的：
      - Commit中关联的卡片自动流转为“DOING“；
      - MR中关联的卡片可路转为”Done“
        ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/issue.assets/workflow_settings.png)

### Coding Issues中展示行云卡片

  * 关联特定行云团队空间后，团队空间卡片会自动同步至“仓库-Issues”页面；
  * 仅平行展示行云团队空间中的卡片，不展示任务；
  * 按照卡片状态分为两类：
    * 待开发：对应行云卡片“测试”阶段及之前的卡片
    * 已完成：对应行云卡片“测试”阶段之后的卡片
  * 可以按照“标签”/“迭代”/“状态”/“受理人”等条件筛选；
    ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/issue.assets/show_card.png)

 * 点击卡片标题，打开卡片详情页；
 * 详情页面可以编辑： “标题”/“描述”/”卡任务处理人”/”迭代”/“状态”/“关联合并请求”
   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/issue.assets/show_card_detail.png)

* 详情页面同时展示关联的commit与合并请求;
  ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/issue.assets/show_card_detail_2.png)

### Coding Issues中快速新建卡片

  * Issues中可以快速新建卡片；
  * 新建后的卡片将自动同步至关联的行云团队空间
  * 新建时需填写：
    *  卡片title
    *  卡片迭代
    *  卡片状态（默认设置为“需求沟通”或者“TODO”）
       ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/issue.assets/new_card.png)

### 关联“Commit”及状态流转

  * 在符合约定式提交的Commit中关联卡片，支持卡片状态**自动流转**；
    * 使用`git commit -m `提交时关联卡片，卡片ID以“#”开头儿，例如：
      `git commit -m "fix: <简短描述|必填> #C2020090167504"`
    * 支持UI界面提交时关联‘行云卡片:
      ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/issue.assets/link_commit.png)

  * Commit中关联的issue触发状态的自动流转；默认的将issues状态流转为“开发阶段”第一个状态
  * 合并请求创建成功后，commits中关联的issue将自动显示在MR的右侧“已关联的issues”
    ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/issue.assets/link_commit_2.png)

关联“合并请求”及状态流转

  *  支持Issue页面关联“合并请求”；
     ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/issue.assets/link_mr.png)

  *  支持“合并请求”页面关联issue
     ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/issue.assets/link_mr_2.png)

  *  合并请求merge时: 支持对已关联的issue状态流转且目标状态用户可选；
     ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/issue.assets/issue-transfer-status.png)

  *  合并请求Merge成功后，可以查看关联卡片的状态；
     ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/issue.assets/issue-status-updated.png)

### 权限管理

| 操作                | 角色和权限                                           |
| ------------------- | ---------------------------------------------------- |
| 设置/关联空间       | `Master`及以上                                       |
| 筛选Issues          | `GUEST`及以上                                        |
| 新建Issue           | `GUEST`及以上 and 是团队空间`成员`及以上             |
| 编辑Issue           | `GUEST`及以上 and 是团队空间`成员`及以上             |
| 变更Issue状态       | `GUEST`及以上 and 是团队空间`成员`及以上             |
| 变更Issue迭代       | `GUEST`及以上 and 是团队空间`成员`及以上             |
| 增删Issue受理人     | `GUEST`及以上 and 是团队空间`成员`及以上             |
| 关联合并请求        | `GUEST`及以上 and 是团队空间`成员`及以上             |
| 合并请求下关联Issue | `GUEST`及以上 and (`合并请求创建者` or `MASTER角色`) |

