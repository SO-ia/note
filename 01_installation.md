## VSCode

### extensions

#### 路径自动补全

##### Path Intellisense

1. 打开扩展商店(Ctrl + Shift + X 或 左侧插件按钮)，搜索 Path Intellisense，点击 install 安装

2. 配置插件

   ```json
   {
       "path-intellisense.mappings": {
               "/": "/", // ”/“ 系统根目录
               "~": "D:/A_Project", // ”~“ home目录
               ".": "${workspaceFolder}" // ”.“ 设置 VScode 的 workspaceFolder，作为插件的 workspaceFolder
               // "abs_path": "/home/user/path/to/directory" // Alias for absolute path to directory.  
       }
   }
   ```




#### Python

##### 括号自动补全

- Name: Pylance
  Id: ms-python.vscode-pylance
  Description: A performant, feature-rich language server for Python in VS Code
  Version: 2024.2.4
  Publisher: Microsoft
  VS Marketplace Link: https://marketplace.visualstudio.com/items?itemName = ms-python.vscode-pylance

- 设置 -> 扩展 -> Pylance -> 将 python.analysis.completeFunctionParens 下方的选项打勾
  ***或***
  直接在 settings.json 中添加 `"python.analysis.completeFunctionParens": true`

##### Python

- Name: Python
  Id: ms-python.python
  Description: Python language support with extension access points for IntelliSense (Pylance), Debugging (Python Debugger), linting, formatting, refactoring, unit tests, and more.
  Version: 2023.14.0
  Publisher: Microsoft
  VS Marketplace Link: https://marketplace.visualstudio.com/items?itemName = ms-python.python

##### Debugger

- Name: Python Debugger
  Id: ms-python.debugpy
  Description: Python Debugger extension using debugpy.
  Version: 2024.0.0
  Publisher: Microsoft
  VS Marketplace Link: https://marketplace.visualstudio.com/items?itemName = ms-python.debugpy

##### Env manager

- Name: Python Environment Manager (deprecated)
  Id: donjayamanne.python-environment-manager
  Description: View and manage Python environments & packages.
  Version: 1.0.4
  Publisher: Don Jayamanne
  VS Marketplace Link: https://marketplace.visualstudio.com/items?itemName = donjayamanne.python-environment-manager

##### python 热门包推荐

- Name: Python Extension Pack
  Id: donjayamanne.python-extension-pack
  Description: Popular Visual Studio Code extensions for Python
  Version: 1.7.0
  Publisher: Don Jayamanne
  VS Marketplace Link: https://marketplace.visualstudio.com/items?itemName = donjayamanne.python-extension-pack

##### Python 语言自动格式化

https://blog.csdn.net/breaksoftware/article/details/128804572



#### Remote SSH

```
ssh -p xxxxx root@rexxxxxd.com
```



##### error

###### 1

```powershell
[09:36:50.162] Running script with connection command: "C:\Windows\System32\OpenSSH\ssh.exe" -T -D 60283 "regixxx.com" bash
[09:36:50.166] Terminal shell path: C:\WINDOWS\System32\cmd.exe
[09:36:50.382] > 9001h 1004h
[09:36:50.382] Got some output, clearing connection timeout
[09:36:50.552] > kex_exchange_identification: read: Connection reset
> ]0;C:\WINDOWS\System32\cmd.exe 
[09:36:50.570] > Connection reset by 120.xx.xxx.xxx port xxxxx
> 过程试图写入的管道不存在。
[09:36:52.567] "install" terminal command done
[09:36:52.568] Install terminal quit with output: 过程试图写入的管道不存在。
[09:36:52.568] Received install output: 过程试图写入的管道不存在。
[09:36:52.569] Failed to parse remote port from server output
[09:36:52.571] Resolver error: Error: 
	at m.Create (c:\Users\username\.vscode\extensions\ms-vscode-remote.remote-ssh-0.102.0\out\extension.js:1:584145)
	at t.handleInstallOutput (c:\Users\username\.vscode\extensions\ms-vscode-remote.remote-ssh-0.102.0\out\extension.js:1:582705)
	at t.tryInstall (c:\Users\username\.vscode\extensions\ms-vscode-remote.remote-ssh-0.102.0\out\extension.js:1:681881)
	at async c:\Users\username\.vscode\extensions\ms-vscode-remote.remote-ssh-0.102.0\out\extension.js:1:644110
	at async t.withShowDetailsEvent (c:\Users\username\.vscode\extensions\ms-vscode-remote.remote-ssh-0.102.0\out\extension.js:1:647428)
	at async t.resolve (c:\Users\username\.vscode\extensions\ms-vscode-remote.remote-ssh-0.102.0\out\extension.js:1:645160)
	at async c:\Users\username\.vscode\extensions\ms-vscode-remote.remote-ssh-0.102.0\out\extension.js:1:720916
[09:36:52.582]
```

