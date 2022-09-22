

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


# Summary of the attack

＃攻击摘要

Imagine a server which is **signing** some **data** by **appending** a **secret** to some known clear text data and then hashing that data. If you know:

想象一下**签名**的服务器**通过**附加** a ** necret **到一些已知的清晰文本数据，然后哈希数据。 如果你知道的话：

* **The length of the secret** (this can be also bruteforced from a given length range)

***秘密的长度**（这也可以从给定的长度范围内违反）
* **The clear text data**

***清晰的文本数据**
* **The algorithm (and it's vulnerable to this attack)**

***算法（并且很容易受到此攻击）**
* **The padding is known**

***已知填充**
  * Usually a default one is used, so if the other 3 requirements are met, this also is

*通常使用默认一个，因此，如果满足了其他3个要求，这也是
  * The padding vary depending on the length of the secret+data, that's why the length of the secret is needed

*填充因秘密+数据的长度而异，这就是为什么需要秘密的长度

Then, it's possible for an **attacker** to **append** **data** and **generate** a valid **signature** for the **previos data + appended data**.

然后，**攻击者**可以**附加** **数据**和**生成**有效**签名**用于** previos数据 +附录数据**。

## How?

Basically the vulnerable algorithms generate the hashes by firstly **hashing a block of data**, and then, **from** the **previously** created **hash** (state), they **add the next block of data** and **hash it**.

基本上，脆弱算法首先**哈希块数据块**，然后，**从** ** the **创建**哈希**（状态），他们**添加了下一个块 数据**和**哈希**。

Then, imagine that the secret is "secret" and the data is "data", the MD5 of "secretdata" is 6036708eba0d11f6ef52ad44e8b74d5b.\

然后，想象一下秘密是“秘密”，数据是“数据”，“ SecretData”的MD5是6036708EBA0D11F6EF52AD44E4E8B74D5B。
If an attacker wants to append the string "append" he can:

如果攻击者想附加字符串“附加”，则可以：

* Generate a MD5 of 64 "A"s

*生成64“ A” S的MD5
* Change the state of the previously initialized hash to 6036708eba0d11f6ef52ad44e8b74d5b

*将先前初始化的哈希的状态更改为6036708EBA0D11F6EF52AD44E8B74D5B
* Append the string "append"

*附加字符串“附录”
* Finish the hash and the resulting hash will be a **valid one for "secret" + "data" + "padding" + "append"**

*完成哈希，结果将是“秘密” +“ data” +“ padding” +“ append” **的**有效的哈希。

## **Tool**

{% embed url="https://github.com/iagox86/hash_extender" %}

# References

You can find this attack good explained in [https://blog.skullsecurity.org/2012/everything-you-need-to-know-about-hash-length-extension-attacks](https://blog.skullsecurity.org/2012/everything-you-need-to-know-about-hash-length-extension-attacks)

您可以在[https://blog.skullsecurity.org/2012/everything-you-need-to-need-to-know-about-hash-lengt-length-extension-extension-extension-attacks]（ org/2012/您需要的一切都知道，以了解范围 - 长度 - 延伸攻击）


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


