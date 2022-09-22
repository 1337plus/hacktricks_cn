

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


# Introduction to GCP Privilege Escalation <a href="#introduction-to-gcp-privilege-escalation" id="introduction-to-gcp-privilege-escalation"></a>

＃GCP特权升级<a href="#introduction to gcp-privilege-escalation“id="indroduction-to-gcp-privilege-escalation"> </a>

GCP, as any other cloud, have some **principals**: users, groups and service accounts, and some **resources** like compute engine, cloud functions…\

GCP作为任何其他云，都有一些**校长**：用户，组和服务帐户以及一些**资源**喜欢计算引擎，云功能…\
Then, via roles, **permissions are granted to those principals over the resources**. This is the way to specify the permissions a principal has over a resource in GCP.\

然后，通过角色，**权限被授予这些委托人的资源**。 这是指定本金对GCP中资源的权限。\ \ \ \
There are certain permissions that will allow a user to **get even more permissions** on the resource or third party resources, and that’s what is called **privilege escalation** (also, the exploitation the vulnerabilities to get more permissions).

有某些权限可以使用户在资源或第三方资源上获得更多的权限**，这就是所谓的**特权升级**（另外，利用了获得更多权限的漏洞）。

Therefore, I would like to separate GCP privilege escalation techniques in **2 groups**:

因此，我想在** 2组**中分开GCP特权升级技术：

* **Privesc to a principal**: This will allow you to **impersonate another principal**, and therefore act like it with all his permissions. e.g.: Abuse _getAccessToken_ to impersonate a service account.

***对校长的PRIVESC **：这将使您**模仿另一个校长**，因此，他的所有权限都像这样行事。 例如：滥用_getAccessToken_模仿服务帐户。
* **Privesc on the resource**: This will allow you to **get more permissions over the specific resource**. e.g.: you can abuse _setIamPolicy_ permission over cloudfunctions to allow you to trigger the function.

***资源上的privesc **：这将使您**对特定资源获得更多权限**。 例如：您可以滥用_setiampolicy_对CloudFunctions的权限，以允许您触发该功能。
  * Note that some **resources permissions will also allow you to attach an arbitrary service account** to the resource. This means that you will be able to launch a resource with a SA, get into the resource, and **steal the SA token**. Therefore, this will allow to escalate to a principal via a resource escalation. This has happened in several resources previously, but now it’s less frequent (but can still happen).

*请注意，一些**资源权限还可以使您可以将任意服务帐户**附加到资源。 这意味着您将能够使用SA启动资源，进入资源，然后**窃取SA代币**。 因此，这将允许通过资源升级升级为本金。 以前在几个资源中发生了这种情况，但是现在它不太频繁（但仍然可以发生）。

Obviously, the most interesting privilege escalation techniques are the ones of the **second group** because it will allow you to **get more privileges outside of the resources you already have** some privileges over. However, note that **escalating in resources** may give you also access to **sensitive information** or even to **other principals** (maybe via reading a secret that contains a token of a SA).

显然，最有趣的特权升级技术是**第二组**的一种，因为它可以使您**在已经拥有一些特权的资源之外获得更多特权。 但是，请注意，**在资源中升级**可能还会让您访问**敏感信息**甚至**其他校长**（也许是通过阅读一个包含SA代币的秘密）。

{% hint style="warning" %}

{％提示样式=“警告”％}
It's important to note also that in **GCP Service Accounts are both principals and permissions**, so escalating privileges in a SA will allow you to impersonate it also.

重要的是还要注意，在** GCP服务帐户中既是校长和权限**，因此SA中的特权升级将使您也可以假冒它。
{% endhint %}

{% hint style="info" %}

{％提示样式=“ info”％}
The permissions between parenthesis indicate the permissions needed to exploit the vulnerability with `gcloud`. Those might not be needed if exploiting it through the API.

括号之间的权限表明用“ gcloud”利用漏洞所需的权限。 如果通过API利用它，可能不需要这些。
{% endhint %}

# Privilege Escalation to Principals

＃特权升级为校长

Check all the **known permissions** that will allow you to **escalate privileges over other principals** in:

检查所有**已知的权限**，这些权限将使您可以**升级特权。

{% content-ref url="gcp-privesc-to-other-principals.md" %}

{％content-ref url =“ gcp-privesc-to-other-principals.md”％}
[gcp-privesc-to-other-principals.md](gcp-privesc-to-other-principals.md)

[gcp-privesc-to-other-principals.md]（gcp-privesc-to to principals.md）
{% endcontent-ref %}

# Privilege Escalation to Resources

＃特权升级为资源

Check all the **known permissions** that will allow you to **escalate privileges over other resources** in:

检查所有**已知的权限**，这些权限将使您可以**升级特权，以升级其他资源**。

{% content-ref url="gcp-privesc-to-resources.md" %}
[gcp-privesc-to-resources.md](gcp-privesc-to-resources.md)

[GCP-PRIVESC-TO-RESOURCES.MD]（GCP-PRIVESC-TO-RESOURCES.MD）
{% endcontent-ref %}

#


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