solution

- remote.SSH: Config File

  填入以下绝对路径

  ```
  C:\Users\username\.ssh\config
  ```

  config 文件内容如下

  ```powershell
  Host regxxx.com
    HostName regixxx.com
    Port xxxx
    User root
  ```

  <font color=red> not work </font>

- 可能是公司内网防火墙设置







#### Jupyter

##### Cell命令模式

目前支持的Jupyter Notebook快捷:

| 快捷键      | 备注                                                 |
| ----------- | ---------------------------------------------------- |
| Enter       | 转入编辑模式                                         |
| Shift-Enter | 运行本单元，选中或插入（最后一个Cell的时候）下个单元 |
| Ctrl-Enter  | 运行本单元                                           |
| Alt-Enter   | 运行本单元，在其下插入新单元                         |
| y           | 单元转入代码状态                                     |
| m           | 单元转入markdown状态 （目前尚不支持R 原生状态）      |
| up          | 选中上方单元                                         |
| k           | 选中上方单元                                         |
| down        | 选中下方单元                                         |
| j           | 选中下方单元                                         |
| a           | 在上方插入新单元                                     |
| b           | 在下方插入新单元                                     |
| dd          | 删除选中的单元                                       |
| l           | 转换行号                                             |
| Shift-Space | 向上滚动                                             |
| Space       | 向下滚动                                             |

##### Cell编辑模式

快捷键(只描述与编辑相关的那些快捷键):

