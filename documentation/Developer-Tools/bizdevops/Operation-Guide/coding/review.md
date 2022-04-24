## 评审 & 合并

目前支持四种代码评审触发方式（Merge Request，Push Request，Pull Request，Only Review）；以及四种代码合并方式（Merge，Merge with non fast-forward，Squash and merge，Rebase and merge）。

### 评审触发方式

四种评审模式的定义：
**Merge Request**：同一仓库中，不同分支间的合并请求所触发的代码评审。

**Push Request**：开发者push新内容时，同时触发代码评审。

**Pull Request**：开发者Fork了当前仓库（比如：A 仓库），当开发者在自己的仓库完成开发后，由当前仓库（A 仓库）的所有者获取开发者仓库的新功能时，触发代码评审。

**Only Review**：Coding平台支持的事后评审情况（即，代码已经合入到目标分支，但后续再次对合并后的代码进行代码评审，此种评审方式，仅仅评审，不会再次合并代码。）

#### Merge Request

实现了同一仓库中，不同分支间的合并请求所触发的代码评审。

1. 选择该仓库，选择**合并请求**页签，点击**新建合并请求**按钮，进入新建评审页面。
   ![](http://devops-minio.jdcloud.com/doc-image/All-Image/review.assets/review00.jpg)
2. 在新建评审页面，首先选择**源分支**和**目标分支**，点击**创建合并请求**按钮，在当前页面弹出添加评审标题和内容的界面。
   ![](http://devops-minio.jdcloud.com/doc-image/All-Image/review.assets/review1.jpg)
3. 输入评审标题和评审内容。如果需要自定义设置本次评审的评审人员，点击评审人员右侧的**自定义**，即可设置。
   ![](http://devops-minio.jdcloud.com/doc-image/All-Image/review.assets/review2.jpg)
4. 点击**创建合并请求**按钮，该评审创建完成，在该评审页面，可查看到评审状态，合并状态，以及相应的评审策略。
   ![](http://devops-minio.jdcloud.com/doc-image/All-Image/review.assets/review5.jpg)
5. 根据正常流程代码评审，合并代码即可；

#### Push Request

实现了开发者push新内容时，同时触发代码评审的操作。

如果您在代码库中想对某个分支使用**Push Request**这种评审方式，需要先对该分支设置强制代码评审策略，设置方法如下：

1. 进入仓库，点击**设置**按钮，点击左侧的**评审规则**菜单，即进入评审规则设置页面，

2. 点击右上角**自定义评审策略**,设置评审策略，在**强制评审策略**中，勾选**Push代码时创建评审**；根据需要可以设置是否**阻塞代码直接合入目标分支**，如果勾选了该选项,则表`git push`命令推送的代码，必须评审通过后，才会被合入到目标分支。

   ![](http://devops-minio.jdcloud.com/doc-image/All-Image/review.assets/setting_ CustomizeReview.jpg)

3. 研发本地开发完成，可以使用git命令进行提交代码，基本命令如下：

   ```
   $ git add . #将当前目录所有文件添加到git暂存区
   $ git commit -m "my first commit" #提交并备注提交信息
   $ git push origin master #将本地提交推送到远程仓库
   ```

   提交代码的同时，Coding系统将会自动创建一个评审，根据设置的**强制代码评审策略**判断是否可以自动合入到目标分支。

4. 根据正常流程代码评审，合并代码即可。

#### Pull Request

实现了开发者Fork了基础仓库（比如：A 仓库），当开发者在自己的仓库完成开发后，由基础仓库（A 仓库）的所有者获取开发者仓库的新功能时，触发代码评审的操作。

1. **派生仓库**：如果您不想在基础仓库中开发，可以将该仓库派生到个人的群组中，在派生库中开发新功能；

2. 登录coding平台，找到基础仓库，选择该仓库，选择**合并请求**页签，点击**新建合并请求**按钮，进入新建评审页面。

3. 在新建评审页面，点击**与派生库进行比较**按钮，选择**head**仓库及分支，选择**base**仓库及分支。 
   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/review.assets/WX20190513-172419@2x.png)

4. 输入评审标题和评审内容。如果需要自定义设置本次评审的评审人员，点击评审人员右侧的**自定义**，即可设置。

5. 点击**创建合并请求**按钮，该评审创建完成，在该评审页面，可查看到评审状态，合并状态，以及相应的评审策略。

6. 根据正常流程代码评审，合并代码即可。


#### Only Review

实现了如何对已经合入的代码进行两个commits的Review评审。属于事后评审情况（即，代码已经合入到目标分支，但后续再次对合并后的代码进行代码评审，此种评审方式，仅仅评审，不会再次合并代码。）

当代码已经合入到目标分支，但是需要代码提交到coding后，登录coding平台，找到该仓库，按照以下步骤进行代码评审操作：

1. 选择该仓库，选择**合并请求**页签，点击**新建合并请求**按钮，进入新建评审页面。
2. 在新建评审页面，首先选择**base commit**和**compare commit**，点击**创建合并请求**按钮，在当前页面弹出添加评审标题和内容的界面。
   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/review.assets/only_review1.jpg)
3. 输入评审标题和评审内容。如果需要自定义设置本次评审的评审人员，点击评审人员右侧的**自定义**，即可设置。
4. 点击**创建合并请求**按钮，该评审创建完成，在该评审页面，可查看到评审状态，合并状态，以及相应的评审策略。
5. 评审组成员对该次评审进行评审即可。


## 代码评审

1. 评审人员收到评审通知（coding界面通知）后，评审该条记录。

   * 界面通知：点击该条MR评审记录，即可跳转到评审界面。
2. 评审人员点击进入该条评审记录，进入评审的**对话**页面，可查看到该评审的基本信息。点击**开始评审**按钮，或者**添加你的评审**或者**更改的文件**页签，跳转到评审页面。
   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/review.assets/review7-20220210142348885.jpg)

3. 在评审页面，可查看到本次评审的变更内容，对变更内容进行评审，或者添加你的评论。评审过程中，可对单行代码进行评论，添加完成后，评审内容是Pending状态，提交评审意见后，其他评审人员即可看到该评论。
   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/review.assets/review9-1.jpg)

4. 点击**Review changes**按钮，填写评论内容，选择评审意见（评论，通过或拒绝 ），代码评审内容支持Markdown格式，点击提交，即评审完成。
   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/review.assets/review9-20220210142411887.jpg)

