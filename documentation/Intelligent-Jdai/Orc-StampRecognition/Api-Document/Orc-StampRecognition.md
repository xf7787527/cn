# 印章识别

## 描述

印章识别

## 请求方式

POST

## 请求地址

```apl
https://aiapi.jd.com/jdai/stampRecognition
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

| 参数名称    | 参数类型          | 是否必填 | 参数说明         |
| :---------- | :---------------- | :------- | :--------------- |
| `code`      | int               | Y        | 返回code码0:成功 |
| `msg`       | string            | N        | msg              |
| `serialNo`  | string            | N        | 交互的流水号     |
| `stampInfo` | `JsonArray` | N        | `印章识别结果`   |
| `+bbox`      | `JsonObject`         | N        | `检测坐标信息`                                   |
| `++top`    | `Integer` | N        | `高`       |
| `++left`   | Integer   | N        | 左         |
| `++width`  | Integer   | N        | 人脸的宽度 |
| `++height` | Integer   | N        | 人脸的高度 |

| `+color`     | String                | N        | `颜色 取值【"red", "gray"】`                     |
| `+shape`     | String                | N        | `形状 取值【“circle”, "rectangle"】`             |
| `+qualities` | `List<String>`        | N        | `质量属性 【"incomplete" 残缺】`                 |
| `+content`   | String                | N        | `印章识别公司名称，返回印章公司名称字段识别结果` |
| +contentExt  | List<String>          | N        | `印章识别其他内容，返回印章所有其他字段识别结果` |
| `+verify`    | String                | N        | `防伪分数  功能开发中`                           |
| `+extended`  | `Map<String, Object>` | N        | `待扩展字段`                                     |


###请求参数示例

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
        "stampInfo":{
            "bbox":{
                "left":356,
                "top":417,
                "width":157,
                "height":158
            },
            "shape":"circle",
            "color":"red",
            "qualities":[

            ],
            "content":"苏州xxxxxxxxxxxx有限公司",
            "contentExt":[
                "3205120029070"
            ],
            "verify":0,
            "extended":null
        },
        "timestamp":1618381882201
    }
}
```
