## 部门视图

主要从部门的维度查看部门下的相关视图，代码库，群组，成员的情况，部门负责人可以查看每个成员提交代码的相关数据。

### 部门总览视图

在部门视图，可以查看您所在部门下的代码提交趋势，代码评审趋势，活跃代码库的趋势，以及top10活跃仓库的情况。

>[权限说明]

>默认可查看本部门以及子部门的部门视图，不能查阅其他部门下的代码提交情况。

| 指标           | 说明                                                         |
| -------------- | ------------------------------------------------------------ |
| 代码库所属部门 | 根据代码库的owner成员所在部门进行划分。                      |
| 活跃代码库     | 统计周期内，该部门下活跃的代码库数（根据commit提交情况，作为活跃情况），并对代码库进行去重操作，从两个维度呈现；<ol><li>按天汇总展示趋势；</li><li>统计周期内的活跃代码库总量；</li></ol> |
| 代码提交       | 统计周期内，根据提交代码的成员所在部门对代码提交量进行汇总计算，从两个维度呈现；<ol><li>按天汇总展示趋势；</li><li>展示统计周期内的提交总量。</li></ol> |
| 代码行数       | 统计周期内，根据提交代码的成员所在部门分别对新增代码行数，删除代码行数进行汇总计算，从两个维度呈现；<ol><li>按天汇总展示趋势；</li><li>展示统计周期内的新增代码行数和删除代码行数。</li></ol> |
| 代码评审       | **代码评审通过的准则**：是根据用户设置的代码评审规则，当该次评审状态为通过时，即为通过；<br> 统计周期内，根据发起代码评审的成员所在部门进行汇总计算，从三个维度呈现；<ol><li>按天汇总展示趋势；</li><li>统计周期内的发起评审总量和代码评审通过数。</li></ol> |
| 代码语言类型   | 该部门下，代码库设置的语言类型进行计算，并百分比呈现。       |
| TOP10仓库      | 根据代码库的活跃情况，以及发起代码评审的总量进行TOP10代码库的取数呈现。 |

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/department.assets/department.jpg)

## 部门仓库查看与管理

### 部门仓库列表

**过滤条件以及排序方式**

| 过滤条件                                              | 排序方式                                                     |
| ----------------------------------------------------- | ------------------------------------------------------------ |
| <ul><li>部门负责的(默认)</li><li>部门参与的</li></ul> | <ul><li>按更新时间降序(默认)</li><li>按更新时间升序</li><li>按名称字母序升序</li><li>按名称字母序降序</li></ul> |

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/department.assets/department_repo.jpg)

### 批量管理部门仓库

机构负责人和机构管理员，可以对该**机构负责的仓库** 进行如下批量管理

#### 变更仓库负责人

a. 查询并选择要变更的仓库；选择“变更仓库负责人”选项：  
![img](http://devops-minio.jdcloud.com/doc-image/All-Image/department.assets/department_repo_changeowner1.png)

b. 指定新的负责人；如果想移除原负责人，请勾选“同时移除原Owner”：  
![img](http://devops-minio.jdcloud.com/doc-image/All-Image/department.assets/department_repo_changeowner2.png)

c. 点击“确定”，显示详细结果：  
![img](http://devops-minio.jdcloud.com/doc-image/All-Image/department.assets/department_repo_changeowner3.png)

#### 转移仓库空间

a. 查询并选择要转移的仓库；选择“转移仓库空间”选项：  

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/department.assets/department_repo_transferspace1.png)

b. 指定新的仓库空间，仓库空间可选范围为当前操作人有权限的空间；  
c. 点击“确定”，显示详细结果：  

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/department.assets/department_repo_transferspace2.png)

#### 添加仓库成员

a. 查询并选择要操作的仓库；选择“添加仓库成员”选项：  

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/department.assets/department_repo_addmember1.png)

b. 指定要添加的成员并指定成员角色，支持同时添加多位成员
c. 点击“确定”，显示详细结果

移除仓库成员

a. 查询并选择要操作的仓库；选择“移除仓库成员”选项：  

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/department.assets/department_repo_removemember1.png)

b. 指定需要移除的成员，支持同时移除多位成员； 
c. 点击“确定”显示预操作结果；如果要继续请点击“再次确认”

## 部门群组查看与管理

在**群组**页面，即可查看(管理)所在部门的群组，以及查看群组的访问权限，群组下的仓库数量和成员数量。

* 普通成员可根据不同维度进行群组筛选查看；  
* 机构负责人/机构管理员还可以批量管理部门群组；

### 部门群组列表

**过滤条件以及排序方式**

| 过滤条件                                              | 排序方式                                                     |
| ----------------------------------------------------- | ------------------------------------------------------------ |
| <ul><li>部门负责的(默认)</li><li>部门参与的</li></ul> | <ul><li>按更新时间降序(默认)</li><li>按更新时间升序</li><li>按名称字母序升序</li><li>按名称字母序降序</li></ul> |

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/department.assets/department_team.jpg)

### 批量管理部门群组

机构负责人和机构管理员，可以对该**机构负责的群组** 进行如下批量管理：

#### 变更群组负责人

a. 查询并选择要变更的群组；选择“变更群组负责人”选项:  

  ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/department.assets/department_team_changeowner1.png)

b. 指定新的负责人；如果想移除原负责人，请勾选“同时移除原Owner”：  
![img](http://devops-minio.jdcloud.com/doc-image/All-Image/department.assets/department_team_changeowner2.png)

c. 点击“确定”，显示详细结果：  
![img](http://devops-minio.jdcloud.com/doc-image/All-Image/department.assets/department_team_changeowner3.png)

#### 添加群组成员

a. 查询并选择要操作的群组；选择“添加群组成员”选项：  

  ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/department.assets/department_team_addmember1.png)

b. 指定要添加的成员并指定成员角色，支持同时添加多位成员  

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/department.assets/department_team_addmember3.png)

c. 点击“确定”，显示详细结果：  

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/department.assets/department_team_addmember2.png)

#### 移除群组成员

a. 查询并选择要操作的群组；选择“移除群组成员”选项：  

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/department.assets/department_team_removemember1.png)

b. 指定要移除的成员，支持同时移除多位成员
c. 点击“确定”显示预操作结果；如果要继续请点击“再次确认”

## 部门成员列表

在**成员**页面，即可查看所在部门下在Coding系统中的成员信息，以及成员所参与的代码库数量和群组数量。

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/department.assets/department_member.jpg)

## 部门设置

### 添加管理员

在“管理员设置”页面，可以为该部门添加两种角色：

* Admin
* Viewer

**Admin**：可以批量管理本部门的仓库/群组/成员，以及设置组织级规则  
**Viewer**：相当于机构负责人的只读权限，可以查看部门的各种统计视图  

>[Admin/Veiwer的说明]
>
>* 支持跨部门、跨体系添加Admin/Viewer  
>  比如：成员A属于四级部门成员，可以跨级成为二级部门Admin/Viewer；方便协助机构负责人管理二级部门下的仓库/群组/成员以及组织级规则。

### 部门切换

拥有多机构权限的机构负责人/机构管理员可以切换部门，进行不同的部门管理。  

![img](http://devops-minio.jdcloud.com/doc-image/All-Image/department.assets/department-switch.png)

