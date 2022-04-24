# 地址解析

## 一、接口描述

### 1. 功能描述

有效识别文本中的地址信息，并按省、市、区、街道、社区、小区、楼栋、单元等详细地址的格式结构化输出。

### 2. 接口使用：

进入京东智联云控制台-账号管理-Access Key管理，创建并获取Access Key。整体流程详见 [调用方法](https://docs.jdcloud.com/cn/common-declaration/api/call-methods) 。

## 二、请求说明

### 1. 接口地址 ：

```
https://aiapi.jdcloud.com/jdai/nlp_address
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

| 类型     | 必填 | 示例值                                                       | 描述     |
| -------- | ---- | ------------------------------------------------------------ | -------- |
| String[] | 是   | ["快递地址是清远市清城区石角镇美林湖大东路口佰仹公司", "深圳市前海深港合作区前湾一路1号A栋201室（入驻深圳市前海商务秘书有限公司）"] | 输入文本 |

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
| data    | list   | {...}   | 返回识别结果              |

data参数信息

| 名称         | 类型   | 示例值   | 描述                             |
| ------------ | ------ | -------- | -------------------------------- |
| province     | string | 山东省   | 省/自治区                        |
| city         | list   | 济南市   | 市/州                            |
| country      | string | 历下区   | 区/县                            |
| town         | string | 运河街道 | 镇/乡/街道/街道办事处/经济开发区 |
| village      | string |          | 村/社区/居民委员会               |
| street       | string | 东风西路 | 路/大道/道/大街/街/巷            |
| streetNumber | string | 29号     | 街道门牌号                       |
| housingState | string | 历下小区 | 居民小区/工业园区                |
| building     | string | 6号楼    | 楼号                             |
| unit         | string | 2单元    | 单元号                           |
| floor        | string | 11楼     | 楼层                             |
| room         | string | 403      | 房间号/楼层区号/商铺号           |
| landMark     | string |          | 标志物/建筑物                    |
| reference    | string |          | 参照物/路标                      |
| location     | string |          | 距离、方位                       |
| poi          | string | 佰仹公司 | 具体的地址实体名                 |
| other        | string |          | 其他                             |

### 2、返回示例

```json
{
  "code": "10000",
  "charge": false,
  "remainTimes": 4998,
  "remainSeconds": -1,
  "msg": "查询成功",
  "result": {
    "data": [
    {
      "province": "",
      "city": "深圳市、深圳市",
      "country": "前海深港合作区",
      "town": "",
      "village": "",
      "street": "前湾一路",
      "streetNumber": "1号",
      "housingState": "",
      "building": "A栋",
      "unit": "",
      "floor": "",
      "room": "201室",
      "landMark": "",
      "reference": "",
      "location": "",
      "poi": "",
      "other": ""
    }
  ],
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

| 业务错误码（code） | message             | 说明         |
| ------------------ | ------------------- | ------------ |
| 200                | SUCCESS             | 成功         |
| 14000              | Address Model Error | 地址解析失败 |
| 14001              | no request body     | 请求参数无值 |