## 合并代码

若评审通过后，根据合并策略的设置，确定是否需要自动合并到目标分支。

* 若合并策略勾选了允许评审通过后自动合并代码，则代码将会自动合入到目标分支；

* 若未勾选，则需要目标分支有权限的成员，根据需求，选择相应的合并方式进行手动合并；
  我们提供四种合并方式：  

>[四种代码合并方式的定义]

>**Merge**：这种方式会优先尝试fast-forward（快进）方式merge，若行不通，再尝试non-fast forward方式。**默认方式**

>**Merge with non fast-forward**：采用non-fast forward方式merge，总是会在目标分支头部生成一个合并点。

>**Squash and merge**：将源分支上所有要合并的commits先汇合成一个commit，然后提交到目标分支头部。

>**Rebase and merge**：Rebase是一种变基操作，本质是将source branch的commits一个一个有序的cherry pick到目标分支头部，保留每个commit的内容但变更sha1。使目标分支的版本树看起来是一条线，简洁易读。  

Coding系统**手动合并**选择页面如下图：  

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/review.assets/merge_code.jpg)

### 四种合并方式的定义与图解

#### Merge

>这种方式会优先尝试fast-forward（快进）方式merge，若行不通，再尝试non-fast forward方式。**默认方式**

**示例一：fast-forward方式**  
如下图所示，bugfix分支从master分支branch out。  

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/review.assets/default-merge-pic1.png)

  合并bugfix分支到master分支时，master分支的状态**没有被更新过**。  
  此时Merge会优先采用**"fast-forward"**（快进）方式，将master分支的head移动到bugfix分支的最新提交。merge后的版本树如下图：  

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/review.assets/default-merge-pic2.png)   **示例二：non-fast forward方式**
  同样的，bugfix分支从master分支branch out，但此后**master分支上有新的提交**。    

  ![](http://devops-minio.jdcloud.com/doc-image/All-Image/review.assets/default-merge-pic3.png)   

  合并bugfix分支到master分支时，Merge会采用**"non-fast forward"**方式，在目标分支头部生成一个新的merge point E。merge结果如下图： 

  ![](http://devops-minio.jdcloud.com/doc-image/All-Image/review.assets/default-merge-pic4.png)   

#### Merge with non-fast forward

>采用non-fast forward方式merge，总是会在目标分支头部生成一个merge point（合并点）。

**示例：**如下图，bugfix分支从master分支branch out，此后master分支**没有再被更新过**。  

  ![](http://devops-minio.jdcloud.com/doc-image/All-Image/review.assets/merge-non-fast-forward-pic1.png)  

  采用non-fast forward方式合并bugfix分支到master分支时，会在目标分支master头部产生一个merge point C。如下图示意：

  ![](http://devops-minio.jdcloud.com/doc-image/All-Image/review.assets/merge-non-fast-forward-pic2.png)  

#### Squash and merge

>将源分支上所有要合并的commits先汇合成一个commit，然后提交到目标分支头部。

**示例：**如下图所示，bugfix分支从master分支branch out。

  ![](http://devops-minio.jdcloud.com/doc-image/All-Image/review.assets/squash-merge-pic1.png)  

  采用squash方式合并bugfix分支到master分支时，bugfix分支的commitX和commitY会先被汇合成一个commit，然后被提交到master分支头部。如下图示：

  ![](http://devops-minio.jdcloud.com/doc-image/All-Image/review.assets/squash-merge-pic2.png)  

#### Rebase and merge

>Rebase是一种变基操作，本质是将source branch的commits一个一个有序的cherry pick到目标分支头部，保留每个commit的内容但变更sha1。使目标分支的版本树看起来是一条线，简洁易读。

**示例：**如下图所示，bugfix分支从master分支branch out。  

  ![](http://devops-minio.jdcloud.com/doc-image/All-Image/review.assets/rebase-merge-pic1.png)  

  采用rebase方式合并bugfix分支到master分支时，bugfix分支的commitX和commitY会被有序的添加到master分支的头部。如图所示，master分支的历史记录成一条直线。  

  ![](http://devops-minio.jdcloud.com/doc-image/All-Image/review.assets/rebase-merge-pic2.png)  

