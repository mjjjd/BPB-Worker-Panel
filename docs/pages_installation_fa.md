<h1 align="center">通过 Cloudflare Pages 安装</h1>

## 介绍
可能你已经知道，使用 Worker 和 Pages 是在 Cloudflare 上搭建代理的两种方法。有趣的是，常用的 Worker 方法有一个限制，即每天最多只能发送十万次请求。当然，这个限制对于2-3个人的使用已经足够了。为了绕过这个限制，我们在 Worker 方法中连接了一个域名，这样就没有限制了（这似乎是 Cloudflare 的一个漏洞）。然而，Pages 没有这个限制。虽然在这个方法中我们使用了名为 Pages functions 的功能，但您仍会收到一封电子邮件，通知您已达到100k的使用容量。在这种情况下，即使您使用个人域名，您也会收到这封电子邮件。**但最终的经验表明，您的服务不会中断。**

另一个重要的优点是更新的便捷性。当项目代码更新时，您也可以轻松更新您的面板，而无需再次执行步骤。更多说明见[更新](#更新)部分。

此外，使用 Pages 的步骤更加简单，您甚至可以在手机上轻松完成这些操作。<br><br>

## 第一步 - Github
在 [Github](https://github.com/signup) 网站上创建一个帐户（注册只需要一个电子邮件）。使用您的 GitHub 凭据登录。

然后，访问 GitHub 的 [BPB-Worker-Panel](https://github.com/bia-pain-bache/BPB-Worker-Panel) 页面，并点击上方的 Fork 按钮。
<br><br>
<p align="center">
  <img src="assets/images/Fork_repo.jpg">
</p>

在下一页中不要更改任何内容，点击 Create Fork。好了，我们在 GitHub 上的工作完成了。
<br><br>
## 第二步 - 创建 Cloudflare KV
如果您没有 Cloudflare 帐户，可以从[这里](https://dash.cloudflare.com/sign-up)创建一个帐户（这里同样只需要一个电子邮件）。在您的 Cloudflare 帐户中，从左侧菜单中进入 KV 部分：

<p align="center">
  <img src="assets/images/Nav_dash_kv.jpg">
</p>

点击 `Create a namespace` 并为其命名，然后点击 Add。
<br><br>
## 第三步 - Cloudflare Pages
现在进入 `Workers and Pages` 部分，像创建 Worker 那样点击 `Create Application`。不同的是这次我们选择 `Pages`：

<p align="center">
  <img src="assets/images/Pages_application.jpg">
</p>

在这里点击 `Connect to Git` 并进入下一步：

<p align="center">
  <img src="assets/images/Connect_to_git.jpg">
</p>

在这里点击 `BPB-Worker-Panel` 使其激活，然后点击 `Begin Setup`。下一步中有一个 `Project Name`，这将成为您的面板域名，一定要更改为一个您喜欢的名字。在这里与 Worker 有些不同，如果您想更改 UUID 或 Proxy IP，您无法直接在代码中更改。如果想使用默认的面板设置，那没问题；否则请先阅读[高级设置（可选）](#高级设置（可选）)部分，然后继续。

现在您可以点击 `Save and Deploy`。
等待几秒钟，直到项目安装完成，点击 `Continue to Project` 进入项目页面。

现在根据下面的图片进入 `Settings` 部分，然后点击 `Functions`：

<p align="center">
  <img src="assets/images/Settings_functions.jpg">
</p>

像 Worker 一样，在页面中找到 `KV namespace bindings` 部分，点击 `Add binding`，并将 `Variable name` 设置为 `bpb`（如图所示），然后选择您在第二步中创建的 KV 命名空间并保存。

<p align="center">
  <img src="assets/images/Pages_bind_kv.jpg">
</p>

我们与 KV 的工作完成了，现在只需再次部署以应用 KV 的更改。

从上方导航栏返回 `Deployment` 部分，从 `Production` 部分进入 `view details`：

<p align="center">
  <img src="assets/images/Pages_production_details.jpg">
</p>

现在在 `Deployment detail` 部分点击 `Manage Deployment` 并选择 `Retry deployment`：

<p align="center">
  <img src="assets/images/Pages_retry_deployment.jpg">
</p>

等待几秒钟，直到完成所有步骤，我们的工作就完成了！

点击返回，并在 `Production` 部分点击 `visit site`，然后在末尾加上 `panel/`，进入面板。配置和提示的教学内容也在[主要教程](configuration_fa.md)中。安装完成，接下来的说明可能不适合所有人！
<br><br>
## 高级设置（可选）
您可能已经注意到我们没有提到更改 UUID 和 Proxy IP 的事情，因为您可以直接使用面板的默认设置而无需进行这一步的操作。
<br><br>

**更改 UUID：**

如您所知，UUID 类似于在共享链接和配置中使用的密码，如果需要，您可以更改它。更改此参数后，您的用户连接将中断，需要重新提供共享链接或配置。如果您在此步骤中未定义 UUID，代码将使用默认的 UUID。
<br><br>

**固定 Proxy IP：**

我们有一个问题，默认情况下，这段代码会使用大量的 IP Proxy，每次连接到 Cloudflare 背后的网站（涵盖了广泛的网络）时，它会随机选择一个新的 IP，导致 IP 不断变化。这种 IP 变化可能会给某些用户（尤其是交易者）带来问题。从版本 2.3.5 开始，您可以通过面板更改 Proxy IP，方法是应用设置并更新订阅就好了。但我建议您使用下文中描述的方法，因为：

> [!注意]
> 如果您通过面板应用 Proxy IP，并且该 IP 失效，您需要替换一个新的 IP 并更新订阅。意味着如果您已经捐赠了配置并更改了 Proxy IP，将没有意义，因为用户没有订阅来更新配置。因此，建议仅将此方法用于个人使用。而下文中提到的第二种方法的好处是它通过 Cloudflare 的控制面板进行，不需要更新配置。

<br>

要更改 UUID 和 Proxy IP，在同一页面（第三步，选择 BPB-Worker-Panel 的地方）中向下滚动，打开 `Environment variables (advanced)` 部分：

<p align="center">
  <img src="assets/images/Pages_env_vars.jpg">
</p>

在这里，您需要指定值。点击 `Add variable`，在第一个框中输入 `UUID`（大写），然后从[这里](https://www.uuidgenerator.net/)获取一个 UUID 并放在第二个框中。

现在再次点击 `Add variable`，在第一个框中输入 `PROXYIP`（大写），IP 可以从下面的链接获取，打开这些链接可以看到一些 IP，您可以检查它们的国家并选择一个：

>[Proxy IP](https://www.nslookup.io/domains/cdn.xn--b6gac.eu.org/dns-records/)

>[Proxy IP](https://www.nslookup.io/domains/cdn-all.xn--b6gac.eu.org/dns-records/)

<p align="center">
  <img src="assets/images/Proxy_ips.jpg">
</p>
<br>

## 更新：
与 Worker 相比，Pages 的一个优势是，当代码发布更新时，您不需要再次下载新的 worker.js 文件并重新开始！实际上，您甚至不需要访问 Cloudflare。只需进入您的 GitHub，进入 `BPB-Worker-Panel` 仓库，然后点击 `Sync fork`：

<p align="center">
  <img src="assets/images/Sync_fork.jpg">
</p>

然后点击 `Update branch`，就完成了。好处是，Cloudflare Pages 会自动检测到更新，并在大约1分钟后自动为您更新。
