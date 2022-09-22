

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


# Carving tools

＃雕刻工具

## Autopsy

The most common tool used in forensics to extract files from images is [**Autopsy**](https://www.autopsy.com/download/). Download it, install it and make it ingest the file to find "hidden" files. Note that Autopsy is built to support disk images and other kind of images, but not simple files.

取证中用于从图像中提取文件的最常见工具是[** opopsy **]（https://www.autopsy.com/download/）。 下载它，安装它并使其摄入文件以查找“隐藏”文件。 请注意，尸检旨在支持磁盘图像和其他类型的图像，而不是简单的文件。

## Binwalk <a id="binwalk"></a>

**Binwalk** is a tool for searching binary files like images and audio files for embedded files and data.  

** Binwalk **是用于搜索嵌入式文件和数据（例如图像和音频文件）等二进制文件的工具。
It can be installed with `apt` however the [source](https://github.com/ReFirmLabs/binwalk) can be found on github.  

它可以使用“ APT”安装，但是[源]（https://github.com/refirmlabs/binwalk）可以在GitHub上找到。
**Useful commands**:

**有用的命令**：

```bash
sudo apt install binwalk #Insllation
binwalk file #Displays the embedded data in the given file
binwalk -e file #Displays and extracts some files from the given file
binwalk --dd ".*" file #Displays and extracts all files from the given file
```

## Foremost

##首先

Another common tool to find hidden files is **foremost**. You can find the configuration file of foremost in `/etc/foremost.conf`. If you just want to search for some specific files uncomment them. If you don't uncomment anything foremost will search for it's default configured file types.

找到隐藏文件的另一个常见工具是**最前提**。 您可以在`/etc/foremost.conf`中找到最远的配置文件。 如果您只想搜索一些特定的文件，请访问它们。 如果您不输入，那么最重要的东西将搜索其默认配置的文件类型。

```bash
sudo apt-get install foremost
foremost -v -i file.img -o output
#Discovered files will appear inside the folder "output"
```

## **Scalpel**

**Scalpel** is another tool that can be use to find and extract **files embedded in a file**. In this case you will need to uncomment from the configuration file \(_/etc/scalpel/scalpel.conf_\) the file types you want it to extract.

**手术刀**是另一个可以用于查找和提取文件中的文件** **的工具。 在这种情况下，您将需要从配置文件\（_/etc/etc/caperpel/scappel.conf_ \）中取消点击您要提取的文件类型。

```bash
sudo apt-get install scalpel
scalpel file.img -o output
```

## Bulk Extractor

This tool comes inside kali but you can find it here: [https://github.com/simsong/bulk\_extractor](https://github.com/simsong/bulk_extractor)

该工具进入Kali内部，但您可以在这里找到它：[https://github.com/simsong/bulk \ _extractor]（

This tool can scan an image and will **extract pcaps** inside it, **network information\(URLs, domains, IPs, MACs, mails\)** and more **files**. You only have to do:

该工具可以扫描图像，并在其中提取pcaps **，**网络信息\（urls，域，IPS，Mac，Mails \）**和更多**文件**。 您只需要做：

```text
bulk_extractor memory.img -o out_folder
```

Navigate through **all the information** that the tool has gathered \(passwords?\), **analyse** the **packets** \(read[ **Pcaps analysis**](../pcap-inspection/)\), search for **weird domains** \(domains related to **malware** or **non-existent**\).

浏览**工具收集的所有信息**（密码？ /）\），搜索**怪异域** \（与**恶意软件**或**不存在** \）有关的域。

## PhotoRec

You can find it in [https://www.cgsecurity.org/wiki/TestDisk\_Download](https://www.cgsecurity.org/wiki/TestDisk_Download)

您可以在[https://www.cgsecurity.org/wiki/testdisk \_download]（

It comes with GUI and CLI version. You can select the **file-types** you want PhotoRec to search for.

它带有GUI和CLI版本。 您可以选择“文件类型” **您希望Photorec搜索。

![](../../../.gitbook/assets/image%20%28524%29.png)

# Specific Data Carving Tools

＃特定数据雕刻工具

## FindAES

Searches for AES keys by searching for their key schedules. Able to find 128. 192, and 256 bit keys, such as those used by TrueCrypt and BitLocker.

通过搜索其密钥时间表来搜索AES键。 能够找到128. 192和256个位键，例如TrueCrypt和Bitlocker使用的键。

Download [here](https://sourceforge.net/projects/findaes/).

下载[此处]（https://sourceforge.net/projects/findaes/）。

# Complementary tools 

＃互补工具

You can use [**viu** ](https://github.com/atanunq/viu)to see images form the terminal.  

您可以使用[** viu **]（https://github.com/atanunq/viu）查看图像形成终端。
You can use the linux command line tool **pdftotext** to transform a pdf into text and read it.

您可以使用Linux命令行工具** pdftotext **将PDF转换为文本并阅读。



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


