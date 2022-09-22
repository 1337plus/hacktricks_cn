# Browser Artifacts

＃浏览器工件

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

{% hint style="danger" %}
<img src="../../../.gitbook/assets/image (307).png" alt="" data-size="original">

<img src =“../../../。gitbook/assets/image（307）.png“ alt =”“ data-size =” ointers =“ ointers”>
Through Security Skills as a Service, we help organizations to **defend against the Dark Hacking Arts**. Security Skills as a Service is an offensive cybersecurity consultancy model that combines an Intelligent Platform with the top-class, globally distributed, offensive security engineers, delivering **high-quality penetration testing results. Security Hubs** bring together offensive penetration testing tactics with human behavioral science, providing real-time insights into threat actors' tradecraft and a **complete assessment of any risks**.

通过安全技能作为服务，我们帮助组织**防御黑暗黑客艺术**。 安全技能作为服务是一种进攻性网络安全咨询模型，将智能平台与顶级，全球分布式，进攻性安全工程师结合在一起，提供**高质量的渗透测试结果。 安全枢纽**将进攻性渗透测试策略与人类行为科学结合在一起，提供对威胁参与者贸易克罗夫特（Tradecraft）的实时见解，并对任何风险**进行完整评估。

{% embed url="https://securityhubs.io/" %}
{% endhint %}

## Browsers Artifacts <a href="#3def" id="3def"></a>

##浏览器文物<a href="#3def" id="3def"> </a>

When we talk about browser artifacts we talk about, navigation history, bookmarks, list of downloaded files, cache data, etc.

当我们谈论浏览器工件时，我们谈论的是，导航历史记录，书签，下载文件列表，缓存数据等。

These artifacts are files stored inside specific folders in the operating system.

这些工件是操作系统中特定文件夹中存储的文件。

Each browser stores its files in a different place than other browsers and they all have different names, but they all store (most of the time) the same type of data (artifacts).

每个浏览器将其文件存储在与其他浏览器不同的位置，并且它们都有不同的名称，但是它们（大多数时候）都存储了相同类型的数据（伪像）。

Let us take a look at the most common artifacts stored by browsers.

让我们看一下浏览器存储的最常见的文物。

* **Navigation History:** Contains data about the navigation history of the user. Can be used to track down if the user has visited some malicious sites for example

***导航历史记录：**包含有关用户导航历史记录的数据。 可以用用户访问过一些恶意网站来追踪
* **Autocomplete Data:** This is the data that the browser suggests based on what you search for the most. Can be used in tandem with the navigation history to get more insight.

***自动完成数据：**这是浏览器根据您最多搜索的数据所建议的数据。 可以与导航历史记录同时使用以获得更多的见解。
* **Bookmarks:** Self Explanatory.

***书签：**自我解释。
* **Extensions and Add ons:** Self Explanatory.

***扩展并添加启动：**自我解释。
* **Cache:** When navigating websites, the browser creates all sorts of cache data (images, javascript files…etc) for many reasons. For example to speed the loading time of websites. These cache files can be a great source of data during a forensic investigation.

***缓存：**导航网站时，浏览器出于许多原因而创建各种缓存数据（图像，JavaScript文件等）。 例如，加快网站的加载时间。 这些缓存文件可以是法医调查期间的重要数据来源。
* **Logins:** Self Explanatory.

***登录：**自我解释。
* **Favicons:** They are the little icons found in tabs, urls, bookmarks and the such. They can be used as another source to get more information about the website or places the user visited.

*** favicons：**它们是标签，URL，书签等中发现的小图标。 它们可以用作另一个来源，以获取有关该网站或访问用户访问的更多信息。
* **Browser Sessions:** Self Explanatory.

***浏览器会议：**自我解释。
* **Downloads:**Self Explanatory.

***下载：**自我解释。
* **Form Data:** Anything typed inside forms is oftentimes stored by the browser, so the next time the user enters something inside of a form the browser can suggest previously entered data.

***表单数据：**浏览器通常会存储内部表单内部的任何内容，因此，下一次用户在浏览器中可以建议先前输入的数据的表单中输入某些内容时。
* **Thumbnails:** Self Explanatory.

