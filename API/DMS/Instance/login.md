# login


## 描述
rds，drds登录实例

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:login

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|
|**instanceId**|String|True| |rds，drds的实例id。|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dbType**|Integer|True| |数据源源类型，CDS("CDS", 1), MYSQL("MYSQL", 2), ORACLE("ORACLE", 3), SQLSERVER("SQLSERVER", 4), CDSMYSQL("CDSMYSQL", 5), CDSORACLE("CDSORACLE", 6), CDSSQLSERVER("CDSSQLSERVER", 7), DATACENTER("DATACENTER", 8), HBASE("Hbase",9),MONGODB("MongoDb",10),ES("ES",11), MYSQL_INS("MYSQL_INS",12), DRDS_INS("DRDS_INS",13)。|
|**addrMode**|Integer|True| |CLASSIC("CLASSIC", 0), RDS("RDS", 1), ECS("ECS", 2), VPC("VPC", 3), 当前只支持rds模式。|
|**dbUser**|String|True| |数据库用户名。|
|**dbPassword**|String|True| |数据库用户密码。|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**error**|[Error](#error)| |

### <div id="Error">Error</div>
|名称|类型|描述|
|---|---|---|
|**code**|Integer|0，成功；-1，失败。|
|**message**|String|错误消息。|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
