# 应用发布-Android-接入文档

## 1. 系统环境
android 支持最小版本4.4



## 2. 接入指南
1. 此SDK需要后台配合，可实现APP多维度灰度功能

2. 直接引入相关SDK ，待私有化部署后，对接人提供

   

## 3. 集成流程
### 3.1 在工程根目录的build.gradle中添加如下

```  java
allprojects {
    repositories {
        maven { url "https://nexus.mpaas.jdcloud.com/repository/jdd-releases/" }
    }
}
```



### 3.2 build.gradle中添加sdk依赖

```groovy
dependencies {
    api 'com.jdt.libs:appupdate:1.0.2'
}
```

### 3.3 在 AndroidManifest.xml 中配置
```xml
<application>
    // 这里定义您的buildVersion
    <meta-data 
        android:name="RELEASE_VERSION"
        android:value="这里定义您的buildVersion" />
</application>
```



### 3.4 配置混淆
```proguard
# publishCenter
-keep class com.jdd.saas.android.appupdate.** {*;}
-dontwarn com.jdd.saas.android.appupdate.**
```



## 4. 基础功能

代码接入可参考样例代码，将配置项替换为自己的数据即可。

### 4.1 Sample代码

```java
public static void init(Application app) {
   AppUpdate.getInstance()
      .setApplication(this)
      .setHost("https://xxxx.com/upgrade")
      .setGateWayId("58c1a11104b36110ba78289c110e9741")
      .setGateWayKey("")
      .setAppCode("3315727c110bf138110b3e11089740b0")
      .setDebug(true)
      .setDeviceId("000000000")
      .setAppChannel("xiaomi")
      .setUserId("zhongyuan")
      .setUpdateDialog(DefaultUpdateDialog.class)
      .init();
}
```

### 4.2 AppUpdate 方法说明

| 方法名 | 是否必要| 默认值 | 说明 |
|  --- |   :--:  |  :--: | :-- |
| fetch | 是  | 无|查询新版本，传参为false,弹框不遵循策略|
| needForceCloseApp | 否  | true|当后台配置强制升级时，用户取消后APP是否会自动关闭，如果是，则会依次关闭所有activity，然后杀死进程|
| setAppChannel | 否  | ""|设置当前渠道|
| setAppCode | 是  | 无|管理后台使用，需要在管理后台生成|
| setApplication | 是  | 无|设置当前Application |
| setDebug | 否  | true |是否是debug模式，debug模式会显示日志 |
| setDeviceId | 否  | ""|设置设备ID |
| setNotificationIntent | 否  | 无|设置在下载更新时，通知栏的pendingintent对象，默认使用getPackageManager().getLaunchIntentForPackage(getPackageName()) |
| setUpdateListener | 否  | null|设置updateListener |
| setUserId | 否  | ""|设置用户ID |
| init | 是 | 无|初始化操作 |
| setUpdateDialog | 否 | 无|自定义弹出的对话框 |

### 4.3 UpdateListener方法说明

| 方法名 | 是否必要| 默认值 | 说明 |
|  --- |   :--:  |  :--: | :-- |
| onUpdateCancel(boolean isForceUpdate) | 否  | 无|用户取消更新|
| onDownloadStart | 否  | 无|开始下载|
| onDownloadFinish | 否  | 无|下载完成|


### 4.4 自定义升级弹框

当弹框洁面需要定制时，可以通过调用AppUpdate的setUpdateDialog方法进行替换。