***缩略图：**自我解释。

## Firefox

## Firefox

Firefox 	create the profiles folder in \~/_**.mozilla/firefox/**_ (Linux), in **/Users/$USER/Library/Application Support/Firefox/Profiles/** (MacOS), _**%userprofile%\AppData\Roaming\Mozilla\Firefox\Profiles\\**_ (Windows)_**.**_\

Firefox在\〜/_ **中创建配置文件夹。mozilla/firefox/** _（linux），in **/user/$ user/library/library/application/firefox/profiles/**（macOS），_** *％userProfile％\ appdata \ roaming \ mozilla \ firefox \ profiles \\ ** _（windows）_ **。** _ \ _ \
Inside this folder, the file _**profiles.ini**_ should appear with the name(s) of the user profile(s).\

在此文件夹中，文件_ ** profiles.ini ** _应该以用户配置文件的名称出现。\ \ \
Each profile has a "**Path**" variable with the name of the folder where its data is going to be stored. The folder should be **present in the same directory where the \_profiles.ini**\_\*\* exist\*\*. If it isn't, then, probably it was deleted.

每个配置文件都有一个“ **路径**”变量，并具有将存储数据的文件夹的名称。 该文件夹应在同一目录中存在**，其中\ _profiles.ini ** \ _ \*\*存在\*\*。 如果不是这样，那么它可能已被删除。

Inside the folder **of each profile** (_\~/.mozilla/firefox/\<ProfileName>/_) path you should be able to find the following interesting files:

在每个配置文件的文件夹**内部**（_ \〜/.mozilla/firefox/\ <prifilename>/_）路径您应该能够找到以下有趣的文件：

* _**places.sqlite**_ : History (moz\_\_places), bookmarks (moz\_bookmarks), and downloads (moz\_\_annos). In Windows the tool [BrowsingHistoryView](https://www.nirsoft.net/utils/browsing\_history\_view.html) can be used to read the history inside _**places.sqlite**_.

*_ ** ploce.sqlite ** _：历史记录（moz \ _ \ _ place），书签（moz \ _ bookmarks）和下载（moz \ _ \ _ annos）。 在Windows中，工具[browsinghistoryview]（https://www.nirsoft.net/utils/browsing \ _history \ _view.html）可用于读取_ ** place.sqlite ** _ _ _ _ _ _ _的历史记录。
  * Query to dump history: `select datetime(lastvisitdate/1000000,'unixepoch') as visit_date, url, title, visit_count, visit_type FROM moz_places,moz_historyvisits WHERE moz_places.id = moz_historyvisits.place_id;`

*查询转储历史记录：`select dateTime（lastVisitDate/1000000，'unixepoch'）作为visit_date，url，url，title，title，title，coot_count，visit_type，moz_historyvisits，moz_historyvisits，moz__places.id = moz_ishistoryvisits.shistoryvisits.place_id;
    * Note that a link type is a number that indicates:

*请注意，链接类型是指示：
      * 1: User followed a link

* 1：用户遵循链接
      * 2: User wrote the URL

* 2：用户写了URL
      * 3: User used a favorite

* 3：用户使用了喜欢的
      * 4: Loaded from Iframe

* 4：从iframe加载
      * 5: Accessed via HTTP redirect 301

* 5：通过HTTP重定向301访问
      * 6: Accessed via HTTP redirect 302

* 6：通过HTTP重定向访问302
      * 7: Downloaded file

* 7：下载文件
      * 8: User followed a link inside an Iframe

* 8：用户遵循iframe中的链接
  * Query to dump downloads: `SELECT datetime(lastModified/1000000,'unixepoch') AS down_date, content as File, url as URL FROM moz_places, moz_annos WHERE moz_places.id = moz_annos.place_id;`

*查询要转储下载：`select dateTime（lastModified/1000000，'unixepoch'）as down_date，content as file，url为moz_annos，moz_annos，moz_annos where moz_annos.id = moz_annos.place_id;
  *
* _**bookmarkbackups/**_ : Bookmarks backups

*_ ** bookmarkbackups/** _：书签备份* _**formhistory.sqlite**_ : **Web form data** (like emails)

*_ ** formhistory.sqlite ** _：** Web表单数据**（如电子邮件）
* _**handlers.json**_ : Protocol handlers (like, which app is going to handle _mailto://_ protocol)

*_ ** handlers.json ** _：协议处理程序（就像，哪个应用程序要处理_mailto：// _ stoloce）
* _**persdict.dat**_ : Words added to the dictionary

*_ ** persdict.dat ** _：添加到字典中的单词
* _**addons.json**_ and \_**extensions.sqlite** \_ : Installed addons and extensions

*_ ** addons.json ** _ and \ _ ** Extensions.sqlite ** \ _：已安装addons和Extensions
* _**cookies.sqlite**_ : Contains **cookies.** [**MZCookiesView**](https://www.nirsoft.net/utils/mzcv.html) can be used in Windows to inspect this file.

*_ ** cookies.sqlite ** _：包含** cookies。 文件。
*   _**cache2/entries**_ or _**startupCache**_ : Cache data (\~350MB). Tricks like **data carving** can also be used to obtain the files saved in the cache. [MozillaCacheView](https://www.nirsoft.net/utils/mozilla\_cache\_viewer.html) can be used to see the **files saved in the cache**.

*_ ** cache2/entries ** _或_ ** startupcache ** _：缓存数据（\ 〜350mb）。 诸如**数据雕刻**之类的技巧也可用于获取缓存中保存的文件。 [mozillacacheview]（https://www.nirsoft.net/utils/mozilla/mozilla \ _cache_viewer.html）可用于查看保存在缓存中的**文件。

    Information that can be obtained:

可以获得的信息：

    * URL, fetch Count, Filename, Content type, File size, Last modified time, Last fetched time, Server Last Modified, Server Response

* URL，获取计数，文件名，内容类型，文件大小，最后修改时间，最后获取时间，服务器最后修改，服务器响应
* _**favicons.sqlite**_ : Favicons
* _**prefs.js**_ : Settings and Preferences

*_ ** prefs.js ** _：设置和首选项
* _**downloads.sqlite**_ : Old downloads database (now it's inside places.sqlite)

*_ ** downloads.sqlite ** _：旧下载数据库（现在它在inside ploces.sqlite）
* _**thumbnails/**_ : Thumbnails

*_ **缩略图/** _：缩略图
* _**logins.json**_ : Encrypted usernames and passwords

*_ ** logins.json ** _：加密用户名和密码
* **Browser’s built-in anti-phishing:** `grep 'browser.safebrowsing' ~/Library/Application Support/Firefox/Profiles/*/prefs.js`

***浏览器的内置反捕捞：**``grep'Browser.safebrowsing'〜/Library/Application Support/firfox/profiles/prefiles/prefs.js`
  * Will return “safebrowsing.malware.enabled” and “phishing.enabled” as false if the safe search settings have been disabled

