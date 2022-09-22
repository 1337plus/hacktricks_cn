# Pcap Inspection

＃PCAP检查

## Pcap Inspection

## PCAP检查

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

{% hint style="info" %}

{％提示样式=“ info”％}
A note about **PCAP** vs **PCAPNG**: there are two versions of the PCAP file format; **PCAPNG is newer and not supported by all tools**. You may need to convert a file from PCAPNG to PCAP using Wireshark or another compatible tool, in order to work with it in some other tools.

关于** PCAP ** vs ** PCAPNG **的注释：PCAP文件格式有两个版本； ** PCAPNG是新的，并且不受所有工具的支持**。 您可能需要使用Wireshark或其他兼容工具将文件从PCAPNG转换为PCAP，以便在其他一些工具中使用它。
{% endhint %}

## Online tools for pcaps

## PCAPS的在线工具

* If the header of your pcap is **broken** you should try to **fix** it using: [http://f00l.de/hacking/**pcapfix.php**](http://f00l.de/hacking/pcapfix.php)

*如果您的PCAP的标题为** ** **您应该尝试**修复**它使用：[http：//f00l.de/hacking/hacking/xplpcapfix.phpdy] .de/hacking/pcapfix.php）
* Extract **information** and search for **malware** inside a pcap in [**PacketTotal**](https://packettotal.com)

*提取**信息**并搜索**恶意软件**在[** packettotal **]（https://packettotal.com）中的PCAP中
* Search for **malicious activity** using [**www.virustotal.com**](https://www.virustotal.com) and [**www.hybrid-analysis.com**](https://www.hybrid-analysis.com)

*搜索**恶意活动**使用[** www.virustotal.com **]（https://www.virustotal.com）和[** www.hybrid-analisy.com **]（https：/https：/ /www.hybrid-analysis）

## Extract Information

##提取信息

The following tools are useful to extract statistics, files, etc.

以下工具可用于提取统计信息，文件等。

### Wireshark

### Wireshark

{% hint style="info" %}

{％提示样式=“ info”％}
**If you are going to analyze a PCAP you basically must to know how to use Wireshark**

**如果您要分析基本上必须知道如何使用Wireshark的PCAP ** **
{% endhint %}

You can find some Wireshark tricks in:

您可以在：

{% content-ref url="wireshark-tricks.md" %}

{％content-ref url =“ wireshark-tricks.md”％}
[wireshark-tricks.md](wireshark-tricks.md)

[WireShark-Tricks.md]（Wireshark-Tricks.md）
{% endcontent-ref %}

### Xplico Framework

### Xplico框架

[**Xplico** ](https://github.com/xplico/xplico)_(only linux)_ can **analyze** a **pcap** and extract information from it. For example, from a pcap file Xplico, extracts each email (POP, IMAP, and SMTP protocols), all HTTP contents, each VoIP call (SIP), FTP, TFTP, and so on.

[** xplico **]（https://github.com/xplico/xplico）_（只有linux）_可以**分析** a ** a ** pcap **并从中提取信息。 例如，从PCAP文件XPLICO中提取每个电子邮件（POP，IMAP和SMTP协议），所有HTTP内容，每个VoIP调用（SIP），FTP，TFTP等。

**Install**

```bash
sudo bash -c 'echo "deb http://repo.xplico.org/ $(lsb_release -s -c) main" /etc/apt/sources.list'
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 791C25CE
sudo apt-get update
sudo apt-get install xplico
```

**Run**

```
/etc/init.d/apache2 restart
/etc/init.d/xplico start
```

Access to _**127.0.0.1:9876**_ with credentials _**xplico:xplico**_

访问_ ** 127.0.0.1：9876DENDEND with凭据_ ** xplico：xplico ** _ _

Then create a **new case**, create a **new session** inside the case and **upload the pcap** file.

然后创建一个**新案例**，在案例中创建一个新的会话**，然后**上传PCAP **文件。

### NetworkMiner

Like Xplico it is a tool to **analyze and extract objects from pcaps**. It has a free edition that you can **download** [**here**](https://www.netresec.com/?page=NetworkMiner). It works with **Windows**.\

像Xplico一样，它是**从PCAPS **分析和提取对象的工具。 它有一个免费的版本，您可以**下载** [**在这里**]（https://www.netresec.com/?page=networkminer）。 它可以与** Windows **。
This tool is also useful to get **other information analysed** from the packets in order to be able to know what was happening in a **quicker** way.

该工具也可用于从数据包中获取其他信息** **，以便能够以更快的方式知道发生了什么。

### NetWitness Investigator

You can download [**NetWitness Investigator from here**](https://www.rsa.com/en-us/contact-us/netwitness-investigator-freeware) **(It works in Windows)**.\

您可以从这里**下载[** NetWitness调查员]（https://www.rsa.com/en-us/contact-us/netwitness-investigator-freeware）**（它在Windows中起作用）**。
This is another useful tool that **analyses the packets** and sorts the information in a useful way to **know what is happening inside**.

这是另一个有用的工具，可以**分析数据包**并以有用的方式对信息进行分类，以**知道**内部发生了什么。

![](<../../../.gitbook/assets/image (567) (1) (1).png>)

### [BruteShark](https://github.com/odedshimon/BruteShark)

* Extracting and encoding usernames and passwords (HTTP, FTP, Telnet, IMAP, SMTP...)

*提取和编码用户名和密码（http，ftp，telnet，imap，smtp ...）
* Extract authentication hashes and crack them using Hashcat (Kerberos, NTLM, CRAM-MD5, HTTP-Digest...)

*提取身份验证哈希并使用哈希猫（Kerberos，ntlm，cram-md5，http-digest ...）破解它们。
* Build a visual network diagram (Network nodes & users)

*构建视觉网络图（网络节点和用户）
* Extract DNS queries
* Reconstruct all TCP & UDP Sessions

*重建所有TCP和UDP会话
* File Carving

*文件雕刻

### Capinfos

```
capinfos capture.pcap
```

### Ngrep

If you are **looking** for **something** inside the pcap you can use **ngrep**. Here is an example using the main filters:

如果您**寻找** ** PCAP内部**，则可以使用** ngrep **。 这是使用主要过滤器的示例：

```bash
ngrep -I packets.pcap "^GET" "port 80 and tcp and host 192.168 and dst host 192.168 and src host 192.168"
```

### Carving

###雕刻

Using common carving techniques can be useful to extract files and information from the pcap:

使用常见的雕刻技术对于从PCAP提取文件和信息很有用：

{% content-ref url="../partitions-file-systems-carving/file-data-carving-recovery-tools.md" %}

{％content-ref url =“ ../ partitions-file-systems-carving/file-data-carving-recovery-tools.md”％}
[file-data-carving-recovery-tools.md](../partitions-file-systems-carving/file-data-carving-recovery-tools.md)

[file-data carving-recovery-tools.md]（../ partitions-file-systems-carving/file-data-carving-carving-recovery-tools.md）
{% endcontent-ref %}

### Capturing credentials

###捕获凭据

You can use tools like [https://github.com/lgandx/PCredz](https://github.com/lgandx/PCredz) to parse credentials from a pcap or a live interface.

您可以使用[https://github.com/lgandx/pcredz]（

## Check Exploits/Malware

##检查exploits/恶意软件

### Suricata

**Install and setup**

**安装和设置**

```
apt-get install suricata
apt-get install oinkmaster
echo "url = http://rules.emergingthreats.net/open/suricata/emerging.rules.tar.gz" >> /etc/oinkmaster.conf
oinkmaster -C /etc/oinkmaster.conf -o /etc/suricata/rules
```

**Check pcap**

**检查PCAP **

```
suricata -r packets.pcap -c /etc/suricata/suricata.yaml -k none -v -l log
```

### YaraPcap

[**YaraPCAP**](https://github.com/kevthehermit/YaraPcap) is a tool that

[** yarapcap **]（https://github.com/kevthehermit/yarapcap）是一种工具

* Reads a PCAP File and Extracts Http Streams.

*读取PCAP文件并提取HTTP流。
* gzip deflates any compressed streams

* gzip放气任何压缩流
* Scans every file with yara

*用yara扫描每个文件
* Writes a report.txt

*写一个report.txt
* Optionally saves matching files to a Dir

*可选将匹配的文件保存到DIR

### Malware Analysis

###恶意软件分析

Check if you can find any fingerprint of a known malware:

检查是否可以找到已知恶意软件的任何指纹：

{% content-ref url="../malware-analysis.md" %}

{％content-ref url =“ ../ malware-analysis.md”％}
[malware-analysis.md](../malware-analysis.md)

[MALWARE-ALASIS.MD]（../ malware-analysis.md）
{% endcontent-ref %}

## Zeek

> Zeek is a passive, open-source network traffic analyzer. Many operators use Zeek as a Network Security Monitor (NSM) to support investigations of suspicious or malicious activity. Zeek also supports a wide range of traffic analysis tasks beyond the security domain, including performance measurement and troubleshooting.

> Zeek是一种被动的开源网络流量分析仪。 许多操作员使用Zeek作为网络安全监视器（NSM）来支持对可疑或恶意活动的调查。 Zeek还支持超出安全域之外的广泛的流量分析任务，包括性能测量和故障排除。

Basically, logs created by `zeek` aren't **pcaps**. Therefore you will need to use **other tools** to analyse the logs where the **information** about the pcaps are.

基本上，`Zeek'创建的日志不是** PCAPS **。 因此，您需要使用**其他工具**来分析有关PCAPS的**信息**的日志。

### Connections Info

###连接信息

```bash
#Get info about longest connections (add "grep udp" to see only udp traffic)
#The longest connection might be of malware (constant reverse shell?)
cat conn.log | zeek-cut id.orig_h id.orig_p id.resp_h id.resp_p proto service duration | sort -nrk 7 | head -n 10

10.55.100.100   49778   65.52.108.225   443     tcp     -       86222.365445
10.55.100.107   56099   111.221.29.113  443     tcp     -       86220.126151
10.55.100.110   60168   40.77.229.82    443     tcp     -       86160.119664


#Improve the metrics by summing up the total duration time for connections that have the same destination IP and Port.
cat conn.log | zeek-cut id.orig_h id.resp_h id.resp_p proto duration | awk 'BEGIN{ FS="\t" } { arr[$1 FS $2 FS $3 FS $4] += $5 } END{ for (key in arr) printf "%s%s%s\n", key, FS, arr[key] }' | sort -nrk 5 | head -n 10

10.55.100.100   65.52.108.225   443     tcp     86222.4
10.55.100.107   111.221.29.113  443     tcp     86220.1
10.55.100.110   40.77.229.82    443     tcp     86160.1

#Get the number of connections summed up per each line
cat conn.log | zeek-cut id.orig_h id.resp_h duration | awk 'BEGIN{ FS="\t" } { arr[$1 FS $2] += $3; count[$1 FS $2] += 1 } END{ for (key in arr) printf "%s%s%s%s%s\n", key, FS, count[key], FS, arr[key] }' | sort -nrk 4 | head -n 10

10.55.100.100   65.52.108.225   1       86222.4
10.55.100.107   111.221.29.113  1       86220.1
10.55.100.110   40.77.229.82    134       86160.1

#Check if any IP is connecting to 1.1.1.1
cat conn.log | zeek-cut id.orig_h id.resp_h id.resp_p proto service | grep '1.1.1.1' | sort | uniq -c

#Get number of connections per source IP, dest IP and dest Port
cat conn.log | zeek-cut id.orig_h id.resp_h id.resp_p proto | awk 'BEGIN{ FS="\t" } { arr[$1 FS $2 FS $3 FS $4] += 1 } END{ for (key in arr) printf "%s%s%s\n", key, FS, arr[key] }' | sort -nrk 5 | head -n 10


# RITA
#Something similar can be done with the tool rita
rita show-long-connections -H --limit 10 zeek_logs

+---------------+----------------+--------------------------+----------------+
|   SOURCE IP   | DESTINATION IP | DSTPORT:PROTOCOL:SERVICE |    DURATION    |
+---------------+----------------+--------------------------+----------------+
| 10.55.100.100 | 65.52.108.225  | 443:tcp:-                | 23h57m2.3655s  |
| 10.55.100.107 | 111.221.29.113 | 443:tcp:-                | 23h57m0.1262s  |
| 10.55.100.110 | 40.77.229.82   | 443:tcp:-                | 23h56m0.1197s  |

#Get connections info from rita
rita show-beacons zeek_logs | head -n 10
Score,Source IP,Destination IP,Connections,Avg Bytes,Intvl Range,Size Range,Top Intvl,Top Size,Top Intvl Count,Top Size Count,Intvl Skew,Size Skew,Intvl Dispersion,Size Dispersion
1,192.168.88.2,165.227.88.15,108858,197,860,182,1,89,53341,108319,0,0,0,0
1,10.55.100.111,165.227.216.194,20054,92,29,52,1,52,7774,20053,0,0,0,0
0.838,10.55.200.10,205.251.194.64,210,69,29398,4,300,70,109,205,0,0,0,0
```

### DNS info

### DNS信息

```bash
#Get info about each DNS request performed
cat dns.log | zeek-cut -c id.orig_h query qtype_name answers

#Get the number of times each domain was requested and get the top 10
cat dns.log | zeek-cut query | sort | uniq | rev | cut -d '.' -f 1-2 | rev | sort | uniq -c | sort -nr | head -n 10

#Get all the IPs
cat dns.log | zeek-cut id.orig_h query | grep 'example\.com' | cut -f 1 | sort | uniq -c

#Sort the most common DNS record request (should be A)
cat dns.log | zeek-cut qtype_name | sort | uniq -c | sort -nr

#See top DNS domain requested with rita
rita show-exploded-dns -H --limit 10 zeek_logs
```

## Other pcap analysis tricks

##其他PCAP分析技巧

{% content-ref url="dnscat-exfiltration.md" %}
[dnscat-exfiltration.md](dnscat-exfiltration.md)
{% endcontent-ref %}

{% content-ref url="wifi-pcap-analysis.md" %}

{％content-ref url =“ wifi-pcap-analysis.md”％}
[wifi-pcap-analysis.md](wifi-pcap-analysis.md)

[WiFi-PCAP-ALASIS.MD]（WiFi-PCAP-分析.md）
{% endcontent-ref %}

{% content-ref url="usb-keystrokes.md" %}
[usb-keystrokes.md](usb-keystrokes.md)
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
