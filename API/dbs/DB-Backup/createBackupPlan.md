# createBackupPlan


## 描述
创建备份计划

## 请求方式
POST

## 请求地址
https://dbs.jdcloud-api.com/v2/regions/{regionId}/backupPlans

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》]|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |备份计划名称，支持中文、数字、大小写字母、英文下划线“_”、减号“-”，且不少于2字符不超过64字符|
|**servicePackage**|String|True| |DBS服务包类型是枚举值， dbs.common.package 表示基础服务包，不含备份流量|
|**chargeSpec**|[ChargeSpec](createbackupplan#chargespec)|True| |购买规格|

### <div id="chargespec">ChargeSpec</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**chargeMode**|String|False|postpaid_by_duration|计费模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration.请参阅具体产品线帮助文档确认该产品线支持的计费类型|
|**chargeUnit**|String|False| |预付费计费单位，预付费必填，当chargeMode为prepaid_by_duration时有效，取值为：month、year，默认为month|
|**chargeDuration**|Integer|False| |预付费计费时长，预付费必填，当chargeMode取值为prepaid_by_duration时有效。当chargeUnit为month时取值为：1~9，当chargeUnit为year时取值为：1、2、3|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](createbackupplan#result)| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**buyId**|String| |
|**orderNubmer**|String| |
|**backupPlanId**|String| |

## 返回码
|返回码|描述|
|---|---|
|**201**|OK|
|**400**|创建备份计划失败|
|**500**|创建备份计划失败|
