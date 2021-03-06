project_path: /web/_project.yaml
book_path: /web/fundamentals/_book.yaml
description:在迁移到 HTTPS 时，开发者面对两个难题，即概念和术语。本指南将为您简要介绍概念和术语。

{# wf_updated_on:2016-08-22 #}
{# wf_published_on:2015-03-27 #}

# 重要的安全术语 {: .page-title }

{% include "web/_shared/contributors/chrispalmer.html" %}
{% include "web/_shared/contributors/mattgaunt.html" %}
  
### TL;DR {: .hide-from-toc }

* 公钥/私钥用于给浏览器与服务器之间的消息签名并将消息解密。
* 证书颁发机构 (CA) 是一个组织，对公钥与公共 DNS 名称（例如“www.foobar.com”）之间的映射进行证实。
* 证书签名请求 (CSR) 是一种数据格式，将一个公钥与拥有该公钥的实体的某些相关元数据绑定在一起

## 什么是公钥和私钥对？

**公钥/私钥对**是一对很大的数字，可用作加密密钥和解密密钥，并且共用一种特别的数学关系。一种常见的密钥对系统是 **[RSA 加密系统](https://en.wikipedia.org/wiki/RSA_(cryptosystem)){: .external}**。
**公钥**用于加密消息，并且消息只能使用对应的**私钥**来解密。您的网络服务器将其公钥公布到全球，客户端（例如网络浏览器）将使用此密钥来建立一个与您的服务器安全通信的通道。



## 什么是证书颁发机构？

**证书颁发机构 (CA)** 是一个组织，对公钥和与公共 DNS 名称（例如“www.foobar.com”）之间的映射进行证实。例如，客户端如何知道特定公钥是否为 www.foobar.com 的真实公钥？按理说，无法知道。CA 证实特定密钥是特定网站的真实密钥，它使用自己的私钥来**[加密签名](https://en.wikipedia.org/wiki/RSA_(cryptosystem)#Signing_messages){: .external}**该网站的公钥。此签名在计算上是无法伪造的。浏览器（和其他客户端）维护**信任锚存储库**，它包含知名 CA 拥有的公钥，并且它们使用这些公钥来**加密验证** CA 的签名。




**X.509 证书**是一种数据格式，将一个公钥与拥有该公钥的实体的某些相关元数据绑定在一起。
就网络而言，密钥的所有者是网站运营商，并且重要的元数据是网络服务器的 DNS 名称。当客户端连接 HTTPS 网络服务器时，网络服务器提供其证书供客户端验证。
客户端验证此证书没有过期，DNS 名称与客户端正尝试连接的服务器名称一致，并且已知的信任锚 CA 已给此证书签名。在大多数情况下，CA 并不直接给网络服务器证书签名；通常有一个**证书链**将一个信任锚链接到一个或多个中间签名者，最终链接到网络服务器自己的证书（**终端实体**）。




## 什么是证书签名请求？

**证书签名请求 (CSR)** 是一种数据格式，就像证书，将一个公钥与拥有该公钥的实体的某些相关元数据绑定在一起。但是，客户端并不解释 CSR；由 CA 解释。当您希望让 CA 证实您的网络服务器公钥时，就向 CA 发送 CSR。
CA 验证 CSR 中的信息，并使用它来生成证书。然后 CA 向您发送最终证书，您在网络服务器上安装该证书（或更可能是证书链）和私钥。





{# wf_devsite_translation #}
