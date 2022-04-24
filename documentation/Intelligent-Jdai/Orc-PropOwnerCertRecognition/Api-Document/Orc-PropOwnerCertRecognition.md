# 房产证识别


## 描述
房产证识别

## 请求方式

POST

## 请求地址

```apl
https://aiapi.jdcloud.com/jdai/propOwnerCertRecognition
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

| 参数名称   | 参数类型 | 是否必填 | 参数说明         |
| :--------- | :------- | :------- | :--------------- |
| `code`     | int      |          | 返回code码0:成功 |
| `msg`      | string   |          | msg              |
| `serialNo` | string   |          | 交互的流水号     |
| `data`     | Object   |          | 识别结果         |

## 字段data的内容说明

|名称|类型|是否必填|描述|
|---|---|---|---|
|      |      |          |      |




## 请求参数示例
```json
{
    "imageItem": {
        "encryptionType": "NON",
        "imgBase64": "",
        "imgType": "COM"
    },
    "serialNo": "12092873283-2313"
}
```

## 返回样例

```json
{
    "msg": "成功",
    "code": 0,
    "data": {
        "result": {
            "msg": "成功",
            "code": 99200999,
            "class": "com.jd.jr.facecloud.common.export.dto.Result",
            "timestamp": 1646723783475
        },
        "data": {
            "textsInfo": [
                {
                    "text": "房权证",
                    "type": "fqz_key",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 151.0,
                            "y": 35.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 218.0,
                            "y": 38.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 217.0,
                            "y": 68.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 150.0,
                            "y": 65.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "西青区",
                    "type": " city_value",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 217.0,
                            "y": 48.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 267.0,
                            "y": 48.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 267.0,
                            "y": 71.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 217.0,
                            "y": 71.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "字弟",
                    "type": "number_key",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 276.0,
                            "y": 39.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 324.0,
                            "y": 39.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 324.0,
                            "y": 71.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 276.0,
                            "y": 71.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "2359423",
                    "type": "number_value",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 337.0,
                            "y": 51.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 398.0,
                            "y": 51.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 398.0,
                            "y": 68.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 337.0,
                            "y": 68.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "房地产权人",
                    "type": "owner_key",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 68.0,
                            "y": 84.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 157.0,
                            "y": 84.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 157.0,
                            "y": 111.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 68.0,
                            "y": 111.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "沈良有",
                    "type": "situation_value",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 173.0,
                            "y": 90.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 230.0,
                            "y": 90.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 230.0,
                            "y": 118.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 173.0,
                            "y": 118.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "附",
                    "type": "other",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 694.0,
                            "y": 88.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 722.0,
                            "y": 88.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 722.0,
                            "y": 116.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 694.0,
                            "y": 116.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "记",
                    "type": "other",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 811.0,
                            "y": 84.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 839.0,
                            "y": 84.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 839.0,
                            "y": 112.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 811.0,
                            "y": 112.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "共有情况",
                    "type": "situation_key",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 72.0,
                            "y": 125.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 158.0,
                            "y": 125.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 158.0,
                            "y": 147.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 72.0,
                            "y": 147.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "单独所有",
                    "type": "situation_value",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 174.0,
                            "y": 128.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 245.0,
                            "y": 128.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 245.0,
                            "y": 155.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 174.0,
                            "y": 155.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "天津西青区全境大寺镇龙腾花园20",
                    "type": "address_value",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 176.0,
                            "y": 170.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 408.0,
                            "y": 167.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 409.0,
                            "y": 187.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 177.0,
                            "y": 190.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "房地坐落",
                    "type": "address_key",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 71.0,
                            "y": 178.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 155.0,
                            "y": 178.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 155.0,
                            "y": 200.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 71.0,
                            "y": 200.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "号楼404",
                    "type": "address_value",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 177.0,
                            "y": 195.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 238.0,
                            "y": 195.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 238.0,
                            "y": 217.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 177.0,
                            "y": 217.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "登记时间",
                    "type": "date_key",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 72.0,
                            "y": 232.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 158.0,
                            "y": 232.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 158.0,
                            "y": 254.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 72.0,
                            "y": 254.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "2011-07-11",
                    "type": "date_value",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 175.0,
                            "y": 240.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 265.0,
                            "y": 240.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 265.0,
                            "y": 262.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 175.0,
                            "y": 262.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "房屋性质",
                    "type": "nature_key",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 72.0,
                            "y": 271.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 158.0,
                            "y": 271.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 158.0,
                            "y": 293.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 72.0,
                            "y": 293.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "房改房",
                    "type": "nature_value",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 174.0,
                            "y": 274.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 229.0,
                            "y": 274.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 229.0,
                            "y": 302.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 174.0,
                            "y": 302.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "规划用途",
                    "type": "purposes_key",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 72.0,
                            "y": 309.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 158.0,
                            "y": 309.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 158.0,
                            "y": 331.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 72.0,
                            "y": 331.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "商业",
                    "type": "purposes_value",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 173.0,
                            "y": 312.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 217.0,
                            "y": 312.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 217.0,
                            "y": 344.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 173.0,
                            "y": 344.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "总层数",
                    "type": "floors_key",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 103.0,
                            "y": 350.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 154.0,
                            "y": 350.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 154.0,
                            "y": 373.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 103.0,
                            "y": 373.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "建筑面积",
                    "type": "area_key",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 171.0,
                            "y": 345.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 240.0,
                            "y": 348.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 239.0,
                            "y": 373.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 170.0,
                            "y": 370.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "套内建筑面积",
                    "type": "Internal_area_key",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 252.0,
                            "y": 349.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 340.0,
                            "y": 349.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 340.0,
                            "y": 371.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 252.0,
                            "y": 371.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "其他",
                    "type": "other",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 369.0,
                            "y": 353.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 421.0,
                            "y": 353.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 421.0,
                            "y": 375.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 369.0,
                            "y": 375.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "(m)",
                    "type": "other",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 190.0,
                            "y": 367.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 222.0,
                            "y": 367.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 222.0,
                            "y": 385.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 190.0,
                            "y": 385.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "(m写)",
                    "type": "other",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 276.0,
                            "y": 366.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 314.0,
                            "y": 366.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 314.0,
                            "y": 388.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 276.0,
                            "y": 388.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "房",
                    "type": "other",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 70.0,
                            "y": 382.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 91.0,
                            "y": 382.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 91.0,
                            "y": 404.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 70.0,
                            "y": 404.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "22",
                    "type": "floors_value",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 106.0,
                            "y": 406.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 129.0,
                            "y": 406.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 129.0,
                            "y": 425.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 106.0,
                            "y": 425.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "131.94",
                    "type": "area_value",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 177.0,
                            "y": 403.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 228.0,
                            "y": 403.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 228.0,
                            "y": 426.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 177.0,
                            "y": 426.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "125.81",
                    "type": "Internal_area_value",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 266.0,
                            "y": 403.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 317.0,
                            "y": 403.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 317.0,
                            "y": 426.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 266.0,
                            "y": 426.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "屋",
                    "type": "other",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 67.0,
                            "y": 413.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 95.0,
                            "y": 413.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 95.0,
                            "y": 440.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 67.0,
                            "y": 440.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "以下空白",
                    "type": "other",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 160.0,
                            "y": 436.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 233.0,
                            "y": 436.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 233.0,
                            "y": 463.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 160.0,
                            "y": 463.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "状",
                    "type": "other",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 69.0,
                            "y": 449.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 91.0,
                            "y": 449.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 91.0,
                            "y": 472.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 69.0,
                            "y": 472.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "况",
                    "type": "other",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 70.0,
                            "y": 484.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 93.0,
                            "y": 484.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 93.0,
                            "y": 506.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 70.0,
                            "y": 506.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "土地使用年限",
                    "type": "land_use_period_key",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 337.0,
                            "y": 547.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 426.0,
                            "y": 545.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 427.0,
                            "y": 565.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 338.0,
                            "y": 567.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "土",
                    "type": "other",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 70.0,
                            "y": 547.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 93.0,
                            "y": 547.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 93.0,
                            "y": 575.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 70.0,
                            "y": 575.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "地号",
                    "type": "other",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 108.0,
                            "y": 548.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 150.0,
                            "y": 548.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 150.0,
                            "y": 571.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 108.0,
                            "y": 571.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "土地使用权取得方式",
                    "type": "method_of_land_key",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 174.0,
                            "y": 549.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 306.0,
                            "y": 549.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 306.0,
                            "y": 568.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 174.0,
                            "y": 568.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "实",
                    "type": "other",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 66.0,
                            "y": 559.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 97.0,
                            "y": 559.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 97.0,
                            "y": 598.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 66.0,
                            "y": 598.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "项发单位",
                    "type": "other",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 728.0,
                            "y": 576.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 795.0,
                            "y": 576.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 795.0,
                            "y": 598.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 728.0,
                            "y": 598.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "丝",
                    "type": "other",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 421.0,
                            "y": 579.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 443.0,
                            "y": 586.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 437.0,
                            "y": 606.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 415.0,
                            "y": 600.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "迪",
                    "type": "other",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 60.0,
                            "y": 572.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 103.0,
                            "y": 572.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 103.0,
                            "y": 638.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 60.0,
                            "y": 638.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "国有出让",
                    "type": "method_of_land_value",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 194.0,
                            "y": 595.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 265.0,
                            "y": 595.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 265.0,
                            "y": 622.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 194.0,
                            "y": 622.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "2024-01-08",
                    "type": "date_value",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 325.0,
                            "y": 609.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 417.0,
                            "y": 609.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 417.0,
                            "y": 628.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 325.0,
                            "y": 628.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                },
                {
                    "text": "营止",
                    "type": "number_key",
                    "class": "com.jd.jdd.vision.ocr.message.TextsInfoObject",
                    "extended": {

                    },
                    "points": [
                        {
                            "x": 408.0,
                            "y": 612.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 437.0,
                            "y": 612.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 437.0,
                            "y": 625.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        },
                        {
                            "x": 408.0,
                            "y": 625.0,
                            "class": "com.jd.jdd.vision.ocr.message.Point"
                        }
                    ]
                }
            ],
            "class": "com.jd.jdd.vision.ocr.message.PropOwnerCentObject",
            "extended": {

            },
            "structedTextsInfo": [
                {
                    "class": "com.jd.jdd.vision.ocr.message.KeyValueObject",
                    "value": "西青区",
                    "key": " city_value",
                    "extended": {

                    }
                },
                {
                    "class": "com.jd.jdd.vision.ocr.message.KeyValueObject",
                    "value": "2359423",
                    "key": "number_value",
                    "extended": {

                    }
                },
                {
                    "class": "com.jd.jdd.vision.ocr.message.KeyValueObject",
                    "value": "沈良有",
                    "key": "situation_value",
                    "extended": {

                    }
                },
                {
                    "class": "com.jd.jdd.vision.ocr.message.KeyValueObject",
                    "value": "单独所有",
                    "key": "situation_value",
                    "extended": {

                    }
                },
                {
                    "class": "com.jd.jdd.vision.ocr.message.KeyValueObject",
                    "value": "2011-07-11",
                    "key": "date_value",
                    "extended": {

                    }
                },
                {
                    "class": "com.jd.jdd.vision.ocr.message.KeyValueObject",
                    "value": "房改房",
                    "key": "nature_value",
                    "extended": {

                    }
                },
                {
                    "class": "com.jd.jdd.vision.ocr.message.KeyValueObject",
                    "value": "商业",
                    "key": "purposes_value",
                    "extended": {

                    }
                },
                {
                    "class": "com.jd.jdd.vision.ocr.message.KeyValueObject",
                    "value": "22",
                    "key": "floors_value",
                    "extended": {

                    }
                },
                {
                    "class": "com.jd.jdd.vision.ocr.message.KeyValueObject",
                    "value": "131.94",
                    "key": "area_value",
                    "extended": {

                    }
                },
                {
                    "class": "com.jd.jdd.vision.ocr.message.KeyValueObject",
                    "value": "125.81",
                    "key": "Internal_area_value",
                    "extended": {

                    }
                },
                {
                    "class": "com.jd.jdd.vision.ocr.message.KeyValueObject",
                    "value": "国有出让",
                    "key": "method_of_land_value",
                    "extended": {

                    }
                },
                {
                    "class": "com.jd.jdd.vision.ocr.message.KeyValueObject",
                    "value": "2024-01-08",
                    "key": "date_value",
                    "extended": {

                    }
                },
                {
                    "class": "com.jd.jdd.vision.ocr.message.KeyValueObject",
                    "value": "天津西青区全境大寺镇龙腾花园20号楼404",
                    "key": "address_value",
                    "extended": {

                    }
                }
            ]
        },
        "class": "com.jd.jr.facecloud.algplat.export.dto.ocr.GeneralRecognitionAlgResp"
    },
    "class": "com.jd.jr.face.business.platfrom.exprot.dto.resp.ocr.PropOwnerCertRecognitionResp",
    "serialNo": "1598547146344-172025157194-181093",
    "timestamp": 1646723783452
}
```
