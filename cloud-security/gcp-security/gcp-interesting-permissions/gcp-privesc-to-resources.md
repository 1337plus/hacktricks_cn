

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


# cloudfunctions

## cloudfunctions.functions.create,iam.serviceAccounts.actAs

## cloudfunctions.functions.create，iam.serviceaccounts.actas

For this method, we will be **creating a new Cloud Function with an associated Service Account** that we want to gain access to. Because Cloud Function invocations have **access to the metadata** API, we can request a token directly from it, just like on a Compute Engine instance.

对于此方法，我们将**创建一个新的云功能，并使用关联的服务帐户**我们想要访问。 由于云功能调用具有**访问元数据** API，因此我们可以直接从其索取令牌，就像在计算引擎实例上一样。

The **required permissions** for this method are as follows:

**所需的权限**对于此方法如下：

* _cloudfunctions.functions.call_ **OR** _cloudfunctions.functions.setIamPolicy_

*cloudfunctions.functions.call **或** cloudfunctions.functions.setiampolicy
* _cloudfunctions.functions.create_

* cloudfunctions.functions.create
* _cloudfunctions.functions.sourceCodeSet_
* _iam.serviceAccounts.actAs_

* _iam.serviceaccounts.actas_

The script for this method uses a premade Cloud Function that is included on GitHub, meaning you will need to upload the associated .zip file and make it public on Cloud Storage (see the exploit script for more information). Once the function is created and uploaded, you can either invoke the function directly or modify the IAM policy to allow you to invoke the function. The response will include the access token belonging to the Service Account assigned to that Cloud Function.

此方法的脚本使用GitHub上包含的预制云功能，这意味着您需要上传关联的.zip文件并将其公开在云存储上（有关更多信息，请参见Exploit脚本）。 创建和上传功能后，您可以直接调用该函数，也可以修改IAM策略以允许您调用该功能。 响应将包括分配给该云功能的服务帐户的访问令牌。

