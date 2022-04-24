# 呼叫中心录音文件识别

## 一、接口描述

### 1. 功能描述

本api服务主要针对呼叫中心场景下录音的音频文件进行语音识别，是一个非实时的识别服务。用户可将待识别的录音文件基于http可访问的地址提交任务到服务，并通过查询接口获取识别结果。录音文件识别服务适合对录音文件进行质检分析，会议以及演讲内容进行识别总结等场景。

### 2. 能力说明

> 1. 录音文件需以http地址形式提交，且http地址是可访问的地址，不能是本地http地址。
> 2. 录音文件URL中只能使用域名，不能使用IP地址。
> 3. 用户提交的录音文件识别任务后，文件识别任务一般将在12小时内返回识别结果。
> 4. 录音文件识别服务分2个接口：
>    （1）先调用创建任务接口上传待识别音频文件URL地址并创建转写任务。
>    （2）轮询调用查询接口获取文件识别结果。
> 5. 支持中文普通话。

### 3. 录音文件要求

> 1. 建议的音频格式：wav、mp3、amr
> 2. 建议的音频采样率：8000 Hz（采样率跟模型领域相关）
> 3. 建议的声道数：单声道
> 4. 音频文件时长：支持5小时以内的录音文件识别
> 5. 音频文件大小：文件大小不能超过512MB

### 4. 接口使用

