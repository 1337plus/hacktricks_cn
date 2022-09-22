

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


# CBC

If the **cookie** is **only** the **username** (or the first part of the cookie is the username) and you want to impersonate the username "**admin**". Then, you can create the username **"bdmin"** and **bruteforce** the **first byte** of the cookie.

如果** cookie **仅** ** ** **用户名**（或cookie的第一部分是用户名），并且您想模仿用户名“ ** admin **”。 然后，您可以创建用户名**“ bdmin” **和** bruteforce ** ** cookie的第一个字节**。

# CBC-MAC

In cryptography, a **cipher block chaining message authentication code** (**CBC-MAC**) is a technique for constructing a message authentication code from a block cipher. The message is encrypted with some block cipher algorithm in CBC mode to create a **chain of blocks such that each block depends on the proper encryption of the previous block**. This interdependence ensures that a **change** to **any** of the plaintext **bits** will cause the **final encrypted block** to **change** in a way that cannot be predicted or counteracted without knowing the key to the block cipher.

在密码学中，A ** Cipher块链接消息身份验证代码**（** CBC-MAC **）是一种从块密码构建消息身份验证代码的技术。 该消息在CBC模式下使用某些块密码算法进行加密，以创建一个**块的链接，使每个块取决于上一个块**的正确加密。 这种相互依存可确保一个**更改**的授权**的任何**都会导致**最终加密块** ** **更改** ** **，以无法预测或反对的方式 知道块密码的钥匙。

To calculate the CBC-MAC of message m, one encrypts m in CBC mode with zero initialization vector and keeps the last block. The following figure sketches the computation of the CBC-MAC of a message comprising blocks![m\_{1}\\|m\_{2}\\|\cdots \\|m\_{x}](https://wikimedia.org/api/rest\_v1/media/math/render/svg/bbafe7330a5e40a04f01cc776c9d94fe914b17f5) using a secret key k and a block cipher E:

为了计算消息M的CBC-MAC，一个以零初始化向量的CBC模式加密M，并保留最后一个块。 下图绘制了包含块的消息的CBC-MAC的计算！[M \ _ {1} \\ | M \ _ {2} \\ | \ | \ cdots \\ | M \ _ {X}]（https） ：：//wikimedia.org/api/rest \ _v1/Media/Math/Math/render/svg/bbafe7330a5e40a0a0a0a0a04f01cc776c94fe914b17f5）使用秘密键k和一个块密钥k和一个块cipher e：

![CBC-MAC structure (en).svg](https://upload.wikimedia.org/wikipedia/commons/thumb/b/bf/CBC-MAC\_structure\_\(en\).svg/570px-CBC-MAC\_structure\_\(en\).svg.png)

# Vulnerability

With CBC-MAC usually the **IV used is 0**.\

使用CBC-MAC通常使用的** IV为0 **。\ \
This is a problem because 2 known messages (`m1` and `m2`) independently will generate 2 signatures (`s1` and `s2`). So:

这是一个问题，因为独立的2个已知消息（`m1`和`m2`）将生成2个签名（`s1`和`s2'）。 所以：

* `E(m1 XOR 0) = s1`
* `E(m2 XOR 0) = s2`

Then a message composed by m1 and m2 concatenated (m3) will generate 2 signatures (s31 and s32):

然后，由M1和M2串联（M3）组成的消息将生成2个签名（S31和S32）：

* `E(m1 XOR 0) = s31 = s1`
* `E(m2 XOR s1) = s32`

**Which is possible to calculate without knowing the key of the encryption.**

**可以在不知道加密的密钥的情况下进行计算。**

Imagine you are encrypting the name **Administrator** in **8bytes** blocks:

想象一下，您是在** 8bytes ** blocks中加密名称**管理员**：

* `Administ`
* `rator\00\00\00`

You can create a username called **Administ** (m1) and retrieve the signature (s1).\

您可以创建一个名为**管理**（M1）的用户名并检索签名（S1）。
Then, you can create a username called the result of `rator\00\00\00 XOR s1`. This will generate `E(m2 XOR s1 XOR 0)` which is s32.\

然后，您可以创建一个名为“ Rator \ 00 \ 00 \ 00 Xor s1”结果的用户名。 这将生成`e（m2 xor s1 xor 0）`是s32。
now, you can use s32 as the signature of the full name **Administrator**.

现在，您可以将S32用作全名**管理员**的签名。

### Summary

＃＃＃ 概括

1. Get the signature of username **Administ** (m1) which is s1

1.获取用户名**管理**（M1）的签名
2. Get the signature of username **rator\x00\x00\x00 XOR s1 XOR 0** is s32**.**

2.获取用户名的签名** rator \ x00 \ x00 \ x00 xor xor s1 xor 0 ** is s32 **。**
3. Set the cookie to s32 and it will be a valid cookie for the user **Administrator**.

3.将cookie设置为S32，它将是用户**管理员**的有效cookie。

# Attack Controlling IV

＃控制IV的攻击

If you can control the used IV the attack could be very easy.\

如果您可以控制二手IV，则攻击可能非常容易。\ \
If the cookies is just the username encrypted, to impersonate the user "**administrator**" you can create the user "**Administrator**" and you will get it's cookie.\

如果cookie只是用户名加密，为了模仿用户“ **管理员**”，您可以创建用户“ **管理员**”，您将获得它的cookie。
Now, if you can control the IV, you can change the first Byte of the IV so **IV\[0] XOR "A" == IV'\[0] XOR "a"** and regenerate the cookie for the user **Administrator.** This cookie will be valid to **impersonate** the user **administrator** with the initial **IV**.

现在，如果您可以控制静脉 用户**管理员。**此cookie将有效**模仿**用户**管理员**使用初始** iv **。

# References

More information in [https://en.wikipedia.org/wiki/CBC-MAC](https://en.wikipedia.org/wiki/CBC-MAC)

更多信息在[https://en.wikipedia.org/wiki/cbc-mac]（https://en.wikipedia.org/wiki/cbc-mac）中


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


