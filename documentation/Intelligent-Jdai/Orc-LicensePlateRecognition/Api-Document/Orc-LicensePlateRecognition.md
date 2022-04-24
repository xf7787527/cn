# 车牌识别


## 描述
车牌识别

## 请求方式

POST

## 请求地址

```apl
https://aiapi.jdcloud.com/jdai/licensePlateRecognition
```



## 请求参数

|名称|类型|是否必需|参数说明|
|---|---|---|---|
| serialNo | string | N      | 请求流水号, 不传接口自动生成                                 |
| imageItem | Object | Y | 图片信息 |
| extMap | map | N | 附加信息, 特殊需求处理 |

imageItem对象信息说明

| 参数名称       | 参数类型 | 是否必填 | 示例值 | 参数说明                                                     |
| -------------- | -------- | -------- | ------ | ------------------------------------------------------------ |
| imgType        | enum     | 是       | DL     | 图片的类型 SFF("采集照")，FF("全景采集照")，NIR("双目采集的近红外照片")，DEEP("深度采集的照片")，IDP("身份证正面")，IDN("身份证反面")，MP("网纹照")，AP("动作照")，VL("行驶证")，DL("驾驶证")，BC("银行卡")，BL("营业执照")，LP("车牌")，COM("通用图片 |
| imgBase64      | String   | 是       | DL     | /9j/4AAQSkZJRgABAQAAAQABAA...                                |
| filename       | String   | 否       |        | 图片的存储名, 指定了则不读base64                             |
| imgUrl         | String   | 否       |        | 图片的Url地址（外网地址可能会有socket连接超时问题，建议传base64） |
| imgArr         | byte[]   | 否       |        | 图片的二进制                                                 |
| encryptionType | enum     | 是       | NON    | 加密方式 AKS,LICENSE,NON AKS解密方式：com.wangyin.key.server.DeviceCryptoService#decryptEnvelop 版本号1.5.3 |



### 返回实体

|名称|类型| 是否必填 |描述|
|---|---|---|---|
|**code**|int|Y| 返回code码,0:成功  |
|msg|string| N | msg                |
|**serialNo**|string|N| 交互的流水号 |
|**plateNo**|String|N|车牌号|



## 请求参数示例

```json
{
    "imageItem": {
        "encryptionType": "NON",
        "imgBase64": "图片base64",
        "imgType": "LP",
        "valid": true
    },
    "imageType": "jpg",
    "serialNo": "1598547146344-172025157194-181093"
}
```

## 返回样例

```json
{
  "code": 0, 
  "msg": "成功", 
  "plateNo": "苏E·05EV8", 
  "serialNo": "1598547146344-172025157194-181093", 
  "timestamp": 1600085312210
}
```

