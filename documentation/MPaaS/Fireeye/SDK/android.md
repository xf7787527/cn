# 行为分析-Android-接入文档

## 1. 系统环境
组件SDK支持Android 4.4 （api 19）及以上系统

## 2. 接入指南
从可视化权限控制以及对宿主安装包大小影响方面考量，目前火眼SDK拆分两种，包含可视化圈选 (huoyan-visualtrace)的sdk和非可视化圈选(huoyan-trace)的sdk。两者使用方式无区别，可以无 缝切换。 

|  | 可视化圈圈选SDK | 自动埋点SDK |
| --- | --- | --- |
| 版本 | 2.0.3 | 2.0.3 |
| 大小 | 271KB | 235KB |
| 全自动埋点 | 支持 | 支持 |
| 配置文件拉取 | 支持 | 支持 |
| 白名单配置 | 支持 | 支持 |
| 可视化圈选 | 支持 | 不支持 |

## 3. 集成流程

### 3.1 手动集成的方式引入
通过将对应的aar文件放入项目app libs包下的方式引入:(根据实际情况引入不同的sdk) 

在应用目录(app)下的build.gradle中声明使用该SDK 

``` groovy
dependencies {
// 引入libs目录下的所有jar
compile fileTree(dir: ‘libs’, include: [‘*.jar’]) 
debugImplementation(name: “huoyan-visualtrace-2.0.3”, ext: ‘aar’) 
releaseImplementation(name: “huoyan-trace-2.0.3”, ext: ‘aar’) 
} 
```

### 3.2 通过maven仓库依赖方式接入(推荐)

1. 在工程build.gradle下添加nexus私服仓库地址

``` groovy
allprojects {
    repositories {
        maven { url "https://nexus.mpaas.jdcloud.com/repository/jdd-releases/" }
    }
}
```



2. 主module build.gradle中引入

``` groovy
    // 采用maven依赖的方式
    // debug下自动引 入可视化圈选功能的sdk
    // com.xxx.huoyan 详细由部署方提供
    debugImplementation ‘com.xxx.huoyan:huoyan-trace:2.0.3’
    // release自动引入去掉 可视化圈选功能的sdk 
    releaseImplementation ‘com.xxx.huoyan:huoyan-trace:2.0.3’
```

其他依赖

```groovy

implementation 'com.google.code.gson:gson:2.7'
```

### 3.3 权限

```xml
<uses-permission android:name="android.permission.RECEIVE_BOOT_COMPLETED" />
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
```

### 3.4 配置混淆

```xml
# 安卓四大组件不混淆
-keep public class * extends android.app.Activity
-keep class * extends android.support.v4.app.Fragment -keep class * extends android.app.Fragment
-keep class * extends android.support.v4.app.Fragment { 
}
-keepclassmembers class * extends android.content.Context { 
public void *(android.view.View); 
public void *(android.view.MenuItem); } 
-keepclassmembers class * extends android.app.Activity { public void *(android.view.View); 
} 
# 自定义控件
-keep public class * extends android.view.View { 
public <init>(android.content.Context);
public <init>(android.content.Context, android.util.AttributeSet); public <init>(android.content.Context, android.util.AttributeSet, int); public void set*(…); 
} 
-keep class * extends android.widget.AdapterView { 
*; } 
# 火眼SDK
-keep class com.jdd.huoyan.** {*;}
-dontwarn com.jdd.huoyan.**
-keep class com.litesuits.orm.** {*;}

```

Ps:如果使用自动埋点时，有其他自定义view组件，也需要添加到混淆配置中 

### 3.5 SDK初始化

#### 3.5.1 原生接入

纯原生Android代码 在应用程序初始化时调用，建议放在application的onCreate方法中 

```java
// 传入Context上下文 
JDDHuoYan.getInstance(this)
        // 配置host(后面不加/) 
        .setHost(“https://xxx.xxx.xxx.xxx:xxxx”)
        // 默认debug开启日志 release包会强制 关闭日志    
        .setDebugEnable(BuildConfig.DEBUG)
        // 应用渠道
        .setAppChannel("渠道一")
        // 是否开启自动埋点 默认关闭
        .setAutoTrack(true)
        // 用户ID 可自由接入宿主app用户id 
        .setDeviceID(“deviceid”)
        //设备ID
        .setUserId("用户名")
        // 上报数量 每次上报数量
        .setBatchReportCount(3, 3, 3)
        // 上报间隔 各种网络情况下上报间隔
        .setReportIntervalSeconds(10, 10, 10)
        // 额外参数(额外参数针对每一次上报 均生效)
        .setExtraParams(createExtendParmas())
        // 在控制后台申请的key和sign
        .setAppKeyAndToken(key, sign)
        //该方法最后调用
        .start();
```

