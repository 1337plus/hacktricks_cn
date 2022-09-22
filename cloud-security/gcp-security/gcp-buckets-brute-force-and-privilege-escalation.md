# GCP - Buckets: Public Assets Brute-Force & Discovery, & Buckets Privilege Escalation

＃GCP-存储桶：公共资产蛮力和发现，＆Bucket＆Bucks oferte升级

## GCP - Buckets: Public Assets Brute-Force & Discovery, & Buckets Privilege Escalation

## GCP-存储桶：公共资产蛮力和发现，＆Bucket＆Buckt oferilege升级

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

## Public Assets Discovery

##公共资产发现

One way to discover public cloud resources that belongs to a company is to scrape their webs looking for them. Tools like [**CloudScraper**](https://github.com/jordanpotti/CloudScraper) will scrape the web an search for **links to public cloud resources** (in this case this tools searches `['amazonaws.com', 'digitaloceanspaces.com', 'windows.net', 'storage.googleapis.com', 'aliyuncs.com']`)

发现属于公司的公共云资源的一种方法是刮擦他们的网。 [** CloudScraper **]（https://github.com/jordanpotti/cloudscraper）等工具将刮擦网络一个搜索**链接到公共云资源**（在这种情况下，此工具搜索`'['amazonaws。 com'，'digitaloceanspaces.com'，'windows.net'，'storage.googleapis.com'，'aliyuncs.com']`）`）

Note that other cloud resources could be searched for and that some times these resources are hidden behind **subdomains that are pointing them via CNAME registry**.

请注意，可以搜索其他云资源，并且有时这些资源隐藏在通过CNAME注册表指向它们的**子域后面。

## Public Resources Brute-Force

##公共资源蛮力

### Buckets, Firebase, Apps & Cloud Functions

###存储桶，燃料，应用和云功能

* [https://github.com/initstring/cloud\_enum](https://github.com/initstring/cloud\_enum): This tool in GCP brute-force Buckets, Firebase Realtime Databases, Google App Engine sites, and Cloud Functions

* [https://github.com/initstring/cloud \ _enum]（ 和云功能
* [https://github.com/0xsha/CloudBrute](https://github.com/0xsha/CloudBrute): This tool in GCP brute-force Buckets and Apps.

* [https://github.com/0xsha/cloudbrute]（

### Buckets

As other clouds, GCP also offers Buckets to its users. These buckets might be (to list the content, read, write...).

与其他云一样，GCP还为其用户提供了存储桶。 这些存储桶可能是（列出内容，读，写...）。

![](<../../.gitbook/assets/image (618) (3).png>)

The following tools can be used to generate variations of the name given and search for miss-configured buckets with that names:

以下工具可用于生成名称的变体，并搜索具有该名称的错过配置的存储桶：

* [https://github.com/RhinoSecurityLabs/GCPBucketBrute](https://github.com/RhinoSecurityLabs/GCPBucketBrute)

## Privilege Escalation

If the bucket policy allowed either “allUsers” or “allAuthenticatedUsers” to **write to their bucket policy** (the **storage.buckets.setIamPolicy** permission)**,** then anyone can modify the bucket policy and grant himself full access.

如果遗愿策略允许“ Allusers”或“ AllauthenticatedUsers”来**写入他们的存储策略**（** storage.buckets.buckets.setiampolicy **许可）**，** 自己完全访问。

### Check Permissions

###检查权限

There are 2 ways to check the permissions over a bucket. The first one is to ask for them by making a request to `https://www.googleapis.com/storage/v1/b/BUCKET_NAME/iam` or running `gsutil iam get gs://BUCKET_NAME`.

有两种方法可以检查存储桶上的权限。

However, if your user (potentially belonging to allUsers or allAuthenticatedUsers") doesn't have permissions to read the iam policy of the bucket (storage.buckets.getIamPolicy), that won't work.

但是，如果您的用户（可能属于Allusers或AllauthenticatiCatedUsers”）没有权限可以阅读Bucket的IAM策略（Storage.buckets.getiampolicy），那将行不通。

The other option which will always work is to use the testPermissions endpoint of the bucket to figure out if you have the specified permission, for example accessing: `https://www.googleapis.com/storage/v1/b/BUCKET_NAME/iam/testPermissions?permissions=storage.buckets.delete&permissions=storage.buckets.get&permissions=storage.buckets.getIamPolicy&permissions=storage.buckets.setIamPolicy&permissions=storage.buckets.update&permissions=storage.objects.create&permissions=storage.objects.delete&permissions=storage.objects.get&permissions=storage.objects.list&permissions=storage.objects.update`

始终将始终可行的另一个选项是使用存储桶的端点端点来确定是否已指定许可，例如访问：`https：//www.googleapis.com/storage/storage/v1/b/bucket_name/iam .get＆permissions = storage.objects.list＆permissions = storage.objects.update`

### Escalating

With the “gsutil” Google Storage CLI program, we can run the following command to grant “allAuthenticatedUsers” access to the “Storage Admin” role, thus **escalating the privileges we were granted** to the bucket:

借助“ GSUTIL” Google Storage CLI程序，我们可以运行以下命令来授予“ AllauthenticatedUsers”对“存储管理员”角色的访问权限，因此**升级了我们被授予的特权**：

```
gsutil iam ch group:allAuthenticatedUsers:admin gs://BUCKET_NAME
```

One of the main attractions to escalating from a LegacyBucketOwner to Storage Admin is the ability to use the “storage.buckets.delete” privilege. In theory, you could **delete the bucket after escalating your privileges, then you could create the bucket in your own account to steal the name**.

从LegacyBucketowner升级为存储管理员的主要景点之一是使用“ store.buckets.delete”特权的能力。 从理论上讲，您可以在升级特权后**删除水桶，然后可以在自己的帐户中创建存储桶以窃取名称**。

## References

* [https://rhinosecuritylabs.com/gcp/google-cloud-platform-gcp-bucket-enumeration/](https://rhinosecuritylabs.com/gcp/google-cloud-platform-gcp-bucket-enumeration/)

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
