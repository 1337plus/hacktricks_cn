

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


# Check BSSIDs

＃检查BSSID

When you receive a capture whose principal traffic is Wifi using WireShark you can start investigating all the SSIDs of the capture with _Wireless --> WLAN Traffic_:

当您收到使用Wireshark的主要流量为WiFi的捕获时，您可以开始使用_wireless-> wlan traffic _：：

![](<../../../.gitbook/assets/image (424).png>)

![](<../../../.gitbook/assets/image (425).png>)

## Brute Force

One of the columns of that screen indicates if **any authentication was found inside the pcap**. If that is the case you can try to Brute force it using `aircrack-ng`:

该屏幕的一列之一指示是否在PCAP **内找到了任何身份验证。 如果是这种情况

```bash
aircrack-ng -w pwds-file.txt -b <BSSID> file.pcap
```

# Data in Beacons / Side Channel

If you suspect that **data is being leaked inside beacons of a Wifi network** you can check the beacons of the network using a filter like the following one: `wlan contains <NAMEofNETWORK>`, or `wlan.ssid == "NAMEofNETWORK"` search inside the filtered packets for suspicious strings.

如果您怀疑**数据已在WiFi网络的信标内泄漏** **您可以使用以下过滤器检查网络的信标：`wlan包含<nameofnetwork>`或`wlan.ssid ===“ nameofnetwork“```搜索过滤的数据包中的可疑字符串。

# Find Unknown MAC Addresses in A Wifi Network

＃在WiFi网络中找到未知的MAC地址

The following link will be useful to find the **machines sending data inside a Wifi Network**:

以下链接对于找到**机器在WiFi网络中发送数据**将很有用：

* `((wlan.ta == e8:de:27:16:70:c9) && !(wlan.fc == 0x8000)) && !(wlan.fc.type_subtype == 0x0005) && !(wlan.fc.type_subtype ==0x0004) && !(wlan.addr==ff:ff:ff:ff:ff:ff) && wlan.fc.type==2`

If you already know **MAC addresses you can remove them from the output** adding checks like this one: `&& !(wlan.addr==5c:51:88:31:a0:3b)`

如果您已经知道** MAC地址，则可以从输出中删除它们**添加这样的支票：`&&！（wlan.addr == 5c：51：88：31：a0：3b）

Once you have detected **unknown MAC** addresses communicating inside the network you can use **filters** like the following one: `wlan.addr==<MAC address> && (ftp || http || ssh || telnet)` to filter its traffic. Note that ftp/http/ssh/telnet filters are useful if you have decrypted the traffic.

一旦检测到**未知Mac **地址网络内部通信您可以使用**过滤器**如下：`wlan.addr == <mac地址> &&（ftp || http || http || ssh || ssh || telnet ）`要过滤其流量。 请注意，如果您解密了流量，FTP/HTTP/SSH/Telnet过滤器将很有用。

# Decrypt Traffic

＃解密流量

Edit --> Preferences --> Protocols --> IEEE 802.11--> Edit

编辑 - >首选项 - >协议 - > IEEE 802.11->编辑

![](<../../../.gitbook/assets/image (426).png>)





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


