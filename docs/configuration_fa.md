# 如何使用

假设您的worker或页面的名称是`worker-polished-leaf-d022`：

您可以通过在其末尾添加`panel/`来查看Panel，如下所示：

> `https://worker-polished-leaf-d022.workers.dev/panel`

首先会进入登录页面，输入默认密码`admin`即可...
> [!IMPORTANT]
> 在Panel底部点击**重置密码**并更改密码，密码必须至少包含**8个字符**，并且至少包含一个**大写字母**和一个**数字**。

现在我们来看看Panel的不同部分：
<br><br>
## 1 - 普通配置

<p align="center">
  <img src="assets/images/Normal-Configs.jpg">
</p>

我从这个部分开始，因为很多人即使没有Fragment也可以使用。

这一部分提供普通配置的订阅链接（不带Fragment）。根据您的应用程序选择相应的链接并使用。Sing-box订阅专为iOS和Android设计，是**最佳延迟**类型。它可以屏蔽约90%的伊朗和国外广告，绕过伊朗网站（不需要关闭VPN即可访问支付门户等），并且还能屏蔽钓鱼和恶意软件链接等。

> [!TIP]
> 什么是**最佳延迟**配置？这个配置将Panel的所有配置合并，每3分钟检查一次哪种配置速度更快并连接到它！如果您输入了干净的IP，也会将其添加到最佳延迟配置中。这个配置类型在Fragment订阅和Nekoray的单一配置中都有。

这个链接提供了6个配置。（您可以通过设置干净IP和Port来增加配置的数量）那么这6个配置有什么不同呢？如何增加它们的数量？更多说明和设置请参见[这里](3-5--清洁IP设置)和[这里](3-6--端口设置)。

> [!CAUTION]
> 使用这些配置时，请在您使用的每个应用程序的设置中关闭Mux。

