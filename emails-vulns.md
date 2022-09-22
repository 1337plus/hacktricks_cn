

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


# Payloads

＃有效载荷

## Ignored parts of an email

##忽略了电子邮件的部分

The symbols: **+, -** and **{}** in rare occasions can be used for tagging and ignored by most e-mail servers

符号：**+， -  **和** {} **在极少数情况下可用于标记和大多数电子邮件服务器忽略

* E.g. john.doe+intigriti@example.com → john.doe@example.com

**Comments between parentheses ()** at the beginning or the end will also be ignored

**括号之间的评论（）**在开始或结束也将被忽略

* E.g. john.doe(intigriti)@example.com → john.doe@example.com

## Whitelist bypass

##白名单旁路

* inti(;inti@inti.io;)@whitelisted.com

* inti(;inti@inti.io; ;)@whitelisted.com
* inti@inti.io(@whitelisted.com)

* inti@inti.io（@whitelisted.com）
* inti+(@whitelisted.com;)@inti.io

* inti+(@whitelisted.com; :)@inti.io

## IPs

## IP

You can also use IPs as domain named between square brackets:

您也可以将IPS用作平方括号之间命名的域：

* john.doe@\[127.0.0.1]
* john.doe@\[IPv6:2001:db8::1]

## Other vulns

##其他漏洞
![](<.gitbook/assets/image (296).png>)

# Third party SSO

＃第三方SSO

## XSS

Some services like **github** or **salesforce allows** you to create an **email address with XSS payloads on it**. If you can **use this providers to login on other services** and this services **aren't sanitising** correctly the email, you could cause **XSS**.

** github **或** salesforce之类的某些服务允许**您可以创建一个带有XSS有效载荷的电子邮件地址**。 如果您可以**使用此提供商登录其他服务**，并且此服务**无法正确消毒**电子邮件，则可能导致** XSS **。

## Account-Takeover

##帐户 - 访问

If a **SSO service** allows you to **create an account without verifying the given email address** (like **salesforce**) and then you can use that account to **login in a different service** that **trusts** salesforce, you could access any account.\

如果** SSO服务**允许您**创建一个帐户而无需验证给定的电子邮件地址**（例如** Salesforce **），然后您可以使用该帐户来**登录其他服务** ** **信任** Salesforce，您可以访问任何帐户。\ \
_Note that salesforce indicates if the given email was or not verified but so the application should take into account this info._

_ note Salesforce指示给定的电子邮件是否已验证，因此该应用程序应考虑此信息。

# Reply-To

＃ 回复

You can send an email using _**From: company.com**_** ** and _**Replay-To: attacker.com**_ and if any **automatic reply** is sent due to the email was sent **from** an **internal address** the **attacker** may be able to **receive** that **response**.

您可以使用_ **发送电子邮件：company.com ** _ ** **和_ ** replay-to：tainter.com ** _ _，如果有任何**自动回复**，则由于电子邮件发送了** 从**和内部地址**发送** **攻击者**可能可以**接收** **响应**。

# **References**

* [**https://drive.google.com/file/d/1iKL6wbp3yYwOmxEtAg1jEmuOf8RM8ty9/view**](https://drive.google.com/file/d/1iKL6wbp3yYwOmxEtAg1jEmuOf8RM8ty9/view)

# Hard Bounce Rate

＃硬跳率

Some applications like AWS have a **Hard Bounce Rate** (in AWS is 10%), that whenever is overloaded the email service is blocked.

某些应用程序（例如AWS）具有**硬跳率**（在AWS中为10％），每当超载的电子邮件服务都会被阻止。

A **hard bounce** is an **email** that couldn’t be delivered for some permanent reasons. Maybe the **email’s** a fake address, maybe the **email** domain isn’t a real domain, or maybe the **email** recipient’s server won’t accept **emails**) , that means from total of 1000 emails if 100 of them were fake or were invalid that caused all of them to bounce, **AWS SES** will block your service.

** hard Bounce **是一个**电子邮件**，由于某些永久原因无法交付。 也许**电子邮件的**一个假地址，也许**电子邮件**域不是真正的域，或者**电子邮件**收件人的服务器不接受**电子邮件**），这意味着从 如果其中100个是假的或导致所有人反弹的无效的电子邮件，则总共有1000封电子邮件，** aws ses **将阻止您的服务。

So, if you are able to **send mails (maybe invitations) from the web application to any email address, you could provoke this block by sending hundreds of invitations to nonexistent users and domains: Email service DoS.**

因此，如果您能够**从Web应用程序发送邮件（可能是邀请）到任何电子邮件地址，则可以通过向不存在的用户和域发送数百个邀请来引发此块：电子邮件服务DOS。


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