*如果安全搜索设置已被禁用
* _**key4.db**_ or _**key3.db**_ : Master key?

To try to decrypt the master password, you can use [https://github.com/unode/firefox\_decrypt](https://github.com/unode/firefox\_decrypt)\

要尝试解密主密码，您可以使用[https://github.com/unode/firefox \ _decrypt]（https://github.com/unode/firefox \ _decrypt）\
With the following script and call you can specify a password file to brute force:

使用以下脚本并致电您可以指定密码文件以违反强制：

{% code title="brute.sh" %}

{％代码标题=“ brute.sh”％}
```bash
#!/bin/bash

#./brute.sh top-passwords.txt 2>/dev/null | grep -A2 -B2 "chrome:"
passfile=$1
while read pass; do
  echo "Trying $pass"
  echo "$pass" | python firefox_decrypt.py
done < $passfile
```
{% endcode %}

![](<../../../.gitbook/assets/image (417).png>)

## Google Chrome

＃＃ 谷歌浏览器

Google Chrome creates the profile inside the home of the user _**\~/.config/google-chrome/**_ (Linux), in _**C:\Users\XXX\AppData\Local\Google\Chrome\User Data\\**_ (Windows), or in \_**/Users/$USER/Library/Application Support/Google/Chrome/** \_ (MacOS).\

Google Chrome在用户家庭内部创建配置文件_ ** \〜/.config/google-chrome/** _（linux），in _ ** c：\ users \ users \ xxx \ appdata \ appdata \ local \ local \ google \ google \ chrome \ chrome \ chrome \ chrome \ 用户数据\\ ** _（Windows）或in \ _ **/user/$ user/library/application/google/chrome/** \ _（macos）。
Most of the information will be saved inside the _**Default/**_ or _**ChromeDefaultData/**_ folders inside the paths indicated before. Here you can find the following interesting files:

大多数信息将保存在_ **默认/** _或_ ** chromedefaultdata/** _ _ _ ** _ _文件夹中。 在这里，您可以找到以下有趣的文件：

* _**History**_: URLs, downloads and even searched keywords. In Windows, you can use the tool [ChromeHistoryView](https://www.nirsoft.net/utils/chrome\_history\_view.html) to read the history. The "Transition Type" column means:

*_ **历史** _：URL，下载甚至搜索的关键字。 在Windows中，您可以使用工具[ChromehistoryView]（https://www.nirsoft.net/utils/chrome \_history \_View.html）阅读历史记录。 “过渡类型”列的意思是：
  * Link: User clicked on a link

*链接：用户单击链接
  * Typed: The url was written

*键入：编写URL
  * Auto Bookmark

*自动书签
  * Auto Subframe: Add

  * Auto Subframe: Add
  * Start page: Home page
  * Form Submit: A form was filled and sent

*表格提交：填写表格并发送
  * Reloaded

*重新加载
* _**Cookies**_: Cookies. [ChromeCookiesView](https://www.nirsoft.net/utils/chrome\_cookies\_view.html) can be used to inspect the cookies.

*_ ** cookies ** _：cookie。 [ChromeCookiesView]（https://www.nirsoft.net/utils/chrome \_cookies \_View.html）可用于检查cookie。
* _**Cache**_: Cache. In Windows, you can use the tool [ChromeCacheView](https://www.nirsoft.net/utils/chrome\_cache\_view.html) to inspect the ca

*_ **缓存** _：缓存。 在Windows中，您可以使用工具[ChromeCacheview]（https://www.nirsoft.net/utils/chrome \ _cache_view.html）检查CA
* _**Bookmarks**_: Bookmarks
* _**Web Data**_: Form History

*_ **网络数据** _：形式历史记录
* _**Favicons**_: Favicons
* _**Login Data**_: Login information (usernames, passwords...)

*_ **登录数据** _：登录信息（用户名，密码...）
* _**Current Session**_ and _**Current Tabs**_: Current session data and current tabs

*_ **当前会话** _和_ **当前选项卡** _：当前会话数据和当前选项卡
* _**Last Session**_ and _**Last Tabs**_: These files hold sites that were active in the browser when Chrome was last closed.

*_ **上次会话** _和_ **最后一个选项卡** _：这些文件在Chrome上一次关闭时保存在浏览器中活跃的站点。
* _**Extensions**_: Extensions and addons folder

*_ **扩展** _：扩展和插件文件夹
* **Thumbnails** : Thumbnails

***缩略图**：缩略图
* **Preferences**: This file contains a plethora of good information such as plugins, extensions, sites using geolocation, popups, notifications, DNS prefetching, certificate exceptions, and much more. If you’re trying to research whether or not a specific Chrome setting was enabled, you will likely find that setting in here.

***首选项**：此文件包含很多好的信息，例如插件，扩展，使用地理位置，弹出式，通知，DNS预取，预取，证书异常等等。 如果您想研究是否启用了特定的镀铬设置，则可能会在此处找到该设置。
* **Browser’s built-in anti-phishing:** `grep 'safebrowsing' ~/Library/Application Support/Google/Chrome/Default/Preferences`

***浏览器的内置反捕捞：**``grep'safebrowsing'〜/library/application supports/google/chrome/default/prefiness“
  * You can simply grep for “**safebrowsing**” and look for `{"enabled: true,"}` in the result to indicate anti-phishing and malware protection is on.

*您可以简单地进行“ ** SafeBrowsing **”，然后查找``'emabled：true，true'}`}`在结果指示反向钓鱼和恶意软件保护的情况下。

## **SQLite DB Data Recovery**

## ** sqlite DB数据恢复**

As you can observe in the previous sections, both Chrome and Firefox use **SQLite** databases to store the data. It's possible to **recover deleted entries using the tool** [**sqlparse**](https://github.com/padfoot999/sqlparse) **or** [**sqlparse\_gui**](https://github.com/mdegrazia/SQLite-Deleted-Records-Parser/releases).

如您在前面的部分中可以观察到的，Chrome和Firefox都使用** sqlite **数据库存储数据。 可以使用该工具** [** sqlparse **]（https://github.com/padfoot9999/sqlparse）**恢复已删除的条目**或** [** SQLPARSE \ _GUI **]（https： //github.com/mdegrazia/sqlite-deleted-records-parser/releases）。

## **Internet Explorer 11**

Internet Explorer stores **data** and **metadata** in different locations. The metadata will allow finding the data.

Internet Explorer存储**数据**和**元数据**在不同的位置。 元数据将允许查找数据。

The **metadata** can be found in the folder `%userprofile%\Appdata\Local\Microsoft\Windows\WebCache\WebcacheVX.data` where VX can be V01, V16, or V24.\

**元数据**可以在文件夹`％userProfile％\ appdata \ local \ microsoft \ windows \ windows \ webcache \ webcache \ webcachevx.data`中找到，其中vx可以为v01，v16或v24。
In the previous folder, you can also find the file V01.log. In case the **modified time** of this file and the WebcacheVX.data file **are different** you may need to run the command `esentutl /r V01 /d` to **fix** possible **incompatibilities**.

在上一个文件夹中，您还可以找到文件v01.log。 如果此文件的修改时间**和webcachevx.data文件**不同** **您可能需要运行命令`esentutl /r v01 /d` to ** fix ** fix **可能的**无兼容** ** *。

Once **recovered** this artifact (It's an ESE database, photorec can recover it with the options Exchange Database or EDB) you can use the program [ESEDatabaseView](https://www.nirsoft.net/utils/ese\_database\_view.html) to open it. Once **opened**, go to the table named "**Containers**".

一旦**恢复** **此工件（这是一个ESE数据库，Photorec可以使用选项交换数据库或EDB恢复它）您可以使用程序[esedatabaseview]（https://wwwww.nirsoft.net.net.net.net/utils/ese \_database \ _view.html）打开它。 一旦**打开**，请转到名为“ **容器**”的表。

![](<../../../.gitbook/assets/image (446).png>)

Inside this table, you can find in which other tables or containers each part of the stored information is saved. Following that, you can find the **locations of the data** stored by the browsers and the **metadata** that is inside.

在此表中，您可以找到保存存储信息的每个部分的其他表或容器。 在此之后，您可以找到由浏览器和内部的**元数据**存储的数据**的**位置。

**Note that this table indicates metadata of the cache for other Microsoft tools also (e.g. skype)**

**请注意，此表表示其他Microsoft工具的缓存元数据（例如Skype）**

### Cache

###缓存

You can use the tool [IECacheView](https://www.nirsoft.net/utils/ie\_cache\_viewer.html) to inspect the cache. You need to indicate the folder where you have extracted the cache date.

您可以使用工具[iecacheview]（https://www.nirsoft.net/utils/ie \_cache_viewer.html）检查缓存。 您需要指示已提取缓存日期的文件夹。

#### Metadata

The metadata information about the cache stores:

有关缓存商店的元数据信息：

* Filename in the disc

*光盘中的文件名
* SecureDIrectory: Location of the file inside the cache directories

*安全级：文件内部的位置
* AccessCount: Number of times it was saved in the cache

* AccessCount：将其保存在缓存中的次数
* URL: The url origin

* URL：URL起源
* CreationTime: First time it was cached

*创建时间：第一次被缓存
* AccessedTime: Time when the cache was used

*访问时间：使用缓存的时间
* ModifiedTime: Last webpage version

*修改时间：最后一个网页版本* ExpiryTime: Time when the cache will expire

*到期时间：缓存到期的时间

#### Files

The cache information can be found in _**%userprofile%\Appdata\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5**_ and _**%userprofile%\Appdata\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\low**_

可以在_ **％userProfile％\ appdata \ local \ local \ Microsoft \ Windows \ Windows \临时Internet Files \ pontent.ie5 ** _ _ ** **％userProfile％\ appdata \ localosoft \ Microsoft \ Windows \ Windows \ Windows \临时Internet中找到缓存信息。 文件\ content.ie5 \ low ** _

The information inside these folders is a **snapshot of what the user was seeing**. The caches have a size of **250 MB** and the timestamps indicate when the page was visited (first time, creation date of the NTFS, last time, modification time of the NTFS).

这些文件夹中的信息是用户看到的**的**快照。 缓存的大小为** 250 MB **，时间戳表示该页面何时访问（第一次，NTFS的创建日期，上次，NTFS的修改时间）。

### Cookies

You can use the tool [IECookiesView](https://www.nirsoft.net/utils/iecookies.html) to inspect the cookies. You need to indicate the folder where you have extracted the cookies.

您可以使用工具[iecookiesView]（https://www.nirsoft.net/utils/iecookies.html）检查cookie。 您需要指示提取cookie的文件夹。

#### **Metadata**

The metadata information about the cookies stored:

有关存储的cookie的元数据信息：

* Cookie name in the filesystem

*文件系统中的cookie名称
* URL
* AccessCount: Number of times the cookies have been sent to the server

* AccessCount：cookie已发送到服务器的次数
* CreationTime: First time the cookie was created

*创建时间：第一次创建了cookie
* ModifiedTime: Last time the cookie was modified

*修改时间：上次修改了cookie
* AccessedTime: Last time the cookie was accessed

*访问时间：上次访问cookie
* ExpiryTime: Time of expiration of the cookie

*到期时间：饼干到期时间

#### Files

The cookies data can be found in _**%userprofile%\Appdata\Roaming\Microsoft\Windows\Cookies**_ and _**%userprofile%\Appdata\Roaming\Microsoft\Windows\Cookies\low**_

cookies数据可以在_ **％userProfile％\ appdata \ roaming \ microsoft \ windows \ windows \ cookies ** _ _ and _ **％userProfile％\ appdata \ roaming \ microsoft \ microsoft \ windows \ cookies \ cookies \ low ** _ _ _

Session cookies will reside in memory and persistent cookie in the disk.

会话cookie将位于内存中，并在磁盘中持续cookie。

### Downloads

###下载

#### **Metadata**

Checking the tool [ESEDatabaseView](https://www.nirsoft.net/utils/ese\_database\_view.html) you can find the container with the metadata of the downloads:

检查工具[esedatabaseview]（https://www.nirsoft.net/utils/ese \ _database \ _view.html）您可以找到带有下载元数据的容器：

![](<../../../.gitbook/assets/image (445).png>)

Getting the information of the column "ResponseHeaders" you can transform from hex that information and obtain the URL, the file type and the location of the downloaded file.

获取“ ResponseHeaders”列的信息您可以从十六进制信息转换，并获取已下载文件的URL，文件类型和位置。

#### Files

Look in the path _**%userprofile%\Appdata\Roaming\Microsoft\Windows\IEDownloadHistory**_

查看路径_ **％userProfile％\ appdata \ roaming \ Microsoft \ Windows \ iedownloadhistory ** _ _

### **History**

＃＃＃ **历史**

The tool [BrowsingHistoryView](https://www.nirsoft.net/utils/browsing\_history\_view.html) can be used to read the history. But first, you need to indicate the browser in advanced options and the location of the extracted history files.

可以使用工具[browsinghistoryview]（https://www.nirsoft.net/utils/browsing \_history \ _view.html）来读取历史记录。 但是首先，您需要在高级选项和提取的历史记录文件的位置中指示浏览器。

#### **Metadata**

* ModifiedTime: First time a URL is found

*修改时间：第一次找到URL
* AccessedTime: Last time

*访问时间：上次
* AccessCount: Number of times accessed

* AccessCount：访问的次数

#### **Files**

Search in _**userprofile%\Appdata\Local\Microsoft\Windows\History\History.IE5**_ and _**userprofile%\Appdata\Local\Microsoft\Windows\History\Low\History.IE5**_

在_ ** _ ** userProfile％\ appdata \ local \ Microsoft \ Windows \ Windows \ history \ history.ies.ie5 ** _和_ ** userProfile％\ appdata \ local \ Microsoft \ Microsoft \ Windows \ Windows \ history \ history \ low \ low \ stistory.ie5 ** _ _

### **Typed URLs**

### **键入URL **

This information can be found inside the registry NTDUSER.DAT in the path:

可以在注册表ntduser.dat中找到此信息：

* _**Software\Microsoft\InternetExplorer\TypedURLs**_

*_ **软件\ Microsoft \ Internet Explorer \ typedurls ** _ _
  * Stores the last 50 URLs typed by the user

*存储用户键入的最后50个URL
* _**Software\Microsoft\InternetExplorer\TypedURLsTime**_

*_ **软件\ Microsoft \ Internet Explorer \ typedurlstime ** _ _
  * last time the URL was typed

*上次URL键入

## Microsoft Edge

## Microsoft Edge

For analyzing Microsoft Edge artifacts all the **explanations about cache and locations from the previous section (IE 11) remain valid** with the only difference that the base locating, in this case, is _**%userprofile%\Appdata\Local\Packages**_ (as can be observed in the following paths):

为了分析Microsoft Edge伪像，有关缓存的所有**说明和上一节（即11）的位置（即11）仍然有效** **，在这种情况下，基本定位是_ **％userProfile％\ appdata \ local的唯一区别 \ packages ** _（可以在以下路径中观察到）：

* Profile Path: _**C:\Users\XX\AppData\Local\Packages\Microsoft.MicrosoftEdge\_XXX\AC**_

*配置文件路径：_ ** c：\ users \ xx \ appdata \ local \ packages \ microsoft.microsoft. \ _xxx \ ac ** _ _
* History, Cookies and Downloads: _**C:\Users\XX\AppData\Local\Microsoft\Windows\WebCache\WebCacheV01.dat**_

*历史记录，cookie和下载：_ ** c：\ users \ xx \ appdata \ local \ local \ microsoft \ windows \ windows \ webcache \ webcachev01.dat ** _ _
* Settings, Bookmarks, and Reading List: _**C:\Users\XX\AppData\Local\Packages\Microsoft.MicrosoftEdge\_XXX\AC\MicrosoftEdge\User\Default\DataStore\Data\nouser1\XXX\DBStore\spartan.edb**_

*设置，书签和阅读列表：_ ** c：\用户\ xx \ appdata \ local \ packages \ microsoft.microsoft.microsoftedge \ _xxx \ ac \ ac \ ac \ microsoftEdge \ microsoftEdge \ user \ user \ user \ default \ datastore \ datastore \ datastore \ dataStore \ datastore \ dataastore \ data \ nouser1 \ nouser1 \ xxx \ dbartan .edb ** _
* Cache: _**C:\Users\XXX\AppData\Local\Packages\Microsoft.MicrosoftEdge\_XXX\AC#!XXX\MicrosoftEdge\Cache**_

*缓存：_ ** c：\ users \ xxx \ appdata \ local \ packages \ microsoft.microsoftEdge \ _xxx \ ac＃！xxx \ microsoftEdge \ microsoftEdge \ cache ** _ _ _ _ _ _
* Last active sessions: _**C:\Users\XX\AppData\Local\Packages\Microsoft.MicrosoftEdge\_XXX\AC\MicrosoftEdge\User\Default\Recovery\Active**_

*上次活动会话：_ ** c：\ users \ xx \ appdata \ local \ packages \ microsoft.microsoftEdge \ _xxx \ ac \ ac \ ac \ microsoftEdge \ microsoftEdge \ user \ user \ user \ default \ recureent \ recuce

## **Safari**

The databases can be found in `/Users/$User/Library/Safari`

数据库可以在“/user/$ user/library/safari”中找到

* **History.db**: The tables `history_visits` _and_ `history_items` contains information about the history and timestamps.

*** history.db **：表`history_visits` _ and_'thistory_items`包含有关历史记录和时间戳的信息。
  * `sqlite3 ~/Library/Safari/History.db "SELECT h.visit_time, i.url FROM history_visits h INNER JOIN history_items i ON h.history_item = i.id"`

*`s sqlite3〜/library/safari/history.db“选择h.visit_time，i.url from stistory_visits h insion_items i history_items i on h.history_item = i.id”
* **Downloads.plist**: Contains the info about the downloaded files.

*** downloads.plist **：包含有关下载文件的信息。
* **Book-marks.plis**t: URLs bookmarked.
* **TopSites.plist**: List of the most visited websites that the user browses to.

*** topsites.plist **：用户浏览最访问量最多的网站的列表。
* **Extensions.plist**: To retrieve an old-style list of Safari browser extensions.

*** Extensions.plist **：检索Safari浏览器扩展名的老式列表。
  * `plutil -p ~/Library/Safari/Extensions/Extensions.plist| grep "Bundle Directory Name" | sort --ignore-case`

*`plutil -p〜/library/safari/extensions/extensions.plist | grep“捆绑目录名称” | 排序 -  ignore-case`
  * `pluginkit -mDvvv -p com.apple.Safari.extension`
* **UserNotificationPermissions.plist**: Domains that are allowed to push notifications.

*** usernotificationpermissions.plist **：允许推动通知的域。
  * `plutil -p ~/Library/Safari/UserNotificationPermissions.plist | grep -a3 '"Permission" => 1'`

*``plutil -p〜/library/safari/usernotification permissions.plist | grep -a3'“许可” => 1'```
* **LastSession.plist**: Tabs that were opened the last time the user exited Safari.

*** lastsession.plist **：上次用户退出Safari时打开的标签。
  * `plutil -p ~/Library/Safari/LastSession.plist | grep -iv sessionstate`
* **Browser’s built-in anti-phishing:** `defaults read com.apple.Safari WarnAboutFraudulentWebsites`

***浏览器的内置反捕捞：**``默认值读取com.apple.safari warnaboutfroudultulenwebsites`
  * The reply should be 1 to indicate the setting is active

*答复应为1表示设置处于活动状态

## Opera

The databases can be found in `/Users/$USER/Library/Application Support/com.operasoftware.Opera`

数据库可以在`/user/$ user/library/application supports/com.operasoftware.opera`中找到

Opera **stores browser history and download data in the exact same format as Google Chrome**. This applies to the file names as well as the table names.

Opera **存储浏览器历史记录，并以与Google Chrome **完全相同的格式下载数据。 这适用于文件名以及表名。

* **Browser’s built-in anti-phishing:** `grep --color 'fraud_protection_enabled' ~/Library/Application Support/com.operasoftware.Opera/Preferences`

***浏览器的内置反捕捞：**``grep-color'fraud_protection_enabled'〜/library/application supports/com.operasoftware.opera/preverences`
  * **fraud\_protection\_enabled** should be **true**

***欺诈\ _ protection \ _enabled **应该** true **

{% hint style="danger" %}
<img src="../../../.gitbook/assets/image (307).png" alt="" data-size="original">

<img src =“../../../。gitbook/assets/image（307）.png“ alt =”“ data-size =” ointers =“ ointers”>

Through Security Skills as a Service, we help organizations to **defend against the Dark Hacking Arts**. Security Skills as a Service is an offensive cybersecurity consultancy model that combines an Intelligent Platform with the top-class, globally distributed, offensive security engineers, delivering **high-quality penetration testing results. Security Hubs** bring together offensive penetration testing tactics with human behavioral science, providing real-time insights into threat actors' tradecraft and a **complete assessment of any risks**.

通过安全技能作为服务，我们帮助组织**防御黑暗黑客艺术**。 安全技能作为服务是一种进攻性网络安全咨询模型，将智能平台与顶级，全球分布式，进攻性安全工程师结合在一起，提供**高质量的渗透测试结果。 安全枢纽**将进攻性渗透测试策略与人类行为科学结合在一起，提供对威胁参与者贸易克罗夫特（Tradecraft）的实时见解，并对任何风险**进行完整评估。

{% embed url="https://securityhubs.io/" %}
{% endhint %}

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
