# Workspace Security

＃工作区安全

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

## Workspace Phishing

##工作区网络钓鱼

### Generic Phishing Methodology

###通用网络钓鱼方法

{% content-ref url="../generic-methodologies-and-resources/phishing-methodology/" %}

{％content-ref url =“ ../通用 - 莫思诺论和归因/网络钓鱼方法/“％}
[phishing-methodology](../generic-methodologies-and-resources/phishing-methodology/)

[网络钓鱼方法]（../ generic-methodogolies-and-resources/eThisting-hododology/）
{% endcontent-ref %}

### Google Groups Phishing

### Google组网络钓鱼

Apparently by default in workspace members [**can create groups**](https://groups.google.com/all-groups) **and invite people to them**. You can then modify the email that will be sent to the user **adding some links.** The **email will come from a google address**, so it will looks **legit** and people might click on the link.

显然，默认情况下，工作空间成员[**可以创建组**]（https://groups.google.com/all-groups）**，并邀请人们给他们**。 然后，您可以修改将发送给用户**添加一些链接的电子邮件。**电子邮件将来自Google地址**，因此看起来**合法**，人们可能会单击链接。 。

### Hangout Phishing

You might be able either to directly talk with a person just having his email address or sending an invitation to talk. Either way, modify an email account maybe naming it "Google Security" and adding some Google logos, and the people will think they are talking to google: [https://www.youtube.com/watch?v=KTVHLolz6cE\&t=904s](https://www.youtube.com/watch?v=KTVHLolz6cE\&t=904s)

您可能可以直接与仅有电子邮件地址的人交谈，或者发送邀请函进行交谈。 无论哪种方式，修改电子邮件帐户都可以将其命名为“ Google Security”并添加一些Google徽标，人们会认为他们正在与Google交谈：[https://www.youtube.com/watch?v=ktvhlolz6ce \＆t = 904s]（https://www.youtube.com/watch?v=ktvhlolz6ce \＆t = 904s）

Just the **same technique** can be used with **Google Chat**.

仅**相同的技术**可以与** Google Chat **一起使用。

### Google Doc Phishing

### Google Doc网络钓鱼

You can create an **apparently legitimate document** and the in a comment **mention some email (like +user@gmail.com)**. Google will **send an email to that email address** notifying that he was mentioned in the document. You can **put a link in that document** to try to make the persona access it.

您可以创建一个显然是合法的文件**，并在评论中**提及一些电子邮件（例如 +user@gmail.com）**。 Google将**将电子邮件发送到该电子邮件地址**通知他在文档中提到了他。 您可以**在该文档中放置一个链接**，以使角色访问它。

### Google Calendar Phishing

### Google日历网络钓鱼

You can **create a calendar event** and add as many email address of the company you are attacking as you have. Schedule this calendar event in **5 or 15 min** from the current time. Make the event looks legit and **put a comment indicating that they need to read something** (with the **phishing link**).\

您可以**创建一个日历事件**，并添加您正在攻击的公司的许多电子邮件地址。 从当前时间安排** 5或15分钟**的日历事件。 使活动看起来合法，并提出评论，表明他们需要阅读一些东西**（带有**网络钓鱼链接**）。\ \ \
To make it looks less suspicious:

* Set that the **receivers cannot see the other invited people**

*设置**接收者看不到其他受邀的人**
* Do **NOT send emails notifying about the event**. Then, the people will only see their warning about a meeting in 5mins and that they need to read that link.

*做**不要发送有关事件通知的电子邮件**。 然后，人民只会看到他们对5分钟会议的警告，他们需要阅读该链接。
* Apparently using the API you can set to **True** that **people** has **accepted** the event and even create **comments on their behalf**.

*显然，使用API，您可以设置为** true ** **人们已经接受**接受了**事件，甚至可以代表他们的**创建**评论。

### OAuth Phishing

### Oauth网络钓鱼

Any of the previous techniques might be used to make the user access a **Google OAuth application** that will **request** the user some **access**. If the user **trust** the **source** he might **trust** the **application** (even if it's asking for high privileged permissions).

以前的任何技术都可以用来使用户访问** Google OAuth应用程序**将**请求**用户一些**访问**。 如果用户**信任** **源**他可能会**信任** **应用程序**（即使是要求高特权权限）。

Note that Google presents an ugly prompt asking warning that the application is untrusted in several cases and from Workspace admins can even prevent people to accept OAuth applications. More on this in the OAuth section.

请注意，Google提出了一个丑陋的提示，询问警告说，该应用程序在几种情况下是不信任的，而从工作区管理员则可以阻止人们接受OAuth应用程序。 在OAUTH部分中有关此信息的更多信息。

## Password Spraying

##密码喷涂

In order to test passwords with all the emails you found (or you have generated based in a email name pattern you might have discover) you can use a tool like [**https://github.com/ustayready/CredKing**](https://github.com/ustayready/CredKing) who will use AWS lambdas to change IP address.

为了使用您发现的所有电子邮件测试密码（或者您已经基于您可能发现的电子邮件名称模式生成），您可以使用[** https：//github.com/ustayready/credkingjequent]之类的工具。 （https://github.com/ustayready/credking）谁将使用AWS lambdas更改IP地址。

## Oauth Apps

## Oauth应用程序

**Google** allows to create applications that can **interact on behalf users** with several **Google services**: Gmail, Drive, GCP...

** Google **允许创建可以**代表用户交互的应用程序**与多个** Google Services **：Gmail，drive，GCP ...

When creating an application to **act on behalf other users**, the developer needs to create an **OAuth app inside GCP** and indicate the scopes (permissions) the app needs to access the users data.\

当创建代表其他用户的应用程序时，开发人员需要在GCP **内创建** oauth应用程序，并指示范围（权限）应用程序需要访问用户数据。\ \ \ \ \ \
When a **user** wants to **use** that **application**, he will be **prompted** to **accept** that the application will access to his data specified in the scopes.

当一个**用户**想要**使用**应用程序**时，他将被**提示**接受**接受**该应用程序将访问其范围中指定的数据。

This is a very juicy way to **phish** non-technical users into using **applications that access sensitive information** because they might not understand the consequences. Therefore, in organizations accounts, there are ways to prevent this from happening.

这是一种非常多汁的方法，可以** phish **非技术用户使用**访问敏感信息**的应用程序，因为他们可能不了解后果。 因此，在组织帐户中，有一些方法可以防止这种情况发生。

### Unverified App prompt

###未经验证的应用提示

As it was mentioned, google will always present a **prompt to the user to accept** the permissions he is giving the application on his behalf. However, if the application is considered **dangerous**, google will show **first** a **prompt** indicating that it's **dangerous** and **making more difficult** to the user to grant the permissions to the app.

如前所述，Google将始终向用户提示**接受他代表他提供申请的权限。 但是，如果认为该应用程序**危险**，Google将首先显示** a **提示**，表明**危险**，并且**使用户更加困难**授予权限 到该应用程序。

This prompt appears in apps that:

该提示在应用程序中出现：

* Uses any scope that can access to private data (Gmail, Drive, GCP, BigQuery...)

*使用任何可以访问私有数据的范围（gmail，drive，gcp，bigquery ...）
* Apps with less than 100 users (apps > 100 a review process is needed also to not show the unverified prompt)

*少于100个用户的应用程序（应用程序> 100个应用程序也需要一个审核过程，以不显示未验证的提示）

### Interesting Scopes

###有趣的范围

You can [**find here**](https://developers.google.com/identity/protocols/oauth2/scopes) a list of all the Google OAuth scopes.

您可以[**在此处找到**]（https://developers.google.com/identity/protocols/oauth2/scopes）列出了所有Google Oauth范围。

* **cloud-platform**: View and manage your data across **Google Cloud Platform** services. You can impersonate the user in GCP.

***云平台**：通过** Google Cloud Platform **服务查看和管理您的数据。 您可以在GCP中冒充用户。
* **directory.readonly**: See and download your organization's GSuite directory. Get names, phones, calendar URLs of all the users.

*** Directory.Readonly **：请参阅并下载组织的GSUITE目录。 获取所有用户的名称，电话，日历URL。

## App Scripts

##应用脚本

Developers can create App Scripts and set them as a standalone project or bound them to Google Docs/Sheets/Slides/Forms. App Scripts is code that will be triggered when a user with editor permission access the doc (and after accepting the OAuth prompt)

开发人员可以创建应用程序脚本并将其设置为独立项目，也可以将其绑定到Google Docs/Sheets/Sheets/幻灯片/表单。 App脚本是当用户许可访问DOC时将触发的代码（在接受OAUTH提示符之后）

However, even if the app isn't verified there are a couple of ways to not show that prompt:

但是，即使未验证该应用程序，也有几种不显示该提示的方法：

* If the publisher of the app is in the same Workspace as the user accessing it

*如果应用程序的发布者与用户访问它的工作空间相同
* If the script is in a drive of the user

*如果脚本在用户的驱动器中

### Copy Document Unverified Prompt Bypass

###复制文档未经验证的提示旁路

When you create a link to share a document a link similar to this one is created: `https://docs.google.com/spreadsheets/d/1i5[...]aIUD/edit`\

创建一个链接共享文档时，创建了类似于此的链接：`https：//docs.google.com/spreadsheets/d/1i5 [...] aiud/edit` \
If you **change** the ending **"/edit"** for **"/copy"**, instead of accessing it google will ask you if you want to **generate a copy of the document.**

如果您**更改** ending **“/edit” ** for*for **“/copy” **，而不是访问它，则会询问您是否要**生成文档的副本。**

{% hint style="warning" %}

{％提示样式=“警告”％}
If someone creates a **copy** of that **document** that **contained the App Script**, he will also be **copying the App Script**, therefore when he **opens** the copied **spreadsheet**, the **regular OAuth prompt** will appear **bypassing the unverified prompt**, because **the user is now the author of the App Script of the copied file**.

如果某人创建了该**文档的**副本**，**包含应用程序脚本**，他也将**复制应用程序脚本**，因此，当他**打开**复制**时** *电子表格**，**常规的OAuth提示**将出现**绕过未验证的提示**，因为**用户现在是复制文件的应用程序脚本的作者**。
{% endhint %}

This method will be able to bypass also the Workspace admin restriction:

此方法将能够绕过工作空间管理限制：

![](<../.gitbook/assets/image (662) (1) (1) (1) (1).png>)

But can be prevented with:

但可以防止：

![](<../.gitbook/assets/image (632).png>)

![](<../.gitbook/assets/image (632).png>)

### Shared Document Unverified Prompt Bypass

###共享文档未验证的提示旁路

Moreover, if someone **shared** with you a document with **editor access**, you can generate **App Scripts inside the document** and the **OWNER (creator) of the document will be the owner of the App Script**.

此外，如果与您共享** **的某人与**编辑器访问**的文档，您可以在文档**内生成**应用程序脚本，并且文档的**所有者（创建者）将是该文档的所有者 应用脚本**。

{% hint style="warning" %}

{％提示样式=“警告”％}
This means, that the **creator of the document will appear as creator of any App Script** anyone with editor access creates inside of it.

这意味着，该文档的**创建者将以任何具有编辑器访问的人的创建者的形式出现。

This also means that the **App Script will be trusted by the Workspace environment** of the creator of the document.

这也意味着**应用程序脚本将被文档创建者的工作区环境**信任。
{% endhint %}

{% hint style="danger" %}
This also means that if an **App Script already existed** and people has **granted access**, anyone with **Editor** permission to the doc can **modify it and abuse that access.**\

这也意味着，如果一个**应用程序脚本已经存在**，并且人们已经**授予访问**，那么任何具有编辑器**的人都可以**对其进行**修改并滥用访问权限。** \ \ \ \ \ \ \ \
To abuse this you also need people to trigger the App Script. And one neat trick if to **publish the script as a web app**. When the **people** that already granted **access** to the App Script access the web page, they will **trigger the App Script** (this also works using `<img>` tags.

要滥用这一点，您还需要人们触发应用程序脚本。 如果要**将脚本发布为Web应用程序**，则一个整洁的技巧。 当已经授予**访问App脚本的**人**访问网页时，他们将**触发应用程序脚本**（这也使用`<img>`标签都可以使用。
{% endhint %}

## Post-Exploitation

### Google Groups Privesc

### Google Groups Privesc

By default in workspace a **group** can be **freely accessed** by any member of the organization.\

默认情况下，工作区A **组**可以被组织的任何成员自由访问**。
Workspace also allow to **grant permission to groups** (even GCP permissions), so if groups can be joined and they have extra permissions, an attacker may **abuse that path to escalate privileges**.

工作空间还允许**授予团体**（甚至是GCP权限）的权限，因此，如果可以加入组并拥有额外的许可，则攻击者可能会**滥用该路径升级特权**。

You potentially need access to the console to join groups that allow to be joined by anyone in the org. Check groups information in [**https://groups.google.com/all-groups**](https://groups.google.com/all-groups).

您可能需要访问控制台才能加入允许由组织中的任何人加入的组。 在[** https：//groups.google.com/all-groupsde]中检查组信息（https://groups.google.com/all-groups）。

### Privesc to GCP Summary

### Privesc至GCP摘要

* Abusing the **google groups privesc** you might be able to escalate to a group with some kind of privileged access to GCP

*滥用** Google组PRIVESC **您可能可以升级到具有某种特权访问GCP的小组
* Abusing **OAuth applications** you might be able to impersonate users and access to GCP on their behalf

*滥用** oauth应用程序**您可以代表他们模仿用户并访问GCP

### Access Groups Mail info

###访问组邮件信息

If you managed to **compromise a google user session**, from [**https://groups.google.com/all-groups**](https://groups.google.com/all-groups) you can see the history of mails sent to the mail groups the user is member of, and you might find **credentials** or other **sensitive data**.

如果您设法**妥协Google用户会话** 可以看到发送给用户成员的邮件组的邮件的历史记录，您可能会发现**凭据**或其他**敏感数据**。

### Takeout - Download Everything Google Knows about an account

###外卖 - 下载Google知道的所有信息

If you have a **session inside victims google account** you can download everything Google saves about that account from [**https://takeout.google.com**](https://takeout.google.com/u/1/?pageId=none)

如果您在受害者内部有一个**会话Google帐户**，您可以从[** https：//takeout.google.comp.d.pom]下载Google Sav About About Alove Save About Alove Save Sav /1/？pageid =无）

### Vault - Download all the Workspace data of users

### Vault-下载用户的所有工作空间数据

If an organization has **Google Vault enabled**, you might be able to access [**https://vault.google.com**](https://vault.google.com/u/1/) and **download** all the **information**.

如果组织已启用了** Google Vault **，则您可以访问[** https：//vault.google.compy]（https://vault.google.com/u/1/）和 **下载**所有**信息**。

### Contacts download

###联系人下载

From [**https://contacts.google.com**](https://contacts.google.com/u/1/?hl=es\&tab=mC) you can download all the **contacts** of the user.

摘自[** https：//contacts.google.compy] 用户。

### Cloudsearch

### CloudSearch

In [**https://cloudsearch.google.com/**](https://cloudsearch.google.com) you can just search **through all the Workspace content** (email, drive, sites...) a user has access to. Ideal to **find quickly sensitive information**.

在[** https：//cloudsearch.google.com/xpry.com/ghyday]（https://cloudsearch.google.com）中，您可以通过所有工作空间内容**搜索**（电子邮件，驱动器，站点... ）用户可以访问。 **找到快速敏感信息**的理想选择。

### Currents

In [**https://currents.google.com/**](https://currents.google.com) you can access a Google **Chat**, so you might find sensitive information in there.

在[** https：//currents.google.com/xpry]（https://currents.google.com）中，您可以访问Google ** chat **，因此您可能会在其中找到敏感信息。

### Google Drive Mining

### Google Drive采矿

When **sharing** a document yo can **specify** the **people** that can access it one by one, **share** it with your **entire company** (**or** with some specific **groups**) by **generating a link**.

当**共享**文档时，您可以**指定**可以一个人访问它的** **，**与您的**整个公司共享**（**或**） 一些特定的**组**）通过**生成链接**。

When sharing a document, in the advance setting you can also **allow people to search** for this file (by **default** this is **disabled**). However, it's important to note that once users views a document, it's searchable by them.

共享文档时，在预先设置中，您还可以**允许人们搜索此文件（**默认**这是**禁用**）。 但是，重要的是要注意，一旦用户查看文档，就可以通过他们搜索。

For sake of simplicity, most of the people will generate and share a link instead of adding the people that can access the document one by one.

为了简单起见，大多数人都会生成和共享一个链接，而不是添加可以一一访问文档的人。

Some proposed ways to find all the documents:

一些建议查找所有文件的方法：

* Search in internal chat, forums...

*在内部聊天中搜索，论坛...
* **Spider** known **documents** searching for **references** to other documents. You can do this within an App Script with[ **PaperChaser**](https://github.com/mandatoryprogrammer/PaperChaser)

***蜘蛛**已知**文档**搜索**参考**到其他文档。 您可以在[** PaperChaser **]（https://github.com/mandatoryprogrammer/praperchaser）的应用程序脚本中执行此操作。

### **Keep Notes**

In [**https://keep.google.com/**](https://keep.google.com) you can access the notes of the user, **sensitive** **information** might be saved in here.

在[** https：//ezep.google.com/phdy]（https://keep.google.com）中，您可以访问用户的笔记，**敏感** **信息**可能会保存 在这里。

### Persistence inside a Google account

### Google帐户中的持久性

If you managed to **compromise a google user session** and the user had **2FA**, you can **generate** an [**app password**](https://support.google.com/accounts/answer/185833?hl=en) and **regenerate the 2FA backup codes** to know that even if the user change the password you **will be able to access his account**. Another option **instead** of **regenerating** the codes is to **enrol your own authenticator** app in the 2FA.

如果您设法**妥协了Google用户会话**，并且用户拥有** 2fa **，则可以**生成** [**应用程序密码**]（https://support.google.com/ 帐户/答案/185833？hl = en）和**再生2FA备份代码**，即使用户更改密码，您**也可以访问他的帐户**。 另一个选项** **的**再生**代码是**在2FA中注册您自己的身份验证器**应用程序。

### Persistence via OAuth Apps

###通过Oauth应用程序的持久性

If you have **compromised the account of a user,** you can just **accept** to grant all the possible permissions to an **OAuth App**. The only problem is that Workspace can configure to **disallow external and/or internal OAuth apps** without being reviewed.\

如果您已经妥协了用户的帐户，则可以**接受**将所有可能的权限授予** oauth应用程序**。 唯一的问题是工作空间可以配置为**禁止外部和/或内部OAuth应用程序**，而无需审核。\ \ \ \
It is pretty common to not trust by default external OAuth apps but trust internal ones, so if you have **enough permissions to generate a new OAuth application** inside the organization and external apps are disallowed, generate it and **use that new internal OAuth app to maintain persistence**.

默认情况下不信任外部OAuth应用程序，而是信任内部应用程序，因此，如果您拥有足够的权限来生成新的OAuth应用程序**，则不允许使用新的OAuth应用程序，并且不允许使用外部应用 内部OAuth应用程序以保持持久性**。

### Persistence via delegation

You can just **delegate the account** to a different account controlled by the attacker.

您可以将帐户**委派给由攻击者控制的其他帐户。

### Persistence via Android App

###通过Android应用程序的持久性

If you have a **session inside victims google account** you can browse to the **Play Store** and **install** a **malware** you have already uploaded it directly **in the phone** to maintain persistence and access the victims phone.

如果您在受害者内部有一个**会话Google帐户**，您可以浏览** play商店**和**安装** a **恶意软件**您已经将其直接上传** ** ** 保持持久性并访问受害者电话。

### **Persistence via Gmail**

* You can create **filters to hide** security notifications from Google

*您可以创建**过滤器隐藏**从Google那里的安全通知
  * from: (no-reply@accounts.google.com) "Security Alert"

*来自：（ no-reply@accounts.google.com）“安全警报”
  * Hide password reset emails
* Create **forwarding address to forward sensitive information** (or everything) - You need manual access.

*创建**转发地址以转发敏感信息**（或所有内容） - 您需要手动访问。
  * Create a forwarding address to send emails that contains the word "password" for example

*创建一个转发地址以发送包含“密码”一词的电子邮件
* Add **recovery email/phone under attackers control**

*添加**攻击者控制下的恢复电子邮件/电话**

### **Persistence via** App Scripts

### **通过**应用程序脚本的持久性

You can create **time-based triggers** in App Scripts, so if the App Script is accepted by the user, it will be **triggered** even **without the user accessing it**.

您可以在应用程序脚本中创建**基于时间的触发器**，因此，如果用户接受应用程序脚本，它将被**触发**甚至**，而无需用户访问它**。

The docs mention that to use `ScriptApp.newTrigger("funcion")` you need the **scope** `script.scriptapp`, but **apparently thats not necessary** as long as you have declare some other scope.

文档提到要使用`scriptapp.newtrigger（“ funcion”）`您需要** scope **`script.script.scriptapp`，但是**显然，只要您声明了其他范围，就不需要**。

### **Administrate Workspace**

### **管理工作区**

In [**https://admin.google.com**/](https://admin.google.com), if you have enough permissions you might be able to modify settings in the Workspace of the whole organization.

在[** https：//admin.google.comxed/]（https://admin.google.com）中，如果您有足够的许可，则可以在整个组织的工作区中修改设置。

You can also search emails through all the users invoices in [**https://admin.google.com/ac/emaillogsearch**](https://admin.google.com/ac/emaillogsearch)

您还可以通过[** https：//admin.google.com/ac/emaillogsearch**]中的所有用户发票搜索电子邮件

## Account Compromised Recovery

##帐户损害恢复

* Log out of all sessions

*登录所有会议
* Change user password

*更改用户密码
* Generate new 2FA backup codes

*生成新的2FA备份代码
* Remove App passwords

*删除应用程序密码
* Remove OAuth apps

*删除Oauth应用程序
* Remove 2FA devices
* Remove email forwarders

*删除电子邮件转发器
* Remove emails filters

*删除电子邮件过滤器
* Remove recovery email/phones

*删除恢复电子邮件/电话
* Remove bad Android Apps

*删除坏Android应用程序
* Remove bad account delegations

*删除不良帐户代表团

## References

* [https://www.youtube-nocookie.com/embed/6AsVUS79gLw](https://www.youtube-nocookie.com/embed/6AsVUS79gLw) - Matthew Bryant - Hacking G Suite: The Power of Dark Apps Script Magic

* [https://www.youtube-nocookie.com/embed/6asvus79glw]（
* [https://www.youtube.com/watch?v=KTVHLolz6cE](https://www.youtube.com/watch?v=KTVHLolz6cE) - Mike Felch and Beau Bullock - OK Google, How do I Red Team GSuite?

* [https://www.youtube.com/watch?v=ktvhlolz6ce] https://www.youtube.com/watch?v=ktvhlolz6ce） GSUITE？

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
