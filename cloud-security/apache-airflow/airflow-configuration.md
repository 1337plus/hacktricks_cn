

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


# Configuration File

**Apache Airflow** generates a **config file** in all the airflow machines called **`airflow.cfg`** in the home of the airflow user. This config file contains configuration information and **might contain interesting and sensitive information.**

** Apache AirFlow **在所有称为** airflow.cfg` **的气流机器中生成一个**配置文件**在气流用户的家中。 此配置文件包含配置信息，**可能包含有趣且敏感的信息。**

**There are two ways to access this file: By compromising some airflow machine, or accessing the web console.**

**有两种访问此文件的方法：通过损害某些气流机或访问Web控制台。**

Note that the **values inside the config file** **might not be the ones used**, as you can overwrite them setting env variables such as `AIRFLOW__WEBSERVER__EXPOSE_CONFIG: 'true'`.

请注意，配置文件中的**值** **可能不是使用**的值，因为您可以覆盖它们设置env变量，例如`iarflow__webserver__expose_config：'true'。

If you have access to the **config file in the web server**, you can check the **real running configuration** in the same page the config is displayed.\

如果您可以访问Web服务器中的**配置文件**，则可以在同一页面中检查**真实的运行配置**。
If you have **access to some machine inside the airflow env**, check the **environment**.

如果您可以访问气流env **内部的某些机器，请检查**环境**。

Some interesting values to check when reading the config file:

阅读配置文件时需要检查一些有趣的值：

## \[api]

* **`access_control_allow_headers`**: This indicates the **allowed** **headers** for **CORS**

***`access_control_allow_headers` **：这表示**允许的** **标题** for ** cors **
* **`access_control_allow_methods`**: This indicates the **allowed methods** for **CORS**

***`access_control_allow_methods` **：这表示**允许的方法** ** for ** cors **
* **`access_control_allow_origins`**: This indicates the **allowed origins** for **CORS**

