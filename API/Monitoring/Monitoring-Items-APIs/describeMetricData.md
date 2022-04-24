# describeMetricData


## 描述
查看某资源单个监控项数据.
metric介绍: <a href="https://docs.jdcloud.com/cn/monitoring/metrics">Metrics</a>
可以使用接口:<a href="https://docs.jdcloud.com/cn/monitoring/metrics">describeMetrics</a>:查询产品线可用的metric列表。
查询起止时间统一向下对齐10s, 举例:开始时间为 08:45:45 会对齐到08:45:40


## 请求方式
GET

## 请求地址
https://monitor.jdcloud-api.com/v2/regions/{regionId}/metrics/{metric}/metricData

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域 Id|
|**metric**|String|True| |监控项英文标识(id)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**aggrType**|String|False| |聚合方式，用于不同时间轴上的聚合。如balance产品同一个resourceId下存在port=80和port=8080等多种维度。可选值参考:sum、avg、min、max|
|**downSampleType**|String|False| |采样方式，用于在时间轴维度上将聚合周期内的数据聚合为一个点。可选值参考：sum(聚合周期内的数据求和)、avg(求平均)、last(最新值)、min(最小值)、max(最大值)|
|**startTime**|String|False| |查询时间范围的开始时间， UTC时间，格式：2016-12-11T00:00:00+0800（注意在url中+要转译为%2B故url中为2016-12-11T00:00:00%2B0800）<br>开始时间不得晚于当前时间,开始时间不得早于 30 天前<br>|
|**endTime**|String|False| |查询时间范围的结束时间, UTC时间，格式：2016-12-11T00:00:00+0800（为空时，将由startTime与timeInterval计算得出）（注意在url中+要转译为%2B故url中为2016-12-11T00:00:00%2B0800）<br>默认为当前时间,结束时间不得晚于当前时间. 如果晚于, 会被默认设成当前时间, 结束时间不得早于 30 天前.<br>|
|**timeInterval**|String|False| |时间间隔：1h，6h，12h，1d，3d，7d，14d，固定时间间隔，timeInterval默认为1h，当前时间往 前1h<br>如果指定了 startTime 和 endTime,可以不用设置. 默认的,三个参数都不设置查询 1h 内数据.<br>timeInterval 默认值 1h<br>endTime 默认值, 当前时间<br>startTime 默认值,  endTime - timeInterval<br>|
|**tags**|[TagFilter[]](describemetricdata#tagfilter)|False| |监控指标数据的维度信息,根据tags来筛选指标数据不同的维度|
|**groupBy**|Boolean|False| |是否对查询的tags分组|
|**rate**|Boolean|False| |是否求速率。仅对累积类型指标有意义, 默认 false|
|**serviceCode**|String|False| |资源的类型，取值vm, lb, ip, database 等,<a href="https://docs.jdcloud.com/cn/monitoring/api/describeservices?content=API&SOP=JDCloud">describeServices</a>：查询己接入云监控的产品线列表|
|**dimension**|String|False| |资源的维度。查询serviceCode下可用的维度请使用describeServices接口|
|**resourceId**|String|True| |资源的uuid|

### <div id="tagfilter">TagFilter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**key**|String|False| |Tag键|
|**values**|String[]|False| |Tag值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describemetricdata#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**metricDatas**|[MetricData[]](describemetricdata#metricdata)| |
### <div id="metricdata">MetricData</div>
|名称|类型|描述|
|---|---|---|
|**data**|[DataPoint[]](describemetricdata#datapoint)| |
|**metric**|[Metric](describemetricdata#metric)| |
|**tags**|[Tag[]](describemetricdata#tag)| |
### <div id="tag">Tag</div>
|名称|类型|描述|
|---|---|---|
|**tagKey**|String| |
|**tagValue**|String| |
### <div id="metric">Metric</div>
|名称|类型|描述|
|---|---|---|
|**aggregator**|String| |
|**calculateUnit**|String| |
|**metric**|String| |
|**metricName**|String| |
|**period**|String| |
### <div id="datapoint">DataPoint</div>
|名称|类型|描述|
|---|---|---|
|**timestamp**|Long|时间戳|
|**value**|Object|值|

## 返回码
|返回码|描述|
|---|---|
|**200**|api DescribeMetricData Response|