#### 3.5.2 RN端接入(如未使用RN，则忽略)

原生混合RN代码(RN端代码需要在编译前引入对应的脚本) 如果宿主应用使用了RN混合开发，需要在Application初始化的时候引入RN的Packages类，具体如下: 

在实现ReactNativeHost对象的getPackages方法中加入 new JDHuoyanPackage()即可。 

```java
public class App extends Application implements ReactApplication {

    private final ReactNativeHost mReactNativeHost = new ReactNativeHost(this) {
        @Override
        protected List<ReactPackage> getPackages() {
            return Arrays.<ReactPackage>asList(
                    new MainReactPackage()
                    , new JDHuoyanPackage()//增加此处Package即可，其他可按照自身项目接入RN方式处理
            );
        }
    };

    @Override
    public ReactNativeHost getReactNativeHost() {
      return mReactNativeHost;
    }
 }
```




## 4. 基础功能



### 4.1 调用事件埋点 

```java
/**
* 事件埋点 
*
* @param eventId 事件ID
* @param paramJson 参数，json格式字符串，可以为null */ 
JDDHuoYan.getInstance().onEvent(String eventID,String paramJson); 
```
或 

```java
// 参数同上，兼容之前版本 
StaticAPI.onEvent(String eventID,String paramJson); 
```

### 4.2 埋点界面 

```java
/**
* ⻚面PV埋点，在Activity 的onResume()中调用，必须与 onPageEnd成对调用 *
* @param activity ⻚面上下文
*/ 
// Activity 
JDDHuoYan.getInstance().onPageBegin(Activity activity); 
// 退出时
JDDHuoYan.getInstance().onPageEnd(Activity activity); 
// Fragment 
JDDHuoYan.getInstance().onPageBegin(Fragment fragment); JDDHuoYan.getInstance().onPageEnd(Fragment fragment); 
```
或 

```java
/**
    * ⻚面PV埋点，在Activity 的onResume()中调用，必须与 onPageEnd成对调用
    *
    * @param activity ⻚面上下文
    * @param name 界面名称，建议使用 fragment.getClass().getSimpleName() */
// 兼容旧版本
StaticAPI.onPageEnd(Activity activity, String name); 
StaticAPI.onPageBegin(Activity activity, String name);
// Fragment
StaticAPI.onPageBegin(fragment.getActivity(), fragment.getClass().getSimpleName());

StaticAPI.onPageEnd(fragment.getActivity(), fragment.getClass().getSimpleName());
```

## 5. 高级功能

无

## 6.隐私政策合规

为了保证您的App顺利通过检测，结合当前监管关注重点，我们制作了SDK初始化合规方案。熟悉监管要求，掌握合规操作流程，拒绝App被下架。

### 合规三步走

#### 1.您需要确保App有《隐私政策》，并且在用户首次启动App时就弹出《隐私政策》取得用户同意。

#### 2.您务必告知用户您选择火眼SDK服务，请在《隐私政策》中增加如下参考条款：

“我们的产品集成火眼SDK，火眼SDK需要采集设备标识符(IMEI/Mac/android ID/IDFA/OPENUDID/GUID、SIM 卡 IMSI 信息)，用于唯一标识设备，以便为提供埋点服务的唯一标识；通过获取存储读写权限用来存储埋点数据”

#### 3.您务必严格遵守如下初始化步骤，确保用户同意《隐私政策》之后，再初始化火眼SDK。

【1】在Applicaiton.onCreate函数中加入逻辑判断，用户没有同意《隐私政策》之前，先不调用SDK初始化。

【2】确保App首次冷启动时，在用户阅读您的《隐私政策》并取得用户授权之后，才调用正式初始化函数。

【3】一旦App获取到《隐私政策》的用户授权，后续的App冷启动，开发者应该保证在Applicaiton.onCreate函数中调用预初始化函数(授权后初始化函数必须调用，不能遗漏)。


