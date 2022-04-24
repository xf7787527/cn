# 质量监控-Android-接入文档

## 1. 系统环境
组件SDK支持Android 4.4 （api 19）及以上系统

## 2. 接入指南
申请应用标识AppKey


## 3. 集成流程

### 3.1 在主工程的build.gradle文件中增加apm-plugin gradle plugin引用:
```  java
buildscript {
   repositories {
        maven { url "https://nexus.mpaas.jdcloud.com/repository/jdd-releases/" }
   }
   dependencies {
        classpath 'com.jdt.libs:apm-gradle-plugin:1.0.0'
   }
 }

 allprojects {
    repositories {
        maven { url "https://nexus.mpaas.jdcloud.com/repository/jdd-releases/" }
    }
}
```
### 3.2 在项目的build.gradle文件中增加如下代码:
``` Java
apply plugin: 'apm-gradle-plugin'

android {
   apmPluginConfig {
   // ApplicationClassName 必选，写上自己APP的applicationName的全路径
   applicationName = "yourApplicationPath"
   // 是否打印日志,可选,默认false
   debug = true
   // 是否打开网络库采集,可选,默认true
   openNetWorkTrack = true
   // 是否打开启动采集,可选,默认true
   openStartupTrack = true
   // 是否打开X5WebView,可选,默认false
   openX5WebViewTrack = false;
   // 是否打开WebView,可选,默认true
   openWebViewTrack = true;
   }
}

dependencies {
    api 'com.jdt.libs:apm:1.0.1'
}
```



### 3.3 配置权限

请在AndroidManifest.xml 设置如下权限：
``` java
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```
### 3.4 SDK初始化
``` java
ApmConfig.Builder apmConfigBuilder =  ApmConfig.newBuilder(app)
.uuidCallBack(
    new IAPMUuidCallBack() {
       @Override
       public String uuid() {
         // 必填，此处需要返回设备ID
         return deviceId;
       }
    }
)
.accountIdCallBack(
    new IAPMAccountIdCallBack() {
       @Override
       public String accountId() {
          // 必填，用户的登录账号或者pin，没有登录返回空串即可
          return accountId;
       }
    }
)
// appName 待私有化部署后，对接人提供
.appName("")
// 版本号.必填
.versionName("")
// 必填
.versionCode(String.valueOf(BuildConfig.RELEASE_VERSION))
// 渠道标识，非必填
.channel("")
// 必填，待私有化部署后，对接人提供
.initPassKey("")
// 上报数据是否加密
.dataEncrypt(false);

String[] crashStr = {
        "\\S+jd.\\S+",
};

// 以下可选是否开启Crash采集上报
CrashInitParameters params = new CrashInitParameters()
                    .addFilters(crashStr);
params.preTerminateMillis = 100L;
params.enableNativeCrashHandler = true;
params.enableJavaCrashHandler = true;
apmConfigBuilder.crashParameters(params);
APM.initialize(apmConfigBuilder.build());
```

### 3.5 混淆配置
``` java
-keep class com.jd.jrapp.library.sgm.** {*;}
```

## 4. 基础功能

### 4.1 启动监控

在主界面Activity(一般为启动页跳转后的页面或MainActivity)的类上增加注解 @StartupDone，确保Activity中包含有onCreate方法。
后台管理界面获取的数据如下图
![start](../../../../image/MPaas/APM/android/start.png)
参数说明：

|        字段       |              备注                    |
| :---------------  | :---------------------------------- |
|    启动耗时(ms)    |   app启动到首页准备OnCreate开始的时间   |
|   首页可见耗时(ms)  |      首页onCreate到第一帧渲染的时间     |

### 4.2 自定义数据监控

1.类名:

  com.jd.jrapp.library.sgm.ApmInstance

2.方法名:

  addErrorLogMonitor

例子：

``` java
ApmErrorLogMonitor apmErrorLogMonitor = new ApmErrorLogMonitor();
ApmInstance.getInstance().addErrorLogMonitor(apmErrorLogMonitor);
```

3.入参说明：

| 字段名          | 意义         | 是否必须                            |
| :------------ | :----------- | :----------------------------------|
| type          | 类型          |                是                  |
| location      | 位置          |               否                   |
| errorCode     | 错误码        |                是                  |
| errorMsg      | 错误原因       |                是                  |

4.后台配置方法：

应用概览-> 选中应用配置(编辑)->高级配置->错误日志类型(添加对应的错误日志ID和错误类型描述)

|        字段       |              备注                    |
| :---------------  | :---------------------------------- |
|    错误日志Id      |          跟入参的type值保持一致        |
|   错误日志类型名称  |          代表含义，可以自己定义         |

![error](../../../../image/MPaas/APM/android/errorLog.png)

## 5. 高级功能

暂无
