# 飞机行程票


## 描述
飞机行程票

## 请求方式

POST

## 请求地址

```apl
https://aiapi.jd.com/jdai/maskInsurance
```



## header请求参数

| 名称             | 类型   | 是否必需 | 示例值           | 描述     |
| ---------------- | ------ | -------- | ---------------- | -------- |
| **Content-Type** | String | 是       | application/json | json格式 |

### body请求参数

|名称|类型|是否必需|参数说明|
|---|---|---|---|
| serialNo | string | N      | 请求流水号, 不传接口自动生成                                 |
| imageItem | Object | Y | 图片信息 |

imageItem对象信息

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
| `airplaneItineraryInfo` | `AirplaneItineraryInfo` | N        | 火车票识别结果    |

## 字段AirplaneItineraryInfo的内容说明

| 参数名称        | 参数类型 | 是否必填 | 参数说明       |
| :-------------- | :------- | :------- | :------------- |
| `userName`      | `String` | N        | `旅客姓名`     |
| `idNumber`      | String   | N        | `旅客身份证号` |
| `startTerminal` | String   | N        | `起始站`       |
| `endTerminal`   | String   | N        | `终点站`       |
| `fare`          | String   | N        | `票价`         |
| `ticketId`      | String   | N        | `票ID码`       |
| `cadFund`       | String   | N        | `民航发展基金` |
| `total`         | String   | N        | `合计`         |
| `eTicketNo`     | String   | N        | `电子客票号码` |
| `issuedBy`      | String   | N        | `填开单位`     |
| `dateOfIssue`   | String   | N        | `填开日期`     |


## 请求参数示例
```json
{
	"imageItem": {
		"imgType": "COM",
		"imgBase64":"",
		"encryptionType": "NON"
	}
}
```

## 返回样例

```json
{
    "code": 0,
    "msg": "成功",
    "serialNo": "12092873283-2313",
    "airplaneItineraryInfo": {         
            "userName": "旅客姓名",
		    "idNumber": "旅客身份证号",
 		    "startTerminal": "起始站", 
 		    "endTerminal": "终点站", 
 		    "fare": "票价", 
 		    "ticketId": "票ID码", 
 		    "cadFund": "民航发展基金", 
 		    "total": "合计", 
 		    "eTicketNo": "电子客票号码", 
 		    "issuedBy": "填开单位",
  		    "dateOfIssue": "填开日期"
    },
    "timestamp": 1618381882201
}
```

