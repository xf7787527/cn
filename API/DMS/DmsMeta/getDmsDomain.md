# getDmsDomain


## 描述
获取Dms域名

## 请求方式
GET

## 请求地址
https://dms.jdcloud-api.com/v1/regions/{regionId}/getDmsDomain

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**domains**|Object|区域到域名映射，例{"cn-north-1":"http://10.222.49.154:8080", "cn-east-1":"http://10.222.49.154:8080"}。|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
