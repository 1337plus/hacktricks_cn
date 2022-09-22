

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


# Types of services

＃服务类型

## Container services

##容器服务

Services that fall under container services have the following characteristics:

属于集装箱服务的服务具有以下特征：

* The service itself runs on **separate infrastructure instances**, such as EC2.

*该服务本身在**单独的基础架构实例**上运行，例如EC2。
* **AWS** is responsible for **managing the operating system and the platform**.

*** AWS **负责**管理操作系统和平台**。
* A managed service is provided by AWS, which is typically the service itself for the **actual application which are seen as containers**.

*AWS提供了托管服务，该服务通常是**实际应用程序的服务本身，被视为容器**。
* As a user of these container services, you have a number of management and security responsibilities, including **managing network access security, such as network access control list rules and any firewalls**.

*作为这些容器服务的用户，您有许多管理和安全责任，包括**管理网络访问安全性，例如网络访问控制列表规则和任何防火墙**。
* Also, platform-level identity and access management where it exists.

*此外，在存在的地方，平台级别的身份和访问管理。
* **Examples** of AWS container services include Relational Database Service, Elastic Mapreduce, and Elastic Beanstalk.

*** AWS容器服务的示例**包括关系数据库服务，Elastic MapReduce和Elastic Beanstalk。

## Abstract Services

##抽象服务

* These services are **removed, abstracted, from the platform or management layer which cloud applications are built on**.

*这些服务被**从云应用程序建立在**的平台或管理层中删除，抽象。
* The services are accessed via endpoints using AWS application programming interfaces, APIs.

*使用AWS应用程序编程接口，API通过端点访问服务。
* The **underlying infrastructure, operating system, and platform is managed by AWS**.

***基础架构，操作系统和平台由AWS **管理。
* The abstracted services provide a multi-tenancy platform on which the underlying infrastructure is shared.

*抽象服务提供了一个多租赁平台，在该平台上共享了基础基础架构。
* **Data is isolated via security mechanisms**.

***数据通过安全机制隔离**。
* Abstract services have a strong integration with IAM, and **examples** of abstract services include S3, DynamoDB, Amazon Glacier, and SQS.

*抽象服务与IAM具有很强的集成，并且**示例**抽象服务包括S3，DynamoDB，Amazon Glacier和SQS。

# IAM - Identity and Access Management

＃iam-身份和访问管理

IAM is the service that will allow you to manage **Authentication**, **Authorization** and **Access Control** inside your AWS account.

IAM是允许您管理**身份验证**，**授权**和**访问控制**的服务。

* **Authentication** - Process of defining an identity and the verification of that identity. This process can be subdivided in: Identification and verification.

***身份验证**  - 定义身份和验证该身份的过程。 该过程可以细分为：识别和验证。
* **Authorization** - Determines what an identity can access within a system once it's been authenticated to it.

***授权**  - 确定系统在系统身份验证后可以在系统中访问什么。
* **Access Control** - The method and process of how access is granted to a secure resource

***访问控制**  - 授予访问权限的方法和过程

IAM can be defined by its ability to manage, control and govern authentication, authorization and access control mechanisms of identities to your resources within your AWS account.

IAM可以通过其管理，控制和管理身份身份的身份验证，授权和访问权限控制机制的能力来定义，身份在AWS帐户中的资源。

## Users

##用户

This could be a **real person** within your organization who requires access to operate and maintain your AWS environment. Or it could be an account to be used by an **application** that may require permissions to **access** your **AWS** resources **programmatically**. Note that **usernames must be unique**.

这可能是您组织中的一个真实人**，需要访问和维护您的AWS环境。 否则可能是一个帐户**应用程序**可能需要使用权限**访问权限**您的** aws **资源**以编程方式**。 请注意，**用户名必须是唯一的**。

### CLI

### CLI

* **Access Key ID**: 20 random uppercase alphanumeric characters like AKHDNAPO86BSHKDIRYT