> [!WARNING]
> 使用此Worker时，您的设备IP会频繁更改，因此不建议用于交易、PayPal甚至Hetzner等敏感站点，可能会导致被封禁。关于固定IP的方法，我们提供了两种解决方案，一个是设置Proxy IP，另一个是Proxy Chain，详细信息请参见[这里](#3-2--链式代理设置)。
<br><br>
## 2 - Fragment订阅和配置

> [!NOTE]
> **此Panel的Fragment配置特点**
> 
> 1- 去除80%的伊朗和国外广告
> 
> 2- 绕过伊朗网站（无需关闭VPN）
> 
> 3- 即使个人域名或Worker被屏蔽也能连接
> 
> 4- 提升所有运营商的质量和速度，特别是那些在Cloudflare上有问题的运营商
> 
> 5- 能打开所有网站，甚至是那些在Cloudflare上的网站（老的Worker有这个问题）
<br>

> [!TIP]
> WorkerLess配置可以打开很多被屏蔽的网站和应用程序！如YouTube、Twitter、Google Play和其他被屏蔽的网站。但要注意，此配置不使用Worker，因此不会更改您的IP，不适合安全任务。Panel中的Fragment设置更改也会应用到此配置上，但不包括Chain Proxy。

> [!TIP]
> 最佳Fragment配置会应用18种不同的Fragment配置，选择对您的运营商速度最快的那种！这18种配置确保没有遗漏的范围，每分钟测试一次所有范围的配置并连接到最好的那个。

接下来我们会解释如何使用这些配置。高级Fragment设置请参见[这里](#3-1--Fragment设置/)。
<br><br>
### 2-1- 在移动设备上使用

<p align="center">
  <img src="assets/images/Fragment-Sub.jpg">
</p>

我们有一个表格，提供给v2rayNG、v2rayN和Streisand应用程序的订阅。
在应用中输入订阅的方法与普通订阅相同。

此订阅提供了与普通订阅相同数量的配置（带有您在Panel中应用的Fragment设置），以及**最佳延迟**配置。您在Panel中进行的任何设置，当您更新订阅时都会应用到所有配置上。

> [!CAUTION]
> 为避免问题，v2rayNG的版本至少需要1.8.19，v2rayN的版本至少需要6.42。

> [!NOTE]
>应用程序Nekobox和Hiddify Next不支持这些配置，因为Nekobox完全不支持Fragment。对于Hiddify Next应用程序，首先从普通订阅获取配置，然后在应用程序设置中按以下方式启用Fragment：

<p align="center">
  <img src="assets/images/Hiddify_fragment.jpg">
</p>
<br>

### 2-2- Warp订阅

<p align="center">
  <img src="assets/images/Warp-Configs.jpg">
</p>

此部分提供一个Warp配置，IP为Cloudflare伊朗，还有一个Warp on Warp（简称WoW）配置，IP为国外，还有一个Warp最佳延迟配置，它会连接到速度最快的Warp配置。默认情况下只有一个Warp和WoW配置，但如果编辑Warp Endpoints和WoW Endpoints部分，可以增加Warp配置的数量。

> [!CAUTION]
> 1- 请注意输入Endpoint时的格式为IP:Port或Domain:port，两者之间用逗号分隔。
> 
> 2- 输入IPv6时需放在[]内。参考如下例子：
> 
> 123.45.8.6:1701 , engage.cloudflareclient:2408 , [2a06:98c1:3120::3]:939

WoW配置在Xray内核上效果不佳。请确保使用扫描器找到适合您运营商的Endpoint。扫描器脚本在Panel内，复制后在Android的Termux上运行。每次更新Warp订阅时，Warp和WoW配置都会改变，但仍使用您的Endpoint。建议对于无法连接到Warp的运营商使用MahsaNG应用程序。
<br><br>
### 2-3- 在桌面上使用Fragment - Nekoray

<p align="center">
  <img src="assets/images/Fragment-Configs.jpg">
</p>

这一部分提供适用于Windows和Linux的Nekoray应用程序的Fragment配置。

如何导入到应用程序中？首先点击Copy Config，然后在Nekoray中：
>1. 右键点击
>2. 新建配置
>3. 类型选择 > 自定义（xray配置）
>4. 粘贴

在这里我们也有**最佳延迟**配置。
<br><br>
## 3 - 高级设置

### 3-1- Fragment设置

<p align="center">
  <img src="assets/images/Fragment-Settings.jpg">
</p>

这一部分是为Fragment配置设置的，不会影响普通配置。

Fragment配置有几个默认值，几乎适用于所有运营商。但假设您有一些经验，知道某些设置在您的运营商上效果更好，想要应用这些设置。您可以更改以下内容：

1. **DNS服务器** - 默认情况下，我将Adguard DNS设置为远程DNS（用于删除广告和垃圾邮件等）和Google DNS为本地DNS。即默认配置为：

>`Remote DNS: https://94.140.14.14/dns-query`
>
>`Local DNS: 8.8.8.8`

2. **Fragment参数** - 默认如下：

>`Length: 100-200`
>
>`Interval: 5-10`

您可以将Cloudflare的DNS（1.1.1.1）替换进来，或者调整其他参数，然后点击Apply。这样Fragment配置将根据您的设置提供。

> [!CAUTION]
> 请勿使用[https://1.1.1.1/dns-query](https://1.1.1.1/dns-query)作为远程DNS，因为它会增加延迟。

> [!NOTE]
> 您可以更改其中一个参数或全部更改。任何更改都会被保存，下次无需重新设置。

> [!IMPORTANT]
> Fragment参数有最大值，Length不能超过500，Interval不能超过30。

<br>

### 3-2- Chain Proxy设置

<p align="center">
  <img src="assets/images/Proxy_IP_settings.jpg">
</p>

我们之前提到过，可以设置一个Proxy IP，使IP在访问Cloudflare后的网站时保持固定，但在访问普通网站时，我们的IP仍然是Worker的，这也会每隔一段时间变化。为了让所有网站的IP都保持固定，我们增加了这个部分。您可以在此放置一个免费的VLESS配置，即使被过滤了（只要仅在伊朗被过滤仍能工作），也可以使您的IP保持不变。

> [!CAUTION]
> 1- 这个配置不能是Worker，否则您的最终IP仍会变化。
>
> 2- 获取免费配置有很多来源，我推荐[racevpn.com](https://racevpn.com)，它有时间限制，可以根据国家获取配置。您也可以使用[IRCF](https://ircfspace.github.io/tconfig/)的配置或[Telegram机器人](https://t.me

/Harry_Vpn_bot)获取免费的Trojan配置。

在空白处粘贴配置并点击Apply即可保存。Chain Proxy设置对所有普通和Fragment配置都适用。Chain Proxy配置只在伊朗被过滤时起作用。请确保应用Chain Proxy前您的VPN是关闭的，因为IP在过滤时只会更改。
<br><br>
### 3-3- 登录页面设置

<p align="center">
  <img src="assets/images/Login_Settings.jpg">
</p>

此部分用于设置Panel的登录名和密码，登录名和密码在此处更改后仍然会保留重置功能（重置会将它们恢复为默认设置），我们可以更改以下内容：

1. **用户名** - 如果您不想使用默认的admin，请更改用户名。
2. **密码** - 必须至少包含8个字符，其中至少一个大写字母和一个数字。

> [!IMPORTANT]
> 更改登录页面时请务必注意，因为如果密码忘记，Panel将不再可用。
<br><br>
### 3-4- 导入/导出设置

<p align="center">
  <img src="assets/images/Import_Export.jpg">
</p>

此部分用于从以前的设置导入数据或将设置导出为文件。您可以将这些设置从一个Panel导出到另一个Panel。导入设置时会覆盖所有当前设置。

> [!IMPORTANT]
> 这将重置密码、Fragment设置、Chain Proxy设置以及端口和IP设置。请在导入前确保已做好备份。
<br><br>
### 3-5- 清洁IP设置

<p align="center">
  <img src="assets/images/Clean-IP.jpg">
</p>

此部分是面向那些需要大量配置但不需要干净IP的人的，默认设置了6个随机IP。如果您想使用您自己的IP，您可以通过访问[https://iplocation.com](https://iplocation.com)来查看您的IP，您将看到所有可用的IP地址。您可以从这里选择一个无错误报告且未被屏蔽的IP并输入，然后点击Apply。
<br><br>
### 3-6- 端口设置

<p align="center">
  <img src="assets/images/Port-Settings.jpg">
</p>

此部分的主要功能是设置Port。默认情况下有6个端口，允许连接6种配置类型：1个普通配置，1个Fragment配置，1个最佳延迟配置，1个Warp配置，1个WoW配置，1个Nekoray配置。

> [!IMPORTANT]
> 您可以更改这些Port，只需确保没有重复的Port或使用默认的Port。如果更改，请同时更改普通配置和Fragment配置，因为它们通常是相同的。

您也可以添加新的Port。只需输入所需的Port，设置类型（普通/Fragment）并点击Apply即可。

### 3-7- 删除广告

此部分为删除Panel中的广告。广告将显示在Panel的右上角。
<br><br>
## 4 - 删除Panel

> [!WARNING]
> 删除Panel后将无法恢复！这是一个无法撤销的操作。删除时，所有配置、设置、端口、IP等信息将被完全删除。

> [!NOTE]
> Panel删除不影响您的Worker，它仍然可以工作，直到Cloudflare账户被封禁或您手动删除它。

对于删除Panel，请联系管理员。

---

如果有任何问题或需要进一步帮助，请随时告诉我！
