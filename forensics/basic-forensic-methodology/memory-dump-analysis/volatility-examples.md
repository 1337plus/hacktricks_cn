# Volatility - CheatSheet

＃波动率 - 作弊表

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

If you want something **fast and crazy** that will launch several Volatility plugins on parallel you can use: [https://github.com/carlospolop/autoVolatility](https://github.com/carlospolop/autoVolatility)

如果您想要一些**快速而疯狂的**可以并行启动多个波动式插件，则可以使用：[https://github.com/carloppolop/autovolatility]（

```bash
python autoVolatility.py -f MEMFILE -d OUT_DIRECTORY -e /home/user/tools/volatility/vol.py # It will use the most important plugins (could use a lot of space depending on the size of the memory)
```

## Installation

## Installation

### volatility3

```bash
git clone https://github.com/volatilityfoundation/volatility3.git
cd volatility3
python3 setup.py install
python3 vol.py —h
```

### volatility2

{% tabs %}
{% tab title="Method1" %}

{％tab title =“ method1”％}
```
Download the executable from https://www.volatilityfoundation.org/26
```
{% endtab %}

{% tab title="Method 2" %}

{％tab title =“方法2”％}
```bash
git clone https://github.com/volatilityfoundation/volatility.git
cd volatility
python setup.py install
```
{% endtab %}
{% endtabs %}

## Volatility Commands

##波动命令

Access the official doc in [Volatility command reference](https://github.com/volatilityfoundation/volatility/wiki/Command-Reference#kdbgscan)

访问[波动命令参考]中的官方文档（https://github.com/volatilityfoundation/volatility/wiki/command-reference#kdbgscan）

### A note on “list” vs. “scan” plugins

Volatility has two main approaches to plugins, which are sometimes reflected in their names. “list” plugins will try to navigate through Windows Kernel structures to retrieve information like processes (locate and walk the linked list of `_EPROCESS` structures in memory), OS handles (locating and listing the handle table, dereferencing any pointers found, etc). They more or less behave like the Windows API would if requested to, for example, list processes.

波动率具有两种主要方法，有时会反映出其名称。 “列表”插件将尝试通过Windows内核结构导航，以检索信息等信息（在存储器中找到和行走'_eprocess'结构的链接列表），OS句柄（定位和列出句柄表，找到任何指针等）） 。 他们或多或少的行为像Windows API一样，如果需要，例如列表进程。

That makes “list” plugins pretty fast, but just as vulnerable as the Windows API to manipulation by malware. For instance, if malware uses DKOM to unlink a process from the `_EPROCESS` linked list, it won’t show up in the Task Manager and neither will it in the pslist.

这使得“列表”插件非常快，但与Windows API一样脆弱，可以通过恶意软件操纵。 例如，如果恶意软件使用DKOM从`_eprocess`链接列表中链接一个进程，则不会显示在任务管理器中，并且它也不会在PSLIST中显示。

“scan” plugins, on the other hand, will take an approach similar to carving the memory for things that might make sense when dereferenced as specific structures. `psscan` for instance will read the memory and try to make`_EPROCESS` objects out of it (it uses pool-tag scanning, which is searching for 4-byte strings that indicate the presence of a structure of interest). The advantage is that it can dig up processes that have exited, and even if malware tampers with the `_EPROCESS` linked list, the plugin will still find the structure lying around in memory (since it still needs to exist for the process to run). The downfall is that “scan” plugins are a bit slower than “list” plugins, and can sometimes yield false positives (a process that exited too long ago and had parts of its structure overwritten by other operations).

另一方面，“扫描”插件将采用类似的方法，类似于将记忆刻录到特定结构时可能有意义的事物。 例如，``psscan`将读取内存并尝试从中制作“ _eprocess”对象（它使用池标签扫描，该对象正在搜索指示存在感兴趣结构的4个字节字符串）。 优势在于它可以挖掘已退出的过程，即使使用“ _eprocess”链接列表的恶意软件设计机，该插件仍然会在存储器中找到位置的结构（因为要运行该过程仍需要存在） 。 失败的是“扫描”插件比“列表”插件慢一点，有时可以产生误报（该过程已在很久以前退出，并且其结构的一部分被其他操作覆盖）。

From: [http://tomchop.me/2016/11/21/tutorial-volatility-plugins-malware-analysis/](http://tomchop.me/2016/11/21/tutorial-volatility-plugins-malware-analysis/)

## OS Profiles

## OS配置文件

### Volatility3

As explained inside the readme you need to put the **symbol table of the OS** you want to support inside _volatility3/volatility/symbols_.\

如读书中所述，您需要在_ volatility 3/domatitions/符号_。_。
Symbol table packs for the various operating systems are available for **download** at:

可用于**下载**的各种操作系统的符号表包：

* [https://downloads.volatilityfoundation.org/volatility3/symbols/windows.zip](https://downloads.volatilityfoundation.org/volatility3/symbols/windows.zip)
* [https://downloads.volatilityfoundation.org/volatility3/symbols/mac.zip](https://downloads.volatilityfoundation.org/volatility3/symbols/mac.zip)
* [https://downloads.volatilityfoundation.org/volatility3/symbols/linux.zip](https://downloads.volatilityfoundation.org/volatility3/symbols/linux.zip)

### Volatility2

###波动2

#### External Profile

You can get the list of supported profiles doing:

您可以获取支持的个人资料列表：

```bash
./volatility_2.6_lin64_standalone --info | grep "Profile"
```

If you want to use a **new profile you have downloaded** (for example a linux one) you need to create somewhere the following folder structure: _plugins/overlays/linux_ and put inside this folder the zip file containing the profile. Then, get the number of the profiles using:

如果要使用**新的配置文件，则已下载**（例如Linux One），需要在以下文件夹结构的某个地方创建：_plugins/Overlays/linux_，然后将其放入此文件夹中包含配置文件的zip文件。 然后，使用以下方式获取配置文件的数量：

```bash
./vol --plugins=/home/kali/Desktop/ctfs/final/plugins --info
Volatility Foundation Volatility Framework 2.6


Profiles
--------
LinuxCentOS7_3_10_0-123_el7_x86_64_profilex64 - A Profile for Linux CentOS7_3.10.0-123.el7.x86_64_profile x64
VistaSP0x64                                   - A Profile for Windows Vista SP0 x64
VistaSP0x86                                   - A Profile for Windows Vista SP0 x86
```

You can **download Linux and Mac profiles** from [https://github.com/volatilityfoundation/profiles](https://github.com/volatilityfoundation/profiles)

您可以**从[https://github.com/volatilityfoundation/profiles下载Linux和Mac配置文件** **

In the previous chunk you can see that the profile is called `LinuxCentOS7_3_10_0-123_el7_x86_64_profilex64`, and you can use it to execute something like:

在上一个块中，您可以看到该配置文件称为`linuxcentos7_3_10_0_0-123_el7_x86_64_profilex64`，您可以使用它来执行类似的操作：

```bash
./vol -f file.dmp --plugins=. --profile=LinuxCentOS7_3_10_0-123_el7_x86_64_profilex64 linux_netscan
```

#### Discover Profile

####发现个人资料

```
volatility imageinfo -f file.dmp
volatility kdbgscan -f file.dmp
```

#### **Differences between imageinfo and kdbgscan**

As opposed to imageinfo which simply provides profile suggestions, **kdbgscan** is designed to positively identify the correct profile and the correct KDBG address (if there happen to be multiple). This plugin scans for the KDBGHeader signatures linked to Volatility profiles and applies sanity checks to reduce false positives. The verbosity of the output and the number of sanity checks that can be performed depends on whether Volatility can find a DTB, so if you already know the correct profile (or if you have a profile suggestion from imageinfo), then make sure you use it (from [here](https://www.andreafortuna.org/2017/06/25/volatility-my-own-cheatsheet-part-1-image-identification/)).

与仅提供配置文件建议的ImageInfo相反，** KDBGSCAN **旨在积极地识别正确的配置文件和正确的KDBG地址（如果碰巧有多个）。 该插件扫描针对与波动率配置文件相关的KDBGHEADER签名，并应用理智检查以减少误报。 输出的详细性和可以执行的理智检查数量取决于波动率是否可以找到DTB，因此，如果您已经知道正确的配置文件（或者是否有来自ImageInfo的配置文件建议），请确保使用它 （源自[此处]（https://www.andreafortuna.org/2017/06/25/volatility-my-own-cheatsheet-cheatsheet-part-part-part-1-image-isendification/））。

Always take a look at the **number of processes that kdbgscan has found**. Sometimes imageinfo and kdbgscan can find **more than one** suitable **profile** but only the **valid one will have some process related** (This is because to extract processes the correct KDBG address is needed)

始终查看KDBGSCAN发现的**数量**。 有时ImageInfo和KDBGSCAN可以找到**多个**合适的**配置文件**，但只有**有效的一个与过程相关的**（这是因为要提取过程需要正确的kdbg地址）

```bash
# GOOD
PsActiveProcessHead           : 0xfffff800011977f0 (37 processes)
PsLoadedModuleList            : 0xfffff8000119aae0 (116 modules)
```

```bash
# BAD
PsActiveProcessHead           : 0xfffff800011947f0 (0 processes)
PsLoadedModuleList            : 0xfffff80001197ac0 (0 modules)
```

#### KDBG

The **kernel debugger block** (named KdDebuggerDataBlock of the type \_KDDEBUGGER\_DATA64, or **KDBG** by volatility) is important for many things that Volatility and debuggers do. For example, it has a reference to the PsActiveProcessHead which is the list head of all processes required for process listing.

**内核调试器块**（命名为\ _kddebugger \ _data64的kddebuggerdatablock，或者是波动性的** kdbg **）对于许多波动性和调试者所做的事情都很重要。 例如，它具有对PsactiveProcesshead的引用，该列表是过程清单所需的所有过程的列表。

## OS Information

## OS信息

```bash
#vol3 has a plugin to give OS information (note that imageinfo from vol2 will give you OS info)
./vol.py -f file.dmp windows.info.Info
```

The plugin `banners.Banners` can be used in **vol3 to try to find linux banners** in the dump.

可以在** vol3中使用插件`banners.Banners“试图在转储中找到Linux标语**。

## Hashes/Passwords

##哈希/密码

Extract SAM hashes, [domain cached credentials](../../../windows-hardening/stealing-credentials/credentials-protections.md#cached-credentials) and [lsa secrets](../../../windows-hardening/authentication-credentials-uac-and-efs.md#lsa-secrets).

提取SAM哈希，[域缓存凭据]（../../../ Windows-hardening/stealing-credentials/recithentials-protections.md＃cached-credentials）和[lsa secrets]（../ ../../。 ./windows-hardening/authentication-credentials-uac-and-efs.md#lsa-secrets）。

{% tabs %}
{% tab title="vol3" %}
```bash
./vol.py -f file.dmp windows.hashdump.Hashdump #Grab common windows hashes (SAM+SYSTEM)
./vol.py -f file.dmp windows.cachedump.Cachedump #Grab domain cache hashes inside the registry
./vol.py -f file.dmp windows.lsadump.Lsadump #Grab lsa secrets
```
{% endtab %}

{% tab title="vol2" %}
```bash
volatility --profile=Win7SP1x86_23418 hashdump -f file.dmp #Grab common windows hashes (SAM+SYSTEM)
volatility --profile=Win7SP1x86_23418 cachedump -f file.dmp #Grab domain cache hashes inside the registry
volatility --profile=Win7SP1x86_23418 lsadump -f file.dmp #Grab lsa secrets
```
{% endtab %}
{% endtabs %}

## Memory Dump

##内存转储

The memory dump of a process will **extract everything** of the current status of the process. The **procdump** module will only **extract** the **code**.

过程的内存转储将**提取该过程当前状态的所有内容。 ** procdump **模块仅**提取** **代码**。

```
volatility -f file.dmp --profile=Win7SP1x86 memdump -p 2168 -D conhost/
```

## Processes

### List processes

Try to find **suspicious** processes (by name) or **unexpected** child **processes** (for example a cmd.exe as a child of iexplorer.exe).\

尝试查找**可疑**过程（按名称）或**意外** child ** process **（例如，cmd.exe作为iexplorer.exe的孩子）。\ \ \ \ \
It could be interesting to **compare** the result of pslist with the one of psscan to identify hidden processes.

**比较** PSLIST与PSSCAN的结果以识别隐藏的过程可能很有趣。

{% tabs %}
{% tab title="vol3" %}
```bash
python3 vol.py -f file.dmp windows.pstree.PsTree # Get processes tree (not hidden)
python3 vol.py -f file.dmp windows.pslist.PsList # Get process list (EPROCESS)
python3 vol.py -f file.dmp windows.psscan.PsScan # Get hidden process list(malware)
```
{% endtab %}

{% tab title="vol2" %}
```bash
volatility --profile=PROFILE pstree -f file.dmp # Get process tree (not hidden)
volatility --profile=PROFILE pslist -f file.dmp # Get process list (EPROCESS)
volatility --profile=PROFILE psscan -f file.dmp # Get hidden process list(malware)
volatility --profile=PROFILE psxview -f file.dmp # Get hidden process list
```
{% endtab %}
{% endtabs %}

### Dump proc

{% tabs %}
{% tab title="vol3" %}
```bash
./vol.py -f file.dmp windows.dumpfiles.DumpFiles --pid <pid> #Dump the .exe and dlls of the process in the current directory
```
{% endtab %}

{% tab title="vol2" %}
```bash
volatility --profile=Win7SP1x86_23418 procdump --pid=3152 -n --dump-dir=. -f file.dmp
```
{% endtab %}
{% endtabs %}

### Command line

＃＃＃ 命令行

Anything suspicious was executed?

有任何可疑的执行？

{% tabs %}
{% tab title="vol3" %}
```bash
python3 vol.py -f file.dmp windows.cmdline.CmdLine #Display process command-line arguments
```
{% endtab %}

{% tab title="vol2" %}
```bash
volatility --profile=PROFILE cmdline -f file.dmp #Display process command-line arguments
volatility --profile=PROFILE consoles -f file.dmp #command history by scanning for _CONSOLE_INFORMATION
```
{% endtab %}
{% endtabs %}

Commands entered into cmd.exe are processed by **conhost.exe** (csrss.exe prior to Windows 7). So even if an attacker managed to **kill the cmd.exe** **prior** to us obtaining a memory **dump**, there is still a good chance of **recovering history** of the command line session from **conhost.exe’s memory**. If you find **something weird** (using the console's modules), try to **dump** the **memory** of the **conhost.exe associated** process and **search** for **strings** inside it to extract the command lines.

输入到cmd.exe的命令由** conhost.exe **处理（Windows 7之前的CSRSS.EXE）。 因此，即使攻击者设法**杀死了cmd.exe ** **先验**向我们获得内存**垃圾箱**，仍然很有可能**恢复命令行会话的历史记录** 来自** conhost.exe的内存**。 如果您发现**一些怪异**（使用控制台的模块），请尝试**倾倒** **内存** ** conhost.exe a相关的** consect **过程，** search ** for ** strings ** strings ** **内部提取命令行。

### Environment

Get the env variables of each running process. There could be some interesting values.

获取每个运行过程的ENV变量。 可能有一些有趣的价值观。

{% tabs %}
{% tab title="vol3" %}
```bash
python3 vol.py -f file.dmp windows.envars.Envars [--pid <pid>] #Display process environment variables
```
{% endtab %}

{% tab title="vol2" %}
```bash
volatility --profile=PROFILE envars -f file.dmp [--pid <pid>] #Display process environment variables

volatility --profile=PROFILE -f file.dmp linux_psenv [-p <pid>] #Get env of process. runlevel var means the runlevel where the proc is initated 
```
{% endtab %}
{% endtabs %}

### Token privileges

Check for privileges tokens in unexpected services.\

在意外服务中检查是否有特权令牌。\
It could be interesting to list the processes using some privileged token.

使用一些特权令牌列出这些过程可能很有趣。

{% tabs %}
{% tab title="vol3" %}
```bash
#Get enabled privileges of some processes
python3 vol.py -f file.dmp windows.privileges.Privs [--pid <pid>]
#Get all processes with interesting privileges
python3 vol.py -f file.dmp windows.privileges.Privs | grep "SeImpersonatePrivilege\|SeAssignPrimaryPrivilege\|SeTcbPrivilege\|SeBackupPrivilege\|SeRestorePrivilege\|SeCreateTokenPrivilege\|SeLoadDriverPrivilege\|SeTakeOwnershipPrivilege\|SeDebugPrivilege"
```
{% endtab %}

{% tab title="vol2" %}
```bash
#Get enabled privileges of some processes
volatility --profile=Win7SP1x86_23418 privs --pid=3152 -f file.dmp | grep Enabled
#Get all processes with interesting privileges
volatility --profile=Win7SP1x86_23418 privs -f file.dmp | grep "SeImpersonatePrivilege\|SeAssignPrimaryPrivilege\|SeTcbPrivilege\|SeBackupPrivilege\|SeRestorePrivilege\|SeCreateTokenPrivilege\|SeLoadDriverPrivilege\|SeTakeOwnershipPrivilege\|SeDebugPrivilege"
```
{% endtab %}
{% endtabs %}

### SIDs

Check each SSID owned by a process.\

检查一个由过程所拥有的每个SSID。\ \
It could be interesting to list the processes using a privileges SID (and the processes using some service SID).

使用特权SID（以及使用某些服务SID的过程）列出过程可能很有趣。

{% tabs %}
{% tab title="vol3" %}
```bash
./vol.py -f file.dmp windows.getsids.GetSIDs [--pid <pid>] #Get SIDs of processes
./vol.py -f file.dmp windows.getservicesids.GetServiceSIDs #Get the SID of services
```
{% endtab %}

{% tab title="vol2" %}
```bash
volatility --profile=Win7SP1x86_23418 getsids -f file.dmp #Get the SID owned by each process
volatility --profile=Win7SP1x86_23418 getservicesids -f file.dmp #Get the SID of each service
```
{% endtab %}
{% endtabs %}

### Handles

Useful to know to which other files, keys, threads, processes... a **process has a handle** for (has opened)

有助于了解哪些其他文件，键，线程，进程... a ** process具有一个句柄**（已打开）

{% tabs %}
{% tab title="vol3" %}
```bash
vol.py -f file.dmp windows.handles.Handles [--pid <pid>]
```
{% endtab %}

{% tab title="vol2" %}
```bash
volatility --profile=Win7SP1x86_23418 -f file.dmp handles [--pid=<pid>]
```
{% endtab %}
{% endtabs %}

### DLLs

{% tabs %}
{% tab title="vol3" %}
```bash
./vol.py -f file.dmp windows.dlllist.DllList [--pid <pid>] #List dlls used by each
./vol.py -f file.dmp windows.dumpfiles.DumpFiles --pid <pid> #Dump the .exe and dlls of the process in the current directory process
```
{% endtab %}

{% tab title="vol2" %}
```bash
volatility --profile=Win7SP1x86_23418 dlllist --pid=3152 -f file.dmp #Get dlls of a proc
volatility --profile=Win7SP1x86_23418 dlldump --pid=3152 --dump-dir=. -f file.dmp #Dump dlls of a proc
```
{% endtab %}
{% endtabs %}

### Strings per processes

###每个过程的字符串

Volatility allows us to check which process a string belongs to.

波动率使我们能够检查字符串所属的过程。

{% tabs %}
{% tab title="vol3" %}
```bash
strings file.dmp > /tmp/strings.txt
./vol.py -f /tmp/file.dmp windows.strings.Strings --strings-file /tmp/strings.txt
```
{% endtab %}

{% tab title="vol2" %}
```bash
strings file.dmp > /tmp/strings.txt
volatility -f /tmp/file.dmp windows.strings.Strings --string-file /tmp/strings.txt

volatility -f /tmp/file.dmp --profile=Win81U1x64 memdump -p 3532 --dump-dir .
strings 3532.dmp > strings_file
```
{% endtab %}
{% endtabs %}

It also allows to search for strings inside a process using the yarascan module:

它还允许使用Yarascan模块在过程中搜索字符串：

{% tabs %}
{% tab title="vol3" %}
```bash
./vol.py -f file.dmp windows.vadyarascan.VadYaraScan --yara-rules "https://" --pid 3692 3840 3976 3312 3084 2784
./vol.py -f file.dmp yarascan.YaraScan --yara-rules "https://"
```
{% endtab %}

{% tab title="vol2" %}
```bash
volatility --profile=Win7SP1x86_23418 yarascan -Y "https://" -p 3692,3840,3976,3312,3084,2784
```
{% endtab %}
{% endtabs %}

### UserAssist

**Windows** systems maintain a set of **keys** in the registry database (**UserAssist keys**) to keep track of programs that are executed. The number of executions and last execution date and time is available in these **keys**.

** Windows **系统在注册表数据库中维护一组**密钥**（**用户库密钥**），以跟踪执行的程序。 这些**键**可用执行数量和最后执行日期和时间。

{% tabs %}
{% tab title="vol3" %}
```bash
./vol.py -f file.dmp windows.registry.userassist.UserAssist
```
{% endtab %}

{% tab title="vol2" %}
```
volatility --profile=Win7SP1x86_23418 -f file.dmp userassist
```
{% endtab %}
{% endtabs %}

## Services

＃＃ 服务

{% tabs %}
{% tab title="vol3" %}
```bash
./vol.py -f file.dmp windows.svcscan.SvcScan #List services
./vol.py -f file.dmp windows.getservicesids.GetServiceSIDs #Get the SID of services
```
{% endtab %}

{% tab title="vol2" %}
```bash
#Get services and binary path
volatility --profile=Win7SP1x86_23418 svcscan -f file.dmp
#Get name of the services and SID (slow)
volatility --profile=Win7SP1x86_23418 getservicesids -f file.dmp
```
{% endtab %}
{% endtabs %}

## Network

{% tabs %}
{% tab title="vol3" %}
```bash
./vol.py -f file.dmp windows.netscan.NetScan
#For network info of linux use volatility2
```
{% endtab %}

{% tab title="vol2" %}
```bash
volatility --profile=Win7SP1x86_23418 netscan -f file.dmp
volatility --profile=Win7SP1x86_23418 connections -f file.dmp#XP and 2003 only
volatility --profile=Win7SP1x86_23418 connscan -f file.dmp#TCP connections 
volatility --profile=Win7SP1x86_23418 sockscan -f file.dmp#Open sockets
volatility --profile=Win7SP1x86_23418 sockets -f file.dmp#Scanner for tcp socket objects

volatility --profile=SomeLinux -f file.dmp linux_ifconfig
volatility --profile=SomeLinux -f file.dmp linux_netstat
volatility --profile=SomeLinux -f file.dmp linux_netfilter
volatility --profile=SomeLinux -f file.dmp linux_arp #ARP table
volatility --profile=SomeLinux -f file.dmp linux_list_raw #Processes using promiscuous raw sockets (comm between processes)
volatility --profile=SomeLinux -f file.dmp linux_route_cache
```
{% endtab %}
{% endtabs %}

## Registry hive

##注册表Hive

### Print available hives

{% tabs %}
{% tab title="vol3" %}
```bash
./vol.py -f file.dmp windows.registry.hivelist.HiveList #List roots
./vol.py -f file.dmp windows.registry.printkey.PrintKey #List roots and get initial subkeys
```
{% endtab %}

{% tab title="vol2" %}
```bash
volatility --profile=Win7SP1x86_23418 -f file.dmp hivelist #List roots
volatility --profile=Win7SP1x86_23418 -f file.dmp printkey #List roots and get initial subkeys
```
{% endtab %}
{% endtabs %}

### Get a value

{% tabs %}
{% tab title="vol3" %}
```bash
./vol.py -f file.dmp windows.registry.printkey.PrintKey --key "Software\Microsoft\Windows NT\CurrentVersion"
```
{% endtab %}

{% tab title="vol2" %}
```bash
volatility --profile=Win7SP1x86_23418 printkey -K "Software\Microsoft\Windows NT\CurrentVersion" -f file.dmp
# Get Run binaries registry value
volatility -f file.dmp --profile=Win7SP1x86 printkey -o 0x9670e9d0 -K 'Software\Microsoft\Windows\CurrentVersion\Run'
```
{% endtab %}
{% endtabs %}

### Dump

```bash
#Dump a hive
volatility --profile=Win7SP1x86_23418 hivedump -o 0x9aad6148 -f file.dmp #Offset extracted by hivelist
#Dump all hives
volatility --profile=Win7SP1x86_23418 hivedump -f file.dmp
```

## Filesystem

### Mount

＃＃＃ 山

{% tabs %}
{% tab title="vol3" %}
```bash
#See vol2
```
{% endtab %}

{% tab title="vol2" %}
```bash
volatility --profile=SomeLinux -f file.dmp linux_mount
volatility --profile=SomeLinux -f file.dmp linux_recover_filesystem #Dump the entire filesystem (if possible)
```
{% endtab %}
{% endtabs %}

### Scan/dump

{% tabs %}
{% tab title="vol3" %}
```bash
./vol.py -f file.dmp windows.filescan.FileScan #Scan for files inside the dump
./vol.py -f file.dmp windows.dumpfiles.DumpFiles --physaddr <0xAAAAA> #Offset from previous command
```
{% endtab %}

{% tab title="vol2" %}
```bash
volatility --profile=Win7SP1x86_23418 filescan -f file.dmp #Scan for files inside the dump
volatility --profile=Win7SP1x86_23418 dumpfiles -n --dump-dir=/tmp -f file.dmp #Dump all files
volatility --profile=Win7SP1x86_23418 dumpfiles -n --dump-dir=/tmp -Q 0x000000007dcaa620 -f file.dmp

volatility --profile=SomeLinux -f file.dmp linux_enumerate_files
volatility --profile=SomeLinux -f file.dmp linux_find_file -F /path/to/file
volatility --profile=SomeLinux -f file.dmp linux_find_file -i 0xINODENUMBER -O /path/to/dump/file
```
{% endtab %}
{% endtabs %}

### Master File Table

{% tabs %}
{% tab title="vol3" %}
```bash
# I couldn't find any plugin to extract this information in volatility3
```
{% endtab %}

{% tab title="vol2" %}
```bash
volatility --profile=Win7SP1x86_23418 mftparser -f file.dmp
```
{% endtab %}
{% endtabs %}

The NTFS file system contains a file called the _master file table_, or MFT. There is at least one entry in the MFT for every file on an NTFS file system volume, including the MFT itself. **All information about a file, including its size, time and date stamps, permissions, and data content**, is stored either in MFT entries, or in space outside the MFT that is described by MFT entries. From [here](https://docs.microsoft.com/en-us/windows/win32/fileio/master-file-table).

NTFS文件系统包含一个名为_master文件表的文件，或MFT。 NTFS文件系统卷（包括MFT本身）中的每个文件中的MFT中至少有一个条目。 **有关文件的所有信息，包括其大小，时间和日期邮票，权限和数据内容**，都存储在MFT条目中，或者由MFT条目描述的MFT之外的空间存储。 来自[here]（https://docs.microsoft.com/en-us/windows/windows/win32/fileio/master-file-table）。

### SSL Keys/Certs

### SSL键/证书

{% tabs %}
{% tab title="vol3" %}
```bash
#vol3 allows to search for certificates inside the registry
./vol.py -f file.dmp windows.registry.certificates.Certificates
```
{% endtab %}

{% tab title="vol2" %}
```bash
#vol2 allos you to search and dump certificates from memory
#Interesting options for this modules are: --pid, --name, --ssl
volatility --profile=Win7SP1x86_23418 dumpcerts --dump-dir=. -f file.dmp
```
{% endtab %}
{% endtabs %}

## Malware

##恶意软件

{% tabs %}
{% tab title="vol3" %}
```bash
./vol.py -f file.dmp windows.malfind.Malfind [--dump] #Find hidden and injected code, [dump each suspicious section]
#Malfind will search for suspicious structures related to malware
./vol.py -f file.dmp windows.driverirp.DriverIrp #Driver IRP hook detection
./vol.py -f file.dmp windows.ssdt.SSDT #Check system call address from unexpected addresses

./vol.py -f file.dmp linux.check_afinfo.Check_afinfo #Verifies the operation function pointers of network protocols
./vol.py -f file.dmp linux.check_creds.Check_creds #Checks if any processes are sharing credential structures
./vol.py -f file.dmp linux.check_idt.Check_idt #Checks if the IDT has been altered
./vol.py -f file.dmp linux.check_syscall.Check_syscall #Check system call table for hooks
./vol.py -f file.dmp linux.check_modules.Check_modules #Compares module list to sysfs info, if available
./vol.py -f file.dmp linux.tty_check.tty_check #Checks tty devices for hooks
```
{% endtab %}

{% tab title="vol2" %}
```bash
volatility --profile=Win7SP1x86_23418 -f file.dmp malfind [-D /tmp] #Find hidden and injected code [dump each suspicious section]
volatility --profile=Win7SP1x86_23418 -f file.dmp apihooks #Detect API hooks in process and kernel memory
volatility --profile=Win7SP1x86_23418 -f file.dmp driverirp #Driver IRP hook detection
volatility --profile=Win7SP1x86_23418 -f file.dmp ssdt #Check system call address from unexpected addresses

volatility --profile=SomeLinux -f file.dmp linux_check_afinfo
volatility --profile=SomeLinux -f file.dmp linux_check_creds
volatility --profile=SomeLinux -f file.dmp linux_check_fop
volatility --profile=SomeLinux -f file.dmp linux_check_idt
volatility --profile=SomeLinux -f file.dmp linux_check_syscall
volatility --profile=SomeLinux -f file.dmp linux_check_modules
volatility --profile=SomeLinux -f file.dmp linux_check_tty
volatility --profile=SomeLinux -f file.dmp linux_keyboard_notifiers #Keyloggers
```
{% endtab %}
{% endtabs %}

### Scanning with yara

###与Yara扫描

Use this script to download and merge all the yara malware rules from github: [https://gist.github.com/andreafortuna/29c6ea48adf3d45a979a78763cdc7ce9](https://gist.github.com/andreafortuna/29c6ea48adf3d45a979a78763cdc7ce9)\

使用此脚本从GitHub下载并合并所有Yara恶意软件规则：[https://gist.github.com/andreaforna/29c6ea48adf3d45a979a78763cdc7ce9]
Create the _**rules**_ directory and execute it. This will create a file called _**malware\_rules.yar**_ which contains all the yara rules for malware.

创建_ **规则** _目录并执行它。 这将创建一个名为_ **恶意软件\ _rules.yar ** _的文件，其中包含所有YARA恶意软件规则。

{% tabs %}
{% tab title="vol3" %}
```bash
wget https://gist.githubusercontent.com/andreafortuna/29c6ea48adf3d45a979a78763cdc7ce9/raw/4ec711d37f1b428b63bed1f786b26a0654aa2f31/malware_yara_rules.py
mkdir rules
python malware_yara_rules.py
#Only Windows
./vol.py -f file.dmp windows.vadyarascan.VadYaraScan --yara-file /tmp/malware_rules.yar
#All
./vol.py -f file.dmp yarascan.YaraScan --yara-file /tmp/malware_rules.yar
```
{% endtab %}

{% tab title="vol2" %}
```bash
wget https://gist.githubusercontent.com/andreafortuna/29c6ea48adf3d45a979a78763cdc7ce9/raw/4ec711d37f1b428b63bed1f786b26a0654aa2f31/malware_yara_rules.py
mkdir rules
python malware_yara_rules.py
volatility --profile=Win7SP1x86_23418 yarascan -y malware_rules.yar -f ch2.dmp | grep "Rule:" | grep -v "Str_Win32" | sort | uniq
```
{% endtab %}
{% endtabs %}

## MISC

## Misc

### External plugins

If you want to use external plugins make sure that the folders related to the plugins are the first parameter used.

如果要使用外部插件，请确保与插件相关的文件夹是使用的第一个参数。

{% tabs %}
{% tab title="vol3" %}
```bash
./vol.py --plugin-dirs "/tmp/plugins/" [...]
```
{% endtab %}

{% tab title="vol2" %}
```bash
 volatilitye --plugins="/tmp/plugins/" [...]
```
{% endtab %}
{% endtabs %}

#### Autoruns

Download it from [https://github.com/tomchop/volatility-autoruns](https://github.com/tomchop/volatility-autoruns)

从[https://github.com/tomchop/volatility-autoruns]（https://github.com/

```
 volatility --plugins=volatility-autoruns/ --profile=WinXPSP2x86 -f file.dmp autoruns
```

### Mutexes

{% tabs %}
{% tab title="vol3" %}
```
./vol.py -f file.dmp windows.mutantscan.MutantScan
```
{% endtab %}

{% tab title="vol2" %}
```bash
volatility --profile=Win7SP1x86_23418 mutantscan -f file.dmp
volatility --profile=Win7SP1x86_23418 -f file.dmp handles -p <PID> -t mutant
```
{% endtab %}
{% endtabs %}

### Symlinks

{% tabs %}
{% tab title="vol3" %}
```bash
./vol.py -f file.dmp windows.symlinkscan.SymlinkScan
```
{% endtab %}

{% tab title="vol2" %}
```bash
volatility --profile=Win7SP1x86_23418 -f file.dmp symlinkscan
```
{% endtab %}
{% endtabs %}

### Bash

It's possible to **read from memory the bash history.** You could also dump the _.bash\_history_ file, but it was disabled you will be glad you can use this volatility module

可以**从内存中读取bash历史记录。

{% tabs %}
{% tab title="vol3" %}
```
./vol.py -f file.dmp linux.bash.Bash
```
{% endtab %}

{% tab title="vol2" %}
```
volatility --profile=Win7SP1x86_23418 -f file.dmp linux_bash
```
{% endtab %}
{% endtabs %}

### TimeLine

{% tabs %}
{% tab title="vol3" %}
```bash
./vol.py -f file.dmp timeLiner.TimeLiner
```
{% endtab %}

{% tab title="vol2" %}
```
volatility --profile=Win7SP1x86_23418 -f timeliner
```
{% endtab %}
{% endtabs %}

### Drivers

{% tabs %}
{% tab title="vol3" %}
```
./vol.py -f file.dmp windows.driverscan.DriverScan
```
{% endtab %}

{% tab title="vol2" %}
```bash
volatility --profile=Win7SP1x86_23418 -f file.dmp driverscan
```
{% endtab %}
{% endtabs %}

### Get clipboard

###获取剪贴板

```bash
#Just vol2
volatility --profile=Win7SP1x86_23418 clipboard -f file.dmp
```

### Get IE history

###获取IE历史

```bash
#Just vol2
volatility --profile=Win7SP1x86_23418 iehistory -f file.dmp
```

### Get notepad text

###获取记事本文字

```bash
#Just vol2
volatility --profile=Win7SP1x86_23418 notepad -f file.dmp
```

### Screenshot

＃＃＃ 截屏

```bash
#Just vol2
volatility --profile=Win7SP1x86_23418 screenshot -f file.dmp
```

### Master Boot Record (MBR)

###主启动记录（MBR）

```
volatility --profile=Win7SP1x86_23418 mbrparser -f file.dmp
```

The MBR holds the information on how the logical partitions, containing [file systems](https://en.wikipedia.org/wiki/File\_system), are organized on that medium. The MBR also contains executable code to function as a loader for the installed operating system—usually by passing control over to the loader's [second stage](https://en.wikipedia.org/wiki/Second-stage\_boot\_loader), or in conjunction with each partition's [volume boot record](https://en.wikipedia.org/wiki/Volume\_boot\_record) (VBR). This MBR code is usually referred to as a [boot loader](https://en.wikipedia.org/wiki/Boot\_loader). From [here](https://en.wikipedia.org/wiki/Master\_boot\_record).

MBR拥有有关如何包含[文件系统]（https://en.wikipedia.org/wiki/file_system）的逻辑分区的信息。 MBR还包含可执行的代码，可作为已安装操作系统的加载程序运行 - 通常通过将控件传递到加载程序的[第二阶段]（https://en.wikipedia.org/wiki/wiki/second-second-stage \_boot \__loader） ，或与每个分区的[卷启动记录]（https://en.wikipedia.org/wiki/volume/volume/_boot \ _record）（vbr）结合使用。 此MBR代码通常称为[boot Loader]（https://en.wikipedia.org/wiki/wiki/boot \ _loader）。 来自[此处]（https://en.wikipedia.org/wiki/master \_boot \_record）。

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
