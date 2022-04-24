# 网关-Android-接入文档

## 1. 系统环境

组件SDK支持Android 4.4 （api 19）及以上系统



## 2. 接入指南

网关SDK，可以作为网络库使用，统一处理SDK对接网关的处理逻辑，业务SDK只需要集成网关SDK即可。



## 3. 集成流程


### 3.1 在工程根目录的build.gradle中添加如下

```groovy
allprojects {
    repositories {
        maven { url "https://nexus.mpaas.jdcloud.com/repository/jdd-releases/" }
    }
}
```

### 3.2 build.gradle中添加sdk依赖

```groovy
dependencies {
    implementation 'com.jdt.libs:gateway:1.0.1'
}
```

### 3.3 网关SDK初始化
``` java
JDDGWUtils.init("host", new OnHandleListener() {
    @Override
    public GwRequestData handleRequestData(BzRequestData data) {
        String body = data.bodyStr;
        Map<String, String> headers = data.headers;
        GwRequestData retData = new GwRequestData();
        // 发起请求之前，对接网关的通用处理，比如添加特殊header、报文加密
        retData.headers = headers;
        retData.body = body;
        return retData;
    }

    @Override
    public BzResponseData handleResponseData(GwResponseData gwResponseData) {
        BzResponseData retData = new BzResponseData();
        // 发起请求回来之后通用处理，比如报文解密
        retData.body = gwResponseData.body;
        retData.headers = gwResponseData.headers;
        return retData;
    }
});
```


### 3.4 配置混淆
``` java
# JDDGateway
-keep class com.jdd.gateway.** {*;}
-dontwarn com.jdd.gateway.**

# JRNetwork
-keep class com.jd.jrapp.library.libnetwork.** {*;}
-dontwarn com.jd.jrapp.library.libnetwork.**
-keep class com.jd.jrapp.library.libnetworkbase.** {*;}
-dontwarn com.jd.jrapp.library.libnetworkbase.** 
-keep class com.jd.jrapp.library.libnetworkcore.okhttp.** {*;}
-dontwarn com.jd.jrapp.library.libnetworkcore.okhttp.**

# OkHttp3
-keep class com.squareup.okhttp3.** { *;}
-dontwarn com.squareup.okhttp3.**
-dontwarn okio.**
```

## 4. 基础功能


#### 4.1 网络请求、响应

示例如下：

```java
JDDRequest.JDDBuilder builder = new JDDRequest.JDDBuilder();
builder.url("/服务端提供的接口");
builder.appID("服务端提供的APPId");

Map<String, String> headParams = new HashMap<>(0);
builder.headers(headParams);

Map<String, Object> msgBody = new HashMap<>(3);
msgBody.put("fund_CompanyId", "80000222");

builder.post(msgBody);
new JDDHttpClient(MainActivity.this)
        .sendRequest(builder.build(), new IJDDResponseCallback() {
    @Override
    public void onFailure(ICall call, int statusCode, String message, Exception e) {

    }
    @Override
    public void onResponse(ICall call, final JDDResponse response) throws IOException {
        if (response.isSuccessful()) {
            runOnUiThread(new Runnable() {
                @Override
                public void run() {
                    String result =
                            response.body().getString();
                    mTextView.setText(String.format("返回结果：\n%s", result));
                }
            });

        }
    }
});
```



#### 4.2 备注


1.appID为配置网关接口时生成，为必传项

2.网关测试接口需要配置hosts,由部署方提供



## 5. 高级功能
无