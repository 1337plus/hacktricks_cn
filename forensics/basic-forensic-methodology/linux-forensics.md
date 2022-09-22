# Linux Forensics

{% hint style="danger" %}
![](<../../.gitbook/assets/image (9) (1).png>)

\
Use [**Trickest**](https://trickest.com/?utm\_campaign=hacktrics\&utm\_medium=banner\&utm\_source=hacktricks) to easily build and **automate workflows** powered by the world's **most advanced** community tools.\

使用[** trickest **]（https://trickest.com/?utm \_campaign=hacktrics \ _utm \ _Medium = bannerver＆utm \ _source=hacktricks = hacktricks）轻松构建和**自动化工作流** **最先进的**社区工具。\
Get Access Today:

立即获取访问：

{% embed url="https://trickest.com/?utm_campaign=hacktrics&utm_medium=banner&utm_source=hacktricks" %}
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

## Initial Information Gathering

##初始信息收集

### Basic Information

＃＃＃ 基本信息

First of all, it's recommended to have some **USB** with **good known binaries and libraries on it** (you can just get ubuntu and copy the folders _/bin_, _/sbin_, _/lib,_ and _/lib64_), then mount the USB, and modify the env variables to use those binaries:

首先，建议在上面有一些** usb ** ** **众所周知的二进制文件和图书馆**（您可以获取ubuntu并复制文件夹_/bin_，_/sbin_，_/_/_/lib，_和 _/lib64_），然后安装USB，然后修改ENV变量以使用这些二进制文件：

```bash
export PATH=/mnt/usb/bin:/mnt/usb/sbin
export LD_LIBRARY_PATH=/mnt/usb/lib:/mnt/usb/lib64
```

Once you have configured the system to use good and known binaries you can start **extracting some basic information**:

一旦配置了系统使用良好和已知的二进制文件，您就可以开始**提取一些基本信息**：

```bash
date #Date and time (Clock may be skewed, Might be at a different timezone)
uname -a #OS info
ifconfig -a || ip a #Network interfaces (promiscuous mode?)
ps -ef #Running processes
netstat -anp #Proccess and ports
lsof -V #Open files
netstat -rn; route #Routing table
df; mount #Free space and mounted devices
free #Meam and swap space
w #Who is connected
last -Faiwx #Logins
lsmod #What is loaded
cat /etc/passwd #Unexpected data?
cat /etc/shadow #Unexpected data?
find /directory -type f -mtime -1 -print #Find modified files during the last minute in the directory
```

#### Suspicious information

####可疑信息

While obtaining the basic information you should check for weird things like:

在获得基本信息时，您应该检查奇怪的事情：

* **Root processes** usually run with low PIDS, so if you find a root process with a big PID you may suspect

***根过程**通常以低pids运行，因此，如果您找到具有大PID的根过程，您可能会怀疑
* Check **registered logins** of users without a shell inside `/etc/passwd`

*检查**注册的登录**，没有外壳的用户`/etc/passwd`
* Check for **password hashes** inside `/etc/shadow` for users without a shell

*检查**密码哈希**内部`/etc/shadow“无外壳的用户

### Memory Dump

###内存转储

To obtain the memory of the running system, it's recommended to use [**LiME**](https://github.com/504ensicsLabs/LiME).\

为了获得运行系统的内存，建议使用[** lime **]（https://github.com/504ensicslabs/lime）。
To **compile** it, you need to use the **same kernel** that the victim machine is using.

要**编译**，您需要使用受害机器使用的** **的内核**。

{% hint style="info" %}

{％提示样式=“ info”％}
Remember that you **cannot install LiME or any other thing** in the victim machine as it will make several changes to it

请记住，您**无法在受害者机器中安装石灰或其他任何东西**，因为它将对其进行多个更改
{% endhint %}

So, if you have an identical version of Ubuntu you can use `apt-get install lime-forensics-dkms`\

因此，如果您有相同的Ubuntu版本，则可以使用``apt-get install install install lime-forensics-dkms' \
In other cases, you need to download [**LiME**](https://github.com/504ensicsLabs/LiME) from github and compile it with correct kernel headers. To **obtain the exact kernel headers** of the victim machine, you can just **copy the directory** `/lib/modules/<kernel version>` to your machine, and then **compile** LiME using them:

在其他情况下，您需要从github下载[** lime **]（https://github.com/504ensicslabs/lime），并使用正确的内核标题对其进行编译。 要**获取受害机器的确切内核标头**，您只需**复制目录**`/lib/lib/lib/<kernel版本>`送给您的计算机，然后使用它们** compile ** lime lime ：

```bash
make -C /lib/modules/<kernel version>/build M=$PWD
sudo insmod lime.ko "path=/home/sansforensics/Desktop/mem_dump.bin format=lime"
```

LiME supports 3 **formats**:

石灰支持3 **格式**：

* Raw (every segment concatenated together)

* RAW（每个片段串联在一起）
* Padded (same as raw, but with zeroes in right bits)

*填充（与RAW相同，但零位为零）
* Lime (recommended format with metadata

*石灰（推荐格式与元数据

LiME can also be used to **send the dump via network** instead of storing it on the system using something like: `path=tcp:4444`

石灰也可以用于**通过网络**发送转储，而不是使用以下内容以：`path = tcp：4444`将其存储在系统上。

### Disk Imaging

#### Shutting down

####关闭

First of all, you will need to **shut down the system**. This isn't always an option as some times system will be a production server that the company cannot afford to shut down.\

首先，您需要**关闭系统**。 这并不总是一个选择，因为有时系统将是公司无法关闭的生产服务器。
There are **2 ways** of shutting down the system, a **normal shutdown** and a **"plug the plug" shutdown**. The first one will allow the **processes to terminate as usual** and the **filesystem** to be **synchronized**, but it will also allow the possible **malware** to **destroy evidence**. The "pull the plug" approach may carry **some information loss** (not much of the info is going to be lost as we already took an image of the memory ) and the **malware won't have any opportunity** to do anything about it. Therefore, if you **suspect** that there may be a **malware**, just execute the **`sync`** **command** on the system and pull the plug.

**有2种关闭系统的方法，一个正常的关闭**和a **“插头插头”关闭**。 第一个将允许**过程照常终止**，并且**文件系统**已被**同步**，但它也将允许可能的**恶意软件** **销毁证据**。 “拉插头”方法可能会带来**一些信息丢失**（由于我们已经拍摄了内存的图像，不会丢失很多信息），而且**恶意软件将没有任何机会** 做任何事情。 因此，如果您**怀疑**可能存在**恶意软件**，则只需在系统上执行**`s sync` ** **命令**并拉插头即可。

#### Taking an image of the disk

####拍摄磁盘的图像

It's important to note that **before connecting your computer to anything related to the case**, you need to be sure that it's going to be **mounted as read only** to avoid modifying any information.

重要的是要注意，**将计算机连接到与案例相关的任何内容之前，您需要确保将其安装为仅读取**，以避免修改任何信息。

```bash
#Create a raw copy of the disk
dd if=<subject device> of=<image file> bs=512

#Raw copy with hashes along the way (more secure as it checks hashes while it's copying the data)
dcfldd if=<subject device> of=<image file> bs=512 hash=<algorithm> hashwindow=<chunk size> hashlog=<hash file>
dcfldd if=/dev/sdc of=/media/usb/pc.image hash=sha256 hashwindow=1M hashlog=/media/usb/pc.hashes
```

### Disk Image pre-analysis

###磁盘图像预进图

Imaging a disk image with no more data.

```bash
#Find out if it's a disk image using "file" command
file disk.img 
disk.img: Linux rev 1.0 ext4 filesystem data, UUID=59e7a736-9c90-4fab-ae35-1d6a28e5de27 (extents) (64bit) (large files) (huge files)

#Check which type of disk image it's
img_stat -t evidence.img 
raw
#You can list supported types with
img_stat -i list
Supported image format types:
        raw (Single or split raw file (dd))
        aff (Advanced Forensic Format)
        afd (AFF Multiple File)
        afm (AFF with external metadata)
        afflib (All AFFLIB image formats (including beta ones))
        ewf (Expert Witness Format (EnCase))

#Data of the image
fsstat -i raw -f ext4 disk.img 
FILE SYSTEM INFORMATION
--------------------------------------------
File System Type: Ext4
Volume Name: 
Volume ID: 162850f203fd75afab4f1e4736a7e776

Last Written at: 2020-02-06 06:22:48 (UTC)
Last Checked at: 2020-02-06 06:15:09 (UTC)

Last Mounted at: 2020-02-06 06:15:18 (UTC)
Unmounted properly
Last mounted on: /mnt/disk0

Source OS: Linux
[...]

#ls inside the image
fls -i raw -f ext4 disk.img
d/d 11: lost+found
d/d 12: Documents
d/d 8193:       folder1
d/d 8194:       folder2
V/V 65537:      $OrphanFiles

#ls inside folder
fls -i raw -f ext4 disk.img 12
r/r 16: secret.txt

#cat file inside image
icat -i raw -f ext4 disk.img 16
ThisisTheMasterSecret
```

{% hint style="danger" %}
![](<../../.gitbook/assets/image (9) (1).png>)

\
Use [**Trickest**](https://trickest.com/?utm\_campaign=hacktrics\&utm\_medium=banner\&utm\_source=hacktricks) to easily build and **automate workflows** powered by the world's **most advanced** community tools.\

使用[** trickest **]（https://trickest.com/?utm \_campaign=hacktrics \ _utm \ _Medium = bannerver＆utm \ _source=hacktricks = hacktricks）轻松构建和**自动化工作流** **最先进的**社区工具。\
Get Access Today:

立即获取访问：

{% embed url="https://trickest.com/?utm_campaign=hacktrics&utm_medium=banner&utm_source=hacktricks" %}
{% endhint %}

## Search for known Malware

##搜索已知恶意软件

### Modified System Files

###修改的系统文件

Some Linux systems have a feature to **verify the integrity of many installed components**, providing an effective way to identify unusual or out of place files. For instance, `rpm -Va` on Linux is designed to verify all packages that were installed using RedHat Package Manager.

一些Linux系统具有**验证许多已安装组件**的完整性的功能，从而提供了一种有效的方法来识别异常或不合时宜的文件。 例如，Linux上的`rpm -VA`旨在验证使用RedHat软件包管理器安装的所有软件包。

```bash
#RedHat
rpm -Va
#Debian
dpkg --verify
debsums | grep -v "OK$" #apt-get install debsums
```

### Malware/Rootkit Detectors

###恶意软件/rootkit检测器

Read the following page to learn about tools that can be useful to find malware:

阅读以下页面以了解可用于查找恶意软件的工具：

{% content-ref url="malware-analysis.md" %}

{％content-ref url =“ malware-Analysis.md”％}
[malware-analysis.md](malware-analysis.md)

[MALWARE-ALASIS.MD]（恶意软件 - 分析）
{% endcontent-ref %}

## Search installed programs

##搜索安装程序

### Package Manager

On Debian-based systems, the _**/var/ lib/dpkg/status**_ file contains details about installed packages and the _**/var/log/dpkg.log**_ file records information when a package is installed.\

在基于debian的系统上，_ **/var/lib/dpkg/status ** _文件包含有关已安装软件包的详细信息，_ **/var/log/log/dpkg.log ** _文件记录信息当包含在软件包时 安装。\ \
On RedHat and related Linux distributions the **`rpm -qa --root=/ mntpath/var/lib/rpm`** command will list the contents of an RPM database on a system.

在RedHat和相关的Linux发行版上，**`````rpm -qa -qa -qa =/mntpath/var/lib/rpm` **命令将列出系统上RPM数据库的内容。

```bash
#Debian
cat /var/lib/dpkg/status | grep -E "Package:|Status:"
cat /var/log/dpkg.log | grep installed
#RedHat
rpm -qa --root=/ mntpath/var/lib/rpm
```

### Other

＃＃＃ 其他

**Not all installed programs will be listed by the above commands** because some applications are not available as packages for certain systems and must be installed from the source. Therefore, a review of locations such as _**/usr/local**_ and _**/opt**_ may reveal other applications that have been compiled and installed from source code.

**并非所有安装程序都将由上述命令列出**，因为某些应用程序无法作为某些系统的软件包可用，必须从源头安装。 因此，对诸如_ **/usr/local ** _和_ **/opt ** _之类的位置的审查可能会揭示已从源代码编译和安装的其他应用程序。

```bash
ls /opt /usr/local
```

Another good idea is to **check** the **common folders** inside **$PATH** for **binaries not related** to **installed packages:**

另一个好主意是**检查** **公共文件夹**内部** $ path ** ** binaries与**安装软件包无关的二进制文件：**

```bash
#Both lines are going to print the executables in /sbin non related to installed packages
#Debian
find /sbin/ -exec dpkg -S {} \; | grep "no path found"
#RedHat
find /sbin/ –exec rpm -qf {} \; | grep "is not"
```

{% hint style="danger" %}
![](<../../.gitbook/assets/image (9) (1).png>)

\
Use [**Trickest**](https://trickest.com/?utm\_campaign=hacktrics\&utm\_medium=banner\&utm\_source=hacktricks) to easily build and **automate workflows** powered by the world's **most advanced** community tools.\

使用[** trickest **]（https://trickest.com/?utm \_campaign=hacktrics \ _utm \ _Medium = bannerver＆utm \ _source=hacktricks = hacktricks）轻松构建和**自动化工作流** **最先进的**社区工具。\
Get Access Today:

立即获取访问：

{% embed url="https://trickest.com/?utm_campaign=hacktrics&utm_medium=banner&utm_source=hacktricks" %}
{% endhint %}

## Recover Deleted Running Binaries

##恢复已删除的运行二进制文件

![](<../../.gitbook/assets/image (641).png>)

## Inspect Autostart locations

##检查AutoStart位置

### Scheduled Tasks

＃＃＃ 计划任务

```bash
cat /var/spool/cron/crontabs/*  \
/var/spool/cron/atjobs \
/var/spool/anacron \
/etc/cron* \
/etc/at* \
/etc/anacrontab \
/etc/incron.d/* \
/var/spool/incron/* \

#MacOS
ls -l /usr/lib/cron/tabs/ /Library/LaunchAgents/ /Library/LaunchDaemons/ ~/Library/LaunchAgents/
```

### Services

＃＃＃ 服务

It is extremely common for malware to entrench itself as a new, unauthorized service. Linux has a number of scripts that are used to start services as the computer boots. The initialization startup script _**/etc/inittab**_ calls other scripts such as rc.sysinit and various startup scripts under the _**/etc/rc.d/**_ directory, or _**/etc/rc.boot/**_ in some older versions. On other versions of Linux, such as Debian, startup scripts are stored in the _**/etc/init.d/**_ directory. In addition, some common services are enabled in _**/etc/inetd.conf**_ or _**/etc/xinetd/**_ depending on the version of Linux. Digital investigators should inspect each of these startup scripts for anomalous entries.

恶意软件将自己作为一种新的，未经授权的服务牢固，这是非常普遍的。 Linux有许多用于启动服务作为计算机启动的脚本。 初始化启动脚本_ **/etc/intab ** _ _调用其他脚本，例如rc.sysinit和_ **/etc/etc.d/rc.d/** _ directory或_ **/etc/etc/ rc.boot/** _在一些较旧版本中。 在其他版本的Linux（例如Debian）上，启动脚本存储在_ **/etc/int.d/** _ Directory中。 此外，在_ **/etc/inetd.conf ** _或_ **/etc/etc/xinetd/** _ _ _ _ _ **/etetd.conf ** _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _的。 数字调查人员应检查这些启动脚本中的每个脚本是否有异常条目。

* _**/etc/inittab**_
* _**/etc/rc.d/**_
* _**/etc/rc.boot/**_

*_ **/etc/rc.boot/** _ _
* _**/etc/init.d/**_
* _**/etc/inetd.conf**_
* _**/etc/xinetd/**_
* _**/etc/systemd/system**_
* _**/etc/systemd/system/multi-user.target.wants/**_

### Kernel Modules

On Linux systems, kernel modules are commonly used as rootkit components for malware packages. Kernel modules are loaded when the system boots up based on the configuration information in the `/lib/modules/'uname -r'` and `/etc/modprobe.d` directories, and the `/etc/modprobe` or `/etc/modprobe.conf` file. These areas should be inspected for items that are related to malware.

在Linux系统上，内核模块通常用作恶意软件软件包的rootkit组件。 当系统基于`/lib/lib/modules/'uname -r''和`ect/modprobe.d`目录以及`/etc/etc/modprobe`或``'eet eetc/modprobe`或`/ etc/modprobe.conf`文件。 这些区域应检查与恶意软件相关的项目。

### Other Autostart Locations

###其他AutoStart位置

There are several configuration files that Linux uses to automatically launch an executable when a user logs into the system that may contain traces of malware.

当用户将可能包含恶意软件痕迹的系统登录到系统中时，Linux使用的几个配置文件可以自动启动可执行文件。

* _**/etc/profile.d/\***_ , _**/etc/profile**_ , _**/etc/bash.bashrc**_ are executed when any user account logs in.

*_ **/etc/profile.d/\ *** _，_ **/etc/profile ** _，_ **/etc/etc/bash.bashrc ** _ _ _当任何用户帐户登录时。
* _**∼/.bashrc**_ , _**∼/.bash\_profile**_ , _**\~/.profile**_ , _**∼/.config/autostart**_ are executed when the specific user logs in.

*_ **〜/.bashrc ** _，_ **〜/.bash \ _ -profile ** _，_ ** \〜/.profile ** _，_，_ ** **〜/.config/autostart ** _是 当特定用户登录时执行。
* _**/etc/rc.local**_ It is traditionally executed after all the normal system services are started, at the end of the process of switching to a multiuser runlevel.

*_ **/etc/rc.local ** _ _传统上是在所有普通系统服务启动之后，在切换到多源Runlevel的过程结束时。

## Examine Logs

Look in all available log files on the compromised system for traces of malicious execution and associated activities such as the creation of a new service.

查看受感染的系统上的所有可用日志文件，以了解恶意执行的痕迹和相关活动，例如创建新服务。

### Pure Logs

###纯日志

**Login** events recorded in the system and security logs, including logins via the network, can reveal that **malware** or an **intruder gained access** to a compromised system via a given account at a specific time. Other events around the time of a malware infection can be captured in system logs, including the **creation** of a **new** **service** or new accounts around the time of an incident.\

**登录**系统和安全日志中记录的事件（包括通过网络登录）可以揭示**恶意软件**或**入侵者在特定时间通过给定的帐户获得折衷的系统的访问权限。 可能会在系统日志中捕获恶意软件感染期间的其他事件，包括**新** **服务**的**创建**或事件发生时的新帐户。\ \ \ \
Interesting system logins:

* **/var/log/syslog** (debian) or **/var/log/messages** (Redhat)
  * Shows general messages and info regarding the system. It is a data log of all activity throughout the global system.

*显示有关系统的一般消息和信息。 它是整个全球系统中所有活动的数据日志。
* **/var/log/auth.log** (debian) or **/var/log/secure** (Redhat)

***/var/log/auth.log **（debian）或**/var/log/secure **（redhat）  * Keep authentication logs for both successful or failed logins, and authentication processes. Storage depends on the system type.

*保留成功或失败登录和身份验证过程的身份验证日志。 存储取决于系统类型。
  * `cat /var/log/auth.log | grep -iE "session opened for|accepted password|new session|not in sudoers"`

*`cat/var/log/auth.log | grep -ie“为|接受密码打开的会话|新会话|不在sudoers中”`````````
* **/var/log/boot.log**: start-up messages and boot info.

***/var/log/boot.log **：启动消息和引导信息。
* **/var/log/maillog** or **var/log/mail.log:** is for mail server logs, handy for postfix, smtpd, or email-related services info running on your server.
* **/var/log/kern.log**: keeps in Kernel logs and warning info. Kernel activity logs (e.g., dmesg, kern.log, klog) can show that a particular service crashed repeatedly, potentially indicating that an unstable trojanized version was installed.

***/var/log/kern.log **：保留内核日志和警告信息。 内核活动日志（例如DMESG，KERN.LOG，KLOG）可以证明特定的服务反复崩溃，可能表明已安装了不稳定的Trojanized版本。
* **/var/log/dmesg**: a repository for device driver messages. Use **dmesg** to see messages in this file.

***/var/log/dmesg **：设备驱动程序消息的存储库。 使用** dmesg **查看此文件中的消息。
* **/var/log/faillog:** records info on failed logins. Hence, handy for examining potential security breaches like login credential hacks and brute-force attacks.

***/var/log/faillog：**记录有关登录失败的信息。 因此，很方便检查潜在的安全漏洞，例如登录凭证黑客攻击和蛮力攻击。
* **/var/log/cron**: keeps a record of Crond-related messages (cron jobs). Like when the cron daemon started a job.

***/var/log/cron **：保留与Crond相关消息的记录（CRON作业）。 就像克朗守护程序开始工作时一样。
* **/var/log/daemon.log:** keeps track of running background services but doesn’t represent them graphically.

***/var/log/daemon.log：**跟踪运行的背景服务，但并未以图形方式表示它们。
* **/var/log/btmp**: keeps a note of all failed login attempts.

***/var/log/btmp **：保留所有失败登录尝试的注释。
* **/var/log/httpd/**: a directory containing error\_log and access\_log files of the Apache httpd daemon. Every error that httpd comes across is kept in the **error\_log** file. Think of memory problems and other system-related errors. **access\_log** logs all requests which come in via HTTP.

***/var/log/httpd/**：包含错误\ _log和access \ _log文件的目录apache httpd守护程序。 HTTPD遇到的每一个错误都保存在**错误\ _log **文件中。 考虑内存问题和其他与系统相关的错误。 **访问\ _log **记录通过HTTP出现的所有请求。
* **/var/log/mysqld.log** or **/var/log/mysql.log**: MySQL log file that records every debug, failure and success message, including starting, stopping and restarting of MySQL daemon mysqld. The system decides on the directory. RedHat, CentOS, Fedora, and other RedHat-based systems use /var/log/mariadb/mariadb.log. However, Debian/Ubuntu use /var/log/mysql/error.log directory.

***/var/log/mysqld.log **或**/var/log/mysql.log **：记录每个调试，失败和成功消息的mySQL日志文件，包括启动，停止，停止和重新启动mySQL守护程序mysqld 。 系统决定目录。 redhat，centos，fedora和其他基于Redhat的系统使用/var/log/mariadb/mariadb.log。 但是，debian/ubuntu使用/var/log/mysql/error.log目录。
* **/var/log/xferlog**: keeps FTP file transfer sessions. Includes info like file names and user-initiated FTP transfers.

***/var/log/xferlog **：保持FTP文件传输会话。 包括信息名称和用户启动的FTP传输之类的信息。* **/var/log/\*** : You should always check for unexpected logs in this directory

***/var/log/\ ***：您应始终在此目录中检查意外日志

{% hint style="info" %}

{％提示样式=“ info”％}
Linux system logs and audit subsystems may be disabled or deleted in an intrusion or malware incident. Because logs on Linux systems generally contain some of the most useful information about malicious activities, intruders routinely delete them. Therefore, when examining available log files, it is important to look for gaps or out of order entries that might be an indication of deletion or tampering.

Linux系统日志和审核子系统可以在入侵或恶意软件事件中被禁用或删除。 由于Linux系统上的日志通常包含有关恶意活动的一些最有用的信息，因此入侵者通常会删除它们。 因此，在检查可用的日志文件时，重要的是要查找差距或订单条目，这可能表明删除或篡改。
{% endhint %}

### Command History

###命令历史记录

Many Linux systems are configured to maintain a command history for each user account:

许多Linux系统被配置为维护每个用户帐户的命令历史记录：

* \~/.bash\_history

* \〜/.bash \ _历史
* \~/.history

* \〜/。历史
* \~/.sh\_history

* \〜/.sh \ _历史
* \~/.\*\_history

* \〜/。\* \ _历史记录

### Logins

Using the command `last -Faiwx` it's possible to get the list of users that have logged in.\

使用命令`last -faiwx`可以获取已登录的用户列表。
It is recommended to check if those logins make sense:

建议检查这些登录是否有意义：

* Any unknown user?

*任何未知用户？
* Any user that shouldn't have a shell logged in?

*任何不应该登录外壳的用户？

This is important as **attackers** some times may copy `/bin/bash` inside `/bin/false` so users like **lightdm** may be **able to login**.

这很重要，因为**攻击者**有时可能会复制`/bin/bash` in`/bin/false`''/bin/false`，因此像** lightdm **这样的用户可以**可以登录**。

Note that you can also **take a look at this information by reading the logs**.

请注意，您还可以通过阅读日志**来查看此信息。

### Application Traces

###应用程序跟踪

* **SSH**: Connections to systems made using SSH to and from a compromised system result in entries being made in files for each user account (_**∼/.ssh/authorized\_keys**_ and _**∼/.ssh/known\_keys**_). These entries can reveal the hostname or IP address of the remote hosts.

*** ssh **：使用SSH和从折衷的系统中制造的系统的连接导致每个用户帐户的文件中的条目（_ **〜/.ssh/授权\ _keys ** _和_ **〜 /.ssh/nown \ _keysdy_）。 这些条目可以揭示远程主机的主机名或IP地址。
* **Gnome Desktop**: User accounts may have a _**∼/.recently-used.xbel**_ file that contains information about files that were recently accessed using applications running on the Gnome desktop.

*** gnome桌面**：用户帐户可能具有_ **〜/。recustally.xbel ** _文件，其中包含有关使用GNOME桌面上运行的应用程序访问的有关文件的信息。
* **VIM**: User accounts may have a _**∼/.viminfo**_ file that contains details about the use of VIM, including search string history and paths to files that were opened using vim.

*** vim **：用户帐户可能具有_ **〜/.viminfo ** _文件，其中包含有关使用VIM的详细信息，包括搜索字符串历史记录和使用VIM打开的文件的路径。
* **Open Office**: Recent files.

***开放办公室**：最新文件。
* **MySQL**: User accounts may have a _**∼/.mysql\_history**_ file that contains queries executed using MySQL.

*** mysql **：用户帐户可能具有_ **〜/.mysql \ _HISTORY ** _文件，该文件包含使用mySQL执行的查询。
* **Less**: User accounts may have a _**∼/.lesshst**_ file that contains details about the use of less, including search string history and shell commands executed via less.

***少**：用户帐户可能具有_ **〜/.lesshst ** _文件，其中包含有关使用较少使用的详细信息，包括搜索字符串历史记录和通过LINS执行的shell命令。

### USB Logs

[**usbrip**](https://github.com/snovvcrash/usbrip) is a small piece of software written in pure Python 3 which parses Linux log files (`/var/log/syslog*` or `/var/log/messages*` depending on the distro) for constructing USB event history tables.

[** usbrip **]（https://github.com/snovvcrash/usbrip）是一小部分软件，用纯Python 3编写，该软件解析Linux linux log Files（`/var/var/log/syslog*`或 /日志/消息*`取决于构建USB事件历史记录表的发行版。

It is interesting to **know all the USBs that have been used** and it will be more useful if you have an authorized list of USBs to find "violation events" (the use of USBs that aren't inside that list).

**知道所有已使用的USB **很有趣，如果您有授权的USB列表来查找“违规事件”（使用不在该列表中的USB），则将更有用。

### Installation

＃＃＃ 安装

```
pip3 install usbrip
usbrip ids download #Download USB ID database
```

### Examples

```
usbrip events history #Get USB history of your curent linux machine
usbrip events history --pid 0002 --vid 0e0f --user kali #Search by pid OR vid OR user
#Search for vid and/or pid
usbrip ids download #Downlaod database
usbrip ids search --pid 0002 --vid 0e0f #Search for pid AND vid
```

More examples and info inside the github: [https://github.com/snovvcrash/usbrip](https://github.com/snovvcrash/usbrip)

GitHub内部的更多示例和信息：[https://github.com/snovvcrash/usbrip]（https://github.com/snovvcrash/usbrip）

{% hint style="danger" %}
![](<../../.gitbook/assets/image (9) (1).png>)

\
Use [**Trickest**](https://trickest.io/) to easily build and **automate workflows** powered by the world's **most advanced** community tools.\

使用[** trickest **]（https://trickest.io/）轻松构建和**自动化工作流**由世界的**最高级**社区工具提供动力。\ \
Get Access Today:

立即获取访问：

{% embed url="https://trickest.com/?utm_campaign=hacktrics&utm_medium=banner&utm_source=hacktricks" %}
{% endhint %}

## Review User Accounts and Logon Activities

##评论用户帐户和登录活动

Examine the _**/etc/passwd**_, _**/etc/shadow**_ and **security logs** for unusual names or accounts created and or used in close proximity to known unauthorized events. Also, check possible sudo brute-force attacks.\

检查_ **/etc/passwd ** _，_ **/etc/etc/shadow ** _ and **安全日志**是否为不寻常的名称或帐户和或在与已知未经授权的事件的近距离接近时创建和或使用。 另外，检查可能的sudo蛮力攻击。\ \
Moreover, check files like _**/etc/sudoers**_ and _**/etc/groups**_ for unexpected privileges given to users.\

此外，检查文件，例如_ **/etc/sudoers ** _和_ **/etc/groups ** _ _ _ _ _ _ _ _
Finally, look for accounts with **no passwords** or **easily guessed** passwords.

最后，查找没有密码**或**很容易猜到的**密码的帐户。

## Examine File System

File system data structures can provide substantial amounts of **information** related to a **malware** incident, including the **timing** of events and the actual **content** of **malware**.\

文件系统数据结构可以提供大量的**信息** **恶意软件**事件，包括事件的**时间和实际的**内容** **恶意软件**。
**Malware** is increasingly being designed to **thwart file system analysis**. Some malware alter date-time stamps on malicious files to make it more difficult to find them with timeline analysis. Other malicious codes are designed to only store certain information in memory to minimize the amount of data stored in the file system.\

**恶意软件**越来越多地被设计为**阻止文件系统分析**。 一些恶意软件更改恶意文件上的日期时间邮票，使得通过时间轴分析更难找到它们。 其他恶意代码旨在仅将某些信息存储在内存中，以最大程度地减少文件系统中存储的数据量。\ \
To deal with such anti-forensic techniques, it is necessary to pay **careful attention to timeline analysis** of file system date-time stamps and to files stored in common locations where malware might be found.

为了处理这种反法医技术，有必要仔细注意文件系统日期邮票的时间表分析**以及存储在可能会发现恶意软件的常见位置的文件。

* Using **autopsy** you can see the timeline of events that may be useful to discover suspicious activity. You can also use the `mactime` feature from **Sleuth Kit** directly.

*使用**尸检**您可以看到可能对发现可疑活动有用的事件的时间表。 您也可以直接使用**侦探套件**的“ mactime”功能。
* Check for **unexpected scripts** inside **$PATH** (maybe some sh or php scripts?)

*检查**意外脚本**内部** $ PATH **（也许是SH或PHP脚本？）
* Files in `/dev` used to be special files, you may find non-special files here related to malware.

*“/dev”中的文件曾经是特殊文件，您可能会在此处找到与恶意软件有关的非特殊文件。
* Look for unusual or **hidden files** and **directories**, such as “.. ” (dot dot space) or “..^G ” (dot dot control-G)

*寻找异常或**隐藏文件**和**目录**，例如“ ..”（点dot space）或“ ..^g”（dot dot control-g）
* Setuid copies of /bin/bash on the system `find / -user root -perm -04000 –print`

*系统上的 /bin /bash的setUID副本`find /-user root -perm -04000 –print`
* Review date-time stamps of deleted **inodes for large numbers of files being deleted around the same time**, which might indicate malicious activity such as the installation of a rootkit or trojanized service.

*查看已删除的日期时间邮票** inodes in Deledes大量文件大约在同一时间被删除**，这可能表明恶意活动，例如安装rootkit或trojanized服务。
* Because inodes are allocated on a next available basis, **malicious files placed on the system at around the same time may be assigned consecutive inodes**. Therefore, after one component of malware is located, it can be productive to inspect neighbouring inodes.

*由于下一个可用的inodes是在系统上分配的，因此可以在同一时间放置在系统上的恶意文件。 因此，在找到了一个恶意软件的一个组件之后，检查相邻的indodes可能是有效的。
* Also check directories like _/bin_ or _/sbin_ as the **modified and or changed time** of new or modified files may be interesting.

*还要查看_/bin_或_/sbin_之类的目录为**修改和/或更改的新文件或修改后的文件可能很有趣。
* It's interesting to see the files and folders of a directory **sorted by creation date** instead of alphabetically to see which files or folders are more recent (the last ones usually).

*有趣的是看到目录的文件和文件夹**按创建日期排序**，而不是字母顺序查看哪些文件或文件夹是最新的（通常是最后一个文件夹）。

You can check the most recent files of a folder using `ls -laR --sort=time /bin`\

您可以使用`ls -lar -sort = time /bin` \'\检查文件夹的最新文件
You can check the inodes of the files inside a folder using `ls -lai /bin |sort -n`

您可以使用“ ls -lai /bin | sort -n`”检查文件夹中文件的inodes

{% hint style="info" %}

{％提示样式=“ info”％}
Note that an **attacker** can **modify** the **time** to make **files appear** **legitimate**, but he **cannot** modify the **inode**. If you find that a **file** indicates that it was created and modified at the **same time** as the rest of the files in the same folder, but the **inode** is **unexpectedly bigger**, then the **timestamps of that file were modified**.

请注意，**攻击者**可以**修改** **时间**使**文件显示** **合法**，但他**无法**修改** inode **。 如果您发现一个**文件**表示与其他文件夹中的其余文件相同的时间进行了**，但** inode **是**出乎意料的** ** ，然后修改该文件的**时间戳**。
{% endhint %}

## Compare files of different filesystem versions

##比较不同文件系统版本的文件

#### Find added files

####查找添加的文件

```bash
git diff --no-index --diff-filter=A _openwrt1.extracted/squashfs-root/ _openwrt2.extracted/squashfs-root/
```

#### Find Modified content

####查找修改的内容

```bash
git diff --no-index --diff-filter=M _openwrt1.extracted/squashfs-root/ _openwrt2.extracted/squashfs-root/ | grep -E "^\+" | grep -v "Installed-Time"
```

#### Find deleted files

```bash
git diff --no-index --diff-filter=A _openwrt1.extracted/squashfs-root/ _openwrt2.extracted/squashfs-root/
```

#### Other filters

####其他过滤器

**`-diff-filter=[(A|C|D|M|R|T|U|X|B)…​[*]]`**

**`-diff-filter = [（A | C | D | M | r | T | U | X | B）…[*]]`**

Select only files that are Added (`A`), Copied (`C`), Deleted (`D`), Modified (`M`), Renamed (`R`), and have their type (i.e. regular file, symlink, submodule, …​) changed (`T`), are Unmerged (`U`), are Unknown (`X`), or have had their pairing Broken (`B`). Any combination of the filter characters (including none) can be used. When `*` (All-or-none) is added to the combination, all paths are selected if there is any file that matches other criteria in the comparison; if there is no file that matches other criteria, nothing is selected.

仅选择添加的文件（``a`），复制（`c'），已删除（`d`），修改（`m`），重命名（`r`），并具有类型（即常规文件，Symlink，symlink） ，subpodule，…）更改（`t`），未经合并（`u'），未知（`x`），或者将它们的配对损坏（`b`）。 滤波器字符（包括无）的任何组合都可以使用。 当``*`（全有或无人）添加到组合中时，如果有任何文件匹配比较中的其他标准，则选择所有路径； 如果没有与其他条件匹配的文件，则没有选择任何内容。

Also, **these upper-case letters can be downcased to exclude**. E.g. `--diff-filter=ad` excludes added and deleted paths.

另外，**这些上案字母可以被降低以排除**。 例如。 `-diff-filter = ad`排除添加和删除的路径。

Note that not all diffs can feature all types. For instance, diffs from the index to the working tree can never have Added entries (because the set of paths included in the diff is limited by what is in the index). Similarly, copied and renamed entries cannot appear if detection for those types is disabled.

请注意，并非所有差异都可以具有所有类型。 例如，从索引到工作树的差异永远无法添加条目（因为diff中包含的路径集受索引中的限制）。 同样，如果禁用了这些类型的检测，则无法出现复制和更名的条目。

## References

* [https://cdn.ttgtmedia.com/rms/security/Malware%20Forensics%20Field%20Guide%20for%20Linux%20Systems\_Ch3.pdf](https://cdn.ttgtmedia.com/rms/security/Malware%20Forensics%20Field%20Guide%20for%20Linux%20Systems\_Ch3.pdf)

* [https://cdn.ttgtmedia.com/rms/security/malware%20forensics%20Field%20Guide%20For%20linux%20linux%20Systemss \ _ch3.pdf]（ ％20Forensics％20 field％20指导％20 for％20linux％20Systems \ _ch3.pdf）
* [https://www.plesk.com/blog/featured/linux-logs-explained/](https://www.plesk.com/blog/featured/linux-logs-explained/)

<details>

<summary><strong>Support HackTricks and get benefits!</strong></summary>

<summary> <strong>支持hacktricks并获得好处！</strong> </summary>

Do you work in a **cybersecurity company**? Do you want to see your **company advertised in HackTricks**? or do you want to have access to the **latest version of the PEASS or download HackTricks in PDF**? Check the [**SUBSCRIPTION PLANS**](https://github.com/sponsors/carlospolop)!

您在**网络安全公司**工作吗？ 您是否想看到您的**公司在hacktricks **中刊登广告？ 还是您想访问**最新版本的豌豆或在pdf **中下载hacktricks？ 检查[**订阅计划**]（https://github.com/sponsors/carlospolop）！

- Discover [**The PEASS Family**](https://opensea.io/collection/the-peass-family), our collection of exclusive [**NFTs**](https://opensea.io/collection/the-peass-family)

 - 发现[**豌豆家庭**]（https://opensea.io/collection/the-peass-family），我们的独家[** nfts **]（https://opensea.io/collection） /家庭家庭）

- Get the [**official PEASS & HackTricks swag**](https://peass.creator-spring.com)

 - 获取[**官方豌豆和hacktricks赃物**]（https://peass.creator-spring.com）

- **Join the** [**💬**](https://emojipedia.org/speech-balloon/) [**Discord group**](https://discord.gg/hRep4RUj7f) or the [**telegram group**](https://t.me/peass) or **follow** me on **Twitter** [**🐦**](https://github.com/carlospolop/hacktricks/tree/7af18b62b3bdc423e11444677a6a73d4043511e9/\[https:/emojipedia.org/bird/README.md)[**@carlospolopm**](https://twitter.com/carlospolopm)**.**

 -  **加入** [**💬**]（https://emojipedia.org/speech-balloon/）[** discord group **]（https://discord.gg/hrep4ruj7f）或[ **电报组**]（https://t.me/peass）或**在** Twitter ** [**🐦**]（https://github.com/carloppolop/hacktrickss on ** twitter **） /ree/7af18b62b3bdc423e114444444677a6a73d4043511e9/ \ [https:/emojipedia.org/bird/bird/readme.md）eardme.md）eghterme.md）eghterme.md）eghterme.md）eghtemplopmbyth

**Share your hacking tricks by submitting PRs to the** [**hacktricks github repo**](https://github.com/carlospolop/hacktricks)**.**

**通过将PRS提交给** [** hacktricks github repo **]（https://github.com/carloppolop/hacktricks）**。

</details>

{% hint style="danger" %}
![](<../../.gitbook/assets/image (9) (1).png>)

\
Use [**Trickest**](https://trickest.com/?utm\_campaign=hacktrics\&utm\_medium=banner\&utm\_source=hacktricks) to easily build and **automate workflows** powered by the world's **most advanced** community tools.\

使用[** trickest **]（https://trickest.com/?utm \_campaign=hacktrics \ _utm \ _Medium = bannerver＆utm \ _source=hacktricks = hacktricks）轻松构建和**自动化工作流** **最先进的**社区工具。\
Get Access Today:

立即获取访问：

{% embed url="https://trickest.com/?utm_campaign=hacktrics&utm_medium=banner&utm_source=hacktricks" %}
{% endhint %}
