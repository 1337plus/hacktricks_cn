

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


Start **searching** for **malware** inside the pcap. Use the **tools** mentioned in [**Malware Analysis**](../malware-analysis.md).

启动**搜索** **恶意软件** PCAP内部。 使用[**恶意软件分析**]中提到的**工具**（../ malware-analysis.md）。

# [Volatility](volatility-examples.md)

＃[波动率]（波动率 -  examples.md）

The premiere open-source framework for memory dump analysis is [Volatility](volatility-examples.md). Volatility is a Python script for parsing memory dumps that were gathered with an external tool (or a VMware memory image gathered by pausing the VM). So, given the memory dump file and the relevant "profile" (the OS from which the dump was gathered), Volatility can start identifying the structures in the data: running processes, passwords, etc. It is also extensible using plugins for extracting various types of artifacts.\

用于内存转储分析的首映开源框架是[波动率]（波动率-Examples.md）。 波动率是用于解析内存转储的Python脚本，该脚本是使用外部工具（或通过暂停VM收集的VMware内存图像）收集的。 因此，给定内存转储文件和相关的“配置文件”（收集转储的操作系统），波动率可以开始识别数据中的结构：运行过程，密码等。使用插件来提取各种插件，它也可扩展 工件类型。\
From: [https://trailofbits.github.io/ctf/forensics/](https://trailofbits.github.io/ctf/forensics/)

# Mini dump crash report

＃迷你转储崩溃报告
When the dump is small (just some KB, maybe a few MB) then it's probably a mini dump crash report and not a memory dump.

当转储很小（只有一些KB，也许是几个MB）时，这可能是一个迷你转储崩溃报告，而不是内存转储。

![](<../../../.gitbook/assets/image (216).png>)

If you have Visual Studio installed, you can open this file and bind some basic information like process name, architecture, exception info and modules being executed:

如果您安装了Visual Studio，则可以打开此文件并绑定一些基本信息，例如正在执行的过程名称，架构，异常信息和模块：

![](<../../../.gitbook/assets/image (217).png>)

You can also load the exception and see the decompiled instructions

您也可以加载异常并查看分解说明

![](<../../../.gitbook/assets/image (219).png>)

![](<../../../.gitbook/assets/image (218).png>)

Anyway, Visual Studio isn't the best tool to perform an analysis of the depth of the dump.

无论如何，Visual Studio并不是对转储深度进行分析的最佳工具。

You should **open** it using **IDA** or **Radare** to inspection it in **depth**.

您应该**打开**它使用** ida **或** radare **在** depth **中检查它。






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