***访问密钥ID **：20个随机大写字母数字字符，例如akhdnapo86bshkdiryt
* **Secret access key ID**: 40 random upper and lowercase characters: S836fh/J73yHSb64Ag3Rkdi/jaD6sPl6/antFtU (It's not possible to retrieve lost secret access key IDs).

***秘密访问密钥ID **：40个随机上下和小写字符：S836FH/J73YHSB64AG3RKDI/JAD6SPL6/ANTFTU（无法检索丢失的秘密访问密钥ID）。

Whenever you need to **change the Access Key** this is the process you should follow:\

每当您需要**更改访问密钥**时，这是您应该关注的过程：\
_Create a new access key -> Apply the new key to system/application -> mark original one as inactive -> Test and verify new access key is working -> Delete old access key_

_创建一个新的访问键 - >将新键应用于系统/应用程序 - >将原始键标记为无活动 - >测试和验证新访问密钥正在工作 - >删除旧访问键_

**MFA** is **supported** when using the AWS **CLI**.

** MFA **使用AWS ** cli **时得到** **。

## Groups

These are objects that **contain multiple users**. Permissions can be assigned to a user or inherit form a group. **Giving permission to groups and not to users the secure way to grant permissions**.

这些对象**包含多个用户**。 可以将权限分配给用户或继承一个组。 **授予小组的许可，而不是向用户提供授予权限的安全方法**。

## Roles

Roles are used to grant identities a set of permissions. **Roles don't have any access keys or credentials associated with them**. Roles are usually used with resources (like EC2 machines) but they can also be useful to grant **temporary privileges to a user**. Note that when for example an EC2 has an IAM role assigned, instead of saving some keys inside the machine, dynamic temporary access keys will be supplied by the IAM role to handle authentication and determine if access is authorized.

角色用于授予身份一组权限。 **角色没有与之关联的任何访问密钥或凭据**。 角色通常与资源（例如EC2机器）一起使用，但它们也可以授予用户**临时特权。 请注意，例如，当EC2具有分配IAM角色时，而不是在计算机内保存一些键，就会由IAM角色提供动态临时访问密钥以处理身份验证并确定是否授权访问。

An IAM role consists of **two types of policies**: A **trust policy**, which cannot be empty, defining who can assume the role, and a **permissions policy**, which cannot be empty, defining what they can access.

IAM角色由**两种类型的策略组成**：A **信任政策**，不能为空，定义谁可以扮演角色，而**权限策略**不能为空，定义什么 他们可以访问。

### AWS Security Token Service (STS)

### AWS安全令牌服务（STS）

This is a web service that enables you to **request temporary, limited-privilege credentials** for AWS Identity and Access Management (IAM) users or for users that you authenticate (federated users).

这是一项Web服务，使您可以**请求临时，有限的特权凭据**，以供AWS身份和访问管理（IAM）用户或您身份验证的用户（联合用户）。

## Policies

### Policy Permissions

###政策权限

Are used to assign permissions. There are 2 types:

用于分配权限。 有两种类型：

* AWS managed policies (preconfigured by AWS)

* AWS托管政策（由AWS预先配置）
* Customer Managed Policies: Configured by you. You can create policies based on AWS managed policies (modifying one of them and creating your own), using the policy generator (a GUI view that helps you granting and denying permissions) or writing  your own..

*客户托管政策：由您配置。 您可以使用策略生成器（一种有助于您授予和拒绝权限的GUI视图）或编写自己的策略生成器（一种GUI视图），可以根据AWS托管策略（修改其中之一并创建自己的一项）制定策略。

By **default access** is **denied**, access will be granted if an explicit role has been specified. \

通过**默认访问**被**被拒绝**，如果指定了明确的角色，将授予访问权限。 \ \
If **single "Deny" exist, it will override the "Allow"**, except for requests that use the AWS account's root security credentials (which are allowed by default).

如果存在**单个“否认”，则它将覆盖“允许” **，除了使用AWS帐户的root Security凭据（默认情况下允许）的请求。

```javascript
{
    "Version": "2012-10-17",  //Version of the policy
    "Statement": [  //Main element, there can be more than 1 entry in this array
        {
            "Sid": "Stmt32894y234276923" //Unique identifier (optional)
            "Effect": "Allow", //Allow or deny
            "Action": [  //Actions that will be allowed or denied
                "ec2:AttachVolume",
                "ec2:DetachVolume"
            ], 
            "Resource": [ //Resource the action and effect will be applied to
                "arn:aws:ec2:*:*:volume/*",
                "arn:aws:ec2:*:*:instance/*"
            ],
            "Condition": { //Optional element that allow to control when the permission will be effective
                "ArnEquals": {"ec2:SourceInstanceARN": "arn:aws:ec2:*:*:instance/instance-id"}
            }
        }
    ]
}
```

### Inline Policies

###内联策略

This kind of policies are **directly assigned** to a user, group or role. Then, they not appear in the Policies list as any other one can use them.\

这种策略是直接分配给用户，组或角色的。 然后，它们不会出现在策略列表中，因为其他任何人都可以使用它们。
Inline policies are useful if you want to **maintain a strict one-to-one relationship between a policy and the identity** that it's applied to. For example, you want to be sure that the permissions in a policy are not inadvertently assigned to an identity other than the one they're intended for. When you use an inline policy, the permissions in the policy cannot be inadvertently attached to the wrong identity. In addition, when you use the AWS Management Console to delete that identity, the policies embedded in the identity are deleted as well. That's because they are part of the principal entity.

如果您想**保持严格的一对一关系与应用程序的身份**之间的严格关系，则内线政策将很有用。 例如，您要确保策略中的权限并未无意中分配给其预定的身份。 当您使用内联策略时，策略中的权限不能无意间附加到错误的身份。 此外，当您使用AWS管理控制台删除该身份时，嵌入身份中的策略也将被删除。 那是因为它们属于主要实体。

### S3 Bucket Policies

Can only be applied to S3 Buckets. They contains an attribute called 'principal' that can be: IAM users, Federated users, another AWS account, an AWS service. P**rincipals define who/what should be allowed or denied access to various S3 resources.**

只能应用于S3桶。 它们包含一个称为“委托人”的属性，可以是：IAM用户，联合用户，另一个AWS帐户，AWS服务。 p ** rincipals定义谁/应该允许或拒绝访问各种S3资源。**

## Multi-Factor Authentication

##多因素身份验证

It's used to **create an additional factor for authentication** in addition to your existing methods, such as password, therefore, creating a multi-factor level of authentication.\

它用于**创建身份验证的附加因素**除了您现有的方法（例如密码），因此创建多因素的身份验证级别。\ \ \
You can use a **free virtual application or a physical device**. You can use apps like google authentication for free to activate a MFA in AWS.

您可以使用**免费虚拟应用程序或物理设备**。 您可以免费使用Google Authentication之类的应用程序来激活AWS中的MFA。

## Identity Federation

##身份联合会

Identity federation **allows users from identity providers which are external** to AWS to access AWS resources securely without having to supply AWS user credentials from a valid IAM user account. \

身份联合会**允许来自身份提供商的用户外部**，可以安全地访问AWS资源，而无需从有效的IAM用户帐户提供AWS用户凭据。 \ \
An example of an identity provider can be your own corporate Microsoft Active Directory(via SAML) or OpenID services (like Google). Federated access will then allow the users within it to access AWS.\

身份提供商的一个示例可以是您自己的Microsoft Active Directory（通过SAML）或OpenID服务（例如Google）。 然后，联合访问将允许其内部的用户访问AWS。
AWS Identity Federation connects via IAM roles.

AWS身份联合会通过IAM角色连接。

### Cross Account Trusts and Roles

###交叉帐户信托和角色

**A user** (trusting) can create a Cross Account Role with some policies and then, **allow another user** (trusted) to **access his account** but only h**aving the access indicated in the new role policies**. To create this, just create a new Role and select Cross Account Role. Roles for Cross-Account Access offers two options. Providing access between AWS accounts that you own, and providing access between an account that you own and a third party AWS account.\

**用户**（信任）可以使用某些策略创建一个跨帐户角色，然后，**允许另一个用户**（可信赖）**访问他的帐户**，但只有h ** aving h ** aving of the the the访问的访问 新角色政策**。 为了创建这个问题，只需创建一个新角色并选择跨帐户角色。 跨账户访问的角色提供了两种选择。 提供您拥有的AWS帐户之间的访问权限，并在拥有的帐户和第三方AWS帐户之间提供访问。\ \
It's recommended to **specify the user who is trusted and not put some generic thing** because if not, other authenticated users like federated users will be able to also abuse this trust.

建议**指定受信任并不放置某些通用物品的用户**，因为如果没有，其他经过验证的用户（如联合用户）也将能够滥用此信任。

### AWS Simple AD

Not supported:

不支持：

* Trust Relations

*信任关系
* AD Admin Center

*广告管理中心
* Full PS API support
* AD Recycle Bin

*广告回收箱
* Group Managed Service Accounts

*小组托管服务帐户
* Schema Extensions
* No Direct access to OS or Instances

*无法直接访问OS或实例

### Web Federation or OpenID Authentication

### Web联合会或OpenID身份验证

The app uses the AssumeRoleWithWebIdentity to create temporary credentials. However this doesn't grant access to the AWS console, just access to resources within AWS.

该应用程序使用asherolewithwebidentity创建临时凭据。 但是，这不会授予对AWS控制台的访问权限，只需访问AWS中的资源即可。

## Other IAM options

##其他IAM选项

* You can **set a password policy setting** options like minimum length and password requirements.

*您可以**设置密码策略设置**选项，例如最小长度和密码要求。
* You can **download "Credential Report"** with information about current credentials (like user creation time, is password enabled...). You can generate a credential report as often as once every **four hours**.

*您可以**下载“凭据报告” **，其中包含有关当前凭据的信息（例如用户创建时间，启用密码...）。 您可以每次**四个小时一次地生成凭据报告。

# KMS - Key Management Service

＃KMS-密钥管理服务

AWS Key Management Service (AWS KMS) is a managed service that makes it easy for you to **create and control **_**customer master keys**_** (CMKs)**, the encryption keys used to encrypt your data. AWS KMS CMKs are **protected by hardware security modules** (HSMs)

AWS密钥管理服务（AWS KMS）是一项托管服务，使您可以轻松地**创建和控制** _ **客户主键** _ **（cmks）**，这是用于加密您的加密密钥 数据。 AWS KMS CMK受硬件安全模块的保护**（HSMS）

KMS uses **symmetric cryptography**. This is used to **encrypt information as rest** (for example, inside a S3). If you need to **encrypt information in transit** you need to use something like **TLS**.\

KMS使用**对称加密**。 这用于将信息加密为REST **（例如，在S3内部）。 如果您需要**在运输中加密信息**，则需要使用** tls **。
KMS is a **region specific service**.

KMS是**特定于区域的服务**。

**Administrators at Amazon do not have access to your keys**. They cannot recover your keys and they do not help you with encryption of your keys. AWS simply administers the operating system and the underlying application it's up to us to administer our encryption keys and administer how those keys are used.

**亚马逊的管理员无法访问您的密钥**。 他们无法恢复您的钥匙，也无法帮助您加密密钥。 AWS只是管理操作系统和基础应用程序，我们可以管理我们的加密密钥并管理如何使用这些键。

**Customer Master Keys** (CMK): Can encrypt data up to 4KB in size. They are typically used to create, encrypt, and decrypt the DEKs (Data Encryption Keys). Then the DEKs are used to encrypt the data.

**客户主键**（CMK）：可以将数据加密至4KB的大小。 它们通常用于创建，加密和解密deks（数据加密密钥）。 然后，杜克斯用于加密数据。

A customer master key (CMK) is a logical representation of a master key in AWS KMS. In addition to the master key's identifiers and other metadata, including its creation date, description, and key state, a **CMK contains the key material which used to encrypt and decrypt data**. When you create a CMK, by default, AWS KMS generates the key material for that CMK. However, you can choose to create a CMK without key material and then import your own key material into that CMK.

客户主密钥（CMK）是AWS KMS中主密钥的逻辑表示。 除了主密钥的标识符和其他元数据（包括其创建日期，描述和密钥状态）外，A ** cmk还包含用于加密和解密数据**的关键材料**。 当您创建CMK时，默认情况下，AWS KMS会为该CMK生成关键材料。 但是，您可以选择在没有密钥材料的情况下创建CMK，然后将自己的关键材料导入该CMK。

There are 2 types of master keys:

主键有两种类型：

* **AWS managed CMKs: Used by other services to encrypt data**. It's used by the service that created it in a region. They are created the first time you implement the encryption in that service. Rotates every 3 years and it's not possible to change it.

*** AWS托管CMK：其他服务用于加密数据**。 它是由在区域中创建它的服务使用的。 它们是在您第一次实施该服务中的加密时创建的。 每3年旋转一次，无法更改它。
* **Customer manager CMKs**: Flexibility, rotation, configurable access and key policy. Enable and disable keys.

***客户经理CMKS **：灵活性，旋转，可配置的访问和关键策略。 启用和禁用密钥。

**Envelope Encryption** in the context of Key Management Service (KMS): Two-tier hierarchy system to **encrypt data with data key and then encrypt data key with master key**.

**信封加密**在密钥管理服务（KMS）的上下文中：两层层次结构系统**使用数据密钥加密数据，然后使用主密钥加密数据密钥。

## Key Policies

##关键政策

These defines **who can use and access a key in KMS**. By default root user has full access over KMS, if you delete this one, you need to contact AWS for support.

这些定义**可以使用和访问kms **的密钥。 默认情况下，root用户在kms上具有完整的访问权限，如果删除此词，则需要与AWS联系以寻求支持。

Properties of a policy:

政策的属性：

* JSON based document

*基于JSON的文件
* Resource --> Affected resources (can be "\*")

*资源 - >受影响的资源（可以是“ \*”）
* Action --> kms:Encrypt, kms:Decrypt, kms:CreateGrant ... (permissions)

*动作 - > KMS：加密，KMS：解密，KMS：CreateGrant ...（权限）
* Effect --> Allow/Deny

*效果 - >允许/拒绝
* Principal --> arn affected

*校长 - >受影响的ARN
* Conditions (optional) --> Condition to give the permissions

*条件（可选） - >提供权限的条件

Grants:

* Allow to delegate your permissions to another AWS principal within your AWS account. You need to create them using the AWS KMS APIs. It can be indicated the CMK identifier, the grantee principal and the required level of opoeration (Decrypt, Encrypt, GenerateDataKey...)

*允许将您的权限委托给您的AWS帐户中的另一个AWS本金。 您需要使用AWS KMS API创建它们。 可以指示CMK标识符，受赠人本金和所需的Opoeration（解密，加密，生成的...）
* After the grant is created a GrantToken and a GratID are issued

*在赠款创建后，授予了拨款并发出拨款

Access:

使用权：

* Via key policy -- If this exist, this takes precedent over the IAM policy, s the IAM olicy is not used

*通过关键策略 - 如果存在，这比IAM策略有先例，S iam Olicy不使用
* Via IAM policy
* Via grants

## Key Administrators

##关键管理员

Key administrator by default:

默认情况下的密钥管理员：

* Have access to manage KMS but not to encrypt or decrypt data

*可以访问管理KM，但不能加密或解密数据
* Only IAM users and roles can be added to Key Administrators list (not groups)

*只有IAM用户和角色可以添加到关键管理员列表（不是组）
* If external CMK is used, Key Administrators have the permission to import key material

*如果使用了外部CMK，关键管理员有权导入关键材料

## Rotation of CMKs

## CMK旋转

* The longer the same key is left in place, the more data is encrypted with that key, and if that key is breached, then the wider the blast area of data is at risk. In addition to this, the longer the key is active, the probability of it being breached increases.

*剩下相同的键的时间越长，该键加密的数据越多，如果键违反了该键，则数据的爆炸面积越宽。 除此之外，钥匙的活动时间越长，其违反键的可能性会增加。
* **KMS rotate customer keys every 365 days** (or you can perform the process manually whenever you want) and **keys managed by AWS every 3 years** and this time it cannot be changed.

*** KMS每365天旋转一次客户键**（或者您可以随时手动执行该过程）和**每3年管理的密钥** **，这次无法更改。
* **Older keys are retained** to decrypt data that was encrypted prior to the rotation

***保留了较旧的键**到旋转之前已加密的解密数据
* In a break, rotating the key won't remove the threat as it will be possible to decrypt all the data encrypted with the compromised key. However, the **new data will be encrypted with the new key**.

*在休息时，旋转钥匙不会消除威胁，因为可以解密所有用折衷的键加密的数据。 但是，**新数据将使用新密钥**进行加密。
* If **CMK** is in state of **disabled** or **pending** **deletion**, KMS will **not perform a key rotation** until the CMK is re-enabled or deletion is cancelled.

*如果** cmk **处于禁用状态**或**待处理** **删除**，KMS将**不执行键旋转**，直到重新启用CMK或取消删除 。

### Manual rotation

###手动旋转

* A **new CMK needs to be created**, then, a new CMK-ID is created, so you will need to **update** any **application** to **reference** the new CMK-ID.

*A **需要创建新的CMK **，然后创建一个新的CMK-ID，因此您需要**更新**任何**应用程序** **参考** 。
* To do this process easier you can **use aliases to refer to a key-id** and then just update the key the alias is referring to.

*为了更轻松地完成此过程，您可以**使用别名来引用键入ID **，然后只需更新别名所指的键即可。
* You need to **keep old keys to decrypt old files** encrypted with it.

*您需要**保留旧密钥以解密旧文件**对其进行了加密。

You can import keys from your on-premises key infrastructure .

您可以从本地密钥基础架构中导入密钥。

## Other information

##其他信息

KMS is priced per number of encryption/decryption requests received from all services per month.

KMS的定价是每月收到所有服务的加密/解密请求。

KMS has full audit and compliance **integration with CloudTrail**; this is where you can audit all changes performed on KMS.

KMS具有完整的审计和合规性**与CloudTrail的集成**； 在这里，您可以在这里审核所有在KMS上执行的更改。

With KMS policy you can do the following:

使用KMS策略，您可以执行以下操作：

* Limit who can create data keys and which services have access to use these keys

*限制谁可以创建数据键，哪些服务可以访问使用这些键
* Limit systems access to encrypt only, decrypt only or both

*限制系统仅访问加密，仅解密或两者兼而有之
* Define to enable systems to access keys across regions (although it is not recommended as a failure in the region hosting KMS will affect availability of systems in other regions).

*定义以使系统能够访问跨区域的密钥（尽管不建议将其作为托管KMS的区域的故障会影响其他地区的系统的可用性）。

You cannot synchronize or move/copy keys across regions; you can only define rules to allow access across region.

您不能同步或跨区域移动/复制键； 您只能定义规则以允许跨区域访问。

# S3

Amazon S3 is a service that allows you **store important amounts of data**.

Amazon S3是一项允许您**存储重要数据**的服务。

Amazon S3 provides multiple options to achieve the **protection** of data at REST. The options include **Permission** (Policy), **Encryption** (Client and Server Side), **Bucket Versioning** and **MFA** **based delete**. The **user can enable** any of these options to achieve data protection. **Data replication** is an internal facility by AWS where **S3 automatically replicates each object across all the Availability Zones** and the organization need not enable it in this case.

Amazon S3提供了多种选择，以实现静止数据的**保护**。 选项包括**权限**（策略），**加密**（客户端和服务器端），**桶装版**和** MFA ** **基于delete **。 **用户可以启用**这些选项以实现数据保护。 **数据复制**是AWS的内部设施，其中** S3自动在所有可用性区域中复制每个对象**，并且在这种情况下，组织不需要启用它。

With resource-based permissions, you can define permissions for sub-directories of your bucket separately.

借助基于资源的权限，您可以分别为存储桶的子目录定义权限。

## S3 Access logs

## S3访问日志

It's possible to **enable S3 access login** (which by default is disabled) to some bucket and save the logs in a different bucket to know who is accessing the bucket. The source bucket and the target bucket (the one is saving the logs needs to be in the same region.

可以**启用S3访问登录**（默认情况下是禁用）到某个存储桶中，并将日志保存在其他存储桶中，以了解谁在访问该存储桶。 源存储桶和目标存储桶（一个保存日志需要在同一区域中。

## S3 Encryption Mechanisms

## S3加密机制

**DEK means Data Encryption Key** and is the key that is always generated and used to encrypt data.

** DEK表示数据加密密钥**，并且是始终生成并用于加密数据的密钥。

**Server-side encryption with S3 managed keys, SSE-S3:** This option requires minimal configuration and all management of encryption keys used are managed by AWS. All you need to do is to **upload your data and S3 will handle all other aspects**. Each bucket in a S3 account is assigned a bucket key.

**使用S3托管密钥，SSE-S3：**此选项需要最小的配置，并且所使用的加密密钥的所有管理均由AWS管理。 您需要做的就是**上传数据，而S3将处理所有其他方面**。 S3帐户中的每个存储桶都分配了一个存储键键。

* Encryption:

*加密：
  * Object Data + created plaintext DEK --> Encrypted data (stored inside S3)

*对象数据 +创建的明文DEK->加密数据（存储在S3中）
  * Created plaintext DEK + S3 Master Key --> Encrypted DEK (stored inside S3) and plain text is deleted from memory

*创建的明文DEK + S3 Master Key->加密的DEK（存储在S3中）和纯文本从内存中删除
* Decryption:

*解密：
  * Encrypted DEK + S3 Master Key --> Plaintext DEK

*加密DEK + S3 MASTER KEY->明文DEK
  * Plaintext DEK + Encrypted data --> Object Data

*明文DEK +加密数据 - >对象数据

Please, note that in this case **the key is managed by AWS** (rotation only every 3 years). If you use your own key you willbe able to rotate, disable and apply access control.

请注意，在这种情况下**钥匙由AWS **管理（仅每3年轮换一次）。 如果您使用自己的密钥，则可以旋转，禁用并应用访问控件。

**Server-side encryption with KMS managed keys, SSE-KMS:** This method allows S3 to use the key management service to generate your data encryption keys. KMS gives you a far greater flexibility of how your keys are managed. For example, you are able to disable, rotate, and apply access controls to the CMK, and order to against their usage using AWS Cloud Trail.

**使用KMS托管密钥，SSE-KMS的服务器端加密：**此方法允许S3使用密钥管理服务来生成数据加密密钥。 KMS可以使您更加灵活地管理钥匙。 例如，您能够禁用，旋转并将访问控件应用于CMK，并使用AWS Cloud Trail命令其使用。

* Encryption:

*加密：
  * S3 request data keys from KMS CMK

* S3请求数据键来自KMS CMK
  * KMS uses a CMK to generate the pair DEK plaintext and DEK encrypted and send them to S£

* KMS使用CMK生成对DEK纯文本并加密DEK并将其发送到S£
  * S3 uses the paintext key to encrypt the data, store the encrypted data and the encrypted key and deletes from memory the plain text key

* S3使用Paintext键来加密数据，存储加密数据以及已加密的键并从内存中删除纯文本键
* Decryption:

*解密：
  * S3 ask to KMS to decrypt the encrypted data key of the object

* S3要求KMS解密对象的加密数据键
  * KMS decrypt the data key with the CMK and send it back to S3

* KMS用CMK解密数据密钥，然后将其发送回S3
  * S3 decrypts the object data

* S3解密对象数据

**Server-side encryption with customer provided keys, SSE-C:** This option gives you the opportunity to provide your own master key that you may already be using outside of AWS. Your customer-provided key would then be sent with your data to S3, where S3 would then perform the encryption for you.

**与客户提供的服务器端加密，提供密钥，SSE-C：**此选项使您有机会提供自己的主密钥，您可能已经在AWS之外使用了这些选项。 然后，您的客户提供的密钥将与您的数据一起发送到S3，然后S3将为您执行加密。

* Encryption:

*加密：
  * The user sends the object data + Customer key to S3

*用户将对象数据 +客户密钥发送到S3
  * The customer key is used to encrypt the data and the encrypted data is stored

*客户密钥用于加密数据并存储加密数据
  * a salted HMAC value of the customer key is stored also for future key validation

*客户密钥的咸HMAC值也存储用于将来的密钥验证
  * the customer key is deleted from memory

*从内存中删除了客户密钥
* Decryption:

*解密：
  * The user send the customer key

*用户发送客户密钥
  * The key is validated against the HMAC value stored

*密钥已针对存储的HMAC值验证
  * The customer provided key is then used to decrypt the data

*然后使用客户提供的密钥来解密数据

**Client-side encryption with KMS, CSE-KMS:** Similarly to SSE-KMS, this also uses the key management service to generate your data encryption keys. However, this time KMS is called upon via the client not S3. The encryption then takes place client-side and the encrypted data is then sent to S3 to be stored.

**使用KMS，CSE-KMS的客户端加密：**与SSE-KMS类似，这也使用密钥管理服务来生成数据加密密钥。 但是，这次是通过客户而不是S3调用KMS。 然后进行加密进行客户端，然后将加密数据发送到存储S3。

* Encryption:

*加密：
  * Client request for a data key to KMS

*客户要求向KMS的数据密钥请求
  * KMS returns the plaintext DEK and the encrypted DEK with the CMK

* KMS返回具有CMK的明文DEK和加密的DEK
  * Both keys are sent back

*两个键都发送回
  * The client then encrypts the data with the plaintext DEK and send to S3 the encrypted data + the encrypted DEK (which is saved as metadata of the encrypted data inside S3)

*客户端然后将数据加密使用明文DEK并将其发送到S3，并将加密数据 +加密DEK发送（将其保存为S3内加密数据的元数据）
* Decryption:

*解密：
  * The encrypted data with the encrypted DEK is sent to the client

*带有加密DEK的加密数据发送给客户
  * The client asks KMS to decrypt the encrypted key using the CMK and KMS sends back the plaintext DEK

*客户要求KMS使用CMK解密加密的键
  * The client can now decrypt the encrypted data

*客户现在可以解密加密数据

**Client-side encryption with customer provided keys, CSE-C:** Using this mechanism, you are able to utilize your own provided keys and use an AWS-SDK client to encrypt your data before sending it to S3 for storage.

**与客户提供的客户端加密，CSE-C：**使用此机制，您可以使用自己提供的键并使用AWS-SDK客户端来加密数据，然后再将其发送到S3进行存储。

* Encryption:

*加密：
  * The client generates a DEK and encrypts the plaintext data

*客户端生成DEK并加密纯文本数据
  * Then, using it's own custom CMK it encrypts the DEK

*然后，使用它自己的自定义CMK，它加密DEK
  * submit the encrypted data + encrypted DEK to S3 where it's stored

*将加密的数据 +加密DEK提交到存储的S3
* Decryption:

*解密：
  * S3 sends the encrypted data and DEK

* S3发送加密数据和DEK
  * As the client already has the CMK used to encrypt the DEK, it decrypts the DEK and then uses the plaintext DEK to decrypt the data

*由于客户端已经使用了CMK来加密DEK，因此将DEK解密，然后使用明文DEK解密数据

# HSM - Hardware Security Module

＃HSM-硬件安全模块

Cloud HSM is a FIPS 140 level two validated **hardware device** for secure cryptographic key storage (note that CloudHSM is a hardware appliance, it is not a virtualized service). It is a SafeNetLuna 7000 appliance with 5.3.13 preloaded. There are two firmware versions and which one you pick is really based on your exact needs. One is for FIPS 140-2 compliance and there was a newer version that can be used.

Cloud HSM是FIPS 140级的两个经过验证的**硬件设备**用于安全加密密钥存储（请注意，CloudHSM是硬件设备，不是虚拟化服务）。 这是一个预装5.3.13的Safenetluna 7000设备。 有两个固件版本，您选择哪个是基于您的确切需求。 一种用于FIPS 140-2合规性，可以使用一个较新的版本。

The unusual feature of CloudHSM is that it is a physical device, and thus it is **not shared with other customers**, or as it is commonly termed, multi-tenant. It is dedicated single tenant appliance exclusively made available to your workloads

CloudHSM的不寻常功能是它是一种物理设备，因此与其他客户没有共享**，或者通常称为多租户。 它是专用于您的工作量的专用单租户

Typically, a device is available within 15 minutes assuming there is capacity, but if the AZ is out of capacity it can take two weeks or more to acquire additional capacity.

通常，假设有能力，可以在15分钟内使用设备，但是如果AZ超出能力，则需要两周或更长时间才能获得额外的容量。

Both KMS and CloudHSM are available to you at AWS and both are integrated with your apps at AWS. Since this is a physical device dedicated to you, **the keys are stored on the device**. Keys need to either be **replicated to another device**, backed up to offline storage, or exported to a standby appliance. **This device is not backed** by S3 or any other service at AWS like KMS.

KMS和CloudHSM在AWS上都可以使用，并且两者都与AWS的应用程序集成在一起。 由于这是一个专用于您的物理设备，**键存储在设备上**。 键需要**复制到另一台设备**，备份到离线存储或导出到备用设备。 **该设备不会由S3或AWS等其他服务备份。

In **CloudHSM**, you have to **scale the service yourself**. You have to provision enough CloudHSM devices to handle whatever your encryption needs are based on the encryption algorithms you have chosen to implement for your solution.\

在** CloudHsm **中，您必须**自己扩展服务**。 您必须提供足够的CloudHSM设备来处理基于您选择为解决方案实现的加密算法的任何内容。
Key Management Service scaling is performed by AWS and automatically scales on demand, so as your use grows, so might the number of CloudHSM appliances that are required. Keep this in mind as you scale your solution and if your solution has auto-scaling, make sure your maximum scale is accounted for with enough CloudHSM appliances to service the solution.

密钥管理服务缩放是由AWS执行的，并会自动按需缩放，因此随着使用的增长，所需的CloudHSM设备的数量也可以。 请记住，当您扩展解决方案时，如果您的解决方案具有自动缩放，请确保使用足够的CloudHSM设备来计算最大规模以服务解决方案。

Just like scaling, **performance is up to you with CloudHSM**. Performance varies based on which encryption algorithm is used and on how often you need to access or retrieve the keys to encrypt the data. Key management service performance is handled by Amazon and automatically scales as demand requires it. CloudHSM's performance is achieved by adding more appliances and if you need more performance you either add devices or alter the encryption method to the algorithm that is faster.

就像缩放一样，** cloudhsm **取决于您。 性能根据使用哪种加密算法以及您需要访问或检索加密数据的键的频率而有所不同。 密钥管理服务的性能由亚马逊处理，并根据需求需要自动扩展。 CloudHSM的性能是通过添加更多设备来实现的，如果您需要更多的性能，则添加设备或更改更快的算法上的加密方法。

If your solution is **multi-region**, you should add several **CloudHSM appliances in the second region and work out the cross-region connectivity with a private VPN connection** or some method to ensure the traffic is always protected between the appliance at every layer of the connection. If you have a multi-region solution you need to think about how to **replicate keys and set up additional CloudHSM devices in the regions where you operate**. You can very quickly get into a scenario where you have six or eight devices spread across multiple regions, enabling full redundancy of your encryption keys.

如果您的解决方案是**多区域**，则应在第二个区域中添加几个** CloudHSM设备，并使用私有VPN连接来划出跨区域连接**或某种方法，以确保在之间始终保护流量 连接各层的设备。 如果您有多区域解决方案，则需要考虑如何**复制密钥并在操作**的区域中设置其他CloudHSM设备。 您可以很快进入一个场景，在这种情况下，您拥有六个或八个设备，分布在多个区域，从而使您的加密密钥完全冗余。

**CloudHSM** is an enterprise class service for secured key storage and can be used as a **root of trust for an enterprise**. It can store private keys in PKI and certificate authority keys in X509 implementations. In addition to symmetric keys used in symmetric algorithms such as AES, **KMS stores and physically protects symmetric keys only (cannot act as a certificate authority)**, so if you need to store PKI and CA keys a CloudHSM or two or three could be your solution.

** CloudHsm **是用于有安全密钥存储的企业类服务，可以用作企业**的信任根。 它可以将私钥存储在PKI中，并在X509实施中将私钥和证书授权密钥存储。 除了对称算法中使用的对称键，例如AES，** KMS商店，并实际保护对称键（不能充当证书授权）** 可能是您的解决方案。

**CloudHSM is considerably more expensive than Key Management Service**. CloudHSM is a hardware appliance so you have fix costs to provision the CloudHSM device, then an hourly cost to run the appliance. The cost is multiplied by as many CloudHSM appliances that are required to achieve your specific requirements.\

** CloudHSM比密钥管理服务贵得多**。 CloudHSM是一种硬件设备，因此您有修复成本来配置CloudHSM设备，然后是每小时运行设备的成本。 成本乘以满足您的特定要求所需的许多CloudHSM设备。
Additionally, cross consideration must be made in the purchase of third party software such as SafeNet ProtectV software suites and integration time and effort. Key Management Service is a usage based and depends on the number of keys you have and the input and output operations. As key management provides seamless integration with many AWS services, integration costs should be significantly lower. Costs should be considered secondary factor in encryption solutions. Encryption is typically used for security and compliance.

此外，必须在购买第三方软件（例如Safenet ProtectV软件套件以及集成时间和精力）时进行交叉考虑。 密钥管理服务是基于用法的，取决于您拥有的密钥数以及输入和输出操作。 由于密钥管理提供了与许多AWS服务的无缝集成，因此集成成本应大大降低。 成本应视为加密解决方案的次要因素。 加密通常用于安全性和合规性。

**With CloudHSM only you have access to the keys** and without going into too much detail, with CloudHSM you manage your own keys. **With KMS, you and Amazon co-manage your keys**. AWS does have many policy safeguards against abuse and **still cannot access your keys in either solution**. The main distinction is compliance as it pertains to key ownership and management, and with CloudHSM, this is a hardware appliance that you manage and maintain with exclusive access to you and only you.

**使用CloudHSM，只有您可以访问键**，而无需详细信息，而CloudHSM可以管理自己的钥匙。 **与KMS，您和亚马逊共同管理您的钥匙**。 AWS确实有许多防止虐待的政策保障，**仍然无法在任何解决方案中访问您的钥匙。 主要区别在于它与关键所有权和管理有关，并且与CloudHSM有关，这是您管理和维护的硬件设备，并拥有对您和您的独家访问权限。

## CloudHSM Suggestions

1. Always deploy CloudHSM in an **HA setup** with at least two appliances in **separate availability zones**, and if possible, deploy a third either on premise or in another region at AWS.

1.始终在**设置**中部署CloudHsm，并在**单独的可用性区域**中至少有两个设备**，如果可能的话，请在AWS的前提或其他区域中部署第三个。
2. Be careful when **initializing** a **CloudHSM**. This action **will destroy the keys**, so either have another copy of the keys or be absolutely sure you do not and never, ever will need these keys to decrypt any data.

2. **初始化** a ** cloudhsm **时要小心。 此操作**将破坏键**，因此要么拥有另一个键的副本，要么绝对确定您不会并且永远不会，因此永远都需要这些密钥来解密任何数据。
3. CloudHSM only **supports certain versions of firmware** and software. Before performing any update, make sure the firmware and or software is supported by AWS. You can always contact AWS support to verify if the upgrade guide is unclear.

3. CloudHSM仅**支持某些版本的固件**和软件。 在执行任何更新之前，请确保AWS支持固件和或软件。 您始终可以联系AWS支持以验证升级指南是否不清楚。
4. The **network configuration should never be changed.** Remember, it's in a AWS data center and AWS is monitoring base hardware for you. This means that if the hardware fails, they will replace it for you, but only if they know it failed.

4. **网络配置永远不要更改。 这意味着，如果硬件失败，他们将为您替换它，但前提是他们知道它失败了。
5. The **SysLog forward should not be removed or changed**. You can always **add** a SysLog forwarder to direct the logs to your own collection tool.

5. ** syslog前进不应删除或更改**。 您可以始终**添加** syslog experter，以将日志引导到您自己的收集工具。
6. The **SNMP** configuration has the same basic restrictions as the network and SysLog folder. This **should not be changed or removed**. An **additional** SNMP configuration is fine, just make sure you do not change the one that is already on the appliance.

6. ** SNMP **配置具有与网络和Syslog文件夹相同的基本限制。 此**不应更改或删除**。 一个**额外的** SNMP配置很好，只需确保您不要更改设备上已经存在的配置即可。
7. Another interesting best practice from AWS is **not to change the NTP configuration**. It is not clear what would happen if you did, so keep in mind that if you don't use the same NTP configuration for the rest of your solution then you could have two time sources. Just be aware of this and know that the CloudHSM has to stay with the existing NTP source.

7. AWS的另一个有趣的最佳实践是**不要更改NTP配置**。 目前尚不清楚如果您这样做会发生什么，请记住，如果您不为其他解决方案使用相同的NTP配置，那么您可以有两个时间来源。 请注意这一点，并知道CloudHSM必须与现有的NTP源保持联系。

The initial launch charge for CloudHSM is $5,000 to allocate the hardware appliance dedicated for your use, then there is an hourly charge associated with running CloudHSM that is currently at $1.88 per hour of operation, or approximately $1,373 per month.

CloudHSM的初始启动费用为5,000美元，用于分配专用于您使用的硬件设备，然后运行CloudHSM的每小时收费目前为每小时每小时1.88美元，或每月约1,373美元。

The most common reason to use CloudHSM is compliance standards that you must meet for regulatory reasons. **KMS does not offer data support for asymmetric keys. CloudHSM does let you store asymmetric keys securely**.

使用CloudHSM的最常见原因是您必须出于监管原因必须达到的合规标准。 ** KMS不提供非对称键的数据支持。 CloudHSM确实可以让您安全地存储不对称的键**。

The **public key is installed on the HSM appliance during provisioning** so you can access the CloudHSM instance via SSH.

**公共密钥在配置过程中安装在HSM设备上**，因此您可以通过SSH访问CloudHSM实例。

# Amazon Athena

＃亚马逊雅典娜

Amazon Athena is an interactive query service that makes it easy to **analyze data** directly in Amazon Simple Storage Service (Amazon **S3**) **using** standard **SQL**.

亚马逊雅典娜（Amazon Athena）是一项交互式查询服务，可以轻松地在Amazon简单存储服务（Amazon ** s3 **）**使用**标准** SQL **中直接分析数据**。

You need to **prepare a relational DB table** with the format of the content that is going to appear in the monitored S3 buckets. And then, Amazon Athena will be able to populate the DB from th logs, so you can query it.

您需要**准备一个关系DB表**，并使用将出现在受监视的S3存储桶中的内容的格式。 然后，亚马逊雅典娜将能够从原木中填充DB，因此您可以查询它。

Amazon Athena supports the **hability to query S3 data that is already encrypted** and if configured to do so, **Athena can also encrypt the results of the query which can then be stored in S3**.

Amazon Athena支持**查询已经加密**的S3数据的功能，如果配置为此，** athena还可以加密查询结果，然后可以将其存储在S3 **中。

**This encryption of results is independent of the underlying queried S3 data**, meaning that even if the S3 data is not encrypted, the queried results can be encrypted. A couple of points to be aware of is that Amazon Athena only supports data that has been **encrypted** with the **following S3 encryption methods**, **SSE-S3, SSE-KMS, and CSE-KMS**.

**这种结果的加密独立于基础查询的S3数据**，这意味着即使未对S3数据进行加密，也可以加密查询结果。 需要注意的几点是，亚马逊雅典娜仅支持已通过**加密**的数据。 。

SSE-C and CSE-E are not supported. In addition to this, it's important to understand that Amazon Athena will only run queries against **encrypted objects that are in the same region as the query itself**. If you need to query S3 data that's been encrypted using KMS, then specific permissions are required by the Athena user to enable them to perform the query.

不支持SSE-C和CSE-E。 除此之外，重要的是要了解亚马逊雅典只能对与查询本身相同区域的“加密对象”进行查询。 如果您需要查询使用KMS加密的S3数据，则Athena用户需要特定的权限才能使他们执行查询。

# AWS CloudTrail

＃AWS CloudTrail

This service **tracks and monitors AWS API calls made within the environment**. Each call to an API (event) is logged. Each logged event contains:

此服务**跟踪环境中的AWS API呼叫**。 每次呼叫对API（事件）记录。 每个记录事件都包含：

* The name of the called API: `eventName`

*称为API的名称：`eventName`
* The called service: `eventSource`

*称为服务：`eventSource'
* The time: `eventTime`

*时间：`eventtime'
* The IP address: `SourceIPAddress`

* IP地址：`sourceIpAddress`
* The agent method: `userAgent`. Examples:

*代理方法：`useragent`。 例子：
  * Signing.amazonaws.com - From AWS Management Console

* signing.amazonaws.com-来自AWS管理控制台
  * console.amazonaws.com - Root user of the account

* console.amazonaws.com-帐户的根用户
  * lambda.amazonaws.com - AWS Lambda
* The request parameters: `requestParameters`
* The response elements: `responseElements`

Event's are written to a new log file **approximately each 5 minutes in a JSON file**, they are held by CloudTrail and finally, log files are **delivered to S3 approximately 15mins after**.\

事件被写入新的日志文件**大约每5分钟在JSON文件**中，它们由CloudTrail持有，最后，日志文件**在**。
CloudTrail allows to use **log file integrity in order to be able to verify that your log files have remained unchanged** since CloudTrail delivered them to you. It creates a SHA-256 hash of the logs inside a digest file. A sha-256 hash of the new logs is created every hour.\

CloudTrail允许使用**日志文件的完整性，以便能够验证您的日志文件是否保持不变**，因为CloudTrail将其传递给了您。 它创建了Digest文件中日志的SHA-256哈希。 每小时都会创建一个新日志的SHA-256哈希。\
When creating a Trail the event selectors will allow you to indicate the trail to log: Management, data or insights events.

创建步道时，事件选择器将允许您指示记录的跟踪：管理，数据或见解事件。

Logs are saved in an S3 bucket. By default Server Side Encryption is used (SSE-S3) so AWS will decrypt the content for the people that has access to it, but for additional security you can use SSE with KMS and your own keys.

日志保存在S3存储桶中。 默认情况下，使用了服务器端加密（SSE-S3），因此AWS会为有权访问它的人解密内容，但是为了获得其他安全性，您可以将SSE与KMS和您自己的钥匙一起使用。

## Log File Naing Convention

##日志文件命名约定

![](<../.gitbook/assets/image (429).png>)

## S3 folder structure

![](<../.gitbook/assets/image (428).png>)

Note that the folders "_AWSLogs_" and "_CloudTrail_" are fixed folder names,

请注意，文件夹“ _awslogs_”和“ _cloudtrail_”是固定文件夹，

**Digest** files have a similar folders path:

**摘要**文件具有类似的文件夹路径：

![](<../.gitbook/assets/image (437).png>)

## Aggregate Logs from Multiple Accounts

##来自多个帐户的汇总日志

* Create a Trial in the AWS account where you want the log files to be delivered to

*在AWS帐户中创建试用，您希望将日志文件交付到
* Apply permissions to the destination S3 bucket allowing cross-account access for CloudTrail and allow each AWS account that needs access

*将权限应用于目的地S3存储桶，允许跨账户访问CloudTrail，并允许每个需要访问的AWS帐户
* Create a new Trail in the other AWS accounts and select to use the created bucket in step 1

*在其他AWS帐户中创建新的步道，然后选择在步骤1中使用创建的存储桶

However, even if you can save al the logs in the same S3 bucket, you cannot aggregate CloudTrail logs from multiple accounts into a CloudWatch Logs belonging to a single AWS account

但是，即使您可以将日志保存在同一S3存储桶中，也无法将云图日志从多个帐户汇总到属于单个AWS帐户的CloudWatch日志中

## Log Files Checking

##日志文件检查

You can check that the logs haven't been altered by running

您可以检查日志是否没有通过运行来更改

```javascript
aws cloudtrail validate-logs --trail-arn <trailARN> --start-time <start-time> [--end-time <end-time>] [--s3-bucket <bucket-name>] [--s3-prefix <prefix>] [--verbose]
```

## Logs to CloudWatch

##登录到CloudWatch

**CloudTrail can automatically send logs to CloudWatch so you can set alerts that warns you when suspicious activities are performed.**\

** CloudTrail可以自动将日志发送到CloudWatch，因此您可以设置警报，以警告您在执行可疑活动时会警告您。** \
Note that in order to allow CloudTrail to send the logs to CloudWatch a **role** needs to be created that allows that action. If possible, it's recommended to use AWS default role to perform these actions. This role will allow CloudTrail to:

请注意，为了允许CloudTrail将日志发送到CloudWatch a **角色**需要创建允许该操作的角色**。 如果可能的话，建议使用AWS默认角色执行这些操作。 这个角色将使CloudTrail得以：

* CreateLogStream: This allows to create a CloudWatch Logs log streams

* createLogstream：这允许创建一个CloudWatch日志日志流
* PutLogEvents: Deliver CloudTrail logs to CloudWatch Logs log stream

* putlogevents：将CloudTrail日志传递到CloudWatch日志日志流

## Event History

##事件历史记录

CloudTrail Event History allows you to inspect in a table the logs that have been recorded:

CloudTrail事件历史记录使您可以在表中检查已记录的日志：

![](<../.gitbook/assets/image (431).png>)

## Insights

##见解

**CloudTrail Insights** automatically **analyzes** write management events from CloudTrail trails and **alerts** you to **unusual activity**. For example, if there is an increase in `TerminateInstance` events that differs from established baselines, you’ll see it as an Insight event. These events make **finding and responding to unusual API activity easier** than ever.

** CloudTrail Insights **自动**分析**从CloudTrail Trails和**警报编写管理事件**您要**不寻常的活动**。 例如，如果“终止”事件与已建立的基线有所不同，则将其视为洞察事件。 这些事件使**寻找和响应异常的API活动比以往任何时候都更容易。

# CloudWatch

＃CloudWatch

Amazon CloudWatch allows to **collect all of your logs in a single repository** where you can create **metrics** and **alarms** based on the logs.\

Amazon CloudWatch允许**在单个存储库中收集所有日志**，您可以根据日志创建**指标**和**警报**。
CloudWatch Log Event have a **size limitation of 256KB of each log line**.

CloudWatch日志事件的大小限制为每个日志行**的256KB。

You can monitor for example logs from CloudTrail.\

您可以从CloudTrail监视如日志。\ \
Events that are monitored:

监视的事件：

* Changes to Security Groups and NACLs

*更改安全组和NACL
* Starting, Stopping, rebooting and terminating EC2instances

*开始，停止，重新启动和终止Ec2instances
* Changes to Security Policies within IAM and S3

*更改IAM和S3内的安全政策
* Failed login attempts to the AWS Management Console

*失败的登录尝试到AWS管理控制台
* API calls that resulted in failed authorization

* API调用导致授权失败的API
* Filters to search in cloudwatch: [https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/FilterAndPatternSyntax.html](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/FilterAndPatternSyntax.html)

*过滤到CloudWatch中的搜索：[https://docs.aws.amazon.com/amazoncloudwatch/latest/logs/filterandpatternsyntax.html]（ .html）

## Agent Installation

##代理安装

You can install agents insie your machines/containers to automatically send the logs back to CloudWatch.

您可以在计算机/容器中安装代理，以自动将日志发送回CloudWatch。

* **Create** a **role** and **attach** it to the **instance** with permissions allowing CloudWatch to collect data from the instances in addition to interacting with AWS systems manager SSM (CloudWatchAgentAdminPolicy & AmazonEC2RoleforSSM)

***创建** a **角色**和**将**附加到**实例**，并带有权限，允许CloudWatch除了与AWS Systems Manager SSM进行交互之外，还可以从实例中收集数据
* **Download** and **install** the **agent** onto the EC2 instance ([https://s3.amazonaws.com/amazoncloudwatch-agent/linux/amd64/latest/AmazonCloudWatchAgent.zip](https://s3.amazonaws.com/amazoncloudwatch-agent/linux/amd64/latest/AmazonCloudWatchAgent.zip)). You can download it from inside the EC2 or install it automatically using AWS System Manager selecting the package AWS-ConfigureAWSPackage

***下载**和**安装** **代理**到EC2实例（[https://s3.amazonaws.com/amazoncloudwatch-agent-agent/linux/linux/amd64/latest/amazoncloudwatchagent.zip.zip] ：//s3.amazonaws.com/amazoncloudwatch-agent/linux/amd64/latest/amazoncloudwatchagent.zip））。 您可以从EC2内部下载它，也可以使用AWS系统管理器自动安装它，以选择软件包AWS-ConfigureAwspackage
* **Configure** and **start** the CloudWatch Agent

***配置**和**开始** CloudWatch代理

A log group has many streams. A stream has many events. And inside of each stream, the events are guaranteed to be in order.

日志组有许多流。 流有许多事件。 在每个流的内部，事件都可以按顺序排列。

# Cost Explorer and Anomaly detection

＃费用探索者和异常检测

This allows you to check how are you expending money in AWS services and help you **detecting anomalies**.\

这使您可以检查如何在AWS服务中花钱并帮助您**检测异常**。
Moreover, you can configure an anomaly detection so AWS will warn you when some anomaly in costs is found.

此外，您可以配置异常检测，因此AWS会在发现一些异常时警告您。

## Budgets

Budgets help to manage costs and usage. You can get **alerted when a threshold is reached**.\

预算有助于管理成本和使用。 达到阈值时，您可以得到**警报**。
Also, they can be used for non cost related monitoring like the usage of a service (how many GB are used in a particular S3 bucket?).

另外，它们可用于非费用相关的监视，例如使用服务（特定的S3存储桶中有多少GB？）。

# AWS Config

＃AWS配置

AWS Config **capture resource changes**, so any change to a resource supported by Config can be recorded, which will **record what changed along with other useful metadata, all held within a file known as a configuration item**, a CI.\

AWS配置**捕获资源更改**，因此可以记录对配置支持的资源的任何更改，它将**记录与其他有用的元数据一起更改的内容，全部保存在称为配置项目的文件中**，一个 ci。\
This service is **region specific**.

该服务是**特定于区域的**。

A configuration item or **CI** as it's known, is a key component of AWS Config. It is comprised of a JSON file that **holds the configuration information, relationship information and other metadata as a point-in-time snapshot view of a supported resource**. All the information that AWS Config can record for a resource is captured within the CI. A CI is created **every time** a supported resource has a change made to its configuration in any way. In addition to recording the details of the affected resource, AWS Config will also record CIs for any directly related resources to ensure the change did not affect those resources too.

众所周知，配置项目或** ci **是AWS配置的关键组成部分。 它由一个JSON文件组成，该文件**包含配置信息，关系信息和其他元数据作为支持资源的时间点快照视图**。 AWS配置可以记录资源的所有信息都在CI中捕获。 每次**都会创建CI。 除了记录受影响资源的详细信息外，AWS配置还将为任何直接相关的资源记录CI，以确保更改也不会影响这些资源。

* **Metadata**: Contains details about the configuration item itself. A version ID and a configuration ID, which uniquely identifies the CI. Ither information can include a MD5Hash that allows you to compare other CIs already recorded against the same resource.

***元数据**：包含有关配置项目本身的详细信息。 版本ID和配置ID，该ID唯一标识了CI。 ITHER信息可以包含MD5HASH，该MD5HASH允许您比较已经录制的其他CI与相同资源进行比较。
* **Attributes**: This holds common **attribute information against the actual resource**. Within this section, we also have a unique resource ID, and any key value tags that are associated to the resource. The resource type is also listed. For example, if this was a CI for an EC2 instance, the resource types listed could be the network interface, or the elastic IP address for that EC2 instance

***属性**：这具有共同的**属性信息与实际资源**。 在本节中，我们还具有唯一的资源ID以及与资源关联的任何键值标签。 还列出了资源类型。 例如，如果这是EC2实例的CI，则列出的资源类型可能是网络接口或该EC2实例的弹性IP地址
* **Relationships**: This holds information for any connected **relationship that the resource may have**. So within this section, it would show a clear description of any relationship to other resources that this resource had. For example, if the CI was for an EC2 instance, the relationship section may show the connection to a VPC along with the subnet that the EC2 instance resides in.

***关系**：这掌握了资源可能拥有**的任何连接关系的信息。 因此，在本节中，它将清楚地描述与本资源所拥有的其他资源的任何关系。 例如，如果CI适用于EC2实例，则关系部分可以显示与EC2实例所属于的子网以及子网的连接。
* **Current configuration:** This will display the same information that would be generated if you were to perform a describe or list API call made by the AWS CLI. AWS Config uses the same API calls to get the same information.

***当前配置：**这将显示与您执行AWS CLI进行的描述或列出API调用的相同信息。 AWS配置使用相同的API调用来获取相同的信息。
* **Related events**: This relates to AWS CloudTrail. This will display the **AWS CloudTrail event ID that is related to the change that triggered the creation of this CI**. There is a new CI made for every change made against a resource. As a result, different CloudTrail event IDs will be created.

***相关事件**：这与AWS CloudTrail有关。 这将显示与触发此CI **创建的更改相关的** AWS CloudTrail事件ID。 对于针对资源进行的每项更改，都有新的CI。 结果，将创建不同的CloudTrail事件ID。

**Configuration History**: It's possible to obtain the configuration history of resources thanks to the configurations items. A configuration history is delivered every 6 hours and contains all CI's for a particular resource type.

**配置历史记录**：由于配置项目，可以获得资源的配置历史记录。 配置历史记录每6小时提供一次，并包含用于特定资源类型的所有CI。

**Configuration Streams**: Configuration items are sent to an SNS Topic to enable analysis of the data.

**配置流**：配置项已发送到SNS主题以启用数据分析。

**Configuration Snapshots**: Configuration items are used to create a point in time snapshot of all supported resources.

**配置快照**：配置项用于创建所有受支持资源的时间点快照。

**S3 is used to store** the Configuration History files and any Configuration snapshots of your data within a single bucket, which is defined within the Configuration recorder. If you have multiple AWS accounts you may want to aggregate your configuration history files into the same S3 bucket for your primary account. However, you'll need to grant write access for this service principle, config.amazonaws.com, and your secondary accounts with write access to the S3 bucket in your primary account.

** s3用于存储**在单个存储桶中，数据的配置历史记录文件和数据的任何配置快照，这是在配置录音机中定义的。 如果您有多个AWS帐户，则可能需要将配置历史记录文件汇总到主帐户的同一S3存储桶中。 但是，您需要授予此服务原理的写入访问权限，config.amazonaws.com和您的辅助帐户，并在主要帐户中对S3存储桶进行写入访问权限。

## Config Rules

##配置规则

Config rules are a great way to help you **enforce specific compliance checks** **and controls across your resources**, and allows you to adopt an ideal deployment specification for each of your resource types. Each rule **is essentially a lambda function** that when called upon evaluates the resource and carries out some simple logic to determine the compliance result with the rule. **Each time a change is made** to one of your supported resources, **AWS Config will check the compliance against any config rules that you have in place**.\

配置规则是帮助您**执行特定合规性检查** **和跨资源的控件的好方法，并允许您为每种资源类型采用理想的部署规范。 每个规则**本质上是一个lambda函数**，当被要求评估资源并执行一些简单的逻辑以确定与规则的合规性结果。 **每次对您支持的资源之一进行更改时，** AWS配置将对您拥有的任何配置规则进行检查**。
AWS have a number of **predefined rules** that fall under the security umbrella that are ready to use. For example, Rds-storage-encrypted. This checks whether storage encryption is activated by your RDS database instances. Encrypted-volumes. This checks to see if any EBS volumes that have an attached state are encrypted.

AWS有许多**预定义的规则**属于准备使用的安全保护伞。 例如，RDS存储加密。 这检查了您的RDS数据库实例是否激活了存储加密。 加密税。 这检查以查看是否有任何具有附件状态的EBS卷。

* **AWS Managed rules**: Set of predefined rules that cover a lot of best practices, so it's always worth browsing these rules first before setting up your own as there is a chance that the rule may already exist.

*** AWS托管规则**：一组涵盖许多最佳实践的预定义规则，因此在设置自己的规则可能已经存在的机会之前，总是值得先浏览这些规则。
* **Custom rules**: You can create your own rules to check specific customconfigurations.

***自定义规则**：您可以创建自己的规则来检查特定的constrycomfigurations。

Limit of 50 config rules per region before you need to contact AWS for an increase.\

在需要与AWS联系以增加之前，每个区域的50个配置规则的限制。\ \
Non compliant results are NOT deleted.

不兼容的结果未删除。

# SNS Topic

＃SNS主题

SNS topic is used as a **configuration stream for notifications** from different AWS services like Config or CloudWatch alarms.\

SNS主题用作来自config或CloudWatch Alarms等不同AWS服务的通知**的**配置流。\ \ \
You can have various endpoints associated to the SNS stream.\

您可以具有与SNS流相关联的各种端点。\ \
You can use SNS topic to send notifications to you via email or to SQS to treate programatically the notification.

您可以使用SNS主题通过电子邮件或SQ向您发送通知，以编程通知。

# Inspector

＃检查员

The Amazon Inspector service is **agent based**, meaning it requires software agents to be **installed on any EC2 instances** you want to assess. This makes it an easy service to be configured and added at any point to existing resources already running within your AWS infrastructure. This helps Amazon Inspector to become a seamless integration with any of your existing security processes and procedures as another level of security.

Amazon Inspector Service是基于代理的**，这意味着您需要在任何要评估的EC2实例上安装软件代理。 这使得在AWS基础架构中已经运行的现有资源的任何位置都可以进行配置和添加。 这有助于亚马逊检查员与您现有的任何安全流程和程序作为另一个安全级别的无缝集成。

These are the tests that AWS Inspector allow you to perform:

这些是AWS检查员允许您执行的测试：

* **CVEs**
* **CIS Benchmarks**
* **Security Best practices**

***安全最佳实践**
* **Network Reachability**

***网络达到性**

You can make any of those run on the EC2 machines you decide.

您可以将其中的任何一个运行在您决定的EC2机器上。

## Element of AWS Inspector

## AWS检查员元素

**Role**: Create or select a role to allow Amazon Inspector to have read only access to the EC2 instances (DescribeInstances)\

**角色**：创建或选择一个角色，以允许Amazon Inspector仅阅读访问EC2实例（DECUDECTINSTANCES）\
**Assessment Targets**: Group of EC2 instances that you want to run an assessment against\

**评估目标**：您想对\进行评估的EC2实例组
**AWS agents**: Software agents that must be install on EC2 instances to monitor. Data is sent to Amazon Inspector using a TLS channel. A regular heartbeat is sent from the agent to the inspector asking for instructions. It can autoupdate itself\

** AWS代理**：必须在EC2实例上安装的软件代理才能监视。 数据使用TLS通道发送给Amazon Inspector。 定期的心跳从代理商发送给检查员，要求指示。 它可以自动化自身\
**Assessment Templates**: Define specific configurations as to how an assessment is run on your EC2 instances. An assessment template cannot be modified after creation.

**评估模板**：定义有关在EC2实例上如何运行评估的特定配置。 创建后无法修改评估模板。

* Rules packages to be used

*要使用的规则软件包
* Duration of the assessment run 15min/1hour/8hours

*评估持续时间运行15分钟/1小时/8小时
* SNS topics, select when notify: Starts, finished, change state, reports a finding

* SNS主题，当通知时选择：开始，完成，更改状态，报告发现
* Attributes to b assigned to findings

*归因于分配给发现的B

**Rule package**: Contains a number of individual rules that are check against an EC2 when an assessment is run. Each one also have a severity (high, medium, low, informational). The possibilities are:

**规则软件包**：包含许多单独的规则，这些规则是在运行评估时对EC2进行检查的。 每个人也有严重性（高，中，低，信息性）。 可能性是：

* Common Vulnerabilities and Exposures (CVEs)

* Common Vulnerabilities and Exposures (CVEs)
* Center for Internet Security (CIS) Benchmark

*互联网安全中心（CIS）基准
* Security Best practices

*安全最佳实践

Once you have configured the Amazon Inspector Role, the AWS Agents are Installed, the target is configured and the template is configured, you will be able to run it. An assessment run can be stopped, resumed, or deleted.

一旦配置了Amazon Inspector角色，就安装了AWS代理，配置了目标并配置了模板，您将能够运行它。 可以停止，恢复或删除评估运行。

Amazon Inspector has a pre-defined set of rules, grouped into packages. Each Assessment Template defines which rules packages to be included in the test. Instances are being evaluated against rules packages included in the assessment template.

Amazon Inspector有一套预定的规则，分组为软件包。 每个评估模板都定义了哪些规则软件包包含在测试中。 正在评估评估模板中包含的规则软件包的实例。

{% hint style="info" %}

{％提示样式=“ info”％}
Note that nowadays AWS already allow you to **autocreate** all the necesary **configurations** and even automatically **install the agents inside the EC2 instances.**

请注意，如今的AWS已经允许您**自动创建**所有必要的**配置**，甚至自动**将代理安装在EC2实例中。**
{% endhint %}

## **Reporting**

## **报告**

**Telemetry**: data that is collected from an instance, detailing its configuration, behavior and processes during an assessment run. Once collected, the data is then sent back to Amazon Inspector in near-real-time over TLS where it is then stored and encrypted on S3 via an ephemeral KMS key. Amazon Inspector then accesses the S3 Bucket, decrypts the data in memory, and analyzes it against any rules packages used for that assessment to generate the findings.

**遥测**：从实例中收集的数据，详细介绍其在评估运行期间的配置，行为和过程。 一旦收集，然后将数据发送回到近实时的TLS上，将数据发送回亚马逊检查员，然后通过短暂的KMS键将其存储和加密在S3上。 然后，Amazon Inspector访问S3存储桶，将数据解密，并根据用于该评估生成发现的任何规则软件包进行分析。

**Assessment Report**: Provide details on what was assessed and the results of the assessment.

**评估报告**：提供有关评估内容和评估结果的详细信息。

* The **findings report** contain the summary of the assessment, info about the EC2 and rules and the findings that occurred.

***调查结果报告**包含评估的摘要，有关EC2和规则的信息以及发生的结果。
* The **full report** is the finding report + a list of rules that were passed.

***完整报告**是查找报告 +通过的规则列表。

# Trusted Advisor

＃值得信赖的顾问

The main function of Trusted Advisor is to **recommend improvements across your AWS account** to help optimize and hone your environment based on **AWS best practices**. These recommendations cover four distinct categories. It's a is a cross-region service.

值得信赖的顾问的主要功能是**建议您在AWS帐户中进行改进**，以帮助基于** AWS最佳实践**优化和磨练您的环境。 这些建议涵盖了四个不同的类别。 这是一个跨区域服务。

1. **Cost optimization:** which helps to identify ways in which you could **optimize your resources** to save money.

1. **成本优化：**有助于确定您可以**优化资源**的方式来节省资金。
2. **Performance:** This scans your resources to highlight any **potential performance issues** across multiple services.

2. **绩效：**这会扫描您的资源以突出显示任何潜在的性能问题**跨多个服务。
3. **Security:** This category analyzes your environment for any **potential security weaknesses** or vulnerabilities.

3. **安全：**此类别分析您的环境是否存在**潜在的安全弱点**或漏洞。
4. **Fault tolerance:** Which suggests best practices to **maintain service operations** by increasing resiliency should a fault or incident occur across your resources.

4. **容忍度：**建议最佳实践**维护服务操作**，如果您的资源中发生故障或事件，则通过提高弹性来维护服务操作。

The full power and potential of AWS Trusted Advisor is only really **available if you have a business or enterprise support plan with AWS**. **Without** either of these plans, then you will only have access to **six core checks** that are freely available to everyone. These free core checks are split between the performance and security categories, with the majority of them being related to security. These are the 6 checks: service limits, Security Groups Specific Ports Unrestricted, Amazon EBS Public Snapshots, Amazon RDS Public Snapshots, IAM Use, and MFA on root account.\

如果您有AWS **的业务或企业支持计划，那么AWS值得信赖的顾问的全部功能和潜力才真正**。 **没有这些计划中的任何一个，那么您只能访问**六个核心检查**，每个人都可以自由使用。 这些免费的核心检查是在性能和安全类别之间分配的，其中大多数与安全性有关。 这是6个检查：服务限制，安全组特定端口，无限制的端口，Amazon EBS Public快照，Amazon RDS公共快照，IAM使用和MFA在Root帐户上。\ \ \
Trusted advisor can send notifications and you can exclude items from it.\

受信任的顾问可以发送通知，您可以将项目排除在内。\ \
Trusted advisor data is **automatically refreshed every 24 hours**, **but** you can perform a **manual one 5 mins after the previous one.**

值得信赖的顾问数据**每24小时自动刷新一次**，**但是**您可以在上一个后5分钟执行手册。**

# Amazon GuardDuty

＃亚马逊警卫队

Amazon GuardDuty is a regional-based intelligent **threat detection service**, the first of its kind offered by AWS, which allows users to **monitor** their **AWS account** for **unusual and unexpected behavior by analyzing VPC Flow Logs, AWS CloudTrail management event logs, Cloudtrail S3 data event logs, and DNS logs**. It uses **threat intelligence feeds**, such as lists of malicious IP addresses and domains, and **machine learning** to identify **unexpected and potentially unauthorized and malicious activity** within your AWS environment. This can include issues like escalations of privileges, uses of exposed credentials, or communication with malicious IP addresses, or domains.\

Amazon GuardDuty是一个基于区域的智能**威胁检测服务**，AWS提供了第一个此类智能检测服务，它允许用户**监视**他们的** AWS帐户**通过分析不寻常和意外的行为 VPC流量日志，AWS CloudTrail管理事件日志，CloudTrail S3数据事件日志和DNS日志**。 它使用**威胁智能供稿**，例如恶意IP地址和域列表，以及**机器学习**，以识别**在AWS环境中的意外且潜在的未经授权和恶意活动**。 这可能包括诸如特权升级，暴露凭据的使用或与恶意IP地址或域的通信。\ \ \ \ \
For example, GuardDuty can detect compromised EC2 instances serving malware or mining bitcoin. It also monitors AWS account access behavior for signs of compromise, such as unauthorized infrastructure deployments, like instances deployed in a Region that has never been used, or unusual API calls, like a password policy change to reduce password strength.\

例如，GuardDuty可以检测到服务恶意软件或采矿比特币的受损EC2实例。 它还监视AWS帐户访问行为是否妥协迹象，例如未经授权的基础架构部署，例如部署在从未使用过的区域中的实例或不寻常的API调用，例如密码策略更改以减少密码强度。
You can **upload list of whitelisted and blacklisted IP addresses** so GuardDuty takes that info into account.

您可以**上传白名单和黑名单的IP地址的列表**这样，GuardDuty将该信息考虑在内。

Finding summary:

* Finding type

*查找类型
* Severity: 7-8.9High, 4-6.9Medium, 01-3.9Low

*严重性：7-8.9高，4-6.9Medium，01-3.9Low
* Region
* Account ID

* 帐户ID
* Resource ID
* Time of detection

*检测时间
* Which threat list was used

*使用了哪个威胁列表

The body has this information:

身体有此信息：

* Resource affected

*受影响的资源
* Action

* 行动
* Actor: Ip address, port and domain

*演员：IP地址，端口和域
* Additional Information

* 附加信息

You can invite other accounts to a different AWS GuardDuty account so **every account is monitored from the same GuardDuty**. The master account must invite the member accounts and then the representative of the member account must accept the invitation.\

您可以将其他帐户邀请到其他AWS GuardDuty帐户中，因此**每个帐户都会从同一守护程序**监视。 主帐户必须邀请会员帐户，然后成员帐户的代表必须接受邀请。
There are different IAM Role permissions to allow GuardDuty to get the information and to allow a user to upload IPs whitelisted and blacklisted.\

有不同的IAM角色权限，可以允许GuardDuty获取信息并允许用户上传IPS白名单和黑名单。\ \ \
GuarDuty uses a service-linked role called "AWSServiceRoleForAmazonGuardDuty" that allows it to retrieve metadata from affected endpoints.

Guarduty使用一个名为“ Awsserviceroleforamazonguardduty”的服务连锁角色，该角色使其可以从受影响的端点中检索元数据。

You pay for the processing of your log files, per 1 million events per months from CloudTrail and per GB of analysed logs from VPC Flow

您为日志文件的处理付费，每月每月从CloudTrail和VPC Flow中的每个GB分析的日志

When a user disable GuardDuty, it will stop monitoring your AWS environment and it won't generate any new findings at all, and the existing findings will be lost.\

当用户禁用Guardduty时，它将停止监视您的AWS环境，并且根本不会生成任何新发现，并且现有发现将丢失。
If you just stop it, the existing findings will remain.

如果您只是停止它，那么现有的发现将保留。

# Amazon Macie

The main function of the service is to provide an automatic method of **detecting, identifying, and also classifying data** that you are storing within your AWS account.

该服务的主要功能是提供一种自动方法，用于**检测，识别以及对您存储在AWS帐户中的数据**进行分类。

The service is backed by **machine learning**, allowing your data to be actively reviewed as different actions are taken within your AWS account. Machine learning can spot access patterns and **user behavior** by analyzing **cloud trail event** data to **alert against any unusual or irregular activity**. Any findings made by Amazon Macie are presented within a dashboard which can trigger alerts, allowing you to quickly resolve any potential threat of exposure or compromise of your data.

该服务得到**机器学习**的支持，可以在您的AWS帐户中采取不同的操作，从而积极审查您的数据。 机器学习可以通过分析**云跟踪事件**数据到**警报，以确定任何异常或不规则活动**，可以发现访问模式和**用户行为**。 亚马逊Macie提出的任何发现都在仪表板中呈现，该发现可以触发警报，从而使您可以快速解决任何潜在的曝光威胁或数据折衷的威胁。

Amazon Macie will automatically and continuously **monitor and detect new data that is stored in Amazon S3**. Using the abilities of machine learning and artificial intelligence, this service has the ability to familiarize over time, access patterns to data. \

Amazon Macie将自动，连续**监视和检测存储在Amazon S3 **中的新数据。 使用机器学习和人工智能的能力，此服务能够随着时间的流逝而熟悉数据。 \ \
Amazon Macie also uses natural language processing methods to **classify and interpret different data types and content**. NLP uses principles from computer science and computational linguistics to look at the interactions between computers and the human language. In particular, how to program computers to understand and decipher language data. The **service can automatically assign business values to data that is assessed in the form of a risk score**. This enables Amazon Macie to order findings on a priority basis, enabling you to focus on the most critical alerts first. In addition to this, Amazon Macie also has the added benefit of being able to **monitor and discover security changes governing your data**. As well as identify specific security-centric data such as access keys held within an S3 bucket.

亚马逊·马基（Amazon Macie）还使用自然语言处理方法来**对不同的数据类型和内容进行分类和解释**。 NLP使用计算机科学和计算语言学的原理来研究计算机与人类语言之间的相互作用。 特别是如何编程计算机以理解和破译语言数据。 **服务可以自动将业务价值分配给以风险分数的形式评估的数据**。 这使Amazon Macie能够优先订购发现，使您能够首先专注于最关键的警报。 除此之外，亚马逊·马基（Amazon Macie）还具有额外的好处，即能够**监视和发现控制数据的安全性更改**。 以及确定以安全性为中心的特定数据，例如在S3存储桶中保存的访问密钥。

This protective and proactive security monitoring enables Amazon Macie to identify critical, sensitive, and security focused data such as API keys, secret keys, in addition to PII (personally identifiable information) and PHI data.

这种保护性和主动的安全性监视使亚马逊Macie能够确定关键，敏感和安全性的数据，例如API键，秘密密钥，除了PII（个人身份信息）和PHI数据外。

This is useful to avoid data leaks as Macie will detect if you are exposing people information to the Internet.

这对于避免数据泄漏很有用，因为Macie将检测到您是否将信息传播到Internet。

It's a **regional service**.

这是一个**区域服务**。

It requires the existence of IAM Role 'AWSMacieServiceCustomerSetupRole' and it needs AWS CloudTrail to be enabled.

它要求存在IAM角色“ AwsmacieservicecustomerSetuprole”，并且需要启用AWS CloudTrail。

Pre-defined alerts categories:

* Anonymized access

*匿名访问
* Config compliance
* Credential Loss
* Data compliance
* Files hosting

*文件托管
* Identity enumeration

*身份枚举
* Information loss

*信息损失
* Location anomaly

*位置异常
* Open permissions
* Privilege escalation
* Ransomware
* Service disruption

*服务中断
* Suspicious access

*可疑访问

The **alert summary** provides detailed information to allow you to respond appropriately. It has a description that provides a deeper level of understanding of why it was generated. It also has a breakdown of the results. 

**警报摘要**提供了详细的信息，以使您能够适当响应。 它具有描述，可以更深入地了解其生成的原因。 它还对结果分解。

The user has the possibility to create new custom alerts.

用户有可能创建新的自定义警报。

**Dashboard categorization**:

**仪表板分类**：

* S3 Objects for selected time range

*所选时间范围的S3对象
* S3 Objects

* S3对象
* S3 Objects by PII - Personally Identifiable Information

* pii的S3对象 - 个人身份信息
* S3 Objects by ACL

* S3对ACL的对象
* High-risk CloudTrail events and associated users

*高风险的CloudTrail事件和相关用户
* High-risk CloudTrail errors and associated users

*高风险的CloudTrail错误和相关用户
* Activity Location

*活动位置
* CloudTrail Events
* Activity ISPs

*活动ISP
* CloudTrail user identity types

* CloudTrail用户身份类型

**User Categories**: Macie categorises the users in the following categories:

**用户类别**：Macie在以下类别中分类用户：

* **Platinum**: Users or roles considered to be making high risk API calls. Often they have admins privileges. You should monitor the pretty god in case they are compromised

***铂金**：被认为是高风险API调用的用户或角色。 他们经常有管理特权。 您应该监视漂亮的上帝，以防他们受到妥协
* **Gold**: Users or roles with history of calling APIs related to infrastructure changes. You should also monitor them

***金**：用户或具有与基础结构更改有关的呼叫API的角色。 您还应该监视它们
* **Silver**: Users or roles performing medium level risk API calls
* **Bronze**: Users or roles using lowest level of risk based on API calls

***青铜**：根据API调用，使用最低风险级别的用户或角色

**Identity types:**

**身份类型：**

* Root: Request made by root user

* root：root用户提出的请求
* IAM user: Request made by IAM user

* IAM用户：IAM用户的请求
* Assumed Role: Request made by temporary assumed credentials (AssumeRole API for STS)

*假定角色：由临时假定凭证提出的请求（STS的假设API）
* Federated User: Request made using temporary credentials (GetFederationToken API fro STS)

*联合用户：使用临时凭据（getfederationtoken api for sts）提出的请求
* AWS Account: Request made by a different AWS account

* AWS帐户：由其他AWS帐户提出的请求
* AWS Service: Request made by an AWS service

* AWS服务：AWS服务的要求

**Data classification**: 4 file classifications exists:

**数据分类**：4文件分类：

* Content-Type: list files based on content-type detected. The given risk is determined by the type of content detected.

* content-type：基于检测到的内容类型的列表文件。 给定的风险取决于检测到的内容类型。
* File Extension: Same as content-type but based on the extension

*文件扩展名：与内容类型相同，但基于扩展名
* Theme: Categorises based on a series of keywords detected within the files

*主题：基于文件中检测到的一系列关键字进行分类
* Regex: Categories based on specific regexps

* REGEX：基于特定正性的类别

The final risk of a file will be the highest risk found between those 4 categories

文件的最终风险将是这4个类别之间发现的最高风险

The research function allows to create you own queries again all Amazon Macie data and perform a deep dive analysis of the data. You can filter results based on: CloudTrail Data, S3 Bucket properties and S3 Objects

研究功能允许您再次创建所有查询所有亚马逊Macie数据，并对数据进行深入的潜水分析。 您可以根据以下方式过滤结果：CloudTrail数据，S3存储桶属性和S3对象

It possible to invite other accounts to Amazon Macie so several accounts share Amazon Macie.

可以邀请其他帐户到亚马逊Macie，因此有几个帐户共享Amazon Macie。

# Route 53

You can very easily create **health checks for web pages** via Route53. For example you can create HTTP checks on port 80 to a page to check that the web server is working.

您可以通过Route53轻松地为网页**创建**健康检查。 例如，您可以在端口80上创建HTTP检查到页面，以检查Web服务器是否正常工作。

Route 53 service is mainly used for checking the health of the instances. To check the health of the instances we can ping a certain DNS point and we should get response from the instance if the instances are healthy.

53号公路服务主要用于检查实例的健康状况。 为了检查实例的健康，我们可以在某个DNS点上找到一个，如果实例健康，我们应该从该实例中得到回应。

# CloufFront

Amazon CloudFront is AWS's **content delivery network that speeds up distribution** of your static and dynamic content through its worldwide network of edge locations. When you use a request content that you're hosting through Amazon CloudFront, the request is routed to the closest edge location which provides it the lowest latency to deliver the best performance. When **CloudFront access logs** are enabled you can record the request from each user requesting access to your website and distribution. As with S3 access logs, these logs are also **stored on Amazon S3 for durable and persistent storage**. There are no charges for enabling logging itself, however, as the logs are stored in S3 you will be stored for the storage used by S3.

Amazon CloudFront是AWS的**内容输送网络，它通过其全球边缘位置网络加快了您的静态和动态内容的分布。 当您使用您通过Amazon CloudFront托管的请求内容时，请求将路由到最接近的边缘位置，该位置为其提供了最低的延迟，以提供最佳性能。 当启用**云方访问日志**时，您可以从每个用户中记录请求的请求，以请求访问您的网站和分发。 与S3访问日志一样，这些日志也被**存储在Amazon S3上，以持久和持久存储**。 没有用于启用日志记录的费用，但是，由于日志存储在S3中，因此您将存储S3使用的存储空间。

The log files capture data over a period of time and depending on the amount of requests that are received by Amazon CloudFront for that distribution will depend on the amount of log fils that are generated. It's important to know that these log files are not created or written to on S3. S3 is simply where they are delivered to once the log file is full. **Amazon CloudFront retains these logs until they are ready to be delivered to S3**. Again, depending on the size of these log files this delivery can take **between one and 24 hours**.

日志文件在一段时间内捕获数据，并取决于亚马逊Cloudfront对该分布收到的请求的数量取决于生成的日志FIL的数量。 重要的是要知道这些日志文件不是在S3上创建或编写的。 S3仅是一旦日志文件已满，将它们交付到的位置。 ** Amazon CloudFront保留这些日志，直到准备将其交付到S3 **为止。 同样，取决于这些日志文件的大小，该交付可能需要一个时间到24小时**。

**By default cookie logging is disabled** but you can enable it.

**默认情况下，cookie记录被禁用**，但是您可以启用它。

# VPC

## VPC Flow Logs

## VPC流日志

Within your VPC, you could potentially have hundreds or even thousands of resources all communicating between different subnets both public and private and also between different VPCs through VPC peering connections. **VPC Flow Logs allows you to capture IP traffic information that flows between your network interfaces of your resources within your VPC**.

在您的VPC中，您可能会通过VPC对等连接在不同子网之间以及在不同的VPC之间进行数百甚至数千个资源。 ** VPC流量日志使您可以捕获VPC中资源网络接口之间流动的IP流量信息。

Unlike S3 access logs and CloudFront access logs, the **log data generated by VPC Flow Logs is not stored in S3. Instead, the log data captured is sent to CloudWatch logs**.

与S3访问日志和CloudFront访问日志不同，VPC流量日志生成的**日志数据不存储在S3中。 而是将捕获的日志数据发送到CloudWatch日志**。

Limitations:

* If you are running a VPC peered connection, then you'll only be able to see flow logs of peered VPCs that are within the same account.

*如果您正在运行VPC凝视连接，那么您将只能看到同一帐户内的凝视VPC的流日志。
* If you are still running resources within the EC2-Classic environment, then unfortunately you are not able to retrieve information from their interfaces

*如果您仍在EC2经典环境中运行资源，那么不幸的是您无法从其界面检索信息
* Once a VPC Flow Log has been created, it cannot be changed. To alter the VPC Flow Log configuration, you need to delete it and then recreate a new one.

*一旦创建了VPC流日志，就无法更改。 要更改VPC Flow日志配置，您需要删除它，然后重新创建新的。
* The following traffic is not monitored and captured by the logs. DHCP traffic within the VPC, traffic from instances destined for the Amazon DNS Server.

*未通过日志监视和捕获以下流量。 VPC中的DHCP流量，来自Amazon DNS服务器的实例流量。
* Any traffic destined to the IP address for the VPC default router and traffic to and from the following addresses, 169.254.169.254 which is used for gathering instance metadata, and 169.254.169.123 which is used for the Amazon Time Sync Service.

*任何目的地为VPC默认路由器的IP地址的流量和访问以下地址的流量，用于收集实例元数据的169.254.169.254，以及用于亚马逊时间同步服务的169.254.169.123。
* Traffic relating to an Amazon Windows activation license from a Windows instance

*与Windows实例的Amazon Windows激活许可证有关的流量
* Traffic between a network load balancer interface and an endpoint network interface

*网络加载平衡器接口和端点网络接口之间的流量

For every network interface that publishes data to the CloudWatch log group, it will use a different log stream. And within each of these streams, there will be the flow log event data that shows the content of the log entries. Each of these **logs captures data during a window of approximately 10 to 15 minutes**.

对于将数据发布到CloudWatch日志组的每个网络接口，它将使用不同的日志流。 在这些流中的每一个中，都会有一些流日志事件数据显示日志条目的内容。 这些**日志中的每一个都在大约10至15分钟的窗口中捕获数据。

![](<../.gitbook/assets/image (432).png>)

![](<../.gitbook/assets/image (433).png>)

## Subnets

Subnets helps to enforce a greater level of security. **Logical grouping of similar resources** also helps you to maintain an **ease of management** across your infrastructure.\

子网有助于执行更大的安全性。 **类似资源的逻辑分组**还可以帮助您保持基础架构的**简化管理**。
Valid CIDR are from a /16 netmask to a /28 netmask.\

有效的CIDR从A /16 NetMask到A /28 NetMask。A subnet cannot be in different availability zones at the same time.

子网不能同时处于不同的可用性区域。

By having **multiple Subnets with similar resources grouped together**, it allows for greater security management. By implementing **network level virtual firewalls,** called network access control lists, or **NACLs**, it's possible to **filter traffic** on specific ports from both an ingress and egress point at the Subnet level.

通过将**多个子网组成相似的资源**，它可以提供更大的安全管理。 通过实现**网络级别虚拟防火墙，**称为网络访问控制列表或** nacls **，可以**从子网级别的入口和出口点上过滤特定端口上的流量**。

When you create a subnet the **network** and **broadcast address** of the subnet **can't be used** for host addresses and **AWS reserves the first three host IP addresses** of each subnet **for** **internal AWS usage**: he first host address used is for the VPC router. The second address is reserved for AWS DNS and the third address is reserved for future use.

当您创建子网时，**网络**和**广播地址**无法使用**用于主机地址，并且** AWS保留每个子网**的前三个主机IP地址** ** *对于** **内部AWS用法**：他使用的第一个主机地址用于VPC路由器。 第二个地址是为AWS DNS保留的，第三个地址保留供将来使用。

It's called **public subnets** to those that have **direct access to the Internet, whereas private subnets do not.**

它被称为“公共子网” **对那些直接访问Internet的人，而私人子网则不访问。** **

In order to make a subnet public you need to **create** and **attach** an **Internet gateway** to your VPC. This Internet gateway is a managed service, controlled, configured, and maintained by AWS. It scales horizontally automatically, and is classified as a highly valuable component of your VPC infrastructure. Once your Internet gateway is attached to your VPC, you have a gateway to the Internet. However, at this point, your instances have no idea how to get out to the Internet. As a result, you need to add a default route to the route table associated with your subnet. The route could have a **destination value of 0.0. 0. 0/0, and the target value will be set as your Internet gateway ID**.

为了使子网公开，您需要**创建**和**附加** and ** Internet网关**到您的VPC。 该Internet网关是由AWS进行控制，配置和维护的托管服务。 它会自动缩放，并被归类为VPC基础架构的高度价值组成部分。 一旦您的Internet网关连接到VPC，您就可以通往Internet。 但是，在这一点上，您的实例不知道如何上网。 结果，您需要在与子网关联的路由表中添加默认路由。 该路线的目标值可能为0.0。 0. 0/0，目标值将设置为您的Internet网关ID **。

By default, all subnets have the automatic assigned of public IP addresses turned off but it can be turned on.

默认情况下，所有子网均具有关闭公共IP地址的自动分配，但可以打开。

**A local route within a route table enables communication between VPC subnets.**

**路由表中的本地路线启用VPC子网之间的通信。**

If you are **connection a subnet with a different subnet you cannot access the subnets connected** with the other subnet, you need to create connection with them directly. **This also applies to internet gateways**. You cannot go through a subnet connection to access internet, you need to assign the internet gateway to your subnet.

如果您是**连接带有不同子网的子网，则无法访问与另一子网连接的子网**，您需要直接与它们建立连接。 **这也适用于Internet网关**。 您不能通过子网连接进入访问Internet，需要将Internet网关分配给子网。

## VPC Peering

VPC peering allows you to **connect two or more VPCs together**, using IPV4 or IPV6, as if they were a part of the same network.

VPC对等使您可以使用IPv4或ipv6将两个或多个VPC连接在一起**，就好像它们是同一网络的一部分一样。

Once the peer connectivity is established, **resources in one VPC can access resources in the other**. The connectivity between the VPCs is implemented through the existing AWS network infrastructure, and so it is highly available with no bandwidth bottleneck. As **peered connections operate as if they were part of the same network**, there are restrictions when it comes to your CIDR block ranges that can be used.\

一旦建立了同行连接，一个VPC中的资源就可以访问另一个VPC的资源**。 VPC之间的连通性是通过现有的AWS网络基础架构实现的，因此它在没有带宽瓶颈的情况下高度可用。 由于**凝视连接就像它们是同一网络的一部分一样，在您的CIDR块范围内有一些限制。\ \ \ \ \
If you have **overlapping or duplicate CIDR** ranges for your VPC, then **you'll not be able to peer the VPCs** together.\

如果您的VPC有**重叠或重复的CIDR **范围，那么**您将无法将VPC*与VPC相关。\ \ \ \ \
Each AWS VPC will **only communicate with its peer**. As an example, if you have a peering connection between VPC 1 and VPC 2, and another connection between VPC 2 and VPC 3 as shown, then VPC 1 and 2 could communicate with each other directly, as can VPC 2 and VPC 3, however, VPC 1 and VPC 3 could not. **You can't route through one VPC to get to another.**

每个AWS VPC只会与其同行**通信。 例如，如果您在VPC 1和VPC 2之间具有对等连接，则如图所示，VPC 2和VPC 3之间的另一个连接，则VPC 1和2可以直接相互通信，但是VPC 2和VPC 3也可以直接通信。 ，VPC 1和VPC 3不能。 **您不能穿过一个VPC到达另一个VPC。**

# AWS Secrets Manager

＃AWS Secrets Manager

AWS Secrets Manager is a great service to enhance your security posture by allowing you to **remove any hard-coded secrets within your application and replacing them with a simple API call** to the aid of your secrets manager which then services the request with the relevant secret. As a result, AWS Secrets Manager acts as a **single source of truth for all your secrets across all of your applications**.

AWS Secrets Manager是一项很好的服务，可以通过允许您**删除应用程序中的任何硬编码秘密，并用简单的API调用**替换您的秘密经理，然后将其替换为Secrets Manager 相关的秘密。 结果，AWS Secrets Manager是您所有应用程序中所有秘密的单一真实来源**。

AWS Secrets Manager enables the **ease of rotating secrets** and therefore enhancing the security of that secret. An example of this could be your database credentials. Other secret types can also have automatic rotation enabled through the use of lambda functions, for example, API keys.

AWS Secrets Manager可以**易于旋转秘密**，从而增强该秘密的安全性。 一个例子可能是您的数据库凭据。 其他秘密类型也可以通过使用Lambda功能（例如API键）具有自动旋转。

Access to your secrets within AWS Secret Manager is governed by fine-grained IAM identity-based policies in addition to resource-based policies.

除基于资源的政策外，AWS Secret Manager在AWS Secret Manager中访问您的秘密还受基于IAM身份的策略的约束。

To allow a user form a different account to access your secret you need to authorize him to access the secret and also authorize him to decrypt the secret in KMS. The Key policy also needs to allows the external user to use it.

为了允许用户形成一个不同的帐户以访问您的秘密，您需要授权他访问该秘密，并授权他在公里中解密秘密。 关键策略还需要允许外部用户使用它。

**AWS Secrets Manager integrates with AWS KMS to encrypt your secrets within AWS Secrets Manager.**

** AWS Secrets Manager与AWS KMS集成，以在AWS Secrets Manager中加密您的秘密。**

# EMR

EMR is a managed service by AWS and is comprised of a **cluster of EC2 instances that's highly scalable** to process and run big data frameworks such Apache Hadoop and Spark.

EMR是AWS的托管服务，由一个**群集的EC2实例组成，可扩展**，可以处理和运行大数据框架，例如Apache Hadoop和Spark。

From EMR version 4.8.0 and onwards, we have the ability to create a **security configuration** specifying different settings on **how to manage encryption for your data within your clusters**. You can either encrypt your data at rest, data in transit, or if required, both together. The great thing about these security configurations is they're not actually a part of your EC2 clusters.

从EMR版本4.8.0及以后，我们可以创建**安全配置** **在**上指定不同的设置，如何在群集中管理数据的加密**。 您可以在静止，运输中或需要时将数据加密。 这些安全配置的好处是它们实际上并不是EC2群集的一部分。

One key point of EMR is that **by default, the instances within a cluster do not encrypt data at rest**. Once enabled, the following features are available.

EMR的一个关键点是**默认情况下，群集中的实例不会在REST **加密数据。 启用后，可以使用以下功能。

* **Linux Unified Key Setup:** EBS cluster volumes can be encrypted using this method whereby you can specify AWS **KMS** to be used as your key management provider, or use a custom key provider.

*** Linux Unified密钥设置：**可以使用此方法对EBS群集量进行加密，从而可以指定AWS ** KMS **作为密钥管理提供商，或使用自定义密钥提供商。
* **Open-Source HDFS encryption:** This provides two Hadoop encryption options. Secure Hadoop RPC which would be set to privacy which uses simple authentication security layer, and data encryption of HDFS Block transfer which would be set to true to use the AES-256 algorithm.

***开源HDFS加密：**这提供了两个Hadoop加密选项。 安全的Hadoop RPC将设置为使用简单身份验证安全层的隐私和HDFS块传输的数据加密，该数据将设置为TRUE以使用AES-256算法。

From an encryption in transit perspective, you could enable **open source transport layer security** encryption features and select a certificate provider type which can be either PEM where you will need to manually create PEM certificates, bundle them up with a zip file and then reference the zip file in S3 or custom where you would add a custom certificate provider as a Java class that provides encryption artefacts.

从传输角度的加密来看，您可以启用**开源传输层安全**加密功能，然后选择一个证书提供商类型，该类型可以是PEM，您可以在其中手动创建PEM证书，用zip文件和zip文件和捆绑它们 然后在S3或自定义中引用ZIP文件，您将在其中添加自定义证书提供商作为提供加密工件的Java类。

Once the TLS certificate provider has been configured in the security configuration file, the following encryption applications specific encryption features can be enabled which will vary depending on your EMR version.

一旦在安全配置文件中配置了TLS证书提供商，可以启用以下加密应用程序特定的加密功能，该功能将根据您的EMR版本而变化。

* Hadoop might reduce encrypted shuffle which uses TLS. Both secure Hadoop RPC which uses Simple Authentication Security Layer, and data encryption of HDFS Block Transfer which uses AES-256, are both activated when at rest encryption is enabled in the security configuration.

* hadoop可能会减少使用TLS的加密洗牌。 使用简单身份验证安全层的安全Hadoop RPC，以及使用AES-256的HDFS块传输的数据加密，都在安全配置中启用静止加密时都被激活。
* Presto: When using EMR version 5.6.0 and later, any internal communication between Presto nodes will use SSL and TLS.

* PRESTO：使用EMR版本5.6.0及以后时，Presto节点之间的任何内部通信都将使用SSL和TLS。
* Tez Shuffle Handler uses TLS.
* Spark: The Akka protocol uses TLS. Block Transfer Service uses Simple Authentication Security Layer and 3DES. External shuffle service uses the Simple Authentication Security Layer.

* SPARK：AKKA协议使用TLS。 块传输服务使用简单的身份验证安全层和3DE。 外部洗牌服务使用简单的身份验证安全层。

# RDS - Relational Database Service

＃RDS-关系数据库服务

RDS allows you to set up a **relational database** using a number of **different engines** such as MySQL, Oracle, SQL Server, etc. During the creation of your RDS database instance, you have the opportunity to **Enable Encryption at the Configure Advanced Settings** screen under Database Options and Enable Encryption.

RDS允许您使用许多**不同的引擎**设置**关系数据库**，例如MySQL，Oracle，SQL Server等。在创建RDS数据库实例期间，您有机会** 在配置高级设置**屏幕数据库选项下启用加密，并启用加密。

By enabling your encryption here, you are enabling **encryption at rest for your storage, snapshots, read replicas and your back-ups**. Keys to manage this encryption can be issued by using **KMS**. It's not possible to add this level of encryption after your database has been created. **It has to be done during its creation**.

通过在此处启用加密，您可以在静止状态下进行**加密以进行存储，快照，读取副本和备份**。 可以使用** kms **发出管理此加密的密钥。 创建数据库后，不可能添加此级别的加密。 **必须在创建期间完成**。

However, there is a **workaround allowing you to encrypt an unencrypted database as follows**. You can create a snapshot of your unencrypted database, create an encrypted copy of that snapshot, use that encrypted snapshot to create a new database, and then, finally, your database would then be encrypted.

但是，有一个方法可以使您可以按照以下方式加密未加密的数据库。 您可以创建未加密数据库的快照，创建该快照的加密副本，使用该加密快照来创建一个新数据库，然后最后，将您的数据库进行加密。

Amazon RDS **sends data to CloudWatch every minute by default.**

默认情况下，Amazon RDS **每分钟将数据发送到CloudWatch。**

In addition to encryption offered by RDS itself at the application level, there are **additional platform level encryption mechanisms** that could be used for protecting data at rest including **Oracle and SQL Server Transparent Data Encryption**, known as TDE, and this could be used in conjunction with the method order discussed but it would **impact the performance** of the database MySQL cryptographic functions and Microsoft Transact-SQL cryptographic functions.

除了RDS本身在应用级别提供的加密外，还有**其他平台级别的加密机制**可以用于保护静止数据的数据，包括** Oracle和SQL Server透明数据加密**，称为TDE，称为TDE，称为TDE， 这可以与讨论的方法顺序结合使用，但会影响数据库MySQL加密功能的性能**和Microsoft Transact-SQL加密功能。

If you want to use the TDE method, then you must first ensure that the database is associated to an option group. Option groups provide default settings for your database and help with management which includes some security features. However, option groups only exist for the following database engines and versions.

如果要使用TDE方法，则必须首先确保数据库与选项组关联。 选项组为您的数据库提供默认设置，并在管理方面提供帮助，其中包括一些安全功能。 但是，仅适用于以下数据库引擎和版本的选项组。

Once the database is associated with an option group, you must ensure that the Oracle Transparent Data Encryption option is added to that group. Once this TDE option has been added to the option group, it cannot be removed. TDE can use two different encryption modes, firstly, TDE tablespace encryption which encrypts entire tables and, secondly, TDE column encryption which just encrypts individual elements of the database.

一旦数据库与选项组关联，则必须确保将Oracle透明数据加密选项添加到该组中。 将此TDE选项添加到选项组后，就无法将其删除。 TDE可以使用两种不同的加密模式，首先是TDE Tabrespace加密，该模式加密整个表，其次，TDE列加密仅加密数据库的各个元素。

# Amazon Kinesis Firehouse

＃亚马逊运动员消防

Amazon Firehose is used to deliver **real-time streaming data to different services** and destinations within AWS, many of which can be used for big data such as S3 Redshift and Amazon Elasticsearch.

Amazon Firehose用于将**实时流数据传递到AWS中的不同服务和目的地，其中许多可用于S3 RedShift和Amazon Elasticsearch等大数据。

The service is fully managed by AWS, taking a lot of the administration of maintenance out of your hands. Firehose is used to receive data from your data producers where it then automatically delivers the data to your chosen destination.

该服务完全由AWS管理，从您的手中掌握了许多维护管理。 FireHose用于接收您的数据生产者的数据，然后自动将数据传递到您选择的目的地。

Amazon Streams essentially collects and processes huge amounts of data in real time and makes it available for consumption.

Amazon流媒体基本上是在实时收集和处理大量数据，并使其可供消费。

This data can come from a variety of different sources. For example, log data from the infrastructure, social media, web clicks during feeds, market data, etc. So now we have a high-level overview of each of these. We need to understand how they implement encryption of any data process in stored should it be required.

这些数据可能来自各种不同的来源。 例如，来自基础架构，社交媒体，供稿，市场数据等的网络点击等日志数据。因此，现在我们对每一个都有高级概述。 我们需要了解他们如何在需要的情况下实施存储中任何数据过程的加密。

When clients are **sending data to Kinesis in transit**, the data can be sent over **HTTPS**, which is HTTP with SSL encryption. However, once it enters the Kinesis service, it is then unencrypted by default. Using both **Kinesis Streams and Firehose encryption, you can assure your streams remain encrypted up until the data is sent to its final destination.** As **Amazon Streams** now has the ability to implement SSE encryption using KMS to **encrypt data as it enters the stream** directly from the producers.

当客户端**将数据发送到运输中的Kinesis **时，可以通过** https **发送数据，该数据是带有SSL加密的HTTP。 但是，一旦进入运动式服务，默认情况下就不会加密它。 使用**运动流和Firehose加密，您可以确保您的流保持加密，直到将数据发送到最终目的地为止。 直接从生产者进入流**时，加密数据。

If Amazon **S3** is used as a **destination**, Firehose can implement encryption using **SSE-KMS on S3**.

如果Amazon ** S3 **用作**目的地**，则FireHose可以使用S3 **上的** SSE-KMS实现加密。

As a part of this process, it's important to ensure that both producer and consumer applications have permissions to use the KMS key. Otherwise encryption and decryption will not be possible, and you will receive an unauthorized KMS master key permission error.

作为此过程的一部分，重要的是要确保生产者和消费者应用都具有使用KMS密钥的权限。 否则，将不可能进行加密和解密，您将收到未经授权的KMS主密钥权限错误。

Kinesis SSE encryption will typically call upon KMS to **generate a new data key every five minutes**. So, if you had your stream running for a month or more, thousands of data keys would be generated within this time frame.

Kinesis SSE加密通常会要求KMS **每五分钟生成新的数据密钥**。 因此，如果您的流持续一个月或更长时间，将在此时间范围内生成数千个数据键。

# Amazon Redshift

＃亚马逊红移
Redshift is a fully managed service that can scale up to over a petabyte in size, which is used as a **data warehouse for big data solutions**. Using Redshift clusters, you are able to run analytics against your datasets using fast, SQL-based query tools and business intelligence applications to gather greater understanding of vision for your business.

RedShift是一项完全管理的服务，可以扩展到大小的超过bet，用作大数据解决方案的**数据仓库**。 使用红移簇，您可以使用快速的，基于SQL的查询工具和商业智能应用程序对数据集进行分析，以收集对业务愿景的更多了解。

**Redshift offers encryption at rest using a four-tired hierarchy of encryption keys using either KMS or CloudHSM to manage the top tier of keys**. **When encryption is enabled for your cluster, it can't be disable and vice versa**. When you have an unencrypted cluster, it can't be encrypted.

** RedShift使用KMS或CloudHSM的四个式加密密钥的层次结构在REST上提供加密，以管理键的顶级键**。 **当您的群集启用加密时，它不能禁用，反之亦然**。 当您有一个未加密的群集时，它就无法加密。

Encryption for your cluster can only happen during its creation, and once encrypted, the data, metadata, and any snapshots are also encrypted. The tiering level of encryption keys are as follows, **tier one is the master key, tier two is the cluster encryption key, the CEK, tier three, the database encryption key, the DEK, and finally tier four, the data encryption keys themselves**.

群集的加密只能在其创建过程中发生，一旦加密，数据，元数据和任何快照也将被加密。 加密密钥的层级级别如下，**层是主密钥，第二层是群集加密密钥，CEK，CEK，第三层，数据库加密密钥，DEK，DEK，最后是第四层，数据加密密钥密钥键。 他们自己**。

## KMS

During the creation of your cluster, you can either select the **default KMS key** for Redshift or select your **own CMK**, which gives you more flexibility over the control of the key, specifically from an auditable perspective.

在创建群集期间，您可以选择**默认的kms键**，或者选择自己的**自己的cmk **，这使您更加灵活地对钥匙的控制，特别是从可视化的角度来看。

The default KMS key for Redshift is automatically created by Redshift the first time the key option is selected and used, and it is fully managed by AWS. The CMK is known as the master key, tier one, and once selected, Redshift can enforce the encryption process as follows. So Redshift will send a request to KMS for a new KMS key.

RedShift首次选择和使用键选项，并使用AWS对RedShift自动创建默认的KMS密钥。 CMK被称为主键，一级，一旦选择，RedShift可以如下执行加密过程。 因此，RedShift将向KMS发送新的KMS密钥的请求。

So Redshift will send a request to KMS for a new KMS key.

因此，RedShift将向KMS发送新的KMS密钥的请求。

This KMS key is then encrypted with the CMK master key, tier one. This encrypted KMS data key is then used as the cluster encryption key, the CEK, tier two. This CEK is then sent by KMS to Redshift where it is stored separately from the cluster. Redshift then sends this encrypted CEK to the cluster over a secure channel where it is stored in memory.

然后，使用CMK Master键（层）对此KMS密钥进行加密。 然后将此加密的KMS数据密钥用作群集加密密钥，即CEK，第二层。 然后，KMS将此Cek发送到RedShift，其中与群集分开存储。 然后，RedShift将此加密的CEK发送到将其存储在内存中的安全通道上的群集。

Redshift then requests KMS to decrypt the CEK, tier two. This decrypted CEK is then also stored in memory. Redshift then creates a random database encryption key, the DEK, tier three, and loads that into the memory of the cluster. The decrypted CEK in memory then encrypts the DEK, which is also stored in memory.

然后，RedShift要求KMS解密Cek，第二层。 然后，该解密的CEK也存储在内存中。 然后，RedShift创建一个随机数据库加密密钥，DEK，第三层，并将其加载到集群的内存中。 然后，在内存中解密的CEK然后加密了DEK，该DEK也存储在内存中。

This encrypted DEK is then sent over a secure channel and stored in Redshift separately from the cluster. Both the CEK and the DEK are now stored in memory of the cluster both in an encrypted and decrypted form. The decrypted DEK is then used to encrypt data keys, tier four, that are randomly generated by Redshift for each data block in the database.

然后将此加密的DEK发送通过安全通道，并与群集分开存储在红移中。 现在，CEK和DEK都以加密和解密的形式存储在群集中。 然后使用解密的DEK来加密第四层数据键，这些密钥是由RedShift随机生成数据库中每个数据块的。

You can use AWS Trusted Advisor to monitor the configuration of your Amazon S3 buckets and ensure that bucket logging is enabled, which can be useful for performing security audits and tracking usage patterns in S3.

您可以使用AWS Trust Advisor监视Amazon S3存储桶的配置，并确保启用存储桶记录，这对于执行安全审核和跟踪S3中的使用模式很有用。

## CloudHSM

## Cloudhsm

When working with CloudHSM to perform your encryption, firstly you must set up a trusted connection between your HSM client and Redshift while using client and server certificates.

使用CloudHSM执行您的加密时，首先，在使用客户端和服务器证书时，必须在HSM客户端和RedShift之间建立可信赖的连接。

This connection is required to provide secure communications, allowing encryption keys to be sent between your HSM client and your Redshift clusters. Using a randomly generated private and public key pair, Redshift creates a public client certificate, which is encrypted and stored by Redshift. This must be downloaded and registered to your HSM client, and assigned to the correct HSM partition.

需要此连接以提供安全的通信，从而使您的HSM客户端和红移簇之间发送加密密钥。 RedShift使用随机生成的私钥和公共密钥对创建公共客户端证书，该证书由RedShift加密和存储。 必须下载并注册给您的HSM客户端，并分配给正确的HSM分区。

You must then configure Redshift with the following details of your HSM client: the HSM IP address, the HSM partition name, the HSM partition password, and the public HSM server certificate, which is encrypted by CloudHSM using an internal master key. Once this information has been provided, Redshift will confirm and verify that it can connect and access development partition.

然后，您必须使用HSM客户端的以下详细信息配置RedShift：HSM IP地址，HSM分区名称，HSM分区密码和公共HSM Server证书，该证书是使用内部主密钥加密的。 提供此信息后，RedShift将确认并验证它可以连接和访问开发分区。

If your internal security policies or governance controls dictate that you must apply key rotation, then this is possible with Redshift enabling you to rotate encryption keys for encrypted clusters, however, you do need to be aware that during the key rotation process, it will make a cluster unavailable for a very short period of time, and so it's best to only rotate keys as and when you need to, or if you feel they may have been compromised.

如果您的内部安全策略或治理控制要求您必须应用钥匙旋转，那么RedShift可以使您能够为加密簇旋转加密键，但是，您确实需要意识到，在密钥旋转过程中，它将使得它使得它会产生 一个群集在很短的时间内不可用，因此最好只在需要时旋转钥匙，或者如果您觉得它们可能受到损害。

During the rotation, Redshift will rotate the CEK for your cluster and for any backups of that cluster. It will rotate a DEK for the cluster but it's not possible to rotate a DEK for the snapshots stored in S3 that have been encrypted using the DEK. It will put the cluster into a state of 'rotating keys' until the process is completed when the status will return to 'available'.

在旋转过程中，红移将为您的群集和该群集的任何备份旋转CEK。 它将为群集旋转一个DEK，但不可能为使用DEK加密的S3中存储的快照旋转DEK。 它将将群集放入“旋转密钥”的状态，直到当状态返回“可用”时完成该过程。

# WAF

AWS WAF is a web application firewall that helps **protect your web applications** or APIs against common web exploits that may affect availability, compromise security, or consume excessive resources. AWS WAF gives you control over **how traffic reaches your applications** by enabling you to create security rules that block common attack patterns, such as SQL injection or cross-site scripting, and rules that filter out specific traffic patterns you define.

AWS WAF是一种Web应用程序防火墙，可帮助**保护您的Web应用程序**或API免受可能影响可用性，损害安全性或消耗过多资源的常见Web利用。 AWS WAF通过使您能够创建阻止常见攻击模式的安全规则（例如SQL注入或跨站点脚本）来控制**流量如何到达应用程序**，以及过滤您定义的特定流量模式的规则。

So there are a number of essential components relating to WAF, these being: Conditions, Rules and Web access control lists, also known as Web ACLs

因此，有许多与WAF有关的基本组件，这些组件是：条件，规则和Web访问控制列表，也称为Web ACLS

## Conditions

＃＃ 条件

Conditions allow you to specify **what elements of the incoming HTTP or HTTPS request you want WAF to be monitoring** (XSS, GEO - filtering by location-, IP address, Size constraints, SQL Injection attacks, strings and regex matching). Note that if you are restricting a country from cloudfront, this request won't arrive to the waf.

条件允许您指定**传入的HTTP或HTTPS请求的哪些元素您希望WAF监视**（XSS，GEO-按位置，IP地址，尺寸约束，SQL注入攻击，字符串和Regex匹配）。 请注意，如果您将一个国家从CloudFront限制，则此请求将不会到达WAF。

You can have **100 conditions of each type**, such as Geo Match or size constraints, however **Regex** is the **exception** to this rule where **only 10 Regex** conditions are allowed but this limit is possible to increase. You are able to have **100 rules and 50 Web ACLs per AWS account**. You are limited to **5 rate-based-rules** per account. Finally you can have **10,000 requests per second** when **using WAF** within your application load balancer.

您可以拥有每种类型**的100条条件，例如GEO匹配或大小约束，但是** REGEX **是该规则的**例外**，其中**仅允许使用10个regex **条件，但是此 限制可以增加。 您可以拥有** 100规则和50个ACL每个AWS帐户**。 每个帐户中，您仅限于** 5个基于费率的规则**。 最后，当**在应用程序加载平衡器中使用waf **时，您可以每秒** 10,000请求。

## Rules

Using these conditions you can create rules: For example, block request if 2 conditions are met.\

使用这些条件您可以创建规则：例如，如果满足2个条件，则阻止请求。\ \
When creating your rule you will be asked to select a **Rule Type**: **Regular Rule** or **Rate-Based Rule**.

创建规则时，您将被要求选择**规则类型**：**常规规则**或**基于费率的规则**。

The only **difference** between a rate-based rule and a regular rule is that **rate-based** rules **count** the **number** of **requests** that are being received from a particular IP address over a time period of **five minutes**.

基于费率的规则和常规规则之间的唯一**差异**是**基于费率的**规则**计数** ** **请求**的** **五分钟**的一段时间内的特定IP地址。

When you select a rate-based rule option, you are asked to **enter the maximum number of requests from a single IP within a five minute time frame**. When the count limit is **reached**, **all other requests from that same IP address is then blocked**. If the request rate falls back below the rate limit specified the traffic is then allowed to pass through and is no longer blocked. When setting your rate limit it **must be set to a value above 2000**. Any request under this limit is considered a Regular Rule.

当您选择基于费率的规则选项时，要求您**在五分钟的时间范围内输入单个IP的最大请求数**。 当达到**的计数限制**时，**从同一IP地址的所有其他请求都会被阻止**。 如果请求率低于指定的速率限制，则允许流量通过，并且不再被阻止。 设置速率时，必须将其设置为超过2000 **的值。 此限制下的任何请求均被视为常规规则。

## Actions

##操作

An action is applied to each rule, these actions can either be **Allow**, **Block** or **Count**.

对每个规则应用了一个操作，这些操作可以**允许**，** block **或** count **。

* When a request is **allowed**, it is **forwarded** onto the relevant CloudFront distribution or Application Load Balancer.

*当允许** **请求时，它被**转发**到相关的云偏发或应用程序负载平衡器上。
* When a request is **blocked**, the request is **terminated** there and no further processing of that request is taken.

*当请求被**阻止**时，请求已被**终止**，并且没有进一步处理该请求。
* A **Count** action will **count the number of requests that meet the conditions** within that rule. This is a really good option to select when testing the rules to ensure that the rule is picking up the requests as expected before setting it to either Allow or Block.

*a **计数**行动将**计算满足条件**的请求的数量**。 在测试规则时，可以选择这是一个非常好的选择，以确保规则在将其设置为允许或阻止之前按预期拾取请求。

If an **incoming request does not meet any rule** within the Web ACL then the request takes the action associated to a **default action** specified which can either be **Allow** or **Block**. An important point to make about these rules is that they are **executed in the order that they are listed within a Web ACL**. So be careful to architect this order correctly for your rule base, **typically** these are **ordered** as shown:

如果“传入请求”不符合Web ACL中的任何规则**，则该请求将相关的操作采用指定的默认操作**，可以**允许**或** block **。 关于这些规则的重要一点是，它们是按照网络ACL **列出的顺序执行的。 因此，请小心为您的规则基础正确构建此订单，**通常**订购** **如下所示：

1. WhiteListed Ips as Allow.

1.白名单IPS允许。
2. BlackListed IPs Block

2.黑名单的IPS块
3. Any Bad Signatures also as Block.

3.任何不良签名也作为块。

## CloudWatch

## CloudWatch

WAF CloudWatch metrics are reported **in one minute intervals by default** and are kept for a two week period. The metrics monitored are AllowedRequests, BlockedRequests, CountedRequests, and PassedRequests.

WAF CloudWatch指标被报告为**默认情况下的一分钟间隔**，并保留了两个星期。 受监控的指标是允许的，阻塞的重点，countedRequests和通过的Quects。

# AWS Firewall Manager

AWS Firewall Manager simplifies your administration and maintenance tasks across multiple accounts and resources for **AWS WAF, AWS Shield Advanced, Amazon VPC security groups, and AWS Network Firewall**. With Firewall Manager, you set up your AWS WAF firewall rules, Shield Advanced protections, Amazon VPC security groups, and Network Firewall firewalls just once. The service **automatically applies the rules and protections across your accounts and resources**, even as you add new resources.

AWS防火墙经理简化了您的管理和维护任务，这些账户和资源跨越了** AWS WAF，AWS Shield Advanced，Amazon VPC安全组和AWS Network Network Firewall **。 使用防火墙管理器，您仅一次设置AWS WAF防火墙规则，Shield Advance Protections，Amazon VPC安全组和网络防火墙防火墙一次。 服务**即使您添加新资源，也会自动应用您的帐户和资源的规则和保护。

It can **group and protect specific resources together**, for example, all resources with a particular tag or all of your CloudFront distributions. One key benefit of Firewall Manager is that it **automatically protects certain resources that are added** to your account as they become active.

它可以**组合和保护特定资源**，例如，所有具有特定标签或所有云方面分布的资源。 防火墙经理的一个关键好处是，它**自动保护某些在您的帐户中添加的资源，它们变得活跃。

**Requisites**: Created a Firewall Manager Master Account, setup an AWS organization and have added our member accounts and enable AWS Config.

**要求**：创建一个防火墙管理器主帐户，设置AWS组织，并添加了我们的会员帐户并启用AWS配置。

A **rule group** (a set of WAF rules together) can be added to an AWS Firewall Manager Policy which is then associated to AWS resources, such as your cloudfront distributions or application load balances.

一个**规则组**（一组WAF规则）可以添加到AWS防火墙管理器策略中，然后与AWS资源相关联，例如您的CloudFront Distributions或应用程序负载余额。

**Firewall Manager policies only allow "Block" or "Count"** options for a rule group (no "Allow" option).

**防火墙管理器策略仅允许规则组的“块”或“计数” **选项（否“允许”选项）。

# AWS Shield

AWS Shield has been designed to help **protect your infrastructure against distributed denial of service attacks**, commonly known as DDoS.

AWS Shield旨在帮助**保护您的基础架构免受分布式拒绝服务攻击**（通常称为DDOS）。

**AWS Shield Standard** is **free** to everyone, and it offers DDoS **protection** against some of the more common layer three, the **network layer**, and layer four, **transport layer**, DDoS attacks. This protection is integrated with both CloudFront and Route 53.

** AWS盾牌标准**是**免费**，它提供了DDOS **保护**针对某些更常见的第三层，**网络层**和第四层，**运输层 **，DDOS攻击。 该保护与云方和53号公路均集成在一起。

**AWS Shield advanced** offers a **greater level of protection** for DDoS attacks across a wider scope of AWS services for an additional cost. This advanced level offers protection against your web applications running on EC2, CloudFront, ELB and also Route 53. In addition to these additional resource types being protected, there are enhanced levels of DDoS protection offered compared to that of Standard. And you will also have **access to a 24-by-seven specialized DDoS response team at AWS, known as DRT**.

** AWS Shield Advanced **为DDOS攻击提供了更高的保护**，以付出更多的AWS服务范围。 该高级级别提供了针对在EC2，CloudFront，ELB和Route 53上运行的Web应用程序的保护。除了受到保护的其他资源类型外，与标准相比，提供了增强的DDOS保护级别。 而且，您还可以在AWS（被称为Drt **）的24厘米专用DDOS响应团队中访问。

Whereas the Standard version of Shield offered protection against layer three and layer four, **Advanced also offers protection against layer seven, application, attacks.**

盾牌的标准版本提供了针对第三层和第四层的保护，**也提供了第七层，应用程序，攻击的保护。**

# VPN

## Site-to-Site VPN

**Connect your on premisses network with your VPC.**

**与您的VPC连接您的前提网络。**

### Concepts

###概念

* **VPN connection**: A secure connection between your on-premises equipment and your VPCs.
*   **VPN tunnel**: An encrypted link where data can pass from the customer network to or from AWS.

*** VPN隧道**：一个加密的链接，数据可以从客户网络传递到AWS。

    Each VPN connection includes two VPN tunnels which you can simultaneously use for high availability.

每个VPN连接都包含两个VPN隧道，您可以同时使用这些隧道以进行高可用性。
* **Customer gateway**: An AWS resource which provides information to AWS about your customer gateway device.

***客户网关**：AWS资源，向AWS提供有关客户网关设备的信息。
* **Customer gateway device**: A physical device or software application on your side of the Site-to-Site VPN connection.

***客户网关设备**：网站对站点VPN连接的物理设备或软件应用程序。
* **Virtual private gateway**: The VPN concentrator on the Amazon side of the Site-to-Site VPN connection. You use a virtual private gateway or a transit gateway as the gateway for the Amazon side of the Site-to-Site VPN connection.

***虚拟私人网关**：站点对站点VPN连接的亚马逊侧的VPN浓缩器。 您可以使用虚拟的私人网关或运输网关作为站点对站点VPN连接的亚马逊侧的网关。
* **Transit gateway**: A transit hub that can be used to interconnect your VPCs and on-premises networks. You use a transit gateway or virtual private gateway as the gateway for the Amazon side of the Site-to-Site VPN connection.

***运输网关**：可用于互连您的VPC和本地网络的公交中心。 您可以将运输网关或虚拟私人网关用作站点对站点VPN连接的亚马逊侧的网关。

### Limitations

* IPv6 traffic is not supported for VPN connections on a virtual private gateway.

*虚拟私人网关上的VPN连接不支持IPv6流量。
* An AWS VPN connection does not support Path MTU Discovery.

* AWS VPN连接不支持路径MTU发现。

In addition, take the following into consideration when you use Site-to-Site VPN.

此外，当您使用站点到站点的VPN时，请考虑以下内容。

* When connecting your VPCs to a common on-premises network, we recommend that you use non-overlapping CIDR blocks for your networks.

*将VPC连接到普通的本地网络时，我们建议您为网络使用非重叠的CIDR块。

## Components of Client VPN <a href="#what-is-components" id="what-is-components"></a>

##客户端vpn <a href="#what-is-components" id="what-is-components"> </a>

**Connect from your machine to your VPC**

**从机器连接到VPC **

### Concepts

###概念

* **Client VPN endpoint:** The resource that you create and configure to enable and manage client VPN sessions. It is the resource where all client VPN sessions are terminated.

***客户端VPN端点：**您创建和配置以启用和管理客户端VPN会话的资源。 这是所有客户端VPN会话终止的资源。
* **Target network:** A target network is the network that you associate with a Client VPN endpoint. **A subnet from a VPC is a target network**. Associating a subnet with a Client VPN endpoint enables you to establish VPN sessions. You can associate multiple subnets with a Client VPN endpoint for high availability. All subnets must be from the same VPC. Each subnet must belong to a different Availability Zone.

***目标网络：**目标网络是您与客户端VPN端点关联的网络。 **来自VPC的子网是目标网络**。 将子网与客户端VPN端点关联，使您可以建立VPN会话。 您可以将多个子网与客户端VPN端点相关联，以获得高可用性。 所有子网都必须来自同一VPC。 每个子网必须属于不同的可用性区。
* **Route**: Each Client VPN endpoint has a route table that describes the available destination network routes. Each route in the route table specifies the path for traffic to specific resources or networks.

***路由**：每个客户端VPN端点都有一个路由表，可描述可用目标网络路由。 路由表中的每个路由都指定了通往特定资源或网络的流量的路径。
* **Authorization rules:** An authorization rule **restricts the users who can access a network**. For a specified network, you configure the Active Directory or identity provider (IdP) group that is allowed access. Only users belonging to this group can access the specified network. **By default, there are no authorization rules** and you must configure authorization rules to enable users to access resources and networks.

***授权规则：**授权规则**限制可以访问网络的用户**。 对于指定的网络，您可以配置允许访问的Active Directory或Identity Provider（IDP）组。 只有属于此组的用户才能访问指定的网络。 **默认情况下，没有授权规则**，您必须配置授权规则以使用户能够访问资源和网络。
* **Client:** The end user connecting to the Client VPN endpoint to establish a VPN session. End users need to download an OpenVPN client and use the Client VPN configuration file that you created to establish a VPN session.

***客户端：**最终用户连接到客户端VPN端点以建立VPN会话。 最终用户需要下载OpenVPN客户端，并使用为建立VPN会话创建的客户端VPN配置文件。
* **Client CIDR range:** An IP address range from which to assign client IP addresses. Each connection to the Client VPN endpoint is assigned a unique IP address from the client CIDR range. You choose the client CIDR range, for example, `10.2.0.0/16`.

***客户端CIDR范围：** IP地址范围从中分配客户端IP地址。 与客户端VPN端点的每个连接都分配了客户端CIDR范围的唯一IP地址。 您选择客户端CIDR范围，例如`10.2.0.0/16`。
* **Client VPN ports:** AWS Client VPN supports ports 443 and 1194 for both TCP and UDP. The default is port 443.

***客户端VPN端口：** AWS客户端VPN支持TCP和UDP的端口443和1194。 默认值为端口443。
* **Client VPN network interfaces:** When you associate a subnet with your Client VPN endpoint, we create Client VPN network interfaces in that subnet. **Traffic that's sent to the VPC from the Client VPN endpoint is sent through a Client VPN network interface**. Source network address translation (SNAT) is then applied, where the source IP address from the client CIDR range is translated to the Client VPN network interface IP address.

***客户端VPN网络接口：**当您将子网与客户端VPN端点关联时，我们在该子网中创建客户端VPN网络接口。 **从客户端VPN端点发送到VPC的流量通过客户端VPN网络接口发送。 然后应用源网络地址转换（SNAT），其中客户端CIDR范围的源IP地址转换为客户端VPN网络接口IP地址。
* **Connection logging:** You can enable connection logging for your Client VPN endpoint to log connection events. You can use this information to run forensics, analyze how your Client VPN endpoint is being used, or debug connection issues.

***连接日志记录：**您可以启用Connection Loggging您的客户端VPN端点以记录连接事件。 您可以使用此信息来运行取证，分析如何使用客户端VPN端点或调试连接问题。
* **Self-service portal:** You can enable a self-service portal for your Client VPN endpoint. Clients can log into the web-based portal using their credentials and download the latest version of the Client VPN endpoint configuration file, or the latest version of the AWS provided client.

***自助服务门户：**您可以为客户端VPN端点启用一个自助门户。 客户端可以使用其凭据登录基于Web的门户，并下载客户VPN端点配置文件的最新版本或最新版本的AWS提供的客户端。

### Limitations

* **Client CIDR ranges cannot overlap with the local CIDR** of the VPC in which the associated subnet is located, or any routes manually added to the Client VPN endpoint's route table.

***客户端CIDR范围不能与关联子网所在的VPC的本地CIDR **重叠，或者手动添加到客户端VPN Endpoint的路由表中的任何路由。
* Client CIDR ranges must have a block size of at **least /22** and must **not be greater than /12.**

*客户端CIDR范围必须具有**最差 /22 **的块大小，并且必须**不大于/12.**********************
* A **portion of the addresses** in the client CIDR range are used to **support the availability** model of the Client VPN endpoint, and cannot be assigned to clients. Therefore, we recommend that you **assign a CIDR block that contains twice the number of IP addresses that are required** to enable the maximum number of concurrent connections that you plan to support on the Client VPN endpoint.

*a **地址的部分**在客户端CIDR范围内用于**支持客户端VPN端点的可用性**模型，并且不能分配给客户端。 因此，我们建议您**分配一个CIDR块，其中包含所需的IP地址数量的两倍，以启用您计划在客户端VPN端点上支持的最大并发连接数。
* The **client CIDR range cannot be changed** after you create the Client VPN endpoint.

***端CIDR范围无法更改**在您创建客户端VPN端点后。
* The **subnets** associated with a Client VPN endpoint **must be in the same VPC**.

*与客户端VPN端点相关的**子网**必须在同一VPC **中。
* You **cannot associate multiple subnets from the same Availability Zone with a Client VPN endpoint**.

*您**无法将同一可用性区域的多个子网与客户端VPN端点**相关联。
* A Client VPN endpoint **does not support subnet associations in a dedicated tenancy VPC**.

*客户端VPN端点**不支持专用租赁VPC **中的子网关联。
* Client VPN supports **IPv4** traffic only.

*客户端VPN支持** IPv4 **流量。
* Client VPN is **not** Federal Information Processing Standards (**FIPS**) **compliant**.

*客户vpn是** **联邦信息处理标准（** fips **）**符合**。
*   If multi-factor authentication (MFA) is disabled for your Active Directory, a user password cannot be in the following format.

*如果您的Active Directory禁用了多因素身份验证（MFA），则用户密码不能采用以下格式。

    ```
    SCRV1:<base64_encoded_string>:<base64_encoded_string>

scrv1：<base64_encoded_string>：<base64_encoded_string>
    ```
* The self-service portal is **not available for clients that authenticate using mutual authentication**.

*自助服务门户**对于使用共同身份验证进行身份验证**的客户不可用。

# Amazon Cognito

Amazon Cognito provides **authentication, authorization, and user management** for your web and mobile apps. Your users can sign in directly with a **user name and password**, or through a **third party** such as Facebook, Amazon, Google or Apple.

Amazon Cognito为您的网络和移动应用程序提供**身份验证，授权和用户管理**。 您的用户可以直接使用**用户名和密码**登录，也可以通过**第三方**（例如Facebook，Amazon，Google或Apple）登录。

The two main components of Amazon Cognito are user pools and identity pools. **User pools** are user directories that provide **sign-up and sign-in options for your app users**. **Identity pools** enable you to grant your users **access to other AWS services**. You can use identity pools and user pools separately or together.

Amazon Cognito的两个主要组成部分是用户池和身份池。 **用户池**是用户目录，可为您的应用程序用户提供**注册和登录选项**。 **身份池**使您能够授予您的用户**访问其他AWS服务**。 您可以分别或一起使用身份池和用户池。

## **User pools**

A user pool is a user directory in Amazon Cognito. With a user pool, your users can **sign in to your web or mobile app** through Amazon Cognito, **or federate** through a **third-party** identity provider (IdP). Whether your users sign in directly or through a third party, all members of the user pool have a directory profile that you can access through an SDK.

用户池是Amazon Cognito中的用户目录。 使用用户池，您的用户可以通过Amazon Cognito，**或Federate **通过**第三方**身份提供商（IDP）登录您的Web或移动应用程序**。 无论您的用户是直接登录还是通过第三方登录，所有用户池的成员都有一个目录配置文件，您可以通过SDK访问。

User pools provide:

* Sign-up and sign-in services.

*注册和登录服务。
* A built-in, customizable web UI to sign in users.

*内置的可自定义Web UI，可签署用户。
* Social sign-in with Facebook, Google, Login with Amazon, and Sign in with Apple, and through SAML and OIDC identity providers from your user pool.

*与Facebook，Google，与Amazon登录的社交登录，并与Apple登录，并通过您的用户池中的SAML和OIDC身份提供商登录。
* User directory management and user profiles.

*用户目录管理和用户配置文件。
* Security features such as multi-factor authentication (MFA), checks for compromised credentials, account takeover protection, and phone and email verification.

*诸如多因素身份验证（MFA）之类的安全功能，检查凭据受损，帐户收购保护以及电话和电子邮件验证。
* Customized workflows and user migration through AWS Lambda triggers.

*定制的工作流和用户通过AWS lambda触发器迁移。

## **Identity pools**

## **身份池**

With an identity pool, your users can **obtain temporary AWS credentials to access AWS services**, such as Amazon S3 and DynamoDB. Identity pools support anonymous guest users, as well as the following identity providers that you can use to authenticate users for identity pools:

使用身份池，您的用户可以**获得临时AWS凭据来访问AWS服务**，例如Amazon S3和DynamoDB。 身份池支持匿名访客用户以及以下身份提供商，您可以用来对身份池进行身份验证用户：

* Amazon Cognito user pools
* Social sign-in with Facebook, Google, Login with Amazon, and Sign in with Apple

*与Facebook，Google，与Amazon登录并与Apple登录的社交登录
* OpenID Connect (OIDC) providers
* SAML identity providers

* SAML身份提供商
* Developer authenticated identities

*开发人员身份验证的身份

To save user profile information, your identity pool needs to be integrated with a user pool.

为了保存用户配置文件信息，您的身份池需要与用户池集成。


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


