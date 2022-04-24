# 通用手写体


## 描述
通用手写体

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

| 参数名称    | 参数类型 | 是否必填 | 参数说明                                                     |
| :---------- | :------- | :------- | :----------------------------------------------------------- |
| `serialNo`  | string   | N        | 请求流水号, 不传接口自动生成                                 |
| `imageItem` | Object   | Y        | 图片信息                                                     |
| cardType    | string   | Y        | 手写体【”handwriting“】，印刷体【”print“】，手写体+印刷体【"all"】 |

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

| 参数名称    | 参数类型        | 是否必填 | 参数说明                   |
| :---------- | :-------------- | :------- | :------------------------- |
| `code`      | int             | Y        | 返回code码0:成功           |
| `msg`       | string          | N        | msg                        |
| `serialNo`  | string          | N        | 交互的流水号               |
| `blur`      |                 | N        | `模糊程度（值越大越清晰）` |
| location    | Point           | N        | 检测字符边框               |
| `textsInfo` | List<TextsInfo> | N        | 识别结果                   |

字段textsInfo的内容说明：

| 参数名称 | 参数类型 | 是否必填 | 参数说明                                                 |
| :------- | :------- | :------- | :------------------------------------------------------- |
| `type``` | string   | Y        | `字体类型：手写体【“handwriting"】，``印刷体【"print"】` |
| `text`   | `string` | Y        | `识别后的文本结果`                                       |
| points   | Point    | Y        | 文本所在位置矩形顶点坐标[pt0, pt1, pt2, pt3]             |

### 请求参数示例

```
{
	"imageItem": {
		"imgType": "COM",
		"imgBase64":"",
		"encryptionType": "NON"
	},
	"imageType": "jpg",
	"cardType": "handwriting"
}
```



### 返回样例

```
{
    "blur": 442.92627,
    "code": 0,
    "msg": "成功",
    "serialNo": "12092873283-2313",
	"location": {
        "top": 227,
        "left": 143,
        "width": 611,
        "height": 114
    }
    "textsInfo": [
        {
            "points": [
                {
                    "x": 1,
                    "y": 143
                },
                {
                    "x": 237,
                    "y": 752
                },
                {
                    "x": 227,
                    "y": 754
                },
                {
                    "x": 331,
                    "y": 144
                }
            ],
            "text": "中文手写体测试",
            "type": "handwriting"
        }
    ],
    "timestamp": 1618467122528
}
```