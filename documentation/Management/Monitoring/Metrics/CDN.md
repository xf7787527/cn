## CDN

获取该产品监控数据的servicecode为cdn，提供的指标信息如下：

metric | 中文名称  | 英文名称 |单位 | 说明
---|--- |--- |--- |---
success_ratio |源站可用性| cdn.origin.success_ratio | % |
res_time|源站延迟|Source Station Delay|ms|
cdn.bw.max | 带宽峰值 | Peak Bandwidth| Mb/s | 
cdn.pv.ratio.4xx |返回码4xx占比|4XX Return Code| % | 
cdn.pv.ratio.5xx |返回码5xx占比|5XX Return Code| % | 
cdn.pv.ratio.hit |命中率 | cdn.pv.ratio.hit | %|
cdn.out.flow|公网网络出流量| Internet Outbound Traffic | MB | 
cdn.pv | 每秒请求数 | QPS | count　|
cdn.bw.max.external | 海外带宽峰值 | Peak Bandwidth| Mb/s | 
cdn.pv.external|海外每秒请求数|cdn.pv.external|counts/s|
cdn.pv.ratio.4xx.external|海外返回码4xx占比|cdn.pv.ratio.4xx.external | % | 
cdn.pv.ratio.5xx.external|海外返回码5xx占比|cdn.pv.ratio.5xx.external | % | 
cdn.pv.ratio.hit.external|海外命中率|cdn.pv.ratio.hit.external  | % | 
cdn.out.flow.external | 海外公网网络出流量 |cdn.out.flow.external | MB |



