## Android集成 {#android}

### **导入SDK** {#sdk}

在 project 级别的 build.gradle 文件中添加 vds-gradle-plugin 依赖：

buildscript {

repositories {

jcenter()

}

dependencies {

classpath &#039;com.android.tools.build:gradle:3.0.1&#039;

classpath &#039;com.growingio.android:vds-gradle-plugin:OP-2.3.1&#039;

//2018-05-02升级，升级前版本为2.0.7

// NOTE: Do not place your application dependencies here; they belong

// in the individual module build.gradle files

}

}

### **添加插件、依赖和对应资源**

在 module 级别的 build.gradle 文件中添加 com.growingio.android 插件、vds-android-agent 依赖和对应的资源：

apply plugin: &#039;com.android.application&#039;

apply plugin: &#039;com.growingio.android&#039;

android {

compileSdkVersion 26

buildToolsVersion &quot;26.0.0&quot;

defaultConfig {

applicationId &quot;com.example.wenke.gioeesdkandroiddemo&quot;

minSdkVersion 15

targetSdkVersion 26

versionCode 1

versionName &quot;1.0&quot;

testInstrumentationRunner &quot;android.support.test.runner.AndroidJUnitRunner&quot;

resValue(&quot;string&quot;, &quot;growingio_project_id&quot;, &quot;96a848cc38c178cd&quot;)

resValue(&quot;string&quot;, &quot;growingio_url_scheme&quot;, &quot;growing.34b72609d4551902&quot;)

}//更改为对应的项目ID和URL scheme

buildTypes {

release {

minifyEnabled false

proguardFiles getDefaultProguardFile(&#039;proguard-android.txt&#039;), &#039;proguard-rules.pro&#039;

}

}

}

dependencies {

compile fileTree(dir: &#039;libs&#039;, include: [&#039;*.jar&#039;])

androidTestCompile(&#039;com.android.support.test.espresso:espresso-core:2.2.2&#039;, {

exclude group: &#039;com.android.support&#039;, module: &#039;support-annotations&#039;

})

compile &#039;com.android.support:appcompat-v7:26.+&#039;

compile &#039;com.android.support.constraint:constraint-layout:1.0.2&#039;

testCompile &#039;junit:junit:4.12&#039;

compile &#039;com.growingio.android:vds-android-agent:OP-2.3.1@aar&#039;

//更新前：compile &#039;com.growingio.android:vds-android-agent:OP-2.0.7@aar&#039;

}

*   确保URL scheme、项目ID和 SDK的版本准确。

### **添加URL scheme** {#url-scheme}

把URL Scheme添加到您的项目，以便我们唤醒您的程序，进行圈选。将该产品的URLScheme添加到你的AndroidManifest.xml中的LAUNCHER Activity下。例如

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

&lt;data android:scheme=&quot;growing.a62ec2138e951a64&quot;/&gt;//改为对应项目的URL scheme

&lt;action android:name=&quot;android.intent.action.VIEW&quot;/&gt;

&lt;category android:name=&quot;android.intent.category.DEFAULT&quot;/&gt;

&lt;category android:name=&quot;android.intent.category.BROWSABLE&quot;/&gt;

&lt;/intent-filter&gt;

&lt;/activity&gt;

&lt;/application&gt;

&lt;/manifest&gt;

*   请添加一整个 intent-filter 区块，并确保其中只有一个 data 字段
*   确保URL scheme准确

### **修改app.java文件** {#app-java}

在app.java中添加以下代码：

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

.setGtaHost(&quot;https://gta.haier.net&quot;)

.setHybridJSSDKUrlPrefix(&quot;https://assets.growingio.com/sdk/hybrid&quot;)

);

LogUtil.i(&quot;GIO&quot;, &quot;APP &quot;);

}

}

### **修改MainActivity.java文件** {#mainactivity-java}

在MainActivity.java中添加以下代码：

package com.example.wenke.gioeesdkandroiddemo;

import android.support.v7.app.AppCompatActivity;

import android.os.Bundle;

import android.util.Log;

import android.view.View;

import android.widget.Button;

import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

@Override

protected void onCreate(Bundle savedInstanceState) {

super.onCreate(savedInstanceState);

setContentView(R.layout.activity_main);

Button button1 = (Button) findViewById(R.id.button1);

button1.setOnClickListener(new View.OnClickListener() {

@Override

public void onClick(View view) {

Log.d(&quot;click&quot;,&quot;点击了button1&quot;);

Toast.makeText(MainActivity.this, &quot;click button1&quot;, Toast.LENGTH_SHORT).show();

}

});

}

}

### **代码混淆** {#-0}

如果你启用了混淆，请在你的proguard-rules.pro中加入如下代码：

-keep class com.growingio.android.sdk.** {

*;

}

-dontwarn com.growingio.android.sdk.**

-keepnames class * extends android.view.View

-keep class * extends android.app.Fragment {

public void setUserVisibleHint(boolean);

public void onHiddenChanged(boolean);

public void onResume();

public void onPause();

}

-keep class android.support.v4.app.Fragment {

public void setUserVisibleHint(boolean);

public void onHiddenChanged(boolean);

public void onResume();

public void onPause();

}

-keep class * extends android.support.v4.app.Fragment {

public void setUserVisibleHint(boolean);

public void onHiddenChanged(boolean);

public void onResume();

public void onPause();

}

### **重要配置项** {#-1}

2.3.7.1采集广告banner数据

很多应用的界面上方都有横向滚动的 Banner 广告。

对于此类广告，如果您的应用通过 ViewPager、AdapterView 或者 RecyclerView 实现，请在 Banner创建时（包括动态创建）调用下面的接口来采集数据。

GrowingIO.getInstance().trackBanner(banner, bannerDescriptions)

其中 bannerDescriptions 是 List&lt;String&gt;类型，包含所有广告图对应的广告内容描述，内容描述需要跟广告的顺序相同。

例如，当您有 5 张广告图时，只需创建一个 String 类型的 List，然后按 5 个广告出现的顺序给 List 的元素设置对应的广告描述，同样设置 5 个元素即可。