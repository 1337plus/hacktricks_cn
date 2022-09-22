# Concourse Architecture

## Concourse Architecture

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

## Architecture

＃＃ 建筑学

![](<../../.gitbook/assets/image (307) (3) (1).png>)

### ATC: web UI & build scheduler

The ATC is the heart of Concourse. It runs the **web UI and API** and is responsible for all pipeline **scheduling**. It **connects to PostgreSQL**, which it uses to store pipeline data (including build logs).

ATC是大厅的核心。 它运行** Web UI和API **，并负责所有管道**调度**。 它**连接到PostgreSQL **，它用于存储管道数据（包括构建日志）。

The [checker](https://concourse-ci.org/checker.html)'s responsibility is to continously checks for new versions of resources. The [scheduler](https://concourse-ci.org/scheduler.html) is responsible for scheduling builds for a job and the [build tracker](https://concourse-ci.org/build-tracker.html) is responsible for running any scheduled builds. The [garbage collector](https://concourse-ci.org/garbage-collector.html) is the cleanup mechanism for removing any unused or outdated objects, such as containers and volumes.

[Checker]（https://concourse-ci.org/checker.html）的责任是不断检查新版本的资源。 [调度程序]（https://concourse-ci.org/scheduler.html）负责为作业安排构建和[build tracker]（https：//concourse-ci.org/build-tracker.html） 负责运行任何计划的构建。 [垃圾收集器]（https://concourse-ci.org/garbage-collector.html）是清理机制，用于删除任何未使用或过时的对象，例如容器和卷。

### TSA: worker registration & forwarding

### TSA：工人注册和转发

The TSA is a **custom-built SSH server** that is used solely for securely **registering** [**workers**](https://concourse-ci.org/internals.html#architecture-worker) with the [ATC](https://concourse-ci.org/internals.html#component-atc).

TSA是**自定义的SSH服务器**，仅用于安全**注册** [**工人**]（https://concourse-ci.org/internals.html#architecture-worker） 使用[atc]（https://concourse-ci.org/internals.html#component-atc）。

The TSA by **default listens on port `2222`**, and is usually colocated with the [ATC](https://concourse-ci.org/internals.html#component-atc) and sitting behind a load balancer.

**的TSA默认值在port`2222` **上听，通常与[atc]（https://concourse-ci.org/internals.html#component-ATC）一起坐在负载平衡器后面。

The **TSA implements CLI over the SSH connection,** supporting [**these commands**](https://concourse-ci.org/internals.html#component-tsa).

** TSA通过SSH连接实现CLI，**支持[**这些命令**]（https://concourse-ci.org/internals.html#component-tsa）。

### Workers

In order to execute tasks concourse must have some workers. These workers **register themselves** via the [TSA](https://concourse-ci.org/internals.html#component-tsa) and run the services [**Garden**](https://github.com/cloudfoundry-incubator/garden) and [**Baggageclaim**](https://github.com/concourse/baggageclaim).

为了执行任务，大厅必须有一些工人。 这些工人**自己注册**通过[tsa]（https://concourse-ci.org/internals.html#component-tsa）并运行服务[** garden **]（https：// github。 com/cloudfoundry-incuubator/garden）和[** baggageclaim **]（https://github.com/concourse/baggageclaim）。

* **Garden**: This is the **Container Manage AP**I, usually run in **port 7777** via **HTTP**.

***花园**：这是**容器管理ap ** i，通常在**端口7777 **通过** http **运行。
* **Baggageclaim**: This is the **Volume Management API**, usually run in **port 7788** via **HTTP**.

*** baggageclaim **：这是**卷管理API **，通常在**端口7788 **通过** http **。

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
