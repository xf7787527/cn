# bindMetrics


## 描述
关联实例自定义监控项，每次都要求全量提交

## 请求方式
POST

## 请求地址
https://smartdba.jdcloud-api.com/v2/regions/{regionId}/bindMetrics

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**metricIds**|String[]|False| |自定义的监控项id数组|
|**panelType**|String|False| |展示类型，取值为： real_time 表示实时监控页面, monitor 表示性能趋势页面 market 表示监控大盘|
|**gid**|String|False| |RDS 实例ID，唯一标识一个RDS实例。如果全部实例生效，可以传all|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|String| |
|**requestId**|String|请求ID|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
