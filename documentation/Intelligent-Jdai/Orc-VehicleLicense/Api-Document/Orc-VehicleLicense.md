# 行驶证识别


## 描述
行驶证识别

## 请求方式

POST

## 请求地址

```apl
https://aiapi.jdcloud.com/jdai/vehicleLicense
```



### 请求参数

| 参数名称  | 参数类型 | 是否必填 | 参数说明                                                     |
| :-------- | :------- | :------- | :----------------------------------------------------------- |
| serialNo  | string   | N        | 请求流水号, 不传接口自动生成                                 |
| imageItem | Object   |          | 图片信息                                                     |
| extMap    | map      | N        | 附加信息, 特殊需求处理                                       |
| cardType  | string   | N        | 取值【“primary”, "vice", "unknown"】注: 若行驶证主副页未知, 传"unknown"字段. |

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

| 参数名称              | 参数类型 | 是否必填 | 参数说明                                    |
| :-------------------- | :------- | :------- | :------------------------------------------ |
| code                | int      |          | 返回code码0:成功                            |
| msg                 | string   |          | msg                                         |
| serialNo            | string   |          | 交互的流水号                                |
| recognitionInfo | String   |          | 识别结果                                |
| plateNo           | string   |          | 号牌号码                                  |
| vehicleType       | string   |          | 车辆类型                                  |
| owner                                  |string||所有人|
| address                                      |string||地址|
| model                                  |string||品牌型号|
| useCharacter                              |string||使用性质|
| engineNo                                  |string||发动机|
| vin                                |string||车辆识别|
| registerDate                                  |string||注册|
| issueDate                                  |string||发证时|
| cardType          | string   |          | 主页：“primary”,副页："vice", 或者"unknown" |



### 请求参数示例

```

{
	"cardType": "primary",
	"imageItem": {
		"encryptionType": "NON",
		"imgBase64": "base64"
	}
}
```



### 返回样例

```
{
  "code": 0, 
  "recognitionInfo": {
    "address": "更庆市蕴山县缜青北路543号21幢2单元2-1", 
    "engineNo": "U27374", 
    "issueDate": "2013-11-27", 
    "model": "大众牌FV7162FAAGG", 
    "owner": "段明亮", 
    "plateNo": "渝A618G6", 
    "registerDate": "2013-11-26", 
    "useCharacter": "非营运", 
    "vehicleType": "小型轿车", 
    "vin": "LFV2A2157D3164452",
	"cardType": "primary"
  }, 
  "serialNo": "1550560993628-172025248021-173330", 
  "timestamp": 1550560993638
}
```

