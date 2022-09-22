

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


**Check for nice cloud hacking tricks in** [**https://hackingthe.cloud**](https://hackingthe.cloud)

**在** [** https：//hackingthe.clouddhyddy]中检查不错的云黑客技巧（https://hackingthe.cloud）

# Generic tools

＃通用工具

There are several tools that can be used to test different cloud environments. The installation steps and links are going to be indicated in this section.

有几种工具可用于测试不同的云环境。 本节将指示安装步骤和链接。

## [ScoutSuite](https://github.com/nccgroup/ScoutSuite)

AWS, Azure, GCP, Alibaba Cloud, Oracle Cloud Infrastructure

```
pip3 install scoutsuite
```

## [cs-suite](https://github.com/SecurityFTW/cs-suite)

AWS, GCP, Azure, DigitalOcean

```
git clone https://github.com/SecurityFTW/cs-suite.git && cd cs-suite/
pip install virtualenv
virtualenv -p python2.7 venv
source venv/bin/activate
pip install -r requirements.txt
python cs.py --help
```

## Nessus

Nessus has an _**Audit Cloud Infrastructure**_ scan supporting: AWS, Azure, Office 365, Rackspace, Salesforce. Some extra configurations in **Azure** are needed to obtain a **Client Id**.

Nessus有一个_ **审核云基础架构** _扫描支持：AWS，Azure，Office 365，Rackspace，Salesforce。 需要在** azure **中获得一些额外的配置，以获取**客户端ID **。

## Common Sense

Take a look to the **network access rules** and detect if the services are correctly protected:

查看**网络访问规则**，并检测服务是否正确保护：

* ssh available from everywhere?

* SSH无处不在？
* Unencrypted services running (telnet, http, ...)?

*运行未加密的服务（telnet，http，...）？
* Unprotected admin consoles?

*未受保护的管理控制台？
* In general, check that all services are correctly protected depending on their needs

*通常，根据其需求，检查所有服务是否正确保护

# Azure

Access the portal here: [http://portal.azure.com/](http://portal.azure.com)\

在此处访问门户网站：[http://portal.azure.com/]（http://portal.azure.com）\
To start the tests you should have access with a user with **Reader permissions over the subscription** and **Global Reader role in AzureAD**. If even in that case you are **not able to access the content of the Storage accounts** you can fix it with the **role Storage Account Contributor**.

要启动测试，您应该可以与用户可以使用**读取器权限的用户访问订阅**和**全球读者在Azuread **中的角色。 即使在这种情况下，您**无法访问存储帐户的内容**，您也可以使用**角色存储帐户贡献者**修复它。

It is recommended to **install azure-cli** in a **linux** and **windows** virtual machines (to be able to run powershell and python scripts): [https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)\

建议在** linux **和** Windows **虚拟机（能够运行PowerShell和Python脚本）中**安装Azure-Cli ** **：[https://docs.microsoft.com/ en-us/cli/azure/install-azure-cli？view = azure-cli-latest]（https://docs.microsoft.com/en-us/cli/cli/azure/install-azure-cli?view = azure -cli-latest）\
Then, run `az login` to login. Note the **account information** and **token** will be **saved** inside _\<HOME>/.azure_ (in both Windows and Linux).

然后，运行“ AZ登录”登录。 注意**帐户信息**和**令牌**将被**保存** ** _ \ <home>/。azure_（在Windows和Linux中）。

Remember that if the **Security Centre Standard Pricing Tier** is being used and **not** the **free** tier, you can **generate** a **CIS compliance scan report** from the azure portal. Go to _Policy & Compliance-> Regulatory Compliance_ (or try to access [https://portal.azure.com/#blade/Microsoft\_Azure\_Security/SecurityMenuBlade/22](https://portal.azure.com/#blade/Microsoft\_Azure\_Security/SecurityMenuBlade/22)).\

请记住，如果使用**安全中心标准定价层**，并且**不** ** free ** tier，则可以**生成** a ** a ** cis合规性扫描报告**来自Azure Portal 。 转到_policy＆Compliance->监管合规性_（或尝试访问[https://portal.azure.com/#blade/microsoft \ _azure _security/securitymenublade/22]（ Blade/Microsoft \ _azure \ _security/SecurityMenublade/22））。
\_\_If the company is not paying for a Standard account you may need to review the **CIS Microsoft Azure Foundations Benchmark** by "hand" (you can get some help using the following tools). Download it from [**here**](https://www.newnettechnologies.com/cis-benchmark.html?keyword=\&gclid=Cj0KCQjwyPbzBRDsARIsAFh15JYSireQtX57C6XF8cfZU3JVjswtaLFJndC3Hv45YraKpLVDgLqEY6IaAhsZEALw\_wcB#microsoft-azure).

\ _ \ _如果公司不为标准帐户付款，则可能需要通过“手”来查看** CIS Microsoft Azure基础基准**（您可以使用以下工具获得一些帮助）。

## Run scanners

Run the scanners to look for **vulnerabilities** and **compare** the security measures implemented with **CIS**.

运行扫描仪以寻找**漏洞**和**比较**使用** cis **实施的安全措施。

```bash
pip install scout
scout azure --cli --report-dir <output_dir>

#Fix azureaudit.py before launching cs.py
#Adding "j_res = {}" on line 1074
python cs.py -env azure

#Azucar is an Azure security scanner for PowerShell (https://github.com/nccgroup/azucar)
#Run it from its folder
.\Azucar.ps1 -AuthMode Interactive -ForceAuth -ExportTo EXCEL

#Azure-CIS-Scanner,CIS scanner for Azure (https://github.com/kbroughton/azure_cis_scanner)
pip3 install azure-cis-scanner #Install
azscan #Run, login before with `az login`
```

## Attack Graph

##攻击图

[**Stormspotter** ](https://github.com/Azure/Stormspotter)creates an “attack graph” of the resources in an Azure subscription. It enables red teams and pentesters to visualize the attack surface and pivot opportunities within a tenant, and supercharges your defenders to quickly orient and prioritize incident response work.

[** Stormspotter **]（https://github.com/azure/stormspotter）在Azure订阅中创建资源的“攻击图”。 它使红色团队和申人能够可视化接地人中的攻击表面和枢纽机会，并为您的防御者增强捍卫者以快速和优先级的事件响应工作。

## More checks

##更多检查

* Check for a **high number of Global Admin** (between 2-4 are recommended). Access it on: [https://portal.azure.com/#blade/Microsoft\_AAD\_IAM/ActiveDirectoryMenuBlade/Overview](https://portal.azure.com/#blade/Microsoft\_AAD\_IAM/ActiveDirectoryMenuBlade/Overview)

*检查**大量的全局管理**（建议在2-4之间）。 请访问：[https://portal.azure.com/#blade/microsoft \ _AAD_AADX_IAM/ACTIVEDIRECTORYMENUBLADE/OVERVIEW]（ 概述）
* Global admins should have MFA activated. Go to Users and click on Multi-Factor Authentication button.

*全球管理员应该激活MFA。 转到用户，然后单击多因素身份验证按钮。

![](<../.gitbook/assets/image (293).png>)

* Dedicated admin account shouldn't have mailboxes (they can only have mailboxes if they have Office 365).

*专用管理帐户不应有邮箱（只有在有Office 365的情况下，它们才能有邮箱）。
* Local AD shouldn't be sync with Azure AD if not needed([https://portal.azure.com/#blade/Microsoft\_AAD\_IAM/ActiveDirectoryMenuBlade/AzureADConnect](https://portal.azure.com/#blade/Microsoft\_AAD\_IAM/ActiveDirectoryMenuBlade/AzureADConnect)). And if synced Password Hash Sync should be enabled for reliability. In this case it's disabled:

*如果不需要，本地广告不应与Azure AD同步（[https://portal.azure.com/#blade/microsoft \ _AAD_AAD_EIM/ACTIVERECTORECERECTORYMENUBLADE/AZUREADCONNECT]（https://portal.azure.com/ ＃blade/microsoft \ _aad \ _iam/procivedirectorymenublade/azureadConnect））。 并且，如果同步密码哈希同步应启用可靠性。 在这种情况下，它被禁用：

![](<../.gitbook/assets/image (294).png>)

* **Global Administrators** shouldn't be synced from a local AD. Check if Global Administrators emails uses the domain **onmicrosoft.com**. If not, check the source of the user, the source should be Azure Active Directory, if it comes from Windows Server AD, then report it.

***全球管理员**不应从本地广告中同步。 检查全局管理员是否使用域** onmicrosoft.com **。 如果不是，请检查用户的来源，源应为Azure Active Directory，如果它来自Windows Server AD，请报告。

![](<../.gitbook/assets/image (295).png>)

* **Standard tier** is recommended instead of free tier (see the tier being used in _Pricing & Settings_ or in [https://portal.azure.com/#blade/Microsoft\_Azure\_Security/SecurityMenuBlade/24](https://portal.azure.com/#blade/Microsoft\_Azure\_Security/SecurityMenuBlade/24))

***建议使用标准级别**而不是免费层（请参阅_pricing＆settings_或[https://portal.azure.com/#blade/microsoft/microsoft \ _azure _security/securitymenublade/24]（24]（24）（ https://portal.azure.com/#blade/microsoft \_azure _security/securitymenublade/24））
*   **Periodic SQL servers scans**:

***定期SQL服务器扫描**：

    _Select the SQL server_ --> _Make sure that 'Advanced data security' is set to 'On'_ --> _Under 'Vulnerability assessment settings', set 'Periodic recurring scans' to 'On', and configure a storage account for storing vulnerability assessment scan results_ --> _Click Save_

_选择SQL Server _-> _ make确保“高级数据安全”设置为'on'_--> _under“漏洞评估设置”，将“定期重复扫描”设置为“ on”，并配置存储帐户以存储以存储 脆弱性评估扫描结果_-> _ Click Save_
* **Lack of App Services restrictions**: Look for "App Services" in Azure ([https://portal.azure.com/#blade/HubsExtension/BrowseResource/resourceType/Microsoft.Web%2Fsites](https://portal.azure.com/#blade/HubsExtension/BrowseResource/resourceType/Microsoft.Web%2Fsites)) and check if anyone is being used. In that case check go through each App checking for "Access Restrictions" and there aren't rules, report it. The access to the app service should be restricted according to the needs.

***缺乏应用程序服务限制**：在Azure中寻找“ App Services”（[https://portal.azure.com/#blade/hubsextension/browseresource/resourcetype/microsoft.web%2fsiets of /portal.azure.com/#blade/hubsextension/browseresource/resourcetype/microsoft.web%2fsites）），检查是否使用过任何人。 在这种情况下，检查遍历每个应用程序检查“访问限制”，没有规则，请报告。 对应用程序服务的访问应根据需求限制。

# Office365

＃办公室365

You need **Global Admin** or at least **Global Admin Reader** (but note that Global Admin Reader is a little bit limited). However, those limitations appear in some PS modules and can be bypassed accessing the features via the web application.

您需要**全局管理员**或至少**全局管理员**（但请注意，全局管理员读者有些限制）。 但是，这些限制出现在某些PS模块中，可以通过Web应用程序绕过访问功能。

# AWS

Get objects in graph: [https://github.com/FSecureLABS/awspx](https://github.com/FSecureLABS/awspx)

在图中获取对象：[https://github.com/fsecurelabs/awspx]（https://github.com/fsecurelabs/awspx）

# GPC

{% content-ref url="gcp-security/" %}

{％content-ref url =“ gcp-security/”％}
[gcp-security](gcp-security/)

[GCP-SECURITY]（GCP-SECURITY/）
{% endcontent-ref %}


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


