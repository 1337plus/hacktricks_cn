

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


# What is Gitea

＃什么是gitea

**Gitea** is a **self-hosted community managed lightweight code hosting** solution written in Go.

** gitea **是一个自托管社区托管轻量级代码托管**编写的解决方案。

![](<../../.gitbook/assets/image (655).png>)

## Basic Information

＃＃ 基本信息

{% content-ref url="basic-gitea-information.md" %}

{％content-ref url =“ basic-gitea-information.md”％}
[basic-gitea-information.md](basic-gitea-information.md)

[basic-gitea-information.md]（基本gitea-information.md）
{% endcontent-ref %}

# Lab

To run a Gitea instance locally you can just run a docker container:

要在本地运行Gitea实例，您只需运行Docker容器：

```bash
docker run -p 3000:3000 gitea/gitea
```

Connect to port 3000 to access the web page.

连接到端口3000以访问网页。

You could also run it with kubernetes:

您也可以使用Kubernetes运行它：

```
helm repo add gitea-charts https://dl.gitea.io/charts/
helm install gitea gitea-charts/gitea
```

# Unauthenticated Enumeration

＃未经身分的枚举

* Public repos: [http://localhost:3000/explore/repos](http://localhost:3000/explore/repos)
* Registered users: [http://localhost:3000/explore/users](http://localhost:3000/explore/users)

*注册用户：[http：// localhost：3000/explore/用户]
* Registered Organizations: [http://localhost:3000/explore/organizations](http://localhost:3000/explore/organizations)

*注册组织：[http：// localhost：3000/explore/组织]（http：// localhost：3000/explore/ablowerations）

Note that by **default Gitea allows new users to register**. This won't give specially interesting access to the new users over other organizations/users repos, but a **logged in user** might be able to **visualize more repos or organizations**.

请注意，默认Gitea允许新用户注册**。 这不会使其他组织/用户存储库与新用户特别有趣，但是登录用户**可能可以**可视化更多的存储库或组织**。

# Internal Exploitation

＃内部开发

For this scenario we are going to suppose that you have obtained some access to a github account.

对于这种情况，我们将假设您已经获得了对GitHub帐户的一些访问权限。

## With User Credentials/Web Cookie

##带有用户凭据/Web Cookie

If you somehow already have credentials for a user inside an organization (or you stole a session cookie) you can **just login** and check which which **permissions you have** over which **repos,** in **which teams** you are, **list other users**, and **how are the repos protected.**

如果您以某种方式已经为组织内部的用户（或者偷走了会话cookie）具有凭据，则可以**登录**，并检查您拥有哪个**权限**，**在**中** ** 您是哪个团队**，**列出其他用户**，以及**如何受到保护。**

Note that **2FA may be used** so you will only be able to access this information if you can also **pass that check**.

请注意，** 2FA可以使用**，因此，如果您还可以**通过该检查**，则只能访问此信息。

{% hint style="info" %}

{％提示样式=“ info”％}
Note that if you **manage to steal the `i_like_gitea` cookie** (currently configured with SameSite: Lax) you can **completely impersonate the user** without needing credentials or 2FA.

请注意，如果您**设法窃取`i_like_gitea` cookie **（当前使用samesite：lax配置），则可以完全**完全模仿用户**，而无需凭据或2FA。
{% endhint %}

## With User SSH Key

##使用用户SSH键

Gitea allows **users** to set **SSH keys** that will be used as **authentication method to deploy code** on their behalf (no 2FA is applied).

gitea允许**用户**设置** ssh键**，它将用作**身份验证方法来代表他们部署代码**（不应用2FA）。

With this key you can perform **changes in repositories where the user has some privileges**, however you can not use it to access gitea api to enumerate the environment. However, you can **enumerate local settings** to get information about the repos and user you have access to:

使用此密钥，您可以在用户具有一些特权**的存储库中执行**更改，但是您无法使用它来访问Gitea API来枚举环境。 但是，您可以**枚举本地设置**，以获取有关您可以访问的存储库和用户的信息：

```bash
# Go to the the repository folder
# Get repo config and current user name and email
git config --list
```

If the user has configured its username as his gitea username you can access the **public keys he has set** in his account in _https://github.com/\<gitea\_username>.keys_, you could check this to confirm the private key you found can be used.

如果用户将其用户名配置为他的gitea用户名，则可以访问他在_https：//github.com/ \ <gitea \ _username> .keys_中的帐户中设置**的**公共键。 确认可以使用您发现的私钥。

**SSH keys** can also be set in repositories as **deploy keys**. Anyone with access to this key will be able to **launch projects from a repository**. Usually in a server with different deploy keys the local file **`~/.ssh/config`** will give you info about key is related.

** SSH键**也可以在存储库中设置为**部署键**。 任何可以访问此密钥的人都可以**从存储库**启动项目。 通常在具有不同部署密钥的服务器中，本地文件**〜/.ssh/config` **将为您提供有关密钥的信息。

### GPG Keys

As explained [**here**](../github-security/basic-github-information.md#ssh-keys) sometimes it's needed to sign the commits or you might get discovered.

如[**在这里**]（../ github-security/basic-github-information.md＃ssh-keys）有时需要签署提交或您可能会被发现。

Check locally if the current user has any key with:

在本地检查当前用户是否有任何密钥：

```shell
gpg --list-secret-keys --keyid-format=long
```

## With User Token

For an introduction about [**User Tokens check the basic information**](basic-gitea-information.md#personal-access-tokens).

有关[**用户令牌检查基本信息**]（基本gitea-information.md＃personal-access-tokens）的介绍。

A user token can be used **instead of a password** to **authenticate** against Gitea server [**via API**](https://try.gitea.io/api/swagger#/). it will has **complete access** over the user.

可以使用用户令牌**而不是密码**来**对gitea Server [**通过api **]（https://try.gitea.io/api/api/swagger#/）进行身份验证**。 它将在用户上获得**完整的访问**。

## With Oauth Application

##带有Oauth应用程序

For an introduction about [**Gitea Oauth Applications check the basic information**](basic-gitea-information.md#oauth-applications).

有关[** gitea oauth应用程序的介绍，请检查基本信息**]（基本gitea-information.md＃oauth-applications）。

An attacker might create a **malicious Oauth Application** to access privileged data/actions of the users that accepts them probably as part of a phishing campaign.

攻击者可能会创建一个恶意的OAuth应用程序**，以访问可能作为网络钓鱼活动的一部分接受用户的特权数据/动作。

As explained in the basic information, the application will have **full access over the user account**.

如基本信息中所述，该应用程序将对用户帐户**具有完整访问权限。

## Branch Protection Bypass

##分支保护旁路

In Github we have **github actions** which by default get a **token with write access** over the repo that can be used to **bypass branch protections**. In this case that **doesn't exist**, so the bypasses are more limited. But lets take a look to what can be done:

在github中，我们有** github操作**，默认情况下，它可以通过写入访问权限**在库存上获得** token，该回购可以用来**绕过分支保护**。 在这种情况下，**不存在**，因此旁路更加有限。 但是让我们看看可以做什么：

* **Enable Push**: If anyone with write access can push to the branch, just push to it.

***启用推送**：如果有人可以将访问权限推到分支，则只需推到它。
* **Whitelist Restricted Pus**h: The same way, if you are part of this list push to the branch.

***白人限制的脓液** h：如果您是此列表的一部分，则以同样的方式推入分支机构。
* **Enable Merge Whitelist**: If there is a merge whitelist, you need to be inside of it

***启用合并白名单**：如果有合并白名单，您需要在其中
* **Require approvals is bigger than 0**: Then... you need to compromise another user

***要求批准大于0 **：然后...您需要妥协另一个用户
* **Restrict approvals to whitelisted**: If only whitelisted users can approve... you need to compromise another user that is inside that list

***将批准限制为白名单**：如果只有白名单用户才能批准...您需要妥协该列表中的另一个用户
* **Dismiss stale approvals**: If approvals are not removed with new commits, you could hijack an already approved PR to inject your code and merge the PR.

***解雇陈旧的批准**：如果未通过新提交删除批准，则可以劫持已经批准的PR来注入您的代码并合并PR。

Note that **if you are an org/repo admin** you can bypass the protections.

请注意，**如果您是组织/repo管理员**，则可以绕过保护措施。

## Enumerate Webhooks

**Webhooks** are able to **send specific gitea information to some places**. You might be able to **exploit that communication**.\

** Webhooks **可以**将特定的Gitea信息发送到某些地方**。 您可能可以**利用该通信**。
However, usually a **secret** you can **not retrieve** is set in the **webhook** that will **prevent** external users that know the URL of the webhook but not the secret to **exploit that webhook**.\

但是，通常一个**秘密**您可以**检索**在** webhook **中设置了** **可以防止**知道Webhook的URL的外部用户，而不是** exploit的秘诀 那个webhook **。\
But in some occasions, people instead of setting the **secret** in its place, they **set it in the URL** as a parameter, so **checking the URLs** could allow you to **find secrets** and other places you could exploit further.

但是在某些情况下，人们没有将**秘密**设置在其位置，而是将其设置在url **中为参数，因此**检查URL **可以让您**找到秘密** *以及您可以进一步利用的其他地方。

Webhooks can be set at **repo and at org level**.

可以在** repo和org级别**设置Webhooks。

# Post Exploitation

## Inside the server

##服务器内部

If somehow you managed to get inside the server where gitea is running you should search for the gitea configuration file. By default it's located in `/data/gitea/conf/app.ini`

如果您设法以某种方式进入Gitea正在运行的服务器内部，则应搜索Gitea配置文件。 默认情况下，它位于`/data/gitea/conf/app.ini`中

In this file you can find **keys** and **passwords**.

在此文件中，您可以找到**键**和**密码**。

In the gitea path (by default: /data/gitea) you can find also interesting information like:

在gitea路径（默认情况下： /data /gitea）您还可以找到有趣的信息，例如：

* The **sqlite** DB: If gitea is not using an external db it will use a sqlite db

*** sqlite ** db：如果Gitea不使用外部DB，它将使用SQLITE DB
* The **sessions** inside the sessions folder: Running `cat sessions/*/*/*` you can see the usernames of the logged users (gitea could also save the sessions inside the DB).

*** sessions **会话文件夹中的**：运行`cat sessions/*/*/*`您可以看到已记录的用户的用户名（Gitea也可以在DB中保存会话）。
* The **jwt private key** inside the jwt folder

*** JWT私钥**在JWT文件夹中
* More **sensitive information** could be found in this folder

*更多**敏感信息**可以在此文件夹中找到

If you are inside the server you can also **use the `gitea` binary** to access/modify information:

如果您在服务器内部，也可以**使用``gitea binary*''访问/修改信息：

* `gitea dump` will dump gitea and generate a .zip file
* `gitea generate secret INTERNAL_TOKEN/JWT_SECRET/SECRET_KEY/LFS_JWT_SECRET` will generate a token of the indicated type (persistence)

*`gitea生成秘密internal_token/jwt_secret/secret_key/lfs_jwt_secret`将生成指示类型的令牌（持久性）
* `gitea admin user change-password --username admin --password newpassword` Change the password

*`gitea管理员用户更改password -username admin -password newPassword“更改密码
* `gitea admin user create --username newuser --password superpassword --email user@user.user --admin --access-token` Create new admin user and get an access token

*`gitea管理员用户创建 -  username newuser -password superpassword -email user@user.user-admin -admin -Access-token`创建新的管理用户并获取访问令牌


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


