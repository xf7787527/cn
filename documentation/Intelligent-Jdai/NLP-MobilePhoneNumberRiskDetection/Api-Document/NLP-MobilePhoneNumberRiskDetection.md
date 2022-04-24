# 手机号码风险识别

## 一、接口描述

### 1. 功能描述

手机号码风险识别服务基于京东庞大的用户行为生态体系，借助于全链路数据处理、实时和离线风险检测识别能力, 结合机器学习、深度学习和图计算等人工智能算法，全方位感知用户实体风险，实现对风险的精准刻画。通过简单的 API 接入，您即可获取业务中手机号码的画像数据，对其风险进行精确评估，搭建或完善已有的风控体系，补充自身风险情报数据，解决因遭遇黑灰产使用虚假信息进行恶意欺诈、作弊、虚假交易等问题。

### 2. 接口使用

进入京东智联云控制台-账号管理-Access Key管理，创建并获取Access Key。整体流程详见 [调用方法](https://docs.jdcloud.com/cn/common-declaration/api/call-methods) 。

## 二、请求说明

### 1. 接口地址 ：

```
https://aiapi.jdcloud.com/jdai/tel_risk_detection
```

### 2. 请求方式：

```
 post
```

### 3. 请求参数

#### （1）query请求参数

公共请求参数

| 名称      | 类型   | 必填 | 示例值                           | 描述                                           |
| --------- | ------ | ---- | -------------------------------- | ---------------------------------------------- |
| appkey    | String | 是   | 80d2b762ecb86593f9668526920f46c  | 您的appkey，可在买家中心控制台中获取           |
| timestamp | long   | 是   | 1541491668060                    | 请求的时间戳，精确到毫秒，timestamp有效期5分钟 |
| sign      | String | 是   | 2e148773a0337a8f2200ba90d445f083 | 签名，根据规则MD5(sectetkey+timestamp)         |
| tel       | String | 是   | 15933068899                      | 需要查询的电话号码                             |

#### （2）header请求参数

业务请求参数

| 名称         | 类型   | 必填 | 示例值                            | 描述         |
| ------------ | ------ | ---- | --------------------------------- | ------------ |
| Content-Type | String | 是   | application/x-www-form-urlencoded | 标准编码格式 |

#### （3）请求代码示例

https://aiapi.jd.com/jdai/tel_risk_detection?tel=15933068899&appkey=<调用者appkey>&timestamp=时间戳&sign=签名

## 三、返回说明

### 1.返回参数

#### （1）公共返回参数

result参数信息

| 名称      | 类型   | 示例值                               | 描述     |
| --------- | ------ | ------------------------------------ | -------- |
| code      | number | 0                                    | 状态code |
| requestId | string | 98a39e53-84d4-448e-9081-29f64a6cd984 | 请求id   |
| message   | string | success                              | 返回信息 |
| data      | Object | {...}                                | data     |

data字段说明

| 名称          | 类型    | 示例值        | 描述                                                         |
| ------------- | ------- | ------------- | ------------------------------------------------------------ |
| code          | string  | 1000          | 参见下方错误码-系统级错误码                                  |
| charge        | boolean | false 或 true | false：不扣费， true：扣费                                   |
| remainTimes   | long    | 1305          | 剩余调用次数；免费api：每天剩余调用次数；收费api：剩余次数；无限制时为-1 |
| remainSeconds | long    | 1223456       | 剩余调用时间（s）；免费api：-1；收费api：剩余调用时间；无限制时为-1 |
| msg           | string  | 查询成功      | 参见下方错误码-系统级错误码                                  |
| result        | object  | {...}         | 查询结果                                                     |

### （2）业务返回参数

| 名称       | 类型   | 描述                              |
| ---------- | ------ | --------------------------------- |
| **result** | Result | API请求成功或者部分成功时返回数据 |

### Result

| 名称     | 类型         | 描述     |
| -------- | ------------ | -------- |
| **data** | CreditResult | 结果数组 |

### CreditResult

| 名称             | 类型              | 描述                                                         |
| ---------------- | ----------------- | ------------------------------------------------------------ |
| **success**      | Boolean           | 是否成功，没成功会在failMsg附上错误信息                      |
| **failMsg**      | String            | 错误描述信息                                                 |
| **dataId**       | String            | 请求数据的ID                                                 |
| **hitCache**     | String            | 是否命中缓存                                                 |
| **inBWList**     | String            | 是否命中黑白名单，black-在黑名单中 white-在白名单中 none-不在任何名单中 |
| **content**      | String            | 对应请求的内容                                               |
| **resourceType** | String            | 数据类型，phone-电话号码                                     |
| **scoreDetail**  | CreditScoreDetail | 评分数据                                                     |

### CreditScoreDetail

| 名称          | 类型   | 描述                                                         |
| ------------- | ------ | ------------------------------------------------------------ |
| **riskTag**   | String | 风险类型，对应riskCode的中文描述                             |
| **riskCode**  | String | 风险类型编码，201-207手机综合风险，包括201-猫池小号、202-异常注册、203-异常登录、204-营销刷券、205-下单黄牛、206-异常支付、207-恶意售后，401-鉴权出错，501-506IP综合风险，包括501-普通代理、 502-秒拨代理IP、503-真人作弊、504-设备伪装、505-地址伪装、506-黑软IP、998-未知。 |
| **riskClass** | String | 风险分类，包括ip、phone、addr。                              |
| **score**     | String | 风险评分，1-低风险 2-中低风险 3-中风险 4-中高风险 5-高风险 0-未知 |
| **scoreDesc** | String | 对应score的中文描述，1-低风险 2-中低风险 3-中风险 4-中高风险 5-高风险 0-未知 |

### 2.返回示例

```
{
    "code": "10000",
    "charge": true,
    "remain": 47,
    "remainTimes": 47,
    "remainSeconds": -1,
    "msg": "查询成功,扣费",
    "result": {
        "requestId": "bvs3rvpjcd4j2abnfbqmi19ntpncpr0u",
        "result": {
            "data": [
                {
                    "success": true,
                    "failMsg": "",
                    "dataId": "c3d9d468-b742-4b48-9001-e26ef39a2ae9",
                    "content": "15244553214",
                    "resourceType": "phone",
                    "scoreDetail": {
                        "riskTag": "未知",
                        "riskCode": "998",
                        "riskClass": "phone",
                        "score": "2",
                        "scoreDesc": "中低风险"
                    },
                    "hitCache": "miss",
                    "inBWList": "none"
                }
            ]
        }
    }
}
```

## 四、错误码信息

### 1.系统级错误码

[详见返回码](https://aidoc.jd.com/user/returncode.html)

### 2.业务错误码

| 返回码  | 描述        |
| ------- | ----------- |
| **200** | OK          |
| **400** | Bad Request |