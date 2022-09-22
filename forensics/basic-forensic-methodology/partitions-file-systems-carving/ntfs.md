# NTFS

## NTFS

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

## **NTFS**

**NTFS** (**New Technology File System**) is a proprietary journaling file system developed by Microsoft.

** ntfs **（**新技术文件系统**）是Microsoft开发的专有日记文件系统。

The cluster is the smallest unit of size in NTFS and the size of the cluster depends on the size of a partition.

群集是NTF中最小的大小的单位，簇的大小取决于分区的大小。

| Partition size           | Sectors per cluster | Cluster size |

| 分区尺寸| 每个集群的扇区| 群集大小|
| ------------------------ | ------------------- | ------------ |
| 512MB or less            | 1                   | 512 bytes    |

| 512MB或更少| 1 | 512字节|
| 513MB-1024MB (1GB)       | 2                   | 1KB          |
| 1025MB-2048MB (2GB)      | 4                   | 2KB          |
| 2049MB-4096MB (4GB)      | 8                   | 4KB          |
| 4097MB-8192MB (8GB)      | 16                  | 8KB          |
| 8193MB-16,384MB (16GB)   | 32                  | 16KB         |
| 16,385MB-32,768MB (32GB) | 64                  | 32KB         |
| Greater than 32,768MB    | 128                 | 64KB         |

| 大于32,768MB | 128 | 64KB |

### **Slack-Space**

### **松弛空间**

As the **smallest** size unit of NTFS is a **cluster**. Each file will be occupying several complete clusters. Then, it's highly probable that **each file occupies more space than necessary**. These **unused** **spaces** **booked** by a file which is called a **slacking** **space** and people could take advantage of this area to **hide** **information**.

由于**最小的**尺寸单位是**群集**。 每个文件将占据几个完整的群集。 然后，**每个文件都占用比必要的更多空间**。 这些**未使用的** **空间** **被称为**懈怠** **空间**的文件预订**，人们可以利用此区域来** hide ** **信息 **。

![](<../../../.gitbook/assets/image (498).png>)

### **NTFS boot sector**

### ** NTFS引导扇区**

When you format an NTFS volume, the format program allocates the first 16 sectors for the Boot metadata file. The first sector is a boot sector with a "bootstrap" code and the following 15 sectors are the boot sector's IPL (Initial Program Loader). To increase file system reliability the very last sector of an NTFS partition contains a spare copy of the boot sector.

当您格式化NTFS卷时，格式程序将为引导元数据文件分配前16个扇区。 第一个扇区是带有“ bootstrap”代码的引导扇区，以下15个扇区是引导扇区的IPL（初始程序加载程序）。 为了提高文件系统可靠性，NTFS分区的最后一个扇区包含引导部门的备用副本。

### **Master File Table (MFT)**

### **主文件表（MFT）**

The NTFS file system contains a file called the Master File Table (MFT). There is at least **one entry in the MFT for every file on an NTFS file system** volume, including the MFT itself. All information about a file, including its **size, time and date stamps, permissions, and data content**, is stored either in MFT entries or in space outside the MFT that is described by MFT entries.

NTFS文件系统包含一个称为主文件表（MFT）的文件。 NTFS文件系统上的每个文件中至少有一个条目**卷，包括MFT本身。 有关文件的所有信息，包括其**大小，时间和日期邮票，权限和数据内容**，都存储在MFT条目中，或在MFT内部通过MFT条目描述的MFT之外的空间中存储。

As **files are added** to an NTFS file system volume, more entries are added to the MFT and the **MFT increases in size**. When **files** are **deleted** from an NTFS file system volume, their **MFT entries are marked as free** and may be reused. However, disk space that has been allocated for these entries is not reallocated, and the size of the MFT does not decrease.

由于**将文件添加到NTFS文件系统卷中，因此将更多条目添加到MFT中，并且** mft的大小增加**。 当**文件**被**从NTFS文件系统卷中删除**时，它们的** mft条目被标记为免费**，并且可以重复使用。 但是，已分配给这些条目的磁盘空间并未重新分配，并且MFT的大小不会减小。

