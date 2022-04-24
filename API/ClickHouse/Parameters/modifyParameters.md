# modifyParameters


## 描述
提交并修改实例的配置参数。 参数修改后，需要重启才能生效。

## 请求方式
PUT

## 请求地址
https://clickhouse.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/parameters

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|
|**instanceId**|String|True| |实例ID，唯一标识一个实例|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**parameters**|[Parameters[]](modifyparameters#parameters)|True| |目前支持的参数 keep_alive_timeout、max_connections、max_partition_size_to_drop、max_table_size_to_drop、max_concurrent_queries、uncompressed_cache_size、mark_cache_size、use_uncompressed_cache、max_memory_usage、distributed_ddl_task_timeout、background_pool_size、max_memory_usage_for_all_queries、max_query_size、max_partitions_per_insert_block|

### <div id="parameters">Parameters</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |参数名称|
|**value**|String|True| |参数修改值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求id|


## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
