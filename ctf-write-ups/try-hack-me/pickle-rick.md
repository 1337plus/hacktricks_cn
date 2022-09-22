# Pickle Rick

## Pickle Rick

<details>

<summary><strong>Support HackTricks and get benefits!</strong></summary>

<summary> <strong>支持hacktricks并获得好处！</strong> </summary>

* Do you work in a **cybersecurity company**? Do you want to see your **company advertised in HackTricks**? or do you want to have access to the **latest version of the PEASS or download HackTricks in PDF**? Check the [**SUBSCRIPTION PLANS**](https://github.com/sponsors/carlospolop)!

*您在**网络安全公司**工作吗？ 您是否想看到您的**公司在hacktricks **中刊登广告？ 还是您想访问**最新版本的豌豆或在pdf **中下载hacktricks？ 检查[**订阅计划**]（https://github.com/sponsors/carlospolop）！
* Discover [**The PEASS Family**](https://opensea.io/collection/the-peass-family), our collection of exclusive [**NFTs**](https://opensea.io/collection/the-peass-family)

*发现[**豌豆家庭**]（https://opensea.io/collection/the-peass-family），我们的独家[** nfts **]（https://opensea.io/collection） /家庭家庭）
* Get the [**official PEASS & HackTricks swag**](https://peass.creator-spring.com)

*获取[**官方豌豆和hacktricks赃物**]（https://peass.creator-spring.com）
* **Join the** [**💬**](https://emojipedia.org/speech-balloon/) [**Discord group**](https://discord.gg/hRep4RUj7f) or the [**telegram group**](https://t.me/peass) or **follow** me on **Twitter** [**🐦**](https://github.com/carlospolop/hacktricks/tree/7af18b62b3bdc423e11444677a6a73d4043511e9/\[https:/emojipedia.org/bird/README.md)[**@carlospolopm**](https://twitter.com/carlospolopm)**.**

** **加入** [**💬**]（https://emojipedia.org/speech-balloon/）[** discord group **]（https://discord.gg/hrep4ruj7f）或[ **电报组**]（https://t.me/peass）或**在** Twitter ** [**🐦**]（https://github.com/carloppolop/hacktrickss on ** twitter **） /ree/7af18b62b3bdc423e114444444677a6a73d4043511e9/ \ [https:/emojipedia.org/bird/bird/readme.md）eardme.md）eghterme.md）eghterme.md）eghterme.md）eghtemplopmbyth
* **Share your hacking tricks by submitting PRs to the** [**hacktricks github repo**](https://github.com/carlospolop/hacktricks)**.**

***通过将PRS提交给** [** hacktricks github repo **]（https://github.com/carloppolop/hacktricks）**。

</details>

![](../../.gitbook/assets/picklerick.gif)

！

This machine was categorised as easy and it was pretty easy.

这台机器被归类为简单，非常简单。

## Enumeration

##枚举

I started **enumerating the machine using my tool** [**Legion**](https://github.com/carlospolop/legion):

我开始使用工具**枚举机器** [** legion **]（https://github.com/carloppolop/legion）：

![](<../../.gitbook/assets/image (79) (1).png>)

In as you can see 2 ports are open: 80 (**HTTP**) and 22 (**SSH**)

如您所见，两个端口是开放的：80（** http **）和22（** ssh **）

So, I launched legion to enumerate the HTTP service:

因此，我启动了军团以枚举HTTP服务：

![](<../../.gitbook/assets/image (234).png>)

Note that in the image you can see that `robots.txt` contains the string `Wubbalubbadubdub`

请注意，在图像中，您可以看到`robots.txt`包含字符串'wubbalubbadubdub`

After some seconds I reviewed what `disearch` has already discovered :

几秒钟后，我回顾了“ Disearch”已经发现的内容：

![](<../../.gitbook/assets/image (235).png>)

![](<../../.gitbook/assets/image (236).png>)

And as you may see in the last image a **login** page was discovered.

正如您在最后一个图像中看到的那样，发现了**登录**页面。

Checking the source code of the root page, a username is discovered: `R1ckRul3s`

检查根页的源代码，发现了一个用户名：`r1ckrul3s`

![](<../../.gitbook/assets/image (237).png>)

Therefore, you can login on the login page using the credentials `R1ckRul3s:Wubbalubbadubdub`

因此，您可以使用凭据`r1ckrul3s登录页面登录页面：wubbalubbadubdub`

## User

Using those credentials you will access a portal where you can execute commands:

使用这些凭据，您将访问可以执行命令的门户：

![](<../../.gitbook/assets/image (241).png>)

Some commands like cat aren't allowed but you can read the first ingredient (flag) using for example grep:

某些命令不允许使用，但是您可以使用例如GREP读取第一个成分（flag）：

![](<../../.gitbook/assets/image (242).png>)

Then I used:

然后我使用了：

![](<../../.gitbook/assets/image (243).png>)

To obtain a reverse shell:

获得反向外壳：

![](<../../.gitbook/assets/image (239).png>)

The **second ingredient** can be found in `/home/rick`

**第二个成分**可以在`/home/rick'中找到

![](<../../.gitbook/assets/image (240).png>)

## Root

The user **www-data can execute anything as sudo**:

用户** www-data可以以sudo **的身份执行任何操作：

![](<../../.gitbook/assets/image (238).png>)

<details>

<summary><strong>Support HackTricks and get benefits!</strong></summary>

<summary> <strong>支持hacktricks并获得好处！</strong> </summary>

* Do you work in a **cybersecurity company**? Do you want to see your **company advertised in HackTricks**? or do you want to have access to the **latest version of the PEASS or download HackTricks in PDF**? Check the [**SUBSCRIPTION PLANS**](https://github.com/sponsors/carlospolop)!

*您在**网络安全公司**工作吗？ 您是否想看到您的**公司在hacktricks **中刊登广告？ 还是您想访问**最新版本的豌豆或在pdf **中下载hacktricks？ 检查[**订阅计划**]（https://github.com/sponsors/carlospolop）！
* Discover [**The PEASS Family**](https://opensea.io/collection/the-peass-family), our collection of exclusive [**NFTs**](https://opensea.io/collection/the-peass-family)

*发现[**豌豆家庭**]（https://opensea.io/collection/the-peass-family），我们的独家[** nfts **]（https://opensea.io/collection） /家庭家庭）
* Get the [**official PEASS & HackTricks swag**](https://peass.creator-spring.com)

*获取[**官方豌豆和hacktricks赃物**]（https://peass.creator-spring.com）
* **Join the** [**💬**](https://emojipedia.org/speech-balloon/) [**Discord group**](https://discord.gg/hRep4RUj7f) or the [**telegram group**](https://t.me/peass) or **follow** me on **Twitter** [**🐦**](https://github.com/carlospolop/hacktricks/tree/7af18b62b3bdc423e11444677a6a73d4043511e9/\[https:/emojipedia.org/bird/README.md)[**@carlospolopm**](https://twitter.com/carlospolopm)**.**

** **加入** [**💬**]（https://emojipedia.org/speech-balloon/）[** discord group **]（https://discord.gg/hrep4ruj7f）或[ **电报组**]（https://t.me/peass）或**在** Twitter ** [**🐦**]（https://github.com/carloppolop/hacktrickss on ** twitter **） /ree/7af18b62b3bdc423e114444444677a6a73d4043511e9/ \ [https:/emojipedia.org/bird/bird/readme.md）eardme.md）eghterme.md）eghterme.md）eghterme.md）eghtemplopmbyth
* **Share your hacking tricks by submitting PRs to the** [**hacktricks github repo**](https://github.com/carlospolop/hacktricks)**.**

***通过将PRS提交给** [** hacktricks github repo **]（https://github.com/carloppolop/hacktricks）**。

</details>
