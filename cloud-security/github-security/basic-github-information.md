

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


# Basic Structure

The basic github environment structure of a big **company** is to own an **enterprise** which owns **several organizations** and each of them may contain **several repositories** and **several teams.**. Smaller companies may just **own one organization and no enterprises**.

一个大**公司**的基本github环境结构是拥有一个**企业**，它拥有**几个组织**，每个组织都可能包含**几个存储库**和**几个团队。** ** 。 较小的公司可能只是**拥有一个组织，而没有企业**。

From a user point of view a **user** can be a **member** of **different enterprises and organizations**. Within them the user may have **different enterprise, organization and repository roles**.

从用户的角度来看，**用户**可以是**不同企业和组织**的**成员**。 在其中，用户可能具有**不同的企业，组织和存储库角色**。

Moreover, a user may be **part of different teams** with different enterprise, organization or repository roles.

此外，用户可能是具有不同企业，组织或存储库角色的不同团队**的一部分。

And finally **repositories may have special protection mechanisms**.

最后，**存储库可能具有特殊的保护机制**。

# Privileges

＃特权

## Enterprise Roles

* **Enterprise owner**: People with this role can **manage administrators, manage organizations within the enterprise, manage enterprise settings, enforce policy across organizations**. However, they **cannot access organization settings or content** unless they are made an organization owner or given direct access to an organization-owned repository

***企业所有者**：具有此角色的人可以**管理管理员，管理企业内的组织，管理企业设置，跨组织执行策略**。 但是，他们**无法访问组织设置或内容**，除非他们成为组织所有者或直接访问组织拥有的存储库
* **Enterprise members**: Members of organizations owned by your enterprise are also **automatically members of the enterprise**.

***企业成员**：您的企业拥有的组织成员也是企业的成员**。

## Organization Roles

##组织角色

In an organisation users can have different roles:

在组织中，用户可以担任不同的角色：

* **Organization owners**: Organization owners have **complete administrative access to your organization**. This role should be limited, but to no less than two people, in your organization.

***组织所有者**：组织所有者**完全对您的组织的管理访问**。 这个角色应受到限制，但在您的组织中不少于两个人。
* **Organization members**: The **default**, non-administrative role for **people in an organization** is the organization member. By default, organization members **have a number of permissions**.

***组织成员**：**默认**，组织中的人**的非管理角色**是组织成员。 默认情况下，组织成员**具有许多权限**。
* **Billing managers**: Billing managers are users who can **manage the billing settings for your organization**, such as payment information.

***计费经理**：计费经理是可以**管理您组织的计费设置的用户**，例如付款信息。
* **Security Managers**: It's a role that organization owners can assign to any team in an organization. When applied, it gives every member of the team permissions to **manage security alerts and settings across your organization, as well as read permissions for all repositories** in the organization.

***安全经理**：这是组织所有者可以分配给组织中任何团队的角色。 应用时，它允许团队的每个成员权限**管理您组织中的安全警报和设置，并为组织中所有存储库**阅读权限。
  * If your organization has a security team, you can use the security manager role to give members of the team the least access they need to the organization.

*如果您的组织有一个安全团队，您可以使用安全管理器角色为团队成员提供他们对组织的最少访问权限。
* **Github App managers**: To allow additional users to **manage GitHub Apps owned by an organization**, an owner can grant them GitHub App manager permissions.

*** github应用程序经理**：要允许其他用户**管理组织拥有的github应用程序**，所有者可以授予他们github应用程序管理器权限。
* **Outside collaborators**: An outside collaborator is a person who has **access to one or more organization repositories but is not explicitly a member** of the organization.

***外部合作者**：外部合作者是一个拥有一个或多个组织存储库但并非明确的组织**的人。

You can **compare the permissions** of these roles in this table: [https://docs.github.com/en/organizations/managing-peoples-access-to-your-organization-with-roles/roles-in-an-organization#permissions-for-organization-roles](https://docs.github.com/en/organizations/managing-peoples-access-to-your-organization-with-roles/roles-in-an-organization#permissions-for-organization-roles)

您可以**比较此表中这些角色的权限** -An-Organization＃permissions-for-Organization-roles]（https://docs.github.com/en/organizations/managing-peoples-peoples-access-access-to-your-organization-with-with-with-roles/Roles/Roles/Roles-in-roles-in-roles-in-an-an--- 组织＃用于组织的权限）

