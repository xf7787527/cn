# describeClusterDetail


## 描述
获取实例详情

## 请求方式
GET

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/instance/{instanceGid}/describeClusterDetail

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceGid**|String|True| |RDS 实例ID，唯一标识一个RDS实例。|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeclusterdetail#result)| |
|**requestId**|String|请求id|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[ClusterDetail](describeclusterdetail#clusterdetail)| |
### <div id="ClusterDetail">ClusterDetail</div>
|名称|类型|描述|
|---|---|---|
|**instanceGid**|String|全局实例id|
|**connectType**|String|接入类型，目前取值为：rds|
|**databaseType**|String|数据库接入类型，如：MYSQL|
|**createTime**|String|创建时间|
|**instanceId**|String|rds实例id|
|**instanceName**|String|rds实例名称|
|**region**|String|地域代码|
|**instanceType**|String|实例类型，如：cluster，standalone|
|**engine**|String|数据库引擎 MySQL|
|**engineVersion**|String|实例版本信息 5.7|
|**instanceClass**|String|实例规格|
|**instanceStatus**|String|实例运行状态|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
