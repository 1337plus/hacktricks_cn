

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


# Testing Environment

＃测试环境

## Running Concourse

##运行大厅

### With Docker-Compose

###与Docker-Compose

This docker-compose file simplifies the installation to do some tests with concourse:

此Docker-Compose文件简化了安装，以进行大厅进行一些测试：

```bash
wget https://raw.githubusercontent.com/starkandwayne/concourse-tutorial/master/docker-compose.yml
docker-compose up -d
```

You can download the command line `fly` for your OS from the web in `127.0.0.1:8080`

您可以从`127.0.0.1：8080`下载Web下载命令行`fly'

### With Kubernetes (Recommended)

###与kubernetes（推荐）

You can easily deploy concourse in **Kubernetes** (in **minikube** for example) using the helm-chart: [**concourse-chart**](https://github.com/concourse/concourse-chart).

您可以在** kubernetes **中轻松部署大厅（例如，在** minikube **）使用helm-chart：[** Concourse-chart **]（https://github.com/concourse/concourse-course-chart-chart ）。

```bash
brew install helm
helm repo add concourse https://concourse-charts.storage.googleapis.com/
helm install concourse-release concourse/concourse
# concourse-release will be the prefix name for the concourse elements in k8s
# After the installation you will find the indications to connect to it in the console

# If you need to delete it
helm delete concourse-release
```

After generating the concourse env, you could generate a secret and give a access to the SA running in concourse web to access K8s secrets:

生成Concourse Env后，您可以生成一个秘密，并访问Concourse Web中的SA访问K8S秘密：

```yaml
echo 'apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  name: read-secrets
rules:
- apiGroups: [""]
  resources: ["secrets"]
  verbs: ["get"]

---

apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: read-secrets-concourse
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: read-secrets
subjects:
- kind: ServiceAccount
  name: concourse-release-web
  namespace: default
  
---

apiVersion: v1
kind: Secret
metadata:
  name: super
  namespace: concourse-release-main
type: Opaque
data:
  secret: MWYyZDFlMmU2N2Rm

