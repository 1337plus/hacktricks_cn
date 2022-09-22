# GCP Security

＃GCP安全性

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

## Security concepts <a href="#security-concepts" id="security-concepts"></a>

##安全概念<a href="#security-concepts" id="security-concepts"> </a>

### **Resource hierarchy**

### **资源层次结构**

Google Cloud uses a [Resource hierarchy](https://cloud.google.com/resource-manager/docs/cloud-platform-resource-hierarchy) that is similar, conceptually, to that of a traditional filesystem. This provides a logical parent/child workflow with specific attachment points for policies and permissions.

Google Cloud使用[资源层次结构]（https://cloud.google.com/resource-manager/docs/cloud-platform-resource-hierce-hierarchy），与传统文件系统相似。 这提供了逻辑上的父/子工作流程，并具有特定的策略和权限附件。

At a high level, it looks like this:

在高水平上，看起来像这样：

```
Organization
--> Folders
  --> Projects
    --> Resources
```

A virtual machine (called a Compute Instance) is a resource. A resource resides in a project, probably alongside other Compute Instances, storage buckets, etc.

虚拟机（称为计算实例）是资源。 资源驻留在项目中，可能与其他计算实例，储物桶等一起使用。

### **IAM Roles**

There are **three types** of roles in IAM:

IAM中有**三种类型的角色：

* **Basic/Primitive roles**, which include the **Owner**, **Editor**, and **Viewer** roles that existed prior to the introduction of IAM.

***基本/原始角色**，其中包括**所有者**，**编辑**和** viever ** **在介绍IAM之前存在的角色。
* **Predefined roles**, which provide granular access for a specific service and are managed by Google Cloud. There are a lot of predefined roles, you can **see all of them with the privileges they have** [**here**](https://cloud.google.com/iam/docs/understanding-roles#predefined\_roles).

***预定义的角色**，它为特定服务提供了粒状访问，并由Google Cloud管理。 有很多预定义的角色，您可以**与他们拥有的特权一起查看所有这些角色（**在这里**]） \ _Roles）。
* **Custom roles**, which provide granular access according to a user-specified list of permissions.

***自定义角色**，根据用户指定的权限列表提供颗粒状访问。

There are thousands of permissions in GCP. In order to check if a role has a permissions you can [**search the permission here**](https://cloud.google.com/iam/docs/permissions-reference) and see which roles have it.

GCP中有成千上万的权限。 为了检查角色是否具有权限，您可以[**在此处搜索权限**]（https://cloud.google.com/iam/docs/permissions-reference），看看哪个角色具有它。

**You can also** [**search here predefined roles**](https://cloud.google.com/iam/docs/understanding-roles#product\_specific\_documentation) **offered by each product.**

**您也可以** [**在这里搜索预定义的角色**]（https://cloud.google.com/iam/docs/docs/understanding-roles#product \ _specific \ _specific \_documentation）**）。 *

**You can find a** [**list of all the granular permissions here**](https://cloud.google.com/iam/docs/custom-roles-permissions-support)**.**

**您可以在此处找到所有粒状权限的列表**]

#### Basic roles

| Name             | Title  | Permissions                                                                                                                                                                                                                                        |

| 名称| 标题| 权限|
| ---------------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **roles/viewer** | Viewer | Permissions for **read-only actions** that do not affect state, such as viewing (but not modifying) existing resources or data.                                                                                                                    |

| **角色/查看器** | 查看器| **仅阅读动作的权限**不影响状态的权限，例如查看（但不修改）现有资源或数据。 |
| **roles/editor** | Editor | All **viewer permissions**, **plus** permissions for actions that modify state, such as changing existing resources.                                                                                                                               |

| **角色/编辑** | 编辑| 所有**查看器权限**，**加上**修改状态的操作的权限，例如更改现有资源。 |
| **roles/owner**  | Owner  | <p>All <strong>Editor</strong> permissions <strong>and</strong> permissions for the following actions:</p><ul><li>Manage roles and permissions for a project and all resources within the project.</li><li>Set up billing for a project.</li></ul> |

| **角色/所有者** | 所有者| <p>全部<stront>编辑</strong>权限<strong>和</strong>以下操作的权限：</p> <ul> <li>管理项目和项目中的所有资源的角色和权限 。</li> <li>为项目设置计费。</li> </ul> |

You can try the following command to specifically **enumerate roles assigned to your service account** project-wide in the current project:

您可以尝试以下命令，以专门**列举为您的服务帐户分配的角色**当前项目中的项目范围内：

```bash
PROJECT=$(curl http://metadata.google.internal/computeMetadata/v1/project/project-id \
    -H "Metadata-Flavor: Google" -s)
ACCOUNT=$(curl http://metadata.google.internal/computeMetadata/v1/instance/service-accounts/default/email \
    -H "Metadata-Flavor: Google" -s)
gcloud projects get-iam-policy $PROJECT  \
    --flatten="bindings[].members" \
    --format='table(bindings.role)' \
    --filter="bindings.members:$ACCOUNT"
```

Don't worry too much if you get denied access to the command above. It's still possible to work out what you can do simply by trying to do it.

如果您被拒绝访问上面的命令，请不要担心太多。 仍然有可能仅通过尝试完成您可以做的事情。

More generally, you can shorten the command to the following to get an idea of the **roles assigned project-wide to all members**.

更一般而言，您可以将命令缩短到以下内容，以了解向所有成员**分配的**角色。

```
gcloud projects get-iam-policy [PROJECT-ID]
```

Or to see the IAM policy [assigned to a single Compute Instance](https://cloud.google.com/sdk/gcloud/reference/compute/instances/get-iam-policy) you can try the following.

或查看IAM策略[分配给单个计算实例]（https://cloud.google.com/sdk/gcloud/reference/compute/compute/get-iam-policy），您可以尝试以下内容。

```
gcloud compute instances get-iam-policy [INSTANCE] --zone [ZONE]
```

### **Organization Policies**

### **组织政策**

The IAM policies indicates the permissions principals has over resources via roles which ara assigned granular permissions. Organization policies **restrict how those service can be used or which features are enabled disabled**. This helps in order to improve the least privilege of each resource in the gcp environment.

IAM政策表明，权限本金通过ARA分配了颗粒处的角色具有优质资源。 组织策略**限制如何使用这些服务或启用哪些功能被禁用**。 这有助于提高GCP环境中每个资源的最低特权。

### **Terraform IAM Policies, Bindings and Memberships**

### ** Terraform IAM政策，绑定和会员资格**

As defined by terraform in [https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/google\_project\_iam](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/google\_project\_iam) using terraform with GCP there are different ways to grant a principal access over a resource:

如Terraform在[https://registry.terraform.io/providers/hashicorp/google/latest/latest/docs/resources/google/google/google \ _project \_iam]（ /最新/docs/resources/google \ _project \ _iam）使用Terraform与GCP使用Terraform，有不同的方法可以通过资源授予主要访问权限：

* **Memberships**: You set **principals as members of roles** **without restrictions** over the role or the principals. You can put a user as a member of a role and then put a group as a member of the same role and also set those principals (user and group) as member of other roles.

***会员资格**：您将**校长设置为角色的成员** **无限制**关于角色或校长的成员。 您可以将用户作为角色的成员，然后将小组作为同一角色的成员，并将这些主体（用户和组）设置为其他角色的成员。
* **Bindings**: Several **principals can be binded to a role**. Those **principals can still be binded or be members of other roles**. However, if a principal which isn’t binded to the role is set as **member of a binded role**, the next time the **binding is applied, the membership will disappear**.

***绑定**：几个**可以扮演角色**。 这些**校长仍然可以伴随或成为其他角色的成员**。 但是，如果没有束缚角色的校长被视为绑定角色的**成员**，那么下次使用绑定时，会员资格将消失**。
* **Policies**: A policy is **authoritative**, it indicates roles and principals and then, **those principals cannot have more roles and those roles cannot have more principals** unless that policy is modified (not even in other policies, bindings or memberships). Therefore, when a role or principal is specified in policy all its privileges are **limited by that policy**. Obviously, this can be bypassed in case the principal is given the option to modify the policy or privilege escalation permissions (like create a new principal and bind him a new role).

***政策**：政策是**权威**，它指示角色和校长，然后，**这些校长不能扮演更多的角色，除非修改该政策，否 其他政策，绑定或会员资格）。 因此，当政策中指定角色或委托人时，其所有特权都受到该政策的限制。 显然，如果委托人可以选择修改策略或特权升级权限（例如创建新的校长并将他绑定新角色），则可以绕过这一点。

### **Service accounts**

### **服务帐户**

Virtual machine instances are usually **assigned a service account**. Every GCP project has a [default service account](https://cloud.google.com/compute/docs/access/service-accounts#default\_service\_account), and this will be assigned to new Compute Instances unless otherwise specified. Administrators can choose to use either a custom account or no account at all. This service account **can be used by any user or application on the machine** to communicate with the Google APIs. You can run the following command to see what accounts are available to you:

虚拟机实例通常被**分配一个服务帐户**。 每个GCP项目都有一个[默认服务帐户]（https://cloud.google.com/compute/compute/docs/access/service-accounts#default/_service \ _account），除非另外指定，否则将分配给新计算实例 。 管理员可以选择使用自定义帐户或根本没有帐户。 该服务帐户**可以由机器上的任何用户或应用程序使用**与Google API进行通信。 您可以运行以下命令以查看可用的帐户：

```
gcloud auth list
```

**Default service accounts will look like** one of the following:

**默认服务帐户看起来像**以下一个：

```
PROJECT_NUMBER-compute@developer.gserviceaccount.com
PROJECT_ID@appspot.gserviceaccount.com
```

A **custom service account** will look like this:

**自定义服务帐户**看起来像这样：

```
SERVICE_ACCOUNT_NAME@PROJECT_NAME.iam.gserviceaccount.com
```

If `gcloud auth list` returns **multiple** accounts **available**, something interesting is going on. You should generally see only the service account. If there is more than one, you can cycle through each using `gcloud config set account [ACCOUNT]` while trying the various tasks in this blog.

如果`gcloud auth List`返回**多个**帐户**可用**，那么正在发生一些有趣的事情。 通常，您应该仅查看服务帐户。 如果有多个以上，则可以使用`gcloud config set account [account]`在此博客中尝试各种任务时都可以循环循环。

### **Access scopes**

### **访问范围**

The **service account** on a GCP Compute Instance will **use** **OAuth** to communicate with the Google Cloud APIs. When [access scopes](https://cloud.google.com/compute/docs/access/service-accounts#accesscopesiam) are used, the OAuth token that is generated for the instance will **have a** [**scope**](https://oauth.net/2/scope/) **limitation included**. This defines **what API endpoints it can authenticate to**. It does **NOT define the actual permissions**.

GCP Compute实例上的**服务帐户**将**使用** ** oauth **与Google Cloud API进行通信。 当[访问范围]（https://cloud.google.com/compute/docs/access/service-accounts#accesscopesiam）时，为实例生成的oauth代币将** **有一个** [** [**] 范围**]（https://oauth.net/2/scope/）**包括**。 这定义了** API端点可以对**进行身份验证。 它确实没有定义实际权限**。

When using a **custom service account**, Google [recommends](https://cloud.google.com/compute/docs/access/service-accounts#service\_account\_permissions) that access scopes are not used and to **rely totally on IAM**. The web management portal actually enforces this, but access scopes can still be applied to instances using custom service accounts programatically.

使用**自定义服务帐户**时，Google [推荐]（https://cloud.google.com/compute/compute/docs/access/service-accounts#service \ _account \ _permissions）访问范围不使用且不使用且不使用 **完全依靠IAM **。 Web Management门户网站实际上可以实施此功能，但是使用自定义服务帐户编程的访问范围仍然可以应用于实例。

There are three options when setting an access scope on a VM instance:

在VM实例上设置访问范围时，有三个选项：

* Allow default access

*允许默认访问
* All full access to all cloud APIs
* Set access for each API

*设置每个API的访问权限

You can see what **scopes** are **assigned** by **querying** the **metadata** URL. Here is an example from a VM with "default" access assigned:

您可以通过**查询** ** ** ** **元数据** ** scopes ** scopes **。 这是来自具有“默认”访问的VM的示例：

```
$ curl http://metadata.google.internal/computeMetadata/v1/instance/service-accounts/default/scopes \
    -H 'Metadata-Flavor:Google'

https://www.googleapis.com/auth/devstorage.read_only
https://www.googleapis.com/auth/logging.write
https://www.googleapis.com/auth/monitoring.write
https://www.googleapis.com/auth/servicecontrol
https://www.googleapis.com/auth/service.management.readonly
https://www.googleapis.com/auth/trace.append
```

The most interesting thing in the **default** **scope** is **`devstorage.read_only`**. This grants read access to all storage buckets in the project. This can be devastating, which of course is great for us as an attacker.

**默认** **范围**中最有趣的事情是** d devstorage.read_only` **。 赠款阅读项目中所有存储存储桶的访问。 这可能是毁灭性的，当然这对我们来说是一名攻击者。

Here is what you'll see from an instance with **no scope limitations**:

这是您从没有范围限制的实例中看到的**：

```
curl http://metadata.google.internal/computeMetadata/v1/instance/service-accounts/default/scopes -H 'Metadata-Flavor:Google'
https://www.googleapis.com/auth/cloud-platform
```

This `cloud-platform` scope is what we are really hoping for, as it will allow us to authenticate to any API function and leverage the full power of our assigned IAM permissions.

我们真正希望的“云 - 平台”范围是我们真正希望的，因为它可以使我们对任何API功能进行身份验证并利用我们分配的IAM权限的全部功能。

It is possible to encounter some **conflicts** when using both **IAM and access scopes**. For example, your service account may have the IAM role of `compute.instanceAdmin` but the instance you've breached has been crippled with the scope limitation of `https://www.googleapis.com/auth/compute.readonly`. This would prevent you from making any changes using the OAuth token that's automatically assigned to your instance.

使用** iam和访问范围**时，可能会遇到一些**冲突**。 例如，您的服务帐户可能具有`compute.instanceadmin'的IAM角色，但是您违反的实例因https：// www.googleapis.com/auth/compute/compute.readonly'的范围而受到损害。 这将阻止您使用自动分配给实例的OAuth代币进行任何更改。

### Default credentials <a href="#default-credentials" id="default-credentials"></a>

**Default service account token**

**默认服务帐户令牌**

The **metadata server** available to a given instance will **provide** any user/process **on that instance** with an **OAuth token** that is automatically used as the **default credentials** when communicating with Google APIs via the `gcloud` command.

给定实例可用的**元数据服务器**将**提供**该实例上的任何用户/进程** **与** oauth token ** **自动用作**默认凭据** 通过“ GCLOUD”命令与Google API进行通信。

You can retrieve and inspect the token with the following curl command:

您可以使用以下curl命令检索并检查令牌：

```bash
curl "http://metadata.google.internal/computeMetadata/v1/instance/service-accounts/default/token" \
    -H "Metadata-Flavor: Google"
```

Which will receive a response like the following:

将收到以下答复：

```json
{
      "access_token":"ya29.AHES6ZRN3-HlhAPya30GnW_bHSb_QtAS08i85nHq39HE3C2LTrCARA",
      "expires_in":3599,
      "token_type":"Bearer"
 }
```

This token is the **combination of the service account and access scopes** assigned to the Compute Instance. So, even though your service account may have **every IAM privilege** imaginable, this particular OAuth token **might be limited** in the APIs it can communicate with due to **access scopes**.

该令牌是服务帐户和访问范围**分配给计算实例的**组合。 因此，即使您的服务帐户可能具有**可以想象的每个IAM特权**，但由于**访问范围**，这种特殊的OAuth令牌**可能受到限制**。

**Application default credentials**

When using one of Google's official GCP client libraries, the code will automatically go **searching for credentials** following a strategy called [Application Default Credentials](https://cloud.google.com/docs/authentication/production).

当使用Google的官方GCP客户端库之一时，该代码将自动进行**搜索凭据**遵循称为[应用程序默认凭据]（https://cloud.google.com/docs/authentication/production）的策略。

1. First, it will check would be the [**source code itself**](https://cloud.google.com/docs/authentication/production#passing\_the\_path\_to\_the\_service\_account\_key\_in\_code). Developers can choose to statically point to a service account key file.

1.首先，它将检查是[**源代码本身**]（https：//cloud.google.com/docs/authentication/authentication/production#passing \ _the \ _the \ _ _path \ _to \ _the \ _service \ _service \ _account \ _account \ _account \ \ \ \ \ \ \ \ \ \ \ \ _ \ _ _key \ _in \ _code）。 开发人员可以选择静态指向服务帐户密钥文件。
2. The next is an **environment variable called `GOOGLE_APPLICATION_CREDENTIALS`**. This can be set to point to a **service account key file**.

2.下一个是一个**环境变量，称为`google_application_credentials` **。 可以将其设置为**服务帐户密钥文件**。
3. Finally, if neither of these are provided, the application will revert to using the **default token provided by the metadata server** as described in the section above.

3.最后，如果两个都没有提供，则该应用程序将恢复为使用上面部分所述的元数据服务器**提供的**默认令牌。

Finding the actual **JSON file with the service account credentials** is generally much **more** **desirable** than **relying on the OAuth token** on the metadata server. This is because the raw service account credentials can be activated **without the burden of access scopes** and without the short expiration period usually applied to the tokens.

与依赖元数据服务器上的OAuth令牌**相比，找到具有服务帐户凭据**的实际** JSON文件通常** ** ** **。 这是因为可以激活原始服务帐户凭据**，而无需访问范围的负担**，并且没有短期到期期限通常适用于代币。

### **Networking**

Compute Instances are connected to networks called VPCs or [Virtual Private Clouds](https://cloud.google.com/vpc/docs/vpc). [GCP firewall](https://cloud.google.com/vpc/docs/firewalls) rules are defined at this network level but are applied individually to a Compute Instance. Every network, by default, has two [implied firewall rules](https://cloud.google.com/vpc/docs/firewalls#default\_firewall\_rules): allow outbound and deny inbound.

计算实例连接到称为VPC或[虚拟私有云]（https://cloud.google.com/vpc/docs/vpc）的网络。 [GCP防火墙]（https://cloud.google.com/vpc/docs/firewalls）规则在此网络级别定义，但单独应用于计算实例。 默认情况下，每个网络都有两个[隐含的防火墙规则]（https://cloud.google.com/vpc/docs/firewalls#default \ _firewall _rules）：允许出站和拒绝入站。

Each GCP project is provided with a VPC called `default`, which applies the following rules to all instances:

每个GCP项目均为称为“ Default”的VPC，该VPC适用于所有实例：

* default-allow-internal (allow all traffic from other instances on the `default` network)

*默认允许内部（允许``默认网络）上其他实例的所有流量）
* default-allow-ssh (allow 22 from everywhere)

*默认允许ssh（无处不在22个）
* default-allow-rdp (allow 3389 from everywhere)

* Default-Allow-RDP（允许到处允许3389）
* default-allow-icmp (allow ping from everywhere)

*默认允许-ICMP（允许无处不在的ping）

**Meet the neighbors**

**见邻居**

Firewall rules may be more permissive for internal IP addresses. This is especially true for the default VPC, which permits all traffic between Compute Instances.

防火墙规则可能更允许内部IP地址。 对于默认VPC而言，尤其如此，该VPC允许在计算实例之间进行所有流量。

You can get a nice readable view of all the subnets in the current project with the following command:

您可以通过以下命令获得当前项目中所有子网的可读视图：

```
gcloud compute networks subnets list
```

And an overview of all the internal/external IP addresses of the Compute Instances using the following:

以及使用以下内容概述计算实例的所有内部/外部IP地址：

```
gcloud compute instances list
```

If you go crazy with nmap from a Compute Instance, Google will notice and will likely send an alert email to the project owner. This is more likely to happen if you are scanning public IP addresses outside of your current project. Tread carefully.

如果您对Compute实例的NMAP疯狂，则Google会注意到，并可能会向项目所有者发送警报电子邮件。 如果您在当前项目之外扫描公共IP地址，则更有可能发生。 小心翼翼。

**Enumerating public ports**

**列举公共港口**

Perhaps you've been unable to leverage your current access to move through the project internally, but you DO have read access to the compute API. It's worth enumerating all the instances with firewall ports open to the world - you might find an insecure application to breach and hope you land in a more powerful position.

也许您一直无法利用当前的访问权限来内部通过该项目，但是您确实已经阅读了对Compute API的访问。 值得列举所有向世界开放的防火墙端口的实例 - 您可能会发现不安全的申请来违反，并希望您登陆更强大的位置。

In the section above, you've gathered a list of all the public IP addresses. You could run nmap against them all, but this may taken ages and could get your source IP blocked.

在上面的部分中，您已收集了所有公共IP地址的列表。 您可以对他们全部运行nmap，但是这可能会花费很长时间，并且可以阻止源IP。

When attacking from the internet, the default rules don't provide any quick wins on properly configured machines. It's worth checking for password authentication on SSH and weak passwords on RDP, of course, but that's a given.

从Internet进行攻击时，默认规则不会在正确配置的机器上快速获胜。 当然，值得检查有关SSH和弱密码的密码身份验证，但这是给定的。

What we are really interested in is other firewall rules that have been intentionally applied to an instance. If we're lucky, we'll stumble over an insecure application, an admin interface with a default password, or anything else we can exploit.

我们真正感兴趣的是有意应用于实例的其他防火墙规则。 如果幸运的话，我们将偶然发现一个不安全的应用程序，带有默认密码的管理接口或我们可以利用的其他任何内容。

[Firewall rules](https://cloud.google.com/vpc/docs/firewalls) can be applied to instances via the following methods:

[防火墙规则]（https://cloud.google.com/vpc/docs/firewalls）可以通过以下方法应用于实例：

* [Network tags](https://cloud.google.com/vpc/docs/add-remove-network-tags)
* [Service accounts](https://cloud.google.com/vpc/docs/firewalls#serviceaccounts)

* [服务帐户]（https://cloud.google.com/vpc/docs/firewalls#serviceaccounts）
* All instances within a VPC

* VPC中的所有实例

Unfortunately, there isn't a simple `gcloud` command to spit out all Compute Instances with open ports on the internet. You have to connect the dots between firewall rules, network tags, services accounts, and instances.

不幸的是，没有一个简单的“ gcloud”命令来吐出所有计算实例，并在互联网上开放端口。 您必须在防火墙规则，网络标签，服务帐户和实例之间连接点。

We've automated this completely using [this python script](https://gitlab.com/gitlab-com/gl-security/gl-redteam/gcp\_firewall\_enum) which will export the following:

我们已经使用[python脚本]（https://gitlab.com/gitlab-com/gl-security/gl-redteam/gcp \ _firewall \ _enum）完全自动化了这一点。

* CSV file showing instance, public IP, allowed TCP, allowed UDP

* CSV文件显示实例，公共IP，允许的TCP，允许的UDP
* nmap scan to target all instances on ports ingress allowed from the public internet (0.0.0.0/0)

* nmap扫描以瞄准公共互联网允许的端口上的所有实例（0.0.0.0/0）
* masscan to target the full TCP range of those instances that allow ALL TCP ports from the public internet (0.0.0.0/0)

* Masscan针对这些实例的完整TCP范围，这些实例允许所有TCP端口从公共Internet（0.0.0.0.0/0）

## Enumeration

##枚举

### Automatic Tools

###自动工具

* [**https://github.com/carlospolop/purplepanda**](https://github.com/carlospolop/purplepanda): Python script to enumerate resources and find privesc paths

*[** https：//github.com/carlospolop/purplepandaxdyddyd ander]
* [https://gitlab.com/gitlab-com/gl-security/security-operations/gl-redteam/gcp\_enum:](https://gitlab.com/gitlab-com/gl-security/security-operations/gl-redteam/gcp\_enum) Bash script to enumerate a GCP environment using gcloud cli and saving the results in

* [https://gitlab.com/gitlab-com/gl-security/security-operations/gl-redteam/gcp \ _enum：]（ 操作/gl-redteam/gcp \ _enum）bash脚本，使用gcloud cli列举GCP环境并将结果保存在
* [https://github.com/RhinoSecurityLabs/GCP-IAM-Privilege-Escalation:](https://github.com/RhinoSecurityLabs/GCP-IAM-Privilege-Escalation) Scripts to enumerate high IAM privileges and to escalate privileges in GCP abusing them (I couldn’t make run the enumerate script)

在GCP虐待它们中（我无法运行枚举脚本）
* [https://github.com/lyft/cartography:](https://github.com/lyft/cartography) Tool to enumerate and print in a graph resources and relations of different cloud platforms

* [https://github.com/lyft/cartography：（https://github.com/lyft/cartography）工具枚举和打印在图形资源和不同云平台的关系中
* [https://github.com/RyanJarv/awesome-cloud-sec:](https://github.com/RyanJarv/awesome-cloud-sec) This is a list of cloud security tools

* [https://github.com/ryanjarv/awesome-cloud-sec:]（https://github.com/ryanjarv/awesome-cloud-sec）

### IAM

| Description                                                                                                                        | Command                                                                                          |

| 描述| 命令|
| ---------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| List **roles**                                                                                                                     | `gcloud iam roles list --filter='etag:AA=='`                                                     |
| Get **description** and permissions of a role                                                                                      | gcloud iam roles describe roles/container.admin                                                  |
| Get iam **policy** of a **organisation**                                                                                           | `gcloud organizations get-iam-policy`                                                            |

| 获得一个**组织**的政策** | `gcloud组织Get-am-Policy` |
| Get iam **policy** of a **project**                                                                                                | `gcloud projects get-iam-policy <project-id>`                                                    |

| 获取**项目**的iam **政策** | `gcloud项目Get-am-Policy <project-id>`|
| Get iam **policy** of a **folder**                                                                                                 | `gcloud resource-manager folders get-iam-policy`                                                 |

| 获取**文件夹**的iam **政策** | `gcloud Resource-Manager文件夹Get-am-Policy` |
| Get **members** of a **group**                                                                                                     | `gcloud identity groups memberships search-transitive-memberships --group-email=email@group.com` |

| 获取**组的** group ** | `gcloud Identity组会员资格搜索传播会员 -  group-email = email@group.com` |
| Get **permissions** of a **role**                                                                                                  | `gcloud iam roles describe roles/accessapproval.approver`                                        |
| [**Testable permissions**](https://cloud.google.com/iam/docs/reference/rest/v1/permissions/queryTestablePermissions) on a resource | `gcloud iam list-testable-permissions --filter "NOT apiDisabled: true`                           |

| [**Testable permissions**](https://cloud.google.com/iam/docs/reference/rest/v1/permissions/queryTestablePermissions) on a resource | `gcloud iam list-testable-permissions --filter "NOT apiDisabled: true`                           |
| List of **grantable** **roles** for a resource                                                                                     | `gcloud iam list-grantable-roles <project URL>`                                                  |
| List **custom** **roles** on a project                                                                                             | `gcloud iam roles list --project $PROJECT_ID`                                                    |

| 列表**自定义** **角色**项目| `gcloud iam角色列表 - 项目$ project_id` |
| List **service accounts**                                                                                                          | `gcloud iam service-accounts list`                                                               |

| 列表**服务帐户** | `gcloud iam服务学会列表|

## Unauthenticated Attacks

##未经验证的攻击

{% content-ref url="gcp-buckets-brute-force-and-privilege-escalation.md" %}

{％content-ref url =“ gcp-buckets-buckets-brute-force-and-provilege-escalation.md”％}
[gcp-buckets-brute-force-and-privilege-escalation.md](gcp-buckets-brute-force-and-privilege-escalation.md)

[GCP-Buckets-Buckets-Force-and-Privilege-Escalation.md]（GCP-Buckets-Buckets-Buckets-force-worce and-Privilege-escalation.md）
{% endcontent-ref %}

#### Phishing

You could **OAuth phish** a user with high privileges.

您可以** oauth phish **具有高特权的用户。

#### Dorks

* **Github**: auth\_provider\_x509\_cert\_url extension:json

*** github **：auth \ _provider \ _x509 \ _cert \ _url扩展：json
## Generic GCP Security Checklists

##通用GCP安全清单

* [Google Cloud Computing Platform CIS Benchmark](https://www.cisecurity.org/cis-benchmarks/)

* [Google Cloud Computing平台CIS基准]（https://www.cisecurity.org/cis-benchmarks/）
* [https://github.com/doitintl/secure-gcp-reference](https://github.com/doitintl/secure-gcp-reference)

## Local Privilege Escalation / SSH Pivoting

##本地特权升级 / SSH枢纽

Supposing that you have compromised a VM in GCP, there are some **GCP privileges** that can allow you to **escalate privileges locally, into other machines and also pivot to other VMs**:

假设您已在GCP中损害了VM，则有一些** GCP特权**可以使您可以**在本地，其他机器中升级特权，并转向其他VMS **：

{% content-ref url="gcp-local-privilege-escalation-ssh-pivoting.md" %}

{％content-ref url =“ gcp-local-privilege-escalation-ssh-pivoting.md”％}
[gcp-local-privilege-escalation-ssh-pivoting.md](gcp-local-privilege-escalation-ssh-pivoting.md)

[GCP-Local-Provilege-sclation-ssh-pivoting.md]（GCP-Local-Provilege-sclacation-sch-pivoting.md）
{% endcontent-ref %}

If you have found some [**SSRF vulnerability in a GCP environment check this page**](../../pentesting-web/ssrf-server-side-request-forgery/#6440).

如果您在GCP环境中找到了一些[** SSRF漏洞，请检查此页面**]（../../ pentesting-web/ssrf-server-side-request-request-forgery/＃6440）。

## GCP Post Exploitation <a href="#cloud-privilege-escalation" id="cloud-privilege-escalation"></a>

## GCP邮政剥削<a href="#cloud-privilege-escalation" id="cloud-privilege-escalation"> </a>

### GCP Interesting Permissions <a href="#organization-level-iam-permissions" id="organization-level-iam-permissions"></a>

### GCP有趣的权限<a href="#organization-Level-iam-permissions" id="organization-level-level-iam-permissions"> </a>

The most common way once you have obtained some cloud credentials of has compromised some service running inside a cloud is to **abuse miss-configured privileges** the compromised account may have. So, the first thing you should do is to enumerate your privileges.

一旦您获得了一些云凭证，最常见的方法损害了云中运行的一些服务是**滥用虐待配置的特权**折衷的帐户可能拥有。 因此，您应该做的第一件事是列举您的特权。

Moreover, during this enumeration, remember that **permissions can be set at the highest level of "Organization"** as well.

此外，在此枚举中，请记住，**权限也可以设置为“组织” **的最高级别。

{% content-ref url="gcp-interesting-permissions/" %}

{％content-ref url =“ GCP Interesting-permissions/“％}
[gcp-interesting-permissions](gcp-interesting-permissions/)

[GCP Interresting-permissions]（GCP Interesting-permissions/）
{% endcontent-ref %}

### Bypassing access scopes <a href="#bypassing-access-scopes" id="bypassing-access-scopes"></a>

###绕过访问范围<a href="#bypassing-access-scopes" id="bypassing-access-copes"> </a>

When [access scopes](https://cloud.google.com/compute/docs/access/service-accounts#accesscopesiam) are used, the OAuth token that is generated for the computing instance (VM) will **have a** [**scope**](https://oauth.net/2/scope/) **limitation included**. However, you might be able to **bypass** this limitation and exploit the permissions the compromised account has.

当[访问范围]（https://cloud.google.com/compute/docs/access/service-accounts#accesscopesiam）时，为计算实例生成的oauth令牌（vm）将* *[**范围**]（https://oauth.net/2/scope/）**包括**。 但是，您也许可以**绕过**此限制并利用折衷帐户所拥有的权限。

The **best way to bypass** this restriction is either to **find new credentials** in the compromised host, to **find the service key to generate an OUATH token** without restriction or to **jump to a different VM less restricted**.

**绕过**这个限制的最佳方法是**在受损的主机中找到新的凭据**，以**找到无限制的服务键，或者**跳至其他 VM少限制**。

**Pop another box**

**弹出另一个盒子**

It's possible that another box in the environment exists with less restrictive access scopes. If you can view the output of `gcloud compute instances list --quiet --format=json`, look for instances with either the specific scope you want or the **`auth/cloud-platform`** all-inclusive scope.

环境中的另一个盒子可能存在限制性访问范围较小的框架。 如果您可以查看`gcloud计算实例列表的输出 -  quiet  -  format = json`，请查找具有所需的特定范围或**``auth/cloud-platform` **全包范围的实例。

Also keep an eye out for instances that have the default service account assigned (`PROJECT_NUMBER-compute@developer.gserviceaccount.com`).

还要注意已分配默认服务帐户的实例（`project_number-compute@developer.gserviceaccount.com`）。

**Find service account keys**

**查找服务帐户键**

Google states very clearly [**"Access scopes are not a security mechanism… they have no effect when making requests not authenticated through OAuth"**](https://cloud.google.com/compute/docs/access/service-accounts#accesscopesiam).

Google国家非常清楚[**“访问范围不是安全机制……在提出未通过Oauth“ **”验证的请求时，它们没有效果（https://cloud.google.com/compute/compute/docs/access/service-service- 帐户＃AccessCopesiam）。

Therefore, if you **find a** [**service account key**](https://cloud.google.com/iam/docs/creating-managing-service-account-keys) stored on the instance you can bypass the limitation. These are **RSA private keys** that can be used to authenticate to the Google Cloud API and **request a new OAuth token with no scope limitations**.

因此，如果您**找到一个** [**服务帐户密钥**]（https://cloud.google.com/iam/docs/creating-managing-managing-managing-service-account-keys）存储在实例上 绕过限制。 这些是** rsa私钥**，可用于对Google Cloud API进行身份验证，并且**请求新的OAuth令牌，没有范围限制**。

Check if any service account has exported a key at some point with:

检查任何服务帐户是否在某个时候导出了一个密钥：

```bash
for i in $(gcloud iam service-accounts list --format="table[no-heading](email)"); do
    echo Looking for keys for $i:
    gcloud iam service-accounts keys list --iam-account $i
done
```

These files are **not stored on a Compute Instance by default**, so you'd have to be lucky to encounter them. The default name for the file is `[project-id]-[portion-of-key-id].json`. So, if your project name is `test-project` then you can **search the filesystem for `test-project*.json`** looking for this key file.

这些文件**默认情况下不存储在计算实例上**，因此您必须幸运地遇到它们。 该文件的默认名称为`[project-id]  -  [键入键] .json`。 因此，如果您的项目名称为`test-project'，则可以**搜索文件系统以查找此密钥文件的`test-project*.json` ** **。

The contents of the file look something like this:

文件的内容看起来像这样：

```json
{
"type": "service_account",
"project_id": "[PROJECT-ID]",
"private_key_id": "[KEY-ID]",
"private_key": "-----BEGIN PRIVATE KEY-----\n[PRIVATE-KEY]\n-----END PRIVATE KEY-----\n",
"client_email": "[SERVICE-ACCOUNT-EMAIL]",
"client_id": "[CLIENT-ID]",
"auth_uri": "https://accounts.google.com/o/oauth2/auth",
"token_uri": "https://accounts.google.com/o/oauth2/token",
"auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs",
"client_x509_cert_url": "https://www.googleapis.com/robot/v1/metadata/x509/[SERVICE-ACCOUNT-EMAIL]"
}
```

Or, if **generated from the CLI** they will look like this:

或者，如果**从cli **产生，他们会看起来像这样：

```json
{
"name": "projects/[PROJECT-ID]/serviceAccounts/[SERVICE-ACCOUNT-EMAIL]/keys/[KEY-ID]",
"privateKeyType": "TYPE_GOOGLE_CREDENTIALS_FILE",
"privateKeyData": "[PRIVATE-KEY]",
"validAfterTime": "[DATE]",
"validBeforeTime": "[DATE]",
"keyAlgorithm": "KEY_ALG_RSA_2048"
}
```

If you do find one of these files, you can tell the **`gcloud` command to re-authenticate** with this service account. You can do this on the instance, or on any machine that has the tools installed.

如果您确实找到了以下文件之一，则可以告诉** gcloud`命令与此服务帐户重新认证**。 您可以在实例上或安装工具的任何机器上执行此操作。

```bash
gcloud auth activate-service-account --key-file [FILE]
```

You can now **test your new OAuth token** as follows:

您现在可以**测试新的Oauth代币**如下：

```bash
TOKEN=`gcloud auth print-access-token`
curl https://www.googleapis.com/oauth2/v1/tokeninfo?access_token=$TOKEN
```

You should see `https://www.googleapis.com/auth/cloud-platform` listed in the scopes, which means you are **not limited by any instance-level access scopes**. You now have full power to use all of your assigned IAM permissions.

您应该查看示波器中列出的https：// www.googleapis.com/auth/auth/cloud-platform`，这意味着您不受任何实例级级访问范围**的限制。 现在，您有权使用所有分配的IAM权限。

### Service account impersonation <a href="#service-account-impersonation" id="service-account-impersonation"></a>

###服务帐户模仿<a href="#service-account-impersonation" id="service-account-Impersonation"> </a>

Impersonating a service account can be very useful to **obtain new and better privileges**.

模仿服务帐户对于获得新的，更好的特权**可能非常有用。

There are three ways in which you can [impersonate another service account](https://cloud.google.com/iam/docs/understanding-service-accounts#impersonating\_a\_service\_account):

您可以通过三种方式[模仿另一个服务帐户]（https://cloud.google.com/iam/docs/understanding-service-accounts#impersonating \ _a \ _service \ _account）：

* Authentication **using RSA private keys** (covered [above](./#bypassing-access-scopes))

*身份验证**使用RSA私钥**（覆盖[上方]（./# bypassing-access-scopes））
* Authorization **using Cloud IAM policies** (covered [here](broken-reference/))

*授权**使用Cloud IAM策略**（涵盖[此处]（browt-reference/））
* **Deploying jobs on GCP services** (more applicable to the compromise of a user account)

***在GCP服务上部署工作**（更适用于用户帐户的妥协）

### Granting access to management console <a href="#granting-access-to-management-console" id="granting-access-to-management-console"></a>

###授予管理控制台的访问

Access to the [GCP management console](https://console.cloud.google.com) is **provided to user accounts, not service accounts**. To log in to the web interface, you can **grant access to a Google account** that you control. This can be a generic "**@gmail.com**" account, it does **not have to be a member of the target organization**.

访问[GCP管理控制台]（https://console.cloud.google.com）已**提供给用户帐户，而不是服务帐户**。 要登录到Web界面，您可以**授予您控制的Google帐户**的访问权限。 这可以是一个通用的“ **@gmail.com”帐户，它确实不必是目标组织的成员**。

To **grant** the primitive role of **Owner** to a generic "@gmail.com" account, though, you'll need to **use the web console**. `gcloud` will error out if you try to grant it a permission above Editor.

为了**授予**所有者**的原始角色**在一个通用的“@gmail.com”帐户中，您需要**使用Web Console **。 如果您尝试授予它的权限，则``gcloud'将出错。

You can use the following command to **grant a user the primitive role of Editor** to your existing project:

您可以使用以下命令来**授予用户编辑器的原始角色**给您现有项目：

```bash
gcloud projects add-iam-policy-binding [PROJECT] --member user:[EMAIL] --role roles/editor
```

If you succeeded here, try **accessing the web interface** and exploring from there.

如果您在这里成功，请尝试**访问Web界面**并从那里进行探索。

This is the **highest level you can assign using the gcloud tool**.

这是您可以使用gcloud工具**分配的**最高级别。

### Spreading to Workspace via domain-wide delegation of authority <a href="#spreading-to-g-suite-via-domain-wide-delegation-of-authority" id="spreading-to-g-suite-via-domain-wide-delegation-of-authority"></a>

###通过权威范围内的域委派<a href =“＃传播到g-suite-via-domain wide-delegation of WaTerority” id =“ veravor” 自权的范围范围授权“> </a>

[**Workspace**](https://gsuite.google.com) is Google's c**ollaboration and productivity platform** which consists of things like Gmail, Google Calendar, Google Drive, Google Docs, etc.

[** workspace **]（https://gsuite.google.com）是Google的c ** ollaboration and Productivity Platform **，它由Gmail，Google Calendar，Google Drive，Google Dive，Google Docs等组成。

**Service accounts** in GCP can be granted the **rights to programatically access user data** in Workspace by impersonating legitimate users. This is known as [domain-wide delegation](https://developers.google.com/admin-sdk/reports/v1/guides/delegation). This includes actions like **reading** **email** in GMail, accessing Google Docs, and even creating new user accounts in the G Suite organization.

**服务帐户**可以通过模仿合法用户来授予GCP中的** **在工作区中访问用户数据的权利。 这被称为[域内委托]（https://developers.google.com/admin-sdk/reports/v1/guides/delegation）。 这包括诸如Gmail中的**阅读** **电子邮件**之类的操作，访问Google文档，甚至在G Suite组织中创建新的用户帐户。

Workspace has [its own API](https://developers.google.com/gsuite/aspects/apis), completely separate from GCP. Permissions are granted to Workspace and **there isn't any default relation between GCP and Workspace**.

Workspace具有[其自己的API]（https://developers.google.com/gsuite/aspects/apis），与GCP完全分开。 授予工作空间的权限，** GCP和Workspace **之间没有任何默认关系。

However, it's possible to **give** a service account **permissions** over a Workspace user. If you have access to the Web UI at this point, you can browse to **IAM -> Service Accounts** and see if any of the accounts have **"Enabled" listed under the "domain-wide delegation" column**. The column itself may **not appear if no accounts are enabled** (you can read the details of each service account to confirm this). As of this writing, there is no way to do this programatically, although there is a [request for this feature](https://issuetracker.google.com/issues/116182848) in Google's bug tracker.

但是，可以**给**一个服务帐户**权限**与工作区用户相比。 如果此时可以访问Web UI，则可以浏览** iam->服务帐户**，看看是否有任何帐户在“域范围内委托”列中列出的“启用”列** ** 。 如果没有启用帐户**，则该列本身可能不会出现**（您可以阅读每个服务帐户的详细信息以确认此消息）。 截至撰写本文时，尽管有[https://issuetracker.google.com/issues/116182848）在Google的Bug Tracker中，但没有办法进行程序上的操作。

To create this relation it's needed to **enable it in GCP and also in Workforce**.

要创建此关系，需要**在GCP和劳动力中启用它。

#### Test Workspace access

####测试工作区访问

To test this access you'll need the **service account credentials exported in JSON** format. You may have acquired these in an earlier step, or you may have the access required now to create a key for a service account you know to have domain-wide delegation enabled.

要测试此访问，您需要以JSON **格式导出的**服务帐户。 您可能已经在较早的步骤中获取了这些，或者现在可能需要访问权限来为您知道的服务帐户创建一个启用域名委托的服务帐户的密钥。

This topic is a bit tricky… your service account has something called a "client\_email" which you can see in the JSON credential file you export. It probably looks something like `account-name@project-name.iam.gserviceaccount.com`. If you try to access Workforce API calls directly with that email, even with delegation enabled, you will fail. This is because the Workforce directory will not include the GCP service account's email addresses. Instead, to interact with Workforce, we need to actually impersonate valid Workforce users.

此主题有些棘手……您的服务帐户具有称为“客户端\ _Email”的内容，您可以在导出的JSON凭据文件中看到。 它可能看起来像``account-name@project-name.iam.gserviceaccount comp ocunter.com''。 如果您尝试通过该电子邮件直接访问Workforce API呼叫，即使启用了授权，您也会失败。 这是因为劳动力目录将不包括GCP服务帐户的电子邮件地址。 取而代之的是，要与劳动力互动，我们需要实际模仿有效的劳动力用户。

What you really want to do is to **impersonate a user with administrative access**, and then use that access to do something like **reset a password, disable multi-factor authentication, or just create yourself a shiny new admin account**.

您真正想做的是**模仿具有管理访问的用户**，然后使用该访问来执行**重置密码，禁用多因素身份验证，或者创建一个闪亮的新管理帐户* *。

Gitlab've created [this Python script](https://gitlab.com/gitlab-com/gl-security/gl-redteam/gcp\_misc/blob/master/gcp\_delegation.py) that can do two things - list the user directory and create a new administrative account. Here is how you would use it:

Gitlab've创建了[此Python脚本]（https://gitlab.com/gitlab-com/gl-security/gl-redteam/gcp \ _misc/blob/master/master/gcp _delegation.py），可以做两件事 -  列出用户目录并创建一个新的管理帐户。 这是您将如何使用它：

```bash
# Validate access only
./gcp_delegation.py --keyfile ./credentials.json \
    --impersonate steve.admin@target-org.com \
    --domain target-org.com

# List the directory
./gcp_delegation.py --keyfile ./credentials.json \
    --impersonate steve.admin@target-org.com \
    --domain target-org.com \
    --list

# Create a new admin account
./gcp_delegation.py --keyfile ./credentials.json \
    --impersonate steve.admin@target-org.com \
    --domain target-org.com \
    --account pwned
```

You can try this script across a range of email addresses to impersonate **various** **users**. Standard output will indicate whether or not the service account has access to Workforce, and will include a **random password for the new admin accoun**t if one is created.

您可以在一系列电子邮件地址中尝试此脚本，以模仿**各种** **用户**。 标准输出将指示该服务帐户是否可以访问劳动力，如果创建了一个新的管理员Accoun ** t的随机密码。

If you have success creating a new admin account, you can log on to the [Google admin console](https://admin.google.com) and have full control over everything in G Suite for every user - email, docs, calendar, etc. Go wild.

如果您成功创建了一个新的管理帐户，则可以登录[Google Admin Console]（https://admin.google.com），并对每个用户的G Suite中的所有内容完全控制 - 电子邮件，电子邮件，文档，日历 等等。疯了。

### Looting

Another promising way to **escalate privileges inside the cloud is to enumerate as much sensitive information as possible** from the services that are being used. Here you can find some enumeration recommendations for some GCP services, but more could be used so feel free to submit PRs indicating ways to enumerate more services:

**升级云中特权的另一种有希望的方法是，从所使用的服务中列举了尽可能多的敏感信息**。 在这里，您可以为某些GCP服务找到一些枚举建议，但可以使用更多建议，因此可以随意提交指示枚举更多服务的方法：

{% hint style="info" %}

{％提示样式=“ info”％}
Note that you can enumerate most resources with `list` (list items of that type), `describe` (describe parent and children items) and `get-iam-policy` (get policy attached to that specific resource).

请注意，您可以用``列表''（该类型的列表项目），``描述''（描述父母和子女项目）和`get-am-policy'列举大多数资源（获取该特定资源附加策略）。
{% endhint %}

There is a gcloud API endpoint that aims to **list all the resources the accessible from the used user accoun**t, it's in alpha bet and only supports a couple of resources, but maybe in the future you can list all you have access to with it: [https://helpmanual.io/man1/gcloud\_alpha\_resources\_list/](https://helpmanual.io/man1/gcloud\_alpha\_resources\_list/)

有一个gcloud API端点，旨在**列出所有可从二手用户访问** t访问的资源，它在alpha bet中仅支持一些资源，但也许将来您可以列出所有拥有的访问权限 与之：[https://helpmanual.io/man1/gcloud \ _alpha \ _RESources \ _list/]（

{% content-ref url="gcp-buckets-enumeration.md" %}

{％content-ref url =“ gcp-buckets-enumeration.md”％}
[gcp-buckets-enumeration.md](gcp-buckets-enumeration.md)
{% endcontent-ref %}

{% content-ref url="gcp-compute-enumeration.md" %}
[gcp-compute-enumeration.md](gcp-compute-enumeration.md)
{% endcontent-ref %}

{% content-ref url="gcp-network-enumeration.md" %}

{％content-ref url =“ gcp-network-enumeration.md”％}
[gcp-network-enumeration.md](gcp-network-enumeration.md)

[GCP-NETWORK-ENUMERATY.MD]（GCP-NETWORK-ENUMERATION.MD）
{% endcontent-ref %}

{% content-ref url="gcp-kms-and-secrets-management-enumeration.md" %}

{％content-ref url =“ gcp-kms and-secrets-management-enumeration.md”％}
[gcp-kms-and-secrets-management-enumeration.md](gcp-kms-and-secrets-management-enumeration.md)

[gcp-kms和screts-management-enumeration.md]（gcp-kms-kms-secrets-secrets-management-enumeration.md）{% endcontent-ref %}

{% content-ref url="gcp-databases-enumeration.md" %}
[gcp-databases-enumeration.md](gcp-databases-enumeration.md)
{% endcontent-ref %}

{% content-ref url="gcp-serverless-code-exec-services-enumeration.md" %}
[gcp-serverless-code-exec-services-enumeration.md](gcp-serverless-code-exec-services-enumeration.md)
{% endcontent-ref %}

{% content-ref url="gcp-looting.md" %}

{％content-ref url =“ gcp-looting.md”％}
[gcp-looting.md](gcp-looting.md)
{% endcontent-ref %}

### Persistance

{% content-ref url="gcp-persistance.md" %}
[gcp-persistance.md](gcp-persistance.md)
{% endcontent-ref %}

## Capture gcloud, gsutil... network

##捕获gcloud，gsutil ...网络

```bash
gcloud config set proxy/address 127.0.0.1
gcloud config set proxy/port 8080
gcloud config set proxy/type http
gcloud config set auth/disable_ssl_validation True

# If you don't want to completely disable ssl_validation use:
gcloud config set core/custom_ca_certs_file cert.pem

# Back to normal
gcloud config unset proxy/address
gcloud config unset proxy/port
gcloud config unset proxy/type
gcloud config unset auth/disable_ssl_validation
gcloud config unset core/custom_ca_certs_file
```

## References

* [https://about.gitlab.com/blog/2020/02/12/plundering-gcp-escalating-privileges-in-google-cloud-platform/](https://about.gitlab.com/blog/2020/02/12/plundering-gcp-escalating-privileges-in-google-cloud-platform/)

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