| 快捷键                    | 备注                                                         |
| ------------------------- | ------------------------------------------------------------ |
| Ctrl + X                  | 剪切/剪切行（空选定）                                        |
| Ctrl + C                  | 复制/复制行（空选定）                                        |
| Ctrl + Delete / Backspace | 删除右边、左边的字                                           |
| Alt + ↑ / ↓               | 向上/向下移动行                                              |
| Shift + Alt + ↓ / ↑       | 向上/向下复制行                                              |
| Ctrl + Shift + K          | 删除行                                                       |
| Ctrl + Shift + \          | 跳到匹配的括号                                               |
| Ctrl + ] / [              | 缩进/突出行                                                  |
| Ctrl + ← / →              | 光标到字首/字尾                                              |
| Ctrl + /                  | 切换行注释                                                   |
| Shift + Alt + A           | 切换块注释                                                   |
| Ctrl + H                  | 查找/替换Vscode的查找快捷键 Ctrl + F 目前在Cell里不能用，但是替换快捷键可以使用，因此可以替代原本的查找功能 |





### settings

#### 插件安装位置

https://blog.csdn.net/weixin_43751329/article/details/122506815



### clear cache

route: **C:\Users\username\AppData\Local\Microsoft\vscode-cpptools**

reference: [link](https://www.52pojie.cn/forum.php?mod=viewthread&tid=1959079)

> 非常感谢该博客的整理，在此引用并在下方粘贴全文

VsCode 是一款 **轻量级** 代码编辑器

可用一段就会很快发现，“轻量级”的 VsCode 并不轻量

不统计不知道，一统计吓一跳，使用了一段时间后，VsCode 占用了我 C 盘 10G+的空间！

好家伙，于是我决定治理一下 VsCode，让 VsCode 变得真正的轻量级。

#### VsCode 的空间占用分析

VsCode 所占用的空间，主要包括四大部分（下面是我写此博客时统计的结果）：

1. `程序的安装目录`：大约会占用 350M
2. `%userprofile%\.vscode`：可达 800M。主要为：各个拓展。VsCode 卸载拓展似乎不会删除硬盘上的文件，因此这个里面很大，并且混有很多不用的
3. `%userprofile%\AppData\Local\Microsoft\vscode-cpptools\ipch`：用一段时间能达到 4G 与 C(++)语言有关，关闭程序后可以直接删。不使用 VsCode 编辑 C/C++的用户可能无此痛苦
4. `%userprofile%\AppData\Roaming\Code`：2G+ 存放用户数据、配置等。 （可以通过启动时添加--user-data-dir NewDir 来使其他目录作为配置）

可以定期删除的地方，有 `3. ipch`（可完全删除） 和 `4. Romaing`（不可完全删除）

##### 4. Romaing 中，到底哪些可以定期删除

对 `%userprofile%\AppData\Roaming\Code` 中的文件进行更进一步地分析，我得到了如下结论：

```css
%userprofile%\AppData\Roaming\Code\CachedExtensionVSIXs   用一段时间可以达到500M   可以直接删
%userprofile%\AppData\Roaming\Code\Cache       很快几十M
%userprofile%\AppData\Roaming\Code\CachedData  很快几十M
%userprofile%\AppData\Roaming\Code\CachedExtensions  安装新插件时，似乎默认不会自动删除，安装插件一多能达到800M
%userprofile%\AppData\Roaming\Code\CachedExtensionVSIXs 反正也是与插件有关的，也能达到几百M
%userprofile%\AppData\Roaming\Code\Code Cache    十几M
%userprofile%\AppData\Roaming\Code\Crashpad      十几M  用来存放崩溃信息
%userprofile%\AppData\Roaming\Code\logs          几十M  这个可以直接删，用来存放日志记录
%userprofile%\AppData\Roaming\Code\Service Worker 1G    
    %userprofile%\AppData\Roaming\Code\Service Worker\CacheStorage   1G  主要位于这里
    %userprofile%\AppData\Roaming\Code\Service Worker\ScriptCache    10M
%userprofile%\AppData\Roaming\Code\User          600M
    %userprofile%\AppData\Roaming\Code\User\workspaceStorage  500M  每打开一个工作目录就会在这个目录下生成一个文件夹
    %userprofile%\AppData\Roaming\Code\User\History           100M
            每Ctrl+S(仅限有修改的成功的重新保存)一次就会生成一个副本。
            这个不是按git的思路只存放更改，而是整个文件全部Copy一份。
            一个100多k的源码保存十次就是1M，对于习惯随手Ctrl+S的用户会占用较大的空间
            但是，删除之后将会影响历史版本的还原。
            其中，文件名采用了代码混淆技术，每个文件会生成一个文件夹，真正的文件名、各个文件对应文件保存时间都在每个文件夹下的entries.json中
    %userprofile%\AppData\Roaming\Code\User\snippets    这个不能删，并且重装还得记得备份（如果没有自动还原的话）这个是用户自定义的代码片段
```

#### 定时删除目录

1. `%userprofile%\AppData\Local\Microsoft\vscode-cpptools\ipch`
2. `%userprofile%\AppData\Roaming\Code\CachedExtensionVSIXs`
3. `%userprofile%\AppData\Roaming\Code\Cache`
4. `%userprofile%\AppData\Roaming\Code\CachedData`
5. `%userprofile%\AppData\Roaming\Code\CachedExtensions`
6. `%userprofile%\AppData\Roaming\Code\CachedExtensionVSIXs`
7. `%userprofile%\AppData\Roaming\Code\Code Cache`
8. `%userprofile%\AppData\Roaming\Code\Crashpad`
9. `%userprofile%\AppData\Roaming\Code\logs`
10. `%userprofile%\AppData\Roaming\Code\Service Worker\CacheStorage`
11. `%userprofile%\AppData\Roaming\Code\Service Worker\ScriptCache`
12. `%userprofile%\AppData\Roaming\Code\User\workspaceStorage`
13. `%userprofile%\AppData\Roaming\Code\User\History`

这么多文件夹总不可能手动地一个一个地删除，因此我写了一个脚本：

```bash
 复制代码 隐藏代码@rem example:
@REM del "%userprofile%/AppData/Local/Microsoft/vscode-cpptools/ipch/" /s /q /f
@REM rd "%userprofile%/AppData/Local/Microsoft/vscode-cpptools/ipch/" /s /q
@REM md "%userprofile%/AppData/Local/Microsoft/vscode-cpptools/ipch/"

@echo off

call:EmptyOneDir "%userprofile%\AppData\Local\Microsoft\vscode-cpptools\ipch"
call:EmptyOneDir "%userprofile%\AppData\Roaming\Code\CachedExtensionVSIXs"
call:EmptyOneDir "%userprofile%\AppData\Roaming\Code\Cache"
call:EmptyOneDir "%userprofile%\AppData\Roaming\Code\CachedData"
call:EmptyOneDir "%userprofile%\AppData\Roaming\Code\CachedExtensions"
call:EmptyOneDir "%userprofile%\AppData\Roaming\Code\CachedExtensionVSIXs"
call:EmptyOneDir "%userprofile%\AppData\Roaming\Code\Code Cache"
call:EmptyOneDir "%userprofile%\AppData\Roaming\Code\Crashpad"
call:EmptyOneDir "%userprofile%\AppData\Roaming\Code\logs"
call:EmptyOneDir "%userprofile%\AppData\Roaming\Code\Service Worker\CacheStorage"
call:EmptyOneDir "%userprofile%\AppData\Roaming\Code\Service Worker\ScriptCache"
call:EmptyOneDir "%userprofile%\AppData\Roaming\Code\User\workspaceStorage"
call:EmptyOneDir "%userprofile%\AppData\Roaming\Code\User\History"

goto end

:EmptyOneDir  rem same as Let empty [path] /q
    echo empty %1
    echo del %1 /s /q /f
    del %1 /s /q /f
    echo rd %1 /s /q
    rd %1 /s /q
    echo md %1
    md %1
:end
```

**只需要将这个脚本另存为 CleanVsCode.bat，并定期双击运行一次，就能定期释放大量空间**

当然，释放的空间直接取决于你的 VsCode 所产生的缓存大小，间接取决于你的 VsCode 的使用次数。

最好关闭 VsCode 后再运行脚本。

#### ⚠️Warning

运行脚本后再次运行 VsCode 基本上看不出什么不同，只是当前工作路径下所打开的文件需要重新手动点击打开。

毕竟是一个能删除很多东西的脚本，因此请谨慎使用。

我作为本篇博客的原创博主，只是为大家提供了一个便捷的方法，但是其可能造成的后果，博主并不承担责任。

但是大家可以放心的是，我自己也在定期运行这个脚本。

准备有空的时候将其加入 Windows 计划，以实现定期地自动释放空间。













## Linux











## Docker

### installation

#### log

1. 打开 wsl

   系统 -> 可选功能 -> 相关设置: 更多 Windows 功能

   <img src=".\assets\1.png" alt="1" style="zoom:60%;" />

   需要重启电脑，重启后弹出 cmd 窗口显示如下：

   ```powershell
   适用于 Linux 的 Windows 子系统必须更新到最新版本才能继续。可通过运行 “wsl.exe --update” 进行更新。
   有关详细信息，请访问 https://aka.ms/wslinstall
   
   按任意键安装适用于 Linux 的 Windows 子系统。
   按 CTRL-C 或关闭此窗口以取消。
   此提示将在 60 秒后超时。
   正在下载: 适用于 Linux 的 Windows 子系统 2.4.13
   正在安装: 适用于 Linux 的 Windows 子系统 2.4.13
   已安装 适用于 Linux 的 Windows 子系统 2.4.13。
   正在安装 Windows 可选组件: VirtualMachinePlatform
   
   部署映像服务和管理工具
   版本: 10.0.26100.1150
   
   映像版本: 10.0.26100.1742
   
   启用一个或多个功能
   [==========================100.0%==========================]
   操作成功完成。
   请求的操作成功。直到重新启动系统前更改将不会生效。
   正在检查更新。
   已安装最新版本的适用于 Linux 的 Windows 子系统。
   按任意键即可退出...
   ```

   

2. 安装包下载

   https://desktop.docker.com/win/main/amd64/Docker%20Desktop%20Installer.exe?utm_source = docker&utm_medium = webreferral&utm_campaign = dd-smartbutton&utm_location = module

   

3. 安装

   cmd 进入安装包目录

   ```powershell
   start /w "" "Docker Desktop Installer.exe" install -accept-license --installation-dir="D:\Program Files\Docker" --wsl-default-data-root="D:\Program Files\Docker\data" --windows-containers-default-data-root="D:\\Program Files\\Docker"
   ```

   - D:\Program Files\Docker 是 Docker Desktop `.exe` 安装程序的安装目录
   - D:\Program Files\Docker\data 是 Docker 存放是 Docker 用于存储镜像、容器、卷等数据的目录
   - D:\Program Files\Docker，表示在 Windows 操作系统中，Docker 程序将被安装在 D 盘的 Program Files 文件夹内的一个名为 Docker 的子文件夹中，记得 **双斜杠**。

   `在运行代码前，一定要提前手动创建好对应文件夹，不然会报错。`
   
   

#### installation reference

[windows10 docker 安装在 D 盘_windows10 docker 安装到 d-CSDN 博客](https://blog.csdn.net/liangcsdn111/article/details/110236655?spm=1001.2101.3001.6650.6&utm_medium=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~Ctr-6-110236655-blog-144635357.235^v43^pc_blog_bottom_relevance_base9&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~Ctr-6-110236655-blog-144635357.235^v43^pc_blog_bottom_relevance_base9&utm_relevant_index=8)

[Windows 装 Docker 至 D 盘/其他盘（最新，最准确，直接装）_docker 安装到 d 盘-CSDN 博客](https://blog.csdn.net/m0_51290571/article/details/144635357)

[Windows10 上开启 WSL2(Windows Subsystem for Linux 2)及 Docker Desktop For Windows - TaylorShi - 博客园](https://www.cnblogs.com/taylorshi/p/13586922.html)

[Windows 11 安装 WSL2 - 知乎](https://zhuanlan.zhihu.com/p/475462241)









## Windows

### 桌面

1. 切换桌面
   Windows 徽标键 + Ctrl + 左右方向键
   
2. 打开桌面选择窗口
   Windows 徽标键 + Tab

   > 按 Tab 切换: 窗口选择 — 桌面选择 — 新建桌面

3. 切换窗口
   Alt + tab
   
4. 高级系统设置

   win + R —> sysdm.cpl





### Typora

#### 格式插件 pandoc

1. 其他格式转换 —— 需安装 `pandoc`

2. GitHub 最新安装包网址 https://github.com/jgm/pandoc/releases/lastest

3. Windows 选择 `pandoc-*-window.msi`

   - 本次选择 [pandoc-3.6.4-windows-x86_64.msi](https://github.com/jgm/pandoc/releases/download/3.6.4/pandoc-3.6.4-windows-x86_64.msi)
   - [下载链接](https://objects.githubusercontent.com/github-production-release-asset-2e65be/571770/218b3377-0d49-4ef9-baf0-64272fbc5df0?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=releaseassetproduction%2F20250415%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250415T011103Z&X-Amz-Expires=300&X-Amz-Signature=1dfb4a7344792ffc55c68d977ba830a9dfd7c633266c6e95b6400688b6869344&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B%20filename%3Dpandoc-3.6.4-windows-x86_64.msi&response-content-type=application%2Foctet-stream)

   ```powershell
   C:\Users\username>pandoc --version
   pandoc 3.6.4
   Features: +server +lua
   Scripting engine: Lua 5.4
   User data directory: C:\Users\username\AppData\Roaming\pandoc
   Copyright (C) 2006-2024 John MacFarlane. Web: https://pandoc.org
   This is free software; see the source for copying conditions. There is no warranty, not even for merchantability or fitness for a particular purpose.
   ```

   

#### 字体格式 Font 

##### Markdown 语法

<table> <tr> <td bgcolor=lightgrey> 背景色 yellow </td> </tr> </table>

##### example

<font color=red> 我是红色 </font>
<font color=#008000> 我是绿色 </font>
<font color=yellow> 我是黄色 </font>
<font color=Blue> 我是蓝色 </font>
<font color= #871F78> 我是紫色 </font>
<font color= #888888> 我是浅灰色 </font>
<font size=3> 我是尺寸 </font>
<font face="楷体" color=#777707 size=2> 我是楷体，绿色，尺寸为 2 </font>

`Ctrl 0` 到 `Ctrl 6`： **普通文本、一级文本~六级文本**

`Ctrl B`： 加粗；**加粗测试**

`Ctrl I`： 斜体；*斜体测试*

`Ctrl U`： 下划线；下划线测试

`Shift Alt 5`： 删除线；删除线测试

`Shift Ctrl ~`： 行内代码块；`行内代码块测试`

`Ctrl K`： 超链接，[超链接测试；欢迎点一个大大的关注！！！]([《LL》 - 博客园 (cnblogs.com)](https://www.cnblogs.com/liulia/))；还支持文章内锚点，按**`Ctrl`** 键点击此处 👉[第一节](https://www.cnblogs.com/liulia/p/14837982.html#Markdown快速入门常用快捷键（typora）)

`Ctrl T`： 表格，支持拖拽移动、网页端表格复制转换

`Ctrl Shift Q`： 引用；

`Shift Ctrl I`： 插入图片；

`Shift Ctrl M`： 公式块；

`- [ ] `： 任务列表(可勾选的序列)**注意每一个符号之间都有空格**

`<sup> 内容 </sup>`： 上标；上标测试

`<sub> 内容 </sub>`： 下标； 下标测试 

`[toc]`： 展示目录

`Ctrl l`： 选中一行

`Ctrl d`： 选中内容/单词

`Ctrl home`： 跳转到文章开头

`Ctrl end`： 跳转到文章结尾

`Ctrl f`： 搜索

`Ctrl h`： 替换

`[^内容]`： 脚注标识



#### Mermaid 语法

> references
>
> [Mermaid 使用教程：从入门到精通 - 知乎](https://zhuanlan.zhihu.com/p/627356428)



#### 插件

##### installation

###### typora-plugin

- 项目地址

  https://github.com/obgnail/typora_plugin

- 中文安装说明

  https://github.com/obgnail/typora_plugin/blob/master/README.md

- 所有版本发布地址

  https://github.com/obgnail/typora_plugin/releases

- 当前下载地址

  [link](https://objects.githubusercontent.com/github-production-release-asset-2e65be/658244193/8f0dac9d-a8f8-4191-b523-470fc33a99df?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=releaseassetproduction%2F20250423%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250423T011205Z&X-Amz-Expires=300&X-Amz-Signature=60815ba6a516439656f3c31eec16b214dbb1e66547522ba73972fde8852e1daa&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B%20filename%3Dtypora-plugin%40v1.13.10.zip&response-content-type=application%2Foctet-stream)

- process

  1. 下载压缩包

  2. 将压缩包内的 plugin 文件夹放到 `window.html` 所在的文件夹下
     当前位于 `D:\A_APP\Typora\resources\app`

     ```powershell
     D:\A_APP\Typora\resources\app:.
     │  window.html
     │
     └─plugin
     ```

  3. 运行 `Typora\resources\app\plugin\bin\install_windows_amd_x64.exe`

     运行成功界面如下

     ![7](assets\typora\7.png)

     

---

###### typora-community-plugin

- <font color=darkred> 该项目只适用于 v1.5.x - v1.9.x </font>

- 项目地址

  https://github.com/typora-community-plugin/typora-community-plugin

- 中文安装说明

  https://github.com/typora-community-plugin/typora-community-plugin/blob/main/docs/zh-cn/user-guide/1a-installation.md

- 所有版本发布地址

  https://github.com/typora-community-plugin/typora-community-plugin/releases

- 当前下载地址

  [link](https://objects.githubusercontent.com/github-production-release-asset-2e65be/668291280/cc0bc27e-6861-49c5-87a4-a099193c59b0?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=releaseassetproduction%2F20250422%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250422T014911Z&X-Amz-Expires=300&X-Amz-Signature=5baa3366edab2abbbad34916b323bffbd0b12434f8bdbf3c72a0aa4d7bdd00f0&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B%20filename%3Dtypora-community-plugin.zip&response-content-type=application%2Foctet-stream)

##### error

###### 1. 找不到命令 install.ps1

```powershell
# 原始命令
install.ps1 -root D:\A_APP\Typora

# 修改命令
.\install.ps1 -root D:\A_APP\Typora
```



###### 2. 无法加载文件 .\install.ps1

.\install.ps1 : 无法加载文件 D:\A_APP\Typora\resources\typora-community-plugin\install.ps1。未对文件 D:\A_APP\Typora\resources\typora-community-plugin\install.ps1 进行数字签名。无法在当前系统上运行该脚本。

```
PS D:\A_APP\Typora\resources\typora-community-plugin> set-ExecutionPolicy RemoteSigned
PS D:\A_APP\Typora\resources\typora-community-plugin> get-executionpolicy
RemoteSigned
```

[执行 powershell 脚本出错：未对文件进行数字签名-CSDN 博客](https://blog.csdn.net/qq_36241539/article/details/118525367)



> references
>
> [Typora 插件安装与配置完全指南-CSDN 博客](https://blog.csdn.net/gitblog_01263/article/details/143046583)





#### 设置代码框默认语言

1. D:\A_APP\Typora\resources\app\app\window\frame.js

2. search `select a language`

3. 在 `textContent=e||""` 的 `“”` 内填上 `python`

4. 改后如下

   ```
   textContent=e||"python"
   ```

   





### pycharm

##### 修改 idea 配置文件位置从 C 盘更改到 D 盘

[link](https://sgknight.blog.csdn.net/article/details/129013857?fromshare=blogdetail&sharetype=blogdetail&sharerId=129013857&sharerefer=PC&sharesource=qq_73921758&sharefrom=from_link)





### Google

#### Browser

##### installation

1、创建 D 盘 A_APP\Google 文件夹：分别创建 Chrome 和 PersonData 文件夹
2、创建 C 盘 Google 文件夹:\Program Files\Google；Google 文件夹里面为空
3、删除 C 盘 Google 文件夹::\Program Files (x86)\Google
4、管理员模式运行 cmd
5、创建软连接

```powershell
mklink /d  "C:\Program Files\Google\Chrome"  "D:\A_APP\Google\Chrome"
mklink /d  "C:\Program Files (x86)\Google"  "D:\A_APP\Google"
mklink /d  "C:\Users\username\AppData\Local\Google" "D:\A_APP\Google\PersonData"
```

6、安装 chrome

6、安装 chrome

 命令如下 

```powershell
C:\Windows\System32>mklink /d  "C:\Program Files\Google\Chrome"  "D:\A_APP\Google\Chrome"
为 C:\Program Files\Google\Chrome <<===>> D:\A_APP\Google\Chrome 创建的符号链接

C:\Windows\System32>mklink /d  "C:\Program Files (x86)\Google"  "D:\A_APP\Google"
为 C:\Program Files (x86)\Google <<===>> D:\A_APP\Google 创建的符号链接

C:\Windows\System32>mklink /d  "C:\Users\username\AppData\Local\Google" "D:\A_APP\Google\PersonData"
为 C:\Users\username\AppData\Local\Google <<===>> D:\A_APP\Google\PersonData 创建的 符号链接
```



##### disable update

`trying ……`

```powershell
修改文件夹名称
D:\A_APP\Google\GoogleUpdater.disabled
D:\A_APP\Google\Update.disabled
```

> references
>
> https://stackoverflow.com/questions/18483087/how-to-disable-google-chrome-auto-update













### Configuration

#### Hosts

1. path

   C:\Windows\System32\drivers\etc\hosts

2. github

   ```powershell
   # github speedup
   140.82.112.3	github.com
   185.199.108.154   github.githubassets.com
   140.82.114.22     central.github.com
   185.199.110.133   desktop.githubusercontent.com
   # assets-cdn.github.com update failed
   185.199.108.133   camo.githubusercontent.com
   185.199.108.133   github.map.fastly.net
   146.75.93.194     github.global.ssl.fastly.net
   140.82.114.4      gist.github.com
   185.199.108.153   github.io
   140.82.114.4      github.com
   140.82.112.6      api.github.com
   185.199.109.133   raw.githubusercontent.com
   185.199.108.133   user-images.githubusercontent.com
   185.199.108.133   favicons.githubusercontent.com
   185.199.108.133   avatars5.githubusercontent.com
   185.199.108.133   avatars4.githubusercontent.com
   185.199.108.133   avatars3.githubusercontent.com
   185.199.108.133   avatars2.githubusercontent.com
   185.199.111.133   avatars1.githubusercontent.com
   185.199.108.133   avatars0.githubusercontent.com
   185.199.108.133   avatars.githubusercontent.com
   140.82.114.9      codeload.github.com
   52.217.161.113    github-cloud.s3.amazonaws.com
   52.217.46.140     github-com.s3.amazonaws.com
   52.217.233.145    github-production-release-asset-2e65be.s3.amazonaws.com
   54.231.233.1      github-production-user-asset-6210df.s3.amazonaws.com
   3.5.27.212        github-production-repository-file-5c1aeb.s3.amazonaws.com
   185.199.109.153   githubstatus.com
   140.82.112.18     github.community
   185.199.108.133   media.githubusercontent.com
   ```

   > [github-hosts: 定时更新 github hosts，提高国内用户访问速度。](https://gitee.com/if-the-wind/github-hosts)
   
   <span style="color:#990000; font-weight:bold;">亲测无效 (不排除公司防火墙问题)</span>







## Java Web

### Maven (.m2)

https://ask.csdn.net/questions/7548212







# Bottom