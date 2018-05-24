## 网站集成

### **代码集成** {#-0}

将以下代码放入需要网站页面统一的&lt;head&gt;&lt;/head&gt;标签中，安装成功后，除 localhost 和 IP 地址外，所有网址下的行为数据都将会被收集。

&lt;script type=&#039;text/javascript&#039;&gt;

!function(e,t,n,g,i){e[i]=e[i]||function(){(e[i].q=e[i].q||[]).push(arguments)},n=t.createElement(&quot;script&quot;),tag=t.getElementsByTagName(&quot;script&quot;)[0],n.async=1,n.src=(&#039;https:&#039;==document.location.protocol?&#039;https://&#039;:&#039;http://&#039;)+g,tag.parentNode.insertBefore(n,tag)}(window,document,&quot;script&quot;,&quot;assets.growingio.com/op/2.0/gio.js&quot;,&quot;gio&quot;);

gio(&#039;init&#039;, &#039;96a848cc38c178cd&#039;, ##需要将此处项目ID修改为您的对应项目的ID，项目ID可以在添加应用的页面可以获得

{&#039;setImp&#039;:false,

//更新前为&#039;setImp&#039;:&#039;false&#039;, 更新不会对数据采集造成影响

&#039;setTrackerHost&#039;:&#039;vds.haier.net:443&#039;,

&#039;setTrackerScheme&#039;:&#039;https&#039;,

&#039;setOrigin&#039;: &#039;https://udg.haier.net&#039;

});

//put your custom page code here

gio(&#039;send&#039;);

&lt;/script&gt;

*   注意：确保项目ID设置无误。

### **重要配置选项** {#-1}

允许页面以 iframe 形式加载：

在 UDG 平台上使用可视化圈选指标功能需要使用 iframe 来加载目标页面。如果您的网站禁止了以 iframe 形式加载，就无法正常使用圈选功能定义指标，需要设置允许以 iframe 形式加载。

将服务器端配置修改成X-Frame-Options: Allow-From http://udg.haier.net，如果您的网站是 https ，请使用X-Frame-Options: Allow-From https://udg.haier.net 。