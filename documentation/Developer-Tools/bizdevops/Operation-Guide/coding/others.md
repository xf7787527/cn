## 与行云的任务关联实例展示

1. 在行云上找到空间内相应的任务ID（卡片编号）；如下图：
   ![img](http://devops-minio.jdcloud.com/doc-image/All-Image/others.assets/jagile.jpg)

2. 提交代码时，关联该任务ID，形式如下：
   <类型>`[可选的作用域]`: **空格** `<描述>` **空格** `#行云卡片编号`

    * **关键字**：feat，fit或docs、refactor、test、style、improvement 其中feat表示新增了一个功能 ，fit表示修复了一个 bug，其他关键字可参考具体文档。
    * **可选的作用域**：例如搜索模块 bundle-search
    * **描述**：描述原则上要描述清楚本次新增或修改的点，这块可以自行发挥
    * **行云卡片编号**：为行云卡片中以C开头的id；
    值得注意的是，行云卡片编号前必须加 `空格` 和 `#号`！！！~  如：#C2019101459157，且将“#卡号”填在message第一行的末尾即可。
    * **提交方式**：根据自己的使用习惯，可命令行提交，或着可视化工具（比如：ide）
      代码提交方式如下：

    ```
    git commit -m " feat(bundle-search): V8.3.4[产品需求] 字号大小调整--搜索;reviewer:mengfanlei #C2019101459157"
   
    ```


3.在行云中任务卡片的详情信息中，查看**代码提交记录**；如下图：
![img](http://devops-minio.jdcloud.com/doc-image/All-Image/others.assets/jagile1.jpg)

## 权限矩阵 

<p>主要展示角色权限和访问级别的权限，以方便研发同学查阅


  <p>
  <strong style="font-size: 20.0px;letter-spacing: -0.008em;">Coding库内角色操作权限</strong>
</p>
  <p>库角色操作权限高于群组角色，该表仅仅表示群组成员未单独在库中增加其他权限的说明</p>
  <table class="wrapped">
    <colgroup> <col/> <col/> <col/> <col/> <col/> <col/> </colgroup>
    <thead>
      <tr>
        <th style="text-align: center;">功能</th>
        <th style="text-align: center;">Guest</th>
        <th style="text-align: center;">Developer</th>
        <th style="text-align: center;">Master</th>
        <th style="text-align: center;">群组Owner</th>
        <th colspan="1">库Owner</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td colspan="1">浏览代码</td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
      </tr>
      <tr>
        <td>克隆或拉取代码（Clone、Pull）</td>
        <td style="text-align: center;">
          <span>✅</span>
        </td>
        <td style="text-align: center;">
          <span>✅</span>
        </td>
        <td style="text-align: center;">
          <span>✅</span>
        </td>
        <td style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
      </tr>
      <tr>
        <td>下载代码</td>
        <td style="text-align: center;">
          <span>✅</span>
        </td>
        <td style="text-align: center;">
          <span>✅</span>
        </td>
        <td style="text-align: center;">
          <span>✅</span>
        </td>
        <td style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
      </tr>
      <tr>
        <td colspan="1">提交历史</td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
      </tr>
      <tr>
        <td colspan="1">分支列表</td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
      </tr>
      <tr>
        <td colspan="1">标签</td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
      </tr>
      <tr>
        <td colspan="1">成员列表</td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
      </tr>
      <tr>
        <td colspan="1">评审列表</td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
      </tr>
      <tr>
        <td colspan="1">发起评审</td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
      </tr>
      <tr>
        <td colspan="1">提交代码（Push）</td>
        <td colspan="1" style="text-align: center;">
          <br/>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
      </tr>
      <tr>
        <td colspan="1">通用设置</td>
        <td colspan="1" style="text-align: center;">
          <br/>
        </td>
        <td colspan="1" style="text-align: center;">
          <br/>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
      </tr>
      <tr>
        <td colspan="1">仓库成员</td>
        <td colspan="1" style="text-align: center;">
          <br/>
        </td>
        <td colspan="1" style="text-align: center;">
          <br/>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
      </tr>
      <tr>
        <td colspan="1">评审规则</td>
        <td colspan="1" style="text-align: center;">
          <br/>
        </td>
        <td colspan="1" style="text-align: center;">
          <br/>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
      </tr>
      <tr>
        <td colspan="1">安全策略</td>
        <td colspan="1" style="text-align: center;">
          <br/>
        </td>
        <td colspan="1" style="text-align: center;">
          <br/>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
      </tr>
      <tr>
        <td colspan="1">集成服务</td>
        <td colspan="1" style="text-align: center;">
          <br/>
        </td>
        <td colspan="1" style="text-align: center;">
          <br/>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
      </tr>
      <tr>
        <td>高级设置-存储库GC</td>
        <td style="text-align: center;">
          <br/>
        </td>
        <td style="text-align: center;">
          <br/>
        </td>
        <td style="text-align: center;">
          <span>✅</span>
        </td>
        <td style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
      </tr>
      <tr>
        <td colspan="1">
          <span>高级设置-更改默认分支</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <br/>
        </td>
        <td colspan="1" style="text-align: center;">
          <br/>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
      </tr>
      <tr>
        <td colspan="1">高级设置-转移仓库</td>
        <td colspan="1" style="text-align: center;">
          <br/>
        </td>
        <td colspan="1" style="text-align: center;">
          <br/>
        </td>
        <td colspan="1" style="text-align: center;">
          <br/>
        </td>
        <td colspan="1" style="text-align: center;">
          <br/>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
      </tr>
      <tr>
        <td colspan="1">高级设置-删除仓库</td>
        <td colspan="1" style="text-align: center;">
          <br/>
        </td>
        <td colspan="1" style="text-align: center;">
          <br/>
        </td>
        <td colspan="1" style="text-align: center;">
          <br/>
        </td>
        <td colspan="1" style="text-align: center;">
          <br/>
        </td>
        <td colspan="1" style="text-align: center;">
          <span>✅</span>
        </td>
      </tr>
    </tbody>
  </table>
<p>
  <strong style="font-size: 20.0px;letter-spacing: -0.008em;">Coding库外人员访问权限</strong>
</p>
<table class="wrapped">
  <colgroup>
    <col/>
    <col/>
    <col/>
    <col/>
  </colgroup>
  <thead><tr>
      <th style="text-align: left;">功能</th>
      <th style="text-align: left;">私有</th>
      <th style="text-align: left;">默认</th>
      <th style="text-align: left;">公开</th>
    </tr></thead>
  <tbody style="font-size: 13px;">  
    <tr style="text-align: left;">
      <td colspan="1" style="text-align: left;">浏览代码</td>
      <td colspan="1" style="text-align: center;">
        <br/>
      </td>
      <td colspan="1" style="text-align: center;">✅</td>
      <td colspan="1" style="text-align: center;">✅</td>
    </tr>
    <tr style="text-align: left;">
      <td style="text-align: left;">克隆或拉取代码（Clone、Pull）</td>
      <td style="text-align: center;">
        <br/>
      </td>
      <td style="text-align: center;">
        <br/>
      </td>
      <td style="text-align: center;">
        <span>✅</span>
      </td>
    </tr>
    <tr style="text-align: left;">
      <td style="text-align: left;">下载代码</td>
      <td style="text-align: center;">
        <br/>
      </td>
      <td style="text-align: center;">
        <br/>
      </td>
      <td style="text-align: center;">
        <span>✅</span>
      </td>
    </tr>
    <tr style="text-align: left;">
      <td colspan="1">fork代码</td>
      <td colspan="1">
        <br/>
      </td>
      <td colspan="1" style="text-align: center;">✅</td>
      <td colspan="1" style="text-align: center;">✅</td>
    </tr>
    <tr style="text-align: left;">
      <td colspan="1" style="text-align: left;">提交历史</td>
      <td colspan="1" style="text-align: center;">
        <br/>
      </td>
      <td colspan="1" style="text-align: center;">✅</td>
      <td colspan="1" style="text-align: center;">
        <span>✅</span>
      </td>
    </tr>
    <tr style="text-align: left;">
      <td colspan="1" style="text-align: left;">分支列表</td>
      <td colspan="1" style="text-align: center;">
        <br/>
      </td>
      <td colspan="1" style="text-align: center;">✅</td>
      <td colspan="1" style="text-align: center;">
        <span>✅</span>
      </td>
    </tr>
    <tr style="text-align: left;">
      <td colspan="1" style="text-align: left;">标签</td>
      <td colspan="1" style="text-align: center;">
        <br/>
      </td>
      <td colspan="1" style="text-align: center;">✅</td>
      <td colspan="1" style="text-align: center;">
        <span>✅</span>
      </td>
    </tr>
    <tr style="text-align: left;">
      <td colspan="1" style="text-align: left;">成员列表</td>
      <td colspan="1" style="text-align: center;">
        <br/>
      </td>
      <td colspan="1" style="text-align: center;">✅</td>
      <td colspan="1" style="text-align: center;">
        <span>✅</span>
      </td>
    </tr>
    <tr style="text-align: left;">
      <td colspan="1" style="text-align: left;">评审列表</td>
      <td colspan="1" style="text-align: center;">
        <br/>
      </td>
      <td colspan="1" style="text-align: center;">✅</td>
      <td colspan="1" style="text-align: center;">
        <span>✅</span>
      </td>
    </tr>
    <tr style="text-align: left;">
      <td colspan="1" style="text-align: left;">发起评审</td>
      <td colspan="1" style="text-align: center;">
        <br/>
      </td>
      <td colspan="1" style="text-align: center;">
        <br/>
      </td>
      <td colspan="1" style="text-align: center;">
        <span>✅</span>
      </td>
    </tr>
    <tr style="text-align: left;">
      <td colspan="1" style="text-align: left;">提交代码（Push）</td>
      <td colspan="1" style="text-align: center;">
        <br/>
      </td>
      <td colspan="1" style="text-align: center;">✅</td>
      <td colspan="1" style="text-align: center;">✅</td>
    </tr>
    <tr style="text-align: left;">
      <td colspan="1" style="text-align: left;">通用设置</td>
      <td colspan="1" style="text-align: center;">
        <br/>
      </td>
      <td colspan="1" style="text-align: center;">
        <br/>
      </td>
      <td colspan="1" style="text-align: center;">
        <span>✅</span>
      </td>
    </tr>
    <tr style="text-align: left;">
      <td colspan="1" style="text-align: left;">仓库成员</td>
      <td colspan="1" style="text-align: center;">
        <br/>
      </td>
      <td colspan="1" style="text-align: center;">
        <br/>
      </td>
      <td colspan="1" style="text-align: center;">
        <span>✅</span>
      </td>
    </tr>
    <tr style="text-align: left;">
      <td colspan="1" style="text-align: left;">评审规则</td>
      <td colspan="1" style="text-align: center;">
        <br/>
      </td>
      <td colspan="1" style="text-align: center;">
        <br/>
      </td>
      <td colspan="1" style="text-align: center;">
        <span>✅</span>
      </td>
    </tr>
    <tr style="text-align: left;">
      <td colspan="1" style="text-align: left;">安全策略</td>
      <td colspan="1" style="text-align: center;">
        <br/>
      </td>
      <td colspan="1" style="text-align: center;">
        <br/>
      </td>
      <td colspan="1" style="text-align: center;">
        <span>✅</span>
      </td>
    </tr>
    <tr style="text-align: left;">
      <td colspan="1" style="text-align: left;">集成服务</td>
      <td colspan="1" style="text-align: center;">
        <br/>
      </td>
      <td colspan="1" style="text-align: center;">
        <br/>
      </td>
      <td colspan="1" style="text-align: center;">
        <span>✅</span>
      </td>
    </tr>
    <tr style="text-align: left;">
      <td style="text-align: left;">高级设置-存储库GC</td>
      <td style="text-align: center;">
        <br/>
      </td>
      <td style="text-align: center;">
        <br/>
      </td>
      <td style="text-align: center;">
        <span>✅</span>
      </td>
    </tr>
    <tr style="text-align: left;">
      <td colspan="1" style="text-align: left;">
        <span>高级设置-更改默认分支</span>
      </td>
      <td colspan="1" style="text-align: left;">
        <br/>
      </td>
      <td colspan="1" style="text-align: left;">
        <br/>
      </td>
      <td colspan="1" style="text-align: center;">✅</td>
    </tr>
    <tr style="text-align: left;">
      <td colspan="1" style="text-align: left;">高级设置-转移仓库</td>
      <td colspan="1" style="text-align: center;">
        <br/>
      </td>
      <td colspan="1" style="text-align: center;">
        <br/>
      </td>
      <td colspan="1" style="text-align: center;">
        <span></span>
      </td>
    </tr>
    <tr style="text-align: left;">
      <td colspan="1" style="text-align: left;">高级设置-删除仓库</td>
      <td colspan="1" style="text-align: center;">
        <br/>
      </td>
      <td colspan="1" style="text-align: center;">
        <br/>
      </td>
      <td colspan="1" style="text-align: center;">
        <span></span>
      </td>
    </tr>
  </tbody>
</table>
  <p>
  <strong style="font-size: 20.0px;letter-spacing: -0.008em;">群组权限和库权限的关系说明</strong>
</p>
  <p>库的访问权限需要基于群组的访问权限进行选择。</p>
  <table class="wrapped">
    <colgroup>
      <col/>
      <col/>
      <col/>
      <col/>
      <col/>
    </colgroup>
    <tbody>
      <tr>
        <th colspan="2" rowspan="2">
        <br>
        </th>
        <th colspan="3" style="text-align: center;">库访问权限</th>
      </tr>
      <tr>
        <th>Public</th>
        <th colspan="1">Default</th>
        <th>Private</th>
      </tr>
      <tr>
        <th rowspan="3">
          群组<br>
          访问<br>
          权限<br>
        </th>
        <th>Public</th>
        <td style="text-align: center;">✅</td>
        <td colspan="1" style="text-align: center;">✅</td>
        <td style="text-align: center;">✅</td>
      </tr>
      <tr>
        <th>Default</th>
        <td class="highlight-red" data-highlight-colour="red" style="text-align: center;">
          <span title=""></span>
        </td>
        <td colspan="1" style="text-align: center;">✅</td>
        <td style="text-align: center;">✅</td>
      </tr>
      <tr>
        <th>Private</th>
        <td class="highlight-red" data-highlight-colour="red" style="text-align: center;">
          <span title=""></span>
        </td>
        <td class="highlight-red" colspan="1" data-highlight-colour="red" style="text-align: center;">
          <span title=""></span>
        </td>
        <td style="text-align: center;">✅</td>
      </tr>
    </tbody>
  </table>


1. 新建库/编辑库
   获取群组的权限，根据群组的访问权限展示库可选择的访问权限
2. 仓库变更群组
   * 如果仓库的权限等级高于转移后目标群组的权限，则仓库权限不变<br>
     比如：仓库repo A权限为Private，目标群组Team1权限：Default，则 变更群组后，repo A的权限不变，还是Private。
   * 如果仓库的权限低于目标群组的权限，则仓库权限变更为群组的权限<br>
     比如：仓库repo A权限为Default，目标群组Team1权限：Private，则 变更群组后，repo A的权限变更为Private。
3. 群组权限发生变化
   * 如果仓库的权限等级高于群组权限变更后的权限，则仓库权限不变<br>
     比如：仓库repo A权限为Private，群组Team1权限：由Public变更为Default or Private，则 变更群组后，repo A的权限不变，还是Private。
   * 如果仓库的权限低于群组变更的权限，则仓库权限变更为群组的权限<br>
     比如：仓库repo A权限为Default，目标群组Team1权限：由Public or Default变更为Private，则 变更群组后，repo A的权限变更为Private。
   * 群组权限由高到低的变化，仓库权限不受影响
4. 个人仓库的访问权限
   个人空间下的仓库，不能变更负责人，如需变更负责人，需先变更群组，然后变更负责人。
5. 派生库的访问权限
   访问级别不能高于源库（如果源库的级别向上调整了，派生库维持源权限，如果源库级别向下调整了，派生库随之调整），不能更改群组。

