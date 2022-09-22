

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


# CBC - Cipher Block Chaining

＃CBC-密码块链接

In CBC mode the **previous encrypted block is used as IV** to XOR with the next block:

在CBC模式下，**以前的加密块用作iv ** to XOR的下一个块：

![CBC encryption](https://defuse.ca/images/cbc\_encryption.png)

！[CBC加密]（https://defuse.ca/images/cbc \_Encryptim.png）
To decrypt CBC the **opposite** **operations** are done:

要解密CBC **对面** **操作**已完成：

![CBC decryption](https://defuse.ca/images/cbc\_decryption.png)

Notice how it's needed to use an **encryption** **key** and an **IV**.

请注意，如何使用**加密** **键**和** iv **。

# Message Padding

As the encryption is performed in **fixed** **size** **blocks**, **padding** is usually needed in the **last** **block** to complete its length.\

由于**固定** **大小** **块**，**填充**通常需要在** last ** ** block **完成其长度时。
Usually **PKCS7** is used, which generates a padding **repeating** the **number** of **bytes** **needed** to **complete** the block. For example, if the last block is missing 3 bytes, the padding will be `\x03\x03\x03`.

通常使用** PKCS7 **，它会生成填充**重复** ** bytes ** ** ** ** ** **需要** **完整**完整**块。 例如，如果最后一个块缺少3个字节，则填充将为`\ x03 \ x03 \ x03`。

Let's look at more examples with a **2 blocks of length 8bytes**:

让我们看更多的示例，其中一个** 2个长度为8比特**：

| byte #0 | byte #1 | byte #2 | byte #3 | byte #4 | byte #5 | byte #6 | byte #7 | byte #0  | byte #1  | byte #2  | byte #3  | byte #4  | byte #5  | byte #6  | byte #7  |
| ------- | ------- | ------- | ------- | ------- | ------- | ------- | ------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- |
| P       | A       | S       | S       | W       | O       | R       | D       | 1        | 2        | 3        | 4        | 5        | 6        | **0x02** | **0x02** |
| P       | A       | S       | S       | W       | O       | R       | D       | 1        | 2        | 3        | 4        | 5        | **0x03** | **0x03** | **0x03** |
| P       | A       | S       | S       | W       | O       | R       | D       | 1        | 2        | 3        | **0x05** | **0x05** | **0x05** | **0x05** | **0x05** |
| P       | A       | S       | S       | W       | O       | R       | D       | **0x08** | **0x08** | **0x08** | **0x08** | **0x08** | **0x08** | **0x08** | **0x08** |

Note how in the last example the **last block was full so another one was generated only with padding**.

请注意，在最后一个示例中，**最后一个块已满，因此仅使用填充**生成另一个块。

# Padding Oracle

When an application decrypts encrypted data, it will first decrypt the data; then it will remove the padding. During the cleanup of the padding, if an **invalid padding triggers a detectable behaviour**, you have a **padding oracle vulnerability**. The detectable behaviour can be an **error**, a **lack of results**, or a **slower response**.

当应用程序解密加密数据时，它将首先解密数据。 然后它将去除填充物。 在清理填充期间，如果一个**无效的填充触发了可检测的行为**，您将有一个**填充甲骨文漏洞**。 可检测的行为可以是**错误**，**缺乏结果**或**慢速响应**。

If you detect this behaviour, you can **decrypt the encrypted data** and even **encrypt any cleartext**.

如果检测到此行为，则可以**解密加密的数据**，甚至**加密任何clearText **。

## How to exploit

##如何利用

You could use [https://github.com/AonCyberLabs/PadBuster](https://github.com/AonCyberLabs/PadBuster) to exploit this kind of vulnerability or just do

您可以使用[https://github.com/aoncyberlabs/padbuster]（https://github.com/aoncyberlabs/padbuster）来利用这种脆弱性

```
sudo apt-get install padbuster
```

In order to test if the cookie of a site is vulnerable you could try:

为了测试网站的cookie是否脆弱，您可以尝试：

```bash
perl ./padBuster.pl http://10.10.10.10/index.php "RVJDQrwUdTRWJUVUeBKkEA==" 8 -encoding 0 -cookies "login=RVJDQrwUdTRWJUVUeBKkEA=="
```

**Encoding 0** means that **base64** is used (but others are available, check the help menu).

**编码0 **意味着** base64 **已使用（但其他可用，请检查帮助菜单）。

You could also **abuse this vulnerability to encrypt new data. For example, imagine that the content of the cookie is "**_**user=MyUsername**_**", then you may change it to "\_user=administrator\_" and escalate privileges inside the application. You could also do it using `paduster`specifying the -plaintext** parameter:

您也可以**滥用这种脆弱性来加密新数据。 例如，想象一下cookie的内容是“ ** _ ** user = myusername ** _ **”，然后您可以将其更改为“ \ _USER = apanistionator \ _”，并在应用程序中升级特权。 您也可以使用`paduster`plaintext **参数：

```bash
perl ./padBuster.pl http://10.10.10.10/index.php "RVJDQrwUdTRWJUVUeBKkEA==" 8 -encoding 0 -cookies "login=RVJDQrwUdTRWJUVUeBKkEA==" -plaintext "user=administrator"
```

If the site is vulnerable `padbuster`will automatically try to find when the padding error occurs, but you can also indicating the error message it using the **-error** parameter.

如果该站点易受攻击，则``padbuster`都会自动尝试在发生填充错误时查找，但您还可以使用**  - 错误**参数表示错误消息。

```bash
perl ./padBuster.pl http://10.10.10.10/index.php "" 8 -encoding 0 -cookies "hcon=RVJDQrwUdTRWJUVUeBKkEA==" -error "Invalid padding"
```

## The theory

＃＃ 理论

In **summary**, you can start decrypting the encrypted data by guessing the correct values that can be used to create all the **different paddings**. Then, the padding oracle attack will start decrypting bytes from the end to the start by guessing which will be the correct value that **creates a padding of 1, 2, 3, etc**.

在**摘要**中，您可以通过猜测可用于创建所有**不同的填充**的正确值开始解密加密数据。 然后，填充甲骨文攻击将通过猜测这将是**创建1、2、3等**的正确值，从而开始从头到尾解密字节。

![](<../.gitbook/assets/image (629) (1) (1).png>)

Imagine you have some encrypted text that occupies **2 blocks** formed by the bytes from **E0 to E15**.\

想象一下，您有一些占据的加密文本** 2块**由字节从** e0到e15 **。
In order to **decrypt** the **last** **block** (**E8** to **E15**), the whole block passes through the "block cipher decryption" generating the **intermediary bytes I0 to I15**.\

为了**解密** **最后** **块**（** e8 ** to ** e15 **），整个块通过“块密码解密”生成**中介字节 i0至i15 **。\ \
Finally, each intermediary byte is **XORed** with the previous encrypted bytes (E0 to E7). So:

最后，每个中间字节都是** Xored **，具有先前的加密字节（E0至E7）。 所以：

* `C15 = D(E15) ^ E7 = I15 ^ E7`
* `C14 = I14 ^ E6`
* `C13 = I13 ^ E5`
* `C12 = I12 ^ E4`
* ...

Now, It's possible to **modify `E7` until `C15` is `0x01`**, which will also be a correct padding. So, in this case: `\x01 = I15 ^ E'7`

现在，可以**修改``e7````直到c15'是`0x01` ***''，这也将是正确的填充。 因此，在这种情况下：`\ x01 = i15 ^ e'7``

So, finding E'7, it's **possible to calculate I15**: `I15 = 0x01 ^ E'7`

因此，找到E'7，可以计算I15 **：`i15 = 0x01 ^ e'7``

Which allow us to **calculate C15**: `C15 = E7 ^ I15 = E7 ^ \x01 ^ E'7`

这使我们可以**计算C15 **：`c15 = e7 ^ i15 = e7 ^ \ x01 ^ e'7`

Knowing **C15**, now it's possible to **calculate C14**, but this time brute-forcing the padding `\x02\x02`.

知道** c15 **，现在可以**计算C14 **，但是这次是野蛮的填充填充`\ x02 \ x02`。

This BF is as complex as the previous one as it's possible to calculate the the `E''15` whose value is 0x02: `E''7 = \x02 ^ I15` so it's just needed to find the **`E'14`** that generates a **`C14` equals to `0x02`**.\

该BF与前一个一样复杂，因为可以计算其值为0x02的`e'15`：`e'7 = \ x02 ^ i15`，因此只需要找到** e e' 14` **生成一个**`c14`等于`0x02` **。
Then, do the same steps to decrypt C14: **`C14 = E6 ^ I14 = E6 ^ \x02 ^ E''6`**

然后，执行相同的步骤来解密C14：**``c14 = e6 ^ i14 = e6 ^ \ x02 ^ e'6` ** **

**Follow this chain until you decrypt the whole encrypted text.**

**遵循此链，直到您解密整个加密文本为止。**

## Detection of the vulnerability

##检测漏洞

Register and account and log in with this account .\

注册和帐户并使用此帐户登录。\ \
If you **log in many times** and always get the **same cookie**, there is probably **something** **wrong** in the application. The **cookie sent back should be unique** each time you log in. If the cookie is **always** the **same**, it will probably always be valid and there **won't be anyway to invalidate i**t.

如果您**登录了很多次，并且始终获得**相同的cookie **，则在应用程序中可能有** **错误**。 ** cookie每次登录时都应该是唯一的**。如果cookie是**总是** ** **相同**，它可能总是有效的，并且无论如何都不会无效 它。

Now, if you try to **modify** the **cookie**, you can see that you get an **error** from the application.\

现在，如果您尝试**修改** ** cookie **，则可以看到您从应用程序中获得**错误**。\ \ \
But if you BF the padding (using padbuster for example) you manage to get another cookie valid for a different user. This scenario is highly probably vulnerable to padbuster.

但是，如果您bf填充物（例如使用padbuster），则设法获得另一个对其他用户有效的cookie。 这种情况很可能很容易受到Padbuster的影响。

# References

* [https://en.wikipedia.org/wiki/Block\_cipher\_mode\_of\_operation](https://en.wikipedia.org/wiki/Block\_cipher\_mode\_of\_operation)

* [https://en.wikipedia.org/wiki/wiki/block \ _cipher_mode_of_of_operation]（https://en.wikipedia.org/wiki/wiki/block/block \ _ciphor_cipher_mmode_of_of_operation）


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


