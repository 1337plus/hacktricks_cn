# Certificates

<details>

<summary><strong>Support HackTricks and get benefits!</strong></summary>

<summary> <strong>支持hacktricks并获得好处！</strong> </summary>

- Do you work in a **cybersecurity company**? Do you want to see your **company advertised in HackTricks**? or do you want to have access to the **latest version of the PEASS or download HackTricks in PDF**? Check the [**SUBSCRIPTION PLANS**](https://github.com/sponsors/carlospolop)!

 - 您在**网络安全公司**工作吗？ 您是否想看到您的**公司在hacktricks **中刊登广告？ 还是您想访问**最新版本的豌豆或在pdf **中下载hacktricks？ 检查[**订阅计划**]（https://github.com/sponsors/carlospolop）！

- Discover [**The PEASS Family**](https://opensea.io/collection/the-peass-family), our collection of exclusive [**NFTs**](https://opensea.io/collection/the-peass-family)

 - 发现[**豌豆家庭**]（https://opensea.io/collection/the-peass-family），我们的独家[** nfts **]（https://opensea.io/collection） /家庭家庭）

- Get the [**official PEASS & HackTricks swag**](https://peass.creator-spring.com)

 - 获取[**官方豌豆和hacktricks赃物**]（https://peass.creator-spring.com）

- **Join the** [**💬**](https://emojipedia.org/speech-balloon/) [**Discord group**](https://discord.gg/hRep4RUj7f) or the [**telegram group**](https://t.me/peass) or **follow** me on **Twitter** [**🐦**](https://github.com/carlospolop/hacktricks/tree/7af18b62b3bdc423e11444677a6a73d4043511e9/\[https:/emojipedia.org/bird/README.md)[**@carlospolopm**](https://twitter.com/carlospolopm)**.**

 -  **加入** [**💬**]（https://emojipedia.org/speech-balloon/）[** discord group **]（https://discord.gg/hrep4ruj7f）或[ **电报组**]（https://t.me/peass）或**在** Twitter ** [**🐦**]（https://github.com/carloppolop/hacktrickss on ** twitter **） /ree/7af18b62b3bdc423e114444444677a6a73d4043511e9/ \ [https:/emojipedia.org/bird/bird/readme.md）eardme.md）eghterme.md）eghterme.md）eghterme.md）eghtemplopmbyth

- **Share your hacking tricks by submitting PRs to the** [**hacktricks github repo**](https://github.com/carlospolop/hacktricks)**.**

 -  **通过将PRS提交给** [** hacktricks github repo **]（https://github.com/carloppolop/hacktricks）**。

</details>

{% hint style="danger" %}
<img src="../.gitbook/assets/image (307).png" alt="" data-size="original">

<img src =“ ../。gitbook/assets/image（307）.png“ alt =”“ data-size =“ ointern”>
Through Security Skills as a Service, we help organizations to **defend against the Dark Hacking Arts**. Security Skills as a Service is an offensive cybersecurity consultancy model that combines an Intelligent Platform with the top-class, globally distributed, offensive security engineers, delivering **high-quality penetration testing results. Security Hubs** bring together offensive penetration testing tactics with human behavioral science, providing real-time insights into threat actors' tradecraft and a **complete assessment of any risks**.

通过安全技能作为服务，我们帮助组织**防御黑暗黑客艺术**。 安全技能作为服务是一种进攻性网络安全咨询模型，将智能平台与顶级，全球分布式，进攻性安全工程师结合在一起，提供**高质量的渗透测试结果。 安全枢纽**将进攻性渗透测试策略与人类行为科学结合在一起，提供对威胁参与者贸易克罗夫特（Tradecraft）的实时见解，并对任何风险**进行完整评估。

{% embed url="https://securityhubs.io/" %}
{% endhint %}

## What is a Certificate

##什么是证书

In cryptography, a **public key certificate,** also known as a **digital certificate** or **identity certificate,** is an electronic document used to prove the ownership of a public key. The certificate includes information about the key, information about the identity of its owner (called the subject), and the digital signature of an entity that has verified the certificate's contents (called the issuer). If the signature is valid, and the software examining the certificate trusts the issuer, then it can use that key to communicate securely with the certificate's subject.

在密码学中，**公共密钥证书，**也称为**数字证书**或**身份证书，**是一种电子文档，用于证明公共密钥的所有权。 该证书包括有关密钥的信息，有关其所有者身份（称为主题）的信息以及已验证证书内容的实体的数字签名（称为发行者）。 如果签名有效，并且检查证书的软件信任发行人，则可以使用该键与证书的主题安全通信。

In a typical [public-key infrastructure](https://en.wikipedia.org/wiki/Public-key\_infrastructure) (PKI) scheme, the certificate issuer is a [certificate authority](https://en.wikipedia.org/wiki/Certificate\_authority) (CA), usually a company that charges customers to issue certificates for them. By contrast, in a [web of trust](https://en.wikipedia.org/wiki/Web\_of\_trust) scheme, individuals sign each other's keys directly, in a format that performs a similar function to a public key certificate.

在典型的[public-key基础架构]（https://en.wikipedia.org/wiki/wiki/public-key \_Infrastructure）（PKI）方案（PKI）方案，证书发行人是[证书授权]（https：// en.wikipedia excipert 。 相比之下，在[https://en.wikipedia.org/wiki/web \_of_trust）方案中，个人直接互相签名 证书。

The most common format for public key certificates is defined by [X.509](https://en.wikipedia.org/wiki/X.509). Because X.509 is very general, the format is further constrained by profiles defined for certain use cases, such as [Public Key Infrastructure (X.509)](https://en.wikipedia.org/wiki/PKIX) as defined in RFC 5280.

公共密钥证书的最常见格式由[X.509]（https://en.wikipedia.org/wiki/x.509）定义。 因为X.509非常通用，因此格式进一步受到某些用例定义的配置文件，例如[公共密钥基础架构（X.509）]（https://en.wikipedia.org/wiki/pkix）为定义 在RFC 5280中。

## x509 Common Fields

## x509普通字段

* **Version Number:** Version of x509 format.

***版本号：** X509格式的版本。
* **Serial Number**: Used to uniquely identify the certificate within a CA's systems. In particular this is used to track revocation information.

***序列号**：用于唯一标识CA系统中的证书。 特别是这用于跟踪撤销信息。
* **Subject**: The entity a certificate belongs to: a machine, an individual, or an organization.

***主题**：证书属于：机器，个人或组织的实体。
  * **Common Name**: Domains affected by the certificate. Can be 1 or more and can contain wildcards.

***通用名称**：受证书影响的域。 可以是1或更多，可以包含通配符。
  * **Country (C)**: Country

***国家（C）**：国家
  * **Distinguished name (DN)**: The whole subject: `C=US, ST=California, L=San Francisco, O=Example, Inc., CN=shared.global.example.net`

***杰出名称（DN）**：整个主题：`c =我们，st = california，l =旧金山，o = example，inc.，cn = sharone.global.global.example.net`
  * **Locality (L)**: Local place

***局部（L）**：本地地方
  * **Organization (O)**: Organization name
  * **Organizational Unit (OU)**: Division of an organisation (like "Human Resources").

***组织部门（OU）**：组织的部门（例如“人力资源”）。
  * **State or Province (ST, S or P)**: List of state or province names

***州或省（ST，S或P）**：州或省份名单清单
* **Issuer**: The entity that verified the information and signed the certificate.

***发行人**：验证信息并签署证书的实体。
  * **Common Name (CN)**: Name of the certificate authority

***通用名（CN）**：证书授权的名称
  * **Country (C)**: Country of the certificate authority

***国家（C）**：证书局的国家
  * **Distinguished name (DN)**: Distinguished name of the certificate authority

***杰出名称（DN）**：证书授权的杰出名称
  * **Locality (L)**: Local place where the organisation can be found.

***局部（l）**：可以找到组织的本地地方。
  * **Organization (O)**: Organisation name
  * **Organizational Unit (OU)**: Division of an organisation (like "Human Resources").

***组织部门（OU）**：组织的部门（例如“人力资源”）。
* **Not Before**: The earliest time and date on which the certificate is valid. Usually set to a few hours or days prior to the moment the certificate was issued, to avoid [clock skew](https://en.wikipedia.org/wiki/Clock\_skew#On\_a\_network) problems.

***在**之前没有：证书有效的最早时间和日期。 通常设置为确保证书的那一刻之前的几个小时或几天，以避免[clock skew]（https://en.wikipedia.org/wiki/clock/clock_skew#un \ _a \ _network）问题。
* **Not After**: The time and date past which the certificate is no longer valid.

***不追随**：证书不再有效的时间和日期。
* **Public Key**: A public key belonging to the certificate subject. (This is one of the main parts as this is what is signed by the CA)

***公钥**：属于证书主题的公钥。 （这是主要部分之一，因为这是CA签名的）
  * **Public Key Algorithm**: Algorithm used to generate the public key. Like RSA.

***公钥算法**：用于生成公钥的算法。 像RSA。
  * **Public Key Curve**: The curve used by the elliptic curve public key algorithm (if apply). Like nistp521.

***公钥曲线**：椭圆曲线公共密钥算法使用的曲线（如果适用）。 像NISTP521一样。
  * **Public Key Exponent**: Exponent used to derive the public key (if apply). Like 65537.

***公钥指数**：用于得出公共密钥的指数（如果适用）。 像65537。
  * **Public Key Size**: The size of the public key space in bits. Like 2048.

***公钥尺寸**：位于位的公共密钥空间的大小。 像2048年。
  * **Signature Algorithm**: The algorithm used to sign the public key certificate.

***签名算法**：用于签署公共密钥证书的算法。
  * **Signature**: A signature of the certificate body by the issuer's private key.

***签名**：发行人的私钥签名证书正文。
* **x509v3 extensions**
  * **Key Usage**: The valid cryptographic uses of the certificate's public key. Common values include digital signature validation, key encipherment, and certificate signing.

***密钥用法**：证书公钥的有效加密用途。 共同值包括数字签名验证，密钥代码和证书签名。
    * In a Web certificate this will appear as a _X509v3 extension_ and will have the value `Digital Signature`

*在Web证书中，这将显示为_x509v3 Extension_，并将具有``数字签名''
  * **Extended Key Usage**: The applications in which the certificate may be used. Common values include TLS server authentication, email protection, and code signing.

***扩展密钥用法**：可以使用证书的应用程序。 共同值包括TLS服务器身份验证，电子邮件保护和代码签名。
    * In a Web certificate this will appear as a _X509v3 extension_ and will have the value `TLS Web Server Authentication`

*在Web证书中，这将显示为_x509v3 Extension_，并将具有`tls Web服务器身份验证'的值
  * **Subject Alternative Name:** Allows users to specify additional host **names** for a single SSL **certificate**. The use of the SAN extension is standard practice for SSL certificates, and it's on its way to replacing the use of the common **name**.

***主题替代名称：**允许用户为单个SSL **证书指定其他主机**名称** **。 SAN扩展的使用是SSL证书的标准实践，它正在替换使用Common **名称**的方式。
  * **Basic Constraint:** This extension describes whether the certificate is a CA certificate or an end entity certificate. A CA certificate is something that signs certificates of others and a end entity certificate is the certificate used in a web page for example (the last par of the chain).

***基本约束：**此扩展名描述证书是CA证书还是最终实体证书。 CA证书是签署他人证书的东西，而最终实体证书是网页中使用的证书（链的最后一个标准）。
  * **Subject Key Identifier** (SKI): This extension declares a unique **identifier** for the public **key** in the certificate. It is required on all CA certificates. CAs propagate their own SKI to the Issuer **Key Identifier** (AKI) extension on issued certificates. It's the hash of the subject public key.

***主题密钥标识符**（滑雪）：此扩展程序为公共**键**唯一**标识符** **键** **。 所有CA证书都需要。 CAS将自己的滑雪板传播到发行者**密钥标识符**（aki）延长的发行证书。 这是主题公钥的哈希。
  * **Authority Key Identifier**: It contains a key identifier which is derived from the public key in the issuer certificate. It's the hash of the issuer public key.

***权限密钥标识符**：它包含一个密钥标识符，该标识符是从发行人证书中的公钥中得出的。 这是发行人公钥的哈希。
  * **Authority Information Access** (AIA): This extension contains at most two types of information :

***权限信息访问**（AIA）：此扩展名最多包含两种类型的信息：
    * Information about **how to get the issuer of this certificate** (CA issuer access method)

*有关**如何获得此证书的发行人**（CA发行者访问方法）的信息
    * Address of the **OCSP responder from where revocation of this certificate** can be checked (OCSP access method).

*可以检查** ocsp响应者的地址。
  * **CRL Distribution Points**: This extension identifies the location of the CRL from which the revocation of this certificate can be checked. The application that processes the certificate can get the location of the CRL from this extension, download the CRL and then check the revocation of this certificate.

*** CRL分配点**：此扩展名确定可以检查该证书的CRL的位置。 处理证书的应用程序可以从此扩展程序中获取CRL的位置，下载CRL，然后检查该证书的撤销。
  * **CT Precertificate SCTs**: Logs of Certificate transparency regarding the certificate

*** ct practificate scts **：证书透明度的日志

### Difference between OCSP and CRL Distribution Points

### OCSP和CRL分配点之间的差异

**OCSP** (RFC 2560) is a standard protocol that consists of an **OCSP client and an OCSP responder**. This protocol **determines revocation status of a given digital public-key certificate** **without** having to **download** the **entire CRL**.\

** OCSP **（RFC 2560）是由** OCSP客户端和OCSP响应者**组成的标准协议。 此协议**确定给定数字公开键证书的撤销状态** **无需**必须**下载** **整个CRL **。\ \ \ \ \ \
**CRL** is the **traditional method** of checking certificate validity. A **CRL provides a list of certificate serial numbers** that have been revoked or are no longer valid. CRLs let the verifier check the revocation status of the presented certificate while verifying it. CRLs are limited to 512 entries.\

** crl **是检查证书有效性的**传统方法**。 A ** CRL提供了已被撤销或不再有效的证书序列号**列表。 CRL让验证者在验证其验证时检查吊销证书的撤销状态。 CRL仅限于512个条目。
From [here](https://www.arubanetworks.com/techdocs/ArubaOS%206\_3\_1\_Web\_Help/Content/ArubaFrameStyles/CertRevocation/About\_OCSP\_and\_CRL.htm).

来自[此处]（https://www.arubanetworks.com/techdocs/arubaos%206 \ _3 \_web_web \_web \ _help/content/arubaframesty/arubaframestyles/certrevocation/certrevocation/certrevocation/about \ out \ _ocspssp \ _and_andththtm）。

### What is Certificate Transparency

###什么是证书透明度

Certificate Transparency aims to remedy certificate-based threats by **making the issuance and existence of SSL certificates open to scrutiny by domain owners, CAs, and domain users**. Specifically, Certificate Transparency has three main goals:

证书透明度旨在通过**使域所有者，CAS和域用户的审查的SSL证书的发行和存在来纠正基于证书的威胁。 具体而言，证书透明度具有三个主要目标：

* Make it impossible (or at least very difficult) for a CA to **issue a SSL certificate for a domain without the certificate being visible to the owner** of that domain.

*使CA **在没有该域的所有者**可见的情况下为域发布SSL证书，使其不可能（或至少很困难）。
* Provide an **open auditing and monitoring system that lets any domain owner or CA determine whether certificates have been mistakenly or maliciously** issued.

*提供一个**开放审计和监视系统，使任何域名所有者或CA确定是否已误以为或恶意**签发证书。
* **Protect users** (as much as possible) from being duped by certificates that were mistakenly or maliciously issued.

***保护用户**（尽可能多）被错误或恶意颁发的证书欺骗。

#### **Certificate Logs**

#### **证书日志**

Certificate logs are simple network services that maintain **cryptographically assured, publicly auditable, append-only records of certificates**. **Anyone can submit certificates to a log**, although certificate authorities will likely be the foremost submitters. Likewise, anyone can query a log for a cryptographic proof, which can be used to verify that the log is behaving properly or verify that a particular certificate has been logged. The number of log servers doesn’t have to be large (say, much less than a thousand worldwide), and each could be operated independently by a CA, an ISP, or any other interested party.

证书日志是简单的网络服务，可维护**密码保证，公开审核，仅附加证书记录**。 **任何人都可以向日志提交证书**，尽管证书机构可能是最重要的提交者。 同样，任何人都可以查询日志以获取加密证明，可以用来验证日志的行为正确或验证特定证书是否已记录。 日志服务器的数量不一定要大（例如，在全球范围内少得多），并且每个人都可以由CA，ISP或任何其他感兴趣的方独立操作。

#### Query

＃＃＃＃ 询问

You can query the logs of Certificate Transparency of any domain in [https://crt.sh/](https://crt.sh).

您可以查询[https://crt.sh/]（https://crt.sh）中任何域的证书透明度的日志。

## Formats

There are different formats that can be used to store a certificate.

有不同的格式可用于存储证书。

#### **PEM Format**

#### ** PEM格式**

* It is the most common format used for certificates

*这是证书最常见的格式
* Most servers (Ex: Apache) expects the certificates and private key to be in a separate files\

*大多数服务器（ex：apache）期望证书和私钥在单独的文件中\
  \- Usually they are Base64 encoded ASCII files\

\  - 通常它们是基本64编码的ASCII文件\
  \- Extensions used for PEM certificates are .cer, .crt, .pem, .key files\

\  - 用于PEM证书的扩展名是.cer，.crt，.pem，.key Files \
  \- Apache and similar server uses PEM format certificates

\  -  Apache和类似的服务器使用PEM格式证书

#### **DER Format**

#### ** der格式**

* The DER format is the binary form of the certificate

* der格式是证书的二进制形式
* All types of certificates & private keys can be encoded in DER format

*所有类型的证书和私钥可以以DER格式编码
* DER formatted certificates do not contain the "BEGIN CERTIFICATE/END CERTIFICATE" statements

*格式的证书不包含“开始证书/结束证书”语句
* DER formatted certificates most often use the ‘.cer’ and '.der' extensions

*格式的证书最常使用“ .cer”和“ .der”扩展名
* DER is typically used in Java Platforms

* der通常在Java平台中使用

#### **P7B/PKCS#7 Format**

#### ** P7B/PKCS＃7格式**

* The PKCS#7 or P7B format is stored in Base64 ASCII format and has a file extension of .p7b or .p7c

* PKCS＃7或P7B格式以Base64 ASCII格式存储，并具有.p7b或.p7c的文件扩展名
* A P7B file only contains certificates and chain certificates (Intermediate CAs), not the private key

* P7B文件仅包含证书和链证书（中级CAS），而不是私钥
* The most common platforms that support P7B files are Microsoft Windows and Java Tomcat

*支持P7B文件的最常见平台是Microsoft Windows和Java Tomcat

#### **PFX/P12/PKCS#12 Format**

#### ** PFX/P12/PKCS＃12格式**

* The PKCS#12 or PFX/P12 format is a binary format for storing the server certificate, intermediate certificates, and the private key in one encryptable file

* PKCS＃12或PFX/P12格式是用于存储服务器证书，中间证书和私钥的二进制格式
* These files usually have extensions such as .pfx and .p12

*这些文件通常具有.pfx和.p12之类的扩展名
* They are typically used on Windows machines to import and export certificates and private keys

*它们通常在Windows机器上用于导入和导出证书和私钥

### Formats conversions

###格式转换

**Convert x509 to PEM**

**将X509转换为PEM **

```
openssl x509 -in certificatename.cer -outform PEM -out certificatename.pem
```

#### **Convert PEM to DER**

#### **将PEM转换为der **

```
openssl x509 -outform der -in certificatename.pem -out certificatename.der
```

**Convert DER to PEM**

**将der转换为PEM **

```
openssl x509 -inform der -in certificatename.der -out certificatename.pem
```

**Convert PEM to P7B**

**将PEM转换为P7B **

**Note:** The PKCS#7 or P7B format is stored in Base64 ASCII format and has a file extension of .p7b or .p7c. A P7B file only contains certificates and chain certificates (Intermediate CAs), not the private key. The most common platforms that support P7B files are Microsoft Windows and Java Tomcat.

**注意：** PKCS＃7或P7B格式以Base64 ASCII格式存储，并具有.p7b或.p7c的文件扩展名。 P7B文件仅包含证书和链证书（中级CAS），而不是私钥。 支持P7B文件的最常见平台是Microsoft Windows和Java Tomcat。

```
openssl crl2pkcs7 -nocrl -certfile certificatename.pem -out certificatename.p7b -certfile CACert.cer
```

**Convert PKCS7 to PEM**

**将PKCS7转换为PEM **

```
openssl pkcs7 -print_certs -in certificatename.p7b -out certificatename.pem
```

**Convert pfx to PEM**

**将PFX转换为PEM **

**Note:** The PKCS#12 or PFX format is a binary format for storing the server certificate, intermediate certificates, and the private key in one encryptable file. PFX files usually have extensions such as .pfx and .p12. PFX files are typically used on Windows machines to import and export certificates and private keys.

**注意：** PKCS＃12或PFX格式是用于存储服务器证书，中间证书和私钥的二进制格式。 PFX文件通常具有.pfx和.p12之类的扩展名。 PFX文件通常在Windows机器上用于导入和导出证书和私钥。

```
openssl pkcs12 -in certificatename.pfx -out certificatename.pem
```

**Convert PFX to PKCS#8**\

**将PFX转换为PKCS＃8 ** \
**Note:** This requires 2 commands

**注意：**这需要2个命令

**1- Convert PFX to PEM**

** 1-将PFX转换为PEM **

```
openssl pkcs12 -in certificatename.pfx -nocerts -nodes -out certificatename.pem
```

**2- Convert PEM to PKCS8**

** 2-将PEM转换为PKCS8 **

```
openSSL pkcs8 -in certificatename.pem -topk8 -nocrypt -out certificatename.pk8
```

**Convert P7B to PFX**\

**将P7B转换为PFX ** \
**Note:** This requires 2 commands

**注意：**这需要2个命令

1- **Convert P7B to CER**

1- **将P7B转换为CER **

```
openssl pkcs7 -print_certs -in certificatename.p7b -out certificatename.cer
```

**2- Convert CER and Private Key to PFX**

** 2-将CER和私钥转换为PFX **

```
openssl pkcs12 -export -in certificatename.cer -inkey privateKey.key -out certificatename.pfx -certfile  cacert.cer
```

{% hint style="danger" %}
<img src="../.gitbook/assets/image (307).png" alt="" data-size="original">

<img src =“ ../。gitbook/assets/image（307）.png“ alt =”“ data-size =“ ointern”>

Through Security Skills as a Service, we help organizations to **defend against the Dark Hacking Arts**. Security Skills as a Service is an offensive cybersecurity consultancy model that combines an Intelligent Platform with the top-class, globally distributed, offensive security engineers, delivering **high-quality penetration testing results. Security Hubs** bring together offensive penetration testing tactics with human behavioral science, providing real-time insights into threat actors' tradecraft and a **complete assessment of any risks**.

通过安全技能作为服务，我们帮助组织**防御黑暗黑客艺术**。 安全技能作为服务是一种进攻性网络安全咨询模型，将智能平台与顶级，全球分布式，进攻性安全工程师结合在一起，提供**高质量的渗透测试结果。 安全枢纽**将进攻性渗透测试策略与人类行为科学结合在一起，提供对威胁参与者贸易克罗夫特（Tradecraft）的实时见解，并对任何风险**进行完整评估。

{% embed url="https://securityhubs.io/" %}
{% endhint %}

<details>

<summary><strong>Support HackTricks and get benefits!</strong></summary>

<summary> <strong>支持hacktricks并获得好处！</strong> </summary>

- Do you work in a **cybersecurity company**? Do you want to see your **company advertised in HackTricks**? or do you want to have access to the **latest version of the PEASS or download HackTricks in PDF**? Check the [**SUBSCRIPTION PLANS**](https://github.com/sponsors/carlospolop)!

 - 您在**网络安全公司**工作吗？ 您是否想看到您的**公司在hacktricks **中刊登广告？ 还是您想访问**最新版本的豌豆或在pdf **中下载hacktricks？ 检查[**订阅计划**]（https://github.com/sponsors/carlospolop）！

- Discover [**The PEASS Family**](https://opensea.io/collection/the-peass-family), our collection of exclusive [**NFTs**](https://opensea.io/collection/the-peass-family)

 - 发现[**豌豆家庭**]（https://opensea.io/collection/the-peass-family），我们的独家[** nfts **]（https://opensea.io/collection） /家庭家庭）

- Get the [**official PEASS & HackTricks swag**](https://peass.creator-spring.com)

 - 获取[**官方豌豆和hacktricks赃物**]（https://peass.creator-spring.com）

- **Join the** [**💬**](https://emojipedia.org/speech-balloon/) [**Discord group**](https://discord.gg/hRep4RUj7f) or the [**telegram group**](https://t.me/peass) or **follow** me on **Twitter** [**🐦**](https://github.com/carlospolop/hacktricks/tree/7af18b62b3bdc423e11444677a6a73d4043511e9/\[https:/emojipedia.org/bird/README.md)[**@carlospolopm**](https://twitter.com/carlospolopm)**.**

 -  **加入** [**💬**]（https://emojipedia.org/speech-balloon/）[** discord group **]（https://discord.gg/hrep4ruj7f）或[ **电报组**]（https://t.me/peass）或**在** Twitter ** [**🐦**]（https://github.com/carloppolop/hacktrickss on ** twitter **） /ree/7af18b62b3bdc423e114444444677a6a73d4043511e9/ \ [https:/emojipedia.org/bird/bird/readme.md）eardme.md）eghterme.md）eghterme.md）eghterme.md）eghtemplopmbyth

- **Share your hacking tricks by submitting PRs to the** [**hacktricks github repo**](https://github.com/carlospolop/hacktricks)**.**

 -  **通过将PRS提交给** [** hacktricks github repo **]（https://github.com/carloppolop/hacktricks）**。

</details>
