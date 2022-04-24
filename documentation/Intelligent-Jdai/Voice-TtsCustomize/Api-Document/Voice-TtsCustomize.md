# 语音合成声音定制

## 一、接口描述

### 1. 功能描述

此系统仅需要用户按照指定的文本提供录音数据（pcm），提交到京东云服务后，系统会自动完成模型训练，并完成服务部署，用户可迅速使用自己定制的语音合成服务。

### 2. 接口数据要求：

- 文本仅支持UTF-8格式
- 文本长度不能超过1000个字符（包含标点）
- 音频数据使用pcm格式，单声道，16-bits，采样率：16000Hz
- 支持语音合成标记语言 (SSML)

### 3. 接口使用：

进入京东智联云控制台-账号管理-Access Key管理，创建并获取Access Key。整体流程详见 [调用方法](https://docs.jdcloud.com/cn/common-declaration/api/call-methods) 。

## 二、请求说明

### 1.合成特色音频

#### 1.1. 接口地址 ：

```
https://aiapi.jdcloud.com/jdai/ai_tts_economic_daily
```

#### 1.2. 请求方式：

```
post
```

#### 1.3. 请求参数

#### （1）query请求参数

公共请求参数

| 名称      | 类型   | 必填 | 示例值                           | 描述                                           |
| --------- | ------ | ---- | -------------------------------- | ---------------------------------------------- |
| appkey    | string | 是   | 80d2b762ecb86593f9668526920f46c  | 您的appkey，可在买家中心控制台中获             |
| timestamp | long   | 是   | 1541491668060                    | 请求的时间戳，精确到毫秒，timestamp有效期5分钟 |
| sign      | string | 是   | 2e148773a0337a8f2200ba90d445f083 | 签名，根据规则MD5(sectetkey,timestamp)         |

#### （2）header请求参数

业务请求参数

| 名称          | 类型   | 必填 | 示例值                                                       | 描述                                                         |
| ------------- | ------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Authorization | string | 是   | Bearer eyJhbGciOiJIUzUxMiJ9XXXX                              | 用户登陆后获取的token，【Bearer 】这个字段要保留，Bearer后有一个空格 |
| Route-Key     | string | 是   | jdtts                                                        | 用户路由信息，以用户名及模型ID的组合：userName_modelID       |
| Service-Type  | string | 是   | synthesis                                                    | 服务类型，这里设置固定值synthesis                            |
| Request-Id    | string | 是   | 65845428-de85-11e8-9517-040973d59a1e                         | 请求语音串标识码。由客户端生成，代表完整的语音识别请求过程，需要注意： - 需要全局唯一 - 对于同一次合成请求Request-Id需要保持一致 - 每个不同的合成请求都要新生成Request-Id，若多次请求使用同一个将会产生不可预知的错误。  生成方法: - libuuid 库可以直接生成。Android 及 iOS 也有相关的生成函数。 |
| Sequence-Id   | int    | 是   | 1                                                            | 文本分段传输的分段号 -1表示非流式，一次性合成音频并返回。 1表示一次新的流式请求开始，分段合成音频返回，发送第二次请求获取第二段数据时Sequence-Id递增并可以不带text文本。 |
| Protocol      | int    | 是   | 1                                                            | 通信协议版本号，这里设置固定值1                              |
| Net-State     | int    | 是   | 1                                                            | 客户端网络状态：1:WIFI，2:移动，3:联通，4:电信，5:其他       |
| Applicator    | int    | 是   | 1                                                            | 应用者，SDK 会提供给不同的应用者(渠道，例如：内部业务(0)，外部业务(1)) |
| Property      | string | 是   | {"platform": "Linux", "version": "0.0.0.1", "parameters": {"aue": "1", "vol": "2.0", "sr": "24000", "sp": "1.0", "tim": "0", "tte": "1"}} | 属性信息，json格式，platform和version为通用属性，parameters字段必填，其中的参数可选，Property允许用户同一个请求的不同包都携带该头，但是建议只在第一包携带 |

- Property参数

| 名称       | 类型   | 必填 | 示例值                                                       | 描述                                                         |
| ---------- | ------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| platform   | string | 是   | Android&Pixel&7.1                                            | 字符串类型，各平台的机型信息，格式为：{平台}&{机型}&{系统版本号} - 平台：Android，iOS，Linux，Windows - 机型：设备的机型名称，如Pixel，iPhoneX等 - 系统版本号：设备系统版本，如2.3.3，4.2.1等 |
| version    | string | 是   | 1.0.0                                                        | 字符串类型，客户端版本号                                     |
| parameters | string | 是   | {"aue": "1", "vol": "2.0", "sr": "24000", "sp": "1.0", "tim": "0", "tte": "1"} | TTS参数                                                      |
|            |        |      |                                                              |                                                              |

- parameters参数

| 名称 | 类型   | 必填 | 示例值 | 描述                                                         |
| ---- | ------ | ---- | ------ | ------------------------------------------------------------ |
| tte  | int    | 是   | 1      | 文本编码格式 1:UTF-8 (目前仅支持UTF-8格式)                   |
| aue  | int    | 是   | 1      | 音频编码格式（默认值：0） 0：wav 1：pcm 2：opus              |
| tim  | int    | 是   | 0      | 模型ID, 通过训练状态接口获取                                 |
| vol  | string | 是   | 2.0    | 音量（默认值：2.0） 取值范围：[0.1, 10.0]                    |
| sp   | string | 是   | 1.0    | 语速（默认值：1.0） 取值范围：[0.5, 2.0]                     |
| sr   | int    | 是   | 24000  | 采样率（默认值：24000） wav和pcm支持4k到24k的采样率 opus支持8k 12k 16k 和24k的采样率 |

#### （3）body请求参数

业务请求参数

| 类型   | 示例值       | 描述                                              |
| ------ | ------------ | ------------------------------------------------- |
| string | 你好，京东！ | 放置要合成的文本，长度不能超过1024字节，UTF-8编码 |

#### 1.4、请求代码示例

```
curl https://aiapi.jd.com/jdai/tts_customize?appkey=68D8FB1BB8E415F1AC8090F527C28241&timestamp=1607050386070&sign=3d3ac6df6befcef25b4b269d2329b514 -v -H 'Service-Type:synthesis' -H "Authorization:Bearer eyJhbGciOiJIUzUxMiJ9XXXX" -H 'Route-Key:JDAI-TTS' -H 'Application-Id:123' -H 'user-id:456' -H 'Request-Id:56a847e6-84c0-4c01-bf4b-d566f2d2dd12' -H 'Sequence-Id:1' -H 'Protocol:v2.0' -H 'Net-State:2' -H 'Applicator:0' -H 'Property:{"platform" : "Linux","version" : "0.0.0.1","parameters": {"tte": 1,"tim":300,"vol":2.0,"sp":1.0,"sr":16000,"aue":1}}' -X POST  -d "京东语音智能"
```

#### 1.5 成功返回值示例

```
{
    "code":"10000",
    "charge":true,
    "remainTimes":4984,
    "remainSeconds":32768246,
    "msg":"查询成功,扣费",
    "result":{
        "status":0,
        "message":"ok",
        "request_id":"a72ead09-9533-4744-9204-578723257579",
        "index":16,
        "progress":1,
        "audio":"BBEEEDYPHA7oDA4MAAv4CRQJrgcuBrwEXXXXXXXXXXXXXXXXXXXX"
    }
}
```

#### 1.6 result返回值说明

| 状态码     | 示例值                               | 描述                         |
| ---------- | ------------------------------------ | ---------------------------- |
| status     | 0                                    | 详情请参照【合成服务错误码】 |
| message    | ok                                   | 错误码描述                   |
| request_id | a72ead09-9533-4744-9204-578723257579 | 请求session的ID              |
| index      | 16                                   | 请求session的索引值          |