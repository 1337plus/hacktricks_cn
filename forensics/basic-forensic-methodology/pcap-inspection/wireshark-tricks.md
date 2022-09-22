# Wireshark tricks

＃Wireshark技巧

## Wireshark tricks

## Wireshark技巧

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

## Improve your Wireshark skills

## Improve your Wireshark skills

### Tutorials

The following tutorials are amazing to learn some cool basic tricks:

以下教程很棒，可以学习一些很酷的基本技巧：

* [https://unit42.paloaltonetworks.com/unit42-customizing-wireshark-changing-column-display/](https://unit42.paloaltonetworks.com/unit42-customizing-wireshark-changing-column-display/)
* [https://unit42.paloaltonetworks.com/using-wireshark-display-filter-expressions/](https://unit42.paloaltonetworks.com/using-wireshark-display-filter-expressions/)
* [https://unit42.paloaltonetworks.com/using-wireshark-identifying-hosts-and-users/](https://unit42.paloaltonetworks.com/using-wireshark-identifying-hosts-and-users/)
* [https://unit42.paloaltonetworks.com/using-wireshark-exporting-objects-from-a-pcap/](https://unit42.paloaltonetworks.com/using-wireshark-exporting-objects-from-a-pcap/)

### Analysed Information

###分析信息

**Expert Information**

**专家信息**

Clicking on _**Analyze** --> **Expert Information**_ you will have an **overview** of what is happening in the packets **analyzed**:

单击_ **分析**  - > **专家信息** _您将有一个**概述**数据包中发生的事情**分析** **：

![](<../../../.gitbook/assets/image (570).png>)

**Resolved Addresses**

**解决地址**

Under _**Statistics --> Resolved Addresses**_ you can find several **information** that was "**resolved**" by wireshark like port/transport to protocol, MAC to the manufacturer, etc. It is interesting to know what is implicated in the communication.

根据_ **统计数据 - >解决地址** _您可以找到几个**信息**，这些信息**已通过Wireshark进行“ **已解决**”，例如港口/运输到协议，Mac到制造商等。这很有趣 知道与交流有关的内容。

![](<../../../.gitbook/assets/image (571).png>)

**Protocol Hierarchy**

**协议层次结构**

Under _**Statistics --> Protocol Hierarchy**_ you can find the **protocols** **involved** in the communication and data about them.

在_ **统计数据下 - >协议层次结构** _ _您可以在通信和有关它们的数据中找到**协议** ** **。

![](<../../../.gitbook/assets/image (572).png>)

**Conversations**

Under _**Statistics --> Conversations**_ you can find a **summary of the conversations** in the communication and data about them.

在_ **统计数据下 - >对话** _ _您可以在通信和有关它们的数据中找到对话的摘要**。

![](<../../../.gitbook/assets/image (573).png>)

**Endpoints**

Under _**Statistics --> Endpoints**_ you can find a **summary of the endpoints** in the communication and data about each of them.

在_ **统计数据下 - >端点** _ _您可以在通信中找到端点**的摘要以及每个端点的数据。

![](<../../../.gitbook/assets/image (575).png>)

**DNS info**

** DNS信息**

Under _**Statistics --> DNS**_ you can find statistics about the DNS request captured.

根据_ **统计信息 - > DNS ** _您可以找到有关捕获的DNS请求的统计信息。

![](<../../../.gitbook/assets/image (577).png>)

**I/O Graph**

** i/o图**

Under _**Statistics --> I/O Graph**_ you can find a **graph of the communication.**

在_ **统计数据下 - > i/o图** _您可以找到通信的**图。**

![](<../../../.gitbook/assets/image (574).png>)

### Filters

Here you can find wireshark filter depending on the protocol: [https://www.wireshark.org/docs/dfref/](https://www.wireshark.org/docs/dfref/)\

在这里，您可以根据协议找到Wireshark过滤器：[https://www.wireshark.org/docs/dfref/]（https://www.wireshark.org/docs/docs/dfref/）
Other interesting filters:

其他有趣的过滤器：

* `(http.request or ssl.handshake.type == 1) and !(udp.port eq 1900)`

*`（http.request或ssl.handshake.type == 1）和！（udp.port eq 1900）``
  * HTTP and initial HTTPS traffic

* HTTP和初始HTTPS流量
* `(http.request or ssl.handshake.type == 1 or tcp.flags eq 0x0002) and !(udp.port eq 1900)`

*`（http.request或ssl.handshake.type == 1或tcp.flags eq 0x0002）and！（udp.port eq 1900）
  * HTTP and initial HTTPS traffic + TCP SYN

* HTTP和初始HTTPS流量 + TCP SYN
* `(http.request or ssl.handshake.type == 1 or tcp.flags eq 0x0002 or dns) and !(udp.port eq 1900)`

*`（http.request或ssl.handshake.type == 1或tcp.flags eq 0x0002或dns）和！（udp.port eq 1900）``
  * HTTP and initial HTTPS traffic + TCP SYN + DNS requests

* HTTP和初始HTTPS流量 + TCP SYN + DNS请求

### Search

＃＃＃ 搜索

If you want to **search** for **content** inside the **packets** of the sessions press _CTRL+f_. You can add new layers to the main information bar (No., Time, Source, etc.) by pressing the right button and then the edit column.

如果您想**搜索** ** content **在**数据包中** sessions of pass _ctrl+f_。 您可以通过按下右键按钮，然后再添加编辑列，将新层添加到主信息栏（否。，时间，源等）。

Practice: [https://www.malware-traffic-analysis.net/](https://www.malware-traffic-analysis.net)

## Identifying Domains

##识别域

You can add a column that shows the Host HTTP header:

您可以添加一个显示主机HTTP标头的列：

![](<../../../.gitbook/assets/image (403).png>)

And a column that add the Server name from an initiating HTTPS connection (**ssl.handshake.type == 1**):

以及从启动HTTPS连接添加服务器名称的列（** ssl.handshake.type == 1 **）：

![](<../../../.gitbook/assets/image (408).png>)

## Identifying local hostnames

##标识本地主机名

### From DHCP

In current Wireshark instead of `bootp` you need to search for `DHCP`

在当前的Wireshark而不是“ bootp”中，您需要搜索`dhcp'

![](<../../../.gitbook/assets/image (404).png>)

### From NBNS

### From NBNS

![](<../../../.gitbook/assets/image (405).png>)

## Decrypting TLS

##解密TLS

### Decrypting https traffic with server private key

###用服务器私钥解密HTTPS流量

_edit>preference>protocol>ssl>_

![](<../../../.gitbook/assets/image (98).png>)

Press _Edit_ and add all the data of the server and the private key (_IP, Port, Protocol, Key file and password_)

按_edit_并添加服务器的所有数据和私钥（_IP，端口，协议，键文件和密码_）

### Decrypting https traffic with symmetric session keys

###用对称会话键解密HTTPS流量

It turns out that Firefox and Chrome both support logging the symmetric session key used to encrypt TLS traffic to a file. You can then point Wireshark at said file and presto! decrypted TLS traffic. More in: [https://redflagsecurity.net/2019/03/10/decrypting-tls-wireshark/](https://redflagsecurity.net/2019/03/10/decrypting-tls-wireshark/)\

事实证明，Firefox和Chrome都支持记录用于将TLS流量加密到文件的对称会话密钥。 然后，您可以将Wireshark指向上述文件和Presto！ 解密的TLS流量。 更多信息：[https://redflagsecurity.net/2019/03/10/decrypting-tls-wireshark/]
To detect this search inside the environment for to variable `SSLKEYLOGFILE`

在环境中检测到可变`sslkeylogfile`的搜索

A file of shared keys will look like this:

共享密钥的文件将看起来像这样：

![](<../../../.gitbook/assets/image (99).png>)

To import this in wireshark go to \_edit > preference > protocol > ssl > and import it in (Pre)-Master-Secret log filename:

要在Wireshark中导入此内容，请转到\ _edit> preferference>“协议”> ssl>并将其导入（PRE） -  Master-Secret log fileName：

![](<../../../.gitbook/assets/image (100).png>)

## ADB communication

Extract an APK from an ADB communication where the APK was sent:

从发送APK的ADB通信中提取APK：

```python
from scapy.all import *

pcap = rdpcap("final2.pcapng")

def rm_data(data):
    splitted = data.split(b"DATA")
    if len(splitted) == 1:
        return data
    else:
        return splitted[0]+splitted[1][4:]

all_bytes = b""
for pkt in pcap:
    if Raw in pkt:
        a = pkt[Raw]
        if b"WRTE" == bytes(a)[:4]:
            all_bytes += rm_data(bytes(a)[24:])
        else:
            all_bytes += rm_data(bytes(a))
print(all_bytes)

f = open('all_bytes.data', 'w+b')
f.write(all_bytes)
f.close()
```

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
