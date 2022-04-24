# 驾驶证识别


## 描述
驾驶证识别

## 请求方式

POST

## 请求地址

```apl
https://aiapi.jdcloud.com/jdai/driverLicenseRecognition
```



## header请求参数

| 名称             | 类型   | 是否必需 | 示例值           | 描述     |
| ---------------- | ------ | -------- | ---------------- | -------- |
| **Content-Type** | String | 是       | application/json | json格式 |

### body请求参数

| 参数名称        | 参数类型 | 是否必填 | 参数说明                     |
| :-------------- | :------- | :------- | :--------------------------- |
| `serialNo`      | string   | N        | 请求流水号, 不传接口自动生成 |
| ```imageItem``` | Object   |          | 图片信息                     |
| `extMap`        | map      | N        | 附加信息, 特殊需求处理       |

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

| 参数名称                    | 参数类型 | 是否必填 | 参数说明         |
| :-------------------------- | :------- | :------- | :--------------- |
| `code`                      | int      |          | 返回code码0:成功 |
| `msg`                       | string   |          | msg              |
| `serialNo`                  | string   |          | 交互的流水号     |
| `````driverLicenseInfo````` | String   |          | `识别结果```     |
| `--licenseNo`               | string   |          | `证号`           |
| `--name`                    | string   |          | `姓名`           |
| `--gender`                  | string   |          | `性别`           |
| `--nation`                  | string   |          | `国籍`           |
| `--address`                 | string   |          | `住址`           |
| `--birth`                   | string   |          | `生日`           |
| `--startDate`               | string   |          | `初次领证日期`   |
| `--classNo`                 | string   |          | `车型`           |
| `--issueDate`               | string   |          | `签发日期`       |
| `--expDate`                 | string   |          | `失效时间`       |
|                             |          |          |                  |
|                             |          |          |                  |

### 请求参数示例

```

{
	"imageItem": {
		"imgType": "DL",
		"encryptionType": "NON",
		"imageType": "jpg"
	}
}
```



### 返回样例

```
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