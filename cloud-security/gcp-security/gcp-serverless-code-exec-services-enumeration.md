

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


# Cloud Functions <a href="reviewing-cloud-functions" id="reviewing-cloud-functions"></a>

＃云功能<a href="reviewing-cloud-functions" id="reviewing-cloud-functions"> </a>

Google [Cloud Functions](https://cloud.google.com/functions/) allow you to host code that is executed when an event is triggered, without the requirement to manage a host operating system. These functions can also store environment variables to be used by the code.

Google [Cloud Functions]（https://cloud.google.com/functions/）允许您在事件触发时托管代码，而无需管理主机操作系统。 这些功能还可以存储代码使用的环境变量。

```bash
# List functions
gcloud functions list

# Get function config including env variables
gcloud functions describe [FUNCTION NAME]

# Get logs of previous runs
# By default, limits to 10 lines
gcloud functions logs read [FUNCTION NAME] --limit [NUMBER]
```

## Enumerate Open Cloud Functions

##枚举开放云功能

With the following code [taken from here](https://gitlab.com/gitlab-com/gl-security/security-operations/gl-redteam/gcp\_misc/-/blob/master/find\_open\_functions.sh) you can find Cloud Functions that permit unauthenticated invocations.

使用以下代码[从此处获取]（https://gitlab.com/gitlab-com/gl-security/security-poperations/gl-redteam/gcp \ _misc/-/blob/blob/master/master/find-_open \ _functions。 sh）您可以找到允许未经身心的调用的云功能。

```bash
#!/bin/bash

############################
# Run this tool to find Cloud Functions that permit unauthenticated invocations
# anywhere in your GCP organization.
# Enjoy!
############################

for proj in $(gcloud projects list --format="get(projectId)"); do
    echo "[*] scraping project $proj"

    enabled=$(gcloud services list --project "$proj" | grep "Cloud Functions API")

    if [ -z "$enabled" ]; then
	continue
    fi


    for func_region in $(gcloud functions list --quiet --project "$proj" --format="value[separator=','](NAME,REGION)"); do
        # drop substring from first occurence of "," to end of string.
        func="${func_region%%,*}"
        # drop substring from start of string up to last occurence of ","
        region="${func_region##*,}"
        ACL="$(gcloud functions get-iam-policy "$func" --project "$proj" --region "$region")"

        all_users="$(echo "$ACL" | grep allUsers)"
        all_auth="$(echo "$ACL" | grep allAuthenticatedUsers)"

        if [ -z "$all_users" ]
        then
              :
        else
              echo "[!] Open to all users: $proj: $func"
        fi

        if [ -z "$all_auth" ]
        then
              :
        else
              echo "[!] Open to all authenticated users: $proj: $func"
        fi
    done
done

```

# App Engine Configurations <a href="reviewing-app-engine-configurations" id="reviewing-app-engine-configurations"></a>

＃应用引擎配置<a href="reviewing-app-engine-configurations" id="reviewing-app-engine-configurations"> </a>

Google [App Engine](https://cloud.google.com/appengine/) is another ["serverless"](https://about.gitlab.com/topics/serverless/) offering for hosting applications, with a focus on scalability. As with Cloud Functions, **there is a chance that the application will rely on secrets that are accessed at run-time via environment variables**. These variables are stored in an `app.yaml` file which can be accessed as follows:

Google [App Engine]（https://cloud.google.com/appengine/）是另一个[“ serverless”]（https://about.gitlab.com/topics/serverless/）提供用于托管应用程序的，重点是 关于可伸缩性。 与云功能一样，**应用程序有可能依靠在运行时通过环境变量访问的秘密**。 这些变量存储在一个app.yaml`文件中，可以访问如下：

```bash
# First, get a list of all available versions of all services
gcloud app versions list

# Then, get the specific details on a given app
gcloud app describe [APP]
```

# Cloud Run Configurations <a href="reviewing-cloud-run-configurations" id="reviewing-cloud-run-configurations"></a>

＃云运行配置<a href="reviewing-cloud-run-configurations" id="reviewing-cloud-run-configurations"> </a>

Google [Cloud Run](https://cloud.google.com/run) is another serverless offer where you can search for env variables also. Cloud Run creates a small web server, running on port 8080, that sits around waiting for an HTTP GET request. When the request is received, a job is executed and the job log is output via an HTTP response.

Google [Cloud Run]（https://cloud.google.com/run）是另一个无服务器的报价，您也可以在其中搜索ENV变量。 Cloud Run创建了一个在端口8080上运行的小型Web服务器，该服务器围绕着等待HTTP获取请求。 收到请求后，执行作业，并通过HTTP响应输出作业日志。

The access to this web server might be public of managed via IAM permissions:

对该Web服务器的访问可能是通过IAM权限公开管理的：

```bash
# First get a list of services across the available platforms
gcloud run services list --platform=managed
gcloud run services list --platform=gke

# To learn more, export as JSON and investigate what the services do
gcloud run services list --platform=managed --format=json
gcloud run services list --platform=gke --format=json

# Attempt to trigger a job unauthenticated
curl [URL]

# Attempt to trigger a job with your current gcloud authorization
curl -H \
    "Authorization: Bearer $(gcloud auth print-identity-token)" \
    [URL]
```

## Enumerate Open CloudRun

With the following code [taken from here](https://gitlab.com/gitlab-com/gl-security/security-operations/gl-redteam/gcp\_misc/-/blob/master/find\_open\_cloudrun.sh) you can find Cloud Run services that permit unauthenticated invocations.

使用以下代码[从此处获取]（https://gitlab.com/gitlab-com/gl-security/security/security-operations/gl-redteam/gcp \_misc/-/blob/blob/master/master/find-_open \ _cloudrun。 sh）您可以找到允许未经身心的调用的云运行服务。

```bash
#!/bin/bash

############################
# Run this tool to find Cloud Run services that permit unauthenticated
# invocations anywhere in your GCP organization.
# Enjoy!
############################

for proj in $(gcloud projects list --format="get(projectId)"); do
    echo "[*] scraping project $proj"

    enabled=$(gcloud services list --project "$proj" | grep "Cloud Run API")

    if [ -z "$enabled" ]; then
	continue
    fi


    for run in $(gcloud run services list --platform managed --quiet --project $proj --format="get(name)"); do
        ACL="$(gcloud run services get-iam-policy $run --platform managed --project $proj)"

        all_users="$(echo $ACL | grep allUsers)"
        all_auth="$(echo $ACL | grep allAuthenticatedUsers)"

        if [ -z "$all_users" ]
        then
              :
        else
              echo "[!] Open to all users: $proj: $run"
        fi

        if [ -z "$all_auth" ]
        then
              :
        else
              echo "[!] Open to all authenticated users: $proj: $run"
        fi
    done
done

```

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


