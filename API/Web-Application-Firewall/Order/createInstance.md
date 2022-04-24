# createInstance


## 描述
创建waf实例

## 请求方式
POST

## 请求地址
https://waf.jdcloud-api.com/v1/regions/{regionId}/billing:createInstance

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**req**|[OrderReq](createinstance#orderreq)|True| |请求|

### <div id="orderreq">OrderReq</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**region**|String|True| |地域信息, hb_bgp, hn, hd_bgp 企业版支持两个，旗舰版支持3个，多个以 , 分隔|
|**buyType**|Integer|True| |购买类型, 1:创建 2:续费 3:升配|
|**timeSpan**|Integer|True| |购买时长|
|**timeUnit**|String|True| |时间单位，month, year|
|**startTime**|Long|True| |创建时间|
|**wafInstanceId**|String|False| |实例id，除新建必传|
|**packageType**|Integer|True| |套餐类型 1:高级版, 2:企业版 3:旗舰版 4:基础版|
|**extraDomainsNum**|Integer|True| |额外的域名扩展包|
|**nickName**|String|False| |实例名，新建订单时必传，只能包含汉字、英文字母、下划线、破折号、数字，且长度不能超过16|
|**returnURL**|String|True| |下单成功后返回的url, eg:http://abc.com|
|**extraBitsLimit**|Integer|True| |额外的qps扩展包,单位为M 该值为50M的倍数|
|**appCode**|String|False| |云鼎的appCode|
|**serviceCode**|String|False| |云鼎的serviceCode|
|**buyScenario**|String|False| |购物车活动参数|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](createinstance#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**buyId**|String|buyId|
|**wafInstanceId**|String|wafInstanceId|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
