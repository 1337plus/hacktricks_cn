# Local Cloud Storage

＃本地云存储

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
<img src="../../../.gitbook/assets/image (307).png" alt="" data-size="original">

<img src =“../../../。gitbook/assets/image（307）.png“ alt =”“ data-size =” ointers =“ ointers”>
Through Security Skills as a Service, we help organizations to **defend against the Dark Hacking Arts**. Security Skills as a Service is an offensive cybersecurity consultancy model that combines an Intelligent Platform with the top-class, globally distributed, offensive security engineers, delivering **high-quality penetration testing results. Security Hubs** bring together offensive penetration testing tactics with human behavioral science, providing real-time insights into threat actors' tradecraft and a **complete assessment of any risks**.

通过安全技能作为服务，我们帮助组织**防御黑暗黑客艺术**。 安全技能作为服务是一种进攻性网络安全咨询模型，将智能平台与顶级，全球分布式，进攻性安全工程师结合在一起，提供**高质量的渗透测试结果。 安全枢纽**将进攻性渗透测试策略与人类行为科学结合在一起，提供对威胁参与者贸易克罗夫特（Tradecraft）的实时见解，并对任何风险**进行完整评估。

{% embed url="https://securityhubs.io/" %}
{% endhint %}

## OneDrive

＃＃ 一个驱动器

In Windows, you can find the OneDrive folder in `\Users\<username>\AppData\Local\Microsoft\OneDrive`. And inside `logs\Personal` it's possible to find the file `SyncDiagnostics.log` which contains some interesting data regarding the synchronized files:

在Windows中，您可以在`\ users \ <username> \ appdata \ local \ Microsoft \ oneDrive`中找到OneDrive文件夹。 内部`logs \ personal``可以找到文件`syncdiagnostics.log'，其中包含有关同步文件的一些有趣数据：

* Size in bytes

*大小在字节中
* Creation date

* 创建日期* Modification date
* Number of files in the cloud

*云中的文件数
* Number of files in the folder

*文件夹中的文件数
* **CID**: Unique ID of the OneDrive user

*** CID **：OneDrive用户的唯一ID
* Report generation time

*报告生成时间
* Size of the HD of the OS

*操作系统的高清大小

Once you have found the CID it's recommended to **search files containing this ID**. You may be able to find files with the name: _**\<CID>.ini**_ and _**\<CID>.dat**_ that may contain interesting information like the names of files synchronized with OneDrive.

找到CID后，建议**包含此ID **的搜索文件。 您可能可以找到名称：_ ** \ <cid> .ini ** _ and _ ** \ <cid> .dat ** _可能包含有趣的信息，例如与OneDrive同步的文件名称。

## Google Drive

## Google Drive
In Windows, you can find the main Google Drive folder in `\Users\<username>\AppData\Local\Google\Drive\user_default`\

在Windows中，您可以在`\ users \ <username> \ appdata \ local \ google \ google \ drive \ user_default` \ usename> \ username> \ username> \ username>中找到主要的Google驱动器文件夹。
This folder contains a file called Sync\_log.log with information like the email address of the account, filenames, timestamps, MD5 hashes of the files, etc. Even deleted files appear in that log file with its corresponding MD5.

该文件夹包含一个名为sync \ _log.log的文件，其中包含诸如帐户的电子邮件地址，文件名，时间戳，文件的MD5哈希等信息。

The file **`Cloud_graph\Cloud_graph.db`** is a sqlite database which contains the table **`cloud_graph_entry`**. In this table you can find the **name** of the **synchronized** **files**, modified time, size, and the MD5 checksum of the files.

