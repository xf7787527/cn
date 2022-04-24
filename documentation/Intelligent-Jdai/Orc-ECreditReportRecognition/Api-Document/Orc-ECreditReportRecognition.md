# pdf征信报告


## 描述
pdf征信报告

## 请求方式

POST

## 请求地址

```apl
https://aiapi.jdcloud.com/jdai/eCreditReportRecognition
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
| 参数名称          | 参数类型          | 是否必填 | 参数说明         |
| :---------------- | :---------------- | :------- | :--------------- |
| `code`            | int               | Y        | 返回code码0:成功 |
| `msg`             | String            | N        | msg              |
| `serialNo`        | String            | N        | 交互的流水号     |
| eCreditReportInfo | JsonObject | N        | 征信报告识别结果 |
| `+excelBase64` | `String`                     | N        | `表格base64`                 |
| `+textLines`   | JsonArray | N        | `非表格区域的文本行识别结果` |
| `++bbox`    | `List<Float>` | N        | `检测坐标信息` |
| `++content` | String        | N        | `文本内容`     |



**18.4.请求参数示例**

```
{
	"imageItem": {
		"imgType": "COM",
		"imgBase64":"",
		"encryptionType": "NON"
	}
}
```



### 返回样例

```
{
    "code":"",
    "charge":"",
    "msg":"",
    "result":{
        "code":0,
        "msg":"成功",
        "serialNo":"12092873283-2313",
        "eCreditReportInfo":{
            "excelBase64":"表格base64",
            "textLines":[
                {
                    "bbox":[
                        575.2999877929688,
                        1607.3125,
                        614.6920166015625,
                        1628.25
                    ],
                    "content":"第1页"
                },
                {
                    "bbox":[
                        479.4200134277344,
                        43.3125,
                        711.9931030273438,
                        64.25
                    ],
                    "content":"登记编号： 00545956000068402412"
                }
            ]
        },
        "timestamp":1618381882201
    }
}
```

