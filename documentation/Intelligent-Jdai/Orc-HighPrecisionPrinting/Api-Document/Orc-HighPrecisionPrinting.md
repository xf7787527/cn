# 通用印刷体高精度版


## 描述
通用印刷体高精度版



请求参数: 

| No.  | 字段     | 类型         | **是否必须** | 说明             | 备注                                                         |
| :--- | :------- | :----------- | :----------- | :--------------- | :----------------------------------------------------------- |
| 1    | token    | String       | 是           | 鉴权码           | 见 [接入步骤第2条](https://cf.jd.com/pages/viewpage.action?pageId=312087830) 申请token；默认 `"81d7b42d-95e6-48a5-955b-f4d84262218e"` |
| 2    | version  | String       | 否           | 版本号           | 默认v1.0                                                     |
| 3    | useCache | boolean      | 否           | 是否使用结果缓存 | 默认true                                                     |
| 4    | urls     | List<String> | 是           | url列表          | 最多8个，仅支持jpg、png、jpeg、bmp、webp格式                 |

**请求参数示例**

| 1 2 3 4 5 6 7 | #高速度ocr-serverserver = ‘http://g.jsf.jd.local/com.jd.cvp.vct.api.ocr.general.GeneralOcr/pro/recognize/1065909/jsf/20000'headers = {'content-type': 'application/json'}`data = json.dumps({` `  ``"token"``:``"81d7b42d-95e6-48a5-955b-f4d84262218e"``,` `  ``"urls"``:[` `    ``"jfs/t1/109940/35/580/298334/5df64bfbEea043f46/61a0830d9d43e894.jpg"``,` `    ``"jfs/t1/111229/40/12117/124215/5f098029Eaa9308f8/6494a1d1e06b1183.jpg"` `  ``]` `})``response = requests.post(server, data=data, headers=headers)` |
| ------------- | ------------------------------------------------------------ |
|               |                                                              |

#### 3. 通用高精度OCR接口

与高速度OCR接口相比，**仅server不同。**请求参数中对应替换server

**Request Server**: https://aiapi.jdcloud.com/jdai/generalPrintRecognition

#### 4. 返回参数

**Response**

| **No.** | **字段**  | **类型**           | 是否必选 | **说明**         | 备注                                                         |
| :------ | :-------- | :----------------- | :------- | :--------------- | :----------------------------------------------------------- |
| 1       | requestId | String             | 是       | 请求id           |                                                              |
| 2       | status    | int                | 是       | 状态码           | 见 [接口返回状态码.status](https://cf.jd.com/pages/viewpage.action?pageId=312092129) |
| 3       | message   | String             | 是       | 状态描述         | 见 [接口返回状态码.message](https://cf.jd.com/pages/viewpage.action?pageId=312092129) |
| 4       | data      | List<DetectResult> | 否       | 图片处理结果列表 | 结果顺序与入参urls顺序一致。为规避乱序风险，建议调用方得到结果后匹配url。 |

**DetectResult**

| **No.** | **字段** | **类型**           | 是否必选 | **说明**     | 备注                                                         |
| :------ | :------- | :----------------- | :------- | :----------- | :----------------------------------------------------------- |
| 1       | code     | int                | 是       | 状态码       | 见 [图片处理状态码.code](https://cf.jd.com/pages/viewpage.action?pageId=312092129) |
| 2       | message  | String             | 是       | 状态描述     | 见 [图片处理状态码.message](https://cf.jd.com/pages/viewpage.action?pageId=312092129) |
| 3       | url      | String             | 是       | 图片url      |                                                              |
| 4       | targets  | List<DetectTarget> | 否       | 识别结果列表 | 列表为空或长度为0表示无识别结果                              |

**DetectTarget**

| **No.** | **字段** | **类型** | 是否必选 | **说明**   | 备注              |
| :------ | :------- | :------- | :------- | :--------- | :---------------- |
| 1       | text     | String   | 是       | 识别的文本 |                   |
| 2       | score    | float    | 是       | 置信度     |                   |
| 3       | location | int[]    | 是       | 检测框位置 | 顶点宽高[x,y,w,h] |


**返回参数示例**

```
{`
`  ``"requestId"``:``"2fe1116b-8c32-4f12-b535-ca452197d141"``,`
`  ``"status"``:0,`
`  ``"message"``:``"成功"``,`
`  ``"data"``:[`
`    ``{`
`      ``"code"``:0,`
`      ``"message"``:``"success"``,`
`      ``"url"``:``"jfs/t1/109940/35/580/298334/5df64bfbEea043f46/61a0830d9d43e894.jpg"``,`
`      ``"targets"``:[`
`        ``{`
`          ``"text"``:``"识别举例1"``,`
`          ``"score"``:0.913,`
`          ``"location"``:[`
`            ``183,`
`            ``143,`
`            ``18,`
`            ``26`
`          ``]`
`        ``}`
`      ``]`
`    ``},`
`    ``{`
`      ``"code"``:0,`
`      ``"message"``:``"success"``,`
`      ``"url"``:``"jfs/t1/111229/40/12117/124215/5f098029Eaa9308f8/6494a1d1e06b1183.jpg"``,`
`      ``"targets"``:[`
`        ``{`
`          ``"text"``:``"识别举例2"``,`
`          ``"score"``:0.743,`
`          ``"location"``:[`
`            ``412,`
`            ``217,`
`            ``62,`
`            ``73`
`          ``]`
`        ``},`
`        ``{`
`          ``"text"``:``"识别举例3"``,,`
`          ``"score"``:0.960,`
`          ``"location"``:[`
`            ``174,`
`            ``245,`
`            ``45,`
`            ``60`
`          ``]`
`        ``}`
`      ``]`
`    ``}`
`  ``]`
`}
```