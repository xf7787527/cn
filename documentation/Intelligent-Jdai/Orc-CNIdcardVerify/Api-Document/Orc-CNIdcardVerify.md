# 中国身份证


## 描述
中国身份证

## 请求方式

POST

## 请求地址

```apl
https://aiapi.jd.com/jdai/ocrRecognition
```

## header请求参数

| 名称             | 类型   | 是否必需 | 示例值           | 描述     |
| ---------------- | ------ | -------- | ---------------- | -------- |
| **Content-Type** | String | 是       | application/json | json格式 |

### body请求参数

| 参数名称     | 参数类型 | 是否必填 | 参数说明                                                     |
| :----------- | :------- | :------- | :----------------------------------------------------------- |
| `serialNo`   | string   | N        | 请求流水号, 不传接口自动生成                                 |
| `idcardItem` | object   | Y        | 采集的图片                                                   |
| `idcardType` | enum     |          | `/** * 身份证检测结果(正面, 反面) */`` ``P("身份证正面"),N("身份证反面");` |
| `extMap`     | map      | N        | 附加信息, 特殊需求处理                                       |

idcardItem对象信息

| 参数名称       | 参数类型 | 是否必填 | 示例值 | 参数说明                                                     |
| -------------- | -------- | -------- | ------ | ------------------------------------------------------------ |
| imgType        | enum     | 是       | DL     | 图片的类型 SFF("采集照")，FF("全景采集照")，NIR("双目采集的近红外照片")，DEEP("深度采集的照片")，IDP("身份证正面")，IDN("身份证反面")，MP("网纹照")，AP("动作照")，VL("行驶证")，DL("驾驶证")，BC("银行卡")，BL("营业执照")，LP("车牌")，COM("通用图片 |
| imgBase64      | String   | 是       | DL     | /9j/4AAQSkZJRgABAQAAAQABAA...                                |
| filename       | String   | 否       |        | 图片的存储名, 指定了则不读base64                             |
| imgUrl         | String   | 否       |        | 图片的Url地址（外网地址可能会有socket连接超时问题，建议传base64） |
| imgArr         | byte[]   | 否       |        | 图片的二进制                                                 |
| encryptionType | enum     | 是       | NON    | 加密方式 AKS,LICENSE,NON AKS解密方式：com.wangyin.key.server.DeviceCryptoService#decryptEnvelop 版本号1.5.3 |

# 返回实体

| 参数名称             | 参数类型 | 是否必填 | 参数说明         |      |
| :------------------- | :------- | :------- | :--------------- | :--- |
| `code`               | int      |          | 返回code码0:成功 |      |
| `msg`                | string   |          | msg              |      |
| `serialNo`           | string   |          | 交互的流水号     |      |
| `idCardInfo`         | object   |          | 正面信息         |      |
| `--name`             | `String` |          | `身份证号`       |      |
| `--cardNo`           | `String` |          | `姓名`           |      |
| `--sex`              | `String` |          | `性别`           |      |
| `--nation`           | `String` |          | `名族`           |      |
| `--address`          | `String` |          | `户籍地址`       |      |
| `--brith`            | `String` |          | 生日yyyymmdd     |      |
| `idCardBackInfo`     | object   |          | 反面信息         |      |
| `--singDate`         | `String` |          | `签发时间`       |      |
| `--expirationDate`   | `String` |          | `过期时间`       |      |
| `--issuingAuthority` | `String` |          | `签证机关`       |      |
| `--overdue`          | `String` |          | `是否过期`       |      |
| `extMap`             | map      |          | 返回身份证url    |      |
| `--idCardUrl`        | `String` |          | 身份证正面url    |      |
| `--idCardBackUrl`    | `String` |          | 身份证反面url    |      |



## 请求参数示例

```
{
	"idcardType": "P",
	"idcardItem": {
		"imgType": "IDP",
		"imgBase64": "图片se64",
		"encryptionType": "NON"
	}
}
```



## 返回样例

```
{
    "code": 0,
    "idCardInfo": {
        "name": "张素芳",
        "address": "山西省忻州市忻府区董村镇太延村二组215号",
        "nation": "汉",
        "cardNo": "142201199003272740",
        "sex": "女"
    },
    "serialNo": "w1232",
    "timestamp": 1547524786490
}
```

