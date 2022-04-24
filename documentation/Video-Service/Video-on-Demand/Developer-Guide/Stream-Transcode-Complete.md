# 视频转码回调

## 事件类型

视频某个转码任务完成时，会触发 StreamTranscodeComplete 事件。

## 回调内容

|字段名称|字段类型| 字段描述                                         |
|--- |--- |----------------------------------------------|
|eventType|String| 事件类型，特定值为 StreamTranscodeComplete            |
|eventTime|String| 事件时间，为 UTC 时间的字符串表示，格式为 yyyy-MM-ddTHH:mm:ssZ |
|taskId|Long| 任务ID                                         |
|templateId|Long| 转码模板ID                                       |
|videoId|String| 视频ID                                         |
|title|String| 视频标题                                         |
|fileUrl|String| 转码文件地址                                       |
|format|String| 转码文件格式                                       |
|size|Long| 转码文件大小，单位 Byte                               |
|duration|Float| 转码视频时长，单位秒                                   |
|fps|String| 转码视频帧率                                       |
|bitrate|String| 转码视频码率                                       |
|width|Integer| 转码视频画面宽度，单位 px                               |
|height|Integer| 转码视频画面高度，单位 px                               |
|definition|String| 转码视频清晰度规格                                    |
|shotImages|Array(String)| 转码附带截图                                       |
|status|String| 转码任务状态                                       |
|errorCode|String| 错误码。视频转码出错的时候，会有该字段表示错误码                     |
|errorMessage|String| 错误消息。视频转码出错的时候，会有该字段表示错误信息                   |

## 内容示例

> 说明：<br>
> 当前仅视频点播仅支持 HTTP 回调，故回调内容即为 HTTP POST Request Body

```json
{
  "bitrate": "969177",
  "definition": "HD",
  "duration": 10.618,
  "eventTime": "2020-07-28T10:04:51.465Z",
  "eventType": "StreamTranscodeComplete",
  "fileUrl": "https://s3.cn-north-1.jcloudcs.com/vod-storage-72757/vod/product/28373149/959/1a541c2f55024fae92741e53d604e8f0.mp4",
  "format": "mp4",
  "fps": "25.000",
  "height": 1280,
  "shotImages": [
    "https://s3.cn-north-1.jcloudcs.com/vod-storage-72757/img/2020/28102587/1/img1.jpg",
    "https://s3.cn-north-1.jcloudcs.com/vod-storage-72757/img/2020/28102587/1/img2.jpg",
    "https://s3.cn-north-1.jcloudcs.com/vod-storage-72757/img/2020/28102587/1/img3.jpg",
    "https://s3.cn-north-1.jcloudcs.com/vod-storage-72757/img/2020/28102587/1/img4.jpg",
    "https://s3.cn-north-1.jcloudcs.com/vod-storage-72757/img/2020/28102587/1/img5.jpg",
    "https://s3.cn-north-1.jcloudcs.com/vod-storage-72757/img/2020/28102587/1/img6.jpg",
    "https://s3.cn-north-1.jcloudcs.com/vod-storage-72757/img/2020/28102587/1/img7.jpg",
    "https://s3.cn-north-1.jcloudcs.com/vod-storage-72757/img/2020/28102587/1/img8.jpg"
  ],
  "size": 1370362,
  "status": "success",
  "taskId": 959,
  "templateId": 958,
  "title": "1595930586758_filter-YiJianMeiHuamp4.mp4",
  "videoId": "e4b7e7d6-fe92-40b0-9870-fa10bb4d8ed5",
  "width": 596
}
```
