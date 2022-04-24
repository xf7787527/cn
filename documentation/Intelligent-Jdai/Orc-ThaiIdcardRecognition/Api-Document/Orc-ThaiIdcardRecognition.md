# 泰国身份证


## 描述
泰国身份证

## 请求方式

POST

## 请求地址

```apl
https://aiapi.jdcloud.com/jdai/thaiIdcardRecognition
```

### 请求参数

| 参数名称  | 参数类型 | 是否必填 | 参数说明                                     |
| :-------- | :------- | :------- | :------------------------------------------- |
| serialNo  | string   | N        | 请求流水号, 不传接口自动生成                 |
| imageItem | Object   |          | 图片信息                                     |
| cardType  | string   | N        | 正反面【“front”，“back”】, 若未知传"unknown" |

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

| 参数名称   | 参数类型 | 是否必填 | 参数说明         |
| :--------- | :------- | :------- | :--------------- |
| `code`     | int      |          | 返回code码0:成功 |
| `msg`      | string   |          | msg              |
| `serialNo` | string   |          | 交互的流水号     |
| `data`     | `Object` |          | 识别结果         |

字段data的内容说明：

正面时data为：

| 参数名称       | 参数类型 | 参数说明                                   | 是否必填 |
| :------------- | :------- | :----------------------------------------- | :------- |
| cardType       | String   | 证件正反面，【"front"， "back"， "other"】 | ``       |
| `id`           | String   | 证件号码                                   |          |
| `thaiName`     | String   | 泰国姓名                                   |          |
| `thaiAddress`  | String   | 住址                                       |          |
| `engFirstName` | String   | 英文姓                                     |          |
| `engLastName`  | String   | 英文名称                                   |          |
| `engBirthDate` | String   | 出生日期                                   |          |
| `issueDate`    | String   | 发证日期                                   |          |
| `expiryDate`   | String   | 有效期                                     |          |

反面时data为：

| 参数名称       | 参数类型 | 参数说明                                   | 是否必填 |
| :------------- | :------- | :----------------------------------------- | :------- |
| cardType       | String   | 证件正反面，【"front"， "back"， "other"】 | ``       |
| `securityCode` | String   |                                            |          |

### 请求参数示例

```
{
    "cardType": "front",
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
    "msg": "成功",
    "code": 0,
    "data": {
        "expiryDate": "19 Dec. 2022",
        "engLastName": "Panpun",
        "thaiName": "น.ส. จีระนันท์ พานพันธ์",
        "engBirthDate": "20 Dec. 1980",
        "cardType": "front",
        "thaiAddress": "137 หมู่ที่ 18 ต.ศรีสุข อ.กันทรวิชัยจ.มหาสารคาม",
        "engFirstName": "Miss Jeranan",
        "id": "3 4404 00493 30 7",
        "issueDate": "20 Dec. 2014"
    },
    "serialNo": "1598547146344-172025157194-181093",
    "timestamp": 1646705681424
}
```

