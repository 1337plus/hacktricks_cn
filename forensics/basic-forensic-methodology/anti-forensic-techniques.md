

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


# Timestamps

An attacker may be interested in **changing the timestamps of files** to avoid being detected.\

攻击者可能有兴趣**更改文件的时间戳**以避免被检测到。
It's possible to find the timestamps inside the MFT in attributes `$STANDARD_INFORMATION` __ and __ `$FILE_NAME`.

可以在属性`$ standard_information` __ and __ $ file_name`中找到MFT内的时间戳。

Both attributes have 4 timestamps: **Modification**, **access**, **creation**, and **MFT registry modification** (MACE or MACB).

这两个属性都有4个时间戳：**修改**，**访问**，**创建**和** MFT注册表修改**（MACE或MACB）。

**Windows explorer** and other tools show the information from **`$STANDARD_INFORMATION`**.

** Windows Explorer **和其他工具显示了** $ standard_information` **的信息。

## TimeStomp - Anti-forensic Tool

## TIMESTOMP-反法务工具

This tool **modifies** the timestamp information inside **`$STANDARD_INFORMATION`** **but** **not** the information inside **`$FILE_NAME`**. Therefore, it's possible to **identify** **suspicious** **activity**.

此工具**修改** **内部的时间戳信息** $ standard_information` ** ** **，但** **不** ** **内部的信息** $ file_name` **。 因此，可以**识别** **可疑** **活动**。

## Usnjrnl

The **USN Journal** (Update Sequence Number Journal), or Change Journal, is a feature of the Windows NT file system (NTFS) that **maintains a record of changes made to the volume**.\

** USN Journal **（更新序列编号期刊）或更改期刊是Windows NT文件系统（NTFS）的功能，该功能**保持了对卷**的更改记录。
It's possible to use the tool [**UsnJrnl2Csv**](https://github.com/jschicht/UsnJrnl2Csv) to search for modifications to this record.

可以使用工具[** usnjrnl2csv **]（https://github.com/jschicht/usnjrnl2csv）来搜索此记录的修改。

![](<../../.gitbook/assets/image (449).png>)

The previous image is the **output** shown by the **tool** where it can be observed that some **changes were performed** to the file.

上一个图像是**工具**显示的**输出**，可以观察到对文件执行了一些**。

## $LogFile

