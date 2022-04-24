# 危险动作识别

## 一、接口描述

### 1. 功能描述

危险动作识别 (video danger recognition) API 为用户提供危险动作识别功能， 用户上传一段视频，返回识别结果，目前可识别的危险行为种类为八种，包括: 抓捕, 行凶, 爆炸, 斗殴, 普通行为, 商店扒窃, 偷盗, 暴力破坏公物

### 2. 能力说明：

输入视频为人物的行为视频，不能提供其他类型的视频， 视频最好为无文字或无水印。

### 3. 接口数据要求：

- 视频格式：MP4， avi
- 视频文件大小：小于10M

### 4. 接口使用：

使用接口前，需要先完成API的下单购买，然后可使用已经封装好的SDK/参照[接口鉴权](https://aidoc.jd.com/user/auth.html)规则进行相应开发，整体流程详见 [接入流程](https://aidoc.jd.com/user/flow.html)

## 二、请求说明

### 1. 接口地址 ：

```
https://aiapi.jd.com/jdai/video_danger_recognition
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

业务请求参数

| 名称  | 类型   | 必填 | 示例值 | 描述     |
| ----- | ------ | ---- | ------ | -------- |
| video | String | 是   | 无     | 视频文件 |

#### （2）header请求参数

业务请求参数

| 名称         | 类型   | 必填 | 示例值                   | 描述       |
| ------------ | ------ | ---- | ------------------------ | ---------- |
| Content-Type | String | 是   | application/octet-stream | 请求头格式 |

#### （3）body请求参数

业务请求参数

| 名称 | 类型   | 必填 | 示例值 | 描述     |
| ---- | ------ | ---- | ------ | -------- |
| 无   | binary | 是   | 无     | 视频文件 |

### 4、请求代码示例

建议您使用我们提供的SDK进行调用，SDK获取及调用方式详见本页一接口描述中的4接口使用

## 三、返回说明

### 1、返回参数

#### （1）公共返回参数

| 名称          | 类型    | 示例值        | 描述                                                         |
| ------------- | ------- | ------------- | ------------------------------------------------------------ |
| code          | string  | 10000         | 参见下方错误码-系统级错误码                                  |
| charge        | boolean | false 或 true | false：不扣费， true：扣费                                   |
| remainTimes   | long    | 1305          | 剩余调用 IMG_FILE_SIZE_MAX: 2097152 # # max accepted IMG filesize (2M=1024*1024*2)次数；免费api：每天剩余调用次数；收费api：剩余次数；无限制时为-1 |
| remainSeconds | long    | 1223456       | 剩余调用时间（s）；免费api：-1；收费api：剩余调用时间；无限制时为-1 |
| msg           | string  | 查询成功      | 参见下方错误码-系统级错误码数                                |
| result        | object  | {...}         | 查询结果                                                     |

#### （2）业务返回参数

| 名称                | 类型   | 示例值                                                       | 描述                                              |
| ------------------- | ------ | ------------------------------------------------------------ | ------------------------------------------------- |
| code                | int    | 0                                                            | 参照四、错误码-业务错误码                         |
| danger_action_class | string | 抓捕(Arrest)                                                 | 返回危险动作识别结果                              |
| message             | string | Success                                                      | 参照四、错误码-业务错误码                         |
| task_id             | string | Arrest003_x264_seg_2020-10-19-16-10-43-07048d9a229bd4596a42058cbfb39883 | task_id，任务ID, 由video名称，上传时间，md5码组成 |
| used_time           | int    | 613                                                          | 每一个视频处理花费的时间，单位为毫秒              |

#### （3）返回参数 danger_action_class 枚举：



| 中文         | 英文                | 中（英）文                    |
| ------------ | ------------------- | ----------------------------- |
| 抓捕         | Arrest              | 抓捕(Arrest)                  |
| 行凶         | Assault             | 行凶(Assault)                 |
| 爆炸         | Explosion           | 爆炸(Explosion)               |
| 斗殴         | Fighting            | 斗殴(Fighting)                |
| 普通行为     | Normal_Videos_event | 普通行为(Normal_Videos_event) |
| 商店扒窃     | Shoplifting         | 商店扒窃(Shoplifting)         |
| 偷盗         | Stealing            | 偷盗(Stealing)                |
| 暴力破坏公物 | Vandalism           | 暴力破坏公物(Vandalism)       |



### 2、返回示例

```
{
    "code": "10000",
    "charge": false,
    "remainTimes": 4998,
    "remainSeconds": -1,
    "msg": "查询成功",
    "result": {
               "code": 0,
               "danger_action_class": "抓捕(Arrest)",
               "message": "Success",
               "task_id": "test1_2020-10-19-17-40-52-07048d9a229bd4596a42058cbfb39883"，
               "used_time": 613
    }
}
```

## 四、错误码

### 1.系统级错误码

[详见返回码](https://aidoc.jd.com/user/returncode.html)

### 2.业务错误码



| 业务错误码（status） | message                                                      | 说明                                      |
| -------------------- | ------------------------------------------------------------ | ----------------------------------------- |
| 0                    | "Success"                                                    | 视频识别成功                              |
| 2000                 | "File error, unsupport video type"                           | 输入的视频文件格式不支持                  |
| 2001                 | "File error, can't read video file"                          | 输入的视频数据解析失败                    |
| 2002                 | "File error, video length limit exceeded"                    | 输入的视频文件大小超过限制                |
| 2003                 | "Request header Content-Type only allows application/octet-stream" | 请求头格式只支持 application/octet-stream |
| 5000                 | "Service error"                                              | 系统错误                                  |
| 5001                 | "Service busy"                                               | 系统忙                                    |

最大支持缓存的视频数量为20个， 当缓存视频数量大于20个之后会返回系统忙