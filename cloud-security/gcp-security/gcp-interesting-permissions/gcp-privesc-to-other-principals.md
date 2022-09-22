

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


{% hint style="info" %}

{％提示样式=“ info”％}
GCP has **hundreds of permissions**. This is just a list containing the **known** ones that could allow you to escalate to other principals.\

GCP拥有数百个权限**。 这只是一个包含**已知**的列表，可以让您升级为其他校长。
If you know about any other permissions not mentioned here, **please send a PR to add it** or let me know and I will add it.

如果您知道此处未提及的任何其他权限，**请发送PR添加**或让我知道，我会添加它。
{% endhint %}

# IAM

## iam.roles.update (iam.roles.get)

If you have the mentioned permissions you will be able to update a role assigned to you and give you extra permissions to other resources like:

如果您有上述权限，您将能够更新分配给您的角色，并为您提供其他资源的额外权限：

```bash
gcloud iam roldes update <rol name> --project <project> --add-permissions <permission>
```

You can find a script to automate the [**creation, exploit and cleaning of a vuln environment here**](gcp-privesc-to-other-principals.md#deploymentmanager) and a python script to abuse this privilege [**here**](https://github.com/RhinoSecurityLabs/GCP-IAM-Privilege-Escalation/blob/master/ExploitScripts/iam.roles.update.py). For more information check the [**original research**](https://rhinosecuritylabs.com/gcp/privilege-escalation-google-cloud-platform-part-1/).

您可以在此处找到一个脚本来自动化[**创建，利用和清洁vuln环境**]（gcp-privesc-to-to-prothincipals.md＃exploymentManager）和python脚本以滥用this ofilege [** ** 在这里**]（https://github.com/rhinosecuritylabs/gcp-iam-privilege-escalation/blob/master/exploitscripts/iam.roles.update.py）。 有关更多信息，请查看[**原始研究**]（https://rhinosecuritylabs.com/gcp/privilege-escalation-google-cloud-cloud-platform-part-part-part-1/）。

## iam.serviceAccounts.getAccessToken (iam.serviceAccounts.get)

## iam.serviceaccounts.getaccesstoken（iam.serviceaccounts.get）

This permission allows to **request an access token that belongs to a Service Account**, so it's possible to request an access token of a Service Account with more privileges than ours.

此权限允许**请求属于服务帐户的访问令牌**，因此可以请求具有比我们更多的特权的服务帐户的访问令牌。

You can find a script to automate the [**creation, exploit and cleaning of a vuln environment here**](https://github.com/carlospolop/gcp\_privesc\_scripts/blob/main/tests/4-iam.serviceAccounts.getAccessToken.sh) and a python script to abuse this privilege [**here**](https://github.com/RhinoSecurityLabs/GCP-IAM-Privilege-Escalation/blob/master/ExploitScripts/iam.serviceAccounts.getAccessToken.py). For more information check the [**original research**](https://rhinosecuritylabs.com/gcp/privilege-escalation-google-cloud-platform-part-1/).

您可以在此处找到一个脚本来自动化[**创建，利用和清洁vuln环境**]（https://github.com/carloppolop/gcp \ _privescccccccccccctscripts/blob/main/main/main/tests/4-4-iam 。 .getAccessToken.py）。 有关更多信息，请查看[**原始研究**]（https://rhinosecuritylabs.com/gcp/privilege-escalation-google-cloud-cloud-platform-part-part-part-1/）。

## iam.serviceAccountKeys.create

## iam.serviceaccountkeys.create

This permission allows us to do something similar to the previous method, but instead of an access token, we are **creating a user-managed key for a Service Account**, which will allow us to access GCP as that Service Account.

此权限使我们能够执行类似于先前方法的事情，但是我们**为服务帐户创建一个用户管理的密钥，而不是访问令牌**，这将使我们能够访问GCP作为该服务帐户。

```bash
gcloud iam service-accounts keys create --iam-account <name>
```

You can find a script to automate the [**creation, exploit and cleaning of a vuln environment here**](https://github.com/carlospolop/gcp\_privesc\_scripts/blob/main/tests/3-iam.serviceAccountKeys.create.sh) and a python script to abuse this privilege [**here**](https://github.com/RhinoSecurityLabs/GCP-IAM-Privilege-Escalation/blob/master/ExploitScripts/iam.serviceAccountKeys.create.py). For more information check the [**original research**](https://rhinosecuritylabs.com/gcp/privilege-escalation-google-cloud-platform-part-1/).

您可以在此处找到一个脚本来自动化[**创建，利用和清洁vuln环境**]（https://github.com/carloppolop/gcp \ _privescccccccccccctscripts/blob/main/main/main/tests/3-3-iam 。 .create.py）。 有关更多信息，请查看[**原始研究**]（https://rhinosecuritylabs.com/gcp/privilege-escalation-google-cloud-cloud-platform-part-part-part-1/）。

Note that **iam.serviceAccountKeys.update won't work to modify the key** of a SA because to do that the permissions iam.serviceAccountKeys.create is also needed.

请注意，** iam.serviceaccountkeys.update不起作用，可以修改SA的键**，因为也需要使用权限。

## iam.serviceAccounts.implicitDelegation

## iam.serviceaccounts.impliticdelegation

If you have the _**iam.serviceAccounts.implicitDelegation**_** permission on a Service Account** that has the _**iam.serviceAccounts.getAccessToken**_** permission on a third Service Account**, then you can use implicitDelegation to **create a token for that third Service Account**. Here is a diagram to help explain.

如果您有_ ** iam.serviceaccounts.impliticdelegation ** _ **在服务帐户上**具有_ ** iam.serviceaccounts.getaccesstoken ** _ ** _ **在第三服务帐户**，然后 您可以使用隐式元素来**为该第三个服务帐户创建令牌**。 这是一个有助于解释的图。

![](https://rhinosecuritylabs.com/wp-content/uploads/2020/04/image2-500x493.png)

You can find a script to automate the [**creation, exploit and cleaning of a vuln environment here**](https://github.com/carlospolop/gcp\_privesc\_scripts/blob/main/tests/5-iam.serviceAccounts.implicitDelegation.sh) and a python script to abuse this privilege [**here**](https://github.com/RhinoSecurityLabs/GCP-IAM-Privilege-Escalation/blob/master/ExploitScripts/iam.serviceAccounts.implicitDelegation.py). For more information check the [**original research**](https://rhinosecuritylabs.com/gcp/privilege-escalation-google-cloud-platform-part-1/).

您可以在此处找到一个脚本来自动化[**创建，利用和清洁vuln环境**]（https://github.com/carlospolop/gcp \ _privescccccccccccccrive_scripts/blob/main/main/main/tests/5-iam 。 .impliticdelegation.py）。 有关更多信息，请查看[**原始研究**]（https://rhinosecuritylabs.com/gcp/privilege-escalation-google-cloud-cloud-platform-part-part-part-1/）。

Note that according to the [**documentation**](https://cloud.google.com/iam/docs/understanding-service-accounts), the delegation only works to generate a token using the [**generateAccessToken()**](https://cloud.google.com/iam/credentials/reference/rest/v1/projects.serviceAccounts/generateAccessToken) method.

请注意，根据[**文档**]（https://cloud.google.com/iam/docs/understanding-service-accounts），该委托只能使用[** generateaccesstoken（）来生成一个令牌 **]（https://cloud.google.com/iam/credentials/reference/rest/v1/projects.serviceaccounts/generateaccesstoken）方法。

## iam.serviceAccounts.signBlob

## iam.serviceaccounts.signblob

The _iam.serviceAccounts.signBlob_ permission “allows signing of arbitrary payloads” in GCP. This means we can **create an unsigined JWT of the SA and then send it as a blob to get the JWT signed** by the SA we are targeting. For more information [**read this**](https://medium.com/google-cloud/using-serviceaccountactor-iam-role-for-account-impersonation-on-google-cloud-platform-a9e7118480ed).

_iam.serviceaccounts.signblob_权限“允许在GCP中签署任意有效载荷”。 这意味着我们可以**创建SA的无可厚非的JWT，然后将其作为斑点发送，以使我们针对的SA签名**。 有关更多信息[**阅读此**]（https://medium.com/google-cloud/ususe-serviceaccountactor-iam-role-for-account-account-mimpersonation-on-google-cloud-plat-plat-platform-a9e7118480ed）。

You can find a script to automate the [**creation, exploit and cleaning of a vuln environment here**](https://github.com/carlospolop/gcp\_privesc\_scripts/blob/main/tests/6-iam.serviceAccounts.signBlob.sh) and a python script to abuse this privilege [**here**](https://github.com/RhinoSecurityLabs/GCP-IAM-Privilege-Escalation/blob/master/ExploitScripts/iam.serviceAccounts.signBlob-accessToken.py) and [**here**](https://github.com/RhinoSecurityLabs/GCP-IAM-Privilege-Escalation/blob/master/ExploitScripts/iam.serviceAccounts.signBlob-gcsSignedUrl.py). For more information check the [**original research**](https://rhinosecuritylabs.com/gcp/privilege-escalation-google-cloud-platform-part-1/).

您可以在此处找到一个脚本来自动化[**创建，利用和清洁vuln环境**]（https://github.com/carloppolop/gcp \ _privesccccccccccccrive_scripts/blob/main/main/main/tests/6-6-iam 。 .signblob-accesstoken.py）和[** there **]（https://github.com/rhinosecuritylabs/gcp-iam-iam-iam-p--iam-privilege-escalation/blob/blob/master/master/exploitss/exploitss/iam.serviceaccienccounts.signblob-gcssegnedurl.py） 。 有关更多信息，请查看[**原始研究**]（https://rhinosecuritylabs.com/gcp/privilege-escalation-google-cloud-cloud-platform-part-part-part-1/）。

## iam.serviceAccounts.signJwt

## iam.serviceaccounts.signjwt

Similar to how the previous method worked by signing arbitrary payloads, this method works by signing well-formed JSON web tokens (JWTs). The difference with the previous method is that **instead of making google sign a blob containing a JWT, we use the signJWT method that already expects a JWT**. This makes it easier to use but you can only sign JWT instead of any bytes.

类似于以前的方法通过签名任意有效载荷的工作方式，该方法通过签名良好的JSON Web令牌（JWTS）来起作用。 与以前的方法的不同之处在于，**不是将Google签名为包含JWT的斑点，而是使用已经期望JWT **的SignJWT方法。 这使其更容易使用，但您只能签署JWT而不是任何字节。

You can find a script to automate the [**creation, exploit and cleaning of a vuln environment here**](https://github.com/carlospolop/gcp\_privesc\_scripts/blob/main/tests/7-iam.serviceAccounts.signJWT.sh) and a python script to abuse this privilege [**here**](https://github.com/RhinoSecurityLabs/GCP-IAM-Privilege-Escalation/blob/master/ExploitScripts/iam.serviceAccounts.signJWT.py). For more information check the [**original research**](https://rhinosecuritylabs.com/gcp/privilege-escalation-google-cloud-platform-part-1/).

您可以在此处找到一个脚本来自动化[**创建，利用和清洁vuln环境**]（https://github.com/carloppolop/gcp \ _privescccccccccccctscripts/blob/main/main/main/main/tests/7-iam 。 .signjwt.py）。 有关更多信息，请查看[**原始研究**]（https://rhinosecuritylabs.com/gcp/privilege-escalation-google-cloud-cloud-platform-part-part-part-1/）。

## iam.serviceAccounts.setIamPolicy <a href="#iam.serviceaccounts.setiampolicy" id="iam.serviceaccounts.setiampolicy"></a>

## iam.serviceaccounts.setiampolicy <a href="#iam.serviceaccounts.setiampolicy" id="iam.serviceaccounts.setiampolicy"> </a>

This permission allows to **add IAM policies to service accounts**. You can abuse it to **grant yourself** the permissions you need to impersonate the service account. In the following example we are granting ourselves the “roles/iam.serviceAccountTokenCreator” role over the interesting SA:

此权限允许将IAM策略添加到服务帐户**。 您可以滥用它来**授予自己**假冒服务帐户所需的权限。 在下面的示例中，我们赋予自己“角色/iam.serviceaccounttokencreator”的角色：有趣的SA：

```bash
gcloud iam service-accounts add-iam-policy-binding "${VICTIM_SA}@${PROJECT_ID}.iam.gserviceaccount.com" \
	--member="user:username@domain.com" \
	--role="roles/iam.serviceAccountTokenCreator"
```

You can find a script to automate the [**creation, exploit and cleaning of a vuln environment here**](https://github.com/carlospolop/gcp\_privesc\_scripts/blob/main/tests/d-iam.serviceAccounts.setIamPolicy.sh)**.**

您可以在此处找到一个脚本来自动化[**创建，利用和清洁vuln环境**]（https://github.com/carloppolop/gcp \ _privescccccccccccccrive_scripts/blob/main/main/main/main/tests/d-yam-d-iam .serviceaccounts.setiampolicy.sh）**。

## iam.serviceAccounts.actAs

## iam.serviceaccounts.actas

This means that as part of creating certain resources, you must “actAs” the Service Account for the call to complete successfully. For example, when starting a new Compute Engine instance with an attached Service Account, you need _iam.serviceAccounts.actAs_ on that Service Account. This is because without that permission, users could escalate permissions with fewer permissions to start with.

这意味着，作为创建某些资源的一部分，您必须“ ACTA”为呼叫完成服务帐户才能成功完成。 例如，当使用附加的服务帐户启动新的计算引擎实例时，您需要_iam.serviceaccounts.actas_在该服务帐户上。 这是因为未经该许可，用户可以从较少的权限开始时升级权限。

**There are multiple individual methods that use \_iam.serviceAccounts.actAs**\_**, so depending on your own permissions, you may only be able to exploit one (or more) of these methods below**. These methods are slightly different in that they **require multiple permissions to exploit, rather than a single permission** like all of the previous methods.

**有多种单独的方法使用\ _iam.serviceaccounts.actas ** \ _ **，因此，根据您自己的权限，您只能利用下面**的其中一种（或更多）。 这些方法略有不同，因为它们**需要多个利用的权限，而不是像所有先前方法一样的单一许可**。

## iam.serviceAccounts.getOpenIdToken

This permission can be used to generate an OpenID JWT. These are used to assert identity and do not necessarily carry any implicit authorization against a resource.

此权限可用于生成OpenID JWT。 这些用于主张身份，不一定要对资源进行任何隐性授权。

According to this [**interesting post**](https://medium.com/google-cloud/authenticating-using-google-openid-connect-tokens-e7675051213b), it's necessary to indicate the audience (service where you want to use the token to authenticate to) and you will receive a JWT signed by google indicating the service account and the audience of the JWT.

根据这个[**有趣的帖子**]（https://medium.com/google-cloud/authenticating-using-using-google-openid-connect-connect-tokens-e7675051213b） 要使用代币进行身份验证），您将收到Google签名的JWT，指示服务帐户和JWT的受众。

You can generate an OpenIDToken (if you have the access) with:

您可以使用：

```bash
# First activate the SA with iam.serviceAccounts.getOpenIdToken over the other SA
gcloud auth activate-service-account --key-file=/path/to/svc_account.json
# Then, generate token
gcloud auth print-identity-token "${ATTACK_SA}@${PROJECT_ID}.iam.gserviceaccount.com" --audiences=https://example.com
```

Then you can just use it to access the service with:

然后，您可以使用它来访问以下方式：

```bash
curl -v -H "Authorization: Bearer id_token" https://some-cloud-run-uc.a.run.app
```

Some services that support authentication via this kind of tokens are:

一些通过这种代币支持身份验证的服务是：

* [Google Cloud Run](https://cloud.google.com/run/)
* [Google Cloud Functions](https://cloud.google.com/functions/docs/)
* [Google Identity Aware Proxy](https://cloud.google.com/iap/docs/authentication-howto)

* [Google Identity Aware Proxy]（https://cloud.google.com/iap/docs/authentication-howto）
* [Google Cloud Endpoints](https://cloud.google.com/endpoints/docs/openapi/authenticating-users-google-id) (if using Google OIDC)

* [Google Cloud Endpoints]（https://cloud.google.com/endpoints/docs/openapi/authenticating-users-google-id）（如果使用Google OIDC）

You can find an example on how to create and OpenID token behalf a service account [**here**](https://github.com/carlospolop-forks/GCP-IAM-Privilege-Escalation/blob/master/ExploitScripts/iam.serviceAccounts.getOpenIdToken.py).

您可以找到一个有关如何创建和OpenID代币代表服务帐户的示例[**在这里**]（https://github.com/carloppolop-forks/gcp-iam-privilege-escalation/blob/master/master/exploitscripts/ iam.serviceaccounts.getopenidtoken.py）。

# resourcemanager

## resourcemanager.organizations.setIamPolicy

## resourcemanager.organizations.setiampolicy

Like in the exploitation of [**iam.serviceAccounts.setIamPolicy**](gcp-privesc-to-other-principals.md#iam.serviceaccounts.setiampolicy), this permission allows you to **modify** your **permissions** against **any resource** at **organization** level. So, you can follow the same exploitation example.

就像在剥削[** iam.serviceaccounts.setiampolicy **]（gcp-privesc-to-other-principals.md＃iam.serviceaccounts.setiampolicy）一样 **反对**任何资源**在**组织**级别。 因此，您可以遵循相同的剥削示例。

## resourcemanager.folders.setIamPolicy

## resourcemanager.folders.setiampolicy

Like in the exploitation of [**iam.serviceAccounts.setIamPolicy**](gcp-privesc-to-other-principals.md#iam.serviceaccounts.setiampolicy), this permission allows you to **modify** your **permissions** against **any resource** at **folder** level. So, you can follow the same exploitation example.

就像在剥削[** iam.serviceaccounts.setiampolicy **]（gcp-privesc-to-other-principals.md＃iam.serviceaccounts.setiampolicy）一样 **反对**任何资源**在**文件夹**级别。 因此，您可以遵循相同的剥削示例。

## resourcemanager.projects.setIamPolicy

## resourcemanager.projects.setiampolicy

Like in the exploitation of [**iam.serviceAccounts.setIamPolicy**](gcp-privesc-to-other-principals.md#iam.serviceaccounts.setiampolicy), this permission allows you to **modify** your **permissions** against **any resource** at **project** level. So, you can follow the same exploitation example.

就像在剥削[** iam.serviceaccounts.setiampolicy **]（gcp-privesc-to-other-principals.md＃iam.serviceaccounts.setiampolicy）一样 **反对**任何资源**在**项目**级别。 因此，您可以遵循相同的剥削示例。

# deploymentmanager

## deploymentmanager.deployments.create

This single permission lets you **launch new deployments** of resources into GCP with arbitrary service accounts. You could for example launch a compute instance with a SA to escalate to it.

此单一的许可使您可以**通过任意服务帐户启动新的资源部署**。 例如，您可以启动使用SA的计算实例来升级。

You could actually **launch any resource** listed in `gcloud deployment-manager types list`

您实际上可以**启动任何资源**列出的任何资源**

In the [**original research**](https://rhinosecuritylabs.com/gcp/privilege-escalation-google-cloud-platform-part-1/) following[ **script**](https://github.com/RhinoSecurityLabs/GCP-IAM-Privilege-Escalation/blob/master/ExploitScripts/deploymentmanager.deployments.create.py) is used to deploy a compute instance, however that script won't work. Check a script to automate the [**creation, exploit and cleaning of a vuln environment here**](https://github.com/carlospolop/gcp\_privesc\_scripts/blob/main/tests/1-deploymentmanager.deployments.create.sh)**.**

在[**原始研究**]（https://rhinosecuritylabs.com/gcp/privilege-escalation-google-google-cloud-platform-part-part-1/）下 .com/rhinosecurityLabs/gcp-am-am-privilege-eScalation/blob/master/exploitscripts/devermentmanager.deployments.create.py）用于部署计算实例，但是该脚本不起作用。 检查一个脚本以自动化[**创建，利用和清洁vuln环境**]（https://github.com/carlospolop/gcp \ _privesccccccccccrivesccccrcts/blob/main/main/main/main/tests/1-deploymentmanager.deployments.deployments.deployments.deployments .greate.sh）**。**

## deploymentmanager.deployments.**update**

This is like the previous abuse but instead of creating a new deployment, you modifies one already existing (so be careful)

这就像以前的虐待一样

Check a script to automate the [**creation, exploit and cleaning of a vuln environment here**](https://github.com/carlospolop/gcp\_privesc\_scripts/blob/main/tests/e-deploymentmanager.deployments.update.sh)**.**

检查一个脚本以自动化[**创建，利用和清洁vuln环境**]（https://github.com/carloppolop/gcp \ _privesccccccccccrivescccrcts/blob/main/main/main/main/tests/e-deploymentmanager.deployments.deployments.deployments.deployments .update.sh）**。**

## deploymentmanager.deployments.**setIamPolicy**

This is like the previous abuse but instead of directly creating a new deployment, you first give you that access and then abuses the permission as explained in the previos _deploymentmanager.deployments.create_ section.

这就像以前的滥用一样，但您没有直接创建新的部署，而是首先给您访问权限，然后滥用限制，如previos _deploymentManager.deployments.create_ exchsect中所述。

# cloudbuild

＃CloudBuild

## cloudbuild.builds.create

## Cloudbuild.builds.create

With this permission you can **submit a cloud build**. The cloudbuild machine will have in it’s filesystem by **default a token of the powerful cloudbuild Service Account**: `<PROJECT_NUMBER>@cloudbuild.gserviceaccount.com` . However, you can **indicate any service account inside the project** in the cloudbuild configuration.\

通过此权限，您可以**提交云版本**。 CloudBuild计算机将在其文件系统中使用**默认功能强大的CloudBuild服务帐户的令牌**：`<project_number>@cloudbuild.gserviceaccount.com`。 但是，您可以**指示项目中的任何服务帐户**在CloudBuild配置中。\ \
Therefore, you can just make the machine exfiltrate to your server the token or **get a reverse shell inside of it and get yourself the token** (the file containing the token might change).

因此，您只需将机器渗透到服务器上的令牌或**将其内部的反向外壳放入其中，然后将您自己换成令牌**（包含令牌的文件可能会更改）。

You can find the original exploit script [**here on GitHub**](https://github.com/RhinoSecurityLabs/GCP-IAM-Privilege-Escalation/blob/master/ExploitScripts/cloudbuild.builds.create.py) (but the location it's taking the token from didn't work for me). Therefore, check a script to automate the [**creation, exploit and cleaning of a vuln environment here**](https://github.com/carlospolop/gcp\_privesc\_scripts/blob/main/tests/f-cloudbuild.builds.create.sh) and a python script to get a reverse shell inside of the cloudbuild machine and [**steal it here**](https://github.com/carlospolop/gcp\_privesc\_scripts/blob/main/tests/f-cloudbuild.builds.create.py) (in the code you can find how to specify other service accounts)**.**

您可以在github **]上找到原始的漏洞脚本[**]（https://github.com/rhinosecuritylabs/gcp-iam-privilege-escalation/blob/master/master/exploits/exploitscripts/cloudbuild.builds.creats.creats.create.py.py.py.py）（）（） 但是，它从代币中获得的位置对我不起作用）。 因此，请检查一个脚本以自动化[**创建，利用和清洁vuln环境**]（https://github.com/carloppolop/gcp \ _privescccccccccccrive_scripts/blob/main/main/main/main/tests/f-cloudbuildbuildbuildbuildbuildbuildbuildbuildbuildbuildbuildbuildbuildbuildbuildbuildbuildbuildbuildbuildbuildbuildbuildbuildbuildbuild 。 main/tests/f-cloudbuild.builds.create.py）（在代码中，您可以找到如何指定其他服务帐户）**。**。

For a more in-depth explanation visit [https://rhinosecuritylabs.com/gcp/iam-privilege-escalation-gcp-cloudbuild/](https://rhinosecuritylabs.com/gcp/iam-privilege-escalation-gcp-cloudbuild/)

有关更深入的解释，请访问[https://rhinosecuritylabs.com/gcp/aiam-privilege-escalation-gcp-cloudbuild/]（ /）

## cloudbuild.builds.update

## Cloudbuild.builds.update

**Potentially** with this permission you will be able to **update a cloud build and just steal the service account token** like it was performed with the previous permission (but unfortunately at the time of this writing I couldn't find any way to call that API).

**有可能**在此许可下，您将可以**更新云版本，然后窃取服务帐户令牌**，就像以前的许可一样（但不幸的是，在撰写本文时，我都找不到 呼叫该API的任何方式）。

# compute

## compute.projects.setCommonInstanceMetadata

With that permission you can **modify** the **metadata** information of an **instance** and change the **authorized keys of a user**, or **create** a **new user with sudo** permissions. Therefore, you will be able to exec via SSH into any VM instance and steal the GCP Service Account the Instance is running with.\

有了该许可，您可以**修改** **元数据** **实例**的信息，然后更改用户**的授权键，或**创建** ** a ** a ** a ** a ** a ** a ** a ** sudo的新用户 **权限。 因此，您将能够通过SSH执行任何VM实例并窃取实例正在运行的GCP服务帐户。\ \
Limitations:

* Note that GCP Service Accounts running in VM instances by default have a **very limited scope**

*请注意，默认情况下在VM实例中运行的GCP服务帐户具有**非常有限的范围**
* You will need to be **able to contact the SSH** server to login

*您需要**可以联系SSH **服务器以登录

For more information about how to exploit this permission check:

有关如何利用此权限检查的更多信息：

{% content-ref url="../gcp-local-privilege-escalation-ssh-pivoting.md" %}

{％content-ref url =“ ../ gcp-local-privilege-escalation-ssh-pivoting.md”％}
[gcp-local-privilege-escalation-ssh-pivoting.md](../gcp-local-privilege-escalation-ssh-pivoting.md)

[gcp-local-privilege-scalation-ssh-pivoting.md]（../ GCP-Local-Privilege-eScalation-ssh-pivoting.md）
{% endcontent-ref %}

## compute.instances.setMetadata

This permission gives the **same privileges as the previous permission** but over a specific instances instead to a whole project. The **same exploits and limitations applies**.

此权限赋予**与以前的权限**相同的特权**，但在特定实例中而不是整个项目。 **相同的利用和限制适用**。

## compute.instances.setIamPolicy

## compute.instances.setiampolicy

This kind of permission will allow you to **grant yourself a role with the previous permissions** and escalate privileges abusing them.

这种许可将使您可以**赋予自己以前的权限**的角色，并升级特权滥用它们。

## **compute.instances.osLogin**

## **compute.instances.osLogin**

If OSLogin is enabled in the instance, with this permission you can just run **`gcloud compute ssh [INSTANCE]`** and connect to the instance. You won't have root privs inside the instance.

如果在此实例中启用了Oslogin，则可以在此权限下运行**`gcloud Compute ssh [instance]`**并连接到实例。 实例中您不会有root priv。

## **compute.instances.osAdminLogin**

If OSLogin is enabled in the instance, with this permission you can just run **`gcloud compute ssh [INSTANCE]`** and connect to the instance. You will have root privs inside the instance.

如果在此实例中启用了Oslogin，则可以在此权限下运行**`gcloud Compute ssh [instance]`**并连接到实例。 您将在实例内有root priv。

# container

## container.clusters.get

This permission allows to **gather credentials for the Kubernetes cluster** using something like:

此权限允许使用类似的东西来**收集kubernetes群集** **的凭据。

```bash
gcloud container clusters get-credentials <cluster_name> --zone <zone>
```

Without extra permissions, the credentials are pretty basic as you can **just list some resource**, but hey are useful to find miss-configurations in the environment.

如果没有额外的权限，凭据是非常基本的，因为您可以**列出一些资源**，但是嘿，对于在环境中找到错觉很有用。

{% hint style="info" %}

{％提示样式=“ info”％}
Note that **kubernetes clusters might be configured to be private**, that will disallow that access to the Kube-API server from the Internet.

请注意，** kubernetes簇可能被配置为私有**，这将不允许从Internet访问Kube-API服务器。
{% endhint %}

## container.clusters.getCredentials

## container.clusters.getcredentials

Apparently this permission might be useful to gather auth credentials (basic auth method isn't supported anymore by GKE if you use the latest GKE versions).

显然，此权限可能对收集身份证书很有用（如果使用最新的GKE版本，GKE不再支持基本的auth方法）。

## container.roles.escalate/container.clusterRoles.escalate

**Kubernetes** by default **prevents** principals from being able to **create** or **update** **Roles** and **ClusterRoles** with **more permissions** that the ones the principal has. However, a **GCP** principal with that permissions will be **able to create/update Roles/ClusterRoles with more permissions** that ones he held, effectively bypassing the Kubernetes protection against this behaviour.

** kubernetes **默认情况下**防止**校长能够**创建**或**更新** **角色**和** clusterRoles ** with **有更多权限** 校长有。 但是，具有该权限的A ** gcp **校长将**能够使用他所拥有的权限创建/更新角色/聚类机器人**，从而有效地绕开了Kubernetes保护这种行为的保护。

**container.roles.create** and/or **container.roles.update** OR **container.clusterRoles.create** and/or **container.clusterRoles.update** respectively are also **necessary** to perform those privilege escalation actions.\

** Container.Roles.Create **和/或** Container.Roles.update **或** Container.ClusterRoles.Create **和/或** Container.ClusterRoles.update **分别**必要** *执行这些特权升级动作。\


## container.roles.bind/container.clusterRoles.bind

## container.roles.bind/container.clusterroles.bind

**Kubernetes** by default **prevents** principals from being able to **create** or **update** **RoleBindings** and **ClusterRoleBindings** to give **more permissions** that the ones the principal has. However, a **GCP** principal with that permissions will be **able to create/update RolesBindings/ClusterRolesBindings with more permissions** that ones he has, effectively bypassing the Kubernetes protection against this behaviour.

** kubernetes **默认情况下**防止**校长能够**创建**或** update ** prolebindings **和** clusterrolebindings **授予**更多权限** 校长有。 但是，具有该权限的A ** GCP **校长将**能够创建/更新具有更多权限**的功能框架/clusterRolesBindings **，实际上，有效地绕过了Kubernetes保护这种行为的保护。

**container.roleBindings.create** and/or **container.roleBindings.update** OR **container.clusterRoleBindings.create** and/or **container.clusterRoleBindings.update** respectively  are also **necessary** to perform those privilege escalation actions.

** container.rolebindings.create **和/或** container.rolebindings.update **或** container.clusterrolebindings.create.greate **和/或** container.clusterRolebindings.update.update **也是必要的** *执行这些特权升级动作。

## container.cronJobs.create, container.cronJobs.update container.daemonSets.create, container.daemonSets.update container.deployments.create, container.deployments.update container.jobs.create, container.jobs.update container.pods.create, container.pods.update container.replicaSets.create, container.replicaSets.update container.replicationControllers.create, container.replicationControllers.update container.scheduledJobs.create, container.scheduledJobs.update container.statefulSets.create, container.statefulSets.update

更新

All these permissions are going to allow you to **create or update a resource** where you can **define** a **pod**. Defining a pod you can **specify the SA** that is going to be **attached** and the **image** that is going to be **run**, therefore you can run an image that is going to **exfiltrate the token of the SA to your server** allowing you to escalate to any service account.\

所有这些权限将允许您**创建或更新资源**，您可以在其中** a ** pod **。 定义一个吊舱，您可以**指定将要**的** **和**映像** **的** **，因此您可以运行将要运行的图像 **将SA的令牌删除到您的服务器**，允许您升级到任何服务帐户。\ \
For more information check:

有关更多信息检查：

{% content-ref url="../../pentesting-kubernetes/abusing-roles-clusterroles-in-kubernetes/" %}

{％content-ref url =“ ../ ../ pentesting-kubernetes/abusing-roles-clusterroles-in-kubernetes/“％}
[abusing-roles-clusterroles-in-kubernetes](../../pentesting-kubernetes/abusing-roles-clusterroles-in-kubernetes/)

[滥用强 - 群体中的kubernetes]（../../ pentesting-kubernetes/abusing-roles-clusterroles-in-kubernetes/）
{% endcontent-ref %}

As we are in a GCP environment, you will also be able to **get the nodepool GCP SA** from the **metadata** service and **escalate privileges in GC**P (by default the compute SA is used).

当我们处于GCP环境中时，您还可以从**元数据**服务中获得NodePool GCP SA **，并且**升级的gc ** p特权（默认情况下，使用计算SA） 。

## container.secrets.get, container.secrets.list

As [**explained in this page**](../../pentesting-kubernetes/abusing-roles-clusterroles-in-kubernetes/#listing-secrets), with these permissions you can **read** the **tokens** of all the **SAs of kubernetes**, so you can escalate to them.

如[**在此页面**]（../../ pentesting-kubernetes/abusing-roles-clusterroles-in-kubernetes/＃listing-secrets）的[../ ../ ../ ../ ../ ../ *令牌** kubernetes **的所有** sas，因此您可以升级为它们。

## container.pods.exec

With this permission you will be able to **exec into pods**, which gives you **access** to all the **Kubernetes SAs running in pods** to escalate privileges within K8s, but also you will be able to **steal** the **GCP Service Account** of the **NodePool**, **escalating privileges in GCP**.

经过此权限，您将可以** exec of Pods **，这使您**访问**在Pods中运行的所有** Kubernetes SAS **以升级K8S内的特权，但您也可以** *窃取** ** nodepool **的** GCP服务帐户**，**在GCP **中升级特权。

## container.pods.portForward

## container.pods.portforward

As [**explained in this page**](../../pentesting-kubernetes/abusing-roles-clusterroles-in-kubernetes/#port-forward), with these permissions you can **access local services** running in **pods** that might allow you to **escalate privileges in Kubernetes** (and in **GCP** if somehow you manage to talk to the metadata service)**.**

如[**在此页面**]（../../ pentesting-kubernetes/abusing-roles-clusterroles-in-kubernetes/＃port-forward）中所述，借助这些权限，您可以**访问本地服务** 在** pods **中运行，可以让您**在kubernetes **中升级特权（并且在** gcp **中，如果您设法与元数据服务交谈）** **。

## container.serviceAccounts.createToken

## container.serviceaccounts.createToken

Because of the **name** of the **permission**, it **looks like that it will allow you to generate tokens of the K8s Service Accounts**, so you will be able to **privesc to any SA** inside Kubernetes. However, I couldn't find any API endpoint to use it, so let me know if you find it.

由于**权限**的**名称**，因此**看起来可以使您生成K8S服务帐户的令牌**，因此您可以** Privesc到任何SA** *在Kubernetes内部。 但是，我找不到使用它的任何API端点，因此如果您找到它，请告诉我。

## container.mutatingWebhookConfigurations.create, container.mutatingWebhookConfigurations.update

## container.mutatingwebhookconfiguration.create，container.mutatingwebhookconfigurations.update

These permissions might allow you to escalate privileges in Kubernetes, but more probably, you could abuse them to **persist in the cluster**.\

这些权限可能使您可以在Kubernetes中升级特权，但更可能，您可能会滥用它们以**坚持在集群中**。
For more information [**follow this link**](../../pentesting-kubernetes/abusing-roles-clusterroles-in-kubernetes/#malicious-admission-controller).

有关更多信息[** **请访问此链接**]（../../ pentesting-kubernetes/abusing-roles-clusterroles-in-kubernetes/＃Malicious-Indermiss-controller）。

# storage

## storage.hmacKeys.create

## storage.hmackeys.create

There is a feature of Cloud Storage, “interoperability”, that provides a way for Cloud Storage to interact with storage offerings from other cloud providers, like AWS S3. As part of that, there are HMAC keys that can be created for both Service Accounts and regular users. We can **escalate Cloud Storage permissions by creating an HMAC key for a higher-privileged Service Account**.

云存储的功能是“互操作性”，它为云存储提供了一种与其他云提供商的存储产品交互的方式，例如AWS S3。 作为其中的一部分，可以为服务帐户和常规用户创建HMAC键。 我们可以通过为更高的服务帐户创建HMAC密钥来升级云存储权限**。

HMAC keys belonging to your user cannot be accessed through the API and must be accessed through the web console, but what’s nice is that both the access key and secret key are available at any point. This means we could take an existing pair and store them for backup access to the account. HMAC keys belonging to Service Accounts **can** be accessed through the API, but after creation, you are not able to see the access key and secret again.

无法通过API访问属于您用户的HMAC键，并且必须通过Web控制台访问，但是很好的是，访问密钥和秘密键在任何时候都可用。 这意味着我们可以将现有对存储并存储它们以备份对帐户的访问。 可以通过API访问属于服务帐户的HMAC密钥**，但是创建后，您将无法再次看到访问密钥和秘密。

![](https://rhinosecuritylabs.com/wp-content/uploads/2020/04/image2-1.png)

The exploit script for this method can be found [here](https://github.com/RhinoSecurityLabs/GCP-IAM-Privilege-Escalation/blob/master/ExploitScripts/storage.hmacKeys.create.py).

可以找到此方法的利用脚本[此处]（https://github.com/rhinosecuritylabs/gcp-iam-privilege-escalation/blob/master/master/exploitscripts/storage.hmackeys.create.py）。

## storage.objects.get

This permission allows you to **download files stored inside Gcp Storage**. This will potentially allow you to escalate privileges because in some occasions **sensitive information is saved there**. Moreover, some Gcp services stores their information in buckets:

此许可使您可以**下载存储在GCP存储中的文件**。 这有可能使您能够升级特权，因为在某些情况下，**敏感信息被保存在那里**。 此外，一些GCP服务将其信息存储在存储桶中：

* **GCP Composer**: When you create a Composer Environment the **code of all the DAGs** will be saved inside a **bucket**. These tasks might contain interesting information inside of their code.

*** GCP COMPOSER **：创建作曲家环境时，所有DAGS的代码**将保存在** buccet **内。 这些任务可能包含其代码中的有趣信息。
* **GCR (Container Registry)**: The **image** of the containers are stored inside **buckets**, which means that if you can read the buckets you will be able to download the images and **search for leaks and/or source code**.

*** gcr（容器注册表）**：容器的**图像**被存储在**桶中**，这意味着，如果您可以阅读存储桶，则可以下载图像和**搜索 用于泄漏和/或源代码**。

## storage.objects.create, storage.objects.delete

## Storage.Objects.create，storege.objects.delete

In order to **create a new object** inside a bucket you need `storage.objects.create` and, according to [the docs](https://cloud.google.com/storage/docs/access-control/iam-permissions#object\_permissions), you need also `storage.objects.delete` to **modify** an existent object.

为了**创建一个新对象**在一个存储桶内，您需要`raseque.objects.create`''，并且根据[docs]（https://cloud.google.com/storage/storage/docs/access/access-cons/access-control/- iam-permissions＃object \ _ permissions），您还需要`soalite.objects.delete` to **修改**存在的对象。

A very **common exploitation** of buckets where you can write in cloud is in case the **bucket is saving web server files**, you might be able to **store new code** that will be used by the web application.

可以在云中写入的水桶的一个非常**的常见剥削**，以防**保存Web服务器文件**，您可以**存储新代码**，该代码将被Web使用 应用。

Moreover, several GCP services also **store code inside buckets** that later is **executed**:

此外，几种GCP服务也**存储代码在存储桶中**，后来被执行**：

* **GCP Composer**: The **DAG code** is **stored in GCP Storage**. This **code** is later **executed** inside the **K8s environment** used by composer, and has also **access to a GCP SA**. Therefore, modifying this code you might be able to get inside the composer k8s env and steal the token of the GCP SA used.

*** GCP Composer **：** DAG代码**已存储在GCP存储中**。 此**代码**稍后被执行** **在** K8S环境中**作曲家使用，并且还可以访问GCP SA **。 因此，修改此代码，您可能可以进入Composer K8S Env中，并窃取所用GCP SA的令牌。
* **GCR (Container Registry)**: The **container images are stored inside buckets**. So if you have write access over them, you could **modify the images** and execute your own code whenever that container is used.

*** gcr（容器注册表）**：**容器图像存储在存储桶中**。 因此，如果您对它们的写入访问权限，则可以**修改图像**并在使用该容器时执行自己的代码。
  * The bucket used by GCR will have an URL similar to `gs://<eu/usa/asia/nothing>.artifacts.<project>.appspot.com` (The top level subdomains are specified [here](https://cloud.google.com/container-registry/docs/pushing-and-pulling)).

* GCR使用的存储桶的URL将与`gs：// <eu/usic/asia/nothing> .artifacts。 //cloud.google.com/container-registry/docs/pushing-and-pulling））。

## storage.objects.setIamPolicy

## Storage.Objects.setiampolicy

You can give you permission to **abuse any of the previous scenarios of this section**.

您可以允许您**滥用本节的任何以前情况。

# storage.objects Write permission

＃storage.Objects写许可

If you can modify or add objects in buckets you might be able to escalate your privileges to other resources that are using the bucket to store code that they execute.

如果您可以在存储桶中修改或添加对象，则可以将您的特权升级到使用使用该存储桶来存储其执行代码的其他资源。

## Composer

##作曲家

**Composer** is **Apache Airflow** managed inside GCP. It has several interesting features:

**作曲家** IS ** Apache Airflow **在GCP内部进行了管理。 它有几个有趣的功能：

* It runs inside a **GKE cluster**, so the **SA the cluster uses is accesible** by the code running inside Composer

*它在一个** gke群集**内运行，因此群集使用的** SA可通过在作曲家内部运行的代码来获得**
* It stores the **code in a bucket**, therefore, **anyone with write access over that bucket** is going to be able change/add a DGA code (the code Apache Airflow will execute)\

*它将**代码存储在存储桶中**，因此，**在该存储桶上具有写入访问的人**将能够更改/添加DGA代码（代码Apache Airflow将执行）\
  Then, if you have **write access over the bucket Composer is using** to store the code you can **privesc to the SA running in the GKE cluster**.

然后，如果您有**在存储桶中写入访问权限，则使用**存储代码，您可以** privesc到在GKE群集中运行的sa **。

# References

* [https://rhinosecuritylabs.com/gcp/privilege-escalation-google-cloud-platform-part-1/](https://rhinosecuritylabs.com/gcp/privilege-escalation-google-cloud-platform-part-1/)
* [https://rhinosecuritylabs.com/cloud-security/privilege-escalation-google-cloud-platform-part-2/](https://rhinosecuritylabs.com/cloud-security/privilege-escalation-google-cloud-platform-part-2/#gcp-privesc-scanner)


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


