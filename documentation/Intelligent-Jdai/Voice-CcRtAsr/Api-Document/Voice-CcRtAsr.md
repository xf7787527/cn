# 呼叫中心实时语音识别

## 一、接口描述

### 1. 功能描述

对于长时间的语音，实时地将语音转换成文字，按句返回语音识别结果。

### 2. 能力说明

实时语音识别 API 专门针对呼叫中心场景进行了模型训练优化，以提高识别准确率。

### 3. 音频要求

> 1. 建议的音频格式：pcm
> 2. 建议的音频采样率：8000 Hz
> 3. 建议的声道数：单声道

### 4. 接口使用

进入京东智联云控制台-账号管理-Access Key管理，创建并获取Access Key。整体流程详见 [调用方法](https://docs.jdcloud.com/cn/common-declaration/api/call-methods) 。

## 二、请求说明

### 1. 接口地址

```
https://aiapi.jdcloud.com/jdai/cc_rt_asr
```

### 2. 请求方式

```
POST
```

### 3. 请求参数

#### （1）query 请求参数

公共请求参数

| 名称      | 类型   | 必填 | 示例值                           | 描述                                              |
| --------- | ------ | ---- | -------------------------------- | ------------------------------------------------- |
| appkey    | string | 是   | 80d2b762ecb86593f9668526920f46c  | 您的 appkey，可在买家中心控制台中获取             |
| timestamp | long   | 是   | 1541491668060                    | 请求的时间戳，精确到毫秒，timestamp 有效期 5 分钟 |
| sign      | string | 是   | 2e148773a0337a8f2200ba90d445f083 | 签名，根据规则MD5（secretkey + timestamp）        |

#### （2）header 请求参数

业务请求参数

| 名称           | 类型   | 必填 | 示例值                                | 描述                                                         |
| -------------- | ------ | ---- | ------------------------------------- | ------------------------------------------------------------ |
| Content-Type   | string | 是   | application/octet-stream              | 内容类型: 不可用的 Content-Type： - multipart/form-data - application/x-www-form-urlencoded |
| Domain         | string | 是   | call_center                           | 模型领域： - call_center，呼叫中心语音识别场景，需要使用 8000 Hz 采样率的音频 |
| Application-Id | string | 是   | *123456789                            | 产品ID： - 业务方应用名称，由业务方在客户端自行生成          |
| Request-Id     | string | 是   | *56a847e6-84c0-4c01-bf4b-d566f2d2dd11 | 请求ID： - *注意：示例值仅供参考，正式使用请务必通过 uuid 生成 - 对于同一次请求 Request-Id 需要保持一致，多次请求使用同一个将会产生不可预知的错误 |
| Sequence-Id    | int    | 是   | -1                                    | 语音传输分段号： - 从 1 开始依次递增，最后一段语音取负值，分为下述两种情况： 1. 在一个 Request-Id 中，上传整个音频文件（整包请求）时：填 -1 2. 在一个 Request-Id 中，音频文件分段上传（流式分包请求）时，遵循默认规则依次递增。例如：一次语音识别请求中，音频分 10 次上传，则 Sequence-Id 依次为：1,2,3,4,5,6,7,8,9,-10 |
| Asr-Protocol   | int    | 是   | 1                                     | 通信协议版本号： - 默认填 1                                  |
| Net-State      | int    | 是   | 2                                     | 客户端网络状态： - NETSTATE_NO_NETWORK = 0; - NETSTATE_NO_WIFI_MOBILE = 1; - NETSTATE_WIFI = 2; - NETSTATE_CDMA = 3; - NETSTATE_EDGE = 4; //移动 2.5G - NETSTATE_EVDO_0 =5; - NETSTATE_EVDO_A = 6; - NETSTATE_GPRS = 7; - NETSTATE_HSDPA = 8; //联通 3G - NETSTATE_HSPA = 9; - NETSTATE_HSUPA = 10; - NETSTATE_UMTS = 11; - NETSTATE_EHRPD = 12; - NETSTATE_EVDO_B = 13; - NETSTATE_HSPAP = 14; - NETSTATE_IDEN = 15; - NETSTATE_LTE = 16; - NETSTATE_UNKOWN_MOBILE = 20; |
| Applicator     | int    | 是   | 1                                     | 业务方信息： - 0：内部业务方 - 1：外部业务方                 |
| Property       | JSON   | 是   | {...}                                 | 语音识别请求参数： - 注意：如果 Sequence-Id 为 1 或 -1 时，则 Property 参数必填；其他情况下，该参数可选填 |

- Property 参数

| 名称     | 类型   | 必填 | 示例值           | 描述                                                         |
| -------- | ------ | ---- | ---------------- | ------------------------------------------------------------ |
| platform | string | 是   | Linux&Centos&7.3 | 平台信息： 格式：{系统信息}&{设备信息}&{系统版本号} - 系统信息：如 Android，iOS，Linux，Windows - 设备信息：如 Pixel 3，iPhone X 等 - 系统版本号：设备系统版本，如 2.3.3，4.2.1 等 - 示例：Android&Pixel 3&7.1；iOS&iPhone X&11.4.1 |
| version  | string | 是   | 0.0.0.1          | 客户端版本号                                                 |
| encode   | JSON   | 是   | {...}            | 音频参数                                                     |

- encode 参数

| 名称             | 类型   | 必填 | 示例值 | 描述                                                         |
| ---------------- | ------ | ---- | ------ | ------------------------------------------------------------ |
| channel          | int    | 是   | 1      | 音频声道数： - 只支持单声道音频，单声道填 1                  |
| format           | string | 是   | wav    | 音频格式： - 支持 wav，amr，mp3 格式                         |
| sample_rate      | int    | 是   | 8000   | 音频采样率： - 对于呼叫中心场景仅支持 8kHz，填 8000          |
| post_process     | int    | 否   | 0      | 数字后处理： - 0：根据服务端配置是否进行数字后处理 - 1：强制开启数字后处理（开启后，会把结果中的数字汉字转换成阿拉伯数字。例如，识别结果中的"一千"会转成"1000"） - -1：强制关闭数字后处理（关闭后，结果中的数字为汉字数字。例如，"一千"） |
| punc_end_process | int    | 否   | 0      | 最终结果标点符号处理： - 0：根据服务端配置是否增加标点符号 - 1：强制开启整句识别结果标点符号处理（开启后，会把最后整句的识别结果做标点处理。例如，"非常好。"） - -1：强制关闭整句识别结果标点符号处理（关闭后，最后整句的识别结果不会做标点处理。例如，"非常好"） |

#### （3）body 请求参数

填充待识别的音频数据（二进制）。 音频数据可按照自定义长度进行切分，按顺序分包上传，并与 header 请求参数中的 Sequence-Id 参数的顺序保持对应。

### 4. 请求代码示例

建议您使用我们提供的 SDK 进行调用，SDK 获取及调用方式详见本页接口描述中的 [4.接口使用](https://aidoc.jd.com/thirdDocs/7/8339f4d34ee648e7ae78c3faf0a0dbe2-618.html### 4. 接口使用)

Python：

```python
# 注意：
# audiofile：待识别的音频文件
# packagelen：音频切分长度
# python3

#coding=utf-8
import requests
import json
import sys
import uuid
import hashlib
from urllib.parse import urlencode
import time
import importlib
importlib.reload(sys)

url = 'https://aiapi.jd.com/jdai/cc_rt_asr'

encode = {
    'channel':1,
    'format':'wav',
    'sample_rate':8000,
    'punc_end_process':1,
    'post_process':1
}

Property = {
    'platform':'Linux&Centos&7.3',
    'version':'0.0.0.1',
    'encode':encode
}

query = {
    'appkey':'your appkey',
    'timestamp':'',
    'sign':''
    }

secretkey = 'your secretkey'

def test_single(audiofile, packagelen):
    query['timestamp'],query['sign'] = sign(secretkey)
    url_query = '?'.join([url, urlencode(query)])
    headers = {
        'Content-Type':'application/octet-stream',
        'Domain':'call_center',
        'Application-Id':'123456789',
        'Request-Id':str(uuid.uuid1()),
        'Sequence-Id':str(-1),
        'Asr-Protocol':str(1),
        'Net-State':str(2),
        'Applicator':str(1),
        'Property':json.dumps(Property)
    }
    seq = 1
    with open(audiofile, 'rb') as f:
        while True:
            body=f.read(int(packagelen))
            if not body or len(body) < int(packagelen):
                headers['Sequence-Id'] = str(-seq)
            else:
                headers['Sequence-Id'] = str(seq)
            print(headers)
            r = requests.post(url, headers=headers, data=body)
            print(r.text)
            seq += 1
            if not body or len(body) < int(packagelen):
                break

def sign(secretkey):
    m = hashlib.md5()
    nowTime = int(time.time() * 1000)
    before = secretkey + str(nowTime)
    m.update(before.encode('utf8'))
    return str(nowTime), m.hexdigest()

if __name__ == '__main__':
    audiofile = sys.argv[1] if len(sys.argv) > 2 else audiofile
    packagelen = sys.argv[2] if len(sys.argv) > 2 else packagelen
    test_single(audiofile, packagelen)
```

## 三、返回说明

### 1. 返回参数

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

| 名称        | 类型   | 示例值                                                   | 描述                               |
| ----------- | ------ | -------------------------------------------------------- | ---------------------------------- |
| request_id  | string | 56a847e6-84c0-4c01-bf4b-d566f2d2dd11                     | 请求ID                             |
| status      | int    | 0                                                        | 状态码                             |
| index       | int    | -1                                                       | 返回结果编号，负数表示全部最终结果 |
| message     | string | 语音数据为空                                             | 错误信息                           |
| content     | array  | [{"text":"你好 京东","start_time":1690,"end_time":3938}] | 识别结果，包含句子的起始结束时间   |
| +text       | string | 你好 京东                                                | 识别结果                           |
| +start_time | int    | 1690                                                     | 起始时间，单位毫秒                 |
| +end_time   | int    | 3938                                                     | 结束时间，单位毫秒                 |

### 2. 返回示例

```Json
{
    "code": "10000",
    "charge": false,
    "remainTimes": 4998,
    "remainSeconds": -1,
    "msg": "查询成功",
    "result": {
        "request_id": "56a847e6-84c0-4c01-bf4b-d566f2d2dd11",
        "status": 0,
        "index": -1,
        "message": "",
        "content": [
            {
                 "text": "你好 京东",
                    "start_time": 1690,
                    "end_time": 3938

            }
        ]
    }
}
```

## 四、错误码

### 1. 系统级错误码

[详见返回码](https://aidoc.jd.com/user/returncode.html)

### 2. 业务错误码

| 业务错误码（status） | message                                | 说明                                                         |
| -------------------- | -------------------------------------- | ------------------------------------------------------------ |
| 31001                | "speech data is empty."                | 语音数据为空                                                 |
| 31003                | "request params error."                | 请求参数出错，缺少 Request-Id、Sequence-Id 或 Application-Id 等。 |
| 31004                | "speech data file header error."       | 音频头部格式解析错误                                         |
| 31005                | "speech sample rate or channel error." | 音频采样率或通道数错误                                       |
| 31006                | "speech format error."                 | 音频格式错误                                                 |
| 32001                | "codec error."                         | 服务内部音频解码错误                                         |
| 32002                | "am server internal error."            | 服务内部 am-server 模块错误                                  |
| 32003                | "connect to decoder server error."     | 无法访问 decoder-server 服务                                 |
| 33001                | "decoder server internal error."       | 服务内部 decoder-server 模块错误                             |
| 33002                | "decoder invoke error."                | 服务内部语音识别解码失败                                     |