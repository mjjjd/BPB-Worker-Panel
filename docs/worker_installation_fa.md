<h1 align="center">安装 Cloudflare Workers</h1>

首先，从 [这里](https://github.com/bia-pain-bache/BPB-Worker-Panel/releases/latest/download/worker.js) 下载 Worker 代码并将其上传到 Cloudflare Workers 仪表板（因为代码量很大，使用手机复制粘贴非常困难，请参考下图上传）。

<p align="center">
  <img src="assets/images/Worker_mobile_upload.jpg">
</p>

面板默认使用 UUID 和代理 IP 进行工作，您可以继续进行下一步。但如果您想要进行更改，请转到 [高级设置](#高级设置-可选) 部分。

最后，保存并部署 Worker。
现在返回到 Workers 仪表板并按照以下步骤操作：

<p align="center">
  <img src="assets/images/Navigate_worker_dash.jpg">
</p>

进入“KV”页面：

<p align="center">
  <img src="assets/images/Nav_dash_kv.jpg">
</p>

在 KV 部分点击“创建一个命名空间”，输入自定义名称（例如 Test）并点击“添加”。

再次回到左侧菜单，进入“Workers & Pages”，打开您创建的 Worker，转到“设置”和“变量”。向下滚动至“KV 命名空间绑定”，点击“添加绑定”，按照下图选择右侧的 KV（例如 Test）。左侧必须为 `bpb`，然后保存并部署。

<p align="center">
  <img src="assets/images/Bind_kv.jpg">
</p>

例如，假设您的 Worker 域名是 worker-polished-leaf-d022.workers.dev，在其后加上 `panel/` 进入面板。例如：

>`https://worker-polished-leaf-d022.workers.dev/panel`

首先进入登录页面，输入默认密码 `admin` 即可访问面板。

安装完成，以下内容可能不适用于所有用户。
有关配置和提示，请参阅[原始教程](configuration_fa.md)。

## 高级设置（可选）

到目前为止，我们没有提到如何更改 UUID 和代理 IP，因为您可以使用面板的默认设置。但是，如果您想要更改它们，可以按照以下步骤操作。建议至少更改 UUID。

### 1- 更改 UUID

如您所知，UUID 就像密码一样用于共享链接和配置。如果需要更改，断开用户连接，重新分享链接或配置。如果在此阶段未定义此参数，则代码将使用默认 UUID。

在第9行有一个 UUID，您可以从 [这里](https://www.uuidgenerator.net/) 复制新的 UUID，然后粘贴到第10行的旧位置，并保存并部署 Worker。

### 2- 固定代理 IP

我们面临的问题是默认情况下，此代码会随机选择多个 IP 代理，用于连接到 Cloudflare 后端网站（包括大部分网络）。这种随机更换 IP 可能会引起某些问题（尤其是交易者）。从版本2.3.5开始，您可以通过面板完成此操作，只需应用更新并完成。但是，建议您使用以下方法，因为：

> [!CAUTION]
> 如果通过面板更改 Proxy IP 并且该 IP 失效，您需要找到并更新链接或配置。如果您已经分发了配置，则更改 Proxy IP 不会有任何效果，因为用户没有配置更新的能力。因此，建议仅个人消费使用此方法。但是，以下方法的好处是可以通过 Cloudflare 仪表板完成，无需更新配置。

打开以下两个链接（代码行12和13中也有）显示了一些 IP 可以选择，您可以检查其国家并选择一个。

>[Proxy IP](https://www.nslookup.io/domains/cdn.xn--b6gac.eu.org/dns-records/)

>[Proxy IP](https://www.nslookup.io/domains/cdn-all.xn--b6gac.eu.org/dns-records/)

<p align="center">
  <img src="assets/images/Proxy_ips.jpg">
</p>

第14行的文本看起来像这样：

```javascript
const proxyIPs = ['cdn.xn--b6gac.eu.org', 'cdn-all.xn--b6gac.eu.org', 'edgetunnel.anycast.eu.org'];
```

当您准备好添加 IP 时，更改为以下内容：

```javascript
const proxyIPs = ['8.218.149.193'];
```

保存并部署 Worker。

> [!WARNING]
> 请注意，这些 IP 数量较多，可能有许多已失效。请进行测试以找到最佳解决方案。

> [!CAUTION]
> 如果使用单个 IP，可能会导致其失效并且很多网站无法访问。必须重新进行所有操作。
