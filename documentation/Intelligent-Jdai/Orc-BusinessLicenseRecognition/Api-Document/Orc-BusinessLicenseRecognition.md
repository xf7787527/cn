# 营业执照识别


## 描述
营业执照识别

## 请求方式

POST

## 请求地址

```apl
https://aiapi.jdcloud.com/jdai/businessLicenseRecognition
```

## header请求参数

| 名称             | 类型   | 是否必需 | 示例值           | 描述     |
| ---------------- | ------ | -------- | ---------------- | -------- |
| **Content-Type** | String | 是       | application/json | json格式 |

### body请求参数

| 参数名称    | 参数类型 | 是否必填                                                     | 参数说明                     |
| :---------- | :------- | :----------------------------------------------------------- | :--------------------------- |
| `serialNo`  | string   | N                                                            | 请求流水号, 不传接口自动生成 |
| `imageItem` | Object   | {"imgType": "DL","encryptionType": "NON","imgBase64": "xxxx"} | 图片信息                     |
| `extMap`    | map      | N                                                            | 附加信息, 特殊需求处理       |

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

| 参数名称              | 参数类型 | 是否必填 | 参数说明                                                |
| :-------------------- | :------- | :------- | :------------------------------------------------------ |
| `code`                | int      |          | 返回code码0:成功                                        |
| `msg`                 | string   |          | msg                                                     |
| `serialNo`            | string   |          | 交互的流水号                                            |
| `businessLicenseInfo` | String   |          | `识别结果```                                            |
| `--usc`               | string   |          | `统一社会信用代码`                                      |
| `--regNo`             | string   |          | `注册号`                                                |
| `--corpName`          | string   |          | `公司名称`                                              |
| `--corpType`          | string   |          | `类型`                                                  |
| `--regCap`            | string   |          | `注册资本`                                              |
| `--address`           | string   |          | `地址```                                                |
| `--regDate`           | string   |          | `注册日期/成立日期`                                     |
| `--legalRep`          | string   |          | `法定代表人`                                            |
| `--opPeriod`          | string   |          | `营业期限`                                              |
| `--scope`             | string   |          | `经营范围`                                              |
| `--cardType`          | string   |          | `营业执照类型：``primary_page(主页)``vice_page（副业）` |
| --extended            | map      |          | 扩展字段                                                |

### 新增字段extended的内容说明：

| 字段名 | 含义                 | 类型   | 备注                                                         |
| :----- | :------------------- | :----- | :----------------------------------------------------------- |
| rotate | 证件转正需旋转的角度 | String | **M/±N**，例： +180/-5说明:**M:** 主角度，返回【+0、+90、+180、+270】之一，分别表示水平正向，逆时针旋转90°，逆时针旋转180°，逆时针旋转270°。**N：**基于主角度的微调角度，0≤N < 90。“+”表示在主角度旋转的基础上再逆时针旋转N°，“-”表示在主角度旋转的基础上再顺时针旋转N°,例： +180/-5（表示先把营业执照图片先逆时针旋转180度，再顺时针旋转5度即转到正方向） 特别说明：微调角度N对大于30度的情况不是很理想 |



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
  "businessLicenseInfo": {
    "address": "海口市海甸五路北侧A2商住楼601室", 
    "corpName": "海南诚德丰餐饮服务有限公司", 
    "corpType": "有限责任公司(台港澳合资)", 
    "legalRep": "李楚娴", 
    "regCap": "壹任壹佰万元人民币", 
    "regNo": "460000400013639", 
    "scope": "注 册 货 本", 
    "cardType": "primary_page",
	"extended": {
             "rotate": "0/+3"
     }
  }, 
  "code": 0, 
  "msg": "成功", 
  "serialNo": "1565771491639-010221165048-127629", 
  "timestamp": 1565771491648
}
```

