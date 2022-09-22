

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


# Ext - Extended Filesystem

**Ext2** is the most common filesystem for **not journaling** partitions (**partitions that don't change much**) like the boot partition. **Ext3/4** are **journaling** and are used usually for the **rest partitions**.

** ext2 **是**不记录的最常见的文件系统**分区（**分区不会更改太多**），例如启动分区。 ** ext3/4 **是**日记**，通常用于**休息分区**。

All block groups in the filesystem have the same size and are stored sequentially. This allows the kernel to easily derive the location of a block group in a disk from its integer index.

文件系统中的所有块组具有相同的大小，并且依次存储。 这使得内核可以轻松地从其整数索引中得出磁盘组中块组的位置。

Every block group contains the following pieces of information:

每个块组都包含以下信息：

* A copy of the filesystem’s superblock

*文件系统超级封锁的副本
* A copy of the block group descriptors

*块组描述符的副本
* A data block bitmap which is used to identify the free blocks inside the group

*用于识别组内的自由块的数据块位图
* An inode bitmap, which is used to identify the free inodes inside the group

* inode位图，用于识别组内的免费inodes
* inode table: it consists of a series of consecutive blocks, each of which contains a predefined Figure 1 Ext2 inode number of inodes. All inodes have the same size: 128 bytes. A 1,024 byte block contains 8 inodes, while a 4,096-byte block contains 32 inodes. Note that in Ext2, there is no need to store on disk a mapping between an inode number and the corresponding block number because the latter value can be derived from the block group number and the relative position inside the inode table. For example, suppose that each block group contains 4,096 inodes and that we want to know the address on the disk of inode 13,021. In this case, the inode belongs to the third block group and its disk address is stored in the 733rd entry of the corresponding inode table. As you can see, the inode number is just a key used by the Ext2 routines to retrieve the proper inode descriptor on the disk quickly

* inode表：它由一系列连续块组成，每个块包含一个预定义的图1 ext2 inode inode的Inode数量。 所有Inodes的大小相同：128字节。 1,024个字节块包含8个inodes，而4,096字节块包含32个inodes。 请注意，在Ext2中，无需在磁盘上存储一个inode号码和相应块号之间的映射，因为后一个值可以从块组号和Inode表中的相对位置得出。 例如，假设每个块组包含4,096个inodes，并且我们想知道Inode 13,021磁盘上的地址。 在这种情况下，Inode属于第三个块组，其磁盘地址存储在相应的Inode表的第733个条目中。 如您所见，Inode编号只是Ext2例程使用的键，以快速检索磁盘上的适当描述符
* data blocks, containing files. Any block which does not contain any meaningful information is said to be free.

*数据块，包含文件。 任何不包含任何有意义信息的块都是免费的。

![](<../../../.gitbook/assets/image (406).png>)

## Ext Optional Features

## Ext可选功能

**Features affect where** the data is located, **how** the data is stored in inodes and some of them might supply **additional metadata** for analysis, therefore features are important in Ext.

**功能会影响数据所在的位置，** **数据如何存储在inodes中，其中一些数据可能会提供**附加的元数据**进行分析，因此功能在EXT中很重要。

Ext has optional features that your OS may or may not support, there are 3 possibilities:

EXT具有您的操作系统可能支持或不支持的可选功能，有3种可能性：

* Compatible
* Incompatible
* Compatible Read Only: It can be mounted but not for writing

*仅兼容读取：可以安装，但不能以写作

If there are **incompatible** features you won't be able to mount the filesystem as the OS won't know how the access the data.

如果存在**不兼容的**功能，您将无法安装文件系统，因为操作系统将不知道如何访问数据。

{% hint style="info" %}

{％提示样式=“ info”％}
A suspected attacker might have non-standard extensions

可疑的攻击者可能具有非标准扩展
{% endhint %}

**Any utility** that reads the **superblock** will be able to indicate the **features** of an **Ext filesystem**, but you could also use `file -sL /dev/sd*`

**任何读取** superblock **的实用程序**将能够指示** ext filesystem **的**功能**，但您也可以使用`file -sl /dev /sd*````

## Superblock

The superblock is the first 1024 bytes from the start and it's repeated in the first block of each group and contains:

超级块是从一开始的第一个1024字节，它在每个组的第一个块中重复，并包含：

* Block size
* Total blocks
* Blocks per block group

*每个块组块
* Reserved blocks before the first block group

*在第一个块组之前保留块
* Total inodes
* Inodes per block group

* inodes每个块组
* Volume name
* Last write time

*最后写时间
* Last mount time

*最后一次安装时间
* Path where the file system was last mounted

*文件系统最后安装的路径
* Filesystem status (clean?)

*文件系统状态（清洁？）

It's possible to obtain this information from an Ext filesystem file using:

可以使用以下方式从Ext文件系统文件中获取此信息

```bash
fsstat -o <offsetstart> /pat/to/filesystem-file.ext
#You can get the <offsetstart> with the "p" command inside fdisk
```

You can also use the free GUI application: [https://www.disk-editor.org/index.html](https://www.disk-editor.org/index.html)\

您也可以使用免费的GUI应用程序：[https://www.disk-editor.org/index.html]（https://www.disk-editor.org/index.html）\
Or you can also use **python** to obtain the superblock information: [https://pypi.org/project/superblock/](https://pypi.org/project/superblock/)

或者，您也可以使用** python **获取超屏幕信息：[https://pypi.org/project/project/superblock/]（https://pypi.org/project/project/superblock/

## inodes

The **inodes** contain the list of **blocks** that **contains** the actual **data** of a **file**.\

** inodes **包含**块**的列表，**包含** ** a ** file **的实际** data **。
If the file is big, and inode **may contain pointers** to **other inodes** that point to the blocks/more inodes containing the file data.

如果文件很大，并且Inode **可能包含** **对其他inodes **的指示，则指向包含文件数据的块/更多inodes。

![](<../../../.gitbook/assets/image (416).png>)

In **Ext2** and **Ext3** inodes are of size **128B**, **Ext4** currently uses **156B** but allocates **256B** on disk to allow a future expansion.

在** ext2 **和** ext3 ** inodes的大小** 128b **，** ext4 **当前使用** 156b **，但在磁盘上分配** 256b **，以允许将来扩展。

Inode structure:

| Offset | Size | Name              | DescriptionF                                     |
| ------ | ---- | ----------------- | ------------------------------------------------ |
| 0x0    | 2    | File Mode         | File mode and type                               |
| 0x2    | 2    | UID               | Lower 16 bits of owner ID                        |

| 0x2 | 2 | uid | 较低的16位所有者ID |
| 0x4    | 4    | Size Il           | Lower 32 bits of file size                       |

| 0x4 | 4 | 大小IL | 较低的32位文件大小|
| 0x8    | 4    | Atime             | Access time in seconds since epoch               |

| 0x8 | 4 | 当地| 自时代以来的访问时间|
| 0xC    | 4    | Ctime             | Change time in seconds since epoch               |

| 0xc | 4 | CTIME | 自时代以来，在几秒钟内更改时间|
| 0x10   | 4    | Mtime             | Modify time in seconds since epoch               |

| 0x10 | 4 | mtime | 自时代以来，在几秒钟内修改时间|
| 0x14   | 4    | Dtime             | Delete time in seconds since epoch               |

| 0x14 | 4 | dtime | 自时代以来，删除时间|
| 0x18   | 2    | GID               | Lower 16 bits of group ID                        |

| 0x18 | 2 | gid | 较低的16位组ID |
| 0x1A   | 2    | Hlink count       | Hard link count                                  |

| 0x1a | 2 | hlink计数| 硬链接计数|
| 0xC    | 4    | Blocks Io         | Lower 32 bits of block count                     |

| 0xc | 4 | 块IO | 较低的32位块计数|
| 0x20   | 4    | Flags             | Flags                                            |
| 0x24   | 4    | Union osd1        | Linux: I version                                 |
| 0x28   | 69   | Block\[15]        | 15 points to data block                         |

| 0x28 | 69 | \ [15] | 数据块15分|
| 0x64   | 4    | Version           | File version for NFS                             |
| 0x68   | 4    | File ACL low      | Lower 32 bits of extended attributes (ACL, etc)  |

| 0x68 | 4 | 文件ACL低| 较低的32位扩展属性（ACL等）|
| 0x6C   | 4    | File size hi      | Upper 32 bits of file size (ext4 only)           |

| 0x6c | 4 | 文件大小hi | 上部32位文件大小（仅EXT4）|
| 0x70   | 4    | Obsolete fragment | An obsoleted fragment address                    |
| 0x74   | 12   | Osd 2             | Second operating system dependent union          |

| 0x74 | 12 | OSD 2 | 第二操作系统依赖联盟|
| 0x74   | 2    | Blocks hi         | Upper 16 bits of block count                     |

| 0x74 | 2 | 块hi | 高16位块计数|
| 0x76   | 2    | File ACL hi       | Upper 16 bits of extended attributes (ACL, etc.) |

| 0x76 | 2 | 文件ACL HI | 上16位扩展属性（ACL等）|
| 0x78   | 2    | UID hi            | Upper 16 bits of owner ID                        |

| 0x78 | 2 | uid hi | 上16位所有者ID |
| 0x7A   | 2    | GID hi            | Upper 16 bits of group ID                        |

| 0x7a | 2 | gid hi | 上16位组ID |
| 0x7C   | 2    | Checksum Io       | Lower 16 bits of inode checksum                  |

| 0x7c | 2 | 校验和 较低的16位Inode校验和

"Modify" is the timestamp of the last time the file's _content_ has been modified. This is often called "_mtime_".\

“修改”是该文件的_content_上一次修改的时间戳。 这通常称为“ _mtime _”。\ \
"Change" is the timestamp of the last time the file's _inode_ has been changed, like by changing permissions, ownership, file name, and the number of hard links. It's often called "_ctime_".

“更改”是最后一次更改文件_INODE_的时间戳，例如通过更改权限，所有权，文件名和硬链接数来更改。 通常称为“ _ctime_”。

Inode structure extended (Ext4):

| Offset | Size | Name         | Description                                 |
| ------ | ---- | ------------ | ------------------------------------------- |
| 0x80   | 2    | Extra size   | How many bytes beyond standard 128 are used |

| 0x80 | 2 | 额外的尺寸| 使用了标准128以外的多少个字节|
| 0x82   | 2    | Checksum hi  | Upper 16 bits of inode checksum             |

| 0x82 | 2 | 校验和hi | 高16位Inode校验和
| 0x84   | 4    | Ctime extra  | Change time extra bits                      |
| 0x88   | 4    | Mtime extra  | Modify time extra bits                      |
| 0x8C   | 4    | Atime extra  | Access time extra bits                      |
| 0x90   | 4    | Crtime       | File create time (seconds since epoch)      |
| 0x94   | 4    | Crtime extra | File create time extra bits                 |
| 0x98   | 4    | Version hi   | Upper 32 bits of version                    |

| 0x98 | 4 | 版本hi | 上32位版本|
| 0x9C   |      | Unused       | Reserved space for future expansions        |

| 0x9c | | 未使用| 保留未来扩展的空间|

Special inodes:

| Inode | Special Purpose                                      |
| ----- | ---------------------------------------------------- |
| 0     | No such inode, numberings starts at 1                |

| 0 | 没有这样的inode，编号从1 |开始。
| 1     | Defective block list                                 |

| 1 | 有缺陷的块列表|
| 2     | Root directory                                       |

| 2 | 根目录|
| 3     | User quotas                                          |
| 4     | Group quotas                                         |
| 5     | Boot loader                                          |

| 5 | 引导加载程序|
| 6     | Undelete directory                                   |

| 6 | Undelete目录|
| 7     | Reserved group descriptors (for resizing filesystem) |

| 7 | 保留的组描述符（用于调整文件系统）|
| 8     | Journal                                              |

| 8 | 日记|
| 9     | Exclude inode (for snapshots)                        |

| 9 | 排除Inode（用于快照）|
| 10    | Replica inode                                        |
| 11    | First non-reserved inode (often lost + found)        |

| 11 | 第一个不保留的Inode（通常丢失 +发现）|

{% hint style="info" %}

{％提示样式=“ info”％}
Not that the creation time only appears in Ext4.

并不是说创建时间仅出现在EXT4中。
{% endhint %}

By knowing the inode number you can easily find its index:

通过了解Inode号码，您可以轻松找到其索引：

* **Block group** where an inode belongs: (Inode number - 1) / (Inodes per group)

***块组** inode属于：（ inode编号-1） /（每组inodes）
* **Index inside it's group**: (Inode number - 1) mod(Inodes/groups)

***索引内部的组** ：（ inode编号-1）mod（inodes/groups）
* **Offset** into **inode table**: Inode number \* (Inode size)

***偏移**进入** inode table **：inode number \*（inode size）
* The "-1" is because the inode 0 is undefined (not used)

*“ -1”是因为Inode 0未定义（未使用）

```bash
ls -ali /bin | sort -n #Get all inode numbers and sort by them
stat /bin/ls #Get the inode information of a file
istat -o <start offset> /path/to/image.ext 657103 #Get information of that inode inside the given ext file
icat -o <start offset> /path/to/image.ext 657103 #Cat the file
```

File Mode

| Number | Description                                                                                         |

| 数字| 描述|
| ------ | --------------------------------------------------------------------------------------------------- |
| **15** | **Reg/Slink-13/Socket-14**                                                                          |
| **14** | **Directory/Block Bit 13**                                                                          |

| ** 14 ** | **目录/块位13 ** |
| **13** | **Char Device/Block Bit 14**                                                                        |

| ** 13 ** | ** char设备/块位14 ** |
| **12** | **FIFO**                                                                                            |
| 11     | Set UID                                                                                             |
| 10     | Set GID                                                                                             |
| 9      | Sticky Bit (without it, anyone with Write & exec perms on a directory can delete and rename files)  |

| 9 | 粘性位（没有它，目录上有Witter＆Exec的任何人都可以删除并重命名文件）|
| 8      | Owner Read                                                                                          |
| 7      | Owner Write                                                                                         |
| 6      | Owner Exec                                                                                          |
| 5      | Group Read                                                                                          |

| 5 | 小组阅读|
| 4      | Group Write                                                                                         |

| 4 | 小组写作|
| 3      | Group Exec                                                                                          |
| 2      | Others Read                                                                                         |

| 2 | 其他人阅读|
| 1      | Others Write                                                                                        |

| 1 | 其他人写|
| 0      | Others Exec                                                                                         |

| 0 | 其他执行|

The bold bits (12, 13, 14, 15) indicate the type of file the file is (a directory, socket...) only one of the options in bold may exit.

粗体位（12、13、14、15）指示文件的类型是（目录，套接字...）仅BOLD中的一个选项可能会退出。

Directories

目录

| Offset | Size | Name      | Description                                                                                                                                                  |
| ------ | ---- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 0x0    | 4    | Inode     |                                                                                                                                                              |
| 0x4    | 2    | Rec len   | Record length                                                                                                                                                |

| 0x4 | 2 | rec len | 记录长度|
| 0x6    | 1    | Name len  | Name length                                                                                                                                                  |
| 0x7    | 1    | File type | <p>0x00 Unknown<br>0x01 Regular</p><p>0x02 Director</p><p>0x03 Char device</p><p>0x04 Block device</p><p>0x05 FIFO</p><p>0x06 Socket</p><p>0x07 Sym link</p> |

| 0x7 | 1 | 文件类型| <p> 0x00未知<br> 0x01常规</p> <p> 0x02导演</p> <p> 0x03 char设备</p> <p> 0x04块设备</p> <p> 0x05 fifo </fifo </ p> <p> 0x06插座</p> <p> 0x07 sym link </p> |
| 0x8    |      | Name      | Name string (up to 255 characters)                                                                                                                           |

| 0x8 | | 名称| 名称字符串（最多255个字符）|

**To increase the performance, Root hash Directory blocks may be used.**

**为了提高性能，可以使用根哈希目录块。**

**Extended Attributes**

**扩展属性**

Can be stored in

可以存储在

* Extra space between inodes (256 - inode size, usually = 100)

* Inodes之间的额外空间（256 -Inode大小，通常= 100）
* A data block pointed to by file\_acl in inode

* inode中的文件\ _acl指向的数据块

Can be used to store anything as a users attribute if the name starts with "user". So data can be hidden this way.

如果名称以“用户”开头，则可以用来存储任何东西作为用户属性。 因此可以以这种方式隐藏数据。

Extended Attributes Entries

扩展属性条目

| Offset | Size | Name         | Description                                                                                                                                                                                                        |
| ------ | ---- | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 0x0    | 1    | Name len     | Length of attribute name                                                                                                                                                                                           |

| 0x0 | 1 | 名称len | 属性名称的长度|
| 0x1    | 1    | Name index   | <p>0x0 = no prefix</p><p>0x1 = user. Prefix</p><p>0x2 = system.posix_acl_access</p><p>0x3 = system.posix_acl_default</p><p>0x4 = trusted.</p><p>0x6 = security.</p><p>0x7 = system.</p><p>0x8 = system.richacl</p> |

| 0x1 | 1 | 名称索引| <p> 0x0 =无前缀</p> <p> 0x1 =用户。 prefix </p> <p> 0x2 = system.posix_acl_access </p> <p> 0x3 = 0x3 = system.posix_acl_default </p> <p> <p> 0x4 = trusted。 > <p> 0x7 =系统。</p> <p> 0x8 = system.richacl </p> |
| 0x2    | 2    | Value offs   | Offset from first inode entry or start of block                                                                                                                                                                    |

| 0x2 | 2 | 价值折扣| 从第一个Inode输入或块开始偏移|
| 0x4    | 4    | Value blocks | Disk block where value stored or zero for this block                                                                                                                                                               |

| 0x4 | 4 | 值块| 磁盘块中存储的值或为零的磁盘|
| 0x8    | 4    | Value size   | Length of value                                                                                                                                                                                                    |

| 0x8 | 4 | 价值大小| 价值长度|
| 0xC    | 4    | Hash         | Hash for attribs in block or zero if in inode                                                                                                                                                                      |

| 0xc | 4 | 哈希| 如果在Inode中，则在块中或零中的属性hash |
| 0x10   |      | Name         | Attribute name w/o trailing NULL                                                                                                                                                                                   |

| 0x10 | | 名称| 属性名称w/o taxt null |

```bash
setfattr -n 'user.secret' -v 'This is a secret' file.txt #Save a secret using extended attributes
getfattr file.txt #Get extended attribute names of a file
getdattr -n 'user.secret' file.txt #Get extended attribute called "user.secret"
```

## Filesystem View

To see the contents of the file system, you can **use the free tool**: [https://www.disk-editor.org/index.html](https://www.disk-editor.org/index.html)\

要查看文件系统的内容，您可以**使用免费工具**：[https://www.disk-editor.org/index.html]（https://www.disk-editor.org/ index.html）\
Or you can mount it in your linux using `mount` command.

或者，您可以使用“ Mount”命令将其安装在Linux中。

[https://piazza.com/class\_profile/get\_resource/il71xfllx3l16f/inz4wsb2m0w2oz#:\~:text=The%20Ext2%20file%20system%20divides,lower%20average%20disk%20seek%20time.](https://piazza.com/class\_profile/get\_resource/il71xfllx3l16f/inz4wsb2m0w2oz#:\~:text=The%20Ext2%20file%20system%20divides,lower%20average%20disk%20seek%20time.)

[https://piazza.com/class \ _profile/get \_Resource/il71xfllx3l16f/inz4wsb2m0w2oz#: \ ~~: Text = the%20Ext2%20File%20File%20System； ：//piazza.com/class \ _profile/get \ _Resource/iL71xfllx3l16f/inz4wsb2m0w2oz＃：\〜：text = text = text = the％20ext2％20file％20system％20system％20divides，降低％20Averical％20Averenage％20Averenage％20Disk％20DESEEK％20Seek％20Time 20time 20time。）。


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


