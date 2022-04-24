# 人脸融合

## 一、接口描述

### 1. 功能描述

人脸融合（Face Morph）是将两幅输入人脸图片融合为一张输出人脸图片。 本API为用户提供人脸融合功能，输入两张图片，第一张为人脸用户图片(image_source)， 第二张为模板图片 (image_target)，输出为一张融合后的图像，其中的身份信息会更像用户图，而发型、背景等属性信息会跟模板图保持一致。

### 2. 能力说明：

输入图像限定为人脸图片。为获得最优融合效果，两张输入图片（用户图，模板图）场景应均为单人头像，而且头部需在输入图片的中间部分，并占比至少50%以上。用户图片可以为正脸或侧脸，模板图片要求必须为正脸图片。模板图非正脸， 多人头像，或占比较低的场景效果不能保证最优。如有需要可以考虑与[人像分割(selfie_segmentation)](https://git.jd.com/doc-neuhub/api-docs/blob/master/image/selfie_segmentation.md)联合使用。

### 3. 接口数据要求：

- 图片格式：base64编码
- 图片类型：JPG, JPEG, PNG
- 图片文件大小：最小 50*50 像素，最大 2048*2048 像素之间
- 图片大小：图片小于2M

### 4. 接口使用：

进入京东智联云控制台-账号管理-Access Key管理，创建并获取Access Key。整体流程详见 [调用方法](https://docs.jdcloud.com/cn/common-declaration/api/call-methods) 。

## 二、请求说明

### 1. 接口地址 ：

```
https://aiapi.jdcloud.com/jdai/face_morph
```

### 2. 请求方式：

```
 post
```

### 3. 请求参数

#### （1）query请求参数

公共请求参数

| 名称      | 类型   | 必填 | 示例值                           | 描述                                           |
| --------- | ------ | ---- | -------------------------------- | ---------------------------------------------- |
| appkey    | string | 是   | 80d2b762ecb86593f9668526920f46c  | 您的appkey，可在买家中心控制台中获             |
| timestamp | long   | 是   | 1541491668060                    | 请求的时间戳，精确到毫秒，timestamp有效期5分钟 |
| sign      | string | 是   | 2e148773a0337a8f2200ba90d445f083 | 签名，根据规则MD5(sectetkey+timestamp)         |

#### （2）body请求参数

业务请求参数

| 名称 | 类型   | 必填 | 示例值                                                       | 描述                 |
| ---- | ------ | ---- | ------------------------------------------------------------ | -------------------- |
| 无   | string | 是   | Python列表(List), List中每个entry为图像Base64编码值，去掉图片头"data:image/png;base64,", [{"image_source": "RgABAQA...", "image_target": "JCQgKDB..."}, ...{"image_source": "LDBkSEw...", "image_target": "4AAQSkZ..."}] （由于过长，不给出完全示例） | 图像base64编码的列表 |

### 4、请求代码示例

建议您使用我们提供的SDK进行调用，SDK获取及调用方式详见本页一接口描述中的4接口使用

## 三、返回说明

### 1、返回参数

#### （1）公共返回参数

| 名称          | 类型    | 示例值        | 描述                                                         |
| ------------- | ------- | ------------- | ------------------------------------------------------------ |
| code          | string  | 10000         | 参见下方错误码-系统级错误码                                  |
| charge        | boolean | false 或 true | false：不扣费， true：扣费                                   |
| remainTimes   | long    | 1305          | 剩余调用次数；免费api：每天剩余调用次数；收费api：剩余次数；无限制时为-1 |
| remainSeconds | long    | 1223456       | 剩余调用时间（s）；免费api：-1；收费api：剩余调用时间；无限制时为-1 |
| msg           | string  | 查询成功      | 参见下方错误码-系统级错误码数                                |
| result        | object  | {...}         | 查询结果                                                     |

#### （2）业务返回参数

| 名称      | 类型   | 示例值              | 描述                           |
| --------- | ------ | ------------------- | ------------------------------ |
| status    | int    | 200                 | 参照四、错误码-业务错误码      |
| message   | string | OK                  | 参照四、错误码-业务错误码      |
| image     | string | iVBORw0KGgoAAAANSUh | 返回融合图像的base64编码       |
| used_time | int    | 79                  | 整个请求花费的时间，单位为毫秒 |

### 2、返回示例

```
{
    "code": "10000",
    "charge": false,
    "remainTimes": 4998,
    "remainSeconds": -1,
    "msg": "查询成功",
    "result": {
               "message":"ok ",
               "status": 200,
               "used_time": 79 
               "image": "iVBORw0KGgoAAAANSUh..."
    }
}
```

## 四、错误码

### 1.系统级错误码

[详见返回码](https://aidoc.jd.com/user/returncode.html)

### 2.业务错误码

| 业务错误码（status） | message                                                      | 说明                                     |
| -------------------- | ------------------------------------------------------------ | ---------------------------------------- |
| 1002                 | "parameter error, both \"image_source\" and \"image_target\" are required" | 缺少必要参数                             |
| 1003                 | "invalid \"image_source\" or \"image_target\" base64 data"   | base64图像解析失败                       |
| 1004                 | "incorrect \"image_source\" or \"image_target\" size"        | 图像大小超过限制                         |
| 1005                 | "not valid json string"                                      | 非法的json字符串                         |
| 1006                 | "other error"                                                | 其他错误                                 |
| 1007                 | "\"image_source\" or \"image_target\" format error"          | 图像格式错误                             |
| 201                  | "input images do not contain proper faces"                   | 输入人脸图片人脸不合规, 比如模板图非正脸 |