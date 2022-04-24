# 电子汇票


## 描述
电子汇票

## 请求方式

POST

## 请求地址

```apl
https://aiapi.jdcloud.com/jdai/eETicketRecognition
```



## header请求参数
|名称|类型|是否必需| 示例值              |描述|
|---|---|---|------------------|---|
|**Content-Type**|String|是| application/json |json格式|

## body请求参数
| 名称            | 类型     |是否必需| 示例值                                                            |描述|
|---------------|--------|---|----------------------------------------------------------------|---|
| **serialNo**  | String |否|                                                                |请求流水号, 不传接口自动生成|
| **imageItem** | Object |是| {"imgType": "DL","encryptionType": "NON","imgBase64": "xxxx"}     |图片信息|
| **+imgType**  | enum   |是| DL                                                             |图片的类型 SFF("采集照")，FF("全景采集照")，NIR("双目采集的近红外照片")，DEEP("深度采集的照片")，IDP("身份证正面")，IDN("身份证反面")，MP("网纹照")，AP("动作照")，VL("行驶证")，DL("驾驶证")，BC("银行卡")，BL("营业执照")，LP("车牌")，COM("通用图片|
| **+imgBase64** | String |是| DL                                                             |/9j/4AAQSkZJRgABAQAAAQABAA...     |
| **+filename** | String |否|| 图片的存储名, 指定了则不读base64                                           |
| **+imgUrl**   | String |否|                                                                |图片的Url地址（外网地址可能会有socket连接超时问题，建议传base64）|
| **+imgArr**   | byte[] |否|                                                                |图片的二进制|
| **+encryptionType** | enum   |是| NON                                                            |加密方式 AKS,LICENSE,NON AKS解密方式：com.wangyin.key.server.DeviceCryptoService#decryptEnvelop 版本号1.5.3|
| **extMap**    | map    |否|                                                                |附加信息, 特殊需求处理|



### 返回实体

## 公共返回参数
|名称|类型|示例值|描述|
|---|---|---|---|
|**code**|string|1000|参见下方错误码-系统级错误码|
|**charge**|boolean|false 或 true    |false：不扣费， true：扣费|
|**remainTimes**|long|1305|剩余调用次数；免费api：每天剩余调用次数；收费api：剩余次数；无限制时为-1|
|**remainSeconds**|long|1223456|剩余调用时间（s）；免费api：-1；收费api：剩余调用时间；无限制时为-1|
|**msg**|String|查询成功    |参见下方错误码-系统级错误码|
|**result**|object|{...}    |业务返回参数|


## 业务返回参数
|名称|类型| 是否必填 |描述|
|---|---|---|---|
|**code**|int|Y| 返回code码,0:成功  |
|msg|string| N | msg                |
|**serialNo**|string|N| 交互的流水号 |
|`ticketFrontInfo`|JsonObject|N|电子汇票识别结果|
| `+issueDate`          | JsonObject   | N        | `出票日期`           |
| ++area          | JsonObject | N        | 文本坐标，x，y为起始点坐标，width和height为矩形框的宽和高 |
| +++height          | int | N        | height为矩形框的高 |
| +++width          | int | N        | width为矩形框宽 |
| +++x          | int | N        | y为起始点坐标 |
| +++y          | int | N        | x为起始点坐标 |
| `++text`        | string    | N        | `文本识别结果`                                            |
| +maturityDate         | JsonObject   | N        | `汇票到期日`         |
| ++area          | JsonObject | N        | 文本坐标，x，y为起始点坐标，width和height为矩形框的宽和高 |
| +++height          | int | N        | height为矩形框的高 |
| +++width          | int | N        | width为矩形框宽 |
| +++x          | int | N        | y为起始点坐标 |
| +++y          | int | N        | x为起始点坐标 |
| `++text`        | string    | N        | `文本识别结果`                                            |
| +billNo               | JsonObject   | N        | `票据号码`           |
| ++area          | JsonObject | N        | 文本坐标，x，y为起始点坐标，width和height为矩形框的宽和高 |
| +++height          | int | N        | height为矩形框的高 |
| +++width          | int | N        | width为矩形框宽 |
| +++x          | int | N        | y为起始点坐标 |
| +++y          | int | N        | x为起始点坐标 |
| `++text`        | string    | N        | `文本识别结果`                                            |
| `+billAmt`            | `JsonObject` | N        | `票据金额`           |
| ++area          | JsonObject | N        | 文本坐标，x，y为起始点坐标，width和height为矩形框的宽和高 |
| +++height          | int | N        | height为矩形框的高 |
| +++width          | int | N        | width为矩形框宽 |
| +++x          | int | N        | y为起始点坐标 |
| +++y          | int | N        | x为起始点坐标 |
| `++text`        | string    | N        | `文本识别结果`                                            |
| +drawerAccount        | JsonObject   | N        | `开票人账号`         |
| ++area          | JsonObject | N        | 文本坐标，x，y为起始点坐标，width和height为矩形框的宽和高 |
| +++height          | int | N        | height为矩形框的高 |
| +++width          | int | N        | width为矩形框宽 |
| +++x          | int | N        | y为起始点坐标 |
| +++y          | int | N        | x为起始点坐标 |
| `++text`        | string    | N        | `文本识别结果`                                            |
| +drawerName           | JsonObject   | N        | `开票人全称`         |
| ++area          | JsonObject | N        | 文本坐标，x，y为起始点坐标，width和height为矩形框的宽和高 |
| +++height          | int | N        | height为矩形框的高 |
| +++width          | int | N        | width为矩形框宽 |
| +++x          | int | N        | y为起始点坐标 |
| +++y          | int | N        | x为起始点坐标 |
| `++text`        | string    | N        | `文本识别结果`                                            |
| +drawerBank           | JsonObject   | N        | `开票人开户行号`     |
| ++area          | JsonObject | N        | 文本坐标，x，y为起始点坐标，width和height为矩形框的宽和高 |
| +++height          | int | N        | height为矩形框的高 |
| +++width          | int | N        | width为矩形框宽 |
| +++x          | int | N        | y为起始点坐标 |
| +++y          | int | N        | x为起始点坐标 |
| `++text`        | string    | N        | `文本识别结果`                                            |
| +drawerBankName       | JsonObject   | N        | `开票人开户行`       |
| ++area          | JsonObject | N        | 文本坐标，x，y为起始点坐标，width和height为矩形框的宽和高 |
| +++height          | int | N        | height为矩形框的高 |
| +++width          | int | N        | width为矩形框宽 |
| +++x          | int | N        | y为起始点坐标 |
| +++y          | int | N        | x为起始点坐标 |
| `++text`        | string    | N        | `文本识别结果`                                            |
| +payeeName            | JsonObject   | N        | `收款人全称`         |
| ++area          | JsonObject | N        | 文本坐标，x，y为起始点坐标，width和height为矩形框的宽和高 |
| +++height          | int | N        | height为矩形框的高 |
| +++width          | int | N        | width为矩形框宽 |
| +++x          | int | N        | y为起始点坐标 |
| +++y          | int | N        | x为起始点坐标 |
| `++text`        | string    | N        | `文本识别结果`                                            |
| +payeeAccount         | JsonObject   | N        | `收款人账号`         |
| ++area          | JsonObject | N        | 文本坐标，x，y为起始点坐标，width和height为矩形框的宽和高 |
| +++height          | int | N        | height为矩形框的高 |
| +++width          | int | N        | width为矩形框宽 |
| +++x          | int | N        | y为起始点坐标 |
| +++y          | int | N        | x为起始点坐标 |
| `++text`        | string    | N        | `文本识别结果`                                            |
| +payeeBank            | JsonObject   | N        | `收款人开户行号`     |
| ++area          | JsonObject | N        | 文本坐标，x，y为起始点坐标，width和height为矩形框的宽和高 |
| +++height          | int | N        | height为矩形框的高 |
| +++width          | int | N        | width为矩形框宽 |
| +++x          | int | N        | y为起始点坐标 |
| +++y          | int | N        | x为起始点坐标 |
| `++text`        | string    | N        | `文本识别结果`                                            |
| +payeeBankName        | JsonObject   | N        | `收款人开户银行`     |
| ++area          | JsonObject | N        | 文本坐标，x，y为起始点坐标，width和height为矩形框的宽和高 |
| +++height          | int | N        | height为矩形框的高 |
| +++width          | int | N        | width为矩形框宽 |
| +++x          | int | N        | y为起始点坐标 |
| +++y          | int | N        | x为起始点坐标 |
| `++text`        | string    | N        | `文本识别结果`                                            |
| +accepterAccount      | JsonObject   | N        | `承兑人账号`         |
| ++area          | JsonObject | N        | 文本坐标，x，y为起始点坐标，width和height为矩形框的宽和高 |
| +++height          | int | N        | height为矩形框的高 |
| +++width          | int | N        | width为矩形框宽 |
| +++x          | int | N        | y为起始点坐标 |
| +++y          | int | N        | x为起始点坐标 |
| `++text`        | string    | N        | `文本识别结果`                                            |
| +accepterName         | JsonObject   | N        | `承兑人全称`         |
| ++area          | JsonObject | N        | 文本坐标，x，y为起始点坐标，width和height为矩形框的宽和高 |
| +++height          | int | N        | height为矩形框的高 |
| +++width          | int | N        | width为矩形框宽 |
| +++x          | int | N        | y为起始点坐标 |
| +++y          | int | N        | x为起始点坐标 |
| `++text`        | string    | N        | `文本识别结果`                                            |
| +accepterBank         | JsonObject   | N        | `承兑人开户行行号`   |
| ++area          | JsonObject | N        | 文本坐标，x，y为起始点坐标，width和height为矩形框的宽和高 |
| +++height          | int | N        | height为矩形框的高 |
| +++width          | int | N        | width为矩形框宽 |
| +++x          | int | N        | y为起始点坐标 |
| +++y          | int | N        | x为起始点坐标 |
| `++text`        | string    | N        | `文本识别结果`                                            |
| +accepterBankName     | JsonObject   | N        | `承兑行开户行名称`   |
| ++area          | JsonObject | N        | 文本坐标，x，y为起始点坐标，width和height为矩形框的宽和高 |
| +++height          | int | N        | height为矩形框的高 |
| +++width          | int | N        | width为矩形框宽 |
| +++x          | int | N        | y为起始点坐标 |
| +++y          | int | N        | x为起始点坐标 |
| `++text`        | string    | N        | `文本识别结果`                                            |
| +accepterDrawerCommit | JsonObject   | N        | `承兑信息出票人承诺` |
| ++area          | JsonObject | N        | 文本坐标，x，y为起始点坐标，width和height为矩形框的宽和高 |
| +++height          | int | N        | height为矩形框的高 |
| +++width          | int | N        | width为矩形框宽 |
| +++x          | int | N        | y为起始点坐标 |
| +++y          | int | N        | x为起始点坐标 |
| `++text`        | string    | N        | `文本识别结果`                                            |
| +accepterCommit       | JsonObject   | N        | `承兑信息承兑人承诺` |
| ++area          | JsonObject | N        | 文本坐标，x，y为起始点坐标，width和height为矩形框的宽和高 |
| +++height          | int | N        | height为矩形框的高 |
| +++width          | int | N        | width为矩形框宽 |
| +++x          | int | N        | y为起始点坐标 |
| +++y          | int | N        | x为起始点坐标 |
| `++text`        | string    | N        | `文本识别结果`                                            |
| +businessContract     | JsonObject   | N        | `交易合同号`         |
| ++area          | JsonObject | N        | 文本坐标，x，y为起始点坐标，width和height为矩形框的宽和高 |
| +++height          | int | N        | height为矩形框的高 |
| +++width          | int | N        | width为矩形框宽 |
| +++x          | int | N        | y为起始点坐标 |
| +++y          | int | N        | x为起始点坐标 |
| `++text`        | string    | N        | `文本识别结果`                                            |
| +allow                | JsonObject   | N        | `能否转让`           |
| ++area          | JsonObject | N        | 文本坐标，x，y为起始点坐标，width和height为矩形框的宽和高 |
| +++height          | int | N        | height为矩形框的高 |
| +++width          | int | N        | width为矩形框宽 |
| +++x          | int | N        | y为起始点坐标 |
| +++y          | int | N        | x为起始点坐标 |
| `++text`        | string    | N        | `文本识别结果`                                            |
| +extended             | JsonObject   | N        | `扩展参数`           |
| ++area          | JsonObject | N        | 文本坐标，x，y为起始点坐标，width和height为矩形框的宽和高 |
| +++height          | int | N        | height为矩形框的高 |
| +++width          | int | N        | width为矩形框宽 |
| +++x          | int | N        | y为起始点坐标 |
| +++y          | int | N        | x为起始点坐标 |
| `++text`        | string    | N        | `文本识别结果`                                            |

## 请求参数示例

```json
{
    "appName": "FACE_xxx",
    "appAuthorityKey": "sADxxx==",
    "businessId": "FACE-xxxxxx",
    "imageItem": {
        "imgType": "COM",
        "imgBase64":"",
        "encryptionType": "NON"
    },
    "imageType": "jpg"
}
```

## 返回样例

```json
{
    "code":"",
    "charge":"",
    "msg":"",
    "result":{
        "code":0,
        "msg":"成功",
        "serialNo":"12092873283-2313",
        "ticketFrontInfo":{
            "accepterBank":{
                "area":{
                    "height":15,
                    "width":87,
                    "x":471,
                    "y":291
                },
                "text":"402473701210"
            },
            "accepterBankName":{
                "area":{
                    "height":20,
                    "width":175,
                    "x":471,
                    "y":313
                },
                "text":"山东沂水农村商业银行营业部"
            },
            "billAmt":{
                "area":{
                    "height":24,
                    "width":59,
                    "x":155,
                    "y":255
                },
                "text":"10000.0"
            },
            "billNo":{
                "area":{
                    "height":19,
                    "width":271,
                    "x":467,
                    "y":134
                },
                "text":"1403337000102014122"
            },
            "drawerBankName":{
                "area":{
                    "height":20,
                    "width":175,
                    "x":115,
                    "y":205
                },
                "text":"山东沂水农村商业银行营业部"
            },
            "drawerName":{
                "area":{
                    "height":20,
                    "width":223,
                    "x":55,
                    "y":156
                },
                "text":"浙程代农业开发有限公司"
            },
            "extended":{

            },
            "issueDate":{
                "area":{
                    "height":19,
                    "width":183,
                    "x":15,
                    "y":111
                },
                "text":"2014-12-25"
            },
            "payeeBankName":{
                "area":{
                    "height":19,
                    "width":175,
                    "x":471,
                    "y":205
                },
                "text":"中国建设银行罗庄区支行"
            },
            "payeeName":{
                "area":{
                    "height":19,
                    "width":199,
                    "x":407,
                    "y":157
                },
                "text":"临沂贸易有限公司"
            }
        },
        "timestamp":1618381882201
    }
}
```