The NTFS file system **reserves space for the MFT to keep the MFT as contiguous as possible** as it grows. The space reserved by the NTFS file system for the MFT in each volume is called the **MFT zone**. Space for files and directories is also allocated from this space, but only after all of the volume space outside of the MFT zone has been allocated.

NTFS文件系统**保留MFT的空间，以使MFT尽可能连续**随着它的生长。 NTFS文件系统为每个卷中的MFT保留的空间称为** MFT区域**。 文件和目录的空间也从该空间分配，但是只有在分配了MFT区域以外的所有音量空间之后。

Depending on the average file size and other variables, **either the reserved MFT zone or the unreserved space on the disk may be allocated first as the disk fills to capacity**. Volumes with a small number of relatively large files will allocate the unreserved space first, while volumes with a large number of relatively small files allocate the MFT zone first. In either case, fragmentation of the MFT starts to take place when one region or the other becomes fully allocated. If the unreserved space is completely allocated, space for user files and directories will be allocated from the MFT zone. If the MFT zone is completely allocated, space for new MFT entries will be allocated from the unreserved space.

根据平均文件大小和其他变量，**保留的MFT区域或磁盘上未保留的空间可以首先分配，因为磁盘填充到容量**。 具有少数相对较大文件的卷将首先分配未保留的空间，而卷则首先分配了大量相对较小的文件。 无论哪种情况，当一个区域或另一个区域完全分配时，MFT的碎片开始发生。 如果未保留的空间已完全分配，则将从MFT区域分配用于用户文件和目录的空间。 如果MFT区域完全分配，将从未保留的空间中分配新的MFT条目的空间。

NTFS file systems also generate a **$MFTMirror**. This is a **copy** of the **first 4 entries** of the MFT: $MFT, $MFT Mirror, $Log, $Volume.

NTFS文件系统还生成A ** $ mftmirror **。 这是MFT的前4个条目**的**复制**：$ mft，$ mft mirror，$ log，$卷。

NTFS reserves the first 16 records of the table for special information:

NTFS保留表的前16个记录以获取特殊信息：

| System File           | File Name | MFT Record | Purpose of the File                                                                                                                                                                                                           |

| 系统文件| 文件名| MFT记录| 文件的目的|
| --------------------- | --------- | ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Master file table     | $Mft      | 0          | Contains one base file record for each file and folder on an NTFS volume. If the allocation information for a file or folder is too large to fit within a single record, other file records are allocated as well.            |

| 主文件表| $ mft | 0 | 在NTFS卷上包含每个文件的一个基本文件记录和文件夹。 如果文件或文件夹的分配信息太大而无法符合单个记录，则也分配了其他文件记录。 |
| Master file table 2   | $MftMirr  | 1          | A duplicate image of the first four records of the MFT. This file guarantees access to the MFT in case of a single-sector failure.                                                                                            |

| 主文件表2 | $ mftmirr | 1 | MFT的前四个记录的重复图像。 此文件可以保证在单扇区故障的情况下访问MFT。 |
| Log file              | $LogFile  | 2          | Contains a list of transaction steps used for NTFS recoverability. Log file size depends on the volume size and can be as large as 4 MB. It is used by Windows NT/2000 to restore consistency to NTFS after a system failure. |

| 日志文件| $ logfile | 2 | 包含用于NTFS可回收性的交易步骤列表。 日志文件大小取决于音量大小，并且可以大至4 MB。 Windows NT/2000使用它来恢复系统故障后与NTF的一致性。 |
| Volume                | $Volume   | 3          | Contains information about the volume, such as the volume label and the volume version.                                                                                                                                       |

| 音量| $音量| 3 | 包含有关卷的信息，例如卷标签和卷版。 |
| Attribute definitions | $AttrDef  | 4          | A table of attribute names, numbers, and descriptions.                                                                                                                                                                        |

