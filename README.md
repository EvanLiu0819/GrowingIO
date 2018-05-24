# 2018-5-2用户中心UDG平台SDK对接文档 {#2018-5-2-udg-sdk}

控制文档

| _当前版本号:_ |  |
| --- | --- |
| _作者&amp;创建日期_ |  |
| _最新更新作者&amp;日期:_ |  |
| _审核&amp;审核日期:_ |  |
| _会签及日期_ |  |
|  |  |
|  | **** |
|  |  |
|  |  |
| _批准人&amp; 批准日期:_ |  |

文件更改履历

| **_更新次数_** | **_更新日期_** | **_修订作者_** | **_主要修订摘要_** |
| --- | --- | --- | --- |
|  | **_2018-4-9_** | **_陆梦飞_** | **_添加RN框架集成方式_** |
|  | **_2018-5-2_** | **_陆梦飞_** |

1.  **_安卓SDK版本由2.0.7升级为2.3.1，与线上版本相同_**
2.  **_ios由2.0.1升级为2.3.1，与线上版本相同_**
3.  **_增加Android和IOS的banner数据采集方法_**

 |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |

**目录**

[1 获取项目ID和URL Scheme 3](export/huo_qu_xiang_mu_id_he_url_scheme/huo_qu_xiang_mu_id_he_url_scheme.md)

1.1 添加应用 3

[1.2 获取项目ID和URL Scheme 3](export/huo_qu_xiang_mu_id_he_url_scheme/huo_qu_xiang_mu_id_he_url_scheme.md)

[2 集成SDK 4](export/jian_ce_shu_ju/jian_ce_sdk_an_zhuang_zhuang_tai.md)

[2.1 网站集成 4](export/shang_chuan_deng_lu_yong_hu_id/zai_tu_biao_zhong_yan_zheng_shu_ju_you_xiao_xing.md)

[2.1.1 代码集成 4](export/ji_cheng_sdk/react_native_sdk_ji_cheng.md#-0)

[2.1.2 重要配置选项 5](export/ji_cheng_sdk/react_native_sdk_ji_cheng.md#-1)

[2.2 IOS集成 5](export/shang_chuan_deng_lu_yong_hu_id/dai_ma_shi_shi.md#ios)

[2.2.1 准备最新IOS SDK 5](export/ji_cheng_sdk/iosji_cheng.md#ios-sdk)

[2.2.2 导入SDK包 5](export/jian_ce_shu_ju/jian_ce_sdk_an_zhuang_zhuang_tai.md)

[2.2.3 在build phases中添加依赖 6](export/ji_cheng_sdk/iosji_cheng.md#build-phases)

[2.2.4 添加编译参数 7](export/shang_chuan_deng_lu_yong_hu_id/zai_tu_biao_zhong_yan_zheng_shu_ju_you_xiao_xing.md)

[2.2.5 在AppDelegate.m添加集成代码 7](export/ji_cheng_sdk/iosji_cheng.md#appdelegate-m)

[2.2.6 添加URL scheme 8](export/ji_cheng_sdk/androidji_cheng.md#url-scheme)

[2.2.7 添加激活圈选代码 8](export/ji_cheng_sdk/react_native_sdk_ji_cheng.md#-0)

[2.3 Android集成 9](export/shang_chuan_deng_lu_yong_hu_id/dai_ma_shi_shi.md#android)

[2.3.1 导入SDK 9](export/jian_ce_shu_ju/jian_ce_sdk_an_zhuang_zhuang_tai.md)

[2.3.2 添加插件、依赖和对应资源 9](export/shang_chuan_deng_lu_yong_hu_id/zai_tu_biao_zhong_yan_zheng_shu_ju_you_xiao_xing.md)

[2.3.3 添加URL scheme 10](export/ji_cheng_sdk/androidji_cheng.md#url-scheme)

[2.3.4 修改app.java文件 12](export/ji_cheng_sdk/android_cordova_ji_cheng.md#app-java)

[2.3.5 修改MainActivity.java文件 13](export/ji_cheng_sdk/androidji_cheng.md#mainactivity-java)

[2.3.6 代码混淆 13](export/ji_cheng_sdk/react_native_sdk_ji_cheng.md#-0)

[2.4 Android cordova 集成 14](export/ji_cheng_sdk/ios_cordova_ji_cheng.md)

[2.4.1 添加cordova插件 14](export/ji_cheng_sdk/android_cordova_ji_cheng.md#cordova)

[2.4.2 导入SDK 14](export/jian_ce_shu_ju/jian_ce_sdk_an_zhuang_zhuang_tai.md)

[2.4.3 修改BUILD.GRADLE文件 15](export/ji_cheng_sdk/android_cordova_ji_cheng.md#build-gradle)

[2.4.4 修改AndroidManifest.xml文件 15](export/ji_cheng_sdk/android_cordova_ji_cheng.md#androidmanifest-xml)

[2.4.5 修改app.java文件 17](export/ji_cheng_sdk/android_cordova_ji_cheng.md#app-java)

[2.4.6 配置cordova 18](export/ji_cheng_sdk/android_cordova_ji_cheng.md#cordova-0)

[3 检测数据 19](export/shang_chuan_deng_lu_yong_hu_id/zai_tu_biao_zhong_yan_zheng_shu_ju_you_xiao_xing.md)

[3.1 检测SDK安装状态 19](export/jian_ce_shu_ju/jian_ce_sdk_an_zhuang_zhuang_tai.md)

[3.2 完成安装 19](export/shang_chuan_deng_lu_yong_hu_id/zai_tu_biao_zhong_yan_zheng_shu_ju_you_xiao_xing.md)

[3.3 查看数据 20](export/shang_chuan_deng_lu_yong_hu_id/zai_tu_biao_zhong_yan_zheng_shu_ju_you_xiao_xing.md)

[4 上传登陆用户ID 21](export/shang_chuan_deng_lu_yong_hu_id/README.md)

[4.1 后台配置 21](export/shang_chuan_deng_lu_yong_hu_id/zai_tu_biao_zhong_yan_zheng_shu_ju_you_xiao_xing.md)

[4.2 代码实施 22](export/shang_chuan_deng_lu_yong_hu_id/zai_tu_biao_zhong_yan_zheng_shu_ju_you_xiao_xing.md)

[4.2.1 Web端 22](export/shang_chuan_deng_lu_yong_hu_id/dai_ma_shi_shi.md#web)

[4.2.2 Android端 22](export/shang_chuan_deng_lu_yong_hu_id/dai_ma_shi_shi.md#android)

[4.2.3 IOS 端 23](export/shang_chuan_deng_lu_yong_hu_id/dai_ma_shi_shi.md#ios)

4.3 在图表中验证数据有效性 23
