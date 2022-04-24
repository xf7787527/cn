# 增值税发票识别


## 描述
增值税发票识别

## 请求方式

POST

## 请求地址

```apl
https://aiapi.jdcloud.com/jdai/invoiceRecognition
```

### 请求参数

| 参数名称  | 参数类型 | 是否必填 | 参数说明                     |
| :-------- | :------- | :------- | :--------------------------- |
| serialNo  | string   | N        | 请求流水号, 不传接口自动生成 |
| imageItem | Object   |          | 图片信息                     |
| extended  | map      | N        | 附加信息, 特殊需求处理       |

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

| 参数名称 | 参数类型 | 是否必填 | 参数说明         |
| :------- | :------- | :------- | :--------------- |
| code     | int      |          | 返回code码0:成功 |
| msg      | string   |          | msg              |
| serialNo | string   |          | 交互的流水号     |
| data     | Object   |          | 识别结果         |

字段data的内容说明：

| 参数名称      | 参数类型 | 是否必填 | 参数说明           |
| :------------ | :------- | :------- | :----------------- |
| `invoiceType` | string   | N        | `发票类型`         |
| IsEInvoice    | String   | N        | 是否电子发票       |
| invoiceCode   | String   | N        | 发票代码           |
| invoiceNo     | String   | N        | 发票号码           |
| buyerName     | String   | N        | 购买方名称         |
| buyerTaxNo    | String   | N        | 购买方税号         |
| buyerAddress  | String   | N        | 购买方地址         |
| buyerAcount   | String   | N        | 购买方开户行及账号 |
| salerName     | String   | N        | 销售方名称         |
| salerTaxNo    | String   | N        | 销售方税号         |
| salerAddress  | String   | N        | 销售方地址         |
| salerAcount   | String   | N        | 销售方账号         |
| invoiceDate   | String   | N        | 开票日期           |
| verifyCode    | String   | N        | 校验码             |
| invoiceAmount | String   | N        | 发票金额           |
| taxAmount     | String   | N        | 发票税额           |
| totalAmount   | String   | N        | 价格合计           |
| remark        | String   | N        | 备注               |
| invoiceStatus | String   | N        | 发票状态           |
| legalizeState | String   | N        | 认证状态           |
| legalizeDate  | String   | N        | 认证日期           |
| payee         | String   | N        | 收款人             |
| reviewer      | String   | N        | 复核人             |
| drawer        | String   | N        | 开票人             |
| detaillists   | List     | N        | 商品详细信息       |

字段detaillists的内容说明：

| 参数名称     | 参数类型 | 是否必填 | 参数说明   |
| :----------- | :------- | :------- | :--------- |
| detailNo     | string   | N        | `明细编号` |
| goodName     | string   | N        | 货物名称   |
| model        | string   | N        | 规格       |
| `unit`       | `string` | N        | `单位`     |
| num          | string   | N        | 数量       |
| unitPrice    | string   | N        | 单价       |
| detailAmount | string   | N        | 金额       |
| taxRate      | string   | N        | 税率       |
| taxAmount    | string   | N        | 税额       |



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
    "msg": "成功",
    "data": {
        "IsEInvoice": "true",
        "arriveCity": "",
        "buyerAcount": "",
        "buyerAddress": "",
        "buyerName": "",
        "buyerTaxNo": "",
        "checkState": "18",
        "departCity": "",
        "detaillists": [
            {
                "detailAmount": "",
                "detailNo": "",
                "extended": {},
                "goodName": "三星(SAMSUNG)S24E360HL23.6英",
                "model": "",
                "num": "",
                "taxAmount": "",
                "taxRate": "",
                "unit": "",
                "unitPrice": ""
            }
        ],
        "drawer": "京东商城",
        "extended": {},
        "invoiceAmount": "828.20",
        "invoiceCode": "111001571071",
        "invoiceDate": "20151212",
        "invoiceNo": "39788264",
        "invoiceStatus": "",
        "invoiceType": "04",
        "legalizeDate": "",
        "legalizeState": "",
        "passenger": "",
        "payee": "京东商城",
        "remark": "",
        "reviewer": "",
        "salerAcount": "",
        "salerAddress": "北京市北京经济技术开发区科创十四街99号2号楼B168室010-56754036",
        "salerName": "北京京东世纪信息技术有限公司",
        "salerTaxNo": "110192562134916",
        "taxAmount": "140.80",
        "totalAmount": "969.00",
        "trainNumber": "",
        "verifyCode": "49507382490687444615"
    },
    "serialNo": "12092873283-2313",
    "timestamp": 1618387383964
}
```

