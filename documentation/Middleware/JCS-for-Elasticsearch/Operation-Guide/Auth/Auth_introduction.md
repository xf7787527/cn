# 用户鉴权

当您需要设置集群、索引的访问权限时，可以通过京东云Elasticsearch的用户鉴权机制，为自定义角色分配权限，并将角色分配给用户，实现权限管控。京东云Elasticsearch提供了多种内置角色，您可以在内置角色的基础上扩展自定义角色，以满足特定需求。

- [开启用户鉴权](../Auth/Auth_on.md)
- [角色管理](../Auth/Role_manage.md)
- [用户管理](../Auth/User_manage.md)
- [关闭用户鉴权](../Auth/Auth_off.md)

## 集群权限
定义集群的操作权限，例如查看集群健康度和Settings、创建快照等。
| 索引权限  | 说明  |
| :------------ | :------------ |
| MANAGE | 修改集群配置信息，添加快照，执行reroute等操作的权限，例如可以通过/_cluster/settings接口修改集群配置。 |
| MONITOR | 查看集群配置信息，查看集群监控数据等操作的权限，例如可以通过/_cluster/settings接口查看集群配置。 |

## 索引权限
定义索引的操作权限，例如只读查看所有索引的所有字段（索引名设置为*后，授予read索引），索引名支持通配符（*）及正则表达式。详细信息，请参见Indices privileges。
| 索引权限  | 说明  |
| :------------ | :------------ |
| ALL | 操作索引的全部权限，例如CRUD document，CRUD index等操作的权限。 |
| MONITOR | 查看索引配置信息，查看索引监控数据等操作的权限，例如可以通过/_stats接口查看索引监控信息。  |
| MANAGE | 修改索引副本等配置信息的操作权限，例如通过/indexName/_settings接口修改索引配置。 |
| CREATE_INDEX | 创建索引的权限。 |
| DELETE_INDEX | 删除索引的权限。 |
| WRITE | 写document的权限，修改mapping的权限。 |
| READ | 读document的权限。 |
| DELETE | 删除document的权限。 |