```java
public class DefaultUpdateDialog extends AbstractUpdateDialog implements View.OnClickListener {

    public DefaultUpdateDialog(Context context, FetchUpdateResult.FetchUpdateData fetchUpdateData) {
        super(context, R.style.dialogTransparent, fetchUpdateData);
        initView(fetchUpdateData);
    }
    protected void initView(FetchUpdateResult.FetchUpdateData fetchUpdateData) {
        setContentView(R.layout.default_updatedialog_layout);
        if (fetchUpdateData == null
                || fetchUpdateData.popuInfo == null
                || fetchUpdateData.apkInfo == null) {
            return;
        }
        TextView windowTitleView = findViewById(R.id.window_title);
        // 更新弹窗标题
        windowTitleView.setText(fetchUpdateData.popuInfo.windowTitle);

        TextView contentTitleView = findViewById(R.id.content_title);
        // 副标题
        contentTitleView.setText(fetchUpdateData.popuInfo.contentTitle);

        TextView contentView = findViewById(R.id.update_dialog_content);
        // 弹窗内容
        contentView.setText(fetchUpdateData.popuInfo.content);

        Button updateButton = findViewById(R.id.update_button);
        // 升级按钮文案
        updateButton.setText(fetchUpdateData.popuInfo.buttonText);
        updateButton.setOnClickListener(this);
        // 取消升级按钮
        ImageView closeView = findViewById(R.id.close);
        if (!fetchUpdateData.forceDownload) {
            closeView.setOnClickListener(this);
        } else {
            closeView.setVisibility(View.INVISIBLE);
        }

        setCanceledOnTouchOutside(false);
    }

    @Override
    public void show() {
        WindowManager.LayoutParams layoutParams = getWindow().getAttributes();
        layoutParams.gravity = Gravity.CENTER;
        layoutParams.width = WindowManager.LayoutParams.WRAP_CONTENT;
        layoutParams.height = WindowManager.LayoutParams.WRAP_CONTENT;
        getWindow().setAttributes(layoutParams);
        super.show();
    }

    @Override
    public void onClick(View v) {
        int id = v.getId();
        if (id == R.id.close) {
            // 取消升级
            cancel();
        } else if (id == R.id.update_button) {
            // 升级
            downloadAPK();
        }
    }
}
```

DefaultUpdateDialog布局可参考xml，布局可按照业务要求，如替换图片，字体颜色大小等。布局中要包含升级按钮、取消升级按钮，以及升级提示文案。



``` xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:background="@android:color/transparent">

    <RelativeLayout
        android:layout_width="290dp"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true">

        <RelativeLayout
            android:id="@+id/rocket_layout"
            android:layout_width="match_parent"
            android:layout_height="149dp"
            android:layout_below="@+id/close"
            android:layout_centerHorizontal="true"
            android:background="@drawable/rocket">
            <TextView
                android:id="@+id/window_title"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:textColor="#FFFFFFFF"
                android:textSize="25sp"
                android:layout_marginTop="29dp"
                android:layout_marginLeft="20dp"
                android:shadowRadius="3.0" />

            <TextView
                android:id="@+id/content_title"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:textColor="#FFFFFFFF"
                android:textSize="22sp"
                android:shadowRadius="3.0"
                android:layout_below="@id/window_title"
                android:layout_alignLeft="@id/window_title"
                android:layout_marginTop="4dp"
                />
        </RelativeLayout>
        <ImageView
            android:id="@id/close"
            android:layout_width="25dp"
            android:layout_height="25dp"
            android:layout_alignRight="@id/rocket_layout"
            android:src="@drawable/close" />

        <com.jdd.saas.android.appupdate.ui.MaxHeightScrollView
            android:id="@+id/update_dialog_content_layout"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_below="@id/rocket_layout"
            android:scrollbars="vertical"
            android:background="@android:color/white"
            app:max_height="250dp">

            <TextView
                android:id="@+id/update_dialog_content"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:textColor="#FF333333"
                android:textSize="16sp"
                android:shadowRadius="3.0"
                android:layout_marginLeft="20dp"
                android:layout_marginRight="20dp"
                />
        </com.jdd.saas.android.appupdate.ui.MaxHeightScrollView>
        <RelativeLayout
            android:id="@+id/update_button_layout"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_below="@+id/update_dialog_content_layout"
            android:background="@drawable/update_dialog_bottom">
            <Button
                android:id="@+id/update_button"
                android:layout_width="250dp"
                android:layout_height="44dp"
                android:background="@drawable/update_dialog_button_shape"
                android:layout_centerHorizontal="true"
                android:layout_marginTop="31dp"
                android:layout_marginBottom="30dp"
                android:textColor="#FFFFFFFF"
                android:textSize="14sp"
                android:textStyle="bold"
                android:shadowRadius="3.0"/>
        </RelativeLayout>
    </RelativeLayout>
</RelativeLayout>
```
## 6.隐私政策合规
“本SDK没有涉及到隐私政策，暂可不增加”

