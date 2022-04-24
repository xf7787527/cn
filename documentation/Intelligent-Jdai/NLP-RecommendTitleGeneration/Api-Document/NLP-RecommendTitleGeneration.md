# 种草标题

## 一、接口描述

### 1. 功能描述

根据输入的sku智能生成多个种草标题

### 2. 接口使用

进入京东智联云控制台-账号管理-Access Key管理，创建并获取Access Key。整体流程详见 [调用方法](https://docs.jdcloud.com/cn/common-declaration/api/call-methods) 。

## 二、请求说明

### 1. 接口地址 ：

```
https://aiapi.jdcloud.com/jdai/nlpseed
```

### 2. 请求方式：

```
 get
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

| 名称       | 类型   | 必填 | 示例值      | 描述                                                         |
| ---------- | ------ | ---- | ----------- | ------------------------------------------------------------ |
| sku        | string | 是   | 72347231146 | sku                                                          |
| titleType  | int    | 是   | 1           | 标题类型：长标题/短标题，1：短标题（10字以内）；0：长标题（10~20字） |
| numContent | int    | 是   | 1           | 标题个数，上限为3                                            |

### 3、请求代码示例

```
curl -X GET 'https://aiapi.jd.com/jdai/nlpseed?sku=10020618051970&numContent=3'
```

## 三、返回说明

### 1、返回参数

#### （1）公共返回参数

| 名称          | 类型    | 示例值        | 描述                                                         |
| ------------- | ------- | ------------- | ------------------------------------------------------------ |
| code          | string  | 1000          | 参见下方错误码-系统级错误码                                  |
| charge        | boolean | false 或 true | false：不扣费， true：扣费                                   |
| remainTimes   | long    | 1305          | 剩余调用次数；免费api：每天剩余调用次数；收费api：剩余次数；无限制时为-1 |
| remainSeconds | long    | 1223456       | 剩余调用时间（s）；免费api：-1；收费api：剩余调用时间；无限制时为-1 |
| msg           | string  | 查询成功      | 参见下方错误码-系统级错误码数                                |
| result        | object  | {...}         | 查询结果                                                     |

#### （2）业务返回参数

| 名称      | 类型   | 示例值 | 描述                        |
| --------- | ------ | ------ | --------------------------- |
| code      | string | 500    | 参见下方错误码-系统级错误码 |
| msg       | string | 否     |                             |
| titleList | object | {...}  | 生成种草标题                |

data说明:

| 名称      | 类型    | 示例值           | 描述     |
| --------- | ------- | ---------------- | -------- |
| title     | string  | 满足你的味蕾需求 | 种草标题 |
| titleType | boolean | 1                | 标题类型 |
| score     | number  | 1                | 分数     |

### 2、返回示例

```
{
  "code": 200,
  "msg": null,
  "titleList": [
    {
      "title": "满足你的味蕾需求",
      "titleType": "0",
      "score": 1
    },
    {
      "title": "精选品质原材料",
      "titleType": "0",
      "score": 1
    },
    {
      "title": "保留水果原汁原味",
      "titleType": "0",
      "score": 1
    }
  ]
}
```

## 四、错误码

### 1.系统级错误码

[详见返回码](https://aidoc.jd.com/user/returncode.html)

### 2. 业务错误码

| 返回码（status） | message                      | 说明（message）      |
| ---------------- | ---------------------------- | -------------------- |
| 300211           | Data Confidence Error        | 基础数据获取失败     |
| 300212           | Data Confidence Error        | 基础数据获取失败     |
| 300213           | Data Confidence Error        | 基础数据获取失败     |
| 300214           | Data Confidence Error        | 基础数据获取失败     |
| 300215           | Data Confidence Error        | 基础数据获取失败     |
| 300216           | Data Confidence Error        | 基础数据获取失败     |
| 300111           | Data Confidence Error!       | 业务返回数据置信度低 |
| 300112           | Data Confidence Error!       | 业务返回数据置信度低 |
| 300261           | Data Confidence Error        | 基础数据获取失败     |
| 300262           | Data Confidence Error        | 基础数据获取失败     |
| 300263           | Data Confidence Error        | 基础数据获取失败     |
| 300264           | Data Confidence Error        | 基础数据获取失败     |
| 300265           | Data Confidence Error        | 基础数据获取失败     |
| 300266           | Data Confidence Error        | 基础数据获取失败     |
| 300267           | Data Confidence Error        | 基础数据获取失败     |
| 300268           | Data Confidence Error        | 基础数据获取失败     |
| 4003             | Permission denied            | 授权访问失败         |
| 3003             | Virtual Goods denied         | 虚拟商品             |
| 300218           | Data Confidence Error        | 种草标题错误         |
| 2001             | Category Not Support Error！ | 品类不支持           |
| 2001             | Category Not Support Error！ | 品类不支持           |
| 500001           |                              | 辅助sku太少          |
| 500002           |                              | 辅助sku太多          |