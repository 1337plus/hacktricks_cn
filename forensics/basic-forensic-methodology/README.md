# Basic Forensic Methodology

＃基本法医方法

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

## Creating and Mounting an Image

##创建和安装图像

{% content-ref url="../../generic-methodologies-and-resources/basic-forensic-methodology/image-acquisition-and-mount.md" %}

{％content-ref url =“ ../../ generic-methodologies-and-resources/basic-forensic-methodology/image-acquicition-and-mount.md”％}
[image-acquisition-and-mount.md](../../generic-methodologies-and-resources/basic-forensic-methodology/image-acquisition-and-mount.md)

[image-acocition-and-mount.md]（../../ generic-methodogogies-and-resources/basic-forensic-methodology/image-acquicition-and-mount.md）
{% endcontent-ref %}

## Malware Analysis

##恶意软件分析

This **isn't necessary the first step to perform once you have the image**. But you can use this malware analysis techniques independently if you have a file, a file-system image, memory image, pcap... so it's good to **keep these actions in mind**:

此**并不是必需的第一步，一旦您拥有图像**。 但是，如果您有文件，文件系统映像，内存图像，PCAP ...因此，**牢记这些操作是很好的，则可以独立使用此恶意软件分析技术。

{% content-ref url="malware-analysis.md" %}

{％content-ref url =“ malware-Analysis.md”％}
[malware-analysis.md](malware-analysis.md)

[MALWARE-ALASIS.MD]（恶意软件 - 分析）
{% endcontent-ref %}

## Inspecting an Image

##检查图像

if you are given a **forensic image** of a device you can start **analyzing the partitions, file-system** used and **recovering** potentially **interesting files** (even deleted ones). Learn how in:

如果给出了设备的**法医图像**，则可以启动**分析分区，文件系统**使用和**恢复**可能**有趣的文件**（甚至已删除）。 了解如何：

{% content-ref url="partitions-file-systems-carving/" %}
[partitions-file-systems-carving](partitions-file-systems-carving/)

[分区文件释放]（分区文件释放/）
{% endcontent-ref %}

Depending on the used OSs and even platform different interesting artifacts should be searched:

根据使用的OSS甚至平台，应搜索不同的有趣工件：

{% content-ref url="windows-forensics/" %}

{％content-ref url =“ Windows-Forensics/”％}
[windows-forensics](windows-forensics/)

[Windows-Forensics]（Windows-Forensics/）
{% endcontent-ref %}

{% content-ref url="linux-forensics.md" %}
[linux-forensics.md](linux-forensics.md)
{% endcontent-ref %}

{% content-ref url="docker-forensics.md" %}

{％content-ref url =“ docker-forensics.md”％}
[docker-forensics.md](docker-forensics.md)

[docker-forensics.md]（docker-forensics.md）
{% endcontent-ref %}

## Deep inspection of specific file-types and Software

##对特定文件类型和软件的深入检查

If you have very **suspicious** **file**, then **depending on the file-type and software** that created it several **tricks** may be useful.\

如果您非常**可疑** ** file **，则**根据文件类型和软件**，可以创建几个**技巧**可能很有用。\ \ \ \ \ \ \
Read the following page to learn some interesting tricks:

阅读以下页面以学习一些有趣的技巧：

{% content-ref url="specific-software-file-type-tricks/" %}

{％content-ref url =“特定软件型式式tricks/“％}
[specific-software-file-type-tricks](specific-software-file-type-tricks/)

[特定软件文件类型 - 特定软件型式式式式 - 
{% endcontent-ref %}

I want to do a special mention to the page:

我想特别提及该页面：

{% content-ref url="specific-software-file-type-tricks/browser-artifacts.md" %}

{％content-ref url =“特定软件型 - 型式tricks/browser-artifacts.md”％}
[browser-artifacts.md](specific-software-file-type-tricks/browser-artifacts.md)

[browser-artifacts.md]（特定软件文件型 -  tricks/browser-artifacts.md）
{% endcontent-ref %}

## Memory Dump Inspection

##内存转储检查

{% content-ref url="memory-dump-analysis/" %}

{％content-ref url =“内存降低 - 分析/”％}
[memory-dump-analysis](memory-dump-analysis/)

[记忆 - 降低分析]（内存降低 - 分析/）
{% endcontent-ref %}

## Pcap Inspection

## PCAP检查

{% content-ref url="pcap-inspection/" %}

{％content-ref url =“ pcap-inspection/”％}
[pcap-inspection](pcap-inspection/)

[PCAP-INSPECTION]（PCAP-inspection/）
{% endcontent-ref %}

## **Anti-Forensic Techniques**

Keep in mind the possible use of anti-forensic techniques:

请记住，可能使用抗飞敏技术：

{% content-ref url="anti-forensic-techniques.md" %}
[anti-forensic-techniques.md](anti-forensic-techniques.md)
{% endcontent-ref %}

## Threat Hunting

##威胁狩猎

{% content-ref url="file-integrity-monitoring.md" %}

{％content-ref url =“ file-integrity-monitoring.md”％}
[file-integrity-monitoring.md](file-integrity-monitoring.md)

[file-integrity-monitoring.md]（file-integrity-monitoring.md）
{% endcontent-ref %}

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
