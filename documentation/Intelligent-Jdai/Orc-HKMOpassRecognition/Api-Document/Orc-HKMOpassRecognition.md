# 港澳通行证识别


## 描述
港澳通行证识别接口

## 请求方式

POST

## 请求地址

```apl
https://aiapi.jdcloud.com/jdai/entryPermitRecognition
```



## 请求参数

|名称|类型|是否必需|参数说明|
|---|---|---|---|
| serialNo | string | N      | 请求流水号, 不传接口自动生成                                 |
| imageItem | Object | Y | 图片信息 |
| cardType | string | N | 港澳通行证类型 正反面【“front”，“back”】, 若未知传"unknown" |

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

| 参数名称  | 参数类型             | 是否必填 | 参数说明                              |
| :-------- | :------------------- | :------- | :------------------------------------ |
| code      | int                  |          | 返回code码0:成功                      |
| msg       | string               |          | msg                                   |
| serialNo  | string               |          | 交互的流水号                          |
| cardType  | String               |          | 港澳通行证类型 正面：front 反面：back |
| frontInfo | EntryPermitFrontInfo |          | 正面信息cardType为front时有信息       |
| backInfo  | EntryPermitBackInfo  |          | 反面信息cardType为back时有信息        |

## 字段AirplaneItineraryInfo的内容说明

| 参数名称   | 参数类型            | 是否必填 | 参数说明                 |
| :--------- | :------------------ | :------- | :----------------------- |
| 参数名称   | 参数类型            | 是否必填 | 参数说明                 |
| smallId    | String              | 否       | 短id号（位于证件右上方） |
| name       | String              | 否       | 姓名                     |
| pinyin     | String              | 否       | 姓名拼音                 |
| birthdate  | String              | 否       | 出生日期                 |
| sex        | String              | 否       | 性别                     |
| valideDate | String              | 否       | 有效期限                 |
| issue      | String              | 否       | 签发机关                 |
| place      | String              | 否       | 签发地点                 |
| longId     | String              | 否       | 长id号（位于证件下方）   |
| extended   | Map<String, Object> | 否       | 预留扩展字段             |

字段EntryPermitBackInfo的内容说明：

| 参数名称   | 参数类型            | 是否必填 | 参数说明                                        |
| :--------- | :------------------ | :------- | :---------------------------------------------- |
| 参数名称   | 参数类型            | 是否必填 | 参数说明                                        |
| cardId     | String              | 否       | id（位于证件左侧，可能不存在）                  |
| typeHk     | String              | 否       | 种类（往来香港签注）                            |
| timesHk    | String              | 否       | 往返有效次数（往来香港签注）                    |
| dateHk     | String              | 否       | 有效期（往来香港签注）                          |
| noteHk     | String              | 否       | 备注（往来香港签注）                            |
| codeHk     | String              | 否       | code码（位于香港签注二维码下方）                |
| typeMacao  | String              | 否       | 种类（往来澳门签注）                            |
| timesMacao | String              | 否       | 往返有效次数（往来澳门签注）                    |
| dateMacao  | String              | 否       | 有效期（往来澳门签注）                          |
| noteMacao  | String              | 否       | 备注（往来澳门签注）                            |
| codeMacao  | String              | 否       | code码（位于澳门签注二维码下方）                |
| keyPs      | String              | 否       | 提示（预存指纹信息(R1L1VHM)，可按规定自助通关） |
| extended   | Map<String, Object> | 否       | 预留扩展字段                                    |

## 请求参数示例

```json
{
    "imageItem": {
        "encryptionType": "NON",
        "imgBase64": "图片base64",
        "valid": true
    },
    "imageType": "jpg",
    "serialNo": "1598547146344-172025157194"
}

```



