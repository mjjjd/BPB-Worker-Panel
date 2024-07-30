<h1 align="center">⁉️ 常见问题解答</h1>

1- 为什么Fragment配置不能连接？
- 如果您启用了 `Routing` 并且VPN未连接，唯一的原因是Geo asset未更新。进入v2rayNG应用的菜单中的 `Geo asset files` 部分，点击云或下载图标进行更新。如果更新失败，无法连接。若无论如何尝试仍无法更新，请从以下两个链接下载两个文件，并在更新失败时点击添加按钮，将这两个文件导入：
> 
>[geoip.dat](https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geoip.dat)
> 
>[geosite.dat](https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geosite.dat)
<br> 

2- 为什么普通配置无法连接？
- 要使用这些配置，请关闭您使用的任何应用程序的 `Mux` 设置。
<br>

3- 为什么Nekobox或Hiddify Next应用程序无法打开任何网站？
- 在应用程序设置中，将 `remote DNS` 设置为：
> `https://8.8.8.8/dns-query`
<br>

4- 为什么v2rayNG不能打开某些内容？
- 在应用程序设置中的 `VPN Settings` 部分，需要关闭 `Enable local DNS`。
<br>

5- 为什么Fragment配置在我的运营商上速度慢？
- 每个运营商都有自己的Fragment设置。大多数情况下默认面板设置是可以的，但在您的运营商上可能需要调整这些值，您需要测试：
> `Length: 10-100`
> 
> `Length: 10-20`
<br>

6- 为什么我的Ping值这么高？
- 千万不要将 `https://1.1.1.1/dns-query` 用作remote DNS，因为它会增加Ping值。
<br>

7- 我根据那两个链接设置了Proxy IP，但无法打开网站！
- 这些IP数量众多，可能很多已经失效。您需要测试并找到一个好的IP。
<br>

8- 设置Proxy IP后起作用了，但现在失效了！
- 如果只使用单个IP，可能在一段时间后再次失效，并且很多网站无法打开。您需要重新进行这些步骤。最好不要设置单个Proxy IP，除非有特定需求使用固定IP。
<br>

9- 为什么访问 `panel/` 地址时出错？
- 请按照教程正确设置，KV没有正确配置。
<br>

10- 部署后Cloudflare返回1101错误！
- 如果使用Worker方法，请尝试通过Pages创建。如果仍有错误，您的Cloudflare账户可能已被识别，请使用新账户，最好通过Pages方法创建。
<br>

11- 我可以用它来进行交易吗？
- 如果您的Cloudflare IP位于德国（通常是这样），使用单个德国Proxy IP可能没有问题，但最好使用Chain Proxy方法来固定IP。
<br>

12- 使用TCP或Reality进行Chain Proxy时无法连接！
- 在v2rayNG设置中，将 `VPN DNS` 设置与面板中的 `Local DNS` 设置相同。例如，两者都设置为1.1.1.1。
<br>

13- 使用Pages方法部署，但在GitHub上同步fork以更新版本时，面板版本未改变！
- Cloudflare每次更新时会为该版本创建一个新的测试链接，因此当您打开项目时，会在Deployment部分看到几个不同的链接。这些都不是您的面板的主要链接，您需要从页面顶部的Production部分点击Visit Site以进入面板。
<br>

14- 激活了非TLS端口但无法连接！
- 请注意，使用非TLS配置时，您只能通过Workers部署，而不能使用个人域名或自定义域名。
<br>

15- 为什么Best Fragment配置无法连接或Ping不工作？
- 在设置中关闭 `Prefer IPv6`。
