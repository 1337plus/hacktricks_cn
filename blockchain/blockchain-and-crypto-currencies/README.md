

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


# Basic Terminology

＃基本术语

* **Smart contract**: Smart contracts are simply **programs stored on a blockchain that run when predetermined conditions are met**. They typically are used to automate the **execution** of an **agreement** so that all participants can be immediately certain of the outcome, without any intermediary’s involvement or time loss. (From [here](https://www.ibm.com/topics/smart-contracts)).

***智能合约**：智能合约只是**存储在满足预定条件时运行的区块链上的程序**。 它们通常用于自动化**协议**的**执行**，以便所有参与者都可以立即确定结果，而无需任何中介的参与或时间损失。 （来自[此处]（https://www.ibm.com/topics/smart-contracts））。
  * Basically, a smart contract is a **piece of code** that is going to be executed when people access and accept the contract. Smart contracts **run in blockchains** (so the results are stored inmutable) and can be read by the people before accepting them.

*基本上，智能合约是一项**代码**，当人们访问并接受合同时将执行。 智能合约**在区块链中运行**（因此，结果存储了不明显），并且可以在接受它们之前先阅读。
* **dApps**: **Decentralised applications** are implemented on top of **smart** **contracts**. They usually have a front-end where the user can interact with the app, the **back-end** is public (so it can be audited) and is implemented as a **smart contract**. Sometimes the use of a database is needed, Ethereum blockchain allocates certain storage to each account.

*** Dapps **：**分散应用程序**在** Smart ** **合同**之上实施。 他们通常具有前端用户可以与应用程序进行交互的前端，**后端**是公开的（可以进行审核），并将其实现为**智能合约**。 有时需要使用数据库，以太坊区块链将某些存储分配给每个帐户。
* **Tokens & coins**: A **coin** is a cryptocurrency that act as **digital** **money** and a **token** is something that **represents** some **value** but it's not a coin.

*** tokens＆Coins **：A **硬币**是一种加密货币，充当**数字** **货币**和a ** token ** **是**代表**的东西 **但这不是硬币。
  * **Utility Tokens**: These tokens allow the user to **access certain service later** (it's something that have some value in a specific environment).

***实用令牌**：这些令牌允许用户**以后访问某些服务**（这是在特定环境中具有一定价值的东西）。
  * **Security Tokens**: These represents the **ownership** or some asset.

***安全令牌**：这些代表**所有权**或某些资产。
* **DeFi**: **Decentralized Finance**.

*** defi **：**分散财务**。
* **DEX: Decentralized Exchange Platforms**.

*** DEX：分散交换平台**。
* **DAOs**: **Decentralized Autonomous Organizations**.

*** daos **：**分散的自主组织**。

# Consensus Mechanisms

＃共识机制

For a blockchain transaction to be recognized, it must be **appended** to the **blockchain**. Validators (miners) carry out this appending; in most protocols, they **receive a reward** for doing so. For the blockchain to remain secure, it must have a mechanism to **prevent a malicious user or group from taking over a majority of validation**.

为了确认区块链事务，必须将其附加** ** **区块链**。 验证者（矿工）执行此附加； 在大多数协议中，他们**因此获得奖励**。 为了使区块链保持安全，必须具有一种机制来防止恶意用户或组接管大多数验证**。

Proof of work, another commonly used consensus mechanism, uses a validation of computational prowess to verify transactions, requiring a potential attacker to acquire a large fraction of the computational power of the validator network.

工作证明是另一种常用的共识机制，使用计算能力验证来验证交易，要求潜在的攻击者获得验证器网络的大部分计算能力。

## Proof Of Work (PoW)

##工作证明（POW）

This uses a **validation of computational prowess** to verify transactions, requiring a potential attacker to acquire a large fraction of the computational power of the validator network.\

这使用计算能力**的**验证来验证交易，要求潜在的攻击者获得验证器网络的计算能力的很大一部分。
The **miners** will **select several transactions** and then start **computing the Proof Of Work**. The **miner with the greatest computation resources** is more probably to **finish** **earlier** the Proof of Work and get the fees of all the transactions.

**矿工**将**选择几笔交易**，然后开始**计算工作证明**。 **具有最大计算资源的矿工**更可能是**完成** ** **工作证明并获得所有交易的费用。

## Proof Of Stake (PoS)

##股份证明（POS）

PoS accomplishes this by **requiring that validators have some quantity of blockchain tokens**, requiring **potential attackers to acquire a large fraction of the tokens** on the blockchain to mount an attack.\

POS通过**要求验证器具有一定数量的区块链令牌**来实现这一目标，要求**潜在的攻击者在区块链上获得大量令牌**以进行攻击。
In this kind of consensus, the more tokens a miner has, the more probably it will be that the miner will be asked to create the next block.\

在这种共识中，矿工拥有的代币越多，越来越有可能要求矿工创建下一个块。\ \ \ \
Compared with PoW, this greatly **reduced the energy consumption** the miners are expending.

与POW相比，这大大减少了矿工所花费的能源消耗。

# Bitcoin

＃比特币

## Transactions

A simple **transaction** is a **movement of money** from an address to another one.\

简单的**交易**是金钱的移动**从一个地址到另一个地址的移动。
An **address** in bitcoin is the hash of the **public** **key**, therefore, someone in order to make a transaction from an address he needs to know the private key associated to that public key (the address).\

一个**地址**在比特币中是** public ** **键**的哈希，因此，某人为了从他需要知道与该公共密钥相关的私钥的地址进行交易（ 地址）。\
Then, when a **transaction** is performed, it's **signed** with the private key of the address to show that the transaction is **legit**.

然后，当执行**交易**时，它是**签名**，用地址的私钥签名，以表明交易是**合法**。

The first part of producing a digital signature in Bitcoin can be represented mathematically in the following way:\

在比特币中生产数字签名的第一部分可以通过以下方式以数学方式表示：\
_**Sig**_ = _**Fsig**_(_**Fhash**_(_**m**_),_**dA**_)

Where:

在哪里：

* \_d\_A is the signing **private key**

*\ _d \ _a是签名**私钥**
* _m_ is the **transaction**

*_m_是**交易**
* Fhash is the hashing function

* fhash是哈希功能
* Fsig is the signing algorithm

* FSIG是签名算法
* Sig is the resulting signature

* SIG是由此产生的签名

The signing function (Fsig) produces a signature (Sig) that comprises of two values: R and S:

签名函数（FSIG）产生一个由两个值组成的签名（SIG）：R和S：：

* Sig = (R, S)

Once R and S have been calculated, they are serialized into a byte stream that is encoded using an international standard encoding scheme that is known as the Distinguished Encoding Rules (or DER). In order to verify that the signature is valid, a signature verification algorithm is used. Verification of a digital signature requires the following:

一旦计算出R和S，它们就会序列化为一个字节流，该字节流使用国际标准编码方案编码，该方案被称为杰出的编码规则（或DER）。 为了验证签名是否有效，使用签名验证算法。 数字签名的验证需要以下内容：

* Signature (R and S)

*签名（R和S）
* Transaction hash

*交易哈希
* The public key that corresponds to the private key that was used to create the signature

*与用于创建签名的私钥相对应的公共密钥

Verification of a signature effectively means that only the owner of the private key (that generated the public key) could have produced the signature on the transaction. The signature verification algorithm will return ‘TRUE’ if the signature is indeed valid.

有效地验证签名意味着只有私钥的所有者（生成公共密钥）才能在交易上产生签名。 如果签名确实有效，则签名验证算法将返回“ true”。

### Multisignature Transactions

A multi-signature **address** is an address that is associated with more than one ECDSA private key. The simplest type is an m-of-n address - it is associated with n private keys, and sending bitcoins from this address requires signatures from at least m keys. A multi-signature **transaction** is one that sends funds from a multi-signature address.

多签名**地址**是与多个ECDSA私钥相关联的地址。 最简单的类型是一个M-n-N地址 - 它与n个私钥关联，并且从该地址发送比特币需要至少M键的签名。 多签名**事务**是从多签名地址发送资金的。

### Transactions Fields

###交易字段

Each bitcoin transaction has several fields:

每个比特币交易都有几个字段：

* **Inputs**: The amount and address **from** where **bitcoins** are **being** transferred

***输入**：来自**的金额和地址** **比特币**被**转移
* **Outputs**: The address and amounts that each **transferred** to **each** **output**

***输出**：每个**转移到**每个** **输出**的地址和金额**
* **Fee:** The amount of **money** that is **payed** to the **miner** of the transaction

***费用：** **金钱** **支付** **交易的**矿工**
* **Script\_sig**: Script signature of the transaction

***脚本\ _sig **：交易的脚本签名
* **Script\_type**: Type of transaction

***脚本\ _type **：交易类型

There are **2 main types** of transactions:

有** 2个交易的主要类型**：

* **P2PKH: "Pay To Public Key Hash"**: This is how transactions are made. You are requiring the **sender** to supply a valid **signature** (from the private key) and **public** **key**. The transaction output script will use the signature and public key and through some cryptographic functions will check **if it matches** with the public key hash, if it does, then the **funds** will be **spendable**. This method conceals your public key in the form of a hash for extra security.

*** p2pkh：“付款到公共密钥哈希” **：这是进行交易的方式。 您要求**发送者**提供有效的**签名**（来自私钥）和** public ** **键**。 事务输出脚本将使用签名和公钥，通过一些加密功能，如果它与公共密钥哈希相匹配，则可以检查**，如果这样做，则**资金**将是**可**的**。 此方法以哈希的形式隐藏了您的公钥，以供额外的安全性。
* **P2SH: "Pay To Script Hash":** The outputs of a transaction are just **scripts** (this means the person how want this money send a script) that, if are **executed with specific parameters, will result in a boolean of `true` or `false`**. If a miner runs the output script with the supplied parameters and results in `true`, the **money will be sent to your desired output**. `P2SH` is used for **multi-signature** wallets making the output scripts **logic that checks for multiple signatures before accepting the transaction**. `P2SH` can also be used to allow anyone, or no one, to spend the funds. If the output script of a P2SH transaction is just `1` for true, then attempting to spend the output without supplying parameters will just result in `1` making the money spendable by anyone who tries. This also applies to scripts that return `0`, making the output spendable by no one.

*** p2sh：“付款到脚本哈希”：**事务的输出只是**脚本**（这意味着要让这笔钱发送脚本的人），如果用特定参数执行**， 将导致“ true”或“ false” **的布尔值。 如果矿工使用提供的参数运行输出脚本，并以``True''的形式运行，则**资金将发送到您所需的输出**。 `p2sh`用于**多签名**钱包，制作输出脚本**逻辑，该逻辑在接受交易之前检查多个签名**。 “ P2SH”也可以用来允许任何人（或没有人）花费资金。 如果P2SH交易的输出脚本只是``1` for true''，那么尝试在不提供参数的情况下花费输出只会导致1`1`使任何尝试的人都可以花钱。 这也适用于返回`0`的脚本，使输出无人使用。

## Lightning Network

##闪电网络

This protocol helps to **perform several transactions to a channe**l and **just** **sent** the **final** **state** to the blockchain to save it.\

该协议有助于**对channe ** l执行几笔交易，而**仅** **已发送** ** final ** **状态**向区块链保存。\ \ \ \ \
This **improves** bitcoin blockchain **speed** (it just on allow 7 payments per second) and it allows to create **transactions more difficult to trace** as the channel is created via nodes of the bitcoin blockchain:

此**改进**比特币区块链**速度**（仅在每秒允许7付款上），并且由于通过比特币区块链的节点创建通道时，它允许创建**交易更难以跟踪**：

![](<../../.gitbook/assets/image (611).png>)

Normal use of the Lightning Network consists of **opening a payment channel** by committing a funding transaction to the relevant base blockchain (layer 1), followed by making **any number** of Lightning Network **transactions** that update the tentative distribution of the channel's funds **without broadcasting those to the blockchain**, optionally followed by closing the payment channel by **broadcasting** the **final** **version** of the settlement transaction to distribute the channel's funds.

闪电网络的正常使用包括**通过向相关基本区块链进行资金交易（第1层），然后制作**任何数字**闪电网络**交易** 渠道资金**的暂定发行，而无需将其广播到区块链**，然后选择通过**广播**结束付款渠道** **最终** ** ** **版本**和解交易的频道以分发频道的频道 资金。

Note that any of the both members of the channel can stop and send the final state of the channel to the blockchain at any time.

请注意，渠道的任何成员都可以随时停止并将渠道的最终状态发送到区块链。

# Bitcoin Privacy Attacks

＃比特币隐私攻击

## Common Input

##公共输入

Theoretically the inputs of one transaction can belong to different users, but in reality that is unusual as it requires extra steps. Therefore, very often it can be assumed that **2 input addresses in the same transaction belongs to the same owner**.

从理论上讲，一个交易的输入可以属于不同的用户，但实际上这是不寻常的，因为它需要额外的步骤。 因此，通常可以假定同一交易中的** 2输入地址属于同一所有者**。

## UTXO Change Address Detection

## UTXO更改地址检测

**UTXO** means **Unspent Transaction Outputs** (UTXOs). In a transaction that uses the output from a previous transaction as an input, the **whole output need to be spent** (to avoid double-spend attacks). Therefore, if the intention was to **send** just **part** of the money from that output to an address and **keep** the **other** **part**, **2 different outputs** will appear: the **intended** one and a **random new change address** where the rest of the money will be saved.

** utxo **表示**无需交易输出**（UTXOS）。 在使用先前交易的输出作为输入的交易中，需要花费** **（以避免双重攻击）。 因此，如果打算**发送**只是**零件**该输出的钱的部分** **将出现：**预期的**一个和一个随机的新更改地址**将节省其余的钱。

Then, a watcher can make the assumption that **the new change address generated belong to the owner of the UTXO**.

然后，观察者可以假设**生成的新更改地址属于UTXO **的所有者。

## Social Networks & Forums

##社交网络和论坛

Some people gives data about theirs bitcoin addresses in different webs on Internet. **This make pretty easy to identify the owner of an address**.

有些人在Internet上的不同网中提供有关其比特币地址的数据。 **这使识别地址的所有者非常容易**。

## Transaction Graphs

##交易图

By representing the transactions in graphs, i**t's possible to know with certain probability to where the money of an account were**. Therefore, it's possible to know something about **users** that are **related** in the blockchain.

通过表示图中的交易，我有可能以某些概率知道帐户的钱是**的位置。 因此，有可能了解有关区块链中与**相关的**的信息。

## **Unnecessary input heuristic**

## **不必要的输入启发式**

Also called the "optimal change heuristic". Consider this bitcoin transaction. It has two inputs worth 2 BTC and 3 BTC and two outputs worth 4 BTC and 1 BTC.

也称为“最佳变化启发式”。 考虑此比特币交易。 它具有两个价值2 BTC和3 BTC的输入，两个输出价值为4 BTC和1 BTC。

```
2 btc --> 4 btc
3 btc     1 btc
```

Assuming one of the outputs is change and the other output is the payment. There are two interpretations: the payment output is either the 4 BTC output or the 1 BTC output. But if the 1 BTC output is the payment amount then the 3 BTC input is unnecessary, as the wallet could have spent only the 2 BTC input and paid lower miner fees for doing so. This is an indication that the real payment output is 4 BTC and that 1 BTC is the change output.

假设其中一个输出是更改，另一个输出是付款。 有两个解释：付款输出是4个BTC输出或1 BTC输出。 但是，如果1 BTC输出是付款金额，则不需要3 BTC输入，因为钱包本可以仅花费2个BTC输入并支付了较低的矿工费用。 这表明实际支付输出为4 BTC，而1 BTC是变更输出。

This is an issue for transactions which have more than one input. One way to fix this leak is to add more inputs until the change output is higher than any input, for example:

这是具有多个输入的交易的问题。 解决此泄漏的一种方法是添加更多输入，直到更改输出高于任何输入，例如：

```
2 btc --> 4 btc
3 btc     6 btc
5 btc
```

## Forced address reuse

##强制地址重用

**Forced address reuse** or **incentivized address reuse** is when an adversary pays an (often small) amount of bitcoin to addresses that have already been used on the block chain. The adversary hopes that users or their wallet software **will use the payments as inputs to a larger transaction which will reveal other addresses via the the common-input-ownership** heuristic. These payments can be understood as a way to coerce the address owner into unintentional address reuse.

**强制地址重复使用**或**激励地址重用**是当对手向已经在块链上使用的地址支付（通常很少）的比特币时。 对手希望用户或其钱包软件**将使用这些付款作为较大交易的投入，该交易将通过共同输入所有权**启发其他地址。 可以将这些付款理解为将地址所有者陷入无意地地址重用的一种方式。

This attack is sometimes incorrectly called a **dust attack**.

这种攻击有时被错误地称为**尘埃攻击**。

The correct behaviour by wallets is to not spend coins that have landed on an already-used empty addresses.

钱包的正确行为是不要花在已经使用的空地址上的硬币。

## Other Blockchain Analysis

##其他区块链分析

* **Exact Payment Amounts**: In order to avoid transactions with a change, the payment needs to be equal to the UTXO (which is highly unexpected). Therefore, a **transaction with no change address are probably transfer between 2 addresses of the same user**.

***确切的付款金额**：为了避免使用更改的交易，付款需要等于UTXO（这是非常出乎意料的）。 因此，没有更改地址的**交易可能是在同一用户的2个地址之间转移的**。
* **Round Numbers**: In a transaction, if one of the outputs is a "**round number**", it's highly probable that this is a **payment to a human that put that** "round number" **price**, so the other part must be the leftover.

***圆数**：在交易中，如果输出之一是“ **圆号**”，则很有可能是向人类支付**的**付款**“圆号” **价格**，所以另一部分必须是剩菜。
* **Wallet fingerprinting:** A careful analyst sometimes deduce which software created a certain transaction, because the many **different wallet softwares don't always create transactions in exactly the same way**. Wallet fingerprinting can be used to detect change outputs because a change output is the one spent with the same wallet fingerprint.

***钱包指纹：**仔细的分析师有时会推论哪种软件创建了一定的交易，因为许多**不同的钱包软件并不总是以完全相同的方式创建交易**。 钱包指纹可用于检测变化输出，因为更改输出是用相同钱包指纹的花费。
* **Amount & Timing correlations**: If the person that performed the transaction **discloses** the **time** and/or **amount** of the transaction, it can be easily **discoverable**.

***金额和正时相关性**：如果执行交易的人**披露**时间**和/或**金额**，则可以很容易地**可发现**。

## Traffic analysis

##流量分析

Some organisation **sniffing your traffic** can see you communicating in the bitcoin network.\

一些组织**嗅探您的流量**可以看到您在比特币网络中进行交流。
If the adversary sees a transaction or block **coming out of your node which did not previously enter**, then it can know with near-certainty that **the transaction was made by you or the block was mined by you**. As internet connections are involved, the adversary will be able to **link the IP address with the discovered bitcoin information**.

如果对手看到以前没有输入**的节点的交易或块**，那么它可以几乎确定地知道**交易是由您进行的，或者块是由您开采的**。 由于涉及互联网连接，对手将能够将IP地址与发现的比特币信息链接在一起。

An attacker that isn't able to sniff all the Internet traffic but that has **a lot of Bitcoin nodes** in order to stay **closer** to the s**o**urces could be able to know the IP address that are announcing transactions or blocks.\

一个无法嗅探所有互联网流量的攻击者，但有很多比特币节点**，以便保持**靠近** ** o ** o ** urces可能能够知道IP 宣布交易或块的地址。
Also, some wallets periodically rebroadcast their unconfirmed transactions so that they are more likely to propagate widely through the network and be mined.

此外，一些钱包会定期重新广播其未经证实的交易，以便他们更有可能通过网络广泛传播并开采。

## Other attacks to find info about the owner of addresses

##其他攻击以查找有关地址所有者的信息

For more attacks read [https://en.bitcoin.it/wiki/Privacy](https://en.bitcoin.it/wiki/Privacy)

有关更多攻击，请阅读[https://en.bitcoin.it/wiki/privacy]（https://en.bitcoin.it/wiki/privacy）

# Anonymous Bitcoins

## Obtaining Bitcoins Anonymously

##匿名获得比特币

* **Cash trades:** Buy bitcoin using cash.

***现金交易：**使用现金购买比特币。
* **Cash substitute:** Buy gift cards or similar and exchange them for bitcoin online.

***现金替代品：**购买礼品卡或类似的东西，然后在线换成比特币。
* **Mining:** Mining is the most anonymous way to obtain bitcoin. This applies to solo-mining as [mining pools](https://en.bitcoin.it/wiki/Pooled\_mining) generally know the hasher's IP address.

***采矿：**采矿是获得比特币的最匿名方法。 这适用于[采矿池]（https://en.bitcoin.it/wiki/pooled \ _Mining）的独奏开采通常都知道Hasher的IP地址。
* **Stealing:** In theory another way of obtaining anonymous bitcoin is to steal them.

***偷窃：**从理论上讲，获得匿名比特币的另一种方式是偷它们。

## Mixers

A user would **send bitcoins to a mixing service** and the service would **send different bitcoins back to the user**, minus a fee. In theory an adversary observing the blockchain would be **unable to link** the incoming and outgoing transactions.

用户会**将比特币发送到混合服务**，并且该服务将**将不同的比特币发送给用户**，减去费用。 从理论上讲，观察区块链的对手将无法连接出来的交易。

However, the user needs to trust the mixing service to return the bitcoin and also to not be saving logs about the relations between the money received and sent.\

但是，用户需要信任混合服务以返回比特币，也不要保存有关接收和发送的货币之间关系的日志。
Some other services can be also used as mixers, like Bitcoin casinos where you can send bitcoins and retrieve them later.

其他一些服务也可以用作搅拌机，例如比特币赌场，您可以在其中发送比特币并稍后再检索。

## CoinJoin

**CoinJoin** will **mix several transactions of different users into just one** in order to make more **difficult** for an observer to find out **which input is related to which output**.\

** COINJOIN **将**将几个不同用户的几笔交易混合到一个**中，以使观察者更难**难以** **发现**哪个输入与输出**。
This offers a new level of privacy, however, **some** **transactions** where some input and output amounts are correlated or are very different from the rest of the inputs and outputs **can still be correlated** by the external observer.

但是，这提供了一个新的隐私级别，**一些** **事务**，其中某些输入和输出量相关或与其余输入和输出完全不同**仍然可以通过**相关联** 外部观察者。

Examples of (likely) CoinJoin transactions IDs on bitcoin's blockchain are `402d3e1df685d1fdf82f36b220079c1bf44db227df2d676625ebcbee3f6cb22a` and `85378815f6ee170aa8c26694ee2df42b99cff7fa9357f073c1192fff1f540238`.

Examples of (likely) CoinJoin transactions IDs on bitcoin's blockchain are `402d3e1df685d1fdf82f36b220079c1bf44db227df2d676625ebcbee3f6cb22a` and `85378815f6ee170aa8c26694ee2df42b99cff7fa9357f073c1192fff1f540238`.

[**https://coinjoin.io/en**](https://coinjoin.io/en)\
**Similar to coinjoin but better and for ethereum you have** [**Tornado Cash**](https://tornado.cash) **(the money is given from miners, so it jus appear in your waller).**

**类似于CoinJoin，但更好，对于以太坊，您有** [**龙卷风现金**]（https://tornado.cash）**（这笔钱来自矿工，所以它出现在您的Waller中）。 **

## PayJoin

The type of CoinJoin discussed in the previous section can be easily identified as such by checking for the multiple outputs with the same value.

可以通过检查具有相同值的多个输出，可以轻松地识别上一节中讨论的共同Join类型。

PayJoin (also called pay-to-end-point or P2EP) is a special type of CoinJoin between two parties where one party pays the other. The transaction then **doesn't have the distinctive multiple outputs** with the same value, and so is not obviously visible as an equal-output CoinJoin. Consider this transaction:

Payjoin（也称为付费点或P2EP）是两方之间的一种特殊类型的共同点，其中一个政党支付另一方。 然后，**的交易没有具有相同值的独特多重输出**，因此显然看不到等值的共同Join。 考虑此交易：

```
2 btc --> 3 btc
5 btc     4 btc
```

It could be interpreted as a simple transaction paying to somewhere with leftover change (ignore for now the question of which output is payment and which is change). Another way to interpret this transaction is that the 2 BTC input is owned by a merchant and 5 BTC is owned by their customer, and that this transaction involves the customer paying 1 BTC to the merchant. There is no way to tell which of these two interpretations is correct. The result is a coinjoin transaction that breaks the common-input-ownership heuristic and improves privacy, but is also **undetectable and indistinguishable from any regular bitcoin transaction**.

它可以被解释为简单的交易，用于剩余的变更的某个地方（现在忽略了哪个输出是付款以及哪些是更改的问题）。 解释这项交易的另一种方法是，2 BTC输入归商家所有，而5 BTC归客户所有，并且此交易涉及向商人支付1 BTC的客户。 没有办法说出这两个解释中的哪一个是正确的。 结果是一项共同交易，破坏了共同的输入启发式启发式并改善了隐私，但与任何常规的比特币交易**都无法发现并且无法区分。

If PayJoin transactions became even moderately used then it would make the **common-input-ownership heuristic be completely flawed in practice**. As they are undetectable we wouldn't even know whether they are being used today. As transaction surveillance companies mostly depend on that heuristic, as of 2019 there is great excitement about the PayJoin idea.

如果Payjoin交易甚至适度地使用，那么这将使**共同输入所有权启发式启发式在实践中完全有缺陷**。 由于它们是无法检测的，我们甚至都不知道它们是否正在使用。 由于交易监视公司大多依赖于该启发式，因此截至2019年，薪资的想法令人兴奋。

# Bitcoin Privacy Good Practices

＃比特币隐私良好实践

## Wallet Synchronization

##钱包同步

Bitcoin wallets must somehow obtain information about their balance and history. As of late-2018 the most practical and private existing solutions are to use a **full node wallet** (which is maximally private) and **client-side block filtering** (which is very good).

比特币钱包必须以某种方式获得有关其平衡和历史的信息。 截至2018年底，最实用和最私人的现有解决方案是使用**完整的节点钱包**（最大私有节点）和**客户端块过滤**（非常好）。

* **Full node:** Full nodes download the entire blockchain which contains every on-chain [transaction](https://en.bitcoin.it/wiki/Transaction) that has ever happened in bitcoin. So an adversary watching the user's internet connection will not be able to learn which transactions or addresses the user is interested in.

***完整节点：**完整节点下载包含所有链链[交易]（https://en.bitcoin.it/wiki/transaction）的整个区块链。 因此，观看用户的Internet连接的对手将无法了解用户感兴趣的哪些交易或解决方案。
* **Client-side block filtering:** Client-side block filtering works by having **filters** created that contains all the **addresses** for every transaction in a block. The filters can test whether an **element is in the set**; false positives are possible but not false negatives. A lightweight wallet would **download** all the filters for every **block** in the **blockchain** and check for matches with its **own** **addresses**. Blocks which contain matches would be downloaded in full from the peer-to-peer network, and those blocks would be used to obtain the wallet's history and current balance.

***客户端块过滤：**通过拥有**过滤器**创建的客户端块过滤作品，其中包含所有**地址**的所有交易**。 过滤器可以测试**元素是否在集合中**； 假阳性是可能的，但不是假否定的。 轻巧的钱包将**下载** **区块链**中每个**块**的所有过滤器，并检查其**自己的** **地址**的匹配项**。 包含匹配的块将从点对点网络中全部下载，这些块将用于获得钱包的历史记录和当前平衡。

## Tor

## tor

Bitcoin network uses a peer-to-peer network, which means that other peers can learn your IP address. This is why it's recommend to **connect through Tor every time you want to interact with the bitcoin network**.

比特币网络使用对等网络，这意味着其他对等方可以学习您的IP地址。 这就是为什么建议每次您要与比特币网络进行交互时，建议通过TOR连接**。

## Avoiding address reuse

**Addresses being used more than once is very damaging to privacy because that links together more blockchain transactions with proof that they were created by the same entity**. The most private and secure way to use bitcoin is to send a brand **new address to each person who pays you**. After the received coins have been spent the address should never be used again. Also, a brand new bitcoin address should be demanded when sending bitcoin. All good bitcoin wallets have a user interface which discourages address reuse.

**地址不止一次使用对隐私非常有害，因为这将更多区块链交易与证明它们是由同一实体创建的证明**。 使用比特币的最私密和安全的方法是向每个付款的人发送品牌**的新地址**。 在收到的硬币上花费后，再也不应再使用地址了。 此外，发送比特币时，应要求全新的比特币地址。 所有优质的比特币钱包都有一个用户界面，该界面阻止地址重复使用。

## Multiple transactions

**Paying** someone with **more than one on-chain transaction** can greatly reduce the power of amount-based privacy attacks such as amount correlation and round numbers. For example, if the user wants to pay 5 BTC to somebody and they don't want the 5 BTC value to be easily searched for, then they can send two transactions for the value of 2 BTC and 3 BTC which together add up to 5 BTC.

**支付**拥有多个链接交易的人**可以大大降低基于金额的隐私攻击的力量，例如数量相关和圆数。 例如，如果用户想向某人支付5 BTC，并且他们不希望轻松搜索5个BTC值，那么他们可以为2个BTC和3 BTC的值发送两次交易，这些交易总计为5 BTC。

## Change avoidance

Change avoidance is where transaction inputs and outputs are carefully chosen to not require a change output at all. **Not having a change output is excellent for privacy**, as it breaks change detection heuristics.

避免变化是仔细选择交易输入和输出以完全不需要更改输出的地方。 **没有更改输出对于隐私**非常好，因为它破坏了变化检测启发式方法。

## Multiple change outputs

##多个更改输出

If change avoidance is not an option then **creating more than one change output can improve privacy**. This also breaks change detection heuristics which usually assume there is only a single change output. As this method uses more block space than usual, change avoidance is preferable.

如果避免更改不是选项，则**创建多个更改输出可以改善隐私**。 这也打破了变化检测启发式方法，通常假设只有单个变化输出。 由于该方法使用的块空间比平时更多，因此避免更改是可取的。

# Monero

When Monero was developed, the gaping need for **complete anonymity** was what it sought to resolve, and to a large extent, it has filled that void.

当开发Monero时，对**完全匿名**的厌恶需求是它试图解决的问题，并且在很大程度上，它填补了这一空白。

# Ethereum

## Gas

Gas refers to the unit that measures the **amount** of **computational** **effort** required to execute specific operations on the Ethereum network. Gas refers to the **fee** required to successfully conduct a **transaction** on Ethereum.

GAS是指测量**计算** ** **的**金额**的单位**在以太坊网络上执行特定操作所需的单位。 GAS是指成功进行以太坊的**交易**所需的**费用。

Gas prices are denoted in **gwei**, which itself is a denomination of ETH - each gwei is equal to **0.000000001 ETH** (10-9 ETH). For example, instead of saying that your gas costs 0.000000001 ether, you can say your gas costs 1 gwei. The word 'gwei' itself means 'giga-wei', and it is equal to **1,000,000,000 wei**. Wei itself is the **smallest unit of ETH**.

汽油价格在** gwei **中表示，这本身就是ETH的面额 - 每个GWEI等于** 0.000000001 eth **（10-9 eth）。 例如，您不必说您的天然气成本为0.000000001，而是可以说汽油成本为1 GWEI。 “ gwei”本身的意思是“ giga-wei”，它等于** 1,000,000,000 wei **。 WEI本身是ETH **的**最小单位。

To calculate the gas that a transaction is going to cost read this example:

为了计算交易将要花费的气体，请阅读此示例：

Let’s say Jordan has to pay Taylor 1 ETH. In the transaction the gas limit is 21,000 units and the base fee is 100 gwei. Jordan includes a tip of 10 gwei.

假设乔丹必须支付泰勒1 ETH。 在交易中，气体限额为21,000台，基本费用为100 GWEI。 约旦包括10 GWEI的小费。

Using the formula above we can calculate this as `21,000 * (100 + 10) = 2,310,000 gwei` or 0.00231 ETH.

使用上面的公式，我们可以将其计算为`21,000 *（100 + 10）= 2,310,000 Gwei`或0.00231 ETH。

When Jordan sends the money, 1.00231 ETH will be deducted from Jordan's account. Taylor will be credited 1.0000 ETH. Miner receives the tip of 0.00021 ETH. Base fee of 0.0021 ETH is burned.

当约旦寄钱时，将从约旦的帐户中扣除1.00231 ETH。 泰勒将获得1.0000 ETH。 矿工收到0.00021 ETH的尖端。 基本费用为0.0021 ETH。

Additionally, Jordan can also set a max fee (`maxFeePerGas`) for the transaction. The difference between the max fee and the actual fee is refunded to Jordan, i.e. `refund = max fee - (base fee + priority fee)`. Jordan can set a maximum amount to pay for the transaction to execute and not worry about overpaying "beyond" the base fee when the transaction is executed.

此外，约旦还可以为交易设置最大费用（``Maxfeepergas'）。 最高费用和实际费用之间的差额退还给约旦，即`newud =最大费用 - （基本费用 +优先费）。 乔丹可以将最高金额设置为以执行交易的费用，而不必担心在执行交易时超出基本费用。

As the base fee is calculated by the network based on demand for block space, this last param: maxFeePerGas helps to control the maximum fee that is going to be payed.

由于基本费用由网络根据块空间的需求计算，因此最后一个参数：MaxFeepergas有助于控制将要支付的最高费用。

## Transactions

Notice that in the **Ethereum** network a transaction is performed between 2 addresses and these can be **user or smart contract addresses**.\

请注意，在**以太坊**网络中，在2个地址之间执行交易，这些交易可以是**或智能合约地址**。
**Smart Contracts** are stored in the distributed ledger via a **special** **transaction**.

**智能合约**通过A Special ** **交易**存储在分布式分类帐中。

Transactions, which change the state of the EVM, need to be broadcast to the whole network. Any node can broadcast a request for a transaction to be executed on the EVM; after this happens, a **miner** will **execute** the **transaction** and propagate the resulting state change to the rest of the network.\

改变EVM状态的交易需要广播到整个网络。 任何节点都可以广播在EVM上执行交易的请求； 发生这种情况之后，**矿工**将**执行** **事务**并将结果状态更改为网络的其余部分。\ \ \ \
Transactions require a **fee** and must be mined to become valid.

交易需要**费**，必须开采才能有效。

A submitted transaction includes the following information:

提交的交易包括以下信息：

* `recipient` – the receiving address (if an externally-owned account, the transaction will transfer value. If a contract account, the transaction will execute the contract code)

*`ceversient“  - 接收地址（如果外部拥有的帐户，交易将转移价值。如果合同帐户，交易将执行合同代码）
* `signature` – the identifier of the sender. This is generated when the sender's private key signs the transaction and confirms the sender has authorised this transaction

*`'签名 - 发件人的标识符。 当发送者的私钥标志交易并确认发件人已授权此交易时，这将生成。
* `value` – amount of ETH to transfer from sender to recipient (in WEI, a denomination of ETH)

*`'value' - 从发送者转移到收件人的ETH数量（在WEI中，ETH的面额）
* `data` – optional field to include arbitrary data
* `gasLimit` – the maximum amount of gas units that can be consumed by the transaction. Units of gas represent computational steps

*``Gaslimit'  - 交易可以消耗的最大气体单位。 气体单位代表计算步骤
* `maxPriorityFeePerGas` - the maximum amount of gas to be included as a tip to the miner

*``MaxPriorityFeepergas`-将最大的气体作为矿工提示
* `maxFeePerGas` - the maximum amount of gas willing to be paid for the transaction (inclusive of `baseFeePerGas` and `maxPriorityFeePerGas`)

*`maxfeepergas`-愿意为交易支付的最大气体（包括``basefeepergas''和``Maxpriorityfeeperga''）

Note that there isn't any field for the origin address, this is because this can be extrapolated from the signature.

请注意，原点地址没有任何字段，这是因为可以从签名中推断出来。

# References

* [https://en.wikipedia.org/wiki/Proof\_of\_stake](https://en.wikipedia.org/wiki/Proof\_of\_stake)

* [https://en.wikipedia.org/wiki/prof/prof \_of_stake]（
* [https://www.mycryptopedia.com/public-key-private-key-explained/](https://www.mycryptopedia.com/public-key-private-key-explained/)
* [https://bitcoin.stackexchange.com/questions/3718/what-are-multi-signature-transactions](https://bitcoin.stackexchange.com/questions/3718/what-are-multi-signature-transactions)
* [https://ethereum.org/en/developers/docs/transactions/](https://ethereum.org/en/developers/docs/transactions/)
* [https://ethereum.org/en/developers/docs/gas/](https://ethereum.org/en/developers/docs/gas/)
* [https://en.bitcoin.it/wiki/Privacy](https://en.bitcoin.it/wiki/Privacy#Forced\_address\_reuse)


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