![](https://rhinosecuritylabs.com/wp-content/uploads/2020/04/image12-750x618.png)

The script creates the function and waits for it to deploy, then it runs it and gets returned the access token.

脚本创建功能并等待其部署，然后运行它并返回访问令牌。

The exploit scripts for this method can be found [here](https://github.com/RhinoSecurityLabs/GCP-IAM-Privilege-Escalation/blob/master/ExploitScripts/cloudfunctions.functions.create-call.py) and [here](https://github.com/RhinoSecurityLabs/GCP-IAM-Privilege-Escalation/blob/master/ExploitScripts/cloudfunctions.functions.create-setIamPolicy.py) and the prebuilt .zip file can be found [here](https://github.com/RhinoSecurityLabs/GCP-IAM-Privilege-Escalation/tree/master/ExploitScripts/CloudFunctions).

可以找到此方法的利用脚本[此处]（https://github.com/rhinosecuritylabs/gcp-cp-iam-privilege-escalation/blob/blob/master/master/exploitscripts/cloudfunctions.functions.functions.create-call.py.py） ]（https://github.com/rhinosecuritylabs/gcp-iam-privilege-escalation/blob/master/master/exploitscripts/cloudfunctions.functions.create-setiampolicy.py.py.py.py）和prebuilt .zip文件可以找到[resight.https] ：//github.com/rhinosecuritylabs/gcp-iam-privilege-escalation/tree/master/master/exploitscripts/cloudfunctions）。

## cloudfunctions.functions.update,iam.serviceAccounts.actAs

## cloudfunctions.functions.update，iam.serviceaccounts.actas

Similar to _cloudfunctions.functions.create_, this method **updates (overwrites) an existing function instead of creating a new one**. The API used to update the function also allows you to **swap the Service Account if you have another one you want to get the token for**. The script will update the target function with the malicious code, then wait for it to deploy, then finally invoke it to be returned the Service Account access token.

类似于_cloudfunctions.functions.create_，此方法**更新（覆盖）现有函数，而不是创建一个新功能**。 用于更新该函数的API还允许您**交换服务帐户，如果您有另一个要获得**的令牌。 脚本将使用恶意代码更新目标函数，然后等待其部署，然后最终调用它以返回服务帐户访问令牌。

The following **permissions are required** for this method:

对于此方法，需要以下**权限**：

* _cloudfunctions.functions.sourceCodeSet_
* _cloudfunctions.functions.update_
* _iam.serviceAccounts.actAs_

* _iam.serviceaccounts.actas_

The exploit script for this method can be found [here](https://github.com/RhinoSecurityLabs/GCP-IAM-Privilege-Escalation/blob/master/ExploitScripts/cloudfunctions.functions.update.py).

可以找到此方法的利用脚本[此处]（https://github.com/rhinosecuritylabs/gcp-iam-privilege-escalation/blob/master/master/exploitscripts/cloudfunctions.functions.update.update.py）。

# compute

## compute.instances.create,iam.serviceAccounts.actAs

## compute.instances.create，iam.serviceaccounts.actas

This method **creates a new Compute Engine instance with a specified Service Account**, then **sends the token** belonging to that Service Account to an **external server.**

此方法**使用指定的服务帐户创建一个新的计算引擎实例**，然后**将属于该服务帐户的令牌**发送给**外部服务器。**

The following **permissions are required** for this method:

对于此方法，需要以下**权限**：

* _compute.disks.create_
* _compute.instances.create_
* _compute.instances.setMetadata_
* _compute.instances.setServiceAccount_

* _compute.instances.setserviceaccount_
* _compute.subnetworks.use_

* COMPUTE.SUBNETWORKS.USE
* _compute.subnetworks.useExternalIp_

* _compute.subnetworks.useexternalip_
* _iam.serviceAccounts.actAs_

* _iam.serviceaccounts.actas_

![](https://rhinosecuritylabs.com/wp-content/uploads/2020/04/image9-750x594.png)

The exploit script for this method can be found [here](https://github.com/RhinoSecurityLabs/GCP-IAM-Privilege-Escalation/blob/master/ExploitScripts/compute.instances.create.py).

可以找到此方法的利用脚本[此处]（https://github.com/rhinosecuritylabs/gcp-iam-privilege-escalation/blob/master/master/exploitscripts/compute.instances.create.py）。

# run

## run.services.create,iam.serviceAccounts.actAs

## run.services.create，iam.serviceaccounts.actass

Similar to the _cloudfunctions.functions.create_ method, this method creates a **new Cloud Run Service** that, when invoked, **returns the Service Account’s** access token by accessing the metadata API of the server it is running on. A Cloud Run service will be deployed and a request can be performed to it to get the token.

类似于_cloudfunctions.functions.create_方法，此方法创建了一个**新的云运行服务**，当调用时，**通过访问它运行的服务器的元数据API，返回服务帐户的**访问令牌。 将部署云运行服务，并可以向其执行请求以获取令牌。

The following **permissions are required** for this method:

对于此方法，需要以下**权限**：

* _run.services.create_
* _iam.serviceaccounts.actAs_

* _iam.serviceaccounts.actas_
* _run.services.setIamPolicy_ **OR** _run.routes.invoke_

*_run.services.setiampolicy_ **或** _run.routes.invoke_

![](https://rhinosecuritylabs.com/wp-content/uploads/2020/04/image8-1000x503.png)

This method uses an included Docker image that must be built and hosted to exploit correctly. The image is designed to tell Cloud Run to respond with the Service Account’s access token when an HTTP request is made.

此方法使用随附的Docker映像，必须构建和托管才能正确利用。 该图像旨在告诉云运行，以便在提出HTTP请求时使用服务帐户的访问令牌响应。

The exploit script for this method can be found [here](https://github.com/RhinoSecurityLabs/GCP-IAM-Privilege-Escalation/blob/master/ExploitScripts/run.services.create.py) and the Docker image can be found [here](https://github.com/RhinoSecurityLabs/GCP-IAM-Privilege-Escalation/tree/master/ExploitScripts/CloudRunDockerImage).

可以找到此方法的利用脚本[此处]（https://github.com/rhinosecuritylabs/gcp-iam-privilege-escalation/blob/master/exploitscripts/run.services.services.create.py）和Docker Image com 可以找到[此处]（https://github.com/rhinosecuritylabs/gcp-iam-privilege-escalation/tree/master/master/exploitscripts/cloudrundockerimage）。

# Cloudscheduler

## cloudscheduler.jobs.create,iam.serviceAccounts.actAs

## cloudscheduler.jobs.create，iam.serviceaccounts.actass

Cloud Scheduler allows you to set up cron jobs targeting arbitrary HTTP endpoints. **If that endpoint is a \*.googleapis.com endpoint**, then you can also tell Scheduler that you want it to authenticate the request **as a specific Service Account**, which is exactly what we want.

云调度程序允许您设置针对任意HTTP端点的CRON作业。 **如果该端点是一个\*。googleapis.com endpoint **，那么您还可以告诉调度程序，您希望它将请求**作为特定服务帐户**进行身份验证，这正是我们想要的。

Because we control all aspects of the HTTP request being made from Cloud Scheduler, we can set it up to hit another Google API endpoint. For example, if we wanted to create a new job that will use a specific Service Account to create a new Storage bucket on our behalf, we could run the following command:

因为我们控制了由Cloud Scheduler制定的HTTP请求的所有方面，所以我们可以将其设置为击中另一个Google API端点。 例如，如果我们想创建一个新作业，该作业将使用特定的服务帐户代表我们创建一个新的存储存储桶，则可以运行以下命令：

```
gcloud scheduler jobs create http test –schedule=’* * * * *’ –uri=’https://storage.googleapis.com/storage/v1/b?project=<PROJECT-ID>’ –message-body “{‘name’:’new-bucket-name’}” –oauth-service-account-email 111111111111-compute@developer.gserviceaccount.com –headers Content-Type=application/json
```

This command would schedule an HTTP POST request for every minute that authenticates as _111111111111-compute@developer.gserviceaccount.com_. The request will hit the Cloud Storage API endpoint and will create a new bucket with the name “new-bucket-name”.

此命令将安排每分钟的HTTP POST请求，以_111111111111111111111111111111111111111111111111111MENTINGER.GSERVICICEACCONT.COM__。 该请求将击中云存储API端点，并将创建一个名称为“ new Bucket-name”的新存储桶。

The following permissions are required for this method:

此方法需要以下权限：

* _cloudscheduler.jobs.create_

* _cloudscheduler.jobs.create_
* _cloudscheduler.locations.list_

* _cloudscheduler.locations.list_
* _iam.serviceAccounts.actAs_

* _iam.serviceaccounts.actas_

To escalate our privileges with this method, we just need to **craft the HTTP request of the API we want to hit as the Service Account we pass in**. Instead of a script, you can just use the gcloud command above.

为了通过这种方法升级我们的特权，我们只需要**制作我们想要在**的服务帐户时要达到的API的HTTP请求。 您可以只使用上面的gcloud命令，而不是脚本。

A similar method may be possible with Cloud Tasks, but we were not able to do it in our testing.

云任务可能可以使用类似的方法，但是我们在测试中无法做到这一点。

# orgpolicy

## orgpolicy.policy.set

This method does **not necessarily grant you more IAM permissions**, but it may **disable some barriers** that are preventing certain actions. For example, there is an Organization Policy constraint named _appengine.disableCodeDownload_ that prevents App Engine source code from being downloaded by users of the project. If this was enabled, you would not be able to download that source code, but you could use _orgpolicy.policy.set_ to disable the constraint and then continue with the source code download.

此方法确实**不一定授予您更多的IAM权限**，但它可能**禁用某些障碍**，这些障碍正在阻止某些行动。 例如，有一个名为_appengine.disablecodedownload_的组织策略约束，该组织可以防止App Engine源代码由项目用户下载。 如果启用了此功能，您将无法下载该源代码，但是您可以使用_orgpolicy.policy.set_禁用约束，然后继续下载源代码。

![](https://rhinosecuritylabs.com/wp-content/uploads/2020/04/image5-1.png)

The screenshot above shows that the _appengine.disableCodeDownload_ constraint is enforced, which means it is preventing us from downloading the source code. Using _orgpolicy.policy.set_, we can disable that enforcement and then continue on to download the source code.

上面的屏幕截图显示_appengine.disablecodedownload_约束已执行，这意味着它阻止我们下载源代码。 使用_orgpolicy.policy.set_，我们可以禁用该执行，然后继续下载源代码。

The exploit script for this method can be found [here](https://github.com/RhinoSecurityLabs/GCP-IAM-Privilege-Escalation/blob/master/ExploitScripts/orgpolicy.policy.set.py).

可以找到此方法的利用脚本[此处]（https://github.com/rhinosecuritylabs/gcp-iam-privilege-escalation/blob/master/master/exploitscripts/orgpolicy.policy.policy.set.set.set.py）。

# serviceusage

The following permissions are useful to create and steal API keys, not this from the docs: _An API key is a simple encrypted string that **identifies an application without any principal**. They are useful for accessing **public data anonymously**, and are used to **associate** API requests with your project for quota and **billing**._

以下权限可用于创建和窃取API键，而不是从文档中来窃取API键：_AN API键是一个简单的加密字符串，**可以标识没有任何主体**的应用程序。 它们对于匿名访问**公共数据很有用，并且用于** apciate ** api请求与您的项目和**帐单**。

Therefore, with an API key you can make that company pay for your use of the API, but you won't be able to escalate privileges.

因此，使用API密钥，您可以使该公司为使用API付费，但是您将无法升级特权。

## serviceusage.apiKeys.create

## serviceusage.apikeys.create

There is another method of authenticating with GCP APIs known as API keys. By default, they are created with no restrictions, which means they have access to the entire GCP project they were created in. We can capitalize on that fact by creating a new API key that may have more privileges than our own user. There is no official API for this, so a custom HTTP request needs to be sent to _https://apikeys.clients6.google.com/_ (or _https://apikeys.googleapis.com/_). This was discovered by monitoring the HTTP requests and responses while browsing the GCP web console. For documentation on the restrictions associated with API keys, visit [this link](https://cloud.google.com/docs/authentication/api-keys).

还有另一种使用称为API键的GCP API进行身份验证的方法。 默认情况下，它们是没有限制的，这意味着他们可以访问其创建的整个GCP项目。我们可以通过创建一个可能比我们自己的用户更具特权的新API密钥来利用这一事实。 没有官方的API，因此需要将自定义的http请求发送到_https：//apikeys.clients6.google.com/_（或_https：//apikeys.googleapis.com/_）。 这是通过在浏览GCP Web控制台时监视HTTP请求和响应来发现的。 有关与API密钥相关的限制的文档，请访问[此链接]（https://cloud.google.com/docs/authentication/api-keys）。

The following screenshot shows how you would create an API key in the web console.

以下屏幕截图显示了如何在Web控制台中创建API键。

![](https://rhinosecuritylabs.com/wp-content/uploads/2020/04/image6-1.png)

With the undocumented API that was discovered, we can also create API keys through the API itself.

有了发现的无证API，我们还可以通过API本身创建API键。

The screenshot above shows a POST request being sent to retrieve a new API key for the project.

上面的屏幕截图显示了发送的帖子请求以检索项目的新API密钥。

The exploit script for this method can be found [here](https://github.com/RhinoSecurityLabs/GCP-IAM-Privilege-Escalation/blob/master/ExploitScripts/serviceusage.apiKeys.create.py).

可以找到此方法的利用脚本[此处]（https://github.com/rhinosecuritylabs/gcp-iam-privilege-escalation/blob/master/master/exploitscripts/servicecripts/serviceusage.apikeysage.apikeysage.apikeys.create.py.py）。

## serviceusage.apiKeys.list

Another undocumented API was found for listing API keys that have already been created (this can also be done in the web console). Because you can still see the API key’s value after its creation, we can pull all the API keys in the project.

发现了另一个无证API，用于列出已经创建的API键（这也可以在Web控制台中完成）。 因为您仍然可以在创建其创建后的API键的值，所以我们可以在项目中提取所有API键。

![](https://rhinosecuritylabs.com/wp-content/uploads/2020/04/image4-1.png)

The screenshot above shows that the request is exactly the same as before, it just is a GET request instead of a POST request. This only shows a single key, but if there were additional keys in the project, those would be listed too.

上面的屏幕截图表明，该请求与以前完全相同，它只是get请求而不是邮政请求。 这仅显示一个键，但是如果项目中还有其他钥匙，也会列出这些键。

The exploit script for this method can be found [here](https://github.com/RhinoSecurityLabs/GCP-IAM-Privilege-Escalation/blob/master/ExploitScripts/serviceusage.apiKeys.list.py).

可以找到此方法的利用脚本[此处]（https://github.com/rhinosecuritylabs/gcp-iam-privilege-escalation/blob/master/master/exploitscripts/servicecripts/serviceusage.apikeusage.apikeys.list.list.py）。

# apikeys

The following permissions are useful to create and steal API keys, not this from the docs: _An API key is a simple encrypted string that **identifies an application without any principal**. They are useful for accessing **public data anonymously**, and are used to **associate** API requests with your project for quota and **billing**._

以下权限可用于创建和窃取API键，而不是从文档中来窃取API键：_AN API键是一个简单的加密字符串，**可以标识没有任何主体**的应用程序。 它们对于匿名访问**公共数据很有用，并且用于** apciate ** api请求与您的项目和**帐单**。

Therefore, with an API key you can make that company pay for your use of the API, but you won't be able to escalate privileges.

因此，使用API密钥，您可以使该公司为使用API付费，但是您将无法升级特权。

## apikeys.keys.create <a href="#apikeys.keys.create" id="apikeys.keys.create"></a>

## api keys.keys.create <a href="#apikeys.keys.keys.create" id="api keys.keys.keys.create"> </a>

This permission allows to **create an API key**:

此权限允许**创建API密钥**：

```bash
gcloud alpha services api-keys create
Operation [operations/akmf.p7-[...]9] complete. Result: {
    "@type":"type.googleapis.com/google.api.apikeys.v2.Key",
    "createTime":"2022-01-26T12:23:06.281029Z",
    "etag":"W/\"HOhA[...]==\"",
    "keyString":"AIzaSy[...]oU",
    "name":"projects/5[...]6/locations/global/keys/f707[...]e8",
    "uid":"f707[...]e8",
    "updateTime":"2022-01-26T12:23:06.378442Z"
}
```

You can find a script to automate the [**creation, exploit and cleaning of a vuln environment here**](https://github.com/carlospolop/gcp\_privesc\_scripts/blob/main/tests/b-apikeys.keys.create.sh).

您可以在此处找到一个脚本来自动化[**创建，利用和清洁vuln环境**]（https://github.com/carloppolop/gcp \ _privescccccccccccrive_scripts/blob/main/main/main/main/tests/b-apikeys/b-apikeysys/b-apikeysys .keys.create.sh）。

## apikeys.keys.getKeyString,apikeys.keys.list <a href="#apikeys.keys.getkeystringapikeys.keys.list" id="apikeys.keys.getkeystringapikeys.keys.list"></a>

These permissions allows **list and get all the apiKeys and get the Key**:

这些权限允许**列表并获取所有apikeys并获取密钥**：

```bash
gcloud alpha services api-keys create
for  key  in  $(gcloud --impersonate-service-account="${SERVICE_ACCOUNT_ID}@${PROJECT_ID}.iam.gserviceaccount.com" alpha services api-keys list --uri); do
	gcloud --impersonate-service-account="${SERVICE_ACCOUNT_ID}@${PROJECT_ID}.iam.gserviceaccount.com" alpha services api-keys get-key-string "$key"
done
```

You can find a script to automate the [**creation, exploit and cleaning of a vuln environment here**](https://github.com/carlospolop/gcp\_privesc\_scripts/blob/main/tests/c-apikeys.keys.getKeyString.sh).

您可以在此处找到一个脚本来自动化[**创建，利用和清洁vuln环境**]（https://github.com/carloppolop/gcp \ _privescccccccccccrive_scripts/blob/main/main/main/main/tests/c-apikeys/c-apikeysys/capikeysys .keys.getKeyString.sh）。

## apikeys.keys.regenerate,apikeys.keys.list <a href="#serviceusage.apikeys.regenerateapikeys.keys.list" id="serviceusage.apikeys.regenerateapikeys.keys.list"></a>

## apikeys.keys.regenerate,apikeys.keys.list <a href="#serviceusage.apikeys.regenerateapikeys.keys.list" id="serviceusage.apikeys.regenerateapikeys.keys.list"></a>

These permissions will (potentially) allow you to **list and regenerate all the apiKeys getting the new Key**.\

这些权限（可能）将允许您**列表并重新生成所有apikeys获取新密钥**。
It’s not possible to use this from `gcloud` but you probably can use it via the API. Once it’s supported, the exploitation will be similar to the previous one (I guess).

不可能从“ gcloud”中使用它，但是您可能可以通过API使用它。 一旦得到支持，剥削将与前一个相似（我想）。

## apikeys.keys.lookup <a href="#apikeys.keys.lookup" id="apikeys.keys.lookup"></a>

This is extremely useful to check to **which GCP project an API key that you have found belongs to**:

这对于检查哪个GCP项目属于**的API密钥非常有用。**：

```bash
gcloud alpha services api-keys lookup AIzaSyD[...]uE8Y
name: projects/5[...]6/locations/global/keys/28d[...]e0e
parent: projects/5[...]6/locations/global
```

In this scenario it could also be interesting to run the tool [https://github.com/ozguralp/gmapsapiscanner](https://github.com/ozguralp/gmapsapiscanner) and check what you can access with the API key

在这种情况下，运行该工具[https://github.com/ozguralp/gmapsapiscanner]（

# secretmanager

＃Secretmanager

## secretmanager.secrets.get

This give you access to read the secrets from the secret manager.

这使您可以访问秘密经理的秘密。

## secretmanager.secrets.setIamPolicy

## Secretmanager.secrets.setiampolicy

This give you access to give you access to read the secrets from the secret manager.

这使您可以访问您可以访问秘密经理的秘密。

# \*.setIamPolicy

If you owns a user that has the **`setIamPolicy`** permission in a resource you can **escalate privileges in that resource** because you will be able to change the IAM policy of that resource and give you more privileges over it.

如果您拥有具有** setiampolicy` **在资源中的用户，则可以**在该资源中升级特权**，因为您将能够更改该资源的IAM策略，并为您提供更多特权。 。

* _cloudfunctions.functions.setIamPolicy_

* _cloudfunctions.functions.setiampolicy_
  * Modify the policy of a Cloud Function to allow yourself to invoke it.

*修改云功能的策略以使自己调用它。

There are tens of resources types with this kind of permission, you can find all of them in [https://cloud.google.com/iam/docs/permissions-reference](https://cloud.google.com/iam/docs/permissions-reference) searching for setIamPolicy.

此类许可有数十种资源类型，您可以在[https://cloud.google.com/iam/docs/permissions-reference-preshions-reference]（ /doc/permissions-参考）搜索setiampolicy。

An **example** of privilege escalation abusing .setIamPolicy (in this case in a bucket) can be found here:

一个**示例**滥用特权升级的.setiampolicy（在这种情况下为桶中）可以在此处找到：

{% content-ref url="../gcp-buckets-brute-force-and-privilege-escalation.md" %}

{％content-ref url =“ ../ gcp-buckets-brute-force-and-privilege-escalation.md“％}
[gcp-buckets-brute-force-and-privilege-escalation.md](../gcp-buckets-brute-force-and-privilege-escalation.md)

[GCP-Buckets-Buckets-Force-and-Privilege-Escalation.md]（../ GCP-Buckets-Buckets-brute-force-and-privilege-eascalation.md）
{% endcontent-ref %}

# Generic Interesting Permissions

＃通用有趣的权限

## \*.create, \*.update

These permissions can be very useful to try to escalate privileges in resources by **creating a new one or updating a new one**. These can of permissions are specially useful if you also has the permission **iam.serviceAccounts.actAs** over a Service Account and the resource you have .create/.update over can attach a service account.

这些权限可以通过**创建新的或更新新的**来升级资源的特权非常有用。 如果您还获得了服务帐户上的权限** iam.serviceaccounts.actas **，则这些权限非常有用。

## \*ServiceAccount\*

## \*serviceaccount \*

This permission will usually let you **access or modify a Service Account in some resource** (e.g.: compute.instances.setServiceAccount). This **could lead to a privilege escalation** vector, but it will depend on each case.

此权限通常会让您**在某些资源**中访问或修改服务帐户（例如：compute.instances.setserviceaccount）。 这个**可能导致特权升级**向量，但这将取决于每种情况。

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