' | kubectl apply -f -
```

## Create Pipeline

A pipeline is made of a list of [Jobs](https://concourse-ci.org/jobs.html) which contains an ordered list of [Steps](https://concourse-ci.org/steps.html).

管道由[Jobs]（https://concourse-ci.org/jobs.html）的列表组成，其中包含[steps]（https://concourse-ci.org/steps.html）的有序列表 。

## Steps

＃＃ 脚步

Several different type of steps can be used:

可以使用几种不同类型的步骤：

* **the** [**`task` step**](https://concourse-ci.org/task-step.html) **runs a** [**task**](https://concourse-ci.org/tasks.html)

*** ** [**任务`step **] /concourse-ci.org/tasks.html）
* the [`get` step](https://concourse-ci.org/get-step.html) fetches a [resource](https://concourse-ci.org/resources.html)

* [`g get'step]（https://concourse-ci.org/get-step.html）获取[resource]（https://concourse-ci.org/resources.html）
* the [`put` step](https://concourse-ci.org/put-step.html) updates a [resource](https://concourse-ci.org/resources.html)

* [p put` step]（https://concourse-ci.org/put-step.html）更新[资源]（https://concourse-ci.org/resources.html）
* the [`set_pipeline` step](https://concourse-ci.org/set-pipeline-step.html) configures a [pipeline](https://concourse-ci.org/pipelines.html)
* the [`load_var` step](https://concourse-ci.org/load-var-step.html) loads a value into a [local var](https://concourse-ci.org/vars.html#local-vars)

* [`load_var`步骤]（https://concourse-ci.org/load-var-step.html）将值加载到[local var]（https://concourse-ci.org/vars.htmls.html） ＃本地视频）
* the [`in_parallel` step](https://concourse-ci.org/in-parallel-step.html) runs steps in parallel

* [``in_parallel`步骤]（https://concourse-ci.org/in-parallel-step.html）在并行运行步骤
* the [`do` step](https://concourse-ci.org/do-step.html) runs steps in sequence

* [``do` step]（https://concourse-ci.org/do-step.html）以顺序运行步骤
* the [`across` step modifier](https://concourse-ci.org/across-step.html#schema.across) runs a step multiple times; once for each combination of variable values

* [````over'spep oftifier''（https://concourse-ci.org/across-step.html#schema.across）多次运行一个步骤； 一次，每种可变值的组合
* the [`try` step](https://concourse-ci.org/try-step.html) attempts to run a step and succeeds even if the step fails

* [`try'step]（https://concourse-ci.org/try-step.html）尝试运行步骤并成功，即使步骤失败了

Each [step](https://concourse-ci.org/steps.html) in a [job plan](https://concourse-ci.org/jobs.html#schema.job.plan) runs in its **own container**. You can run anything you want inside the container _(i.e. run my tests, run this bash script, build this image, etc.)_. So if you have a job with five steps Concourse will create five containers, one for each step.

每个[step]（https://concourse-ci.org/steps.html）在[工作计划]（https://concourse-ci.org/jobs.html#schema.job.job.job.plan）中都在其 *中运行 *自己的容器**。 您可以在容器中运行任何想要的东西_（即运行我的测试，运行此bash脚本，构建此图像等）_。 因此，如果您有五个步骤大厅的工作，将创建五个容器，每个步骤一个。

Therefore, it's possible to indicate the type of container each step needs to be run in.

因此，可以指示每个步骤需要运行的容器类型。

## Simple Pipeline Example

```yaml
jobs:
- name: simple
  plan:
  - task: simple-task
    privileged: true
    config:
      # Tells Concourse which type of worker this task should run on
      platform: linux
      image_resource:
        type: registry-image
        source:
          repository: busybox # images are pulled from docker hub by default
      run:
        path: sh
        args:
        - -cx
        - |
          sleep 1000
          echo "$SUPER_SECRET"
      params:
        SUPER_SECRET: ((super.secret))
```

```bash
fly -t tutorial set-pipeline -p pipe-name -c hello-world.yml
# pipelines are paused when first created
fly -t tutorial unpause-pipeline -p pipe-name
# trigger the job and watch it run to completion
fly -t tutorial trigger-job --job pipe-name/simple --watch
# From another console
fly -t tutorial intercept --job pipe-name/simple
```

Check **127.0.0.1:8080** to see the pipeline flow.

检查** 127.0.0.1：8080 **查看管道流。

## Bash script with output/input pipeline

##带有输出/输入管道的BASH脚本

It's possible to **save the results of one task in a file** and indicate that it's an output and then indicate the input of the next task as the output of the previous task. What concourse does is to **mount the directory of the previous task in the new task where you can access the files created by the previous task**.

可以**将一个任务的结果保存在文件**中，并指示它是输出，然后指示下一个任务的输入作为上一个任务的输出。 Concourse的作用是**将上一个任务的目录安装在新任务中，您可以访问上一个任务**创建的文件。

## Triggers

You don't need to trigger the jobs manually every-time you need to run them, you can also program  them to be run every-time:

您无需每次需要运行这些工作就可以手动触发作业，也可以每次对其进行编程以进行运行：

* Some time passes: [Time resource](https://github.com/concourse/time-resource/)
* On new commits to the main branch: [Git resource](https://github.com/concourse/git-resource)

*在新提交的主要分支：[git Resource]（https://github.com/concourse/git-resource）
* New PR's: [Github-PR resource](https://github.com/telia-oss/github-pr-resource)

* new pr：[github-pr Resource]（https://github.com/telia-oss/github-pr-resource）
* Fetch or push the latest image of your app: [Registry-image resource](https://github.com/concourse/registry-image-resource/)

*获取或推动应用程序的最新图像：[注册表 - 图像资源]（https://github.com/concourse/registry-image-image-resource/）

Check a YAML pipeline example that triggers on new commits to master in [https://concourse-ci.org/tutorial-resources.html](https://concourse-ci.org/tutorial-resources.html)

检查一个YAML管道示例，该示例触发新的承诺在[https://concourse-ci.org/tutorial-resources.html]：https://concourse-ci.org/tutorial-resources.html）


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