| 属性定义| $ attrdef | 4 | 属性名称，数字和描述表。 |
| Root file name index  | $         | 5          | The root folder.                                                                                                                                                                                                              |

| 根文件名索引| $ | 5 | 根文件夹。 |
| Cluster bitmap        | $Bitmap   | 6          | A representation of the volume showing which clusters are in use.                                                                                                                                                             |

| 群集位图| $ bitmap | 6 | 表示使用了哪些簇的卷的表示。 |
| Boot sector           | $Boot     | 7          | Includes the BPB used to mount the volume and additional bootstrap loader code used if the volume is bootable.                                                                                                                |

| 引导部门| $ boot | 7 | 包括用于安装音量的BPB和如果卷为启动的其他Bootstrap加载程序代码。 |
| Bad cluster file      | $BadClus  | 8          | Contains bad clusters for the volume.                                                                                                                                                                                         |

| 坏集群文件| $ badclus | 8 | 包含该卷的不良簇。 |
| Security file         | $Secure   | 9          | Contains unique security descriptors for all files within a volume.                                                                                                                                                           |

| 安全文件| $安全| 9 | 包含卷中所有文件的唯一安全描述符。 |
| Upcase table          | $Upcase   | 10         | Converts lowercase characters to matching Unicode uppercase characters.                                                                                                                                                       |

| 上箱表| $ upcase | 10 | 将小写字符转换为匹配的Unicode大写字符。 |
| NTFS extension file   | $Extend   | 11         | Used for various optional extensions such as quotas, reparse point data, and object identifiers.                                                                                                                              |

| NTFS扩展文件| $扩展| 11 | 用于各种可选扩展名，例如配额，重新验证点数据和对象标识符。 |
|                       |           | 12-15      | Reserved for future use.                                                                                                                                                                                                      |

| | | 12-15 | 保留供将来使用。 |
| Quota management file | $Quota    | 24         | Contains user assigned quota limits on the volume space.                                                                                                                                                                      |

| 配额管理文件| $配额| 24 | 在卷空间中包含用户分配的配额限制。 |
| Object Id file        | $ObjId    | 25         | Contains file object IDs.                                                                                                                                                                                                     |

| 对象ID文件| $ objid | 25 | 包含文件对象ID。 |
| Reparse point file    | $Reparse  | 26         | This file contains information about files and folders on the volume including reparse point data.                                                                                                                            |

| 再生点文件| $ reparse | 26 | 该文件包含有关卷上的文件和文件夹的信息，包括重建点数据。 |

### Each entry of the MFT looks like the following:

### MFT的每个条目看起来如下：

![](<../../../.gitbook/assets/image (499).png>)

Note how each entry starts with "FILE". Each entry occupies 1024 bits. So after 1024 bit from the start of an MFT entry, you will find the next one.

注意每个条目如何以“文件”开头。 每个条目占1024位。 因此，从MFT入口开始1024位后，您将找到下一个。

