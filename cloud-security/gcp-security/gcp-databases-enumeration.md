

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


Google has [a handful of database technologies](https://cloud.google.com/products/databases/) that you may have access to via the default service account or another set of credentials you have compromised thus far.

Google拥有[少数数据库技术]（https://cloud.google.com/products/databases/），您可能可以通过默认服务帐户或迄今为止已妥协的另一组凭据访问。

Databases will usually contain interesting information, so it would be completely recommended to check them. Each database type provides various **`gcloud` commands to export the data**. This typically involves **writing the database to a cloud storage bucket first**, which you can then download. It may be best to use an existing bucket you already have access to, but you can also create your own if you want.

数据库通常包含有趣的信息，因此完全建议检查它们。 每个数据库类型都提供各种**``gcloud`命令来导出数据**。 这通常涉及**将数据库首先写入云存储桶**，然后您可以下载。 最好使用您已经可以访问的现有存储桶，但是如果需要，您也可以创建自己的东西。

As an example, you can follow [Google's documentation](https://cloud.google.com/sql/docs/mysql/import-export/exporting) to exfiltrate a Cloud SQL database.

例如，您可以关注[Google的文档]（https://cloud.google.com/sql/docs/mysql/mysql/import-export/exporting）去删除云SQL数据库。

## [Cloud SQL](https://cloud.google.com/sdk/gcloud/reference/sql/)

Cloud SQL instances are **fully managed, relational MySQL, PostgreSQL and SQL Server databases**. Google handles replication, patch management and database management to ensure availability and performance.[Learn more](https://cloud.google.com/sql/docs/)

云SQL实例**完全管理，关系MySQL，PostgreSQL和SQL Server数据库**。 Google处理复制，补丁管理和数据库管理以确保可用性和性能。[了解更多]（https://cloud.google.com/sql/docs/）

If you find any of these instances in use, you could try to **access it from the internet** as they might be miss-configured and accessible.

如果您发现使用中的任何一个实例，则可以尝试**从Internet **访问它，因为它们可能会错过配置和访问。

```bash
# Cloud SQL
gcloud sql instances list
gcloud sql databases list --instance [INSTANCE]
gcloud sql backups list --instance [INSTANCE]
gcloud sql export sql <DATABASE_INSTANCE> gs://<CLOUD_STORAGE_BUCKET>/cloudsql/export.sql.gz --database <DATABASE_NAME>
```

## [Cloud Spanner](https://cloud.google.com/sdk/gcloud/reference/spanner/)

Fully managed relational database with unlimited scale, strong consistency, and up to 99.999% availability.

具有无限规模，强大的一致性和高达99.999％的可用性的完全管理的关系数据库。

```bash
# Cloud Spanner
gcloud spanner instances list
gcloud spanner databases list --instance [INSTANCE]
gcloud spanner backups list --instance [INSTANCE]
```

## [Cloud Bigtable](https://cloud.google.com/sdk/gcloud/reference/bigtable/) <a href="#cloud-bigtable" id="cloud-bigtable"></a>

## [cloud bigtable]（https://cloud.google.com/sdk/gcloud/reference/reference/bigtable/）<a href="#cloud-bigtable" ID="cloud-bigtable"> </a>

A fully managed, scalable NoSQL database service for large analytical and operational workloads with up to 99.999% availability. [Learn more](https://cloud.google.com/bigtable).

可用于大型分析和运营工作负载的全面管理，可扩展的NOSQL数据库服务，可用性高达99.999％。 [了解更多]（https://cloud.google.com/bigtable）。

```bash
# Cloud Bigtable
gcloud bigtable instances list
gcloud bigtable clusters list
gcloud bigtable backups list --instance [INSTANCE]
```

## [Cloud Firestore](https://cloud.google.com/sdk/gcloud/reference/firestore/)

Cloud Firestore is a flexible, scalable database for mobile, web, and server development from Firebase and Google Cloud. Like Firebase Realtime Database, it keeps your data in sync across client apps through realtime listeners and offers offline support for mobile and web so you can build responsive apps that work regardless of network latency or Internet connectivity. Cloud Firestore also offers seamless integration with other Firebase and Google Cloud products, including Cloud Functions. [Learn more](https://firebase.google.com/docs/firestore).

Cloud Firestore是Firebase和Google Cloud的移动，Web和服务器开发的灵活，可扩展的数据库。 像Firebase实时数据库一样，它可以通过实时侦听器使您的数据在客户端应用程序之间保持同步，并为移动和Web提供离线支持，因此您可以构建响应式应用程序，无论网络延迟或Internet连接如何。 Cloud Firestore还提供与其他Firebase和Google Cloud产品（包括云功能）的无缝集成。 [了解更多]（https://firebase.google.com/docs/firestore）。

```
gcloud firestore indexes composite list
gcloud firestore indexes fields list
gcloud firestore export gs://my-source-project-export/export-20190113_2109 --collection-ids='cameras','radios'
```

## [Firebase](https://cloud.google.com/sdk/gcloud/reference/firebase/)

## [firebase]（https://cloud.google.com/sdk/gcloud/reference/reference/firebase/）

The Firebase Realtime Database is a cloud-hosted NoSQL database that lets you store and sync data between your users in realtime. [Learn more](https://firebase.google.com/products/realtime-database/).

Firebase实时数据库是一个云托管的NOSQL数据库，可让您实时存储和同步数据。 [了解更多]（https://firebase.google.com/products/realtime-database/）。

## Memorystore

## MemoryStore

Reduce latency with scalable, secure, and highly available in-memory service for [**Redis**](https://cloud.google.com/sdk/gcloud/reference/redis) and [**Memcached**](https://cloud.google.com/sdk/gcloud/reference/memcache). Learn more.

使用可扩展，安全且高度可用的内存服务来减少延迟，用于[** redis **]（https://cloud.google.com/sdk/gcloud/referend/reference/redis）和[** memcached **]（ https://cloud.google.com/sdk/gcloud/reference/memcache）。 学到更多。

```bash
gcloud memcache instances list --region [region]
# You should try to connect to the memcache instances to access the data

gcloud redis instances list --region [region]
gcloud redis instances export gs://my-bucket/my-redis-instance.rdb my-redis-instance --region=us-central1
```

## [Bigquery](https://cloud.google.com/bigquery/docs/bq-command-line-tool)

BigQuery is a fully-managed enterprise data warehouse that helps you manage and analyze your data with built-in features like machine learning, geospatial analysis, and business intelligence. BigQuery’s serverless architecture lets you use SQL queries to answer your organization’s biggest questions with zero infrastructure management. BigQuery’s scalable, distributed analysis engine lets you query terabytes in seconds and petabytes in minutes. [Learn more](https://cloud.google.com/bigquery/docs/introduction).

BigQuery是一家完全管理的企业数据仓库，可帮助您使用机器学习，地理空间分析和商业智能等内置功能来管理和分析数据。 BigQuery的无服务器体系结构使您可以使用SQL查询来通过零基础架构管理来回答组织的最大问题。 Bigquery的可扩展分布式分析引擎可让您在几秒钟内在几分钟内查询trabytes。 [了解更多]（https://cloud.google.com/bigquery/docs/introduction）。

```bash
bq ls -p #List rojects
bq ls -a #List all datasets
bq ls #List datasets from current project
bq ls <dataset_name> #List tables inside the DB

# Show information
bq show "<proj_name>:<dataset_name>"
bq show "<proj_name>:<dataset_name>.<table_name>"
bq show --encryption_service_account

bq query '<query>' #Query inside the dataset

# Dump the table or dataset
bq extract ds.table gs://mybucket/table.csv
bq extract -m ds.model gs://mybucket/model
```

Big query SQL Injection: [https://ozguralp.medium.com/bigquery-sql-injection-cheat-sheet-65ad70e11eac](https://ozguralp.medium.com/bigquery-sql-injection-cheat-sheet-65ad70e11eac)

大查询SQL注入：[https：//ozguralp.medium.com/bigquery-sql-injoction-indoction-indoction-cheat-sheet-65ad70e11eac]（ ）


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


