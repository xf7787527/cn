## 货架商品检测

### 1.描述

密集场景下货架商品检测接口，根据请求的图片，检测出图片中货架上商品的目标框，并返回检测结果

### 2.接口地址

```
https://aiapi.jdcloud.com/jdai/detect_shelf_product
```

### 3.请求方式

```
POST
```

### 4. 接口使用：

进入京东智联云控制台-账号管理-Access Key管理，创建并获取Access Key。整体流程详见 [调用方法](https://docs.jdcloud.com/cn/common-declaration/api/call-methods) 。

### 5. 请求参数

#### （1）query请求参数

公共请求参数

| 名称      | 类型   | 必填 | 示例值                           | 描述                                           |
| --------- | ------ | ---- | -------------------------------- | ---------------------------------------------- |
| appkey    | string | 是   | 80d2b762ecb86593f9668526920f46c  | 您的appkey，可在买家中心控制台中获取           |
| timestamp | long   | 是   | 1541491668060                    | 请求的时间戳，精确到毫秒，timestamp有效期5分钟 |
| sign      | string | 是   | 2e148773a0337a8f2200ba90d445f083 | 签名，根据规则MD5(sectetkey+timestamp)，       |

#### （2）header请求参数

业务请求参数

| 名称         | 类型   | 必填 | 示例值                            | 描述                                       |
| ------------ | ------ | ---- | --------------------------------- | ------------------------------------------ |
| Content-Type | string | 是   | application/x-www-form-urlencoded | 标准编码格式，imgBase64="图像Base64编码值" |

#### （3）body请求参数

业务请求参数

| 名称      | 类型   | 必填 | 描述                                                         |
| --------- | ------ | ---- | ------------------------------------------------------------ |
| imgBase64 | string | 是   | 图像Base64编码值，去掉图片头"data:image/png;base64,"，imgBase64="/9j/4AAQSk..."（由于过长，不给出示例） |

```
python
    with open('test.png','rb') as f:
    base64_data = base64.b64encode(f.read())
    data = {
        'imgBase64':base64_data
        }
```

### 6.返回参数

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

|   名称    |  类型  |        示例值        |               描述               |
| :-------: | :----: | :------------------: | :------------------------------: |
| “status”  | string |         '0'          |            返回信息码            |
| "message" | string | 'Inference Succeed!' |             返回信息             |
| “bboxes”  |  list  |       [..,..,]       | 请求处理图片的检测目标框结果列表 |

bboxes 参数说明

|     名称     |  类型  |      示例值      |      描述      |
| :----------: | :----: | :--------------: | :------------: |
| “Confidence” | float  |     '0.992'      | 目标框的置信度 |
|    "bbox"    |  list  | [x1, y1, x2, y2] |   目标框坐标   |
| “class_name” | string |     'object'     |  目标框的类别  |

bbox 参数说明

| 名称 | 类型 | 示例值 |        描述        |
| :--: | :--: | :----: | :----------------: |
|  x1  | int  |   23   | 目标框左上角x坐标  |
|  y1  | int  |   43   | 目标框左上角y 坐标 |
|  x2  | int  |   56   | 目标框右下角x坐标  |
|  y2  | int  |   78   | 目标框右下角y坐标  |

错误码说明：

| 错误码（status） |      错误信息（message）      |
| :--------------: | :---------------------------: |
|       ’0‘        |     'Inference Succeed!'      |
|     '10002'      |  'base64 data is too large!'  |
|     '10004'      |     'base64 data error!'      |
|     '10005'      | 'input error! not supported!' |

#### (2) 返回示例

```
{
    "bboxes": [
        {
            "Confidence": 0.9920008182525635,
            "bbox": [
                479,
                1496,
                588,
                1667
            ],
            "class_name": "object"
        },
        {
            "Confidence": 0.9798628687858582,
            "bbox": [
                598,
                1428,
                707,
                1666
            ],
            "class_name": "object"
        },
        {
            "Confidence": 0.9729764461517334,
            "bbox": [
                363,
                1507,
                472,
                1669
            ],
            "class_name": "object"
        },
        ...
        ...
        ...
        {
            "Confidence": 0.5022118091583252,
            "bbox": [
                926,
                1834,
                993,
                1908
            ],
            "class_name": "object"
        }
    ],
    "message": "Inference Succeed!",
    "status": "0"
```

#### (3) 请求示例

```
with open(sys.argv[1],'rb') as f:
    base64_data = base64.b64encode(f.read())

request_data = {
        'imgBase64':base64_data
        }

results = requests.post(url = url, data = request_data)
result_dict = json.loads(results.content)
bboxes = result_dict['bboxes']
```