Using the [**Active Disk Editor**](https://www.disk-editor.org/index.html) it's very easy to inspect the entry of a file in the MFT. Just right click on the file and then click "Inspect File Record"

使用[**活动磁盘编辑器**]（https://www.disk-editor.org/index.html）非常容易检查MFT中的文件输入。 只需右键单击文件，然后单击“检查文件记录”

![](<../../../.gitbook/assets/image (500).png>)

![](<../../../.gitbook/assets/image (501).png>)

Checking the **"In use**" flag it's very easy to know if a file was deleted (a value of **0x0 means deleted**).

检查**“使用**”标志，很容易知道是否已删除文件（** 0x0的值表示已删除**）。

![](<../../../.gitbook/assets/image (510).png>)

It's also possible to recover deleted files using FTKImager:

也可以使用ftkimager恢复已删除的文件：

![](<../../../.gitbook/assets/image (502).png>)

### MFT Attributes

### mft属性

Each MFT entry has several attributes as the following image indicates:

每个MFT条目都有几个属性，如以下图像所示：

![](<../../../.gitbook/assets/image (506).png>)

Each attribute indicates some entry information identified by the type:

每个属性指示该类型标识的一些条目信息：

| Type Identifier | Name                     | Description                                                                                                       |

| 类型标识符| 名称| 描述|
| --------------- | ------------------------ | ----------------------------------------------------------------------------------------------------------------- |
| 16              | $STANDARD\_INFORMATION   | General information, such as flags; the last accessed, written, and created times; and the owner and security ID. |

| 16 | $标准\ _信息| 一般信息，例如标志； 最后的访问，书面和创建时间； 以及所有者和安全ID。 |
| 32              | $ATTRIBUTE\_LIST         | List where other attributes for a file can be found.                                                              |

| 32 | $属性\ _list | 列出可以找到文件的其他属性。 |
| 48              | $FILE\_NAME              | File name, in Unicode, and the last accessed, written, and created times.                                         |

| 48 | $ file \ _name | 文件名，以Unicode以及最后的访问，编写和创建的时间。 |
| 64              | $VOLUME\_VERSION         | Volume information. Exists only in version 1.2 (Windows NT).                                                      |

| 64 | $卷\ _version | 卷信息。 仅存在于1.2版（Windows NT）中。 |
| 64              | $OBJECT\_ID              | A 16-byte unique identifier for the file or directory. Exists only in versions 3.0+ and after (Windows 2000+).    |

| 64 | $对象\ _id | 文件或目录的16字节唯一标识符。 仅在版本3.0+和之后存在（Windows 2000+）。 |
| 80              | $SECURITY\_ DESCRIPTOR   | The access control and security properties of the file.                                                           |

| 80 | $ Security \ _描述符| 文件的访问控制和安全属性。 |
| 96              | $VOLUME\_NAME            | Volume name.                                                                                                      |
| 112             | $VOLUME\_ INFORMATION    | File system version and other flags.                                                                              |

| 112 | $卷\ _信息| 文件系统版本和其他标志。 |
| 128             | $DATA                    | File contents.                                                                                                    |
| 144             | $INDEX\_ROOT             | Root node of an index tree.                                                                                       |

| 144 | $ index \ _root | 索引树的根节点。 |
| 160             | $INDEX\_ALLOCATION       | Nodes of an index tree rooted in $INDEX\_ROOT attribute.                                                          |

| 160 | $ index \ _ Allocation | 索引树的节点扎根于$ index \ _root属性。 |
| 176             | $BITMAP                  | A bitmap for the $MFT file and for indexes.                                                                       |

| 176 | $ bitmap | $ MFT文件和索引的位图。 |
| 192             | $SYMBOLIC\_LINK          | Soft link information. Exists only in version 1.2 (Windows NT).                                                   |

| 192 | $ Symbolic \ _link | 软链接信息。 仅存在于1.2版（Windows NT）中。 |
| 192             | $REPARSE\_POINT          | Contains data about a reparse point, which is used as a soft link in version 3.0+ (Windows 2000+).                |

| 192 | $ reparse \ _point | 包含有关复杂点的数据，该数据用作3.0+版本中的软链接（Windows 2000+）。 |
| 208             | $EA\_INFORMATION         | Used for backward compatibility with OS/2 applications (HPFS).                                                    |

| 208 | $ ea \ _信息| 用于与OS/2应用程序（HPFS）向后兼容。 |
| 224             | $EA                      | Used for backward compatibility with OS/2 applications (HPFS).                                                    |

| 224 | $ ea | 用于与OS/2应用程序（HPFS）向后兼容。 |
| 256             | $LOGGED\_UTILITY\_STREAM | Contains keys and information about encrypted attributes in version 3.0+ (Windows 2000+).                         |

| 256 | $记录\ _utility \ _stream | 在3.0+版本中包含有关加密属性的密钥和信息（Windows 2000+）。 |

For example the **type 48 (0x30)** identifies the **file name**:

例如，**类型48（0x30）**标识**文件名**：

![](<../../../.gitbook/assets/image (508).png>)

It is also useful to understand that **these attributes can be resident** (meaning, they exist within a given MFT record) or **nonresident** (meaning, they exist outside a given MFT record, elsewhere on the disk, and are simply referenced within the record). For example, if the attribute **$Data is resident**, this means that the **whole file is saved in the MFT**, if it's nonresident, then the content of the file is in another part of the file system.

也可以理解**这些属性可以是居民**（意味着它们存在于给定的MFT记录中）或**非居民**（这意味着它们存在于给定的MFT记录之外，在磁盘其他地方，并且 仅在记录中引用）。 例如，如果属性** $数据是居民**，则意味着**整个文件保存在mft **中，如果是居民，则文件的内容在文件系统的另一部分中。

Some interesting attributes:

一些有趣的属性：

* [$STANDARD\_INFORMATION](https://flatcap.org/linux-ntfs/ntfs/attributes/standard\_information.html) (among others):

* [$标准\ _information]（https://flatcap.org/linux-ntfs/ntfs/attributes/standard \ _information.html）（等）：
  * Creation date
  * Modification date
  * Access date
  * MFT update date
  * DOS File permissions
* [$FILE\_NAME](https://flatcap.org/linux-ntfs/ntfs/attributes/file\_name.html) (among others):

* [$ file \ _name]（https://flatcap.org/linux-ntfs/ntfs/attributes/file_name.html）（等）：
  * File name
  * Creation date

* 创建日期
  * Modification date
  * Access date
  * MFT update date
  * Allocated size

*分配的尺寸
  * Real size
  * [File reference](https://flatcap.org/linux-ntfs/ntfs/concepts/file\_reference.html) to the parent directory.

* [文件参考]（https://flatcap.org/linux-ntfs/ntfs/concepts/file_reference.html）到父级目录。
* [$Data](https://flatcap.org/linux-ntfs/ntfs/attributes/data.html) (among others):

* [$ data]（https://flatcap.org/linux-ntfs/ntfs/attributes/data.html）（等）：
  * Contains the file's data or the indication of the sectors where the data resides. In the following example, the attribute data is not resident so the attribute gives information about the sectors where the data resides.

*包含文件的数据或数据所在的扇区的指示。 在下面的示例中，属性数据不是居民，因此该属性提供了有关数据所在的扇区的信息。

![](<../../../.gitbook/assets/image (507) (1).png>)

![](<../../../.gitbook/assets/image (509).png>)

### NTFS timestamps

![](<../../../.gitbook/assets/image (512).png>)

Another useful tool to analyze the MFT is [**MFT2csv**](https://github.com/jschicht/Mft2Csv) (select the mft file or the image and press dump all and extract to extract all the objects).\

分析MFT的另一个有用工具是[** mft2csv **]（https://github.com/jschicht/mft2csv）（选择MFT文件或图像文件，然后按所有图像，然后按所有转储并提取所有对象）。
This program will extract all the MFT data and present it in CSV format. It can also be used to dump files.

该程序将提取所有MFT数据，并以CSV格式呈现它。 它也可以用于转储文件。

![](<../../../.gitbook/assets/image (513).png>)

### $LOGFILE

The file **`$LOGFILE`** contains **logs** about the **actions** that have been **performed** **to** **files**. It also **saves** the **action** it would need to perform in case of a **redo** and the action needed to **go back** to the **previous** **state**.\

文件** $ logFile` **包含** logs **关于** action **的** ** ** ** ** ** ** **文件**。 它还**保存** **操作**需要执行** redo **，并且需要**返回**到**前** **状态**所需的操作 。\
These logs are useful for the MFT to rebuild the file system in case some kind of error happened. The maximum size of this file is **65536KB**.

如果发生某种错误，这些日志对于MFT重建文件系统很有用。 该文件的最大尺寸为** 65536KB **。

To inspect the `$LOGFILE` you need to extract it and inspect the `$MFT` previously with [**MFT2csv**](https://github.com/jschicht/Mft2Csv).\

要检查“ $ logFile”，您需要提取它并以前使用[** mft2csv **]（https://github.com/jschicht/mft2csv）进行检查。
Then run [**LogFileParser**](https://github.com/jschicht/LogFileParser) against this file and select the exported `$LOGFILE` file and the CVS of the inspection of the `$MFT`. You will obtain a CSV file with the logs of the file system activity recorded by the `$LOGFILE` log.

然后对此文件运行[** logfileparser **]（https://github.com/jschicht/logfileparser），然后选择导出的`$ logfile`文件''和$ mft'的检查的CVS。 您将获得一个CSV文件，其中包含“ $ logFile”日志记录的文件系统活动的日志。

![](<../../../.gitbook/assets/image (515).png>)

Filtering by filenames you can see **all the actions performed against a file**:

通过文件名过滤您可以看到**所有针对文件执行的操作**：

![](<../../../.gitbook/assets/image (514).png>)

### $USNJnrl

The file `$EXTEND/$USNJnrl/$J` is an alternate data stream of the file `$EXTEND$USNJnrl`. This artifact contains a **registry of changes produced inside the NTFS volume with more detail than `$LOGFILE`**.

文件`$ extent/$ usnjnrl/$ j'是文件的替代数据流$扩展$ usnjnrl`。 该工件包含NTFS卷中产生的变化的注册表，其细节比“ $ logFile” **。

To inspect this file you can use the tool [**UsnJrnl2csv**](https://github.com/jschicht/UsnJrnl2Csv).

要检查此文件，您可以使用该工具[** usnjrnl2csv **]（https://github.com/jschicht/usnjrnl2csv）。

Filtering by the filename it's possible to see **all the actions performed against a file**. Also, you can find the `MFTReference` in the parent folder. Then looking at that `MFTReference` you can find **information from the parent folder.**

通过文件名过滤，可以看到**所有针对文件执行的操作**。 另外，您可以在父文件夹中找到“ mftreference”。 然后查看该“ mftreference”，您可以从父文件夹中找到**信息。**

![](<../../../.gitbook/assets/image (516).png>)

### $I30

Every **directory** in the file system contains an **`$I30`** **attribute** that must be maintained whenever there are changes to the directory's contents. When files or folders are removed from the directory, the **`$I30`** index records are re-arranged accordingly. However, **re-arranging of the index records may leave remnants of the deleted file/folder entry within the slack space**. This can be useful in forensics analysis for identifying files that may have existed on the drive.

文件系统中的每个**目录**都包含一个** $ i30` ** **属性**，只要目录的内容都有更改，就必须维护。 当文件或文件夹从目录中删除时，** $ i30` **索引记录将相应重新安排。 但是，**索引记录的重新安排可能会将已删除的文件/文件夹条目的残余物留在Slack Space **内。 这对于标识驱动器上可能存在的文件的取证分析可能很有用。

You can get the `$I30` file of a directory from the **FTK Imager** and inspect it with the tool [Indx2Csv](https://github.com/jschicht/Indx2Csv).

您可以从** ftk Imager **获取目录的“ $ i30”文件，然后使用工具[Indx2CSV]（https://github.com/jschichth/indx2csv）进行检查。

![](<../../../.gitbook/assets/image (519).png>)

With this data, you can find **information about the file changes performed inside the folder** but note that the deletion time of a file isn't saved inside this log. However, you can see that **last modified date** of the **`$I30` file**, and if the **last action performed** over the directory is the **deletion** of a file, the times may be the same.

使用此数据，您可以找到有关文件夹内执行的文件更改的信息**，但请注意，文件的删除时间并未保存在该日志中。 但是，您可以看到** $ i30`文件**的最后一个修改日期**，如果**执行的最后一个操作**在目录上执行**是文件的**删除**，则 时间可能相同。

### $Bitmap

The **`$BitMap`** is a special file within the NTFS file system. This file keeps **track of all of the used and unused clusters** on an NTFS volume. When a file takes up space on the NTFS volume the location used is marked out in the `$BitMap`.

** $ bitmap` **是NTFS文件系统中的特殊文件。 该文件可以在NTFS卷上保留所有已使用和未使用的群集**的**。 当文件占用NTFS卷上的空间时，使用的位置在“ $ bitmap”中标记了。

![](<../../../.gitbook/assets/image (523).png>)

### ADS (Alternate Data Stream)

Alternate data streams allow files to contain more than one stream of data. Every file has at least one data stream. In Windows, this default data stream is called `:$DATA`.\

备用数据流允许文件包含多个数据流。 每个文件至少都有一个数据流。 在Windows中，此默认数据流称为“：$ data”。\ \
In this [page you can see different ways to create/access/discover alternate data streams](../../../windows-hardening/basic-cmd-for-pentesters.md#alternate-data-streams-cheatsheet-ads-alternate-data-stream) from the console. In the past, this cause a vulnerability in IIS as people were able to access the source code of a page by accessing the `:$DATA` stream like `http://www.alternate-data-streams.com/default.asp::$DATA`.

在此[页面上，您可以看到创建/访问/发现替代数据流的不同方法]（../../../ Windows-hardening/basic-cmd-for-penters.md＃ntures＃替代data-streams-cheatsheetsheet -ADS-ADS-Alternate-Data-stream）来自控制台。 过去，由于人们能够访问`：$ data流（如http://www.alternate-data-streams.com/default.asp）访问`：$ data流来访问页面的源代码的漏洞。 :: $ data`。

Using the tool [**AlternateStreamView**](https://www.nirsoft.net/utils/alternate\_data\_streams.html) you can search and export all the files with some ADS.

使用工具[** externAteStreamView **]（https://www.nirsoft.net/utils/alternate/alternate \ _data \ _Streams.html）您可以使用一些广告搜索和导出所有文件。

![](<../../../.gitbook/assets/image (518).png>)

Using the FTK imager and double clicking on a file with ADS you can **access the ADS data**:

使用FTK成像器并双击带有广告的文件，您可以**访问广告数据**：

![](<../../../.gitbook/assets/image (517).png>)

If you find an ADS called **`Zone.Identifier`** (see the above image), this usually contains **information about how the file was downloaded**. There would be a "ZoneId" field with the following info:

如果您找到一个称为**'Zone.Identifier` **的广告（请参见上图），则通常包含有关如何下载文件**的**信息。 将有一个“区域性”字段，其中包含以下信息：

* Zone ID = 0 -> Mycomputer

*区域ID = 0-> myComputer
* Zone ID = 1 -> Intranet
* Zone ID = 2 -> Trusted

*区域ID = 2->信任
* Zone ID = 3 -> Internet
* Zone ID = 4 -> Untrusted

*区域ID = 4->不信任

Moreover, different software may store additional information:

此外，不同的软件可能会存储其他信息：

| Software                                                            | Info                                                                         |

| 软件| 信息|
| ------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| Google Chrome, Opera, Vivaldi,                                      | ZoneId=3, ReferrerUrl, HostUrl                                               |
| Microsoft Edge                                                      | ZoneId=3, LastWriterPackageFamilyName=Microsoft.MicrosoftEdge\_8wekyb3d8bbwe |

| Microsoft Edge | diessID = 3，lastwriterpackagefamilyname = microsoft.microsoftedge \ _8wekyb3d8bbwe |
| Firefox, Tor browser, Outlook2016, Thunderbird, Windows Mail, Skype | ZoneId=3                                                                     |

| Firefox，Tor浏览器，Outlook2016，Thunderbird，Windows Mail，Skype | 区域= 3 |
| μTorrent                                                            | ZoneId=3, HostUrl=about:internet                                             |

| μtorrent| Zoneid = 3，Hosturl =大约：Internet |

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