All metadata changes to a file system are logged to ensure the consistent recovery of critical file system structures after a system crash. This is called [write-ahead logging](https://en.wikipedia.org/wiki/Write-ahead\_logging).\

对文件系统的所有元数据更改均已记录，以确保系统崩溃后关键文件系统结构的一致恢复。 这称为[write-head Loggging]（https://en.wikipedia.org/wiki/write-write-ahead \ _logging）。
The logged metadata is stored in a file called “**$LogFile**”, which is found in a root directory of an NTFS file system.\

已记录的元数据存储在名为“ ** $ logfile **”的文件中，该文件位于NTFS文件系统的根目录中。\ \ \
It's possible to use tools like [LogFileParser](https://github.com/jschicht/LogFileParser) to parse this file and find changes.

可以使用[logfileparser]（https://github.com/jschicht/logfileparser）之类的工具来解析此文件并查找更改。

![](<../../.gitbook/assets/image (450).png>)

Again, in the output of the tool it's possible to see that **some changes were performed**.

同样，在工具的输出中，有可能看到**进行了一些更改**。

Using the same tool it's possible to identify to **which time the timestamps were modified**:

使用相同的工具，可以识别**修改时间戳**的时间**：

![](<../../.gitbook/assets/image (451).png>)

* CTIME: File's creation time

* ctime：文件的创建时间
* ATIME: File's modification time
* MTIME: File's MFT registry modification

* mtime：文件的MFT注册表修改
* RTIME: File's access time

* rtime：文件的访问时间

## `$STANDARD_INFORMATION` and `$FILE_NAME` comparison

##`$ standard_information`和`$ file_name`比较

Another way to identify suspicious modified files would be to compare the time on both attributes looking for **mismatches**.

识别可疑修改文件的另一种方法是将两个属性上的时间进行比较，以寻找**不匹配**。

## Nanoseconds

##纳秒

**NTFS** timestamps have a **precision** of **100 nanoseconds**. Then, finding files with timestamps like 2010-10-10 10:10:**00.000:0000 is very suspicious**.

** ntfs **时间戳具有**精度** ** 100纳秒**。 然后，查找具有2010-10-10等时间戳的文件10:10：** 00.000：0000非常可疑**。

## SetMace - Anti-forensic Tool

## setmace-反法务工具

This tool can modify both attributes `$STARNDAR_INFORMATION` and `$FILE_NAME`. However, from Windows Vista, it's necessary for a live OS to modify this information.

该工具可以修改两个属性`$ starndar_information`和$ file_name`。 但是，从Windows Vista来看，实时OS必须修改此信息。

# Data Hiding

NFTS uses a cluster and the minimum information size. That means that if a file occupies uses and cluster and a half, the **reminding half is never going to be used** until the file is deleted. Then, it's possible to **hide data in this slack space**.

NFTS使用群集和最小信息大小。 这意味着，如果文件占用使用和群集，则**提醒一半永远不会使用**，直到删除文件为止。 然后，可以**将数据隐藏在此松弛空间**中。

There are tools like slacker that allow hiding data in this "hidden" space. However, an analysis of the `$logfile` and `$usnjrnl` can show that some data was added:

有一些诸如Slacker之类的工具可以隐藏在此“隐藏”空间中的数据。 但是，对“ $ logFile”和`$ usnjrnl`的分析都可以表明添加了一些数据：

![](<../../.gitbook/assets/image (452).png>)

Then, it's possible to retrieve the slack space using tools like FTK Imager. Note that this kind of tool can save the content obfuscated or even encrypted.

然后，可以使用FTK Imager等工具来检索松弛空间。 请注意，这种工具可以保存混淆甚至加密的内容。

# UsbKill

This is a tool that will **turn off the computer if any change in the USB** ports is detected.\

这是一个工具，如果检测到USB **端口的任何更改，将**关闭计算机。\ \ \
A way to discover this would be to inspect the running processes and **review each python script running**.

一种发现这一点的方法是检查运行过程，并**查看每个运行的Python脚本**。

# Live Linux Distributions

These distros are **executed inside the RAM** memory. The only way to detect them is **in case the NTFS file-system is mounted with write permissions**. If it's mounted just with read permissions it won't be possible to detect the intrusion.

这些发行版在RAM **内存中执行。 检测它们的唯一方法是**如果NTFS文件系统使用写入权限**安装。 如果仅使用读取权限安装，则将无法检测到入侵。

# Secure Deletion

＃安全删除

[https://github.com/Claudio-C/awesome-data-sanitization](https://github.com/Claudio-C/awesome-data-sanitization)

# Windows Configuration

＃Windows配置

It's possible to disable several windows logging methods to make the forensics investigation much harder.

可以禁用几种Windows Logging方法，以使法医调查更加困难。

## Disable Timestamps - UserAssist

This is a registry key that maintains dates and hours when each executable was run by the user.

这是一个注册表密钥，该密码在用户运行每个可执行文件时保持日期和数小时。

Disabling UserAssist requires two steps:

禁用用户助手需要两个步骤：

1. Set two registry keys, `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Advanced\Start_TrackProgs` and `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Advanced\Start_TrackEnabled`, both to zero in order to signal that we want UserAssist disabled.

我们希望用户助手禁用。
2. Clear your registry subtrees that look like `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\UserAssist\<hash>`.

2.清除您的注册表子树，看起来像`hkey_current_user \ Software \ Microsoft \ Windows \ currentversion \ explorer \ userAssist \ userAssist \ <hash>`。

## Disable Timestamps - Prefetch

##禁用时间戳 - 预取

This will save information about the applications executed with the goal of improving the performance of the Windows system. However, this can also be useful for forensics practices.

这将节省有关执行应用程序的信息，以改善Windows系统的性能。 但是，这对于取证实践也可能很有用。

* Execute `regedit`
* Select the file path `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SessionManager\Memory Management\PrefetchParameters`

*选择文件路径`hkey_local_machine \ system \ currentcontrolset \ control \ sessionmanager \ memory Management \ PrefetchParameters`
* Right-click on both `EnablePrefetcher` and `EnableSuperfetch`

*右键单击`enablePrefetcher'和'enablesuperfetch'
* Select Modify on each of these to change the value from 1 (or 3) to 0

*选择对每个修改以将值从1（或3）更改为0
* Restart

## Disable Timestamps - Last Access Time

##禁用时间戳 - 上次访问时间
Whenever a folder is opened from an NTFS volume on a Windows NT server, the system takes the time to **update a timestamp field on each listed folder**, called the last access time. On a heavily used NTFS volume, this can affect performance.

每当从Windows NT服务器上的NTFS卷打开文件夹时，系统都会花费时间来**更新每个列出的文件夹上的时间戳字段**，称为最后一个访问时间。 在大量使用的NTFS卷上，这可能会影响性能。

1. Open the Registry Editor (Regedit.exe).

1.打开注册表编辑（regedit.exe）。
2. Browse to `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\FileSystem`.

2.浏览到`hkey_local_machine \ system \ currentcontrolset \ control \ filesystem`。
3. Look for `NtfsDisableLastAccessUpdate`. If it doesn’t exist, add this DWORD and set its value to 1, which will disable the process.

3.寻找`ntfsdisablelastaccessupdate`。 如果不存在，请添加此dword并将其值设置为1，这将禁用该过程。
4. Close the Registry Editor, and reboot the server.

4.关闭注册表编辑器，然后重新启动服务器。

## Delete USB History

##删除USB历史记录

All the **USB Device Entries** are stored in Windows Registry Under the **USBSTOR** registry key that contains sub keys which are created whenever you plug a USB Device into your PC or Laptop. You can find this key here H`KEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Enum\USBSTOR`. **Deleting this** you will delete the USB history.\

所有** USB设备条目**都存储在** usbstor **注册表密钥下的Windows注册表中，该密钥包含每当将USB设备插入PC或笔记本电脑时创建的子键。 您可以在此处找到此键h`key_local_machine \ system \ currentControlset \ enum \ usbstor`。 **删除此**您将删除USB历史记录。\
You may also use the tool [**USBDeview**](https://www.nirsoft.net/utils/usb\_devices\_view.html) to be sure you have deleted them (and to delete them).

您也可以使用工具[** usbdeview **]（https://www.nirsoft.net/utils/usb \_devices/_view.html）确保已删除它们（并删除它们）。

Another file that saves information about the USBs is the file `setupapi.dev.log` inside `C:\Windows\INF`. This should also be deleted.

保存有关USB的信息的另一个文件是`setUpapi.dev.log` insion c：\ windows \ inf` insed'setupapi.dev.log。 这也应删除。

## Disable Shadow Copies

##禁用影子副本

**List** shadow copies with `vssadmin list shadowstorage`\

**列表**带有`vssadmin list shadowstorage` \ shadow cops
**Delete** them running `vssadmin delete shadow`

You can also delete them via GUI following the steps proposed in [https://www.ubackup.com/windows-10/how-to-delete-shadow-copies-windows-10-5740.html](https://www.ubackup.com/windows-10/how-to-delete-shadow-copies-windows-10-5740.html)

您还可以按照GUI删除它们，按照[https://www.ubackup.com/windows-10/how-to-delete-hadow-copies-windows-windows-10-5740.html]（https：https://// www.ubackup.com/windows-10/how-to-delete-shadow-copies-windows-10-5740.html）

To disable shadow copies:

禁用影子副本：

1. Go to the Windows start button and type "services" into the text search box; open the Services program.

1.转到Windows启动按钮，然后在文本搜索框中键入“服务”； 打开服务程序。
2. Locate "Volume Shadow Copy" from the list, highlight it,  and then right-click > Properties.

2.从列表中找到“音量阴影复制”，突出显示，然后右键单击>属性。
3. From the "Startup type" drop-down menu, select Disabled, and then click Apply and OK.

3.从“启动类型”下拉菜单中，选择“禁用”，然后单击“应用”并确定。

![](<../../.gitbook/assets/image (453).png>)

It's also possible to modify the configuration of which files are going to be copied in the shadow copy in the registry `HKLM\SYSTEM\CurrentControlSet\Control\BackupRestore\FilesNotToSnapshot`

还可以修改要在注册表中的影子副本中复制哪些文件的配置。

## Overwrite deleted files

* You can use a **Windows tool**: `cipher /w:C` This will indicate cipher to remove any data from the available unused disk space inside the C drive.

*您可以使用** Windows工具**：`cipher /w：c`这将指示密码以从C驱动器内的可用未使用的磁盘空间中删除任何数据。
* You can also use tools like [**Eraser**](https://eraser.heidi.ie)

*您还可以使用[**橡皮擦**]（https://eraser.heidi.ie）之类的工具

## Delete Windows event logs

* Windows + R --> eventvwr.msc --> Expand "Windows Logs" --> Right click each category and select "Clear Log"

* Windows + R-> EventVwr.msc->展开“ Windows Logs”  - >右键单击每个类别，然后选择“清除日志”
* `for /F "tokens=*" %1 in ('wevtutil.exe el') DO wevtutil.exe cl "%1"`

*`for /f“ tokens =*”％1 in（'wevtutil.exe el'）do wevtutil.exe cl“％1”'
* `Get-EventLog -LogName * | ForEach { Clear-EventLog $_.Log }`

## Disable Windows event logs

##禁用Windows事件日志

* `reg add 'HKLM\SYSTEM\CurrentControlSet\Services\eventlog' /v Start /t REG_DWORD /d 4 /f`

*`'reg添加'hklm \ system \ currentcontrolset \ services \ eventlog' /v start /t reg_dword /d 4 /f`
* Inside the services section disable the service "Windows Event Log"

*在“服务”部分中禁用服务“ Windows Event Log”
* `WEvtUtil.exec clear-log` or `WEvtUtil.exe cl`

## Disable $UsnJrnl

* `fsutil usn deletejournal /d c:`


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