## Members Privileges

##会员特权

In _https://github.com/organizations/\<org\_name>/settings/member\_privileges_ you can see the **permissions users will have just for being part of the organisation**.

在_https：//github.com/organizations/ \ <org \ _name>/settings/member \ _privileges _您可以看到**权限用户只能成为组织的一部分**。

The settings here configured will indicate the following permissions of members of the organisation:

此处配置的设置将指示组织成员的以下权限：

* Be admin, writer, reader or no permission over all the organisation repos.

*成为所有组织存储库的管理员，作家，读者或无许可。
* If members can create private, internal or public repositories.

*如果会员可以创建私人，内部或公共存储库。
* If forking of repositories is possible

*如果可能的存储库有可能
* If it's possible to invite outside collaborators

*如果可以邀请外部合作者
* If public or private sites can be published

*如果可以发布公共或私人网站
* The permissions admins has over the repositories

*权限管理员对存储库有
* If members can create new teams

*如果成员可以创建新团队

## Repository Roles

##存储库角色

By default repository roles are created:

默认情况下，创建了存储库角色：

* **Read**: Recommended for **non-code contributors** who want to view or discuss your project

***读**：建议**想要查看或讨论您的项目的非代码贡献者**
* **Triage**: Recommended for **contributors who need to proactively manage issues and pull requests** without write access

***分类**：建议为需要主动管理问题并提取请求的贡献者**而无需写访问
* **Write**: Recommended for contributors who **actively push to your project**

***写**：建议为主动推进您项目的贡献者**
* **Maintain**: Recommended for **project managers who need to manage the repository** without access to sensitive or destructive actions

***维护**：建议**需要管理存储库**的项目经理，而无需访问敏感或破坏性的动作
* **Admin**: Recommended for people who need **full access to the project**, including sensitive and destructive actions like managing security or deleting a repository

***管理员**：建议需要**完全访问该项目的人**，包括敏感和破坏性的动作，例如管理安全性或删除存储库

You can **compare the permissions** of each role in this table [https://docs.github.com/en/organizations/managing-access-to-your-organizations-repositories/repository-roles-for-an-organization#permissions-for-each-role](https://docs.github.com/en/organizations/managing-access-to-your-organizations-repositories/repository-roles-for-an-organization#permissions-for-each-role)

您可以**比较此表中每个角色的权限** 组织＃permissions-for-each-role]（https://docs.github.com/en/organizations/managing-access-to-your-organization-repositories/repository-for-roles-for-an-organization#permissions-formissions-for  - 仪式）

You can also **create your own roles** in _https://github.com/organizations/\<org\_name>/settings/roles_

您也可以**在_https：//github.com/organizations/ \ <org \ _name>/settings/setings/roles_中**创建自己的角色**

## Teams

##团队

You can **list the teams created in an organization** in _https://github.com/orgs/\<org\_name>/teams_. Note that to see the teams which are children of other teams you need to access each parent team.

您可以**列出组织中创建的团队**在_https：//github.com/orgs/ \ <org \ _name>/teams_中。 请注意，要看到团队是其他团队的孩子，您需要访问每个家长团队。

![](<../../.gitbook/assets/image (630) (1).png>)

## Users

##用户

The users of an organization can be **listed** in _https://github.com/orgs/\<org\_name>/people._

可以在_https：//github.com/orgs/ \ <org \ _name>/people._中列出组织的用户。

In the information of each user you can see the **teams the user is member of**, and the **repos the user has access to**.

在每个用户的信息中，您可以看到**团队用户是**的成员，并且**存储库用户可以访问**。

# Github Authentication

＃github身份验证

Github offers different ways to authenticate to your account and perform actions on your behalf.

Github提供了不同的方式来验证您的帐户并代表您执行操作。

## Web Access

## Web访问

Accessing **github.com** you can login using your **username and password** (and a **2FA potentially**).

访问** github.com **您可以使用您的**用户名和密码**登录（以及A ** 2fa可能**）。

## **SSH Keys**

