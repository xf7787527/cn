# describeAccounts


## 描述
查询 Clickhouse account列表信息

## 请求方式
GET

## 请求地址
https://clickhouse.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/accounts

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,∞)。pageNumber为-1时，返回所有数据页码；超过总页数时，显示最后一页;|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为10，取值范围：[10,100]，用于查询列表的接口|
|**filters**|[Filter[]](describeaccounts#filter)|False| |accountStatus, 支持operator选项：eq<br>|

<div id="filter">Filter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeaccounts#result)| |
|**requestId**|String| |

<div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**accounts**|[Account[]](describeaccounts#account)| |
|**totalCount**|Number| |
<div id="account">Account</div>
|名称|类型|描述|
|---|---|---|
|**accountName**|String|账号名|
|**privileges**|String|权限|
|**accountStatus**|String|账号状态|
|**createTime**|Integer|账号创建时间|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
