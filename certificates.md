

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


# What is a Certificate

＃什么是证书

In cryptography, a **public key certificate,** also known as a **digital certificate** or **identity certificate,** is an electronic document used to prove the ownership of a public key. The certificate includes information about the key, information about the identity of its owner \(called the subject\), and the digital signature of an entity that has verified the certificate's contents \(called the issuer\). If the signature is valid, and the software examining the certificate trusts the issuer, then it can use that key to communicate securely with the certificate's subject.

在密码学中，**公共密钥证书，**也称为**数字证书**或**身份证书，**是一种电子文档，用于证明公共密钥的所有权。 该证书包括有关密钥的信息，有关其所有者\（称为主题\）的身份的信息以及已验证证书内容\（称为发行者\）的实体的数字签名。 如果签名有效，并且检查证书的软件信任发行人，则可以使用该键与证书的主题安全通信。

In a typical [public-key infrastructure](https://en.wikipedia.org/wiki/Public-key_infrastructure) \(PKI\) scheme, the certificate issuer is a [certificate authority](https://en.wikipedia.org/wiki/Certificate_authority) \(CA\), usually a company that charges customers to issue certificates for them. By contrast, in a [web of trust](https://en.wikipedia.org/wiki/Web_of_trust) scheme, individuals sign each other's keys directly, in a format that performs a similar function to a public key certificate.

在典型的[public-key基础架构]（https://en.wikipedia.org/wiki/wiki/public-key_infrastructure）\（pki \）方案中，证书发行人是[证书当局]（https：//en.wikipedia] 。 相比之下，在[https://en.wikipedia.org/wiki/web_of_trust）方案中（https：//en.wikipedia.org/web_of_trust）中，个人直接以与公共密钥证书相似的函数的格式直接签名。

The most common format for public key certificates is defined by [X.509](https://en.wikipedia.org/wiki/X.509). Because X.509 is very general, the format is further constrained by profiles defined for certain use cases, such as [Public Key Infrastructure \(X.509\)](https://en.wikipedia.org/wiki/PKIX) as defined in RFC 5280.

公共密钥证书的最常见格式由[X.509]（https://en.wikipedia.org/wiki/x.509）定义。 因为X.509非常通用，因此格式进一步受到某些用例定义的配置文件，例如[公共密钥基础架构\（x.509 \）]（https://en.wikipedia.org/wiki/pkix） 如RFC 5280所定义。

# x509 Common Fields

＃x509公共字段

* **Version Number:** Version of x509 format.

***版本号：** X509格式的版本。
* **Serial Number**: Used to uniquely identify the certificate within a CA's systems. In particular this is used to track revocation information.

***序列号**：用于唯一标识CA系统中的证书。 特别是这用于跟踪撤销信息。
* **Subject**: The entity a certificate belongs to: a machine, an individual, or an organization.

***主题**：证书属于：机器，个人或组织的实体。
  * **Common Name**: Domains affected by the certificate. Can be 1 or more and can contain wildcards.

***通用名称**：受证书影响的域。 可以是1或更多，可以包含通配符。
  * **Country \(C\)**: Country

***国家 /地区\（C \）**：国家
  * **Distinguished name \(DN\)**: The whole subject: `C=US, ST=California, L=San Francisco, O=Example, Inc., CN=shared.global.example.net`

***杰出名称\（dn \）**：整个主题：`c = us，st = california，l =旧金山，o = example，inc.，cn = sharone.global.global.example.net`
  * **Locality \(L\)**: Local place

*** locality \（l \）**：本地地方
  * **Organization \(O\)**: Organization name

***组织\（O \）**：组织名称
  * **Organizational Unit \(OU\)**: Division of an organisation \(like "Human Resources"\).

***组织单位\（OU \）**：组织\的部门（例如“人力资源” \）。
  * **State or Province \(ST, S or P\)**: List of state or province names

***州或省\（ST，S或P \）**：州名称或省份名单
* **Issuer**: The entity that verified the information and signed the certificate.

***发行人**：验证信息并签署证书的实体。
  * **Common Name \(CN\)**: Name of the certificate authority

***通用名称\（cn \）**：证书授权的名称
  * **Country \(C\)**: Country of the certificate authority

***国家 /地区\（C \）**：证书授权国的国家
  * **Distinguished name \(DN\)**: Distinguished name of the certificate authority

***杰出名称\（dn \）**：证书授权的杰出名称
  * **Locality \(L\)**: Local place where the organisation can be found.

*** locality \（l \）**：可以找到组织的本地地方。
  * **Organization \(O\)**: Organisation name
  * **Organizational Unit \(OU\)**: Division of an organisation \(like "Human Resources"\).

***组织单位\（OU \）**：组织\的部门（例如“人力资源” \）。
* **Not Before**: The earliest time and date on which the certificate is valid. Usually set to a few hours or days prior to the moment the certificate was issued, to avoid [clock skew](https://en.wikipedia.org/wiki/Clock_skew#On_a_network) problems.

***在**之前没有：证书有效的最早时间和日期。 通常将证书发行的那一刻之前的几个小时或几天设置为避免[clock skew]（https://en.wikipedia.org/wiki/clock_skew#un_a_a_network）问题。
* **Not After**: The time and date past which the certificate is no longer valid.

***不追随**：证书不再有效的时间和日期。
* **Public Key**: A public key belonging to the certificate subject. \(This is one of the main parts as this is what is signed by the CA\)

***公钥**：属于证书主题的公钥。 \（这是主要部分之一，因为这是CA \签名的）
  * **Public Key Algorithm**: Algorithm used to generate the public key. Like RSA.

***公钥算法**：用于生成公钥的算法。 像RSA。
  * **Public Key Curve**: The curve used by the elliptic curve public key algorithm \(if apply\). Like nistp521.

***公钥曲线**：椭圆曲线公共密钥算法\（如果应用\）使用的曲线。 像NISTP521一样。
  * **Public Key Exponent**: Exponent used to derive the public key \(if apply\). Like 65537.

***公共密钥指数**：用于得出公共密钥\（如果应用\）的指数。 像65537。
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
  * **Subject Alternative Name:**  Allows users to specify additional host **names** for a single SSL **certificate**. The use of the SAN extension is standard practice for SSL certificates, and it's on its way to replacing the use of the common **name**.

***主题替代名称：**允许用户为单个SSL **证书指定其他主机**名称** **。 SAN扩展的使用是SSL证书的标准实践，它正在替换使用Common **名称**的方式。
  * **Basic Constraint:** This extension describes whether the certificate is a CA certificate or an end entity certificate. A CA certificate is something that signs certificates of others and a end entity certificate is the certificate used in a web page for example \(the last par of the chain\).

***基本约束：**此扩展名描述证书是CA证书还是最终实体证书。 CA证书是签署他人证书的东西，而最终实体证书是网页中使用的证书\（链的最后一个标准\）。
  *  **Subject Key Identifier** \(SKI\): This extension declares a unique **identifier** for the public **key** in the certificate. It is required on all CA certificates. CAs propagate their own SKI to the Issuer **Key Identifier** \(AKI\) extension on issued certificates. It's the hash of the subject public key.

***主题密钥标识符** \（SKI \）：此扩展名声明了证书中的公共**键**唯一**标识符**。 所有CA证书都需要。 CAS将自己的滑雪板传播到发行者**密钥标识符** \（aki \）延长的发行证书。 这是主题公钥的哈希。
  * **Authority Key Identifier**: It contains a key identifier which is derived from the public key in the issuer certificate. It's the hash of the issuer public key.

***权限密钥标识符**：它包含一个密钥标识符，该标识符是从发行人证书中的公钥中得出的。 这是发行人公钥的哈希。
  * **Authority Information Access** \(AIA\): This extension contains at most two types of information :

***权限信息访问** \（AIA \）：此扩展名最多包含两种类型的信息：
    * Information about **how to get the issuer of this certificate** \(CA issuer access method\)

*有关**如何获得此证书的发行人** \（CA发行者访问方法\）的信息
    * Address of the **OCSP responder from where revocation of this certificate** can be checked \(OCSP access method\).

*可以检查** ocsp响应者的地址。
  * **CRL Distribution Points**: This extension identifies the location of the CRL from which the revocation of this certificate can be checked. The application that processes the certificate can get the location of the CRL from this extension, download the CRL and then check the revocation of this certificate.

*** CRL分配点**：此扩展名确定可以检查该证书的CRL的位置。 处理证书的应用程序可以从此扩展程序中获取CRL的位置，下载CRL，然后检查该证书的撤销。

## Difference between OSCP and CRL Distribution Points

## OCSP和CRL分配点之间的差异

**OCSP** \(RFC 2560\) is a standard protocol that consists of an **OCSP client and an OCSP responder**. This protocol **determines revocation status of a given digital public-key certificate** **without** having to **download** the **entire CRL**.  

** OCSP ** \（RFC 2560 \）是由** OCSP客户端和OCSP响应者**组成的标准协议。 该协议**确定给定数字公开键证书的撤销状态** **无需**下载** **整个CRL **。
**CRL** is the **traditional method** of checking certificate validity. A **CRL provides a list of certificate serial numbers** that have been revoked or are no longer valid. CRLs let the verifier check the revocation status of the presented certificate while verifying it. CRLs are limited to 512 entries.  

** crl **是检查证书有效性的**传统方法**。 A ** CRL提供了已被撤销或不再有效的证书序列号**列表。 CRL让验证者在验证其验证时检查吊销证书的撤销状态。 CRL限制为512个条目。
From [here](https://www.arubanetworks.com/techdocs/ArubaOS%206_3_1_Web_Help/Content/ArubaFrameStyles/CertRevocation/About_OCSP_and_CRL.htm#:~:text=OCSP%20%28RFC%202560%29%20is%20a,to%20download%20the%20entire%20CRL.&text=A%20CRL%20provides%20a%20list,or%20are%20no%20longer%20valid.).

来自[此处]（https://www.arubanetworks.com/techdocs/arubaos%206_3_1_web_help/content/content/arubaframesty/certrevocation/certrevocation/certrevocation/about_ocsp_and_ocsp_and_and_and_htm.htm.htm.htm.htm.htm.htm＃ 到％20下载％20％20 entire％20crl。



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


