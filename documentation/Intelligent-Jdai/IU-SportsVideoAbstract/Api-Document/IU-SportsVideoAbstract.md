# 体育视频摘要

体育视频摘要服务支持用户上传一段足球比赛视频，生成并返回该段足球比赛的精彩集锦。目前仅支持足球赛事视频剪辑，后续将会支持更多视频内容自动剪辑。

# 视频上传接口

## 一、接口描述

### 1.功能描述

用于用户上传需要剪辑的视频至体育视频摘要服务。

### 2.能力描述

当前支持上传一段足球比赛的特写镜头视频，生成该视频的精彩片段。

### 3.接口数据要求：

> 1. 视频格式：mp4，avi
> 2. 视频长度要求：不限制上传视频的长度，但系统最多只读取视频的前十分钟进行处理
> 3. 本测试版系统最大支持缓存的视频数量为5个，当视频数量大于5个之后会返回系统忙。不限制上传视频的长度，但是在视频处理时最高只考虑视频的前10min，生成的精彩集锦最长为5min

### 4.接口使用

平台为每个API提供试用体验服务，您在AI市场选择“免费试用”规格下单后，即可开始体验业内领先的人工智能API服务。免费试用服务具有调用量、QPS限制，如需更高性能的API服务，可以提交咨询工单，联系京东AI扩容购买。在获得使用权限后，您可使用已经封装好的SDK/参照[接口鉴权](https://aidoc.jd.com/user/auth.html)规则进行相应开发，整体流程详见 [接入流程](https://aidoc.jd.com/user/flow.html)

## 二、请求说明

### 1.接口地址

```
https://aiapi.jd.com/jdai/upload_soccer_video
```

### 2.请求方式

```
POST
```

### 3.请求参数

#### (1) Query请求参数

公共请求参数

| 名称      | 类型   | 必填 | 示例值                           | 描述                                           |
| --------- | ------ | ---- | -------------------------------- | ---------------------------------------------- |
| appkey    | String | 是   | 80d2b762ecb86593f9668526920f46c  | 您的appkey，可在买家中心控制台中获取           |
| timestamp | long   | 是   | 1541491668060                    | 请求的时间戳，精确到毫秒，timestamp有效期5分钟 |
| sign      | String | 是   | 2e148773a0337a8f2200ba90d445f083 | 签名，根据规则MD5(sectetkey+timestamp)         |
| video     | String | 是   | 无                               | 视频文件名                                     |

#### (2) Header请求参数

业务请求参数

|     key      |  type  |           value            |
| :----------: | :----: | :------------------------: |
| Content-Type | string | 'application/octet-stream' |

#### (3) Body请求参数

| 名称 | 类型   | 必填 | 示例值 | 描述     |
| ---- | ------ | ---- | ------ | -------- |
| 无   | binary | 是   | 无     | 视频文件 |

确认支持的视频格式包括：mp4，avi。

### 4.请求代码示例

建议您使用我们提供的SDK进行调用，SDK获取及调用方式详见本页一接口描述中的4接口使用

## 三、返回说明

### 1.返回参数

#### (1) 公共返回参数

| 名称          | 类型    | 示例值        | 描述                                                         |
| ------------- | ------- | ------------- | ------------------------------------------------------------ |
| code          | string  | 1000          | 参见下方错误码-系统级错误码                                  |
| charge        | boolean | false 或 true | false：不扣费， true：扣费                                   |
| remainTimes   | long    | 1305          | 剩余调用次数；免费api：每天剩余调用次数；收费api：剩余次数；无限制时为-1 |
| remainSeconds | long    | 1223456       | 剩余调用时间（s）；免费api：-1；收费api：剩余调用时间；无限制时为-1 |
| msg           | string  | 查询成功      | 参见下方错误码-系统级错误码                                  |
| result        | object  | {...}         | 查询结果                                                     |

#### (2) 业务返回参数

result参数信息

|   key   |  type  |                value                 |
| :-----: | :----: | :----------------------------------: |
|  code   |  int   |                  0                   |
| messgae | string |               "Sucess"               |
| task_id | string | '2020-09-18-dassdasdasjiojonsidnisa' |

### 2.返回示例

```
{
    "code": "10000",
    "charge": true,
    "remain": 497,
    "remainTimes": 497,
    "remainSeconds": -1,
    "msg": "查询成功,扣费",
    "result": {
        "code": 0,
        "message": "Success",
        "task_id": "2020-10-30-09-01-19-d7cfdc3ca054d12ea92a4d31fe447770"
    }
}
```

## 四、状态码

### 1.系统级状态码

[详见返回码](https://aidoc.jd.com/user/returncode.html)

### 2.业务级状态码

| code |              message              |               说明               |
| :--: | :-------------------------------: | :------------------------------: |
|  0   |              Sucess               | 调用成功，视频上传成功，开始剪辑 |
| 2000 | File error, unsupport video type  |     输入的视频文件格式不支持     |
| 2001 | File error, can't read video file |      输入的视频数据解析失败      |
| 5000 |           Service error           |             系统错误             |
| 5001 |           Service busy            |              系统忙              |

# 视频剪辑状态查询接口

## 一、接口描述

### 1.功能描述

用于用户查询剪辑状态，并获取最终阶级视频的下载连接

### 2.能力描述

提供用户依据视频上传接口返回的任务id查询视频剪辑状态获取视频剪辑结果的能力。

## 二、请求说明

### 1.接口地址

```
https://aiapi.jd.com/jdai/video_editor_status
```

### 2.请求方式

```
POST
```

### 3.请求参数

#### (1) Query请求参数

公共请求参数

| 名称      | 类型   | 必填 | 示例值                           | 描述                                           |
| --------- | ------ | ---- | -------------------------------- | ---------------------------------------------- |
| appkey    | String | 是   | 80d2b762ecb86593f9668526920f46c  | 您的appkey，可在买家中心控制台中获取           |
| timestamp | long   | 是   | 1541491668060                    | 请求的时间戳，精确到毫秒，timestamp有效期5分钟 |
| sign      | String | 是   | 2e148773a0337a8f2200ba90d445f083 | 签名，根据规则MD5(sectetkey+timestamp)，       |

#### (2) Header请求参数

业务请求参数

|     key      |  type  |       value        |
| :----------: | :----: | :----------------: |
| Content-Type | string | 'application/json' |

#### (3) Body请求参数

业务请求参数

|   key   |  type  |                value                 |
| :-----: | :----: | :----------------------------------: |
| task_id | string | '2020-09-18-dassdasdasjiojonsidnisa' |

### 4.请求代码示例

建议您使用我们提供的SDK进行调用，SDK获取及调用方式详见本页一接口描述中的4接口使用

## 三、返回说明

### 1、返回参数

#### (1) 公共返回参数

| 名称          | 类型    | 示例值        | 描述                                                         |
| ------------- | ------- | ------------- | ------------------------------------------------------------ |
| code          | string  | 1000          | 参见下方错误码-系统级错误码                                  |
| charge        | boolean | false 或 true | false：不扣费， true：扣费                                   |
| remainTimes   | long    | 1305          | 剩余调用次数；免费api：每天剩余调用次数；收费api：剩余次数；无限制时为-1 |
| remainSeconds | long    | 1223456       | 剩余调用时间（s）；免费api：-1；收费api：剩余调用时间；无限制时为-1 |
| msg           | string  | 查询成功      | 参见下方错误码-系统级错误码                                  |
| result        | object  | {...}         | 查询结果                                                     |

#### (2) 业务返回参数

result参数信息

|      key      |  type  |             value             |
| :-----------: | :----: | :---------------------------: |
|     code      |  int   |               0               |
|    message    | string |           "Finish"            |
| progress_rate |  int   |              100              |
| editor_result | string | "http://storage.jd.com/XXXXX" |

只有当code为0，editor_result字段才会有值，值为剪辑之后视频的下载链接。

### 2.返回值示例

```
{
    "code": "10000",
    "charge": true,
    "remain": 496,
    "remainTimes": 496,
    "remainSeconds": -1,
    "msg": "查询成功,扣费",
    "result": {
        "code": 1001,
        "message": "Not find error, input task_id not exist"
    }
}
```

## 四、状态码

### 1.系统级状态码

[详见返回码](https://aidoc.jd.com/user/returncode.html)

### 2.业务级状态码

| code |                     message                      |                  说明                   |
| :--: | :----------------------------------------------: | :-------------------------------------: |
|  0   |                      Finish                      |              视频剪辑完成               |
| 1000 |          Key error, 'task_id' not exist          |          输入参数中没有task_id          |
| 1001 |     Not find error, input task_id not exist      |           输入的task_id不存在           |
| 1002 |    File error, input video file decode error     |        输入的视频无法被正常解析         |
| 2000 |      Content error, unsupport video content      |     输入的视频被判定为不是足球视频      |
| 2001 | Content error, can't find useful highlight clips |     输入的视频未找到可用的精彩片段      |
| 3000 |                    Processing                    | 视频剪辑中，进度可通过progress_rate获得 |
| 5000 |                  Service error                   |                系统错误                 |