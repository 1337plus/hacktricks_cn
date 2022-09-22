

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
Do you use **Hacktricks every day**? Did you find the book **very** **useful**? Would you like to **receive extra help** with cybersecurity questions? Would you like to **find more and higher quality content on Hacktricks**?  

您每天使用** hacktricks **吗？ 您是否发现这本书** ** **有用**？ 您想**在网络安全问题上获得额外的帮助**吗？ 您想**在hacktricks上找到更多和更高质量的内容**吗？
[**Support Hacktricks through github sponsors**](https://github.com/sponsors/carlospolop) **so we can dedicate more time to it and also get access to the Hacktricks private group where you will get the help you need and much more!**

[**通过github赞助商**支持hacktricks **]（https://github.com/sponsors/carlospolop）**，因此我们可以花更多的时间来访问它，还可以访问hacktricks私人小组，您将获得帮助。 需要等等！**
{% endhint %}

If you want to know about my **latest modifications**/**additions** or you have **any suggestion for HackTricks** or **PEASS**, - **Join the** [**💬**](https://emojipedia.org/speech-balloon/)[**Discord group**](https://discord.gg/hRep4RUj7f) or the [**telegram group**](https://t.me/peass), or **follow** me on **Twitter** [**🐦**](https://github.com/carlospolop/hacktricks/tree/7af18b62b3bdc423e11444677a6a73d4043511e9/[https:/emojipedia.org/bird/README.md)[**@carlospolopm**](https://twitter.com/carlospolopm)**.**  

如果您想知道我的**最新修改**/**添加**，或者您对hacktricks **或** Peass **有任何建议， -  **加入** [** ** ** ** ** ]（https://emojipedia.org/speech-balloon/）[** discord group **]（https://discord.gg/hrep4ruj7f）或[** telegram group **]（https：// tttps：// tttps：// t 。 /bird/readme.md) [@carllospolopmxed]（
If you want to **share some tricks with the community** you can also submit **pull requests** to [**https://github.com/carlospolop/hacktricks**](https://github.com/carlospolop/hacktricks) that will be reflected in this book and don't forget to **give ⭐** on **github** to **motivate** **me** to continue developing this book.

如果您想与社区分享一些技巧**，也可以提交**拉申请** **给[** https：//github.com/carloppolop/hacktrickshephy]（https://github.com） /carlospolop/hacktricks）将反映在本书中，不要忘记**给** github **给** **激励** **我**继续开发这本书。

# Assets discoveries

> So you were said that everything belonging to some company is inside the scope, and you want to figure out what this company actually owns.

>因此，您被说过，属于某些公司的一切都在范围内，您想弄清楚该公司实际拥有的东西。

The goal of this phase is to obtain all the **companies owned by the main company** and then all the **assets** of these companies. To do so, we are going to:

此阶段的目的是获取主要公司拥有的所有**公司，然后获得这些公司的所有**资产**。 为此，我们将要：

1. Find the acquisitions of the main company, this will give us the companies inside the scope.

1.找到主要公司的收购，这将为我们提供范围内的公司。
2. Find the ASN \(if any\) of each company, this will give us the IP ranges owned by each company

2.找到每个公司的ASN \（如果有），这将为我们提供每个公司拥有的IP范围
3. Use reverse whois lookups to search for other entries \(organisation names, domains...\) related to the first one \(this can be done recursively\)

3.使用反向WHOIS查找来搜索与第一个\相关的其他条目（组织名称，域... \）（可以递归\）
4. Use other techniques like shodan `org`and `ssl`filters to search for other assets \(the `ssl` trick can be done recursively\).

4.使用其他技术，例如shodan`org`和`ssl` -filters搜索其他资产\（可以递归地完成``ssl`技巧''。

## Acquisitions

First of all, we need to know which **other companies are owned by the main company**.  

首先，我们需要知道其他公司归主要公司**所有**。
One option is to visit [https://www.crunchbase.com/](https://www.crunchbase.com/), **search** for the **main company**, and **click** on "**acquisitions**". There you will see other companies acquired by the main one.  

一种选择是访问[https://www.crunchbase.com/]（ 在“ **获取**”上。 在那里，您会看到其他公司收购的其他公司。
Other option is to visit the **Wikipedia** page of the main company and search for **acquisitions**.

另一个选择是访问主要公司的** Wikipedia **页面，并搜索**收购**。

> Ok, at this point you should know all the companies inside the scope. Lets figure out how to find their assets.

>好吧，在这一点上，您应该知道范围内的所有公司。 让我们弄清楚如何找到他们的资产。

## ASNs

An autonomous system number \(**ASN**\) is a **unique number** assigned to an **autonomous system** \(AS\) by the **Internet Assigned Numbers Authority \(IANA\)**.  

一个自主系统编号\（** asn ** \）是一个**唯一号码**，由** Internet分配的数字授权\（iana \）**分配给**自治系统** \（as \）** 。
An **AS** consists of **blocks** of **IP addresses** which have a distinctly defined policy for accessing external networks and are administered by a single organisation but may be made up of several operators.

** AS **由** IP地址**的**块**组成，这些块**具有明显定义的访问外部网络的策略，并由一个组织管理，但可以由多个运营商组成。

It's interesting to find if the **company have assigned any ASN** to find its **IP ranges.** It will be interested to perform a **vulnerability test** against all the **hosts** inside the **scope** and **look for domains** inside these IPs.  

有趣的是找到**公司是否已分配任何Asn **来找到其** IP范围。 范围**和**在这些IP中寻找域**。
You can search by** company name**, by** IP **or by** domain **in** [**https://bgp.he.net/**](https://bgp.he.net/)**.  

您可以通过** company name **，通过** ip **或** domain ** in ** [** https：//bgp.he.net/pehand in ** in ** domain **]（https：// bgp。 he.net/)**。
Depending on the region of the company this links could be useful to gather more data:** [**AFRINIC**](https://www.afrinic.net/) **\(Africa\),** [**Arin**](https://www.arin.net/about/welcome/region/)**\(North America\),** [**APNIC**](https://www.apnic.net/) **\(Asia\),** [**LACNIC**](https://www.lacnic.net/) **\(Latin America\),** [**RIPE NCC**](https://www.ripe.net/) **\(Europe\). Anyway, probably all the** useful information **\(IP ranges and Whois\)** appears already in the first link**.

根据公司的区域，此链接对于收集更多数据可能很有用：** [** Afrinic **]（https://www.afrinic.net/）** \（africa \），** [** [** *arin **]（https://www.arin.net/about/welcome/region/）** \（北美\），** [** apnic **]（https：//www.apnic。 net/）** \（asia \），** [** lacnic **]（https://www.lacnic.net/）** \（拉丁美洲\），** [** ripe ncc ** ]（https://www.ripe.net/）** \（欧洲\）。 无论如何，可能所有有用的信息** \（ip范围和whois \）**已经出现在第一个链接中**。

```bash
#You can try "automate" this with amass, but it's not very recommended
amass intel -org tesla
amass intel -asn 8911,50313,394161
```

You can find the IP ranges of an organisation also using [http://asnlookup.com/](http://asnlookup.com/) \(it has free API\).  

您可以使用[http://asnlookup.com/]（
You can fins the IP and ASN of a domain using [http://ipv4info.com/](http://ipv4info.com/).

您可以使用[http://ipv4info.com/]（http://ipv4info.com/找到域的IP和ASN。

## Looking for vulnerabilities

##寻找漏洞

At this point we known **all the assets inside the scope**, so if you are allowed you could launch some **vulnerability scanner** \(Nessus, OpenVAS\) over all the hosts.  

在这一点上，我们知道范围内的所有资产**，因此，如果允许您在所有主机上启动一些**漏洞扫描仪** \（nessus，openvas \）。
Also, you could launch some [**port scans**](pentesting/pentesting-network/#discovering-hosts-from-the-outside) or use services like** shodan **to find** open ports **and depending on what you find you should** take a look in this book to how to pentest several possible service running**.  

此外，您可以启动一些[**端口扫描**]（penterting/penteTing-network/＃Discovering-the-the-the-Outside）或使用** Shodan **之类的服务来找到** open open ports **和 根据您的发现，您应该**在这本书中查看如何满足几个可能的服务**。
Also, It could be worth it to mention that you can also prepare some** default username **and** passwords **lists and try to** bruteforce** services with [https://github.com/x90skysn3k/brutespray](https://github.com/x90skysn3k/brutespray).

另外，值得一提的是，您还可以准备一些默认用户名**和**密码**列表，然后尝试使用[https://github.com/x90skysn3k/brutespray ** bruteforce **服务**服务 ]（https://github.com/x90skysn3k/brutespray）。

# Domains

> We know all the companies inside the scope and their assets, it's time to find the domains inside the scope.

>我们知道范围内的所有公司及其资产，是时候找到范围内的域名了。

_Please, note that in the following purposed techniques you can also find subdomains and that information shouldn't be underrated._

请注意，在以下建议的技术中，您还可以找到子域，并且不应低估信息。

First of all you should look for the **main domain**\(s\) of each company. For example, for _Tesla Inc._ is going to be _tesla.com_.

首先，您应该寻找每个公司的**主域** \（s \）。 例如，对于_tesla Inc._，将为_tesla.com_。

## Reverse DNS

As you have found all the IP ranges of the domains you could try to perform **reverse dns lookups** on those **IPs to find more domains inside the scope**. Try to use some dns server of the victim or some well-known dns server \(1.1.1.1, 8.8.8.8\)

当您发现域的所有IP范围时，您可以尝试在这些** IP上执行**反向DNS查找**，以在范围内找到更多域**。 尝试使用受害者的某些DNS服务器或一些知名的DNS服务器\（1.1.1.1，8.8.8.8 \）

```bash
dnsrecon -r <DNS Range> -n <IP_DNS>   #DNS reverse of all of the addresses
dnsrecon -d facebook.com -r 157.240.221.35/24 #Using facebooks dns
dnsrecon -r 157.240.221.35/24 -n 1.1.1.1 #Using cloudflares dns
dnsrecon -r 157.240.221.35/24 -n 8.8.8.8 #Using google dns
```

For this to work, the administrator has to enable manually the PTR.  

为此，管理员必须手动启用PTR。
You can also use a online tool for this info: [http://ptrarchive.com/](http://ptrarchive.com/)

您还可以使用在线工具进行此信息：[http://ptrarchive.com/]（http://ptrarchive.com/）

## Reverse Whois \(loop\)

Inside a **whois** you can find a lot of interesting **information** like **organisation name**, **address**, **emails**, phone numbers... But which is even more interesting is that you can find **more assets related to the company** if you perform **reverse whois lookups by any of those fields** \(for example other whois registries where the same email appears\).  

在一个** whois **内部，您可以找到很多有趣的**信息**喜欢**组织名称**，**地址**，**电子邮件**，电话号码...但是更有趣 是，如果您执行**反向WHOIS查找** ** \（例如，同一电子邮件出现相同的电子邮件\）。
You can use online tools like:

* [https://viewdns.info/reversewhois/](https://viewdns.info/reversewhois/) - **Free**
* [https://domaineye.com/reverse-whois](https://domaineye.com/reverse-whois)  - **Free**
* [https://www.reversewhois.io/](https://www.reversewhois.io/)  - **Free**
* [https://www.whoxy.com/](https://www.whoxy.com/) - **Free** web, not free API.

*[https://www.whoxy.com/]（
* [http://reversewhois.domaintools.com/](http://reversewhois.domaintools.com/) - Not free

* [http://reversewhois.domaintools.com/]（http://reversewhois.domaintools.com/）
* [https://drs.whoisxmlapi.com/reverse-whois-search](https://drs.whoisxmlapi.com/reverse-whois-search) - Not Free \(only **100 free** searches\)

*[https://drs.whoisxmlapi.com/reverse-whois-search]（
* [https://www.domainiq.com/](https://www.domainiq.com/) - Not Free

You can automate this task using [**DomLink** ](https://github.com/vysecurity/DomLink)\(requires a whoxy API key\).  

您可以使用[** domlink **]自动化此任务（https://github.com/vysecurity/domlink）\（需要一个whoxy api键\）。
You can also perform some automatic reverse whois discovery with [amass](https://github.com/OWASP/Amass): `amass intel -d tesla.com -whois`

您还可以使用[amass]（https://github.com/owasp/amass）执行一些自动反向WHOIS发现：`amass intel -d tesla.com -whois'whois'

**Note that you can use this technique to discover more domain names every time you find a new domain.**

**请注意，您可以使用此技术在每次找到新域中发现更多域名。**

## Trackers

##跟踪器

If find the **same ID of the same tracker** in 2 different pages you can suppose that **both pages** are **managed by the same team**.  

如果在2个不同页面中找到同一跟踪器**的**相同的ID，则可以假设**这两个页面**由同一团队**管理**。
For example, if you see the same **Google Analytics ID** or the same **Adsense ID** on several pages.

例如，如果您看到相同的** Google Analyticsics ID **或几个页面上的相同** adsense ID **。

There are some pages that let you search by these trackers and more:

有一些页面可让您通过这些跟踪器搜索等等：

* [**BuiltWith**](https://builtwith.com/)

*[** buildwith **]（https://builtwith.com/）
* [**Sitesleuth**](https://www.sitesleuth.io/)
* [**Publicwww**](https://publicwww.com/)
* [**SpyOnWeb**](http://spyonweb.com/)

## **Favicon**

Did you know that we can find related domains and sub domains to our target by looking for the same favicon icon hash? This is exactly what [favihash.py](https://github.com/m4ll0k/Bug-Bounty-Toolz/blob/master/favihash.py) tool made by [@m4ll0k2](https://twitter.com/m4ll0k2) does. Here’s how to use it:

您是否知道我们可以通过寻找相同的Favicon图标哈希来找到与我们的目标相关的域和子域？ 这正是[favihash.py]（https://github.com/m4ll0k/bug-bounty-toolz/blob/master/master/favihash.py）工具由[@m4ll0k2]（httpps://ttps://twitter.com/ m4ll0k2）。 这是使用它的方法：

```bash
cat my_targets.txt | xargs -I %% bash -c 'echo "http://%%/favicon.ico"' > targets.txt
python3 favihash.py -f https://target/favicon.ico -t targets.txt -s
```

![favihash - discover domains with the same favicon icon hash](https://www.infosecmatter.com/wp-content/uploads/2020/07/favihash.jpg)

！[favihash-使用相同的favicon图标哈希发现域]（https://www.infosecmatter.com/wp-content/uploads/2020/07/favihash.jpg）

Simply said, favihash will allow us to discover domains that have the same favicon icon hash as our target.

简而言之，Favihash将使我们能够发现具有与我们的目标相同的Favicon图标哈希的域。

## Other ways

＃＃ 其他方法

**Note that you can use this technique to discover more domain names every time you find a new domain.**

**请注意，您可以使用此技术在每次找到新域中发现更多域名。**

### Shodan

As you already know the name of the organisation owning the IP space. You can search by that data in shodan using: `org:"Tesla, Inc."` Check the found hosts for new unexpected domains in the TLS certificate.

您已经知道拥有IP空间的组织的名称。 您可以使用以下方式在Shodan中搜索该数据：`org：“ Tesla，Inc.。”``检查发现的主机是否在TLS证书中找到新的意外域。

You could access the **TLS certificate** of the main web page, obtain the **Organisation name** and then search for that name inside the **TLS certificates** of all the web pages known by **shodan** with the filter : `ssl:"Tesla Motors"`

您可以访问主网页的** tls证书**，获取**组织名称**，然后在** Shodan **已知的所有网页的** tls证书**中搜索该名称** 使用过滤器：`ssl：“ Tesla Motors”`````

### Google

Go to the main page an find something that identifies the company, like the copyright \("Tesla © 2020"\). Search for that in google or other browsers to find possible new domains/pages.

转到主页一个找到可以识别公司的东西，例如版权\（“ Tesla©2020” \）。 在Google或其他浏览器中搜索它，以查找可能的新域/页面。

### Assetfinder

[**Assetfinder** ](https://github.com/tomnomnom/assetfinder)is a tool that look for **domains related** with a main domain and **subdomains** of them, pretty amazing.

[** AssetFinder **]（https://github.com/tomnomnom/assetfinder）是一种工具，它可以查找与主要域相关的**域与它们相关的**和**子域**，非常惊人。

## Looking for vulnerabilities

##寻找漏洞

Check for some [domain takeover](pentesting-web/domain-subdomain-takeover.md#domain-takeover). Maybe some company is **using some a domain** but they **lost the ownership**. Just register it \(if cheap enough\) and let know the company.

检查一些[域接管]（penterting-web/domain-subdomain-takeover.md＃domain-takeover）。 也许某些公司正在使用某个域**，但他们**失去了所有权**。 只需注册它\（如果足够便宜），然后知道公司。

If you find any **domain with an IP different** from the ones you already found in the assets discovery, you should perform a **basic vulnerability scan** \(using Nessus or OpenVAS\) and some [**port scan**](pentesting/pentesting-network/#discovering-hosts-from-the-outside) with **nmap/masscan/shodan**. Depending on which services are running you can find in **this book some tricks to "attack" them**.  

如果您发现与在资产发现中已经找到的IP不同**的任何**域，则应执行**基本漏洞扫描** \（使用nessus或openvas \）和一些[**端口扫描 **]（penting/penterting-network/＃unding-the-the-the-outside）使用** nmap/masscan/shodan **。 根据正在运行的服务，您可以在**这本书中找到一些技巧来“攻击”它们**。
_Note that sometimes the domain is hosted inside an IP that is not controlled by the client, so it's not in the scope, be careful._

_注意，有时该域托管在不受客户端不受控制的IP中，因此它不在范围中，请小心。

# Subdomains

> We know all the companies inside the scope, all the assets of each company and all the domains related to the companies.

>我们知道范围内的所有公司，每个公司的所有资产以及与公司有关的所有领域。

It's time to find all the possible subdomains of each found domain.

是时候找到每个发现域的所有可能子域了。

## DNS

Let's try to get **subdomains** from the **DNS** records. We should also try for **Zone Transfer** \(If vulnerable, you should report it\).

让我们尝试从** dns **记录中获取**子域**。 我们还应该尝试**区域传输** \（如果脆弱，您应该报告\）。

```bash
dnsrecon -a -d tesla.com
```

## OSINT

The fastest way to obtain a lot of subdomains is search in external sources. I'm not going to discuss which sources are the bests and how to use them, but you can find here several utilities: [https://pentester.land/cheatsheets/2018/11/14/subdomains-enumeration-cheatsheet.html](https://pentester.land/cheatsheets/2018/11/14/subdomains-enumeration-cheatsheet.html)

获得许多子域的最快方法是在外部来源中进行搜索。 我不会讨论哪些来源是最好的以及如何使用它们，但是您可以在这里找到几个公用事业：[https：//pentester.land/cheatsheets/2018/11/11/14/subdomains-enumeration-enumeration-cheatsheet.html ]（https://pentester.land/cheatsheets/2018/11/14/subdomains-enumeration-cheatsheet.html）

A really good place to search for subdomains is [https://crt.sh/](https://crt.sh/).

寻找子域的一个非常好的地方是[https://crt.sh/]（https://crt.sh/）。

The most used tools are [**Amass**](https://github.com/OWASP/Amass)**,** [**subfinder**](https://github.com/projectdiscovery/subfinder)**,** [**findomain**](https://github.com/Edu4rdSHL/findomain/)**,** [**OneForAll**](https://github.com/shmilylty/OneForAll/blob/master/README.en.md)**,** [**assetfinder**](https://github.com/tomnomnom/assetfinder)**,** [**Sudomy**](https://github.com/Screetsec/Sudomy)**.** I would recommend to start using them configuring the API keys, and then start testing other tools or possibilities.

最常用的工具是[** amass **]（https://github.com/owasp/amass）**，** [** subfinder **]（https://github.com/projectdiscovery/subfinder） **，** [** findomain **]（https://github.com/edu4rdshl/findomain/） /blob/master/readme.en.md)*********** [** AssetFinder **]（https://github.com/tomnomnom/assetfinder）**，** [** sustomy **]（https ：//github.com/screetsec/sudomy）**。**我建议开始使用它们配置API键，然后开始测试其他工具或可能性。

```bash
amass enum [-active] [-ip] -d tesla.com
./subfinder-linux-amd64 -d tesla.com [-silent]
./findomain-linux -t tesla.com [--quiet]
python3 oneforall.py --target tesla.com [--dns False] [--req False] run
assetfinder --subs-only <domain>
```

Another possibly interesting tool is [**gau**](https://github.com/lc/gau)**.** It fetches known URLs from AlienVault's Open Threat Exchange, the Wayback Machine, and Common Crawl for any given domain.

另一个可能有趣的工具是[** gau **]（https://github.com/lc/gau）**。 领域。

### [chaos.projectdiscovery.io](https://chaos.projectdiscovery.io/#/)

### [chaos.projectdiscovery.io]（https://chaos.projectdiscovery.io/#/）

This project offers for **free all the subdomains related to bug-bounty programs**. You can access this data also using [chaospy](https://github.com/dr-0x0x/chaospy) or even access the scope used by this project [https://github.com/projectdiscovery/chaos-public-program-list](https://github.com/projectdiscovery/chaos-public-program-list)

该项目提供**免费的所有与Bug-Bounty程序有关的子域**。 您还可以使用[chaospy]（https://github.com/dr-0x0x/chaospy）访问此数据，甚至可以访问此项目使用的范围[https://github.com/projectdiscovery/chaos-covery/chaos-public-public-public-public-public-public-public-public -list]（https：//github.com/projectdiscovery/chaos-public-program-list）

You could also find subdomains scrapping the web pages and parsing them \(including JS files\) searching for subdomains using [SubDomainizer](https://github.com/nsonaniya2010/SubDomainizer) or [subscraper](https://github.com/Cillian-Collins/subscraper).

您还可以找到子域废弃网页并解析它们\（包括JS文件\），使用[subdomainizer]（https://github.com/nsoniya2010/subdomainizer）或[subscraper]（https：// github）搜索子域。 COM/CILLIAN-COLLINS/用户）。

### RapidDNS

Quickly find subdomains using [RapidDNS](https://rapiddns.io/) API \(from [link](https://twitter.com/Verry__D/status/1282293265597779968)\):

快速使用[RapidDNS]（https://rapiddns.io/）API \（来自[link]（https://twitter.com/verry __d/status/1282293265597779968）\）快速找到子域。

```text
rapiddns(){
curl -s "https://rapiddns.io/subdomain/$1?full=1" \
 | grep -oP '_blank">\K[^<]*' \
 | grep -v http \
 | sort -u
}
```

### Shodan

You found **dev-int.bigcompanycdn.com**, make a Shodan query like the following:

您发现** dev-int.bigcompanycdn.com **，对以下内容进行shodan查询：

* http.html:”dev-int.bigcompanycdn.com”

* http.html：“ dev-int.bigcompanycdn.com”
* http.html:”[https://dev-int-bigcompanycdn.com”](https://dev-int-bigcompanycdn.com”)

## DNS Brute force

Let's try to find new **subdomains** brute-forcing DNS servers using possible subdomain names.  

让我们尝试使用可能的子域名找到新的**子域**野蛮的DNS服务器。
The most recommended tools for this are [**massdns**](https://github.com/blechschmidt/massdns)**,** [**gobuster**](https://github.com/OJ/gobuster)**,** [**aiodnsbrute**](https://github.com/blark/aiodnsbrute) **and** [**shuffledns**](https://github.com/projectdiscovery/shuffledns). The first one is faster but more prone to errors \(you should always check for **false positives**\) and the second one **is more reliable** \(always use gobuster\).

最推荐的工具是[** massdns **]（https://github.com/blechschmidt/massdns）**，** [** gobuster **]（https://github.com/oj/ gobuster）**，** [** aiodnsbrute **]（https://github.com/blark/blark/aiodnsbrute）**和** [** shuffledns **] 洗牌）。 第一个更快但更容易出现错误\（您应该始终检查** false Prientives ** \），而第二个**更可靠** \（始终使用Gobuster \）。

For this action you will need some common subdomains lists like:

对于此操作，您需要一些常见的子域列表，例如：

* [https://gist.github.com/jhaddix/86a06c5dc309d08580a018c66354a056](https://gist.github.com/jhaddix/86a06c5dc309d08580a018c66354a056)
* [https://github.com/pentester-io/commonspeak](https://github.com/pentester-io/commonspeak)

{% code title="Gobuster bruteforcing dns" %}

{％代码标题=“ Gobuster bruteforcing DNS”％}
```bash
gobuster dns -d mysite.com -t 50 -w subdomains.txt
```
{% endcode %}

For **massdns** you will need to pass as argument the file will all the **possible well formed subdomains** you want to bruteforce and list of DNS resolvers to use. Some projects that use massdns as base and provides better results by checking massdns results are [**shuffledns**](https://github.com/projectdiscovery/shuffledns) **and** [**puredns**](https://github.com/d3mondev/puredns)**.**

对于** massdns **，您将需要传递，因为参数将所有**可能形成的子域**您要使用bruteforce和DNS解析器列表。 一些使用MassDNS作为基础并通过检查MassDNS结果提供更好结果的项目是[** Shuffledns **]（https://github.com/projectdiscovery/shuffledns）**和** [** puredns **]（https） ：//github.com/d3mondev/puredns）**。**

```bash
sed 's/$/.domain.com/' subdomains.txt > bf-subdomains.txt
./massdns -r resolvers.txt -w /tmp/results.txt bf-subdomains.txt
grep -E "tesla.com. [0-9]+ IN A .+" /tmp/results.txt

shuffledns -d example.com -list example-subdomains.txt -r resolvers.txt
puredns bruteforce all.txt domain.com
```

Note how these tools require a **list of IPs of public DNSs**. If these public DNSs are malfunctioning \(DNS poisoning for example\) you will get bad results. In order to generate a list of trusted DNS resolvers you can download the resolvers from [https://public-dns.info/nameservers-all.txt](https://public-dns.info/nameservers-all.txt) and use [**dnsvalidator**](https://github.com/vortexau/dnsvalidator) to filter them.

请注意，这些工具如何需要公共DNSS **的IPS列表。 如果这些公共DNS发生故障\（例如，DNS中毒），您将获得不好的结果。 为了生成可信赖的DNS解析器列表，您可以从[https://public-dns.info/nameservers-all.al.txt]（ 并使用[** dnsvalidator **]（https://github.com/vortexau/dnsvalidator）进行过滤它们。

## VHosts

### IP VHosts

You can find some VHosts in IPs using [HostHunter](https://github.com/SpiderLabs/HostHunter)

您可以使用[hosthunter]（https://github.com/spiderlabs/hosthunter）在IPS中找到一些VHOST

### Brute Force

If you suspect that some subdomain can be hidden in a web server you could try to brute force it:

如果您怀疑某些子域可以隐藏在Web服务器中，则可以尝试强迫它：

```bash
gobuster vhost -u https://mysite.com -t 50 -w subdomains.txt

wfuzz -c -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-20000.txt --hc 400,404,403 -H "Host: FUZZ.example.com" -u http://example.com -t 100

#From https://github.com/allyshka/vhostbrute
vhostbrute.py --url="example.com" --remoteip="10.1.1.15" --base="www.example.com" --vhosts="vhosts_full.list"
```

{% hint style="info" %}

{％提示样式=“ info”％}
With this technique you may even be able to access internal/hidden endpoints.

使用此技术，您甚至可以访问内部/隐藏端点。
{% endhint %}

## CORS Brute Force

## Cors蛮力

Sometimes you will find pages that only return the header _**Access-Control-Allow-Origin**_ when a valid domain/subdomain is set in the _**Origin**_ header. In these scenarios, you can abuse this behavior to **discover** new **subdomains**.

有时，您会发现仅返回标题_ **访问控制的页面** _ _ _当有效域/子域设置为_ ** origin ** _ header中时。 在这些情况下，您可以滥用这种行为，以发现**新**子域**。

```bash
ffuf -w subdomains-top1million-5000.txt -u http://10.10.10.208 -H 'Origin: http://FUZZ.crossfit.htb' -mr "Access-Control-Allow-Origin" -ignore-body
```

## DNS Brute Force v2

Once you have finished looking for subdomains you can use [**dnsgen** ](https://github.com/ProjectAnte/dnsgen)and [**altdns**](https://github.com/infosec-au/altdns) to generate possible permutations of the discovered subdomains and use again **massdns** and **gobuster** to search new domains.

找到子域后，您可以使用[** dnsgen **]（https://github.com/project.com/projectante/dnsgen）和[** altdns **]（https：//github.com/infosec-com/infosec-au /altdns）为了生成发现的子域的可能排列，并再次使用** massdns **和** Gobuster **搜索新域。

## Buckets Brute Force

##桶蛮力

While looking for **subdomains** keep an eye to see if it is **pointing** to any type of **bucket**, and in that case [**check the permissions**](pentesting/pentesting-web/buckets/)**.**  

在寻找**子域的同时，**请注意它是否**指向任何类型的**桶**，在这种情况下[**检查权限**] /buckets/)**********************
Also, as at this point you will know all the domains inside the scope, try to [**brute force possible bucket names and check the permissions**](pentesting/pentesting-web/buckets/).

另外，在这一点上，您将知道范围内的所有域，请尝试[**蛮力可能的存储桶名称并检查权限**]（penting/pentesting/pentesting-web/buckets/）。

## Monitorization

You can **monitor** if **new subdomains** of a domain are created by monitoring the **Certificate Transparency** Logs [**sublert** ](https://github.com/yassineaboukir/sublert/blob/master/sublert.py)does.

您可以**监视**如果**新的子域**是通过监视**证书透明度** logs [** sublert **]（https://github.com/yassineaboukir/sublert/sublert/blob）创建域的新子域** /master/sublert.py)does。

## Looking for vulnerabilities

##寻找漏洞

Check for possible [**subdomain takeovers**](pentesting-web/domain-subdomain-takeover.md#subdomain-takeover).  

检查可能的[**子域收购**]（penterting-web/domain-subdomain-takeover.md＃子域takebover）。
If the **subdomain** is pointing to some **S3 bucket**, [**check the permissions**](pentesting/pentesting-web/buckets/).

如果**子域**指向一些** s3桶**，则[**检查权限**]（penterting/pentesting/pentesting-web/buckets/）。

If you find any **subdomain with an IP different** from the ones you already found in the assets discovery, you should perform a **basic vulnerability scan** \(using Nessus or OpenVAS\) and some [**port scan**](pentesting/pentesting-network/#discovering-hosts-from-the-outside) with **nmap/masscan/shodan**. Depending on which services are running you can find in **this book some tricks to "attack" them**.  

如果您发现与在资产发现中已经找到的IP不同**的任何**子域，则应执行**基本漏洞扫描** \（使用nessus或openvas \）和一些[**端口扫描 **]（penting/penterting-network/＃发现主持人 - 从而发现主持人）用** nmap/masscan/shodan **。 根据正在运行的服务，您可以在**这本书中找到一些技巧来“攻击”它们**。
_Note that sometimes the subdomain is hosted inside an IP that is not controlled by the client, so it's not in the scope, be careful._

_注意，有时该子域托管在不受客户端不受控制的IP中，因此它不在范围中，请小心。

# Web servers hunting

> We have found all the companies and their assets and we know IP ranges, domains and subdomains inside the scope. It's time to search for web servers.

>我们已经找到了所有公司及其资产，我们知道范围内的IP范围，域和子域。 现在该搜索Web服务器了。

In the previous steps probably you have already perform some **recon to the IPs and domains discovered**, so you may **already found all the possible web servers**. However, if you haven't we are now going to see some **fast tricks to search for web servers** inside the scope.

在前面的步骤中，您可能已经对发现的IPS和域进行了一些**侦察，因此您可以**已经找到了所有可能的Web服务器**。 但是，如果您没有，我们现在将看到一些**快速技巧来搜索范围内的Web服务器**。

Please, note that this will be **oriented to search for web apps**, you should **perform the vulnerability** and **port scanning** also \(**if allowed** by the scope\).

请注意，这将被**面向搜索Web应用程序**，您应该**执行漏洞**和**端口扫描** **也\（如果允许使用范围\）。

A **fast method** to discover **ports open** related to **web** servers using [**masscan** can be found here](pentesting/pentesting-network/#http-port-discovery).  

A **快速方法**发现**与** Web **有关的端口**使用[** Masscan **可以在此处找到]（penterting/pentesting-network/＃http-port-discovery）。
Another friendly tool to look for web servers is [**httprobe**](https://github.com/tomnomnom/httprobe) **and** [**fprobe**](https://github.com/theblackturtle/fprobe). You just pass a list of domains and it will try to connect to port 80 \(http\) and 443 \(https\). You can additional indicate to try other ports:

寻找Web服务器的另一个友好工具是[** httprobe **]（https://github.com/tomnomnom/httprobe）**和** [** fprobe **]（https://github.com/ theblackturtle/fprobe）。 您只需传递域列表，它将尝试连接到端口80 \（http \）和443 \（https \）。 您可以额外指示尝试其他端口：

```bash
cat /tmp/domains.txt | httprobe #Test all domains inside the file for port 80 and 443
cat /tmp/domains.txt | httprobe -p http:8080 -p https:8443 #Check port 80, 443 and 8080 and 8443
```

## Screenshots

##屏幕截图

Now that you have discovered **all the web servers** running in the scope \(in **IPs** of the company and all the **domains** and **subdomains**\) you probably **don't know where to start**. So, let's make it simple and start just taking screenshots of all of them. Just **taking a look** to the **main page** of all of them you could find **weird** endpoints more **prone** to be **vulnerable**.

现在您已经发现了所有网络服务器**在范围\（在公司的** ips **中运行）和所有**域**和** subdomains ** \）您可能** don' t知道从哪里开始**。 因此，让我们变得简单，然后开始拍摄所有内容的屏幕截图。 只需**查看** **主页**所有这些主页**您可能会发现**怪异**端点更多**容易** **变得**脆弱**。

To perform the proposed idea you can use [**EyeWitness**](https://github.com/FortyNorthSecurity/EyeWitness), [**HttpScreenshot**](https://github.com/breenmachine/httpscreenshot), \[**Aquatone**\]\(**[https://github.com/michenriksen/aquatone](https://github.com/michenriksen/aquatone)**\)**, **\[**shutter**\]\(**[https://shutter-project.org/downloads/](https://shutter-project.org/downloads/)**\) or [**webscreenshot**](https://github.com/maaaaz/webscreenshot)**.**

要执行提出的想法，您可以使用[**眼睛**]（https://github.com/fortynorthsecurity/eyewitness），[** httpscreenshot **]（httpscreenshot **]（https://github.com/breenmachine/httpsccreenshot），httpscreenshot），） \ [** aquatone ** \] \（** [https://github.com/michenriksen/aquatone]（https://github.com/michenriksen/aquatone/aquatone）** \）** \）** **快门** \] \（** [https://shutter-project.org/downloads/]（https://shutter-project.org/downloads/）** \） ]（https://github.com/maaaaz/webscreenshot）**。**

# Recapitulation 1

> Congratulations! At this point you have already perform all the basic enumeration. Yes, it's basic because a lot more enumeration can be done \(will see more tricks later\).  

>恭喜！ 此时，您已经执行所有基本枚举。 是的，这是基本的，因为可以进行更多的枚举\（以后会看到更多技巧\）。
> Do you know that the BBs experts recommends to spend only 10-15mins in this phase? But don't worry, one you have practice you will do this even faster than that.

>您知道BBS专家建议在此阶段只花10-15分钟吗？ 但是不用担心，您有练习，您会比这更快地这样做。

So you have already:

所以你已经：

1. Found all the **companies** inside the scope

1.在范围内找到了所有**公司**
2. Found all the **assets** belonging to the companies \(and perform some vuln scan if in scope\)

2.找到属于公司\的所有**资产**（如果在范围\中执行一些vuln扫描）
3. Found all the **domains** belonging to the companies

3.找到所有属于公司的**域**
4. Found all the **subdomains** of the domains \(any subdomain takeover?\)

4.找到了域的所有**子域**（任何子域接管？\）
5. Found all the **web servers** and took a **screenshot** of them \(anything weird worth a deeper look?\)

5.找到了所有** Web服务器**，并拿了一个**屏幕截图**（值得更深入的外观的任何奇怪的东西？\）

Then, it's time for the real Bug Bounty hunt! In this methodology I'm **not going to talk about how to scan hosts** \(you can see a [guide for that here](pentesting/pentesting-network/)\), how to use tools like Nessus or OpenVas to perform a **vuln scan** or how to **look for vulnerabilities** in the services open \(this book already contains tons of information about possible vulnerabilities on a lot of common services\). **But, don't forget that if the scope allows it, you should give it a try.**

然后，是时候进行真正的Boun Bounty Hunt了！ 在这种方法中，我**不会谈论如何扫描宿主** \（您可以在此看到[此处的指南]（penting/pentesting/pentesting-network/）\），如何使用nessus或openvas等工具 要执行** vuln扫描**或如何**在“服务”中寻找漏洞**（本书已经包含有关许多普通服务\）的大量信息。 **但是，不要忘记，如果范围允许，您应该尝试一下。**

# **Bug hunting OSINT related information**

＃**错误狩猎OSINT相关信息**

Now that we have built the list of assets of our scope it's time to search for some OSINT low-hanging fruits.

现在，我们已经建立了范围的资产列表，是时候搜索一些Osint低悬挂果实了。

## Api keys leaks in github

* [https://github.com/hisxo/gitGraber](https://github.com/hisxo/gitGraber)
* [https://github.com/eth0izzle/shhgit](https://github.com/eth0izzle/shhgit)
* [https://github.com/techgaun/github-dorks](https://github.com/techgaun/github-dorks)
* [https://github.com/michenriksen/gitrob](https://github.com/michenriksen/gitrob)
* [https://github.com/anshumanbh/git-all-secrets](https://github.com/anshumanbh/git-all-secrets)
* [https://github.com/awslabs/git-secrets](https://github.com/awslabs/git-secrets)
* [https://github.com/kootenpv/gittyleaks](https://github.com/kootenpv/gittyleaks)
* [https://github.com/dxa4481/truffleHog](https://github.com/dxa4481/truffleHog)
* [https://github.com/obheda12/GitDorker](https://github.com/obheda12/GitDorker)

**Dorks**: _AWS\_SECRET\_ACCESS\_KEY, API KEY, API SECRET, API TOKEN… ROOT PASSWORD, ADMIN PASSWORD, COMPANYNAME SECRET, COMPANYNAME ROOT, GCP SECRET, AWS SECRET, “username password” extension:sql, “private” extension:pgp..._

** dorks **：_aws \ _secret \ _access \ _key，api键，API秘密，API秘密，API令牌…root密码，admin Password，CompanyName Secret，CompanyName root，GCP Secret，AWS Secret，AWS Secret，AWS Secret，AWS SECRET，“用户名密码”扩展：SQL：SQL：SQL，“ SQL，”，“ SQL，”，“ SQL，” 私人”扩展名：PGP ... _

### More Github Dorks

###更多github傻瓜

* extension:pem private
* extension:ppk private
* extension:sql mysql dump password
* extension:json api.forecast.io

*扩展名：json api.forecast.io
* extension:json mongolab.com
* extension:yaml mongolab.com
* extension:ica \[WFClient\] Password=

*扩展名：ICA \ [WFCLIENT \]密码=
* extension:avastlic “support.avast.com”
* extension:js jsforce conn.login
* extension:json googleusercontent client\_secret

You can also search for leaked secrets in all open repository platforms using: [https://searchcode.com/?q=auth\_key](https://searchcode.com/?q=auth_key)

您还可以使用以下方式在所有开放存储库平台中搜索泄漏的秘密，[https://searchcode.com/?q=Auth_key]

# [**Pentesting Web Methodology**](pentesting/pentesting-web/)

＃[** pentesting Web方法**]（penterting/pentesting-web/）

Anyway, the **majority of the vulnerabilities** found by bug hunters resides inside **web applications**, so at this point I would like to talk about a **web application testing methodology**, and you can [**find this information here**](pentesting/pentesting-web/).

无论如何，错误猎人发现的**大多数漏洞**位于** Web应用程序内**，因此，在这一点上，我想谈论** Web应用程序测试方法**，您可以[** ** 在此处找到此信息**]（penting/pentesting-web/）。

# Recapitulation 2

> Congratulations! The testing has finished! I hope you have find some vulnerabilities.

>恭喜！ 测试已经完成！ 希望您能找到一些漏洞。

At this point you should have already read the Pentesting Web Methodology and applied it to the scope.  

在这一点上，您应该已经阅读了pent的Web方法并将其应用于范围。
As you can see there is a lot of different vulnerabilities to search for.

如您所见，有很多不同的漏洞可以搜索。

**If you have find any vulnerability thanks to this book, please reference the book in your write-up.**

**如果您有任何脆弱性，请在本书中找到任何脆弱性，请在您的文章中引用该书。**



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


