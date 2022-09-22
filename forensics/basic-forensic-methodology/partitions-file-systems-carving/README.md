# Partitions/File Systems/Carving

＃分区/文件系统/雕刻

## Partitions/File Systems/Carving

##分区/文件系统/雕刻

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

## Partitions

A hard drive or an **SSD disk can contain different partitions** with the goal of separating data physically.\

硬盘驱动器或** SSD磁盘可以包含不同的分区**，其目标是将数据分开。
The **minimum** unit of a disk is the **sector** (normally composed of 512B). So, each partition size needs to be multiple of that size.

磁盘的**最小单位是**扇区**（通常由512b组成）。 因此，每个分区大小都必须是该大小的倍数。

### MBR (master Boot Record)

### MBR（主启动记录）

It's allocated in the **first sector of the disk after the 446B of the boot code**. This sector is essential to indicate to the PC what and from where a partition should be mounted.\

在引导代码的446b **的446b之后，它在磁盘的**第一扇区中分配。 该扇区对于向PC表示什么以及应安装分区的位置至关重要。\ \
It allows up to **4 partitions** (at most **just 1** can be active/**bootable**). However, if you need more partitions you can use **extended partitions**. The **final byte** of this first sector is the boot record signature **0x55AA**. Only one partition can be marked as active.\

它最多可以** 4个分区**（最多只能** 1 **可以是活动/**可启动**）。 但是，如果您需要更多的分区，则可以使用**扩展分区**。 该第一扇区的最终字节**是引导记录签名** 0x55AA **。 只有一个分区可以标记为活动。\ \
MBR allows **max 2.2TB**.

MBR允许**最大2.2TB **。

![](<../../../.gitbook/assets/image (489).png>)

![](<../../../.gitbook/assets/image (490).png>)

From the **bytes 440 to the 443** of the MBR you can find the **Windows Disk Signature** (if Windows is used). The logical drive letter of the hard disk depends on the Windows Disk Signature. Changing this signature could prevent Windows from booting (tool: [**Active Disk Editor**](https://www.disk-editor.org/index.html)**)**.

从**字节440到MBR的443 **，您可以找到** Windows磁盘签名**（如果使用Windows）。 硬盘的逻辑驱动字母取决于Windows磁盘签名。 更改此签名可以防止Windows引导（工具：[**活动磁盘编辑器**]（https://www.disk-editor.org/index.html）**）**。

![](<../../../.gitbook/assets/image (493).png>)

**Format**

**格式**

| Offset      | Length     | Item                |

| 偏移| 长度| 项目|
| ----------- | ---------- | ------------------- |
| 0 (0x00)    | 446(0x1BE) | Boot code           |
| 446 (0x1BE) | 16 (0x10)  | First Partition     |

| 446（0x1be）| 16（0x10）| 第一分区|
| 462 (0x1CE) | 16 (0x10)  | Second Partition    |

| 462（0x1CE）| 16（0x10）| 第二个分区|
| 478 (0x1DE) | 16 (0x10)  | Third Partition     |

| 478（0x1de）| 16（0x10）| 第三分区|
| 494 (0x1EE) | 16 (0x10)  | Fourth Partition    |

| 494（0x1EE）| 16（0x10）| 第四个分区|
| 510 (0x1FE) | 2 (0x2)    | Signature 0x55 0xAA |

**Partition Record Format**

**分区记录格式**

| Offset    | Length   | Item                                                   |

| 偏移| 长度| 项目|
| --------- | -------- | ------------------------------------------------------ |
| 0 (0x00)  | 1 (0x01) | Active flag (0x80 = bootable)                          |

| 0（0x00）| 1（0x01）| 活动标志（0x80 =可启动）|
| 1 (0x01)  | 1 (0x01) | Start head                                             |
| 2 (0x02)  | 1 (0x01) | Start sector (bits 0-5); upper bits of cylinder (6- 7) |

| 2（0x02）| 1（0x01）| 开始部门（位0-5）; 圆柱的上部（6-7）|
| 3 (0x03)  | 1 (0x01) | Start cylinder lowest 8 bits                           |

| 3（0x03）| 1（0x01）| 启动气缸最低8位|
| 4 (0x04)  | 1 (0x01) | Partition type code (0x83 = Linux)                     |
| 5 (0x05)  | 1 (0x01) | End head                                               |

| 5（0x05）| 1（0x01）| 端头|
| 6 (0x06)  | 1 (0x01) | End sector (bits 0-5); upper bits of cylinder (6- 7)   |

| 6（0x06）| 1（0x01）| 端部门（位0-5）; 圆柱的上部（6-7）|
| 7 (0x07)  | 1 (0x01) | End cylinder lowest 8 bits                             |

| 7（0x07）| 1（0x01）| 末端气缸最低8位|
| 8 (0x08)  | 4 (0x04) | Sectors preceding partition (little endian)            |

| 8（0x08）| 4（0x04）| 分区前的扇区（小末日）|
| 12 (0x0C) | 4 (0x04) | Sectors in partition                                   |

| 12（0x0c）| 4（0x04）| 分区中的扇区|

In order to mount an MBR in Linux you first need to get the start offset (you can use `fdisk` and the `p` command)

为了在Linux中安装MBR

![](<../../../.gitbook/assets/image (413) (3) (3) (3) (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (2).png>)

And then use the following code

然后使用以下代码

```bash
#Mount MBR in Linux
mount -o ro,loop,offset=<Bytes>
#63x512 = 32256Bytes
mount -o ro,loop,offset=32256,noatime /path/to/image.dd /media/part/
```

**LBA (Logical block addressing)**

** lba（逻辑块地址）**

**Logical block addressing** (**LBA**) is a common scheme used for **specifying the location of blocks** of data stored on computer storage devices, generally secondary storage systems such as hard disk drives. LBA is a particularly simple linear addressing scheme; **blocks are located by an integer index**, with the first block being LBA 0, the second LBA 1, and so on.

**逻辑块地址**（** lba **）是一种常见方案，用于**指定存储在计算机存储设备上的数据的位置**的位置**，通常是辅助存储系统，例如硬盘驱动器。 LBA是一个特别简单的线性寻址方案； **块由整数索引**定位，第一个块为lba 0，第二个lba 1，依此类推。

### GPT (GUID Partition Table)

### GPT（GUID分区表）

It’s called GUID Partition Table because every partition on your drive has a **globally unique identifier**.

它称为GUID分区表，因为您的驱动器上的每个分区都有一个全球唯一的标识符**。

Just like MBR it starts in the **sector 0**. The MBR occupies 32bits while **GPT** uses **64bits**.\

就像MBR一样，它从**扇区0 **开始。 MBR占32bits，而** gpt **使用** 64bits **。
GPT **allows up to 128 partitions** in Windows and up to **9.4ZB**.\

gpt **允许在Windows中最多允许128个分区**，最多可** 9.4zb **。\ \ \
Also, partitions can have a 36 character Unicode name.

此外，分区可以具有36个字符的Unicode名称。

On an MBR disk, the partitioning and boot data are stored in one place. If this data is overwritten or corrupted, you’re in trouble. In contrast, **GPT stores multiple copies of this data across the disk**, so it’s much more robust and can recover if the data is corrupted.

在MBR磁盘上，分区和引导数据存储在一个地方。 如果这些数据被覆盖或损坏，那么您会遇到麻烦。 相反，** gpt在整个磁盘上存储了此数据的多个副本**，因此它更强大，并且如果数据损坏，可以恢复。

GPT also stores **cyclic redundancy check (CRC)** values to check that its data is intact. If the data is corrupted, GPT can notice the problem and **attempt to recover the damaged data** from another location on the disk.

GPT还存储**循环冗余检查（CRC）**值以检查其数据是否完整。 如果数据损坏，GPT可能会注意到问题，并且**尝试从磁盘上的另一个位置恢复损坏的数据**。

**Protective MBR (LBA0)**

**保护mbr（lba0）**

For limited backward compatibility, the space of the legacy MBR is still reserved in the GPT specification, but it is now used in a **way that prevents MBR-based disk utilities from misrecognizing and possibly overwriting GPT disks**. This is referred to as a protective MBR.

对于有限的向后兼容性，Legacy MBR的空间仍保留在GPT规范中，但是现在它以一种防止基于MBR的磁盘实用程序的方式使用它，无法误解并可能覆盖GPT磁盘**。 这被称为保护性MBR。

![](<../../../.gitbook/assets/image (491).png>)

**Hybrid MBR (LBA 0 + GPT)**

In operating systems that support **GPT-based boot through BIOS** services rather than EFI, the first sector may also still be used to store the first stage of the **bootloader** code, but **modified** to recognize **GPT** **partitions**. The bootloader in the MBR must not assume a sector size of 512 bytes.

在支持基于gpt的启动的操作系统中，通过BIOS **而不是EFI，第一扇区还可以用于存储** bootloader **代码的第一阶段，但**修改**识别 ** gpt ** **分区**。 MBR中的引导加载程序不得假设扇区大小为512字节。

**Partition table header (LBA 1)**

**分区表标头（LBA 1）**

The partition table header defines the usable blocks on the disk. It also defines the number and size of the partition entries that make up the partition table (offsets 80 and 84 in the table).

分区表标头定义磁盘上的可用块。 它还定义了构成分区表的分区条目的数量和大小（表格中的80和84）。

| Offset    | Length   | Contents                                                                                                                                                                        |

| 偏移| 长度| 内容|
| --------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 0 (0x00)  | 8 bytes  | Signature ("EFI PART", 45h 46h 49h 20h 50h 41h 52h 54h or 0x5452415020494645ULL[ ](https://en.wikipedia.org/wiki/GUID\_Partition\_Table#cite\_note-8)on little-endian machines) |

| 0（0x00）| 8字节| 签名（“ EFI Part”，45H 46H 49H 20H 50H 41H 52H 54H或0X545241502049464645ULL []（https://en.wikipedia.org/wiki/guid/guid/guid/guid/guid/guid \ _partition \ _partition \ _pable_table.table#cite #cit #note-nill-ian-ian-nime-nian-ian-nian-nian-nian-nian-nian-nian-nian-nian-nian-nian-nir-enchine） |
| 8 (0x08)  | 4 bytes  | Revision 1.0 (00h 00h 01h 00h) for UEFI 2.8                                                                                                                                     |

| 8（0x08）| 4个字节| 修订版1.0（00H 00H 01H 00H 00H）用于UEFI 2.8 |
| 12 (0x0C) | 4 bytes  | Header size in little endian (in bytes, usually 5Ch 00h 00h 00h or 92 bytes)                                                                                                    |

| 12（0x0c）| 4个字节| Little Endian的标头尺寸（以字节为单位，通常为5CH 00H 00H 00H或92个字节）|
| 16 (0x10) | 4 bytes  | [CRC32](https://en.wikipedia.org/wiki/CRC32) of header (offset +0 up to header size) in little endian, with this field zeroed during calculation                                |

| 16（0x10）| 4个字节| [CRC32]（https://en.wikipedia.org/wiki/crc32）在Little Endian中的标题（偏移+0至标头尺寸），在计算过程中此字段为零|
| 20 (0x14) | 4 bytes  | Reserved; must be zero                                                                                                                                                          |

| 20（0x14）| 4个字节| 预订的; 必须为零|
| 24 (0x18) | 8 bytes  | Current LBA (location of this header copy)                                                                                                                                      |

| 24（0x18）| 8字节| 当前LBA（此标头副本的位置）|
| 32 (0x20) | 8 bytes  | Backup LBA (location of the other header copy)                                                                                                                                  |

| 32（0x20）| 8字节| 备份LBA（其他标题副本的位置）|
| 40 (0x28) | 8 bytes  | First usable LBA for partitions (primary partition table last LBA + 1)                                                                                                          |

| 40（0x28）| 8字节| 第一个可分区的LBA（主要分区表LAST LBA + 1）|| 48 (0x30) | 8 bytes  | Last usable LBA (secondary partition table first LBA − 1)                                                                                                                       |

| 48（0x30）| 8字节| 最后可用的LBA（辅助分区表第一lba -1）|
| 56 (0x38) | 16 bytes | Disk GUID in mixed endian                                                                                                                                                       |
| 72 (0x48) | 8 bytes  | Starting LBA of an array of partition entries (always 2 in primary copy)                                                                                                        |

| 72（0x48）| 8字节| 启动一系列分区条目的lba（始终在主副本中2个）|
| 80 (0x50) | 4 bytes  | Number of partition entries in array                                                                                                                                            |

| 80（0x50）| 4个字节| 数组中的分区条目数|
| 84 (0x54) | 4 bytes  | Size of a single partition entry (usually 80h or 128)                                                                                                                           |

| 84（0x54）| 4个字节| 单个分区条目的大小（通常为80h或128）|
| 88 (0x58) | 4 bytes  | CRC32 of partition entries array in little endian                                                                                                                               |

| 88（0x58）| 4个字节| Little Endian中的分区条目阵列的CRC32 |
| 92 (0x5C) | \*       | Reserved; must be zeroes for the rest of the block (420 bytes for a sector size of 512 bytes; but can be more with larger sector sizes)                                         |

| 92（0x5C）| \* | 预订的; 其余块必须为零（扇区大小为512字节的420个字节；但可以在较大的扇区尺寸的情况下更零）|

**Partition entries (LBA 2–33)**

| GUID partition entry format |          |                                                                                                                   |

| GUID分区条目格式| | |
| --------------------------- | -------- | ----------------------------------------------------------------------------------------------------------------- |
| Offset                      | Length   | Contents                                                                                                          |

| 偏移| 长度| 内容|
| 0 (0x00)                    | 16 bytes | [Partition type GUID](https://en.wikipedia.org/wiki/GUID\_Partition\_Table#Partition\_type\_GUIDs) (mixed endian) |

| 0（0x00）| 16字节| [分区类型GUID]（https://en.wikipedia.org/wiki/guid/guid \_partition \ _table#partition \ _type \ _guids）（混合endian）|
| 16 (0x10)                   | 16 bytes | Unique partition GUID (mixed endian)                                                                              |
| 32 (0x20)                   | 8 bytes  | First LBA ([little endian](https://en.wikipedia.org/wiki/Little\_endian))                                         |

| 32（0x20）| 8字节| 第一个LBA（[[Little Endian]（https://en.wikipedia.org/wiki/little \_Endian））|
| 40 (0x28)                   | 8 bytes  | Last LBA (inclusive, usually odd)                                                                                 |

| 40（0x28）| 8字节| 最后LBA（包含性，通常是奇怪的）|
| 48 (0x30)                   | 8 bytes  | Attribute flags (e.g. bit 60 denotes read-only)                                                                   |

| 48（0x30）| 8字节| 属性标志（例如，位60表示只读）|
| 56 (0x38)                   | 72 bytes | Partition name (36 [UTF-16](https://en.wikipedia.org/wiki/UTF-16)LE code units)                                   |

**Partitions Types**

![](<../../../.gitbook/assets/image (492).png>)

More partition types in [https://en.wikipedia.org/wiki/GUID\_Partition\_Table](https://en.wikipedia.org/wiki/GUID\_Partition\_Table)

更多分区类型在[https://en.wikipedia.org/wiki/guid/guid/guid \_partition \_table]（

### Inspecting

###检查

After mounting the forensics image with [**ArsenalImageMounter**](https://arsenalrecon.com/downloads/), you can inspect the first sector using the Windows tool [**Active Disk Editor**](https://www.disk-editor.org/index.html)**.** In the following image an **MBR** was detected on the **sector 0** and interpreted:

在使用[** arsenalimagemounter **]（https://arsenalrecon.com/downloads/）安装法医图像后，您可以使用Windows工具[** Active Disk Editor **]（https：/// www.disk-editor.org/index.html).4dhed）在下面的图像中，在** sector 0 **上检测到** mbr **并解释：

![](<../../../.gitbook/assets/image (494).png>)

If it was a **GPT table instead of an MBR** it should appear the signature _EFI PART_ in the **sector 1** (which in the previous image is empty).

如果是** gpt表，而不是mbr **，则应在**扇区1 **中显示签名_efi part_（在上一个图像中为空）。

## File-Systems

### Windows file-systems list

### Windows文件系统列表

* **FAT12/16**: MSDOS, WIN95/98/NT/200
* **FAT32**: 95/2000/XP/2003/VISTA/7/8/10
* **ExFAT**: 2008/2012/2016/VISTA/7/8/10
* **NTFS**: XP/2003/2008/2012/VISTA/7/8/10
* **ReFS**: 2012/2016

### FAT

＃＃＃ 胖的

The **FAT (File Allocation Table)** file system is named for its method of organization, the file allocation table, which resides at the beginning of the volume. To protect the volume, **two copies** of the table are kept, in case one becomes damaged. In addition, the file allocation tables and the root folder must be stored in a **fixed location** so that the files needed to start the system can be correctly located.

** fat（文件分配表）**文件系统以其组织分配表的方法命名，该方法位于卷开始时。 为了保护音量，**桌子的两个副本**如果被损坏，则保留了桌子的两份。 此外，文件分配表和根文件夹必须存储在**固定位置** **，以便启动系统所需的文件可以正确找到。

![](<../../../.gitbook/assets/image (495).png>)

The minimum space unit used by this file system is a **cluster, typically 512B** (which is composed of a number of sectors).

该文件系统使用的最小空间单元是一个**群集，通常为512B **（由许多扇区组成）。

The earlier **FAT12** had a **cluster addresses to 12-bit** values with up to **4078** **clusters**; it allowed up to 4084 clusters with UNIX. The more efficient **FAT16** increased to **16-bit** cluster address allowing up to **65,517 clusters** per volume. FAT32 uses 32-bit cluster address allowing up to **268,435,456 clusters** per volume

较早的** fat12 **有一个**群集地址为12位**值，最多** 4078 ** **簇**; 它允许使用UNIX多达4084个群集。 效率更高的** fat16 **增加到** 16位**群集地址，最多可** 65,517个簇**每卷。 FAT32使用32位群集地址，最多可** 268,435,456个簇**

The **maximum file size allowed by FAT is 4GB** (minus one byte) because the file system uses a 32-bit field to store the file size in bytes, and 2^32 bytes = 4 GiB. This happens for FAT12, FAT16 and FAT32.

脂肪允许的**最大文件大小为4GB **（减一个字节），因为文件系统使用32位字段将文件大小存储在字节中，而2^32个字节= 4 GIB。 这发生在FAT12，FAT16和FAT32中。

The **root directory** occupies a **specific position** for both FAT12 and FAT16 (in FAT32 it occupies a position like any other folder). Each file/folder entry contains this information:

** root目录**占据了fat12和fat16的特定位置**（在FAT32中，它像其他任何文件夹一样占据位置）。 每个文件/文件夹条目都包含以下信息：

* Name of the file/folder (8 chars max)

*文件/文件夹的名称（最大8个字符）
* Attributes
* Date of creation

*创建日期
* Date of modification

*修改日期
* Date of last access

*上次访问日期
* Address of the FAT table where the first cluster of the file starts

*文件的第一个集群开始的脂肪表的地址
* Size

When a file is "deleted" using a FAT file system, the directory entry remains almost **unchanged** except for the **first character of the file name** (modified to 0xE5), preserving most of the "deleted" file's name, along with its time stamp, file length and — most importantly — its physical location on the disk. The list of disk clusters occupied by the file will, however, be erased from the File Allocation Table, marking those sectors available for use by other files created or modified thereafter. In the case of FAT32, it is additionally an erased field responsible for the upper 16 bits of the file start cluster value.

当使用胖文件系统“删除”文件时，目录条目几乎保持**不变**，除了文件名**的**第一个字符（修改为0xE5），保留大多数“删除”文件的文件 名称，及其时间戳，文件长度，最重要的是 - 其物理位置在磁盘上。 但是，文件占用的磁盘群集列表将从文件分配表中删除，并将这些扇区标记为可用于此后创建或修改的其他文件的扇区。 在FAT32的情况下，它是负责文件启动群集值16位的擦除字段。

### **NTFS**

{% content-ref url="ntfs.md" %}
[ntfs.md](ntfs.md)
{% endcontent-ref %}

### EXT

**Ext2** is the most common file system for **not journaling** partitions (**partitions that don't change much**) like the boot partition. **Ext3/4** are **journaling** and are used usually for the **rest partitions**.

** ext2 **是**最常见的文件系统** **分区（**分区不会更改太多**），例如启动分区。 ** ext3/4 **是**日记**，通常用于**休息分区**。

{% content-ref url="ext.md" %}
[ext.md](ext.md)
{% endcontent-ref %}

## **Metadata**

Some files contain metadata. This information is about the content of the file which sometimes might be interesting to an analyst as depending on the file type, it might have information like:

有些文件包含元数据。 此信息是关于文件的内容，这些信息有时可能对分析师很有趣，因为它取决于文件类型，它可能具有以下信息：

* Title
* MS Office Version used

* MS Office版本使用
* Author

* 作者
* Dates of creation and last modification

*创建日期和最后修改的日期
* Model of the camera

*相机的模型
* GPS coordinates

* GPS坐标
* Image information

*图像信息

You can use tools like [**exiftool**](https://exiftool.org) and [**Metadiver**](https://www.easymetadata.com/metadiver-2/) to get the metadata of a file.

您可以使用[** exiftool **]（https://exiftool.org）和[** metadiver **]（https：//www.easmetadata.com/metadiver-2/）等工具以获取 一份文件。

## **Deleted Files Recovery**

## **删除文件恢复**

### Logged Deleted Files

As was seen before there are several places where the file is still saved after it was "deleted". This is because usually the deletion of a file from a file system just marks it as deleted but the data isn't touched. Then, it's possible to inspect the registries of the files (like the MFT) and find the deleted files.

如前几个地方，在“删除”文件后仍然保存该文件。 这是因为通常从文件系统中删除文件只是将其标记为已删除，但数据未触摸。 然后，可以检查文件的注册表（如MFT）并找到已删除的文件。

Also, the OS usually saves a lot of information about file system changes and backups, so it's possible to try to use them to recover the file or as much information as possible.

此外，该操作系统通常会节省有关文件系统更改和备份的大量信息，因此可以尝试使用它们来恢复文件或尽可能多的信息。

{% content-ref url="file-data-carving-recovery-tools.md" %}

{％content-ref url =“ file-data carving-recovery-tools.md”％}
[file-data-carving-recovery-tools.md](file-data-carving-recovery-tools.md)

[file-data carving-recovery-tools.md]（file-data carving-recovery-tools.md）
{% endcontent-ref %}

### **File Carving**

### **文件雕刻**

**File carving** is a technique that tries to **find files in the bulk of data**. There are 3 main ways tools like this work: **Based on file types headers and footers**, based on file types **structures** and based on the **content** itself.

**文件雕刻**是一种试图**在大量数据中找到文件的技术。 像这样的工具有3种主要方法：**基于文件类型的标头和页脚**，基于文件类型**结构**，并基于**内容**本身。

Note that this technique **doesn't work to retrieve fragmented files**. If a file **isn't stored in contiguous sectors**, then this technique won't be able to find it or at least part of it.

请注意，此技术**不起作用可检索零碎的文件**。 如果文件**未存储在连续的扇区**中，则该技术将无法找到它或至少一部分。

There are several tools that you can use for file Carving indicating the file types you want to search for

有几种工具可以用于文件雕刻，指示要搜索的文件类型

{% content-ref url="file-data-carving-recovery-tools.md" %}

{％content-ref url =“ file-data carving-recovery-tools.md”％}
[file-data-carving-recovery-tools.md](file-data-carving-recovery-tools.md)

[file-data carving-recovery-tools.md]（file-data carving-recovery-tools.md）
{% endcontent-ref %}

### Data Stream **C**arving

###数据流** c ** art

Data Stream Carving is similar to File Carving but **instead of looking for complete files, it looks for interesting fragments** of information.\

数据流雕刻类似于文件雕刻，但**而不是寻找完整的文件，它寻找有趣的片段**。
For example, instead of looking for a complete file containing logged URLs, this technique will search for URLs.

例如，该技术不会寻找包含已记录URL的完整文件，而是会搜索URL。

{% content-ref url="file-data-carving-recovery-tools.md" %}

{％content-ref url =“ file-data carving-recovery-tools.md”％}
[file-data-carving-recovery-tools.md](file-data-carving-recovery-tools.md)

[file-data carving-recovery-tools.md]（file-data carving-recovery-tools.md）
{% endcontent-ref %}

### Secure Deletion

###安全删除

Obviously, there are ways to **"securely" delete files and part of logs about them**. For example, it's possible to **overwrite the content** of a file with junk data several times, and then **remove** the **logs** from the **$MFT** and **$LOGFILE** about the file, and **remove the Volume Shadow Copies**.\

显然，有一些方法可以**“安全”删除文件以及有关它们的一部分**。 例如，可以**几次覆盖文件的内容**，然后**删除** ** logs ** ** $ mft **和** $ logfile ** 关于文件，**删除卷影副本**。\ \
You may notice that even performing that action there might be **other parts where the existence of the file is still logged**, and that's true and part of the forensics professional job is to find them.

您可能会注意到，即使执行该操作，也可能会有其他部分仍记录了文件，这是事实，而法医专业工作的一部分是找到它们。

## References

* [https://en.wikipedia.org/wiki/GUID\_Partition\_Table](https://en.wikipedia.org/wiki/GUID\_Partition\_Table)
* [http://ntfs.com/ntfs-permissions.htm](http://ntfs.com/ntfs-permissions.htm)
* [https://www.osforensics.com/faqs-and-tutorials/how-to-scan-ntfs-i30-entries-deleted-files.html](https://www.osforensics.com/faqs-and-tutorials/how-to-scan-ntfs-i30-entries-deleted-files.html)
* [https://docs.microsoft.com/en-us/windows-server/storage/file-server/volume-shadow-copy-service](https://docs.microsoft.com/en-us/windows-server/storage/file-server/volume-shadow-copy-service)
* **iHackLabs Certified Digital Forensics Windows**

*** IHACKLABS认证的数字取证Windows **

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
