## 网站集成

### **代码集成** {#-0}

将以下代码放入需要网站页面统一的&lt;head&gt;&lt;/head&gt;标签中，安装成功后，除 localhost 和 IP 地址外，所有网址下的行为数据都将会被收集。

```
<script type='text/javascript'>
```

*   注意：确保项目ID设置无误。

### **重要配置选项** {#-1}

允许页面以 iframe 形式加载：

在 GrowingIO 平台上使用可视化圈选指标功能需要使用 iframe
来加载目标页面。如果您的网站禁止了以 iframe
形式加载，就无法正常使用圈选功能定义指标，需要设置允许以 iframe
形式加载。

将服务器端配置修改成X-Frame-Options: Allow-From http://gio.growingio.com，\
如果您的网站是 https ，请使用X-Frame-Options: Allow-From
https://gio.growingio.com 。