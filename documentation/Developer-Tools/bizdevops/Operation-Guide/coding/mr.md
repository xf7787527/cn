## 合并请求

点击“合并请求”，查看所有与自己相关的合并请求；同时支持根据不同条件搜索合并请求

### 创建的

* 此tab页面列出所有当前登陆用户创建的合并请求；  

* 默认按照“已开启的”/“已关闭的”分类、最新创建排序。

  ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/mr.assets/created-mr.png)

### 提及的

* 此tab页面列出在MR的comments中@过当前登陆用户的合并请求；   

* 默认按照“已开启的”/“已关闭的”分类、最新创建排序。

  ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/mr.assets/mentioned-mr.png)

### 邀请评审的

* 此tab页面列出在MR中邀请登陆用户评审的合并请求；  
* 默认按照“已开启的”/“已关闭的”分类、最新创建排序。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/mr.assets/review-requested-mr.png)

### 搜索合并请求

>搜索范围：当前登陆账户的所有可见仓库；public+internal+为仓库成员的private仓库

目前我们提供多项搜索条件，详细用法如下：

* **搜索创建者为某erp的MR**  
  author:erp  
    * 举例说明：  
      author:hanxiaojie3    

* **搜索MR状态为closed或者open的MR**  
  State:[closed,open]  
    * 仅支持closed, open两个值；其他值视为非法，并同时清空搜索条件state  
    * 举例说明：  
      author:hanxiaojie3 state:aaa  
         则仅返回符合搜索条件“author:hanxiaojie3”的MR  

* **搜索提及某个用户的MR**  
  mentions:erp  
    * 举例说明：  
      state:open mentions:hanxiaojie3  
        搜索状态为open并且在评论中提及hanxiaojie3的MR  
      ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/mr.assets/search_mentions.png)

>[说明:]目前尚不支持mentions与author的组合搜索   

* **搜索邀请某个用户评审的MR**  
  review-requested:erp  
    * 举例说明：  
      state:open review-requested:hanxiaojie3   
        搜索状态为open并且邀请hanxiaojie3参加评审的MR  
      ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/mr.assets/search_review_requested.png)  

>[说明:]目前尚不支持review-requested与author的组合搜索   

* **搜索 标题中包含某个关键字的MR**  
  title:content  
    * 举例说明：   
      author:hanxiaojie3 state:open title:commmit  
        搜索hanxiaojie3创建的title中包含“commit”的状态为openMR  
      ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/mr.assets/search_title.png)

* **按照创建时间搜索MR**  
  created:[>, <, =, >=, <=]  
    * 举例说明：  
      author:hanxiaojie3 created:>2020-03-12 repo:han-test/test-1115   
        搜索2020-03-12以后由hanxiaojie3创建的在某个特定repo中的MR  
      ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/mr.assets/search_created.png)


* **按照MR创建的源分支和目标分支搜索**  
  source-branch:branchname  
  target-branch:branchname  
    * 举例说明：   
      author:hanxiaojie3 state:open target-branch:master   
        搜索由hanxiaojie3创建的状态为open，target分支为master的MR  
      ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/mr.assets/search_branch.png)

 