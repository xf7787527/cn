# 商品信息抽取

## 一、接口描述

### 1. 功能描述

从商品描述中抽取商品相关属性

### 2. 接口使用

进入京东智联云控制台-账号管理-Access Key管理，创建并获取Access Key。整体流程详见 [调用方法](https://docs.jdcloud.com/cn/common-declaration/api/call-methods) 。

## 二、请求说明

### 1. 接口地址 ：

```
https://aiapi.jdcloud.com/jdai/nlppredictbysku
```

### 2. 请求方式：

```
 GET
```

### 3. 请求参数

#### （1）query请求参数

公共请求参数

| 名称      | 类型   | 必填 | 示例值                           | 描述                                           |
| --------- | ------ | ---- | -------------------------------- | ---------------------------------------------- |
| appkey    | string | 是   | 80d2b762ecb86593f9668526920f46c  | 您的appkey，可在买家中心控制台中获             |
| timestamp | long   | 是   | 1541491668060                    | 请求的时间戳，精确到毫秒，timestamp有效期5分钟 |
| sign      | string | 是   | 2e148773a0337a8f2200ba90d445f083 | 签名，根据规则MD5(sectetkey+timestamp)         |

#### （2）业务请求参数

业务请求参数

| 名称 | 类型   | 必填 | 示例值       | 描述    |
| ---- | ------ | ---- | ------------ | ------- |
| sku  | string | 是   | 100011202392 | 商品sku |

### 3、请求代码示例

```
https://aiapi.jd.com/jdai/nlppredictbysku?sku=100011202392
```

## 三、返回说明

### 1、返回参数

#### （1）公共返回参数

| 名称          | 类型    | 示例值        | 描述                                                         |
| ------------- | ------- | ------------- | ------------------------------------------------------------ |
| code          | string  | 1000          | 参见下方错误码-系统级错误码                                  |
| charge        | boolean | false 或 true | false：不扣费， true：扣费                                   |
| remain        | long    | 1305          | 剩余调用次数；免费api：每天剩余调用次数；收费api：剩余次数；无限制时为-1 |
| remainTimes   | long    | 1305          | 剩余调用次数；免费api：每天剩余调用次数；收费api：剩余次数；无限制时为-1 |
| remainSeconds | long    | 1223456       | 剩余调用时间（s）；免费api：-1；收费api：剩余调用时间；无限制时为-1 |
| msg           | string  | 查询成功      | 参见下方错误码-系统级错误码数                                |
| result        | object  | {...}         | 查询结果                                                     |

#### （2）业务返回参数

| 名称 | 类型   | 示例值 | 描述                        |
| ---- | ------ | ------ | --------------------------- |
| code | string | 1000   | 参见下方错误码-系统级错误码 |
| msg  | string | 否     |                             |
| data | object | []     | 输出内容                    |

data 参数说明

| 名称       | 类型   | 示例值                                             | 描述       |
| ---------- | ------ | -------------------------------------------------- | ---------- |
| sku        | long   | 100011202392                                       | 商品sku    |
| title      | string | Montblanc 万宝龙 大班软皮粒纹系列鲨鱼钥匙扣 124587 | 商品标题   |
| categoryId | 9191   | 否                                                 | 商品分类   |
| pairs      | object | []                                                 | 属性键值对 |

pairs 参数说明

| 名称      | 类型   | 示例值                                             | 描述       |
| --------- | ------ | -------------------------------------------------- | ---------- |
| attribute | string | 商品属性                                           | 属性值     |
| value     | string | Montblanc 万宝龙 大班软皮粒纹系列鲨鱼钥匙扣 124587 | 商品标题   |
| startPos  | int    | 0                                                  | 开始位置   |
| endPos    | int    | 结束位置                                           | 属性键值对 |
| modelType | string | 模型类型                                           | deep_model |

\### 2、返回示例 ``` { "code": 200, "data": { "sku": "100011202392", "title": "Montblanc 万宝龙 大班软皮粒纹系列鲨鱼钥匙扣 124587", "categoryId": "9191", "pairs": [ { "attribute": "品牌", "value": "Montblanc", "startPos": 0, "endPos": 9, "modelType": "deep_model" }, { "attribute": "品牌", "value": "万宝龙", "startPos": 10, "endPos": 13, "modelType": "deep_model" }, { "attribute": "产品词", "value": "钥匙扣", "startPos": 24, "endPos": 27, "modelType": "deep_model" } ] }, "msg": "请求成功" } ``` ## 四、错误码 ### 1.系统级错误码 [详见返回码](https://aidoc.jd.com/user/returncode.html) ### 2. 业务错误码

| 返回码（code） | message | 说明（message）  |
| -------------- | ------- | ---------------- |
| 500            |         | 模型解析数据失败 |
| 401            |         | 无权访问         |