***
* **`auth_backend`**: [**According to the docs**](https://airflow.apache.org/docs/apache-airflow/stable/security/api.html)  a few options can be in place to configure who can access to the API:

***`auth_backend` **：[**根据文档**]（https://airflow.apache.org/docs/apache-apache-airflow/stable/security/api.html）可以在 配置谁可以访问API的地方：
  * `airflow.api.auth.backend.deny_all`: **By default nobody** can access the API

*`airflow.api.auth.backend.deny_all`：**默认情况下没有人**可以访问API
  * `airflow.api.auth.backend.default`: **Everyone can** access it without authentication

*`airflow.api.auth.backend.default`：**每个人都可以**无需身份验证即可访问它
  * `airflow.api.auth.backend.kerberos_auth`: To configure **kerberos authentication**

*`airflow.api.auth.backend.kerberos_auth`：配置** kerberos authentication **
  * `airflow.api.auth.backend.basic_auth`: For **basic authentication**

*`airflow.api.auth.backend.basic_auth`：for **基本身份验证**
  * `airflow.composer.api.backend.composer_auth`: Uses composers authentication (GCP) (from [**here**](https://cloud.google.com/composer/docs/access-airflow-api)).

*`airflow.composer.api.backend.composer_auth`：使用Composers Authentication（GCP）（来自[** there ** there **]（https://cloud.google.com/composer.com/composer/composer/docs/access-airflow-api）） 。
    * `composer_auth_user_registration_role`: This indicates the **role** the **composer user** will get inside **airflow** (**Op** by default).

*`composer_auth_user_registration_role`：这表示**角色** **作曲家用户**将进入** airflow **（默认情况下** op **）。
  * You can also **create you own authentication** method with python.

*您还可以**使用Python创建自己的身份验证**方法。
* **`google_key_path`:** Path to the **GCP service account key**

***``google_key_path`：**通往** GCP服务帐户密钥的路径**

## **\[atlas]**

* **`password`**: Atlas password
* **`username`**: Atlas username

***``用户名**：Atlas用户名

## \[celery]

＃＃ \[芹菜]

* **`flower_basic_auth`** : Credentials (_user1:password1,user2:password2_)

***`flower_basic_auth` **：凭据（_user1：password1，user2：password2_）
* **`result_backend`**: Postgres url which may contain **credentials**.

***``result_backend` **：postgres url可能包含**凭据**。
* **`ssl_cacert`**: Path to the cacert

***`ssl_cacert` **：通往cacert的路径
* **`ssl_cert`**: Path to the cert

***`ssl_cert` **：通往证书的路径
* **`ssl_key`**: Path to the key

***`s ssl_key` **：通往钥匙的路径

## \[core]

* **`dag_discovery_safe_mode`**: Enabled by default. When discovering DAGs, ignore any files that don’t contain the strings `DAG` and `airflow`.

***`dag_discovery_safe_mode` **：默认启用。 在发现DAG时，请忽略任何不包含字符串`dag'和``气流''的文件。
* **`fernet_key`**: Key to store encrypted variables (symmetric)

***`fernet_key` **：存储加密变量的关键（对称）
* **`hide_sensitive_var_conn_fields`**: Enabled by default, hide sensitive info of connections.

***`hide_sensisitive_var_conn_fields` **：默认启用，隐藏连接的敏感信息。
* **`security`**: What security module to use (for example kerberos)

***安全`**：要使用什么安全模块（例如kerberos）

## \[dask]

* **`tls_ca`**: Path to ca

***`tls_ca` **：通往CA的路径
* **`tls_cert`**: Part to the cert

***`tls_cert` **：证书的一部分
* **`tls_key`**: Part to the tls key

***`tls_key` **：tls键的部分

## \[kerberos]

* **`ccache`**: Path to ccache file

***`ccache` **：通往ccache文件的路径
* **`forwardable`**: Enabled by default

## \[logging]

* **`google_key_path`**: Path to GCP JSON creds.

***``google_key_path` **：通往GCP JSON CREDS的路径。

## \[secrets]

* **`backend`**: Full class name of secrets backend to enable

***后端`**：完整的秘密后端名称为启用
* **`backend_kwargs`**: The backend\_kwargs param is loaded into a dictionary and passed to **init** of secrets backend class.

***`backend_kwargs` **：后端\ _kwargs param已加载到字典中，并传递给** init ** of Secrets Backend类。

## \[smtp]

* **`smtp_password`**: SMTP password
* **`smtp_user`**: SMTP user

## \[webserver]

* **`cookie_samesite`**: By default it's **Lax**, so it's already the weakest possible value

***`cookie_samesite` **：默认情况下它是** lax **，所以它已经是最弱的值
* **`cookie_secure`**: Set **secure flag** on the the session cookie

***`cookie_secure` **：设置**安全标志**在会话cookie上
* **`expose_config`**: By default is False, if true, the **config** can be **read** from the web **console**

***``expose_config` **：默认情况下是错误的，如果是的，则可以** config ** **从Web ** ponsole ** ** ponsole ** **
* **`expose_stacktrace`**: By default it's True, it will show **python tracebacks** (potentially useful for an attacker)

***``expose_stacktrace` **：默认情况下，它将显示** Python Trackbacks **（对攻击者可能有用）
* **`secret_key`**: This is the **key used by flask to sign the cookies** (if you have this you can **impersonate any user in Airflow**)

***`secret_key` **：这是烧瓶用来签署cookies **的**键（如果有的话，可以**模仿气流中的任何用户**）
* **`web_server_ssl_cert`**: **Path** to the **SSL** **cert**

***`web_server_ssl_cert` **：**路径**到** ssl ** ** ** cert **
* **`web_server_ssl_key`**: **Path** to the **SSL** **Key**

***`web_server_ssl_key` **：**路径**到** ssl ** **键**
* **`x_frame_enabled`**: Default is **True**, so by default clickjacking isn't possible

***`x_frame_enabled` **：默认值为** true **，因此默认情况下是无法使用的

## Web Authentication

## Web身份验证

By default **web authentication** is specified in the file **`webserver_config.py`** and is configured as

默认情况下** Web Authentication **在文件**``weberver_config.py` ** **中指定

```bash
AUTH_TYPE = AUTH_DB
```

Which means that the **authentication is checked against the database**. However, other configurations are possible like

这意味着根据数据库**检查**身份验证。 但是，其他配置也可以像

```bash
AUTH_TYPE = AUTH_OAUTH
```

To leave the **authentication to third party services**.

将**身份验证留给第三方服务**。

However, there is also an option to a**llow anonymous users access**, setting the following parameter to the **desired role**:

但是，** llow匿名用户访问**也有一个选项，将以下参数设置为**所需的角色**：

```bash
AUTH_ROLE_PUBLIC = 'Admin'
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


