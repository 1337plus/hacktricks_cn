# Basic Gitea Information

＃基本gitea信息

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

## Basic Structure

The basic gitea environment structure is to group repos by **organization(s),** each of them may contain **several repositories** and **several teams.** However, note that just like in github users can have repos outside of the organization.

基本的gitea环境结构是由**组织组成的组件，**每个人都可能包含**几个存储库**和**几个团队。 在组织之外。

Moreover, a **user** can be a **member** of **different organizations**. Within the organization the user may have **different permissions over each repository**.

此外，**用户**可以是**不同组织**的**成员。 在组织中，用户可能对每个存储库都具有不同的权限**。

A user may also be **part of different teams** with different permissions over different repos.

用户也可能是不同团队**的一部分，并且与不同的存储库相比具有不同的权限。

And finally **repositories may have special protection mechanisms**.

最后，**存储库可能具有特殊的保护机制**。

## Permissions

### Organizations

###组织

When an **organization is created** a team called **Owners** is **created** and the user is put inside of it. This team will give **admin access** over the **organization**, those **permissions** and the **name** of the team **cannot be modified**.

当创建一个**的组织**一个名为**所有者**的团队是**创建**，并且用户被放入其中。 该团队将在**组织**上提供**管理员访问**，这些**权限**和团队的**名称** **无法修改**。

**Org admins** (owners) can select the **visibility** of the organization:

** org管理员**（所有者）可以选择组织的可见性**：

* Public
* Limited (logged in users only)

*有限（仅登录用户）
* Private (members only)

*私人（仅成员）

**Org admins** can also indicate if the **repo admins** can **add and or remove access** for teams. They can also indicate the max number of repos.

** org管理员**还可以指示** repo admins **是否可以**添加和或删除团队的访问**。 他们还可以指示最大的存储库数。

When creating a new team, several important settings are selected:

创建新团队时，选择了几个重要的设置：

* It's indicated the **repos of the org the members of the team will be able to access**: specific repos (repos where the team is added) or all.

*指示团队成员将能够访问**：特定的存储库（添加团队的位置）或全部。
* It's also indicated **if members can create new repos** (creator will get admin access to it)

*它还指示**如果成员可以创建新的存储库**（创建者将获得管理员的访问）
* The **permissions** the **members** of the repo will **have**:

***权限** **仓库的成员**将**有**：
  * **Administrator** access

***管理员**访问
  * **Specific** access:

***特定**访问：

![](<../../.gitbook/assets/image (648) (1).png>)

### Teams & Users

###团队和用户

In a repo, the **org admin** and the **repo admins** (if allowed by the org) can **manage the roles** given to collaborators (other users) and teams. There are **3** possible **roles**:

在回购中，** org admin **和** repo admins **（如果由组织允许）可以**管理赋予合作者（其他用户）和团队的角色**。 有** 3 **可能的**角色**：

* Administrator
* Write
* Read

* 读

## Gitea Authentication

## Gitea身份验证

### Web Access

### Web访问

Using **username + password** and potentially (and recommended) a 2FA.

使用**用户名 +密码**，并可能（并推荐）2FA。

### **SSH Keys**

