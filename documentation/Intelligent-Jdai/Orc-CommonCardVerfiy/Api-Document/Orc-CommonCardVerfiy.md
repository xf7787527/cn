# 通用卡证质检


## 描述
通用卡证质检

## 请求方式

POST

## 请求地址

```apl
https://aiapi.jdcloud.com/jdai/commonCardVerfiy
```

## header请求参数

| 名称             | 类型   | 是否必需 | 示例值           | 描述     |
| ---------------- | ------ | -------- | ---------------- | -------- |
| **Content-Type** | String | 是       | application/json | json格式 |

### body请求参数

| 参数名称    | 参数类型 | 是否必填 | 参数说明                     |
| :---------- | :------- | :------- | :--------------------------- |
| `serialNo`  | string   | N        | 请求流水号, 不传接口自动生成 |
| `imageItem` | Object   |          | 图片信息                     |
| `extended`  | map      | N        | 附加信息, 特殊需求处理       |

`imageItem`对象信息

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
| `data`      | Object    |          | 得分                            |
| `algResult` | `Boolean` |          | 防伪结果，true通过，false不通过 |

字段data的内容说明：

| 参数名称       | 参数类型 | 参数说明                           |
| :------------- | :------- | :--------------------------------- |
| bbox           | Object   | 【"left", "top","width","height"】 |
| blur           | Float    | 质检【是否模糊】分数               |
| incompleteness | Float    | 身份证【是否残缺】分数             |
| fakePortrait   | Float    | 防伪【头像贴图】分数               |
| fakeMonocopy   | Float    | 防伪【是否复印件】分数             |
| fakeColorcopy  | Float    | 防伪【是否彩印】分数               |
| fakeScreen     | Float    | 防伪【是否屏幕翻拍】分数           |

### 请求参数示例

```
{
    "imageItem": {
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
    "data": {
        "blur": 0.1
    },
    "algResult":true,
    "msg": "成功",
    "serialNo": "12092873283-2313",
    "timestamp": 1646188619374
}
```

