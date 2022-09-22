

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


# RBAC

＃RBAC

Airflow ships with a **set of roles by default**: **Admin**, **User**, **Op**, **Viewer**, and **Public**. **Only `Admin`** users could **configure/alter the permissions for other roles**. But it is not recommended that `Admin` users alter these default roles in any way by removing or adding permissions to these roles.

默认情况下，气流带有一组**角色，**：** admin **，**用户**，** op **，** viever **和** public **。 **只有``admin` ** admin`用户都可以**配置/更改其他角色的权限**。 但是，不建议通过删除或添加这些角色的权限来以任何方式更改这些默认角色。

* **`Admin`** users have all possible permissions.

***管理**用户拥有所有可能的权限。* **`Public`** users (anonymous) don’t have any permissions.

***``public` **用户（匿名）没有任何权限。
* **`Viewer`** users have limited viewer permissions (only read). It **cannot see the config.**

***查看器**用户的观众权限有限（仅阅读）。 它**看不到配置。**
* **`User`** users have `Viewer` permissions plus additional user permissions that allows him to manage DAGs a bit. He **can see the config file**

***``用户`**用户拥有'Viewer'权限以及其他用户权限，使他可以管理DAG。 他**可以看到配置文件**
* **`Op`** users have `User` permissions plus additional op permissions.

