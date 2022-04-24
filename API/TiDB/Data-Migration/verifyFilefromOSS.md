# verifyFilefromOSS


## 描述
校验需要导入的备份文件在OSS上是否存在，需要的读取权限是否具备

## 请求方式
POST

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/migration:verifyFilefromOSS

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ossLink**|String|True| |要校验的文件bucket及路径,例如Bucket为db_bak,文件路径为test_server/db1/20181013.bak,则ossLink为db_bak/test_server/db1/20181013.bak|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](verifyfilefromoss#result)| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**success**|String|true：成功false:失败,文件不存在，类型不对或需要的权限不正确|
|**errMsg**|String|具体的错误信息|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
