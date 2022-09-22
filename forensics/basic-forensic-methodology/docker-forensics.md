# Docker Forensics

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

## Container modification

There are suspicions that some docker container was compromised:

有一些怀疑某些Docker容器被妥协：

```bash
docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
cc03e43a052a        lamp-wordpress      "./run.sh"          2 minutes ago       Up 2 minutes        80/tcp              wordpress
```

You can easily **find the modifications done to this container with regards to the image** with:

您可以轻松地**找到有关图像**的对此容器进行的修改：

```bash
docker diff wordpress
C /var
C /var/lib
C /var/lib/mysql
A /var/lib/mysql/ib_logfile0
A /var/lib/mysql/ib_logfile1
A /var/lib/mysql/ibdata1
A /var/lib/mysql/mysql
A /var/lib/mysql/mysql/time_zone_leap_second.MYI
A /var/lib/mysql/mysql/general_log.CSV
...
```

In the previous command **C** means **Changed** and **A,** **Added**.\

在上一个命令中** c **表示**更改**和** a，** **添加**。
If you find that some interesting file like `/etc/shadow` was modified you can download it from the container to check for malicious activity with:

如果您发现修改了一些有趣的文件，例如“/etc/shadow”，则可以从容器中下载它以检查恶意活动：

```bash
docker cp wordpress:/etc/shadow.
```

You can also **compare it with the original one** running a new container and extracting the file from it:

您也可以**将其与原始一个**进行比较，然后从中提取文件并从中提取文件：

```bash
docker run -d lamp-wordpress
docker cp b5d53e8b468e:/etc/shadow original_shadow #Get the file from the newly created container
diff original_shadow shadow
```

If you find that **some suspicious file was added** you can access the container and check it:

如果发现**添加了一些可疑文件**，您可以访问容器并检查：

```bash
docker exec -it wordpress bash
```

## Images modifications

##图像修改

When you are given an exported docker image (probably in `.tar` format) you can use [**container-diff**](https://github.com/GoogleContainerTools/container-diff/releases) to **extract a summary of the modifications**:

当您获得导出的Docker映像（可能是`.tar`格式）时，可以使用[** container-diff **]（https://github.com/googlecontainertools/container-container-diff/releases） 修改**的摘要：

```bash
docker save <image> > image.tar #Export the image to a .tar file
container-diff analyze -t sizelayer image.tar
container-diff analyze -t history image.tar
container-diff analyze -t metadata image.tar
```

Then, you can **decompress** the image and **access the blobs** to search for suspicious files you may have found in the changes history:

然后，您可以**解压缩**图像和**访问blobs **以搜索您在更改历史记录中可能发现的可疑文件：

```bash
tar -xf image.tar
```

### Basic Analysis

###基本分析

You can get **basic information** from the image running:

您可以从运行图像中获得**基本信息**：

```bash
docker inspect <image> 
```

You can also get a summary **history of changes** with:

您还可以获取更改的摘要** **的历史：

```bash
docker history --no-trunc <image>
```

You can also generate a **dockerfile from an image** with:

您还可以从图像**生成** dockerfile：

```bash
alias dfimage="docker run -v /var/run/docker.sock:/var/run/docker.sock --rm alpine/dfimage"
dfimage -sV=1.36 madhuakula/k8s-goat-hidden-in-layers>
```

### Dive

In order to find added/modified files in docker images you can also use the [**dive**](https://github.com/wagoodman/dive) (download it from [**releases**](https://github.com/wagoodman/dive/releases/tag/v0.10.0)) utility:

为了在docker映像中查找添加/修改的文件，您还可以使用[** dive **]（https://github.com/wagoodman/dive）（从[** relesease **]（https：https：https：https：https：https：https：https：https： //github.com/wagoodman/dive/releases/tag/v0.10.0））实用程序：

```bash
#First you need to load the image in your docker repo
sudo docker load < image.tar                                                                                                                                                                                                         1 ⨯
Loaded image: flask:latest

#And then open it with dive:
sudo dive flask:latest
```

This allows you to **navigate through the different blobs of docker images** and check which files were modified/added. **Red** means added and **yellow** means modified. Use **tab** to move to the other view and **space** to collapse/open folders.

这使您可以**浏览Docker Images **的不同斑点，并检查哪些文件已修改/添加。 **红色**表示添加和**黄色**表示修改。 使用**选项卡**移动到其他视图，并且**空间**折叠/打开文件夹。

With die you won't be able to access the content of the different stages of the image. To do so you will need to **decompress each layer and access it**.\

使用Die，您将无法访问图像不同阶段的内容。 为此，您需要**解压缩每一层并访问**。
You can decompress all the layers from an image from the directory where the image was decompressed executing:

您可以从图像被解压缩执行的目录中解压缩所有层：

```bash
tar -xf image.tar
for d in `find * -maxdepth 0 -type d`; do cd $d; tar -xf ./layer.tar; cd ..; done
```

## Credentials from memory

##来自内存的凭据

Note that when you run a docker container inside a host **you can see the processes running on the container from the host** just running `ps -ef`

请注意，当您在主机内运行Docker容器**时，您可以看到从主机上运行的过程**仅运行`ps -ef`

Therefore (as root) you can **dump the memory of the processes** from the host and search for **credentials** just [**like in the following example**](../../linux-hardening/privilege-escalation/#process-memory).

因此（作为根）您可以**从主机中倾倒进程的内存**，并搜索**凭据** [** just [**''在以下示例**]（../ ../ linux-hardening /特权 - 估算/＃流程模式）。

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