You can configure your account with one or several public keys allowing the related **private key to perform actions on your behalf.** [http://localhost:3000/user/settings/keys](http://localhost:3000/user/settings/keys)

您可以使用一个或几个公共键配置您的帐户，允许相关的**专用密钥代表您执行操作。 /用户/设置/键）

#### **GPG Keys**

You **cannot impersonate the user with these keys** but if you don't use it it might be possible that you **get discover for sending commits without a signature**.

您**无法使用这些键模拟用户**，但是如果您不使用它，则可能有可能您**发现在没有签名的情况下发送提交**。

### **Personal Access Tokens**

### **个人访问令牌**

You can generate personal access token to **give an application access to your account**. A personal access token gives full access over your account: [http://localhost:3000/user/settings/applications](http://localhost:3000/user/settings/applications)

您可以生成个人访问令牌，以**为您的帐户提供访问权限。 个人访问令牌可以通过您的帐户进行完整访问：[http：// localhost：3000/user/settings/apply]（http：// localhost：3000/user/settings/applications）

### Oauth Applications

### oauth应用程序

Just like personal access tokens **Oauth applications** will have **complete access** over your account and the places your account has access because, as indicated in the [docs](https://docs.gitea.io/en-us/oauth2-provider/#scopes), scopes aren't supported yet:

就像个人访问令牌** oauth应用程序**将在您的帐户和您的帐户可以访问的地方提供**完整的访问**，因为如[docs]中所示（https://docs.gitea.io/en -us/oauth2-provider/＃scopes），范围尚不支持：

![](<../../.gitbook/assets/image (662) (1).png>)

### Deploy keys

### Deploy keys

Deploy keys might have read-only or write access to the repo, so they might be interesting to compromise specific repos.

部署键可能只读或编写对存储库的访问权限，因此折衷特定的存储库可能很有趣。

## Branch Protections

##分支保护

Branch protections are designed to **not give complete control of a repository** to the users. The goal is to **put several protection methods before being able to write code inside some branch**.

分支保护措施旨在**不完全控制存储库**。 目的是**在能够在某些分支中编写代码之前，请使用几种保护方法。

The **branch protections of a repository** can be found in _https://localhost:3000/\<orgname>/\<reponame>/settings/branches_

**存储库的分支保护**可以在_ https：// localhost中找到：3000/\ <org name>/\ <repo name>/settings/branches _

{% hint style="info" %}

{％提示样式=“ info”％}
It's **not possible to set a branch protection at organization level**. So all of them must be declared on each repo.

**不可能在组织级别设置分支保护**。 因此，必须在每个存储库上声明所有这些。
{% endhint %}

Different protections can be applied to a branch (like to master):

可以将不同的保护措施应用于分支（例如主人）：

* **Disable Push**: No-one can push to this branch

***禁用推动**：没有人可以推到这个分支机构
* **Enable Push**: Anyone with access can push, but not force push.

***启用推动**：任何具有访问权限的人都可以推动，但不能强迫推动。
* **Whitelist Restricted Push**: Only selected users/teams can push to this branch (but no force push)

***白人限制推送**：只有选定的用户/团队才能推到该分支（但没有力量推动）
* **Enable Merge Whitelist**: Only whitelisted users/teams can merge PRs.

***启用合并白名单**：只有白名单的用户/团队才能合并PR。
* **Enable Status checks:** Require status checks to pass before merging.

***启用状态检查：**需要在合并之前通过状态检查。
* **Require approvals**: Indicate the number of approvals required before a PR can be merged.

***要求批准**：指示可以合并PR之前所需的批准数量。
* **Restrict approvals to whitelisted**: Indicate users/teams that can approve PRs.

***将批准限制为白名单**：指示可以批准PRS的用户/团队。
* **Block merge on rejected reviews**: If changes are requested, it cannot be merged (even if the other checks pass)

***块合并被拒绝的评论**：如果要求更改，则不能合并（即使其他支票通过）
* **Block merge on official review requests**: If there official review requests it cannot be merged

*** Block合并在官方审查请求中**：如果有官方审查请求，则无法合并
* **Dismiss stale approvals**: When new commits, old approvals will be dismissed.

***解雇陈旧的批准**：当新提交时，旧批准将被驳回。
* **Require Signed Commits**: Commits must be signed.

***要求签名提交**：必须签署提交。
* **Block merge if pull request is outdated**

***块合并如果拉动请求已过时**
* **Protected/Unprotected file patterns**: Indicate patterns of files to protect/unprotect against changes

***受保护/未受保护的文件模式**：指示文件模式以保护/没有保护免受更改

{% hint style="info" %}

{％提示样式=“ info”％}
As you can see, even if you managed to obtain some credentials of a user, **repos might be protected avoiding you to pushing code to master** for example to compromise the CI/CD pipeline.

如您所见，即使您设法获得了用户的一些凭据，** repos可能会受到保护，避免您将代码推向主**，例如损害CI/CD管道。
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
