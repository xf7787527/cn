# 拍照翻译


## 描述
拍照翻译

## 请求方式

POST

## 请求地址

```apl
https://aiapi.jdcloud.com/jdai/translationRecognition
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
| `srcLang`         | String   | Y        | 源语言种类 Afrikaans (af), Amharic (am), Arabic (ar), Asturian (ast), Azerbaijani (az), Bashkir (ba), Belarusian (be), Bulgarian (bg), Bengali (bn), Breton (br), Bosnian (bs), Catalan; Valencian (ca), Cebuano (ceb), Czech (cs), Welsh (cy), Danish (da), German (de), Greeek (el), English (en), Spanish (es), Estonian (et), Persian (fa), Fulah (ff), Finnish (fi), French (fr), Western Frisian (fy), Irish (ga), Gaelic; Scottish Gaelic (gd), Galician (gl), Gujarati (gu), Hausa (ha), Hebrew (he), Hindi (hi), Croatian (hr), Haitian; Haitian Creole (ht), Hungarian (hu), Armenian (hy), Indonesian (id), Igbo (ig), Iloko (ilo), Icelandic (is), Italian (it), Japanese (ja), Javanese (jv), Georgian (ka), Kazakh (kk), Central Khmer (km), Kannada (kn), Korean (ko), Luxembourgish; Letzeburgesch (lb), Ganda (lg), Lingala (ln), Lao (lo), Lithuanian (lt), Latvian (lv), Malagasy (mg), Macedonian (mk), Malayalam (ml), Mongolian (mn), Marathi (mr), Malay (ms), Burmese (my), Nepali (ne), Dutch; Flemish (nl), Norwegian (no), Northern Sotho (ns), Occitan (post 1500) (oc), Oriya (or), Panjabi; Punjabi (pa), Polish (pl), Pushto; Pashto (ps), Portuguese (pt), Romanian; Moldavian; Moldovan (ro), Russian (ru), Sindhi (sd), Sinhala; Sinhalese (si), Slovak (sk), Slovenian (sl), Somali (so), Albanian (sq), Serbian (sr), Swati (ss), Sundanese (su), Swedish (sv), Swahili (sw), Tamil (ta), Thai (th), Tagalog (tl), Tswana (tn), Turkish (tr), Ukrainian (uk), Urdu (ur), Uzbek (uz), Vietnamese (vi), Wolof (wo), Xhosa (xh), Yiddish (yi), Yoruba (yo), Chinese (zh), Zulu (zu)    括号内的为枚举项 |
| `tgtLang`         | String   | Y        | 同上                                                         |

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

| 参数名称          | 参数类型                | 是否必填 | 参数说明         |
| :---------------- | :---------------------- | :------- | :--------------- |
| `code`            | int                     | Y        | 返回code码0:成功 |
| `msg`             | string                  | N        | msg              |
| `serialNo`        | string                  | N        | 交互的流水号     |
| `translationInfo` | `JsonArray` | Y        | 翻译信息         |
| `+id`           | `int`        | N        | `识别框编号 为每个检测到的框定义id`        |
| `+text`         | String       | N        | `识别的文本行内容`                         |
| `+boxesXy`      | List<String> | N        | `返回四个角点的坐标`                       |
| `+translation`  | String       | N        | `识别文本行对应的翻译`                     |
| `+detectStatus` | boolean      | N        | `文本框检测是否成功 true 成功  false 失败` |

请求参数示例

```
{
    "srcLang":"zh",
    "tgtLang":"en",
    "imageItem":{
        "imgType":"COM",
        "imgBase64":"",
        "encryptionType":"NON"
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
        "vehicleInvoiceInfo":[
            {
                "id":1,
                "text":"1I Page",
                "boxesXy":[
                    "2021",
                    "3230",
                    "2155",
                    "3237",
                    "2152",
                    "3282",
                    "2019",
                    "3276"
                ],
                "translation":"1 of Page",
                "detectStatus":true
            },
            {
                "id":2,
                "text":"元房等)，每月从该物业收到的收入以及物业的价值。",
                "boxesXy":[
                    "228",
                    "3087",
                    "1184",
                    "3093",
                    "1183",
                    "3138",
                    "228",
                    "3133"
                ],
                "translation":"The income received from the property and the value of the property per month",
                "detectStatus":true
            }
        ],
        "timestamp":1618381882201
    }
}
```

