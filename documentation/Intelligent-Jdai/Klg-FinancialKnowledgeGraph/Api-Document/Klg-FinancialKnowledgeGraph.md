# 金融知识图谱  

## 一、接口描述

### 1. 功能描述

抽取文本中的实体（公司、产品等）、关系（业务、客户技术、供应商等关系）、指标值并构建出spo三元组知识图谱。

### 2. 接口使用：

进入京东智联云控制台-账号管理-Access Key管理，创建并获取Access Key。整体流程详见 [调用方法](https://docs.jdcloud.com/cn/common-declaration/api/call-methods) 。

## 二、请求说明

### 1. 接口地址 ：

```
https://aiapi.jdcloud.com/jdai/graph
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
| appkey    | String | 是   | 80d2b762ecb86593f9668526920f46c  | 您的appkey，可在买家中心控制台中获取           |
| timestamp | long   | 是   | 1541491668060                    | 请求的时间戳，精确到毫秒，timestamp有效期5分钟 |
| sign      | String | 是   | 2e148773a0337a8f2200ba90d445f083 | 签名，根据规则MD5(sectetkey+timestamp)         |

#### （2）header请求参数

业务请求参数

| 名称         | 类型   | 必填 | 示例值           | 描述                       |
| ------------ | ------ | ---- | ---------------- | -------------------------- |
| Content-Type | String | 是   | application/json | 表示请求JSON格式的文本信息 |

#### （3）body请求参数

业务请求参数

| 名称    | 类型   | 必填 | 示例值                                                       | 描述                             |
| ------- | ------ | ---- | ------------------------------------------------------------ | -------------------------------- |
| content | string | 是   | 阿莱德目前的零部件产品主要可分为三大类，分别为射频与透波防护器件、EMI及IP防护器件和电子导热散热器件。 | 输入文本（长度限制在5000字以内） |

### 4、请求代码示例

建议您使用我们提供的SDK进行调用，SDK获取及调用方式详见本页一接口描述中的4接口使用

## 三、返回说明

### 1、返回参数

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

result参数信息

| 名称    | 类型   | 示例值  | 描述                      |
| ------- | ------ | ------- | ------------------------- |
| code    | int    | 200     | 参照四、错误码-业务错误码 |
| message | string | SUCCESS | 状态码描述                |
| data    | json   | {...}   | 返回识别结果              |

data参数信息

| 名称                | 类型    | 示例值                           | 描述                                          |
| ------------------- | ------- | -------------------------------- | --------------------------------------------- |
| nodata              | boolean | false                            | 是否没有数据                                  |
| nodes               | list    |                                  | 节点                                          |
| - id                | string  | 14b653f1797e4db0b961eea833b03341 | 节点id                                        |
| - label             | string  | prod                             | 节点类别（prod:产品，corp：公司，spec：指标） |
| - properties        | json    |                                  | 属性                                          |
| -- domain           | string  |                                  | 所属公司                                      |
| -- name             | string  |                                  | 名称                                          |
| -- originalWord     | string  |                                  | 原始名称                                      |
| edges               | list    |                                  | 边                                            |
| - id                | string  | 1851070243--2014732324           | 边id                                          |
| - inVertexId        | string  | 894a576e78f847dab61c8346b13af077 | 入节点的id                                    |
| - outVertexId       | string  | b90d32cb9bc541e1b1de4d91a0cf1816 | 出节点的id                                    |
| - label             | string  | 业务                             | 边名称                                        |
| - properties        | json    |                                  | 属性                                          |
| -- originalSentence | string  |                                  | 所在原句                                      |

### 2、返回示例

```json
{
    "code": "10000",
    "charge": false,
    "remainTimes": 4998,
    "remainSeconds": -1,
    "msg": "查询成功",
    "result": {
        "data": {
            "nodes": [
                {
                    "id": "b90d32cb9bc541e1b1de4d91a0cf1816",
                    "label": "corp",
                    "properties": {
                        "domain": "阿莱德",
                        "name": "阿莱德",
                        "originalWord": "阿莱德",
                        "word": "阿莱德"
                    }
                },
                {
                    "id": "14b653f1797e4db0b961eea833b03341",
                    "label": "prod",
                    "properties": {
                        "domain": "阿莱德",
                        "name": "射频与透波防护器件",
                        "originalWord": "射频与透波防护器件",
                        "word": "射频与透波防护器件"
                    }
                },
                {
                    "id": "894a576e78f847dab61c8346b13af077",
                    "label": "prod",
                    "properties": {
                        "domain": "阿莱德",
                        "name": "EMI及IP防护器件",
                        "originalWord": "EMI及IP防护器件",
                        "word": "EMI及IP防护器件"
                    }
                },
                {
                    "id": "b3c097e0ad7d42ac937dc4fb03c4552e",
                    "label": "prod",
                    "properties": {
                        "domain": "阿莱德",
                        "name": "电子导热散热器件",
                        "originalWord": "电子导热散热器件",
                        "word": "电子导热散热器件"
                    }
                }
            ],
            "edges": [
                {
                    "id": "1851070243--2014732324",
                    "inVertexId": "894a576e78f847dab61c8346b13af077",
                    "outVertexId": "b90d32cb9bc541e1b1de4d91a0cf1816",
                    "label": "业务",
                    "properties": {}
                },
                {
                    "id": "1851070243-950830530",
                    "inVertexId": "14b653f1797e4db0b961eea833b03341",
                    "outVertexId": "b90d32cb9bc541e1b1de4d91a0cf1816",
                    "label": "业务",
                    "properties": {}
                },
                {
                    "id": "1851070243--1031202062",
                    "inVertexId": "b3c097e0ad7d42ac937dc4fb03c4552e",
                    "outVertexId": "b90d32cb9bc541e1b1de4d91a0cf1816",
                    "label": "业务",
                    "properties": {}
                }
            ],
            "nodata": false
        },
        "code": 200,
        "message": "SUCCESS",
        "success": true
    }
}
```

## 四、错误码

### 1.系统级错误码

[详见返回码](https://aidoc.jd.com/user/returncode.html)

### 2.业务错误码

| 业务错误码（code） | message          | 说明           |
| ------------------ | ---------------- | -------------- |
| 200                | SUCCESS          | 成功           |
| 12001              | Content empty    | 输入的文本为空 |
| 12002              | Content too long | 文章内容太长   |
| 12004              | Server error     | 程序内部错误   |