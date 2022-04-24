# 驾驶证识别


## 描述
用于识别驾驶证信息

## 请求方式
POST

## 请求地址
https://aiapi.jdcloud.com/api/v1/ocr/driverLicense


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

## 公共返回参数
|名称|类型|示例值|描述|
|---|---|---|---|
|**code**|string|1000|参见下方错误码-系统级错误码|
|**charge**|boolean|false 或 true    |false：不扣费， true：扣费|
|**remainTimes**|long|1305|剩余调用次数；免费api：每天剩余调用次数；收费api：剩余次数；无限制时为-1|
|**remainSeconds**|long|1223456|剩余调用时间（s）；免费api：-1；收费api：剩余调用时间；无限制时为-1|
|**msg**|String|查询成功    |参见下方错误码-系统级错误码|
|**result**|object|{...}    |查询结果|

## 业务返回参数
| 名称                    |类型|示例值|描述|
|-----------------------|---|---|---|
| **code**              |int|0|返回code码 0:成功|
| **msg**               |String|ok    |msg|
| **timestamp**         |string|1550560993638        |时间戳|
| **serialNo**          |string|1550560993628-172025248021-173330    |交互的流水号|
| **driverLicenseInfo** |string|    {...}|识别结果|
| **+address**          |string|广东省潮州市湘桥区六亩村水闸路14号    |住址|
| **+birth**             |string|1989-05-13    |生日|
| **+classNo**           |string|C1|车型|
| **+expDate**           |string|6年|失效时间|
| **+gender**            |string|男|性别|
| **+issueDate**         |string|2011-05-19    |签发日期|
| **+licenseNo**         |string|445102198905131752    |证号|
| **+name**              |string|赖旭宇|姓名|
| **+nation**            |string|中国|国籍|
| **+startDate**         |string|2011-05-19    |初次领证日期|


## 错误码
|业务错误码（code）    |message|说明|
|---|---|---|
|**0**|成功|请求成功|
|**非0**|失败|请求失败|

## 请求参数示例
```json
{
    "imageItem": {
        "imgBase64":"",
        "encryptionType": "NON"
    }
}
```

## 返回样例

```json
{
  "code": 0, 
  "driverLicenseInfo": {
    "address": "广东省潮州市湘桥区六亩村水闸路14号", 
    "birth": "1989-05-13", 
    "classNo": "C1", 
    "expDate": "6年", 
    "gender": "男", 
    "issueDate": "2011-05-19", 
    "licenseNo": "445102198905131752", 
    "name": "赖旭宇", 
    "nation": "中国", 
    "startDate": "2011-05-19"
  }, 
  "serialNo": "1550560993628-172025248021-173330", 
  "timestamp": 1550560993638
}
```