进入京东智联云控制台-账号管理-Access Key管理，创建并获取Access Key。整体流程详见 [调用方法](https://docs.jdcloud.com/cn/common-declaration/api/call-methods) 。

## 二、创建任务接口说明

### 1. 接口地址

```
https://aiapi.jdcloud.com/jdai/cc_fasr_create
```

### 2. 请求方式

```
post
```

### 3. 请求参数

#### （1）query 请求参数

公共请求参数

| 名称      | 类型   | 必填 | 示例值                           | 描述                                              |
| --------- | ------ | ---- | -------------------------------- | ------------------------------------------------- |
| appkey    | string | 是   | 80d2b762ecb86593f9668526920f46c  | 您的 appkey，可在买家中心控制台中获取             |
| timestamp | long   | 是   | 1541491668060                    | 请求的时间戳，精确到毫秒，timestamp 有效期 5 分钟 |
| sign      | string | 是   | 2e148773a0337a8f2200ba90d445f083 | 签名，根据规则MD5（secretkey + timestamp）        |

#### （2）body 请求参数

| 名称       | 类型   | 必填 | 示例值                                                       | 描述                                                         |
| ---------- | ------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| domain     | string | 是   | call_center                                                  | 语音识别模型， 可选项： - call_center，呼叫中心场景，需要使用 8000 Hz 采样率的音频 |
| format     | string | 是   | wav                                                          | 音频格式， 可选项： - wav - mp3 - amr                        |
| samplerate | int    | 是   | 8000                                                         | 音频采样率， 采样率需与所选模型匹配 - 8000                   |
| speech_url | string | 是   | http://voice.s3.cn-north-1.jdcloud-oss.com/tmp_audio/audio-00000.mp3 | 录音文件http地址，可采用京东云对象存储进行音频文件存储。     |

### 4. 请求代码示例

Python 3 示例程序如下：

```python
import requests
import json
import time
import uuid
import hashlib
from urllib.parse import urlencode
import sys
import importlib
importlib.reload(sys)

url = 'https://aiapi.jd.com/jdai/cc_fasr_create'

query = {
    'appkey':'your appkey',
    'timestamp':'',
    'sign':''
    }

filelink = 'http://voice.s3.cn-north-1.jdcloud-oss.com/tmp_audio/audio-00000.mp3'
secretkey = 'your secretkey'

body_param = {
    'format':'mp3',
    'samplerate': 8000,
    'domain':'call_center',
    'speech_url':filelink
    }


def test_single():
  query['timestamp'],query['sign'] = sign(secretkey)
  url_query = '?'.join([url, urlencode(query)])
  r = requests.post(url_query, data=json.dumps(body_param))
  print(r.text)

def sign(secretkey):
    m = hashlib.md5()
    nowTime = int(time.time() * 1000)
    before = secretkey + str(nowTime)
    m.update(before.encode('utf8'))
    return str(nowTime), m.hexdigest()

if __name__ == '__main__':
    test_single()
```

### 5. 返回参数

#### （1）公共返回参数

| 名称          | 类型    | 示例值        | 描述                                                         |
| ------------- | ------- | ------------- | ------------------------------------------------------------ |
| code          | string  | 1000          | 参见下方错误码-系统级错误码                                  |
| charge        | boolean | false 或 true | false：不扣费， true：扣费                                   |
| remainTimes   | long    | 1305          | 剩余调用次数；免费api：每天剩余调用次数；收费api：剩余次数；无限制时为-1 |
| remainSeconds | long    | 1223456       | 剩余调用时间（s）；免费api：-1；收费api：剩余调用时间；无限制时为-1 |
| msg           | string  | 查询成功      | 参见下方错误码-系统级错误码                                  |
| result        | object  | {...}         | 查询结果                                                     |

#### （2）业务返回参数

服务器返回的识别结果采用 JSON 格式：

| 名称       | 类型   | 示例值                               | 描述                                      |
| ---------- | ------ | ------------------------------------ | ----------------------------------------- |
| request_id | string | 56a847e6-84c0-4c01-bf4b-d566f2d2dd11 | 本次请求ID                                |
| status     | int    | 0                                    | 状态码                                    |
| message    | string | 语音数据为空                         | 错误信息，当status为非0错误码时可参考本项 |
| taskid     | string | 10a6edbc-a18e-574a-89b0-baf7358ece3e | 任务id，用于后续查询接口使用              |

### 6. 返回示例

```Json
{
    "code": "10000",
    "charge": false,
    "remainTimes": 4998,
    "remainSeconds": -1,
    "msg": "查询成功",
    "result": {
        "request_id": "c30b2ff0-9ffd-11ea-9ee8-fa163ef3b453",
        "status": 0,
        "message": "OK",
        "taskid": "10a6edbc-a18e-574a-89b0-baf7358ece3e"
    }
}
```

## 三、查询接口说明

通过创建任务接口创建转写任务后，可以用任务id定期轮询查询识别结果，一般12小时内会转写完成，识别结果默认保存72小时。

### 1. 接口地址

```
https://aiapi.jd.com/jdai/cc_fasr_query
```

### 2. 请求方式

```
post
```

### 3. 请求参数

#### （1）query 请求参数

公共请求参数

| 名称      | 类型   | 必填 | 示例值                           | 描述                                              |
| --------- | ------ | ---- | -------------------------------- | ------------------------------------------------- |
| appkey    | string | 是   | 80d2b762ecb86593f9668526920f46c  | 您的 appkey，可在买家中心控制台中获取             |
| timestamp | long   | 是   | 1541491668060                    | 请求的时间戳，精确到毫秒，timestamp 有效期 5 分钟 |
| sign      | string | 是   | 2e148773a0337a8f2200ba90d445f083 | 签名，根据规则MD5（secretkey + timestamp）        |

#### （2）body 请求参数

| 名称   | 类型   | 必填 | 示例值                               | 描述                                 |
| ------ | ------ | ---- | ------------------------------------ | ------------------------------------ |
| taskid | string | 是   | 10a6edbc-a18e-574a-89b0-baf7358ece3e | 任务id，创建任务时服务端返回的任务id |

### 4. 请求代码示例

Python 3 示例程序如下：

```python
import requests
import json
import time
import uuid
import hashlib
from urllib.parse import urlencode
import sys
import importlib
importlib.reload(sys)

url = 'https://aiapi.jd.com/jdai/cc_fasr_query'

query = {
    'appkey':'your appkey',
    'timestamp':'',
    'sign':''
    }

filelink = 'http://voice.s3.cn-north-1.jdcloud-oss.com/tmp_audio/audio-00000.mp3'
secretkey = 'your secretkey'

body_param = {
    'taskid':'10a6edbc-a18e-574a-89b0-baf7358ece3e',
    }


def test_single():
  query['timestamp'],query['sign'] = sign(secretkey)
  url_query = '?'.join([url, urlencode(query)])
  r = requests.post(url_query, data=json.dumps(body_param))
  print(r.text)

def sign(secretkey):
    m = hashlib.md5()
    nowTime = int(time.time() * 1000)
    before = secretkey + str(nowTime)
    m.update(before.encode('utf8'))
    return str(nowTime), m.hexdigest()

if __name__ == '__main__':
    test_single()
```

### 5. 返回参数

#### （1）公共返回参数

| 名称          | 类型    | 示例值        | 描述                                                         |
| ------------- | ------- | ------------- | ------------------------------------------------------------ |
| code          | string  | 1000          | 参见下方错误码-系统级错误码                                  |
| charge        | boolean | false 或 true | false：不扣费， true：扣费                                   |
| remainTimes   | long    | 1305          | 剩余调用次数；免费api：每天剩余调用次数；收费api：剩余次数；无限制时为-1 |
| remainSeconds | long    | 1223456       | 剩余调用时间（s）；免费api：-1；收费api：剩余调用时间；无限制时为-1 |
| msg           | string  | 查询成功      | 参见下方错误码-系统级错误码                                  |
| result        | object  | {...}         | 查询结果                                                     |

#### （2）业务返回参数

服务器返回的识别结果采用 JSON 格式：

| 名称         | 类型   | 示例值                               | 描述                                         |
| ------------ | ------ | ------------------------------------ | -------------------------------------------- |
| request_id   | string | 56a847e6-84c0-4c01-bf4b-d566f2d2dd11 | 本次请求ID                                   |
| status       | int    | 0                                    | 状态码                                       |
| message      | string | ok                                   | 错误信息，当status为非0错误码时可参考本项    |
| content      | object | {...}                                | 识别结果                                     |
| +taskid      | string | 10a6edbc-a18e-574a-89b0-baf7358ece3e | 任务id                                       |
| +task_status | string | WAITING                              | 任务状态，具体取值可参考错误码及任务状态章节 |
| +err_no      | int    | 20002                                | 任务执行失败错误码                           |
| +err_msg     | string | download audio failed!               | 任务执行失败错误信息                         |
| +sentences   | array  | [{},{}]                              | 按句子的识别结果                             |
| ++text       | string | 你好京东                             | 识别文本                                     |
| ++begin_time | int    | 1003                                 | 单位是毫秒                                   |
| ++end_time   | int    | 6124                                 | 单位是毫秒                                   |
| +task_result | string | 你好京东。                           | 识别结果文本                                 |

### 6. 返回示例

等待转写返回示例

```Json
{
    "code": "10000",
    "charge": false,
    "remainTimes": 4998,
    "remainSeconds": -1,
    "msg": "查询成功",
    "result": {
        "request_id": "a80431dc-9fff-11ea-af7e-fa163ef3b453",
        "status": 0,
        "message": "OK",
        "content": {
            "taskid": "10a6edbc-a18e-574a-89b0-baf7358ece3e",
            "task_status": "WAITING"
        }
    }
}
```

转写失败返回示例

```
{
    "code": "10000",
    "charge": false,
    "remainTimes": 4998,
    "remainSeconds": -1,
    "msg": "查询成功",
    "result": {
        "request_id": "0d28ff4a-a0d0-11ea-9fe4-fa163ef3b453",
        "status": 0,
        "message": "OK",
        "content": {
            "taskid": "195f5f5c-8143-5559-83f0-80a69bc917cb",
            "task_status": "FAILED",
            "err_no": 20002,
            "err_msg": "download audio failed!"
        }
    }
}
```

转写成功返回示例

```
{
    "code": "10000",
    "charge": false,
    "remainTimes": 4998,
    "remainSeconds": -1,
    "msg": "查询成功",
    "result": {
        "request_id": "00058c18-a001-11ea-b7fc-fa163ef3b453",
        "status": 0,
        "message": "OK",
        "content": {
            "taskid": "61cab300-ccf9-555e-9244-10019f758491",
            "task_status": "SUCCESS",
           "sentences": [{
                "text":"你好京东",
                "begin_time":1132,
                "end_time":5131
            }, 
            {
                "text":"我的物流到哪了",
                "begin_time":7132,
                "end_time":12131
            }],
            "task_result": "你好京东我的物流到哪了"
        }
    }
}
```

## 四、任务状态及错误码说明

### 1. 任务状态

| 任务状态取值（task_status） | 状态说明   |
| --------------------------- | ---------- |
| WAITING                     | 等待转写   |
| RUNNING                     | 转写进行中 |
| SUCCESS                     | 转写成功   |
| FAILED                      | 转写失败   |

### 2. 错误码

#### （1） 系统级错误码

[详见返回码](https://aidoc.jd.com/user/returncode.html)

#### （2） 业务错误码

##### 接口错误码

| 接口错误码（status） | message               | 说明                 |
| -------------------- | --------------------- | -------------------- |
| 10001                | "create task failed!" | 创建任务失败         |
| 10004                | "no task info!"       | 查询失败，无此任务id |
| 10005                | "param error!"        | 请求参数错误         |
| 10006                | "param type error!"   | 请求参数类型错误     |

##### 录音文件转写结果错误码

| 任务错误码（err_no） | err_msg                  | 说明                                             |
| -------------------- | ------------------------ | ------------------------------------------------ |
| 20001                | "internal error!"        | 任务内部错误                                     |
| 20002                | "download audio failed!" | 下载语音失败，请确认提交的音频文件http地址可访问 |
| 20003                | "audio format error!"    | 音频格式错误                                     |