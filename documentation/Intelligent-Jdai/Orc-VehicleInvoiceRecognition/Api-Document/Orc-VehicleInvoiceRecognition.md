# 机动车销售发票识别


## 描述
机动车销售发票识别

## 请求方式

POST

## 请求地址

```apl
https://aiapi.jd.com/jdai/vehicleInvoiceRecognition
```



### 请求参数

| 参数名称  | 参数类型 | 是否必填 | 参数说明                     |
| :-------- | :------- | :------- | :--------------------------- |
| serialNo  | string   | N        | 请求流水号, 不传接口自动生成 |
| imageItem | Object   | Y        | 图片信息                     |

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

| 参数名称             | 参数类型             | 是否必填 | 参数说明         |
| :------------------- | :------------------- | :------- | :--------------- |
| `code`               | int                  | Y        | 返回code码0:成功 |
| `msg`                | string               | N        | msg              |
| `serialNo`           | string               | N        | 交互的流水号     |
| `vehicleInvoiceInfo` | `VehicleInvoiceInfo` | Y        | 购车发票识别信息 |

字段VehicleInvoiceInfo的内容说明：

| 参数名称                   | 参数类型 | 是否必填 | 参数说明       |
| :------------------------- | :------- | :------- | :------------- |
| `totalAmount`              | `String` | N        | `价税合计`     |
| `engineNumber`             | String   | N        | `发动机号码`   |
| `address`                  | String   | N        | `地址`         |
| `salerName`                | String   | N        | `销货单位名称` |
| `invoiceNo`                | String   | N        | `发票号码`     |
| `brandModel`               | String   | N        | `厂牌型号`     |
| `vin`                      | String   | N        | `车辆识别代号` |
| `invoiceDate`              | String   | N        | `开票日期`     |
| `vehicleType`              | String   | N        | `车辆类型`     |
| `invoiceCode`              | String   | N        | `发票代码`     |
| `taxpayerIdentificationNo` | String   | N        | `纳税人识别号` |

**请求参数示例**

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
    "code": 0,
    "msg": "成功",
    "serialNo": "12092873283-2313",
    "vehicleInvoiceInfo": {
			"totalAmount":"价税合计",
 			"engineNumber":"发动机号码", 
 			"address":"地址", 
 			"salerName":"销货单位名称", 
 			"invoiceNo":"发票号码", 
 			"brandModel":"厂牌型号", 
 			"vin":"车辆识别代号", 
 			"invoiceDate":"开票日期", 
 			"vehicleType":"车辆类型", 
 			"invoiceCode":"发票代码", 
 			"taxpayerIdentificationNo":"纳税人识别号"
		},
    "timestamp": 1618381882201
}
```