You can configure your account with one or several public keys allowing the related **private key to perform actions on your behalf.** [https://github.com/settings/keys](https://github.com/settings/keys)

您可以使用一个或几个公共键配置您的帐户，允许相关的**私钥代表您执行操作。** [https://github.com/settings/keys/keys] /键）

### **GPG Keys**

You **cannot impersonate the user with these keys** but if you don't use it it might be possible that you **get discover for sending commits without a signature**. Learn more about [vigilant mode here](https://docs.github.com/en/authentication/managing-commit-signature-verification/displaying-verification-statuses-for-all-of-your-commits#about-vigilant-mode).

您**无法使用这些键模拟用户**，但是如果您不使用它，则可能有可能您**发现在没有签名的情况下发送提交**。 了解有关[在此处的警惕模式]的更多信息（https://docs.github.com/en/authentication/managing-commit-signature-verification/displaying-verification-statuses-statuses-for-all-all-al-for-all-of-your-commits#about-vigilant- -模式）。

## **Personal Access Tokens**

## **个人访问令牌**

You can generate personal access token to **give an application access to your account**. When creating a personal access token the **user** needs to **specify** the **permissions** to **token** will have. [https://github.com/settings/tokens](https://github.com/settings/tokens)

您可以生成个人访问令牌，以**为您的帐户提供访问权限。 当创建个人访问令牌时，**用户**需要**指定**权限** **将** ** ** **。 [https://github.com/settings/tokens]（https://github.com/settings/tokens）

## Oauth Applications

## Oauth应用程序

Oauth applications may ask you for permissions **to access part of your github information or to impersonate you** to perform some actions. A common example of this functionality is the **login with github button** you might find in some platforms.

OAuth应用程序可能会要求您提供权限**访问您的一部分GitHub信息或假冒您**以执行一些操作。 此功能的一个常见示例是您可能会在某些平台中找到的**登录。

* You can **create** your own **Oauth applications** in [https://github.com/settings/developers](https://github.com/settings/developers)

*您可以**创建**您自己的** OAuth应用程序**在[https://github.com/settings/developers]（
* You can see all the **Oauth applications that has access to your account** in [https://github.com/settings/applications](https://github.com/settings/applications)

*您可以在[https://github.com/settings/applications]（https://github.com/settings/applications中查看所有可以访问您的帐户**的** oauth应用程序）
* You can see the **scopes that Oauth Apps can ask for** in [https://docs.github.com/en/developers/apps/building-oauth-apps/scopes-for-oauth-apps](https://docs.github.com/en/developers/apps/building-oauth-apps/scopes-for-oauth-apps)

*您可以在[https://docs.github.com/en/developers/apps/building-oauth-apps/scopes-for-oauth-apps购买** oauth应用程序可以要求**的**范围** ：//docs.github.com/en/developers/apps/building-oauth-apps/scopes-for-oauth-apps）
* You can see third party access of applications in an **organization** in _https://github.com/organizations/\<org\_name>/settings/oauth\_application\_policy_

*您可以在_https：//github.com/organizations/ \ <org \ _name>/settings/oauth \ _application \ _policy__policy__policy__policy__policy__ _policy_

Some **security recommendations**:

一些**安全建议**：

* An **OAuth App** should always **act as the authenticated GitHub user across all of GitHub** (for example, when providing user notifications) and with access only to the specified scopes..

*一个** oauth app **应始终**充当所有github **的身份验证的github用户（例如，在提供用户通知时），并且仅访问指定的范围。
* An OAuth App can be used as an identity provider by enabling a "Login with GitHub" for the authenticated user.

*通过为身份验证的用户启用“使用GitHub登录”，可以将OAuth应用程序用作身份提供商。
* **Don't** build an **OAuth App** if you want your application to act on a **single repository**. With the `repo` OAuth scope, OAuth Apps can **act on \_all**\_\*\* of the authenticated user's repositorie\*\*s.

***不要**构建** oauth应用程序**如果您希望您的应用程序在**单个存储库上行动**。 使用“ repo” Oauth范围，Oauth应用程序可以**在身份验证的用户的repositorie \*\*s的\ _all ** \ _ \*\*上行动。
* **Don't** build an OAuth App to act as an application for your **team or company**. OAuth Apps authenticate as a **single user**, so if one person creates an OAuth App for a company to use, and then they leave the company, no one else will have access to it.

***不要**构建一个OAuth应用程序，以充当您的**团队或公司的应用程序**。 OAuth应用程序可以用作单个用户**，因此，如果一个人创建了一个供公司使用的OAuth应用程序，然后他们离开公司，则没有其他人可以访问它。
* **More** in [here](https://docs.github.com/en/developers/apps/getting-started-with-apps/about-apps#about-oauth-apps).

***更多**在[此处]（https://docs.github.com/en/developers/apps/getting-started-with-with-apps/about-apps#about-oauth-apps）。

## Github Applications

## github应用程序

Github applications can ask for permissions to **access your github information or impersonate you** to perform specific actions over specific resources. In Github Apps you need to specify the repositories the app will have access to.

GitHub应用程序可以要求**访问您的github信息或假冒您**的权限，以通过特定资源执行特定的操作。 在GitHub应用程序中，您需要指定该应用程序可以访问的存储库。

* To install a GitHub App, you must be an **organisation owner or have admin permissions** in a repository.

*要安装GitHub应用程序，您必须是**组织所有者或在存储库中拥有管理权限**。
* The GitHub App should **connect to a personal account or an organisation**.

*GitHub应用程序应该**连接到个人帐户或组织**。
* You can create your own Github application in [https://github.com/settings/apps](https://github.com/settings/apps)

*您可以在[https://github.com/settings/apps]（https://github.com/settings/apps中创建自己的github应用程序
* You can see all the **Github applications that has access to your account** in [https://github.com/settings/apps/authorizations](https://github.com/settings/apps/authorizations)

*您可以在[https://github.com/settings/apps/authorizations]（https://github.com/settings/apps/authorizations中查看所有可以访问您的帐户**的** github应用程序。
* These are the **API Endpoints for Github Applications** [https://docs.github.com/en/rest/overview/endpoints-available-for-github-app](https://docs.github.com/en/rest/overview/endpoints-available-for-github-apps). Depending on the permissions of the App it will be able to access some of them

*这些是GitHub应用程序的** API端点** [https://docs.github.com/en/rest/rest/overview/endpoints-available-for-github-app-https://docs.github.com /en/rest/概述/端点 - 可用for-github-apps）。 根据应用程序的权限，它将能够访问其中一些
* You can see installed apps in an **organization** in _https://github.com/organizations/\<org\_name>/settings/installations_

*您可以在_https：//github.com/organizations/ \ <org \ _name>/settings/interlations_中看到**组织**中的已安装应用程序**

Some security recommendations:

一些安全建议：

* A GitHub App should **take actions independent of a user** (unless the app is using a [user-to-server](https://docs.github.com/en/apps/building-github-apps/identifying-and-authorizing-users-for-github-apps#user-to-server-requests) token). To keep user-to-server access tokens more secure, you can use access tokens that will expire after 8 hours, and a refresh token that can be exchanged for a new access token. For more information, see "[Refreshing user-to-server access tokens](https://docs.github.com/en/apps/building-github-apps/refreshing-user-to-server-access-tokens)."

*GitHub应用程序应**采取独立于用户**的操作（除非应用程序使用[user-to-server]（https://docs.github.com/en/apps/building-github-apps/ 识别和授权 - 用户for-github-apps＃用户对服务器重试）令牌）。 为了使用户到服务器的访问令牌更加安全，您可以使用将在8个小时后到期的访问令牌，以及可以将其用于新访问令牌的刷新令牌。 有关更多信息，请参见“ [刷新用户对服务器访问令牌]（https://docs.github.com/en/apps/building-github-apps/refreshing-user-to-serer-to-server-access-cess-tokens）。 “
* Make sure the GitHub App integrates with **specific repositories**.

*确保GitHub应用程序与**特定的存储库集成**。
* The GitHub App should **connect to a personal account or an organisation**.

*GitHub应用程序应该**连接到个人帐户或组织**。
* Don't expect the GitHub App to know and do everything a user can.

*不要指望GitHub应用程序知道并尽一切努力。
* **Don't use a GitHub App if you just need a "Login with GitHub" service**. But a GitHub App can use a [user identification flow](https://docs.github.com/en/apps/building-github-apps/identifying-and-authorizing-users-for-github-apps) to log users in _and_ do other things.

***如果您只需要“使用github”服务登录**，请勿使用GitHub应用程序**。 但是GitHub应用程序可以使用[用户识别流]（https://docs.github.com/en/apps/building-github-apps/indiseifying-andifying-andifying-andifying-andorizing-users-for-github-apps） 在_和_做其他事情。
* Don't build a GitHub App if you _only_ want to act as a GitHub user and do everything that user can do.

*如果您想充当github用户并执行用户可以做的一切，请不要构建GitHub应用程序。
* If you are using your app with GitHub Actions and want to modify workflow files, you must authenticate on behalf of the user with an OAuth token that includes the `workflow` scope. The user must have admin or write permission to the repository that contains the workflow file. For more information, see "[Understanding scopes for OAuth apps](https://docs.github.com/en/apps/building-oauth-apps/understanding-scopes-for-oauth-apps/#available-scopes)."

*如果您将应用程序与github操作一起使用并想修改工作流文件，则必须用包含`workflow范围的OAuth令牌代表用户对用户进行身份验证。 用户必须对包含WorkFlow文件的存储库有管理权或写入权限。 有关更多信息，请参见“ [了解OAuth应用程序的范围]（https://docs.github.com/en/apps/building-oauth-apps/understanding-scopes-for-oauth-apps/#available-scopes）。 “
* **More** in [here](https://docs.github.com/en/developers/apps/getting-started-with-apps/about-apps#about-github-apps).

***更多**在[此处]（https://docs.github.com/en/developers/apps/getting-started-with-with-apps/about-apps#about-github-apps）。

## Deploy keys

Deploy keys might have read-only or write access to the repo, so they might be interesting to compromise specific repos.

部署键可能只读或编写对存储库的访问权限，因此折衷特定的存储库可能很有趣。

## Github Actions

## github动作

This **isn't a way to authenticate in github**, but a **malicious** Github Action could get **unauthorised access to github** and **depending** on the **privileges** given to the Action several **different attacks** could be done. See below for more information.

这个**不是在github **中进行身份验证的一种方法，但是a **恶意** github动作可以**未经授权访问github ** **和** **，具体取决于**的**特权** 动作几个**可以进行不同的攻击**。 请参阅下面的详细信息。

# Git Actions

＃git动作

Git actions allows to automate the **execution of code when an event happen**. Usually the code executed is **somehow related to the code of the repository** (maybe build a docker container or check that the PR doesn't contain secrets).

GIT操作允许在事件发生**时自动执行代码。 通常，执行的代码与存储库的代码**相关（也许可以构建Docker容器，或检查PR是否包含秘密）。

## Configuration

In _https://github.com/organizations/\<org\_name>/settings/actions_ it's possible to check the **configuration of the github actions** for the organization.

在_https：//github.com/organizations/ \ <org \ _name>/settings/Actions_中，可以检查组织的** github操作**的配置**。

It's possible to disallow the use of github actions completely, **allow all github actions**, or just allow certain actions.

可以完全禁止使用GitHub动作的使用，**允许所有GitHub动作**，或者只允许某些操作。

It's also possible to configure **who needs approval to run a Github Action** and the **permissions of the \_GITHUB\_TOKEN**\_\*\* of a Github Action when it's run\*\*.

还可以配置需要批准的**来运行github操作**和\ _github \ _token ** \ _ \ _ \*\*的**权限，当时它是运行\*\*的。

## Git Secrets

Github Action usually need some kind of secrets to interact with github or third party applications. To **avoid putting them in clear-text** in the repo, github allow to put them as **Secrets**.

GitHub Action通常需要某种秘密来与GitHub或第三方应用程序进行互动。 **避免将它们放入回购中的清晰文本**中，github允许将它们作为**秘密**。

These secrets can be configured **for the repo or for all the organization**. Then, in order for the **Action to be able to access the secret** you need to declare it like:

这些秘密可以为回购或所有组织配置**。 然后，为了使**行动能够访问秘密**，您需要声明它：

```yaml
steps:
  - name: Hello world action
    with: # Set the secret as an input
      super_secret: ${{ secrets.SuperSecret }}
    env: # Or as an environment variable
      super_secret: ${{ secrets.SuperSecret }}
```

### Example using Bash <a href="#example-using-bash" id="example-using-bash"></a>

###示例使用bash <a href="#example-usish-bash" id="example-using-using-bash"> </a>

```yaml
steps:
  - shell: bash
    env:
      SUPER_SECRET: ${{ secrets.SuperSecret }}
    run: |
      example-command "$SUPER_SECRET"
```

{% hint style="warning" %}

{％提示样式=“警告”％}
Secrets **can only be accessed from the Github Actions** that have them declared.

秘密**只能从宣布它们的github动作**访问。

Once configured in the repo or the organizations **users of github won't be able to access them again**, they just will be able to **change them**.

一旦在存储库中配置或github的组织**无法再次访问它们**，他们将能够**更改它们**。
{% endhint %}

Therefore, the **only way to steal github secrets is to be able to access the machine that is executing the Github Action** (in that scenario you will be able to access only the secrets declared for the Action).

因此，**窃取GitHub Secrets的唯一方法是能够访问执行GitHub Action **的机器（在这种情况下，您将只能访问该操作的秘密）。

## Git Environments

Github allows to create **environments** where you can save **secrets**. Then, you can give the github action access to the secrets inside the environment with something like:

GitHub允许创建**环境**您可以保存**秘密**。 然后，您可以将GitHub动作访问环境内部的秘密，例如：

```yaml
jobs:
  deployment:
    runs-on: ubuntu-latest
    environment: env_name
```

You can configure an environment to be **accessed** by **all branches** (default), **only protected** branches or **specify** which branches can access it.

您可以通过**所有分支**（默认）配置一个被**访问的环境**，**仅保护**分支或**指定哪些分支可以访问它。

## Git Action Box

## git动作盒

A Github Action can be **executed inside the github environment** or can be executed in a **third party infrastructure** configured by the user.

可以在github环境中**执行github操作，也可以在用户配置的**第三方基础结构**中执行。

Several organizations will allow to run Github Actions in a **third party infrastructure** as it use to be **cheaper**.

几个组织将允许在**第三方基础架构**中运行github动作，因为它用来**便宜**。

You can **list the self-hosted runners** of an organization in _https://github.com/organizations/\<org\_name>/settings/actions/runners_

您可以**列出组织中的自托运动员**在_https：//github.com/organizations/ \ <org \ _name>/settings/settings/actions/runners_中

The way to find which **Github Actions are being executed in non-github infrastructure** is to search for `runs-on: self-hosted` in the Github Action configuration yaml.

在非GITHUB基础结构中找到哪种** github动作**是在github Action配置yaml中搜索`runs-ons-ons-ons-ons-ons-ons-onsed'。

It's **not possible to run a Github Action of an organization inside a self hosted box** of a different organization because **a unique token is generated for the Runner** when configuring it to know where the runner belongs.

**不可能在另一个组织的自托管框**内运行组织的github动作，因为**在配置它时，为跑步者生成了唯一的令牌，以了解跑步者的属性。

If the custom **Github Runner is configured in a machine inside AWS or GCP** for example, the Action **could have access to the metadata endpoint** and **steal the token of the service account** the machine is running with.

例如，如果在AWS或GCP **内配置了自定义** GitHub Runner，则操作**可以访问元数据端点**，并且**窃取服务帐户的令牌**机器正在运行机器正在运行 和。

## Git Action Compromise

## git行动妥协

If all actions (or a malicious action) are allowed a user could use a **Github action** that is **malicious** and will **compromise** the **container** where it's being executed.

如果允许所有操作（或恶意动作）用户可以使用**恶意**的** github操作**，并且将**妥协** ** **容器**被执行。

{% hint style="danger" %}
A **malicious Github Action** run could be **abused** by the attacker to:

攻击者可能会滥用**恶意的github行动**行动。

* **Steal all the secrets** the Action has access to

***窃取所有秘密**动作可以访问
* **Move laterally** if the Action is executed inside a **third party infrastructure** where the SA token used to run the machine can be accessed (probably via the metadata service)

***横向移动**如果在一个**第三方基础架构中执行操作**可以访问用于运行机器的SA令牌（可能是通过元数据服务）
* **Abuse the token** used by the **workflow** to **steal the code of the repo** where the Action is executed or **even modify it**.

***滥用令牌** ** workflow **用于**窃取执行操作或**修改**的repo **的代码**。
{% endhint %}

# Branch Protections

＃分支保护

Branch protections are designed to **not give complete control of a repository** to the users. The goal is to **put several protection methods before being able to write code inside some branch**.

分支保护措施旨在**不完全控制存储库**。 目的是**在能够在某些分支中编写代码之前，请使用几种保护方法。

The **branch protections of a repository** can be found in _https://github.com/\<orgname>/\<reponame>/settings/branches_

可以在_https：//github.com/ \ <Orgname>/\ <redoname>/settings/branches_中找到**存储库**的分支保护**

{% hint style="info" %}

{％提示样式=“ info”％}
It's **not possible to set a branch protection at organization level**. So all of them must be declared on each repo.

**不可能在组织级别设置分支保护**。 因此，必须在每个存储库上声明所有这些。
{% endhint %}

Different protections can be applied to a branch (like to master):

可以将不同的保护措施应用于分支（例如主人）：

* You can **require a PR before merging** (so you cannot directly merge code over the branch). If this is select different other protections can be in place:

*您可以**在合并之前需要PR **（因此您不能直接通过分支合并代码）。 如果选择了不同的其他保护措施，则可以使用：
  * **Require a number of approvals**. It's very common to require 1 or 2 more people to approve your PR so a single user isn't capable of merge code directly.

***需要许多批准**。 通常需要1或2个人批准您的PR，因此单个用户无法直接合并代码。
  * **Dismiss approvals when new commits are pushed**. If not, a user may approve legit code and then the user could add malicious code and merge it.

***当推动新提交时，请撤销批准**。 如果没有，用户可以批准合法代码，然后用户可以添加恶意代码并将其合并。
  * **Require reviews from Code Owners**. At least 1 code owner of the repo needs to approve the PR (so "random" users cannot approve it)

***需要代码所有者的评论**。 回购的至少1个代码所有者需要批准PR（因此“随机”用户不能批准它）
  * **Restrict who can dismiss pull request reviews.** You can specify people or teams allowed to dismiss pull request reviews.

***限制谁可以驳回拉扯请求审查。
  * **Allow specified actors to bypass pull request requirements**. These users will be able to bypass previous restrictions.

***允许指定的参与者绕过拉请求要求**。 这些用户将能够绕过以前的限制。
* **Require status checks to pass before merging.** Some checks needs to pass before being able to merge the commit (like a github action checking there isn't any cleartext secret).

***需要在合并之前通过状态检查。
* **Require conversation resolution before merging**. All comments on the code needs to be resolved before the PR can be merged.

***在合并之前需要解决对话**。 在合并PR之前，需要解决有关代码的所有评论。
* **Require signed commits**. The commits need to be signed.

***要求签名的提交**。 委托需要签名。
* **Require linear history.** Prevent merge commits from being pushed to matching branches.

***需要线性历史记录。**防止合并被推到匹配的分支。
* **Include administrators**. If this isn't set, admins can bypass the restrictions.

***包括管理员**。 如果没有设定，管理员可以绕过限制。
* **Restrict who can push to matching branches**. Restrict who can send a PR.

***限制谁可以推到匹配的分支**。 限制谁可以发送公关。

{% hint style="info" %}

{％提示样式=“ info”％}
As you can see, even if you managed to obtain some credentials of a user, **repos might be protected avoiding you to pushing code to master** for example to compromise the CI/CD pipeline.

如您所见，即使您设法获得了用户的一些凭据，** repos可能会受到保护，避免您将代码推向主**，例如损害CI/CD管道。
{% endhint %}

# References

* [https://docs.github.com/en/organizations/managing-access-to-your-organizations-repositories/repository-roles-for-an-organization](https://docs.github.com/en/organizations/managing-access-to-your-organizations-repositories/repository-roles-for-an-organization)
* [https://docs.github.com/en/enterprise-server@3.3/admin/user-management/managing-users-in-your-enterprise/roles-in-an-enterprise](https://docs.github.com/en/enterprise-server@3.3/admin/user-management/managing-users-in-your-enterprise/roles-in-an-enterprise)[https://docs.github.com/en/enterprise-server](https://docs.github.com/en/enterprise-server@3.3/admin/user-management/managing-users-in-your-enterprise/roles-in-an-enterprise)
* [https://docs.github.com/en/get-started/learning-about-github/access-permissions-on-github](https://docs.github.com/en/get-started/learning-about-github/access-permissions-on-github)
* [https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-github-user-account/managing-user-account-settings/permission-levels-for-user-owned-project-boards](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-github-user-account/managing-user-account-settings/permission-levels-for-user-owned-project-boards)
* [https://docs.github.com/en/actions/security-guides/encrypted-secrets](https://docs.github.com/en/actions/security-guides/encrypted-secrets)


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


