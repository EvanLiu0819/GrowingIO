
**目录**
========

[[1] [获取项目ID和URL Scheme]
3](#获取项目id和url-scheme)

[[1.1] [添加应用] 3](#添加应用)

[[1.2] [获取项目ID和URL Scheme]
3](#获取项目id和url-scheme-1)

[[2] [集成SDK] 4](#集成sdk)

[[2.1] [网站集成] 4](#网站集成)

[[2.1.1] [代码集成] 4](#代码集成)

[[2.1.2] [重要配置选项] 5](#重要配置选项)

[[2.2] [IOS集成] 5](#_Toc505547646)

[[2.2.1] [准备最新IOS SDK] 5](#准备最新ios-sdk)

[[2.2.2] [导入SDK包] 5](#导入sdk包)

[[2.2.3] [在build phases中添加依赖]
6](#在build-phases中添加依赖)

[[2.2.4] [添加编译参数] 7](#添加编译参数)

[[2.2.5] [在AppDelegate.m添加集成代码]
7](#在appdelegate.m添加集成代码)

[[2.2.6] [添加URL scheme] 8](#添加url-scheme)

[[2.2.7] [添加激活圈选代码]
8](#添加激活圈选代码)

[[2.3] [Android集成] 9](#android集成)

[[2.3.1] [导入SDK] 9](#导入sdk)

[[2.3.2] [添加插件、依赖和对应资源]
9](#添加插件依赖和对应资源)

[[2.3.3] [添加URL scheme] 10](#添加url-scheme-1)

[[2.3.4] [修改app.java文件]
12](#修改app.java文件)

[[2.3.5] [修改MainActivity.java文件]
13](#修改mainactivity.java文件)

[[2.3.6] [代码混淆] 13](#代码混淆)

[[2.4] [Android cordova 集成]
14](#ios-cordova-集成)

[[2.4.1] [添加cordova插件] 14](#添加cordova插件)

[[2.4.2] [导入SDK] 14](#导入sdk-1)

[[2.4.3] [修改BUILD.GRADLE文件]
15](#修改build.gradle文件)

[[2.4.4] [修改AndroidManifest.xml文件]
15](#修改androidmanifest.xml文件)

[[2.4.5] [修改app.java文件]
17](#修改app.java文件-1)

[[2.4.6] [配置cordova] 18](#配置cordova)

[[3] [检测数据] 19](#检测数据)

[[3.1] [检测SDK安装状态] 19](#检测sdk安装状态)

[[3.2] [完成安装] 19](#完成安装)

[[3.3] [查看数据] 20](#查看数据)

[[4] [上传登陆用户ID] 21](#上传登陆用户id)

[[4.1] [后台配置] 21](#后台配置)

[[4.2] [代码实施] 22](#代码实施)

[[4.2.1] [Web端] 22](#web端)

[[4.2.2] [Android端] 22](#android端)

[[4.2.3] [IOS 端] 23](#ios-端)

[[4.3] [在图表中验证数据有效性]
23](#在图表中验证数据有效性)

获取项目ID和URL Scheme
======================

集成前，请向项目管理员申请登陆账号

添加应用
--------

点击右上角新建---添加新应用---添加应用，选择对应的平台

![](media/image3.png){width="6.0in" height="3.079861111111111in"}

获取项目ID和URL Scheme
----------------------

页面中标黄位置为对应的项目ID和URL Scheme（Android和IOS平台）

![](media/image4.png){width="6.0in" height="1.8159722222222223in"}

![](media/image5.png){width="6.0in" height="2.6881944444444446in"}

集成SDK
=======

网站集成
--------

### 代码集成

将以下代码放入需要网站页面统一的\<head\>\</head\>标签中，安装成功后，除
localhost 和 IP 地址外，所有网址下的行为数据都将会被收集。

```
<script type='text/javascript'>!function(e,t,n,g,i){e[i]=e[i]||function(){(e[i].q=e[i].q||[]).push(arguments)},n=t.createElement("script"),tag=t.getElementsByTagName("script")[0],n.async=1,n.src=('https:'==document.location.protocol?'https://':'http://')+g,tag.parentNode.insertBefore(n,tag)}(window,document,"script","assets.growingio.com/op/2.0/gio.js","gio");  gio('init', '96a848cc38c178cd',  ##需要将此处项目ID修改为您的对应项目的ID，项目ID可以在添加应用的页面可以获得  {'setImp':false,//更新前为'setImp':'false', 更新不会对数据采集造成影响   'setTrackerHost':'vds.growingio.com:443',    'setTrackerScheme':'https',   'setOrigin': 'https://gio.growingio.com'  });  //put your custom page code here  gio('send');</script>
```

-   注意：确保项目ID设置无误。

### 重要配置选项

允许页面以 iframe 形式加载：

在 GrowingIO 平台上使用可视化圈选指标功能需要使用 iframe
来加载目标页面。如果您的网站禁止了以 iframe
形式加载，就无法正常使用圈选功能定义指标，需要设置允许以 iframe
形式加载。

将服务器端配置修改成X-Frame-Options: Allow-From http://gio.growingio.com，\
如果您的网站是 https ，请使用X-Frame-Options: Allow-From
https://gio.growingio.com 。

IOS集成
-------

### 准备最新IOS SDK

点击下载[*[iOS
SDK]*](http://assets.growingio.com/sdk/GrowingIO-iOS-SDK-2.3.1.zip)

### 导入SDK包

将SDK包解压缩并拷贝到您代码的工程目录里。

![](media/image6.png){width="6.339583333333334in"
height="2.262405949256343in"}

### 在build phases中添加依赖

![](media/image7.png){width="6.339583333333334in"
height="3.721007217847769in"}

![](media/image8.png){width="6.339583333333334in"
height="3.647107392825897in"}

### 添加编译参数

![](media/image9.png){width="6.339583333333334in"
height="1.571266404199475in"}

### 在AppDelegate.m添加集成代码
```
#import "Growing.h"...- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {        ...        [Growing startWithAccountId:@"96a848cc38c178cd"];// 改成对应项目ID        [Growing setImp:NO];        [Growing setTrackerHost:@"https://vds.growingio.com"]; //修改为vds域名        [Growing setDataHost:@"https://gio.growingio.com"];  //修改为主域名        [Growing setGtaHost:@"https://gta.growingio.com"];  //修改为gta域名        [Growing setHybridJSSDKUrlPrefix:@"https://assets.growingio.com/sdk/hybrid/1.0"];        [Growing setEnableLog:YES];  // 开启调试日志 可以开启日志}
```
### 添加URL scheme

![](media/image10.png){width="6.339583333333334in"
height="2.6569444444444446in"}

### 添加激活圈选代码

因为您代码的复杂程度以及iOS SDK的版本差异，有时候 \[Growing
handleUrl:url\] 并没有被调用。请在各个平台上调试这段代码，确保当App被URL
scheme唤醒之后，该函数能被调用到。

```
- (BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(NSString *)sourceApplication annotation:(id)annotation {    if ([Growing handleUrl:url]) // 请务必确保该函数被调用    {        return YES;    }    return NO;    }
```

### 重要配置项

2.2.8.1采集广告Banner数据

很多应用上方都有横向滚动的Banner广告。对于这样的广告，如果要收集数据，请在响应点击的控件上添加如下代码

```
UIView *view;…view.growingAttributesValue = 广告的唯一ID;
```


其中view是您的广告元素，请确保两点：

-   对不同广告图，广告的唯一ID也不相同

-   响应点击的控件，与设置ID的控件是同一个

例如，当您的横向滚动广告共有3张广告图时，您可以在3个响应点击的View上分别设置不同的广告唯一ID，类似如下效果：

```
view1.growingAttributesValue = @“ad1”;view2.growingAttributesValue = @“ad2”;view3.growingAttributesValue = @“ad3”;
```

此外，当您想采集一些可能没有文字的控件（比如UIImageView，UIView）时，也可以给属性growingAttributesValue赋值作为文字，用来在圈选的时候区分不同的内容。

Android集成
-----------

### 导入SDK

在 project 级别的 build.gradle 文件中添加 vds-gradle-plugin 依赖：

```
    buildscript {            repositories {                jcenter()            }            dependencies {                classpath 'com.android.tools.build:gradle:3.0.1'                classpath 'com.growingio.android:vds-gradle-plugin:OP-2.3.1'//2018-05-02升级，升级前版本为2.0.7                // NOTE: Do not place your application dependencies here; they belong                // in the individual module build.gradle files            }    }
```
### 添加插件、依赖和对应资源

在 module 级别的 build.gradle 文件中添加 com.growingio.android
插件、vds-android-agent 依赖和对应的资源：

```
apply plugin: 'com.android.application'apply plugin: 'com.growingio.android'android {    compileSdkVersion 26    buildToolsVersion "26.0.0"    defaultConfig {        applicationId "com.example.wenke.gioeesdkandroiddemo"        minSdkVersion 15        targetSdkVersion 26        versionCode 1        versionName "1.0"        testInstrumentationRunner "android.support.test.runner.AndroidJUnitRunner"        resValue("string", "growingio_project_id", "96a848cc38c178cd")        resValue("string", "growingio_url_scheme", "growing.34b72609d4551902")    }//更改为对应的项目ID和URL scheme    buildTypes {        release {            minifyEnabled false            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'        }    }}dependencies {    compile fileTree(dir: 'libs', include: ['*.jar'])    androidTestCompile('com.android.support.test.espresso:espresso-core:2.2.2', {        exclude group: 'com.android.support', module: 'support-annotations'    })    compile 'com.android.support:appcompat-v7:26.+'    compile 'com.android.support.constraint:constraint-layout:1.0.2'testCompile 'junit:junit:4.12'	compile 'com.growingio.android:vds-android-agent:OP-2.3.1@aar'
	
	//更新前：compile 'com.growingio.android:vds-android-agent:OP-2.0.7@aar'}
```
-   确保URL scheme、项目ID和 SDK的版本准确。

### 添加URL scheme

把URL
Scheme添加到您的项目，以便我们唤醒您的程序，进行圈选。将该产品的URLScheme添加到你的AndroidManifest.xml中的LAUNCHER
Activity下。例如

```
<?xml version="1.0" encoding="utf-8"?><manifest xmlns:android="http://schemas.android.com/apk/res/android" package="com.example.wenke.gioeesdkandroiddemo"><uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW"/><uses-permission android:name="android.permission.INTERNET"/><uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/><application    android:name=".App"    android:allowBackup="true"    android:icon="@mipmap/ic_launcher"    android:label="@string/app_name"    android:roundIcon="@mipmap/ic_launcher_round"    android:supportsRtl="true"    android:theme="@style/AppTheme">    <activity android:name=".MainActivity">        <intent-filter>            <action android:name="android.intent.action.MAIN" />            <category android:name="android.intent.category.LAUNCHER" />        </intent-filter>        <intent-filter>            <data android:scheme="growing.a62ec2138e951a64"/>//改为对应项目的URL scheme            <action android:name="android.intent.action.VIEW"/>            <category android:name="android.intent.category.DEFAULT"/>            <category android:name="android.intent.category.BROWSABLE"/>        </intent-filter>    </activity></application></manifest>
```

-   请添加一整个 intent-filter 区块，并确保其中只有一个 data 字段

-   确保URL scheme准确

### 修改app.java文件

在app.java中添加以下代码：

```
package com.example.wenke.gioeesdkandroiddemo;import android.app.Application;import com.growingio.android.sdk.collection.Configuration;import com.growingio.android.sdk.collection.GConfig;import com.growingio.android.sdk.collection.GrowingIO;import com.growingio.android.sdk.utils.LogUtil;/*** Created by wenke on 2017/12/8.*/public class App extends Application {@Overridepublic void onCreate() {    super.onCreate();    GrowingIO.startWithConfiguration(this, new Configuration()//                .setDisableImpression(true)            .useID()            .trackAllFragments()            .setTestMode(true)            .setDebugMode(true)            .setChannel("optest")            .setTrackerHost("https://vds.growingio.com")  // vds域名            .setDataHost("https://gio.growingio.com") // 前端主域名            .setGtaHost("https://gta.growingio.com")  //gta域名            .setHybridJSSDKUrlPrefix("https://assets.growingio.com/sdk/hybrid")    );    LogUtil.i("GIO", "APP ");}}
```
### 修改MainActivity.java文件

在MainActivity.java中添加以下代码：

```
package com.example.wenke.gioeesdkandroiddemo;import android.support.v7.app.AppCompatActivity;import android.os.Bundle;import android.util.Log;import android.view.View;import android.widget.Button;import android.widget.Toast;public class MainActivity extends AppCompatActivity {    @Override    protected void onCreate(Bundle savedInstanceState) {        super.onCreate(savedInstanceState);        setContentView(R.layout.activity_main);        Button button1 = (Button) findViewById(R.id.button1);        button1.setOnClickListener(new View.OnClickListener() {            @Override            public void onClick(View view) {                Log.d("click","点击了button1");                Toast.makeText(MainActivity.this, "click button1", Toast.LENGTH_SHORT).show();            }        });    }
```

### 代码混淆

如果你启用了混淆，请在你的proguard-rules.pro中加入如下代码：

```
-keep class com.growingio.android.sdk.** {    *;}-dontwarn com.growingio.android.sdk.**-keepnames class * extends android.view.View-keep class * extends android.app.Fragment {    public void setUserVisibleHint(boolean);    public void onHiddenChanged(boolean);    public void onResume();    public void onPause();}-keep class android.support.v4.app.Fragment {    public void setUserVisibleHint(boolean);    public void onHiddenChanged(boolean);    public void onResume();    public void onPause();}-keep class * extends android.support.v4.app.Fragment {    public void setUserVisibleHint(boolean);    public void onHiddenChanged(boolean);    public void onResume();    public void onPause();}
```
### 重要配置项

2.3.7.1采集广告banner数据

很多应用的界面上方都有横向滚动的 Banner 广告。

对于此类广告，如果您的应用通过 ViewPager、AdapterView 或者 RecyclerView
实现，请在 Banner创建时（包括动态创建）调用下面的接口来采集数据。

GrowingIO.getInstance().trackBanner(banner, bannerDescriptions)

其中 bannerDescriptions 是
List\<String\>类型，包含所有广告图对应的广告内容描述，内容描述需要跟广告的顺序相同。

例如，当您有 5 张广告图时，只需创建一个 String 类型的 List，然后按 5
个广告出现的顺序给 List 的元素设置对应的广告描述，同样设置 5
个元素即可。

IOS cordova 集成
----------------

ios cordova集成参照ios的集成方式


Android cordova 集成
--------------------

### 添加cordova插件

```
cordova plugin add cordova-growingio-plugin
```

注意：cordova-growing-plugin依赖cordova.5.0.0以上，目前不支持低版本。

### 导入SDK

ANDROID/BUILD.GRADLE文件添加

```
buildscript {  repositories {    jcenter()  }  dependencies {    classpath 'com.android.tools.build:gradle:1.5.0'    classpath 'com.growingio.android:vds-gradle-plugin:2.1.0' //sdk版本  }}allprojects {  repositories {    jcenter()  }}
```
注意高亮部分的sdk版本

### 修改BUILD.GRADLE文件

找到ANDROID/APP/BUILD.GRADLE文件加入以下代码

```
apply plugin: 'com.android.application'apply plugin: 'com.growingio.android'android {   defaultConfig {      resValue("string", "growingio_project_id", "96a848cc38c178cd")      resValue("string", "growingio_url_scheme", "growing.a62ec2138e951a64")   }//更改为对应的项目ID和URL scheme}dependencies {    compile 'com.growingio.android:vds-android-agent:2.1.0@aar'}
```
### 修改AndroidManifest.xml文件

在AndroidManifest.xml文件添加以下代码：

```
<?xml version="1.0" encoding="utf-8"?><manifest xmlns:android="http://schemas.android.com/apk/res/android" package="com.example.wenke.gioeesdkandroiddemo"><uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW"/><uses-permission android:name="android.permission.INTERNET"/><uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/><application    android:name=".App"    android:allowBackup="true"    android:icon="@mipmap/ic_launcher"    android:label="@string/app_name"    android:roundIcon="@mipmap/ic_launcher_round"    android:supportsRtl="true"    android:theme="@style/AppTheme">    <activity android:name=".MainActivity">        <intent-filter>            <action android:name="android.intent.action.MAIN" />            <category android:name="android.intent.category.LAUNCHER" />        </intent-filter>        <intent-filter>            <data android:scheme="growing.a62ec2138e951a64"/>//修改为对应的URL scheme            <action android:name="android.intent.action.VIEW"/>            <category android:name="android.intent.category.DEFAULT"/>            <category android:name="android.intent.category.BROWSABLE"/>        </intent-filter>    </activity></application></manifest>
```

### 修改app.java文件

在app.java添加以下代码

```
ackage com.example.wenke.gioeesdkandroiddemo;import android.app.Application;import com.growingio.android.sdk.collection.Configuration;import com.growingio.android.sdk.collection.GConfig;import com.growingio.android.sdk.collection.GrowingIO;import com.growingio.android.sdk.utils.LogUtil;/*** Created by wenke on 2017/12/8.*/public class App extends Application {@Overridepublic void onCreate() {    super.onCreate();    GrowingIO.startWithConfiguration(this, new Configuration()//                .setDisableImpression(true)            .useID()            .trackAllFragments()            .setTestMode(true)            .setDebugMode(true)            .setChannel("optest")            .setTrackerHost("https://vds.growingio.com")  // vds域名            .setDataHost("https://gio.growingio.com") // 前端主域名            .setGtaHost("https://gta.growingio.com") // gta域名            .setHybridJSSDKUrlPrefix("https://assets.growingio.com/sdk/hybrid")    );    LogUtil.i("GIO", "APP ");}}
```
### 配置cordova

当应用程序打开时，需要初始化会话并启动采集功能。所以，在deviceready或者resume事件触发时，可以通过下列方式初始化会话。

```
// sample index.js  var app = {    initialize: function() {      this.bindEvents();    },    bindEvents: function() {      document.addEventListener('deviceready', this.onDeviceReady, false);      document.addEventListener('resume', this.onDeviceResume, false);    },    onDeviceReady: function() {      app.initGrowingIO();    },    onDeviceResume: function() {      app.initGrowingIO();    },    initGrowingIO: function() {      // 初始化      try {        var gio = window.cordova.require('cordova-plugin-growingio.GrowingIO');        var onSucc = function(msg) {          alert(msg);        };        var onFail = function(msg) {          alert(msg);        };        gio.init('96a848cc38c178cd',                {                    channel: '员工端下载',                    trackerHost:'https://vds.growingio.com', //vds域名                    dataHost:'https://gio.growingio.com', // 前端主域名                    gtaHost:'https://gta.growingio.com',  //gta域名       hybridJSSDKUrlPrefix:'https://assets.growingio.com/sdk/hybrid'                },                 onSucc,                 onFail);      } catch(err) {        handleException(err);      }    }  };
```

React Native SDK 集成
---------------------

### 说明

react-native-growingio 用于RN开发者手动发送数据。

### 引入

```
npm install --save https://github.com/growingio/react-native-growingio.gitnpm installreact-native link react-native-growingio
```

### 配置

#### IOS

如果react-native link
react-native-growingio失败(成功则忽略此步骤),即发现Libraries中没有GrowingIORNPlugin.xcodeproj,则可手动配置;

a.打开XCode\'s工程中, 右键点击Libraries文件夹 ➜ Add Files to \<\...\>

b.去node\_modules ➜ react-native-growingio ➜ ios ➜ 选择
GrowingIORNPlugin.xcodeproj

c.在工程Build Phases ➜ Link Binary With
Libraries中添加libGrowingIORNPlugin.a

添加初始化函数: 在 AppDelegate 中引入\#import
\"Growing.h\"并添加启动方法

```
- (BOOL)application:(UIApplication *)application  didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {      ...      // 启动GrowingIO      [Growing startWithAccountId:@"项目ID"];      // 其他配置      // 开启Growing调试日志 可以开启日志      // [Growing setEnableLog:YES];  }
```

-   按照文档 ios集成 "在build phases中添加依赖" 进行后续配置。

#### Android

在Application中的onCreate方法中初始化：

```
  GrowingIO.startWithConfiguration(this, new Configuration()	.useID()	.trackAllFragments()	.setChannel("**应用商店"));
```
AndroidManifest.xml以及module级别build.gradle中android defaultConfig
中添加的属性，请见官网配置。 [添加官网配置](https://docs.growingio.com/sdk-20/sdk-20-api-wen-dang/android-sdk-21-an-zhuang.html)

###  方法说明

| 方法名 | 参数 | 说明 |
| -- | -- | -- |
| track | (String eventId, Object eventLevelVariable(optional)) | 自定义事件（计数器类型） |
| trackWithNumber | (String eventId, Number number, Object eventLevelVariable(optional)) | 自定义事件（数值类型） |
| page | (String page) | 页面浏览事件 |
| setUserId | (String userId) | 设置登录用户ID |
| clearUserId |  | 清除登录用户ID |
| setPageVariable | (String page, Object pageLevelVariables) | 设置页面级变量 |
| setEvar | (Object conversionVariables) | 设置转化变量 |
| setPeopleVariable | (Object peopleVariables) | 设置用户变量 |


### JS中调用方式

在定义Component之前引入

```
import {    NativeModules} from 'react-native';
```

之后就可以使用GrowingIO的方法,例如在js中调用自定义事件方法：

 ```
 NativeModules.GrowingIO.track("registerSuccess", {"gender":"male"});
 ```
 
### Tips

由于最新的ReactNative
打包gradlew存在bug，所以android在打debug包和releae包时要进行如下操作：

在工程目录下

mkdir Android/app/assets

在app build.gradle android中添加：

```
sourceSets {     main {         assets.srcDirs = ['assets']     } }
```

在工程目录下：

```
react-native bundle --platform android --dev false --entry-file App.js --bundle-output android/app/assets/index.android.bundle  --assets-dest android/app/src/main/res/
```

demo 可见
https://github.com/growingio/react-native-growingio/examples/App.js

检测数据
========

检测SDK安装状态
---------------

SDK安装成功后，点击"去检测SDK安装状态"按钮

![](media/image11.png){width="6.339583333333334in"
height="1.2361111111111112in"}

完成安装
--------

选择与您的应用具有相同URL或包名的一项，点击"完成安装"

![](media/image12.png){width="6.339583333333334in"
height="3.738888888888889in"}

查看数据
--------

SDK安装成功后，数据会在一小时后更新，在概览页面即可进行全局指标的查看![](media/image13.png){width="6.339583333333334in"
height="2.6506944444444445in"}

![](media/image14.png){width="6.339583333333334in"
height="3.061111111111111in"}

验证是否能够正常圈选
--------------------

在系统中点击圈选，选择刚刚添加的应用，在地址栏输入集成SDK的系统地址，显示绿色的SDK标志，代表该页面集成SDK成功，且已经能够正常完成圈选。

![](media/image15.png){width="6.0in" height="2.259027777777778in"}

![](media/image16.png){width="6.0in" height="1.8111111111111111in"}

如果显示红色标志，代表该页面成功集成SDK，按照提示内容进行问题排查，排查后仍未解决，可联系系统负责人。

![](media/image17.png){width="6.0in" height="1.1368055555555556in"}

上传登陆用户ID
==============

为了在GrowingIO后台看到登陆用户的相关趋势和指标，需要上传用户的登陆ID。

注意：如果您的应用是互联网应用，且已对接用户中心，上传的用户ID必须是用户中心统一的登录ID，如果需要上传自己应用的用户ID及其他业务数据，可以按照需求进行对应变量的上传。（根据业务需求进行埋点可与项目负责人联系）

后台配置
--------

1.在GrowingIO 后台导航栏中找到"打点管理"功能

![](media/image18.png){width="6.339583333333334in"
height="1.5868055555555556in"}

2.点击"用户变量"，开启"登陆用户ID"

![](media/image19.png){width="6.339583333333334in"
height="2.2055555555555557in"}

代码实施
--------

当用户登录之后调用setUserId API，设置登录用户ID

当用户登出之后调用clearUserId，清除已经设置的登录用户ID。

参数（注意大小写）：

| 参数名称 | 参数类型 | 是否必须 | 说明 |
| -- | -- | -- | -- |
| userId | String | 是 | 用户的登录用户ID


### Web端

```
//setUserId API原型gio('setUserId', userId);//setuserId API调用示例gio('setUserId', '1234567890');//clearUserId API原型和调用示例gio('clearUserId');
```

### Android端

```
// setUserId API原型GrowingIO.getInstance().setUserId(String userId);// setuserId API调用示例GrowingIO.getInstance().setUserId(String "1234567890");// clearUserId API原型GrowingIO.getInstance().clearUserId();// clearUserId API调用示例GrowingIO.getInstance().clearUserId();
```
### IOS 端

```
// setUserId API原型+ (void)setUserId:(NSString *)userId;// setuserId API调用示例[Growing setUserId:@"1234567890"];// clearUserId API原型+ (void)clearUserId;// clearUserId API调用示例[Growing clearUserId];
```

在图表中验证数据有效性
----------------------

1.在"分析"模块中，选择新建事件分析。

![](media/image20.png){width="6.339583333333334in"
height="2.029861111111111in"}

2.在"指标"下拉菜单选择指标（建议使用全局指标如页面访问量），在"维度"下拉菜单选择登陆用户ID，在右侧表格中看到上传的登陆用户ID，代表上传成功。

![](media/image21.png){width="6.339583333333334in"
height="2.276388888888889in"}
