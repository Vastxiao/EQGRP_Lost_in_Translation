# by vastxiao

## 目录结构

- windows/    包含Windows漏洞、后门、利用工具，等配置文件信息。
    * start\_lp.py    可执行py文件，其实调用configure\_lp.py。
    * configure\_lp.py
    * fb.py    可执行py文件，FuzzBunch工具启动文件。
- swift/      包括 银行攻击的一些内容
- oddjob/     包括与ODDJOB 后门相关的doc

## 工具介绍

windows这里包含两个工具：

* FuzzBunch
* DanderSpiritz

### FuzzBunch

FuzzBunch有点类似于metasploit，并且可跨平台，通过fb.py使用。

#### (1)环境使用
1. windows32
2. python-2.6.6.msi
3. pywin32-216.win32-py2.6.exe
4. java
5. 工具放在英文路径下，不能含有中文，目标机防火墙关闭
6. 在windows利用工具目录下创建listeningposts目录(注意不是c:/windows)
7. 复制EQGRP_Lost_in_Translation下的windows目录到工作目录。
8. 通过fb.py启动(windows 命令行窗口运行python fb.py)

**FuzzBunch框架的执行，需要各种配置项，启动fb.py后，根据提示指定：**
1. 目标的IP地址
2. 攻击者的回调地址(就是运行fb.py框架的主机地址);
3. 指示转发选项是否将被使用;
4. 指定log日志目录;
5. 该项目名称。

```
[*] Retargetting Session

[?] Default Target IP Address [] : 192.168.8.1
[?] Default Callback IP Address [] : 192.168.1.101
[?] Use Redirection [yes] : no

[?] Base Log directory [D:\logs] : c:\my_work\logs
[*] Checking c:\my_work\logs for projects
Index     Project
-----     -------
0         Create a New Project

[?] Project [0] :
[?] New Project Name : aaa
[?] Set target log directory to 'c:\my_work\logs\aaa\z192.168.8.1'? [Yes] : yes
```

#### (2)配置完成后的命令帮助

配置完成之后,进入下一步,使用help查看帮助命令:

```
fb > help

Core Commands
=============

  Command         Description
  -------         -----------
  !               Shortcut for shell
  ?               Shortcut for help
  autorun         Set autorun mode
  back            退出当前使用的功能交互模式
  banner          Print the startup banner
  changeprompt    Change the command prompt
  echo            Echo a message
  enter           Enter the context of a plugin
  eof             Quit program (CTRL-D)
  exit            Alias for back
  help            Print out help
  history         Run a previous command.
  info            Print information about the current context
  mark            Mark a session item
  python          Drop to an interactive Python interpreter
  quit            退出fuzzbunch
  redirect        Configure redirection
  resizeconsole   None
  retarget        重设目标ip，回调ip
  script          Run a script
  session         Show session items
  setg            Set a global variable
  shell           Execute a shell command
  show            Show plugin info
  sleep           Sleep for n seconds
  standardop      Print standard OP usage message
  toolpaste       Paste and convert data from external tool output
  unsetg          Unset a global variable
  use             Activate a plugin for use and enter context

fb >
```

#### (3)fb的使用功能分类

fb的使用是通过使用各种模块插件的功能实现的。

这里有fb的功能插件分类：

```
fb > info

--[ Version 3.5.1
  * 2 ImplantConfigs   # 注入配置
  * 0 ListeningPost
  * 15 Exploits        # 漏洞利用相关
  * 16 Touches         # 目标识别和利用漏洞发现
  * 15 Payloads        # 目标攻击成功后的操作
  * 2 Specials
```

#### (4)执行fb各类功能模块

开始执行fb的各类功能是使用use命令来调用相关模块插件：

使用``use <plugin name>``后将会进入相应插件的命令行：

```
fb > use Printjoblist

[!] Entering Plugin Context :: Printjoblist
[*] Applying Global Variables
[+] Set TargetIp => 10.0.10.254
[+] Set NetworkTimeout => 60

fb Touch (Printjoblist) >
```



### DanderSpiritz

# 参考教程

* http://www.360zhijia.com/360anquanke/191386.html
* http://bobao.360.cn/learning/detail/3739.html
* http://www.tuicool.com/articles/ErqAren


