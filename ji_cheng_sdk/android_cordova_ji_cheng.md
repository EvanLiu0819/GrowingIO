## Android cordova 集成 {#android-cordova}

### **添加cordova插件** {#cordova}

cordova plugin add cordova-growingio-plugin

注意：cordova-growing-plugin依赖cordova.5.0.0以上，目前不支持低版本。

### **导入SDK** {#sdk}

ANDROID/BUILD.GRADLE文件添加

buildscript {

repositories {

jcenter()

}

dependencies {

classpath &#039;com.android.tools.build:gradle:1.5.0&#039;

classpath &#039;com.growingio.android:vds-gradle-plugin:2.1.0&#039;

}

}

allprojects {

repositories {

jcenter()

}

}

注意高亮部分的sdk版本

### **修改BUILD.GRADLE文件** {#build-gradle}

找到ANDROID/APP/BUILD.GRADLE文件加入以下代码

apply plugin: &#039;com.android.application&#039;

apply plugin: &#039;com.growingio.android&#039;

android {

defaultConfig {

resValue(&quot;string&quot;, &quot;growingio_project_id&quot;, &quot;96a848cc38c178cd&quot;)

resValue(&quot;string&quot;, &quot;growingio_url_scheme&quot;, &quot;growing.a62ec2138e951a64&quot;)

}//更改为对应的项目ID和URL scheme

}

dependencies {

compile &#039;com.growingio.android:vds-android-agent:2.1.0@aar&#039;

}

### **修改AndroidManifest.xml文件** {#androidmanifest-xml}

在AndroidManifest.xml文件添加以下代码：

&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;

&lt;manifest xmlns:android=&quot;http://schemas.android.com/apk/res/android&quot; package=&quot;com.example.wenke.gioeesdkandroiddemo&quot;&gt;

&lt;uses-permission android:name=&quot;android.permission.SYSTEM_ALERT_WINDOW&quot;/&gt;

&lt;uses-permission android:name=&quot;android.permission.INTERNET&quot;/&gt;

&lt;uses-permission android:name=&quot;android.permission.ACCESS_NETWORK_STATE&quot;/&gt;

&lt;application

android:name=&quot;.App&quot;

android:allowBackup=&quot;true&quot;

android:icon=&quot;@mipmap/ic_launcher&quot;

android:label=&quot;@string/app_name&quot;

android:roundIcon=&quot;@mipmap/ic_launcher_round&quot;

android:supportsRtl=&quot;true&quot;

android:theme=&quot;@style/AppTheme&quot;&gt;

&lt;activity android:name=&quot;.MainActivity&quot;&gt;

&lt;intent-filter&gt;

&lt;action android:name=&quot;android.intent.action.MAIN&quot; /&gt;

&lt;category android:name=&quot;android.intent.category.LAUNCHER&quot; /&gt;

&lt;/intent-filter&gt;

&lt;intent-filter&gt;

&lt;data android:scheme=&quot;growing.a62ec2138e951a64&quot;/&gt;

//修改为对应的URL scheme

&lt;action android:name=&quot;android.intent.action.VIEW&quot;/&gt;

&lt;category android:name=&quot;android.intent.category.DEFAULT&quot;/&gt;

&lt;category android:name=&quot;android.intent.category.BROWSABLE&quot;/&gt;

&lt;/intent-filter&gt;

&lt;/activity&gt;

&lt;/application&gt;

&lt;/manifest&gt;

### **修改app.java文件** {#app-java}

在app.java添加以下代码

package com.example.wenke.gioeesdkandroiddemo;

import android.app.Application;

import com.growingio.android.sdk.collection.Configuration;

import com.growingio.android.sdk.collection.GConfig;

import com.growingio.android.sdk.collection.GrowingIO;

import com.growingio.android.sdk.utils.LogUtil;

/**

* Created by wenke on 2017/12/8.

*/

public class App extends Application {

@Override

public void onCreate() {

super.onCreate();

GrowingIO.startWithConfiguration(this, new Configuration()

// .setDisableImpression(true)

.useID()

.trackAllFragments()

.setTestMode(true)

.setDebugMode(true)

.setChannel(&quot;optest&quot;)

.setTrackerHost(&quot;https://vds.haier.net&quot;) // marathon external_lb

.setDataHost(&quot;https://udg.haier.net&quot;)

.setGtaHost(&quot;https://gta.haier.net:8443&quot;)

.setHybridJSSDKUrlPrefix(&quot;https://assets.growingio.com/sdk/hybrid&quot;)

);

LogUtil.i(&quot;GIO&quot;, &quot;APP &quot;);

}

}

### **配置cordova** {#cordova-0}

当应用程序打开时，需要初始化会话并启动采集功能。所以，在deviceready或者resume事件触发时，可以通过下列方式初始化会话。

// sample index.js

var app = {

initialize: function() {

this.bindEvents();

},

bindEvents: function() {

document.addEventListener(&#039;deviceready&#039;, this.onDeviceReady, false);

document.addEventListener(&#039;resume&#039;, this.onDeviceResume, false);

},

onDeviceReady: function() {

app.initGrowingIO();

},

onDeviceResume: function() {

app.initGrowingIO();

},

initGrowingIO: function() {

// 初始化

try {

var gio = window.cordova.require(&#039;cordova-plugin-growingio.GrowingIO&#039;);

var onSucc = function(msg) {

alert(msg);

};

var onFail = function(msg) {

alert(msg);

};

gio.init(&#039;96a848cc38c178cd&#039;,

{

channel: &#039;员工端下载&#039;,

trackerHost:&#039;https://vds.haier.net&#039;,

dataHost:&#039;https://udg.haier.net&#039;,

gtaHost:&#039;https://gta.haier.net&#039;,

hybridJSSDKUrlPrefix:&#039;https://assets.growingio.com/sdk/hybrid&#039;

},

onSucc,

onFail);

} catch(err) {

handleException(err);

}

}

};