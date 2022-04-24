# upgradeEngineVersion


## 描述
升级TiDB引擎版本，例如从4.0.6 升级到4.0.8. 目前支持小版本的升级，可升级到平台支持的最新的小版本

## 请求方式
POST

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:upgradeEngineVersion

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**version**|String|False| |升级后的版本号|
|**timing**|String|False| |版本升级的时间点,时间格式yyyy-mm-dd hh:mm:ss。不传或者传入空表示取消升级|


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**202**|OK|
