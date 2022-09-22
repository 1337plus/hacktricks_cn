

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


# Stackdriver logging

[Stackdriver](https://cloud.google.com/stackdriver/) is Google's general-purpose infrastructure logging suite which might be capturing sensitive information like syslog-like capabilities that report individual commands run inside Compute Instances, HTTP requests sent to load balancers or App Engine applications, network packet metadata for VPC communications, and more.

[StackDriver]（https://cloud.google.com/stackdriver/）是Google的通用 - 馆基础架构日志记录套件，它可能会捕获敏感信息，例如syslog类似于syslog的功能，例如报告单个命令在计算实例中运行的单个命令，http recesptions，http recesptions http recespts http recess of load load load load sending load load ofer 平衡器或应用引擎应用程序，用于VPC通信的网络数据包元数据等等。

The service account for a Compute Instance **only needs WRIT**E access to enable logging on instance actions, **but** an administrator may **mistakenly** **grant** the service account both **READ** and WRITE access. If this is the case, you can explore logs for sensitive data.

Compute实例的服务帐户**只需要命令** e访问实例操作的启用记录，**但是，管理员可能会**错误地** ** **授予**服务帐户两者都**读** ** 并写入访问。 如果是这种情况，您可以探索敏感数据的日志。

[gcloud logging](https://cloud.google.com/sdk/gcloud/reference/logging/) provides tools to get this done. First, you'll want to see what types of logs are available in your current project.

[gcloud Loggging]（https://cloud.google.com/sdk/gcloud/reference/logging/）提供了完成此操作的工具。 首先，您需要查看当前项目中有哪些类型的日志。

```bash
# List logs
gcloud logging logs list
NAME
projects/REDACTED/logs/OSConfigAgent
projects/REDACTED/logs/cloudaudit.googleapis.com%2Factivity
projects/REDACTED/logs/cloudaudit.googleapis.com%2Fsystem_event
projects/REDACTED/logs/bash.history
projects/REDACTED/logs/compute.googleapis.com
projects/REDACTED/logs/compute.googleapis.com%2Factivity_log

# Read logs
gcloud logging read [FOLDER]

# Write logs
# An attacker writing logs may confuse the Blue Team
gcloud logging write [FOLDER] [MESSAGE]
```

# AI platform configurations <a href="reviewing-ai-platform-configurations" id="reviewing-ai-platform-configurations"></a>

＃AI平台配置<a href="reviewing-ai-platform-configurations" id="reviewing-ai-platform-configurations"> </a>

Google [AI Platform](https://cloud.google.com/ai-platform/) is another "serverless" offering for machine learning projects.

Google [AI平台]（https://cloud.google.com/ai-platform/）是机器学习项目的另一种“无服务器”产品。

There are a few areas here you can look for interesting information - models and jobs. Try the following commands.

您可以在这里寻找一些有趣的信息 - 模型和作业。 尝试以下命令。

```
$ gcloud ai-platform models list --format=json
$ gcloud ai-platform jobs list --format=json
```

# Cloud pub/sub <a href="reviewing-cloud-pubsub" id="reviewing-cloud-pubsub"></a>

＃Cloud Pub/sub <a href="reviewing-cloud-pubsub" id="reviewing-cloud-pubsub"> </a>

Google [Cloud Pub/Sub](https://cloud.google.com/pubsub/) is a service that allows independent applications to **send messages** back and forth. Basically, there are **topics** where applications may **subscribe** to send and receive **messages** (which are composed by the message content and some metadata).

Google [Cloud Pub/sub]（https://cloud.google.com/pubsub/）是一项允许独立应用程序**发送消息**的服务。 基本上，有**主题**应用程序可以**订阅**发送和接收**消息**（由消息内容和一些元数据组成）。

```bash
# Get a list of topics in the project
gcloud pubsub topics list

# Get a list of subscriptions across all topics
gcloud pubsub subscriptions list --format=json

# This will retrive a non ACKed message (and won't ACK it)
gcloud pubsub subscriptions pull [SUBSCRIPTION NAME]
```

However, you may have better results [asking for a larger set of data](https://cloud.google.com/pubsub/docs/replay-overview), including older messages. This has some prerequisites and could impact applications, so make sure you really know what you're doing.

但是，您可能会获得更好的结果[询问较大的数据]（https://cloud.google.com/pubsub/docs/replay-overview），包括较旧的消息。 这有一些先决条件并可能影响应用程序，因此请确保您真的知道自己在做什么。

# Cloud Git repositories <a href="reviewing-cloud-git-repositories" id="reviewing-cloud-git-repositories"></a>

＃云git存储库<a href="reviewing-cloud-git-repositories“id="reviewing-cloud-git-repositories"> </a>

Google's [Cloud Source Repositories](https://cloud.google.com/source-repositories/) are Git designed to be private storage for source code. You might **find useful secrets here**, or use the **source to discover vulnerabilities** in other applications.

Google的[Cloud Source存储库]（https://cloud.google.com/source-repositories/）是git设计的，是用于源代码的私人存储。 您可能**在这里找到有用的秘密，或使用**源在其他应用程序中发现漏洞**。

You can explore the available repositories with the following commands:

您可以使用以下命令探索可用的存储库：

```bash
# enumerate what's available
gcloud source repos list

# clone a repo locally
gcloud source repos clone [REPO NAME]
```

# Cloud Filestore Instances

Google [Cloud Filestore](https://cloud.google.com/filestore/) is NAS for Compute Instances and Kubernetes Engine instances. You can think of this like any other **shared document repository -** a potential source of sensitive info.

Google [Cloud Filestore]（https://cloud.google.com/filestore/）是NAS用于计算实例和kubernetes引擎实例。 您可以像任何其他**共享文档存储库一样想到这一点 -  **潜在的敏感信息来源。

If you find a filestore available in the project, you can **mount it** from within your compromised Compute Instance. Use the following command to see if any exist.

如果您在项目中找到可用的文件，则可以从折衷的计算实例中**安装**。 使用以下命令查看是否存在。

```
gcloud filestore instances list --format=json
```

# Containers

```bash
gcloud container images list
gcloud container subnets list
gcloud container clusters list
gcloud container clusters get-credentials [NAME]

# Run a container locally
docker run --rm -ti gcr.io/<project-name>/secret:v1 sh
```

# Kubernetes

First, you can check to see if any Kubernetes clusters exist in your project.

首先，您可以检查项目中是否存在任何Kubernetes群集。

```
gcloud container clusters list
```

If you do have a cluster, you can have `gcloud` automatically configure your `~/.kube/config` file. This file is used to authenticate you when you use [kubectl](https://kubernetes.io/docs/reference/kubectl/overview/), the native CLI for interacting with K8s clusters. Try this command.

如果您确实有群集，则可以让`gcloud'自动配置`〜/.kube/config`文件。 当您使用[kubectl]（https://kubernetes.io/docs/reference/reference/kubectl/overview/）（用于与K8S群集交互）时，此文件用于对您进行身份验证。 尝试此命令。

```
gcloud container clusters get-credentials [CLUSTER NAME] --region [REGION]
```

Then, take a look at the `~/.kube/config` file to see the generated credentials. This file will be used to automatically refresh access tokens based on the same identity that your active `gcloud` session is using. This of course requires the correct permissions in place.

然后，查看`〜/.kube/config`文件以查看生成的凭据。 该文件将根据您的活动“ GCLOUD”会话所使用的相同身份自动刷新访问令牌。 当然，这需要正确的权限。

Once this is set up, you can try the following command to get the cluster configuration.

设置此设置后，您可以尝试以下命令获取群集配置。

```
kubectl cluster-info
```

You can read more about `gcloud` for containers [here](https://cloud.google.com/sdk/gcloud/reference/container/).

您可以在容器[此处]（https://cloud.google.com/sdk/gcloud/reference/reference/container/）阅读有关“ GCLOUD”的更多信息。

This is a simple script to enumerate kubernetes in GCP: [https://gitlab.com/gitlab-com/gl-security/security-operations/gl-redteam/gcp\_k8s\_enum](https://gitlab.com/gitlab-com/gl-security/security-operations/gl-redteam/gcp\_k8s\_enum)

这是一个简单的脚本，可以在GCP中枚举kubernetes：[https://gitlab.com/gitlab-com/gl-security/security/security-operations/gl-redteam/gcp \ _k8s \ _enum] /gitlab-com/gl-security/security-operations/gl-redteam/gcp \ _k8s \ _enum）

# References

* [https://about.gitlab.com/blog/2020/02/12/plundering-gcp-escalating-privileges-in-google-cloud-platform/#reviewing-stackdriver-logging](https://about.gitlab.com/blog/2020/02/12/plundering-gcp-escalating-privileges-in-google-cloud-platform/#reviewing-stackdriver-logging)


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