文件**`cloud_graph \ cloud_graph.db` **是一个包含表** cloud_graph_entry` **的sqlite数据库。 在此表中，您可以找到**同步** **文件**的**名称**，修改时间，大小和文件的MD5校验和文件。

The table data of the database **`Sync_config.db`** contains the email address of the account, the path of the shared folders and the Google Drive version.

数据库的表数据**`sync_config.db` **包含帐户的电子邮件地址，共享文件夹的路径和Google驱动器版本。

## Dropbox

## Dropbox

Dropbox uses **SQLite databases** to manage the files. In this\

Dropbox使用** sqlite数据库**来管理文件。 在这个
You can find the databases in the folders:

您可以在文件夹中找到数据库：

* `\Users\<username>\AppData\Local\Dropbox`

*`\ users \ <用户名> \ appdata \ local \ dropbox`
* `\Users\<username>\AppData\Local\Dropbox\Instance1`

*`\ users \ <用户名> \ appdata \ local \ dropbox \ instance1`
* `\Users\<username>\AppData\Roaming\Dropbox`

*`\ users \ <用户名> \ appdata \ roaming \ dropbox`

And the main databases are:

主要数据库是：

* Sigstore.dbx
* Filecache.dbx

* Filecache.dbx
* Deleted.dbx
* Config.dbx

The ".dbx" extension means that the **databases** are **encrypted**. Dropbox uses **DPAPI** ([https://docs.microsoft.com/en-us/previous-versions/ms995355(v=msdn.10)?redirectedfrom=MSDN](https://docs.microsoft.com/en-us/previous-versions/ms995355\(v=msdn.10\)?redirectedfrom=MSDN))

“ .dbx”扩展名是指**数据库**已加密**。 dropbox使用** dpapi **（[https://docs.microsoft.com/en-us/previous-versions/ms995355(V=MMSDN.10)?rediredectectedfrom = msdn]（ /en-us/previous-versions/ms995355 \（v = mmsdn.10 \)？

To understand better the encryption that Dropbox uses you can read [https://blog.digital-forensics.it/2017/04/brush-up-on-dropbox-dbx-decryption.html](https://blog.digital-forensics.it/2017/04/brush-up-on-dropbox-dbx-decryption.html).

为了更好地了解Dropbox使用的加密，您可以读取[https://blog.digital-forensics.it/2017/04/brush-up-on-dropbox-dbx-decryption.html] -forensics.it/2017/04/brush-up-on-dropbox-dbx-decryption.html）。

However, the main information is:

但是，主要信息是：

* **Entropy**: d114a55212655f74bd772e37e64aee9b
* **Salt**: 0D638C092E8B82FC452883F95F355B8E
* **Algorithm**: PBKDF2
* **Iterations**: 1066

***迭代**：1066

Apart from that information, to decrypt the databases you still need:

除了这些信息外，要解密您仍然需要的数据库：

* The **encrypted DPAPI key**: You can find it in the registry inside `NTUSER.DAT\Software\Dropbox\ks\client` (export this data as binary)

***加密dpapi键**：您可以在`ntuser.dat \ software \ dropbox \ ks \ client`（将此数据导出为二进制）中的注册表中找到它。
* The **`SYSTEM`** and **`SECURITY`** hives

***``系统`**和**安全`** hives
* The **DPAPI master keys**: Which can be found in `\Users\<username>\AppData\Roaming\Microsoft\Protect`

*** dpapi master键**：可以在`\ users \ <username> \ appdata \ roaming \ microsoft \ microsoft \ procept`
* The **username** and **password** of the Windows user

***用户名**和**密码** Windows用户的密码

Then you can use the tool [**DataProtectionDecryptor**](https://nirsoft.net/utils/dpapi\_data\_decryptor.html)**:**

然后，您可以使用工具[** dataprotectiondecryptor **]（https://nirsoft.net/utils/dpapi \ _data \ _decryptor.html）**：**

![](<../../../.gitbook/assets/image (448).png>)

If everything goes as expected, the tool will indicate the **primary key** that you need to **use to recover the original one**. To recover the original one, just use this [cyber\_chef receipt](https://gchq.github.io/CyberChef/#recipe=Derive\_PBKDF2\_key\(%7B'option':'Hex','string':'98FD6A76ECB87DE8DAB4623123402167'%7D,128,1066,'SHA1',%7B'option':'Hex','string':'0D638C092E8B82FC452883F95F355B8E'%7D\)) putting the primary key as the "passphrase" inside the receipt.

如果一切都按预期进行，则该工具将指示**主键**您需要**恢复原始的**。 要恢复原始的，只需使用此[Cyber \ _CHEF收据]（https：//gchq.github.io/cyberchef/cyberchef/#recipe=derive \ _pbkdf2 \ _key \（％7B'option'： '：'98FD6A76ECB87DE8DAB4623123402167'％7D，128,1066，'SHA1'，％7b'option'：'hex'，'string'，'string'：'0d638c092e8b8b8b8b8b82fc45228888888888888883f955b355b8emane nestry nistery nistery nistery nyder'' 。

The resulting hex is the final key used to encrypt the databases which can be decrypted with:

最终的六角形是用于加密数据库的最终键，该数据库可以解密：

```bash
sqlite -k <Obtained Key> config.dbx ".backup config.db" #This decompress the config.dbx and creates a clear text backup in config.db
```

The **`config.dbx`** database contains:

**``config.dbx` **数据库包含：

* **Email**: The email of the user

***电子邮件**：用户的电子邮件
* **usernamedisplayname**: The name of the user

*** usernamedisplayname **：用户名称
* **dropbox\_path**: Path where the dropbox folder is located

*** dropbox \ _ path **：Dropbox文件夹的位置
* **Host\_id: Hash** used to authenticate to the cloud. This can only be revoked from the web.

***主机\ _id：哈希**用于对云进行身份验证。 这只能从网络上撤销。
* **Root\_ns**: User identifier

The **`filecache.db`** database contains information about all the files and folders synchronized with Dropbox. The table `File_journal` is the one with more useful information:

**``feecache.db` **数据库包含有关与Dropbox同步的所有文件和文件夹的信息。 表`file_journal`是一个有更多有用信息的信息：

* **Server\_path**: Path where the file is located inside the server (this path is preceded by the `host_id` of the client).

***服务器\ _ path **：文件位于服务器内部的路径（此路径在客户端的`host_id'之前）。
* **local\_sjid**: Version of the file

*** local \ _sjid **：文件的版本
* **local\_mtime**: Modification date
* **local\_ctime**: Creation date

* **local\_ctime**: Creation date

Other tables inside this database contain more interesting information:

该数据库中的其他表包含更多有趣的信息：

* **block\_cache**: hash of all the files and folders of Dropbox

*** block \ _cache **：dropbox的所有文件和文件夹的哈希
* **block\_ref**: Related the hash ID of the table `block_cache` with the file ID in the table `file_journal`

*** block \ _ref **：与表`file_journal“ file_journal”中的文件ID相关联的hash ID
* **mount\_table**: Share folders of dropbox

***安装\ _table **：共享Dropbox的文件夹
* **deleted\_fields**: Dropbox deleted files
* **date\_added**

{% hint style="danger" %}
<img src="../../../.gitbook/assets/image (307).png" alt="" data-size="original">

<img src =“../../../。gitbook/assets/image（307）.png“ alt =”“ data-size =” ointers =“ ointers”>

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
