# 通用图片审核

## 一、接口描述

### 1. 功能描述

准确识别图片中的涉黄、涉政、暴恐、违禁、广告等场景敏感内容，辅助人工高效精准定位问题图片，降低运营审核人力成本。

### 2. 接口数据要求：

> 1. 图片格式：jpg/jpeg、png
> 2. 图片大小：<= 5M

### 3. 接口使用：

进入京东智联云控制台-账号管理-Access Key管理，创建并获取Access Key。整体流程详见 [调用方法](https://docs.jdcloud.com/cn/common-declaration/api/call-methods) 。

## 二、请求说明

### 1. 接口地址 ：

```
https://aiapi.jdcloud.com/jdai/censor_image
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

#### （2）header请求参数

业务请求参数

| 名称         | 类型   | 必填 | 示例值           | 描述       |
| ------------ | ------ | ---- | ---------------- | ---------- |
| Content-Type | String | 是   | application/json | 请求头格式 |

#### （3）body请求参数

#### 业务请求参数

| 名称   | 类型   | 必填 | 示例值                        | 描述                                   |
| ------ | ------ | ---- | ----------------------------- | -------------------------------------- |
| url    | String | 是   | 'http://a.com/b.jpg'          | 图片url公网地址                        |
| scenes | Array  | 是   | ['porn', 'terror', 'text'...] | 选择需要审核的算法场景，至少选择一个。 |

#### scenes入参说明

| 字段         | 说明     |
| ------------ | -------- |
| porn         | 鉴黄     |
| terror       | 暴恐     |
| politics     | 涉政人物 |
| prohibitions | 违禁品   |
| ads          | 广告     |
| text         | 文本审核 |

### 4、请求代码示例

建议您使用我们提供的SDK进行调用，SDK获取及调用方式详见本页一接口描述中的3接口使用

## 三、返回说明

### 1、返回参数

#### （1）公共返回参数

| 名称          | 类型    | 示例值        | 描述                                                         |
| ------------- | ------- | ------------- | ------------------------------------------------------------ |
| code          | string  | 1000          | 参见下方错误码-系统级错误码                                  |
| charge        | boolean | false 或 true | false：不扣费， true：扣费                                   |
| remainTimes   | long    | 1305          | 剩余调用次数；免费api：每天剩余调用次数；收费api：剩余次数；无限制时为-1 |
| remainSeconds | long    | 1223456       | 剩余调用时间（s）；免费api：-1；收费api：剩余调用时间；无限制时为-1 |
| msg           | string  | 查询成功      | 参见下方错误码-系统级错误码                                  |
| result        | object  | {...}         | 查询结果                                                     |

#### （2）业务返回参数

result参数信息

| 字段           | 类型   | 说明                                                         |
| -------------- | ------ | ------------------------------------------------------------ |
| status         | Int    | 审核任务状态和进度 0: 审核成功，非0为失败                    |
| requestId      | String | 请求id                                                       |
| message        | String | 对状态码的信息描述                                           |
| label          | Int    | 审核综合结果；0：无违规；1：疑似违规，需要人工复核； 2： 确定违规。 status=0时存在。 |
| data           | JSON   | 各个审核算法能力维度结果。status=0时存在。                   |
| + porn         | JSON   | 鉴黄的审核结果                                               |
| + politics     | JSON   | 敏感人物的审核结果                                           |
| + terror       | JSON   | 暴恐的审核结果                                               |
| + prohibitions | JSON   | 违禁品的审核结果                                             |
| + ads          | JSON   | 广告的审核结果                                               |
| + text         | JSON   | OCR文本的审核结果                                            |

##### 1.鉴黄结果

###### "porn" 下数据结构：

| 字段        | 必须 | 类型  | 示例值 | 说明                                                         |
| ----------- | ---- | ----- | ------ | ------------------------------------------------------------ |
| label       | 是   | Int   | 0      | 审核综合结果；0：无违规；1：疑似违规，需要人工复核； 2： 确定违规； |
| pornScore   | 是   | Float | 0.23   | 图片涉黄置信度评分，同score置信度评分。                      |
| vulgarScore | 是   | Float | 0.22   | 图片低俗置信度评分，同score置信度评分。                      |
| sexyScore   | 是   | Float | 0.34   | 图片性感置信度评分，同score置信度评分。                      |

##### 2.政治敏感人物结果

###### "politics" 下数据结构：

| 字段        | 必须 | 类型   | 示例值         | 说明                                                         |
| ----------- | ---- | ------ | -------------- | ------------------------------------------------------------ |
| label       | 是   | Int    | 0              | 政治人物审核结果；0：无违规；1：疑似违规，需要人工复核； 2： 确定违规； |
| politicians | 是   | Array  | []             | 审核出来的政治人物数组                                       |
| + name      | 是   | String | 普京           | 政治人物姓名                                                 |
| + score     | 是   | Float  | 0.7            | 评分                                                         |
| + location  | 是   | Array  | [98,123,13,45] | 政治人物在图片中的位置[x,y,width,height]                     |

##### 3.暴恐结果

###### "terror" 下数据结构：

| 字段       | 必须 | 类型   | 示例值         | 说明                                                         |
| ---------- | ---- | ------ | -------------- | ------------------------------------------------------------ |
| label      | 是   | Int    | 0              | 暴恐分类状态；0：无违规；1：疑似违规，需要人工复核； 2： 确定违规； |
| flags      | 是   | Array  |                | 旗帜的数组                                                   |
| + name     | 是   | String | 纳粹标志       | 旗帜名称                                                     |
| + score    | 是   | Float  | 0.7            | 评分                                                         |
| + location | 是   | Array  | []             | 旗帜位置信息                                                 |
| bloodiness | 是   | Float  | 0.34           | 血腥场景置信度评分                                           |
| flame      | 是   | Float  | 0.1            | 爆炸场景置信度评分                                           |
| riot       | 是   | Float  | 0.23           | 暴乱场景置信度评分                                           |
| terrorists | 是   | Array  | []             | 暴恐人物数组                                                 |
| + name     | 是   | String | 普京           | 政治人物姓名                                                 |
| + score    | 是   | Float  | 0.7            | 评分                                                         |
| + location | 是   | Array  | [98,123,13,45] | 政治人物在图片中的位置[x,y,width,height]                     |

###### 4.违禁品结果

###### "prohibitions" 下数据结构：

| 字段        | 必须 | 类型  | 示例值 | 说明                                                         |
| ----------- | ---- | ----- | ------ | ------------------------------------------------------------ |
| label       | 是   | Int   | 0      | 违禁品检测状态：0：无违规；1：疑似违规，需要人工复核； 2： 确定违规； |
| gunScore    | 是   | Float | 0.2    | 枪支置信度评分，同score置信度评分。                          |
| cutterScore | 是   | Float | 0.7    | 管制刀具置信度评分，同score置信度评分。                      |

##### 5.广告结果

###### "ads" 下数据结构：

| 字段           | 必须 | 类型   | 示例值                | 说明                                                         |
| -------------- | ---- | ------ | --------------------- | ------------------------------------------------------------ |
| label          | 是   | Int    | 0                     | 违禁品检测状态：0：无违规；1：疑似违规，需要人工复核； 2： 确定违规； |
| logo           | 是   | Array  |                       | 通用品牌logo                                                 |
| +score         | 是   | Float  | 0.34                  | logo检测结果置信度评分                                       |
| +logoName      | 是   | Float  | 1229                  | logo代号                                                     |
| +location      | 是   | Float  | [83, 193, 49, 12]     | logo在图片中的位置[x,y,width,height]                         |
| qrcode         | 是   | Array  |                       | 二维码                                                       |
| +score         | 是   | Float  | 0.75                  | 二维码检测结果置信度评分                                     |
| +location      | 是   | Array  | [29, 193, 99, 45]     | 二维码在图片中的位置[x,y,width,height]                       |
| barcode        | 是   | Array  |                       | 条形码                                                       |
| +score         | 是   | Float  | 0.75                  | 条形码检测结果置信度评分                                     |
| +location      | 是   | Array  | [29, 193, 99, 45]     | 条形码在图片中的位置[x,y,width,height]                       |
| contacts       | 是   | Object |                       | 图片中文本存在的联系方式，注意：该结果无置信度评分           |
| +mobileNumbers | 是   | Array  | ["15754322876"]       | 手机号码                                                     |
| +phoneNumbers  | 是   | Array  | ["010-465371831"]     | 电话号码                                                     |
| +emails        | 是   | Array  | ["8736510345@qq.com”] | 邮箱地址                                                     |
| +urls          | 是   | Array  | ["www.taobao.com"]    | 网站                                                         |
| +sns           | 是   | Array  | ["8736510345"]        | 社交网络联系方式，如微信、qq、微博                           |

##### 6.文本审核结果

###### "text" 下数据结构：

| 字段     | 必须 | 类型   | 示例值               | 说明                                                         |
| -------- | ---- | ------ | -------------------- | ------------------------------------------------------------ |
| label    | 是   | Int    |                      | 文本审核综合结果；0：无违规；1：疑似违规，需要人工复核； 2： 确定违规。 |
| porn     | 是   | Object |                      | 文本鉴黄结果                                                 |
| +label   | 是   | Int    | 0                    | 文本鉴黄检测状态：0：无违规；1：疑似违规，需要人工复核； 2： 确定违规； |
| +score   | 是   | Float  | 0.3                  | 文本涉黄置信度评分                                           |
| +words   | 是   | Array  | ["三级片"，"大保健"] | 命中文本中的涉黄文本审核，可能为空                           |
| politics | 是   | Object |                      | 文本涉政结果                                                 |
| +label   | 是   | Int    | 0                    | 文本涉政检测状态：0：无违规；1：疑似违规，需要人工复核； 2： 确定违规； |
| +score   | 是   | Float  | 0.41                 | 文本涉政置信度评分                                           |
| +words   | 是   | Array  | ["天安门"，"白宫"]   | 命中文本中的涉政文本审核，可能为空                           |
| terror   | 是   | Object |                      | 文本涉恐结果                                                 |
| +label   | 是   | Int    | 0                    | 文本涉恐检测状态：0：无违规；1：疑似违规，需要人工复核； 2： 确定违规； |
| +score   | 是   | Float  | 0.24                 | 文本涉恐置信度评分                                           |
| +words   | 是   | Array  | ["911事件"]          | 命中文本中的涉恐文本审核，可能为空                           |

#### 置信度评分说明

**0.9 <= score <= 1.0** : 确认违规，可以自动驳回。

**0.5 <= score < 0.9** : 疑似违规，需要人工复审。

**0<= score < 0.5** : 无违规。

### 2、返回示例

```json
{
    "requestId": "c5721b2b7cdb488fafb1e065c4c40619",
    "status": 0,
    "message": "success",
    "data": {
        "porn": {
            "pornScore": 0.1236,
            "vulgarScore": 0.2684,
            "sexyScore": 0.4781,
            "label": 0
        },
        "politics": {
            "label": 1,
            "politicians": [{
                "name": "xxx",
                "score": 0.56,
                "location": [83, 193, 49, 12]
            }]
        },
        "terror": {
            "label": 2,
            "flags": [{
                "score": 0.73,
                "name": "纳粹标志",
                "location": [100, 350, 100, 40]
            }],
            "bloodiness": 0.34,
            "riot": 0.18,
            "flame": 0.28,
            "terrorists": [{
                "name": "xxx",
                "score": 0.56,
                "location": [83, 193, 49, 12]
            }]

        },
        "prohibitions": {
            "label": 1,
            "cutterScore": 0.66,
            "gunScore": 0.39
        },
        "ads": {
            "label": 2,
            "logo": [{
                "score": 0.54,
                "logoName": "29313",
                "location": [23, 391, 451, 31]
            }],
            "qrcode": [{
                "score": 1.0,
                "location": [0, 0, 0, 0]
            }],
            "barcode": [],
            "contacts": {
                "mobileNumbers": ["123098", "2309870"],
                "phoneNumbers": ["010-2398729'", "078-23982098"],
                "emails": ["abc@gmail.com"],
                "urls": ["https://baidu.com"],
                "sns": ["121"]
            }
        }
    },
    "text": {
        "label": 1,
        "porn": {
            "label": 1,
            "words": ["三级片", "大保健"],
            "score": 0.7883
        },
        "politics": {
            "label": 1,
            "words": ["特朗普", "天安门"],
            "score": 0.534
        },
        "terror": {
            "label": 1,
            "words": ["拉登", "911事件"],
            "score": 0.853
        }
    }
}
```

## 四、错误码

### 1.系统级错误码

[详见返回码](https://aidoc.jd.com/user/returncode.html)

### 2.业务错误码

#### status状态码

| 错误号 | 错误信息                              | 说明                   |
| ------ | ------------------------------------- | ---------------------- |
| 0      | success                               | 成功                   |
| 101    | Request body should be in json format | 请求body必须是json格式 |
| 102    | Parameters are missing                | 参数缺失               |
| 103    | Value of parameters are empty         | 参数值为空             |
| 104    | File format error                     | 不支持的图片格式       |
| 105    | Download error                        | 下载失败               |
| 106    | Parameter value error                 | 参数值错误             |
| 107    | File size error                       | 文件大小错误           |
| 500    | Internal error                        | 内部错误               |