# 香港身份证质检防伪


## 描述
香港身份证质检防伪

## 请求方式

POST

## 请求地址

```apl
https://aiapi.jdcloud.com/jdai/hkIdCardVerify
```



## header请求参数

| 名称             | 类型   | 是否必需 | 示例值           | 描述     |
| ---------------- | ------ | -------- | ---------------- | -------- |
| **Content-Type** | String | 是       | application/json | json格式 |

### body请求参数

| 参数名称            | 参数类型 | 是否必填 | 参数说明                     |
| :------------------ | :------- | :------- | :--------------------------- |
| `serialNo`          | string   | N        | 请求流水号, 不传接口自动生成 |
| `imageItem`         | Object   | Y        | 图片信息                     |
| `imageItemExposure` | Object   | N        | 曝光图片信息                 |
| `extended`          | map      | N        | 附加信息, 特殊需求处理       |

imageItem、imageItemExposure对象信息

| 参数名称       | 参数类型 | 是否必填 | 示例值 | 参数说明                                                     |
| -------------- | -------- | -------- | ------ | ------------------------------------------------------------ |
| imgType        | enum     | 是       | DL     | 图片的类型 SFF("采集照")，FF("全景采集照")，NIR("双目采集的近红外照片")，DEEP("深度采集的照片")，IDP("身份证正面")，IDN("身份证反面")，MP("网纹照")，AP("动作照")，VL("行驶证")，DL("驾驶证")，BC("银行卡")，BL("营业执照")，LP("车牌")，COM("通用图片 |
| imgBase64      | String   | 是       | DL     | /9j/4AAQSkZJRgABAQAAAQABAA...                                |
| filename       | String   | 否       |        | 图片的存储名, 指定了则不读base64                             |
| imgUrl         | String   | 否       |        | 图片的Url地址（外网地址可能会有socket连接超时问题，建议传base64） |
| imgArr         | byte[]   | 否       |        | 图片的二进制                                                 |
| encryptionType | enum     | 是       | NON    | 加密方式 AKS,LICENSE,NON AKS解密方式：com.wangyin.key.server.DeviceCryptoService#decryptEnvelop 版本号1.5.3 |

### 返回实体

| 参数名称    | 参数类型  | 是否必填 | 参数说明                        |
| :---------- | :-------- | :------- | :------------------------------ |
| `code`      | int       |          | 返回code码0:成功                |
| `msg`       | string    |          | msg                             |
| `serialNo`  | string    |          | 交互的流水号                    |
| `data`      | Object    |          | 识别结果                        |
| `algResult` | `Boolean` |          | 防伪结果，true通过，false不通过 |

字段data的内容说明：

| 参数名称      | 参数类型 | 参数说明 |
| :------------ | :------- | :------- |
| `quality```   | Object   | ``       |
| `antiForgery` | `Object` |          |

字段quality的内容说明：

| 参数名称 | 参数类型 | 参数说明            |
| :------- | :------- | :------------------ |
| blur     | Float    | 证据模糊程度分数    |
| cover    | Float    | 防伪点/关键区域遮挡 |

字段antiForgery的内容说明：

| 参数名称      | 参数类型 | 参数说明                              |
| :------------ | :------- | :------------------------------------ |
| portraitBB    | Float    | `两个大人像防伪点分数`                |
| portraitBS    | `Float`  | `大小头像防伪点分数`                  |
| verify1       | Float    | 其他防伪点1分数                       |
| verify2       | Float    | 其他防伪点2分数                       |
| fakePortrait  | Float    | 防伪【头像贴图】分数,v2.1版本新增     |
| fakeMonocopy  | Float    | 防伪【是否复印件】分数,v2.1版本新增   |
| fakeColorcopy | Float    | 防伪【是否彩印】分数,v2.1版本新增     |
| fakeScreen    | Float    | 防伪【是否屏幕翻拍】分数,v2.1版本新增 |

### 请求参数示例

```
{
    "imageItem": {
        "encryptionType": "NON",
        "imgBase64": "",
        "imgType": "COM"
    },
     "imageItemExposure": {
        "encryptionType": "NON",
        "imgBase64": "",
        "imgType": "COM"
    },
    "serialNo": "12092873283-2313"
}
```

### 返回样例

```
{
    "code": 0,
    "quality": {
        "blur": 0.1
    },
     "antiForgery": {
        "portraitBB": 0.1
    }, 
    "algResult":true,
    "msg": "成功",
    "serialNo": "12092873283-2313",
    "timestamp": 1646188619374
}
```



