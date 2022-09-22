

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


# ECB

(ECB) Electronic Code Book - symmetric encryption scheme which **replaces each block of the clear text** by the **block of ciphertext**. It is the **simplest** encryption scheme. The main idea is to **split** the clear text into **blocks of N bits** (depends on the size of the block of input data, encryption algorithm) and then to encrypt (decrypt) each block of clear text using the only key.

（欧洲央行）电子代码簿 - 对称加密方案，该方案**用ciphertext **的**块代替了清晰文本的每个块**。 这是**最简单的加密方案。 主要思想是**拆分**清晰的文本中** n位**块（取决于输入数据块的大小，加密算法），然后使用清晰文本的每个块加密（解密） 唯一的钥匙。

![](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e6/ECB_decryption.svg/601px-ECB_decryption.svg.png)

Using ECB has multiple security implications:

使用欧洲央行具有多种安全性含义：

* **Blocks from encrypted message can be removed**

***可以删除来自加密消息的块**
* **Blocks from encrypted message can be moved around**

***可以四处移动加密消息的块**

# Detection of the vulnerability

＃检测漏洞

Imagine you login into an application several times and you **always get the same cookie**. This is because the cookie of the application is **`<username>|<password>`**.\

想象一下，您多次登录到应用程序，并且您**总是获得相同的cookie **。 这是因为该应用程序的cookie是**`<用户名> | <passwert>`**。\ \ \ \ \ \
Then, you generate to new users, both of them with the **same long password** and **almost** the **same** **username**.\

然后，您将生成新用户，两者都使用**相同的长密码**和**几乎** ** same ** **用户名**。
You find out that the **blocks of 8B** where the **info of both users** is the same are **equals**. Then, you imagine that this might be because **ECB is being used**. 

您会发现8B **的**块，两个用户的**信息**均为**等于**。 然后，您可以想象这可能是因为**欧洲央行正在使用**。

Like in the following example. Observe how these** 2 decoded cookies** has several times the block **`\x23U\xE45K\xCB\x21\xC8`**

就像以下示例一样。 观察这些** 2解码cookie **有几次块** \ x23u \ xe45k \ xcb \ xcb \ x21 \ xc8` ** **

```
\x23U\xE45K\xCB\x21\xC8\x23U\xE45K\xCB\x21\xC8\x04\xB6\xE1H\xD1\x1E \xB6\x23U\xE45K\xCB\x21\xC8\x23U\xE45K\xCB\x21\xC8+=\xD4F\xF7\x99\xD9\xA9

\x23U\xE45K\xCB\x21\xC8\x23U\xE45K\xCB\x21\xC8\x04\xB6\xE1H\xD1\x1E \xB6\x23U\xE45K\xCB\x21\xC8\x23U\xE45K\xCB\x21\xC8+=\xD4F\xF7\x99\xD9\xA9
```

This is because the **username and password of those cookies contained several times the letter "a"** (for example). The **blocks** that are **different** are blocks that contained **at least 1 different character** (maybe the delimiter "|" or some necessary difference in the username).

这是因为这些cookie的**用户名和密码几次包含字母“ a” **（例如）。 **不同**的**块**是包含**至少1个不同字符**的块（也许是定界符“ |”或用户名中的一些必要区别）。

Now, the attacker just need to discover if the format is `<username><delimiter><password>` or `<password><delimiter><username>`. For doing that, he can just **generate several usernames **with s**imilar and long usernames and passwords until he find the format and the length of the delimiter:**

现在，攻击者只需要发现格式是否为“ <username> <deLimiter> <password>`or'或`<密码> <DeLimiter> <username>`。 为此，他只能**生成几个用户名**，带有s ** imilar和长的用户名和密码，直到找到定界符的格式和长度：**

| Username length: | Password length: | Username+Password length: | Cookie's length (after decoding): |

| 用户名长度：| 密码长度：| 用户名+密码长度：| cookie的长度（解码后）：|
| ---------------- | ---------------- | ------------------------- | --------------------------------- |
| 2                | 2                | 4                         | 8                                 |
| 3                | 3                | 6                         | 8                                 |
| 3                | 4                | 7                         | 8                                 |
| 4                | 4                | 8                         | 16                                |
| 7                | 7                | 14                        | 16                                |

# Exploitation of the vulnerability

＃剥削漏洞

## Removing entire blocks

##删除整个块

Knowing the format of the cookie (`<username>|<password>`), in order to impersonate the username `admin` create a new user called `aaaaaaaaadmin` and get the cookie and decode it:

了解cookie的格式（`<用户名> | <passwert>`），以模仿用户名`admin`创建一个名为`aaaaaaaaaadmin`的新用户''并进行cookie并解码：

```
\x23U\xE45K\xCB\x21\xC8\xE0Vd8oE\x123\aO\x43T\x32\xD5U\xD4
```

We can see the pattern `\x23U\xE45K\xCB\x21\xC8` created previously with the username that contained only `a`.\

我们可以看到模式`\ x23U \ xe45k \ xcb \ x21 \ xc8`先前使用的用户名创建的，该用户名仅包含`
Then, you can remove the first block of 8B and you will et a valid cookie for the username `admin`:

然后，您可以删除8B的第一个块，然后将用户名``admin''的有效cookie：

```
\xE0Vd8oE\x123\aO\x43T\x32\xD5U\xD4
```

## Moving blocks

In many databases it is the same to search for `WHERE username='admin';` or for `WHERE username='admin    ';` _(Note the extra spaces)_

在许多数据库中，搜索``where用户名='admin';或for`where用户名='admin';

So, another way to impersonate the user `admin` would be to:

因此，冒充用户``admin''的另一种方法是：

* Generate a username that: `len(<username>) + len(<delimiter) % len(block)`. With a block size of `8B` you can generate username called: `username       `, with the delimiter `|` the chunk `<username><delimiter>` will generate 2 blocks of 8Bs.

*生成一个用户名：`len（<username>） + len（<deLimiter）％len（block）`。 使用“ 8b”的块大小，您可以生成名为：``用户名'的用户名。
* Then, generate a password that will fill an exact number of blocks containing the username we want to impersonate and spaces, like: `admin   ` 

*然后，生成一个密码，该密码将填充包含我们想要的用户名和空格的用户名的确切块，例如：`admin'

The cookie of this user is going to be composed by 3 blocks: the first 2 is the blocks of the username + delimiter and the third one of the password (which is faking the username): `username       |admin   `

该用户的cookie将由3个块组成：第一个块是用户名 +定界符和密码的第三个块（正在伪造用户名）：`username | admin```

** Then, just replace the first block with the last time and will be impersonating the user `admin`: `admin          |username`**

**然后，只需上次替换第一个块，然后冒充用户`admin'：`admin | username` **

# References

* [http://cryptowiki.net/index.php?title=Electronic_Code_Book\_(ECB)](http://cryptowiki.net/index.php?title=Electronic_Code_Book_\(ECB\))


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