***``op` **用户拥有``用户''权限以及其他OP权限。

Note that **admin** users can **create more roles** with more **granular permissions**.

请注意，Admin **用户可以**创建更多的角色**使用更多**粒状权限**。

Also note that the only default role with **permission to list users and roles is Admin, not even Op** is going to be able to do that.

另请注意，唯一具有**列出用户和角色的默认角色是管理员，甚至无法做到这一点。

## Default Permissions

These are the default permissions per default role:

这些是每个默认角色的默认权限：

* **Admin**

\[can delete on Connections, can read on Connections, can edit on Connections, can create on Connections, can read on DAGs, can edit on DAGs, can delete on DAGs, can read on DAG Runs, can read on Task Instances, can edit on Task Instances, can delete on DAG Runs, can create on DAG Runs, can edit on DAG Runs, can read on Audit Logs, can read on ImportError, can delete on Pools, can read on Pools, can edit on Pools, can create on Pools, can read on Providers, can delete on Variables, can read on Variables, can edit on Variables, can create on Variables, can read on XComs, can read on DAG Code, can read on Configurations, can read on Plugins, can read on Roles, can read on Permissions, can delete on Roles, can edit on Roles, can create on Roles, can read on Users, can create on Users, can edit on Users, can delete on Users, can read on DAG Dependencies, can read on Jobs, can read on My Password, can edit on My Password, can read on My Profile, can edit on My Profile, can read on SLA Misses, can read on Task Logs, can read on Website, menu access on Browse, menu access on DAG Dependencies, menu access on DAG Runs, menu access on Documentation, menu access on Docs, menu access on Jobs, menu access on Audit Logs, menu access on Plugins, menu access on SLA Misses, menu access on Task Instances, can create on Task Instances, can delete on Task Instances, menu access on Admin, menu access on Configurations, menu access on Connections, menu access on Pools, menu access on Variables, menu access on XComs, can delete on XComs, can read on Task Reschedules, menu access on Task Reschedules, can read on Triggers, menu access on Triggers, can read on Passwords, can edit on Passwords, menu access on List Users, menu access on Security, menu access on List Roles, can read on User Stats Chart, menu access on User's Statistics, menu access on Base Permissions, can read on View Menus, menu access on Views/Menus, can read on Permission Views, menu access on Permission on Views/Menus, can get on MenuApi, menu access on Providers, can create on XComs]

\ [可以在连接上删除，可以在连接上读取，可以在连接上进行编辑，可以在连接上创建，可以在DAG上读取，可以在DAG上进行编辑，可以在DAG上删除，可以在DAG运行上读取，可以在DIG运行中阅读，可以在任务实例上阅读，CAN，可以在任务实例上进行编辑，可以在DAG运行中删除，可以在DAG运行中创建，可以在DAG运行上进行编辑，可以在审核日志上阅读，可以在Importerror上读取，可以在池上删除，可以在池上阅读，可以在池上进行编辑，可以在池上编辑，可以在池上创建，可以在提供商上读取，可以在变量上删除，可以在变量上读取，可以在变量上编辑，可以在变量上创建，可以在XCOM上读取，可以在XCOM上读取，可以在DAG代码上阅读，可以在配置上阅读，可以在插件上阅读，可以在插件上阅读，可以阅读角色，可以在权限上阅读，可以删除角色，可以编辑角色，可以在角色上创建，可以在用户上阅读，可以在用户上创建，可以在用户上编辑，可以删除用户，可以在DAG依赖项上阅读，可以在作业上阅读，可以阅读我的密码，可以在密码上编辑，可以在我的个人资料上阅读，可以在个人资料上进行编辑，可以在SLA MISSE上阅读s，可以在任务日志上阅读，可以在网站上阅读，浏览菜单访问，dag依赖项上的菜单访问，菜单访问dag runs，菜单访问，文档上的菜单访问，菜单上的菜单访问，菜单访问作品，菜单上的菜单访问，菜单访问菜单访问在审核日志上，菜单访问插件，菜单访问SLA错过，任务实例上的菜单访问，可以在任务实例上创建，可以在任务实例上删除，在admin上进行菜单访问，配置上的菜单访问，菜单访问连接，菜单访问，pool on pools，菜单上的菜单访问变量，XCOMS上的菜单访问，可以在XCOMS上删除，可以在任务重新安排上阅读，任务重新安排上的菜单访问，可以在触发器上读取，触发器上的菜单访问，可以在密码上读取，可以在密码上进行编辑，在密码上进行编辑，菜单访问菜单访问，访问菜单。列表用户，菜单访问安全性，列表角色上的菜单访问，可以在用户统计数据图上阅读，用户统计信息菜单访问，基本权限菜单访问，可以在视图菜单上阅读，菜单访问，视图/菜单上的菜单访问，可以在许可方面阅读视图，视图/菜单许可时访问菜单，可以获取Menuapi，在XCOMS上可以创建菜单访问菜单]

* **Op**

\[can delete on Connections, can read on Connections, can edit on Connections, can create on Connections, can read on DAGs, can edit on DAGs, can delete on DAGs, can read on DAG Runs, can read on Task Instances, can edit on Task Instances, can delete on DAG Runs, can create on DAG Runs, can edit on DAG Runs, can read on Audit Logs, can read on ImportError, can delete on Pools, can read on Pools, can edit on Pools, can create on Pools, can read on Providers, can delete on Variables, can read on Variables, can edit on Variables, can create on Variables, can read on XComs, can read on DAG Code, can read on Configurations, can read on Plugins, can read on DAG Dependencies, can read on Jobs, can read on My Password, can edit on My Password, can read on My Profile, can edit on My Profile, can read on SLA Misses, can read on Task Logs, can read on Website, menu access on Browse, menu access on DAG Dependencies, menu access on DAG Runs, menu access on Documentation, menu access on Docs, menu access on Jobs, menu access on Audit Logs, menu access on Plugins, menu access on SLA Misses, menu access on Task Instances, can create on Task Instances, can delete on Task Instances, menu access on Admin, menu access on Configurations, menu access on Connections, menu access on Pools, menu access on Variables, menu access on XComs, can delete on XComs]

\ [可以在连接上删除，可以在连接上读取，可以在连接上进行编辑，可以在连接上创建，可以在DAG上读取，可以在DAG上进行编辑，可以在DAG上删除，可以在DAG运行上读取，可以在DIG运行中阅读，可以在任务实例上阅读，CAN，可以在任务实例上进行编辑，可以在DAG运行中删除，可以在DAG运行中创建，可以在DAG运行上进行编辑，可以在审核日志上阅读，可以在Importerror上读取，可以在池上删除，可以在池上阅读，可以在池上进行编辑，可以在池上编辑，可以在池上创建，可以在提供商上读取，可以在变量上删除，可以在变量上读取，可以在变量上编辑，可以在变量上创建，可以在XCOM上读取，可以在XCOM上读取，可以在DAG代码上阅读，可以在配置上阅读，可以在插件上阅读，可以在插件上阅读，可以在DAG依赖项上阅读，可以在作业上阅读，可以在密码上阅读，可以在密码上进行编辑，可以在我的个人资料上阅读，可以在我的个人资料上进行编辑，可以在SLA错过上阅读，可以在任务日志上阅读，可以继续阅读网站，浏览菜单访问，DAG依赖项上的菜单访问，DAG运行中的菜单访问，文档上的菜单访问，文档上的菜单访问，菜单a菜单CCESS在作业上，菜单访问审核日志，菜单上的菜单访问，SLA错过的菜单访问，任务实例上的菜单访问，可以在任务实例上创建，可以在任务实例上删除，在admin上菜单访问，菜单访问，配置上的菜单，菜单，菜单访问连接，菜单上的菜单访问，变量上的菜单访问，XCOMS上的菜单访问，可以在XCOM上删除]

* **User**

\[can read on DAGs, can edit on DAGs, can delete on DAGs, can read on DAG Runs, can read on Task Instances, can edit on Task Instances, can delete on DAG Runs, can create on DAG Runs, can edit on DAG Runs, can read on Audit Logs, can read on ImportError, can read on XComs, can read on DAG Code, can read on Plugins, can read on DAG Dependencies, can read on Jobs, can read on My Password, can edit on My Password, can read on My Profile, can edit on My Profile, can read on SLA Misses, can read on Task Logs, can read on Website, menu access on Browse, menu access on DAG Dependencies, menu access on DAG Runs, menu access on Documentation, menu access on Docs, menu access on Jobs, menu access on Audit Logs, menu access on Plugins, menu access on SLA Misses, menu access on Task Instances, can create on Task Instances, can delete on Task Instances]

\ [可以在DAG上阅读，可以在DAG上进行编辑，可以在DAG上删除，可以在DAG运行中读取，可以在任务实例上阅读，可以在任务实例上进行编辑，可以在DAG运行中删除DAG运行，可以在DAG运行中创建，可以在DAG运行中进行编辑，可以在 DAG运行，可以在审核日志上阅读，可以在Importerror上阅读，可以在XCOMS上阅读，可以在DAG代码上阅读，可以在插件上阅读，可以在DAG依赖项上阅读，可以在工作上阅读，可以在我的密码上阅读，可以在我的密码上阅读，可以编辑， 我的密码可以在我的个人资料上阅读，可以在我的个人资料上进行编辑，可以在SLA错过上阅读，可以在任务日志上阅读，可以在网站上阅读，浏览菜单访问，菜单访问DAG依赖项，菜单访问DAG运行，菜单，菜单 访问文档，文档上的菜单访问，菜单上的菜单访问，审核日志上的菜单访问，插件上的菜单访问，菜单访问SLA错过，菜单访问菜单访问，在任务实例上可以创建，可以在任务实例上创建，可以在任务实例上删除]

* **Viewer**

\[can read on DAGs, can read on DAG Runs, can read on Task Instances, can read on Audit Logs, can read on ImportError, can read on XComs, can read on DAG Code, can read on Plugins, can read on DAG Dependencies, can read on Jobs, can read on My Password, can edit on My Password, can read on My Profile, can edit on My Profile, can read on SLA Misses, can read on Task Logs, can read on Website, menu access on Browse, menu access on DAG Dependencies, menu access on DAG Runs, menu access on Documentation, menu access on Docs, menu access on Jobs, menu access on Audit Logs, menu access on Plugins, menu access on SLA Misses, menu access on Task Instances]

\ [可以在DAGS上阅读，可以在DAG运行中阅读，可以在任务实例上阅读，可以在审核日志上阅读，可以在Inporterror上阅读，可以在XCOM上读取，可以在XCOM上阅读，可以在DAG代码上阅读，可以在DAG代码上阅读，可以在插件上阅读，可以在DAG上阅读DAG上的DAG上阅读 依赖项，可以在作业上阅读，可以在密码上阅读，可以在密码上进行编辑，可以在我的个人资料上阅读，可以在我的个人资料上进行编辑，可以在SLA错过上阅读，可以在任务日志上阅读，可以在网站上阅读，菜单访问 在浏览中，在dag依赖项上访问菜单，菜单访问dag runs，菜单上的菜单访问，菜单上的菜单访问，菜单上的菜单访问作品，菜单访问在审核日志上，菜单访问插件上的菜单访问，菜单上的菜单访问SLA错过，菜单访问菜单访问菜单上 任务实例]

* **Public**

\[]


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


