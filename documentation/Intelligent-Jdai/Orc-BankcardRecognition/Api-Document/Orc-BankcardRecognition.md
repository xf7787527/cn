# 银行卡识别（V2）


## 描述
银行卡识别（V2）

## 请求方式

POST

## 请求地址

```apl
https://aiapi.jd.com/jdai/bankcardRecognition
```



## header请求参数

| 名称             | 类型   | 是否必需 | 示例值           | 描述     |
| ---------------- | ------ | -------- | ---------------- | -------- |
| **Content-Type** | String | 是       | application/json | json格式 |

### body请求参数

| 参数名称        | 参数类型 | 是否必填 | 示例值                                                       | 参数说明                            |
| :-------------- | :------- | :------- | ------------------------------------------------------------ | :---------------------------------- |
| `serialNo`      | string   | N        |                                                              | 请求流水号, 不传接口自动生成        |
| ```imageItem``` | Object   |          | {"imgType": "DL","encryptionType": "NON","imgBase64": "xxxx"} | 图片信息                            |
| `extMap`        | map      | N        |                                                              | 附加信息, 特殊需求处理              |
| `token`         | String   | N        |                                                              | 如果是银行卡SDK,则通过token串联流程 |

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

| 参数名称               | 参数类型 | 是否必填 | 参数说明         |
| :--------------------- | :------- | :------- | :--------------- |
| `code`                 | int      |          | 返回code码0:成功 |
| `msg`                  | string   |          | msg              |
| `serialNo`             | string   |          | 交互的流水号     |
| `````bankcardInfo````` | String   |          | `识别结果```     |



bankcardInfo实体

| 参数名称   | 参数类型 | 是否必填 | 参数说明              |
| ---------- | -------- | -------- | --------------------- |
| cardNumber | string   |          | 银行卡号码            |
| cardType`  | string   |          | 卡类型(借记卡,信用卡) |
| issuer     | string   |          | 发行机构 银行名称     |
| validDate  | string   |          | 有效期                |
| owner      | string   |          | 持卡人                |



### 请求参数示例

```
{
	"imageItem": {
		"encryptionType": "NON",
		"imgBase64": "base64"
	}
}
```



### 返回样例

```
{
  "bankcardInfo": {
    "cardNumber": "4367421147620083682", 
    "cardType": "借记卡", 
    "issuer": "中国建设银行", 
    "owner": "", 
    "validDate": ""
  }, 
  "code": 0, 
  "msg": "成功", 
  "serialNo": "1553592610027-010221165048-166635", 
  "timestamp": 1553592610037
}
```

