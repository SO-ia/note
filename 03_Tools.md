## VIM

### 常见命令

##### 退出命令

按 ESC 键 跳到命令模式，然后输入: q（不保存）或者: wq（保存） 退出。
: w 保存文件但不退出 vi
: w file 将修改另外保存到 file 中，不退出 vi
: w! 强制保存，不推出 vi
: wq 保存文件并退出 vi
: wq! 强制保存文件，并退出 vi
: q 不保存文件，退出 vi
: q! 不保存文件，强制退出 vi
: e! 放弃所有修改，从上次保存文件开始再编辑命令历史

以: 和/开头的命令都有历史纪录，可以首先键入: 或/然后按上下箭头来选择某个历史命令。

##### 启动 vim

在命令行窗口中输入以下命令即可

vim 直接启动 vim

vim filename 打开 vim 并创建名为 filename 的文件

##### 文件命令

打开单个文件

vim file

同时打开多个文件

vim file1 file2 file3 …

在 vim 窗口中打开一个新文件

: open file

在新窗口中打开文件

: split file

切换到下一个文件

: bn

切换到上一个文件

: bp

查看当前打开的文件列表，当前正在编辑的文件会用 [] 括起来。

: args

打开远程文件，比如 ftp 或者 share folder

: e ftp://192.168.10.76/abc.txt

: e \qadrive\test\1.txt

##### vim 的模式

正常模式（按 Esc 或 Ctrl+[进入） 左下角显示文件名或为空
插入模式（按 i 键进入） 左下角显示–INSERT–
可视模式（不知道如何进入） 左下角显示–VISUAL–

##### 插入命令

i 在当前位置生前插入
I 在当前行首插入
a 在当前位置后插入
A 在当前行尾插入
o 在当前行之后插入一行
O 在当前行之前插入一行

##### 查找命令

/text　　查找 text，按 n 健查找下一个，按 N 健查找前一个。
?text　　查找 text，反向查找，按 n 健查找下一个，按 N 健查找前一个。

vim 中有一些特殊字符在查找时需要转义　　.*[]^%/?~$

: set ignorecase　　忽略大小写的查找
: set noignorecase　　不忽略大小写的查找

##### 查找很长的词

如果一个词很长，键入麻烦，可以将光标移动到该词上，按*或#键即可以该单词进行搜索，相当于/搜索。而#命令相当于?搜索。

: set hlsearch　　高亮搜索结果，所有结果都高亮显示，而不是只显示一个匹配。
: set nohlsearch　　关闭高亮搜索显示
: nohlsearch　　关闭当前的高亮显示，如果再次搜索或者按下 n 或 N 键，则会再次高亮。
: set incsearch　　逐步搜索模式，对当前键入的字符进行搜索而不必等待键入完成。
: set wrapscan　　重新搜索，在搜索到文件头或尾时，返回继续搜索，默认开启。

##### 替换命令

ra 将当前字符替换为 a，当期字符即光标所在字符。
s/old/new/ 用 old 替换 new，替换当前行的第一个匹配
s/old/new/g 用 old 替换 new，替换当前行的所有匹配
%s/old/new/ 用 old 替换 new，替换所有行的第一个匹配
%s/old/new/g 用 old 替换 new，替换整个文件的所有匹配
: 10,20 s/^/ /g 在第 10 行知第 20 行每行前面加四个空格，用于缩进。
ddp 交换光标所在行和其下紧邻的一行。

##### 移动命令

h 左移一个字符
l 右移一个字符，这个命令很少用，一般用 w 代替。
k 上移一个字符
j 下移一个字符

以上四个命令可以配合数字使用，比如 20j 就是向下移动 20 行，5h 就是向左移动 5 个字符，在 Vim 中，很多命令都可以配合数字使用，比如删除 10 个字符 10x，在当前位置后插入 3 个！，3a！，这里的 Esc 是必须的，否则命令不生效。

w 向前移动一个单词（光标停在单词首部），如果已到行尾，则转至下一行行首。此命令快，可以代替 l 命令。
b 向后移动一个单词 2b 向后移动 2 个单词
e，同 w，只不过是光标停在单词尾部
ge，同 b，光标停在单词尾部。
^ 移动到本行第一个非空白字符上。
0（数字 0）移动到本行第一个字符上，
移动到本行第一个字符。同 0 健。
移动到下面 3 行的行尾
gg 移动到文件头。 = [[
G（shift + g） 移动到文件尾。 = ]]
f（find）命令也可以用于移动，fx 将找到光标后第一个为 x 的字符，3fd 将找到第三个为 d 的字符。
F 同 f，反向查找。

跳到指定行，冒号+行号，回车，比如跳到 240 行就是 : 240 回车。另一个方法是行号+G，比如 230G 跳到 230 行。

Ctrl + e 向下滚动一行
Ctrl + y 向上滚动一行
Ctrl + d 向下滚动半屏
Ctrl + u 向上滚动半屏
Ctrl + f 向下滚动一屏
Ctrl + b 向上滚动一屏

##### 撤销和重做

u 撤销（Undo）
U 撤销对整行的操作
Ctrl + r 重做（Redo），即撤销的撤销。

##### 删除命令

x 删除当前字符
3x 删除当前光标开始向后三个字符
X 删除当前字符的前一个字符。X = dh
dl 删除当前字符， dl = x
dh 删除前一个字符
dd 删除当前行
dj 删除上一行
dk 删除下一行
10d 删除当前行开始的 10 行。
D 删除当前字符至行尾。D = d 删除当前字符之后的所有字符（本行）
kdgg 删除当前行之前所有行（不包括当前行）
jdG（jd shift + g） 删除当前行之后所有行（不包括当前行）
: 1,10d 删除 1-10 行
: 11, d 删除所有行
J(shift + j)　　删除两行之间的空行，实际上是合并两行。

##### 拷贝和粘贴

yy 拷贝当前行
nyy 拷贝当前后开始的 n 行，比如 2yy 拷贝当前行及其下一行。
p 在当前光标后粘贴, 如果之前使用了 yy 命令来复制一行，那么就在当前行的下一行粘贴。
shift+p 在当前行前粘贴
: 1,10 co 20 将 1-10 行插入到第 20 行之后。
: 1, 将整个文件复制一份并添加到文件尾部。

正常模式下按 v（逐字）或 V（逐行）进入可视模式，然后用 jklh 命令移动即可选择某些行或字符，再按 y 即可复制

ddp 交换当前行和其下一行
xp 交换当前字符和其后一个字符

##### 剪切命令

正常模式下按 v（逐字）或 V（逐行）进入可视模式，然后用 jklh 命令移动即可选择某些行或字符，再按 d 即可剪切

ndd 剪切当前行之后的 n 行。利用 p 命令可以对剪切的内容进行粘贴
: 1,10d 将 1-10 行剪切。利用 p 命令可将剪切后的内容进行粘贴。
: 1, 10 m 20 将第 1-10 行移动到第 20 行之后。

##### 退出命令

: wq 保存并退出
ZZ 保存并退出
: q! 强制退出并忽略所有更改
: e! 放弃所有修改，并打开原来文件。

##### 窗口命令

: split 或 new 打开一个新窗口，光标停在顶层的窗口上
: split file 或: new file 用新窗口打开文件
split 打开的窗口都是横向的，使用 vsplit 可以纵向打开窗口。
Ctrl+ww 移动到下一个窗口
Ctrl+wj 移动到下方的窗口
Ctrl+wk 移动到上方的窗口

##### 关闭窗口

: close 最后一个窗口不能使用此命令，可以防止意外退出 vim。
: q 如果是最后一个被关闭的窗口，那么将退出 vim。
ZZ 保存并退出。

关闭所有窗口，只保留当前窗口

: only

##### 录制宏

按 q 键加任意字母开始录制，再按 q 键结束录制（这意味着 vim 中的宏不可嵌套），使用的时候@加宏名，比如 qa。。。q 录制名为 a 的宏，@a 使用这个宏。

##### 执行 shell 命令

:! command
:! ls 列出当前目录下文件
:! perl -c script.pl 检查 perl 脚本语法，可以不用退出 vim，非常方便。
:! perl script.pl 执行 perl 脚本，可以不用退出 vim，非常方便。
: suspend 或 Ctrl - Z 挂起 vim，回到 shell，按 fg 可以返回 vim。

##### 注释命令

perl 程序中#开始的行为注释，所以要注释某些行，只需在行首加入#

3,5 s/^/#/g 注释第 3-5 行
3,5 s/^#//g 解除 3-5 行的注释
1,$ s/^/#/g 注释整个文档。
:%s/^/#/g 注释整个文档，此法更快。

##### 帮助命令

: help or F1 显示整个帮助
: help xxx 显示 xxx 的帮助，比如 : help i, : help CTRL-[（即 Ctrl+[的帮助）
: help ‘number’ Vim 选项的帮助用单引号括起
: help 特殊键的帮助用 <> 扩起
: help -t Vim 启动参数的帮助用-
：help i_ 插入模式下 Esc 的帮助，某个模式下的帮助用模式_主题的模式

帮助文件中位于||之间的内容是超链接，可以用 Ctrl+]进入链接，Ctrl+o（Ctrl + t）返回

##### 其他非编辑命令

. 重复前一次命令

: set ruler?　　查看是否设置了 ruler，在.vimrc 中，使用 set 命令设制的选项都可以通过这个命令查看
: scriptnames　　查看 vim 脚本文件的位置，比如.vimrc 文件，语法文件及 plugin 等。
: set list 显示非打印字符，如 tab，空格，行尾等。如果 tab 无法显示，请确定用 set lcs = tab:>-命令设置了.vimrc 文件，并确保你的文件中的确有 tab，如果开启了 expendtab，那么 tab 将被扩展为空格。

##### Vim 教程

###### 在 Unix 系统上

$ vimtutor

###### 在 Windows 系统上

: help tutor

##### syntax

: syntax 列出已经定义的语法项
: syntax clear 清除已定义的语法规则
: syntax case match 大小写敏感，int 和 Int 将视为不同的语法元素
: syntax case ignore 大小写无关，int 和 Int 将视为相同的语法元素，并使用同样的配色方案







## Git

### 1. Installation

- 下载链接

  [installation link](https://objects.githubusercontent.com/github-production-release-asset-2e65be/23216272/c6c1c87b-d3af-4ae8-9cd6-78a4aea72a77?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=releaseassetproduction%2F20250421%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250421T071022Z&X-Amz-Expires=300&X-Amz-Signature=d21a386a6ebebd71c8a6d5a90407d870f0c8140cad1016735ac8398c9cbded81&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B%20filename%3DGit-2.49.0-64-bit.exe&response-content-type=application%2Foctet-stream)

  [Releases · git-for-windows/git](https://github.com/git-for-windows/git/releases/)

- 项目地址

  [git](https://github.com/git/git)

- 说明文档

  [中文](https://git-scm.com/book/zh/v2)

  [English](https://git-scm.com/book/en/v2)

- 确认安装目录为 `D:A_APP\Git`
  ![0](assets/git/0.png)

- 选择安装组件
  ![1](assets/git/1.png)

  1. Windows Explorer integration（Windows 资源管理器集成）：
     Git 会将一些功能集成到 Windows 资源管理器中。
     这样，在 Windows 资源管理器中你可以直接执行 Git 相关操作，如查看文件状态标记、执行 Git 命令等。
  2. Git Bash Here：
     右键单击文件或文件夹时会在菜单中添加 "Git Bash Here" 选项。
     这样你可以通过该选项打开 Git Bash 终端并自动切换到所选文件或文件夹所在的目录。
  3. Git GUI Here：
     右键单击文件或文件夹时会在菜单中添加 "Git GUI Here" 选项。
     这样你可以通过该选项打开 Git GUI 图形化界面并自动切换到所选文件或文件夹所在的目录。
  4. Git LFS (Large File Support)：
     Git 会安装 Git LFS 扩展，用于管理大型文件，如图像、音频和视频文件。
     使用 Git LFS 可以更高效地处理大型文件，并避免将它们存储在 Git 仓库中造成不必要的负担。
  5. Asociate .git* configuration files with the default text editor：
     Git 会关联.gtiignore、.gitattributes 等扩展名为.gt+的配置文件与系统默认的文本编辑器。
     这样你可以直接双击这些文件，在默认文本编辑器中打开并进行编辑。
  6. Associate .sh files to be run with Bash：
     Git 会关联.sh 扩展名的文件与 Bash 终端。
     这样你可以直接双击.sh 文件，在 Bash 终端中运行脚本。
  7. Check daily for Git for Windows updates：
     Git 会每天检查是否有 Git for Windows 的更新版本，并在有更新时提醒你进行更新。
  8. (NEW!) Add a Git Bash Profile to Windows Terminal：
     Git 会将一个 Git Bash 配置文件添加到 Windows Terminal 中。
     Windows Terminal 是 Windows 上的一个多功能终端应用程序，添加 Git Bash 配置文件后可以直接在 Windows Terminal 中使用 Git Bash。
  9. (NEW!) Scalar (Git add-on to manage large scale repositories)：
     Git 会安装 Scalar，这是一个 Git 的附加组件，用于管理大规模仓库。
     Scalar 提供了一些工具和功能，使大规模仓库的克隆、检出等操作更高效。

- 开始菜单目录
  ![2](assets/git/2.png)

- 默认编辑器选择
  ![3](assets/git/3.png)

- 初始化新项目的主干名称
  ![4](assets/git/4.png)

  在最新的 Git 版本中，关于选择默认分支名称（Default Branch Name），有以下几个选项：

  1. 让 Git 决定（Let Git decide）： 这是 Git 2.28 版本之前的默认行为。即在创建新的仓库时，Git 会使用默认的分支名称 master。
  2. 覆盖新的默认分支名称（Override the default branch name for new repositories）： 由于技术和文化因素的考虑，Git 2.28 版本引入了一个新的默认分支名称的选项。你可以将默认分支更改为其他名称（如 main）。

- 调整 git 的环境变量
  ![5](assets/git/5.png)

  1. “Use Git from Git Bash only”（仅使用 Git Bash 中的 Git）： 这是最谨慎的选择，因为它不会修改你的系统环境变量（PATH）。你只能在 Git Bash 中使用 Git 命令行工具。

  2. “Git from the command line and also from 3rd-party software”（从命令行和第三方软件中使用 Git）： 这是推荐的选项，它会将一些最基本的 Git 包装器添加到你的系统环境变量（PATH），以避免在环境中混乱地添加可选的 Unix 工具。你将能够从 Git Bash、命令提示符和 Windows PowerShell 中使用 Git，并且可以在 PATH 中寻找 Git 的任何第三方软件。

  3. “Use Git and optional Unix tools from the Command Prompt”（从命令提示符中使用 Git 和可选的 Unix 工具）： 这个选项会将 Git 和可选的 Unix 工具都添加到你的系统环境变量（PATH）中。需要注意的是，这将覆盖 Windows 中的一些工具（如 "find" 和 "sort"）。只有当你完全理解这些影响并愿意接受时，才应选择这个选项。

     > 根据你的需求和对系统环境变量的了解，选择合适的选项进行安装。如果你不确定该选择哪个选项，推荐选择第二个选项，因为它提供了最大的灵活性，并且能够在多个环境中使用 Git。

- 选择 SSH 可执行文件
  ![6](assets/git/6.png)

  1. “Use bundled OpenSSH”（使用捆绑的 OpenSSH）： 这个选项使用 Git 自带的 ssh.exe。Git 将会安装自己的 OpenSSH（以及相关的二进制文件），并使用它们。
  2. “Use external OpenSSH”（使用外部 OpenSSH）： 这是一个新选项！这个选项使用外部的 ssh.exe。Git 不会安装自己的 OpenSSH（和相关的二进制文件），而是使用在系统环境变量 PATH 中找到的 OpenSSH。
     在选择 SSH 可执行文件时，是指在 Git 配置中设置使用哪个 SSH 客户端程序来进行远程操作和身份验证。

  > 为什么要选择 SSH 可执行文件呢？
  >
  > 这是因为 Git 使用 SSH 协议与远程仓库进行安全通信和身份验证。SSH（Secure Shell）是一种加密的网络协议，用于在不安全网络上安全地执行远程命令和传输数据。通过 SSH，Git 能够连接到远程 Git 仓库并进行操作，例如推送和拉取代码。
  >
  > 选择适当的 SSH 可执行文件对于 Git 很重要，原因如下：
  >
  > 安全性：SSH 提供了一种安全的通信渠道，通过加密和身份验证来保护数据的传输和访问。选择可靠的 SSH 可执行文件有助于确保 Git 与远程仓库之间的通信是安全的，防止数据泄露和未经授权的访问。
  > 兼容性：不同平台和操作系统可能支持不同的 SSH 客户端程序。通过选择适合你操作系统的 SSH 可执行文件，可以确保 Git 在你的环境中正常工作并与远程仓库进行通信。
  > 功能和性能：不同的 SSH 客户端程序可能具有不同的功能和性能特点。根据你对功能和性能的需求，选择适合的 SSH 可执行文件可以提供更好的用户体验和效率。

- 选择 HTTPS 后端传输
  ![7](assets/git/7.png)

  在选择 HTTPS 传输后端时，可以选择 Git 使用哪个 SSL/TLS 库进行 HTTPS 连接。以下是两个可选项及其含义：

  1. 使用 OpenSSL 库： 选择此选项将指示 Git 使用 OpenSSL 库来处理 HTTPS 连接。OpenSSL 是一种广泛使用的开源 SSL/TLS 库，提供了安全的加密和身份验证功能。选择此选项后，Git 将使用预配置的 ca-bundle.crt 文件来验证服务器证书。这个文件中包含了受信任的根证书，用于验证远程服务器的证书是否有效和可信任。
  2. 使用本机 Windows Secure Channel 库： 选择此选项将指示 Git 使用 Windows 本地的 Secure Channel 库来处理 HTTPS 连接。这个库是 Windows 操作系统提供的默认 SSL/TLS 实现，能够与 Windows 证书存储一起工作。选择此选项后，Git 将使用 Windows 证书存储来验证服务器证书。这意味着 Git 将使用操作系统中的证书管理机制，例如 Windows 证书管理器和 Active Directory 域服务，来验证远程服务器的证书。此选项还允许您使用公司内部的根 CA 证书，例如通过 Active Directory 域服务分发的证书。

  > 选择合适的 HTTPS 传输后端取决于您的操作系统和环境要求。如果您使用的是 Windows 操作系统，并且希望能够与 Windows 证书存储一起工作并使用公司内部的根 CA 证书，那么选择本机 Windows Secure Channel 库是一个不错的选择。如果您使用的是其他操作系统或有特定需求，如使用特定版本的 SSL/TLS 库或自定义证书存储机制，那么选择 OpenSSL 库可能更适合。

- 配置行尾转换
  ![8](assets/git/8.png)

  这里也选择第一个，可以保证在 Windows 和 Unix 环境下检出的文件都使用正确的行尾符号，减少由于行尾符号差异引起的问题。

  1. Checkout Windows style, commit Unix style line endings： 这个选项表示在检出（checkout）文本文件时，Git 会将行尾符号 LF （Unix 风格）自动转换为 CRLF （Windows 风格）。而在提交（commit）文本文件时，Git 会将行尾符号 CRLF 转换回 LF。这适用于跨平台项目，特别是在 Windows 环境下进行开发，并且希望在 Windows 上保留 CRLF 行尾符号的习惯。该选项需要将 "core.autocrlf" 设置为 "true"。
  2. Checkout as-is, commit Unix-style line endings： 这个选项表示在检出文本文件时，Git 不会执行任何行尾符号的转换，保持原样。但是在提交文本文件时，Git 会将行尾符号 CRLF 转换为 LF。这适用于跨平台项目，特别是在 Unix 环境下进行开发，并且希望在提交时统一使用 LF 行尾符号。该选项需要将 "core.autocrlf" 设置为 "input"。
  3. Checkout as-is, commit as-is： 这个选项表示在检出和提交文本文件时都不执行行尾符号的转换，保持原样。这个选项通常不推荐用于跨平台项目，因为不同操作系统使用不同的行尾符号（CRLF 或 LF）。如果项目中的文件包含不一致的行尾符号，可能会导致问题。该选项需要将 "core.autocrlf" 设置为 "false"。

- 配置 Git Bash 使用的终端模拟器
  ![9](assets/git/9.png)

  相比之下，cmd 的劣势是较大的，推荐选择第一个

  1. 使用 MinTTY： Git Bash 将使用 MinTTY 作为终端仿真器。MinTTY 具有可调整大小的窗口、非矩形选择以及 Unicode 字体的特性。它适用于与 Win32 控制台程序（如交互式 Python 或 node.js）一起使用，并提供更好的兼容性和功能。在 MinTTY 环境下运行 Windows 控制台程序时，需要使用 "winpty" 来启动。
  2. 使用 Windows 默认控制台窗口： Git 将使用 Windows 的默认控制台窗口(cmd.exe)作为终端仿真器。这个选项适用于与传统的 Windows 控制台程序一起使用，如交互式 Python 或 node.js。然而，Windows 默认控制台窗口的功能相对有限，默认的滚动回退（scroll-back）功能有限，需要配置 Unicode 字体才能正确显示非 ASCII 字符，并且在 Windows 10 之前，它的窗口大小不可自由调整，只允许矩形文本选择。

- git pull 默认行为
  ![10](assets/git/10.png)

  默认情况下，‘git pull’ 的行为取决于 git 配置中的 merge.default 参数。通常有以下三个选项可供选择：

  1. Default (fast forward or merge)： 这是’git pull’ 的标准行为：如果可能，将当前分支快进到被拉取的分支，否则创建一个合并提交。
  2. Rebase： 将当前分支变基到被拉取的分支上。如果没有本地提交需要变基，则相当于快进操作。
  3. Only ever fast-forward： 只进行快进操作，将当前分支快进到被拉取的分支。如果不可行，则操作失败。

  默认情况下，大多数 git 库配置为执行 Default（fast forward or merge）行为。这意味着在 ‘git pull’ 命令时，Git 会尝试使用快进操作将当前分支更新到已拉取分支的最新状态。如果无法进行快进操作，例如存在冲突，Git 将创建一个合并提交。

- 选择凭证助手
  ![11](assets/git/11.png)

  在 Git 中，凭据助手用于管理和存储您在与远程代码库进行身份验证时使用的凭据，例如用户名和密码。根据上述选项，有两个选择：

  1. Git Credential Manager： 使用跨平台的 Git Credential Manager（GCM）。Git Credential Manager 是一个凭据助手工具，可以帮助您在访问远程 Git 存储库时自动处理身份验证。它能够安全地存储并检索您的凭据。如果您选择此选项，Git 会配置使用 GCM 作为凭据助手。
  2. None： 不使用凭据助手。如果您选择此选项，Git 将不会配置任何凭据助手，并在需要身份验证时，每次都会要求您手动输入凭据。

  选择哪个凭据助手适合您取决于您的需求和偏好。如果您希望自动处理身份验证并避免频繁输入凭据，可以选择 Git Credential Manager。如果您更倾向于手动输入凭据或者使用其他凭据管理工具，则可以选择 None。

  设置凭据助手的方式取决于您所使用的操作系统和 Git 版本。您可以通过运行以下命令来查看或更改凭据助手的配置：

  ```
  git config --get credential.helper
  git config --global credential.helper <helper>
  ```

  其中，<helper> 可以是 “manager” 或 “none”。通过更改 credential.helper 配置参数，您可以选择相应的凭据助手或不使用凭据助手。

- 配置额外选项
  ![12](assets/git/12.png)

  根据提供的选项，有两个额外功能可以配置：

  1. 启用文件系统缓存： 通过将 “core.fscache” 设置为 “true”，文件系统数据将被批量读取并缓存到内存中，以用于某些操作。这将显著提高性能。启用文件系统缓存可以加快某些 Git 操作的速度，特别是对于频繁访问文件系统的操作。注意，现有的代码库不受此设置的影响。
  2. 启用符号链接： 启用符号链接功能需要具备 “SeCreateSymbolicLink” 权限。启用符号链接功能后，您可以在 Git 仓库中创建和使用符号链接（也称为软连接）。符号链接可以在文件系统中指向其他文件或目录，类似于快捷方式。请注意，此设置对现有的代码库没有影响，只会影响新创建的仓库。

  选择是否启用这些功能取决于您的需求和操作环境。如果您希望改善某些操作的性能，并且具备适当的权限，则可以启用文件系统缓存和符号链接功能。

  要配置这些选项，您可以使用以下命令：

  ```
  git config --global core.fscache true     # 启用文件系统缓存
  git config --global core.symlinks true    # 启用符号链接
  ```

  其中，--global 标志表示将配置应用于全局 Git 配置。您还可以使用 --local 标志将配置应用于当前仓库的配置文件。

- **==安装完成==**
  可以通过选择安装的快捷方式来启动应用程序。 点击 “Finish” 退出设置。 您可以选择以下操作：

  1. “Launch Git Bash”：启动 Git Bash 终端。
     通过选择 “Launch Git Bash”，您可以打开 Git Bash 终端，它是一个命令行界面，您可以在其中执行 Git 命令和其他命令。
  2. “View Release Notes”：查看版本说明。
     通过选择 “View Release Notes”，您可以查看关于当前安装版本的发行说明，了解有关该版本的新功能、更改和修复的信息。

  命令行窗口输入 `git --version` 或者 `git -v` 可以验证

  ![13](assets/git/configuration/13.png)





> references
>
> ⭐ [Git 安装详解（写吐了，看完不后悔）-CSDN 博客](https://blog.csdn.net/qq_45730223/article/details/131693287)
>
> [超详细的 Git 下载安装、环境变量配置教程_安装好 git 之后如何配置-CSDN 博客](https://blog.csdn.net/secretstarlyp/article/details/106576882)
>
> [Git 下载安装（windows）_git-2.49.0-64-bit.exe-CSDN 博客](https://blog.csdn.net/W_chuanqi/article/details/146918456)







### 2. configuration

- 全局用户信息设置

  如果提交文件时没有配置用户名与邮件地址，那么则默认使用全局用户信息

  ```powershell
  git config --global user.name "Machine_1"
  git config --global user.email "Machine_1@machine_1.com"
  ```

  全局用户信息查看

  ```powershell
  git config --global user.name
  git config --global user.email
  ```

  具体项目用户信息设置

  ```powershell
  git config user.name "personal"
  git config user.email "personal@126.com"
  ```

  

- SSH 密钥对

  ```
  ssh-keygen -t rsa -b 4096 -C "xxxx"
  ```

  `xxxx`: 

  1. 部分教程习惯将 `-C` 参数设置为某个邮箱, 实际没有用处
  2. `-C` 只是给产生的密钥对添加一个注释，可能可以说明密钥对的用途
  3. 即 **产生 ssh 密钥对时，`ssh-keygen -t rsa -C "xxxx"`，里面输入的 email 与 Git 设定的用户名，与 GitHub 等代码托管网站的用户名毫无关联**

  推荐做法: 

  1. 每台电脑上产生秘钥对时，加注释信息内容主要跟这台机器相关的内容

  2. 秘钥加入到代码托管网站的列表时，用这个跟某台电脑密切相关的名称

  3. 示例

     | 电脑简称 | 秘钥对产生注释 | 代码托管网站上秘钥标题 |
     | :------: | :------------: | :--------------------: |
     |   HoPC   |   -C “HoPC”    |          HoPC          |
     |   CoPC   |   -C “CoPC”    |          CoPC          |
     |   Book   |   -C “Book”    |          Book          |
     |    VM    |    -C “VM”     |           VM           |

     4 个密钥对，把这个 4 个秘钥对的公钥，分别加入到 GitHub 和 Gitee 的 SSH 公钥列表里面。对于某台电脑来说，只需要一个密钥对，就能够访问多个代码托管网站了，我们这里，访问 GitHub 的时候，秘钥替代了 [personal@126.com](mailto:personal@126.com) 这个账户的的密码，而访问 Gitee 的时候，就代表的是 [company@company.cn](mailto:company@company.cn) 这个账户了。

  > [OpenSSH for Windows 中基于密钥的身份验证 | Microsoft Learn](https://learn.microsoft.com/zh-cn/windows-server/administration/openssh/openssh_keymanagement#user-key-generation)
  
- 完成配置

  

  



### 3. learning

#### a. Git 用户名+邮箱配置

- 前提

  远程仓库的两种协议

  1. SSH — 只认机器

     权限认证：公钥 + 私钥

  2. HTTPS — 只认账号

     权限认证：账号 + 密码

- 原因

  1. Git：分布式版本控制系统

  2. 远程仓库需要记录每次的操作是由谁来完成的

- 影响

  1. 记录内容: 用户名 (username) + 邮箱 (email)

  2. 记录内容 **不会进行身份验证**，只会出现在远程仓库的 commits 中

  3. 即理论上这两项内容可以随便配置:

     github 中的真实邮箱 —— commits 记录显示邮箱对应的账号
     github 不存在的邮箱 —— commits 记录显示配置的用户名

- 查看

  ```bash
  git config  --list
  git config --global --list	# 查看全局配置
  ```

  当前全局配置为

  ```bash
  username+Machine_1@username MINGW64 /d/C_git (main)
  $ git config --global --list
  user.name=Machine_1
  user.email=Machine_1@machine_1.com
  filter.lfs.clean=git-lfs clean -- %f
  filter.lfs.smudge=git-lfs smudge -- %f
  filter.lfs.process=git-lfs filter-process
  filter.lfs.required=true
  ```

  

- references

  > [对 Git 用户名与 Github 账户关系的理解_我的 user.name 和 github 用户名 是什么-CSDN 博客](https://blog.csdn.net/belongtocode/article/details/100716812)
  >
  > [对给 git 配置邮箱和用户名的理解_git 配置邮箱的意义-CSDN 博客](https://blog.csdn.net/ITWANGBOIT/article/details/103618427)



#### b. 分布式版本控制系统

每台机器都有一份

<img src="assets/git/learning/001.png" style="zoom:30%;" />



#### c. SSH 无密登录 Github

|    PC     |                 command                 |     sign      | git-name  |        git-email        |
| :-------: | :-------------------------------------: | :-----------: | :-------: | :---------------------: |
| 本机代号  | ssh-keygen -t rsa -b 4096 -C "本机代号" |               |           |                         |
| Machine_1 |   ssh-keygen -t ecdsa -C "Machine_1"    | Machine_1_key | Machine_1 | Machine_1@machine_1.com |
|           |                                         |               |           |                         |



##### 1 Windows 生成 SSH 密钥对 (用户端)

- powershell or cmd

- command

  ```
  ssh-keygen -t ecdsa -b 4096 -C "本机代号"
  ```

  1. `-t ecdsa`：指定密钥类型为 ecdsa (默认为 rsa)
  2. `-b 4096`：设置密钥长度为 4096 位，以增加安全性。
  3. `-C "snn_adversial"`：注释信息，可用于标识密钥，如使用者名称或用途。

- 提示密码保存路径 (可选)

  1. 默认路径如下 `C:\Users\%username%/.ssh/id_ecdsa`

  ![1](assets/git/configuration/1.png)

- 设置密码短语 `passphrase` (可选)

  1. 用于加密私钥文件 ( 将密码与密钥文件一起使用来提供双因素身份验证)
  2. 当前 `Machine_1` 设置 **`passphrase_for_machine_1_ssh`**

  ![3](assets/git/configuration/3.png)

- 密钥对生成

  ```powershell
  C:\Users\%username%>ssh-keygen -t ecdsa -C "Machine_1"
  Generating public/private ecdsa key pair.
  Enter file in which to save the key (C:\Users\%username%/.ssh/id_ecdsa):
  Enter passphrase (empty for no passphrase):
  Enter same passphrase again:
  Your identification has been saved in C:\Users\%username%/.ssh/id_ecdsa
  Your public key has been saved in C:\Users\%username%/.ssh/id_ecdsa.pub
  The key fingerprint is:
  SHA256:ssh_private_key_stored_in_machine_1 Machine_1
  The key's randomart image is:
  +---[ECDSA 256]---+
  |                 |
  ```
  
  ![4](assets/git/configuration/4.png)
  
  
  
- 密钥对文件 `C:\Users\%username%\.ssh`

  ```powershell
      目录: C:\Users\%username%\.ssh
  
  Mode                 LastWriteTime         Length Name
  ----                 -------------         ------ ----
  -a----         2025/4/28      9:57            537 id_ecdsa
  -a----         2025/4/28      9:57            167 id_ecdsa.pub
  ```

  1. `id_ecdsa`: 私钥文件
  2. `id_ecdsa.pub`: 公钥文件，用于服务器上的配置

  ![5](assets/git/configuration/5.png)

> [Windows 系统上配置 SSH 密钥验证，实现无密码登录_windows ssh 密钥登录-CSDN 博客](https://blog.csdn.net/qq_22841387/article/details/143575256)

##### Machine_2

```
ROUTE:
D:\A_APP\ssh\Machine_2_id_ecdsa
```



##### 2 将 SSH 密钥添加到 ssh-agent

- **powershell**

- 查看 ssh-agent 运行状态

  ```powershell
  > Get-Service -Name ssh-agent
  
  Status   Name               DisplayName
  ------   ----               -----------
  Stopped  ssh-agent          OpenSSH Authentication Agent
  ```

- 设置为手动启动并启动

  ```powershell
  > Get-Service -Name ssh-agent | Set-Service -StartupType Manual
  > Get-Service -Name ssh-agent
  
  Status   Name               DisplayName
  ------   ----               -----------
  Stopped  ssh-agent          OpenSSH Authentication Agent
  
  
  > Start-Service ssh-agent
  > Get-Service -Name ssh-agent
  
  Status   Name               DisplayName
  ------   ----               -----------
  Running  ssh-agent          OpenSSH Authentication Agent
  ```

- 将 SSH 密钥添加到 ssh-agent

  此处 `passphrase` 输入 **`passphrase_for_machine_1_ssh`**

  ```powershell
  > ssh-add c:/Users/%username%/.ssh/id_ecdsa
  Enter passphrase for c:/Users/%username%/.ssh/id_ecdsa:
  Identity added: c:/Users/%username%/.ssh/id_ecdsa (Machine_1)
  ```

  or (无法使用 ~/.ssh/ )

  ```powershell
  > ssh-add .ssh/id_ecdsa
  Enter passphrase for .ssh/id_ecdsa:
  Identity added: .ssh/id_ecdsa (Machine_1)
  ```

  ![7](assets/git/configuration/7.png)

- 查看已添加的密钥

  ```powershell
  > ssh-add -l
  256 SHA256:ssh_private_key_stored_in_machine_1 Machine_1 (ECDSA)
  ```

  ![8](assets/git/configuration/8.png)

---



- **git bash**

- 启动 SSH-Agent

  ```bash
  $ eval `ssh-agent`
  Agent pid 1535
  ```

- 查看 SSH-Agent 服务信息

  ```bash
  $ ps aux | grep ssh-agent
       1535       1    1535      25996  ?         197108 11:23:07 /usr/bin/ssh-agent
  ```

- 将 SSH 密钥添加到 ssh-agent

  此处 `passphrase` 输入 `passphrase_for_machine_1_ssh`

  ```bash
  username+Machine_1@username MINGW64 ~
  $ ssh-add ~/.ssh/id_ecdsa
  Enter passphrase for /c/Users/%username%/.ssh/id_ecdsa:
  Identity added: /c/Users/%username%/.ssh/id_ecdsa (Machine_1)
  ```

- 查看已添加的密钥

  ```bash
  # 私钥
  $ ssh-add -l
  256 SHA256:ssh_private_key_stored_in_machine_1 Machine_1 (ECDSA)
  
  # 公钥
  $ ssh-add -L
  ecdsa-sha2-nistp256 ssh_public_key_matched_with_machine_1 Machine_1
  ```

- 



##### 3 Github 添加 SSH 密钥

1. 网页添加

   <img src="assets/git/configuration/14.png" alt="14" style="zoom:50%;" />

2. 设置名称

   - `Machine_1`: `Machine_1_key`

3. 复制公钥

   powershell / git bash

   - Machine_1

     ```powershell
     cat ~/.ssh/id_ecdsa.pub
     ecdsa-sha2-nistp256 ssh_public_key_matched_with_machine_1 Machine_1
     ```

     <img src="assets/git/configuration/15.png" alt="15" style="zoom:60%;" />

4. 填写认证码 / 密码

5. 









##### reference

> [windows 使用 ssh-agent 管理私钥_windows ssh-agent-CSDN 博客](https://blog.csdn.net/jchnlau/article/details/140714151)
>
> [（诊断）为 GitHub 添加 SSH key 时出现“Could not open a connection to your authentication agent”错误的应对方案](https://www.cnblogs.com/Security-Darren/p/4106328.html)
>
> [SSH 开机自启配置及服务状态查看_查看 ssh 服务状态-CSDN 博客](https://blog.csdn.net/m0_46282787/article/details/133313272)
>
> [Linux 之 ssh-agent 命令_ssh-agent bash-CSDN 博客](https://blog.csdn.net/weixin_37335761/article/details/120107437)
>
> [ssh：ssh-agent、ssh-add_ssh add-CSDN 博客](https://blog.csdn.net/weixin_43972437/article/details/114578337)
>
> [Git 连接 Github（SSH 方式）_git 拉取 github 项目 ssh 方式-CSDN 博客](https://blog.csdn.net/brilliant_zy/article/details/147075809)
>
> :star: ssh-agent 用法详解 https://www.cnblogs.com/f-ck-need-u/p/10484531.html
>
> 完整教程 [基于 SSH 协议配置 Git 连接 GitHub](https://blog.csdn.net/qq_42815188/article/details/128735530?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-1-128735530-blog-147075809.235^v43^pc_blog_bottom_relevance_base9&spm=1001.2101.3001.4242.2&utm_relevant_index=3)
>
> https://github.com/wwalker/ssh-find-agent



##### 初次配置log

```bash
username+Machine_1@username MINGW64 ~
$ ssh-add -l
Could not open a connection to your authentication agent.

username+Machine_1@username MINGW64 ~
$ ps aux | grep ssh-agent

username+Machine_1@username MINGW64 ~
$ echo $SSH_AUTH_SOCK


username+Machine_1@username MINGW64 ~
$ echo $SSH_AGENT_PID


username+Machine_1@username MINGW64 ~
$ /etc/init.d/sshd status
bash: /etc/init.d/sshd: No such file or directory

username+Machine_1@username MINGW64 ~
$ eval `ssh-agent`
Agent pid 1535

username+Machine_1@username MINGW64 ~
$ ps aux | grep ssh-agent
     1535       1    1535      25996  ?         197108 11:23:07 /usr/bin/ssh-agent

username+Machine_1@username MINGW64 ~
$ ps aux | grep ssh-agent
     1535       1    1535      25996  ?         197108 11:23:07 /usr/bin/ssh-agent

username+Machine_1@username MINGW64 ~
$ ssh-add -l
The agent has no identities.

username+Machine_1@username MINGW64 ~
$ ssh-add -l
The agent has no identities.

username+Machine_1@username MINGW64 ~
$ ps aux | grep ssh-agent
     1535       1    1535      25996  ?         197108 11:23:07 /usr/bin/ssh-agent

username+Machine_1@username MINGW64 ~
$ ssh-add c:/Users/Dc:/Users/%username%/.ssh/id_ecdsa
: No such file or directory
: No such file or directory
c:/Users/%username%/.ssh/id_ecdsa: No such file or directory

username+Machine_1@username MINGW64 ~
$ ssh-add ~/.ssh/id_ecdsa
: No such file or directory
-add: No such file or directory
Enter passphrase for /c/Users/%username%/.ssh/id_ecdsa:
Identity added: /c/Users/%username%/.ssh/id_ecdsa (Machine_1)

username+Machine_1@username MINGW64 ~
$ ssh-add -l
256 SHA256:ssh_private_key_stored_in_machine_1 Machine_1 (ECDSA)

username+Machine_1@username MINGW64 ~
$ ssh-add -d ~/.ssh/id_ecdsa
Identity removed: /c/Users/%username%/.ssh/id_ecdsa ECDSA (Machine_1)

username+Machine_1@username MINGW64 ~
$ ssh-add ~/.ssh/id_ecdsa
Enter passphrase for /c/Users/%username%/.ssh/id_ecdsa:
Identity added: /c/Users/%username%/.ssh/id_ecdsa (Machine_1)

username+Machine_1@username MINGW64 ~
$ ssh-add -l
256 SHA256:ssh_private_key_stored_in_machine_1 Machine_1 (ECDSA)

username+Machine_1@username MINGW64 ~
$ ssh-agent
SSH_AUTH_SOCK=/tmp/ssh-5rjjx2oHEZT0/agent.1617; export SSH_AUTH_SOCK;
SSH_AGENT_PID=1618; export SSH_AGENT_PID;
echo Agent pid 1618;

username+Machine_1@username MINGW64 ~
$ ps aux | grep ssh-agent
     1618       1    1618      28108  ?         197108 14:45:38 /usr/bin/ssh-agent
     1535       1    1535      25996  ?         197108 11:23:07 /usr/bin/ssh-agent

username+Machine_1@username MINGW64 ~
$ kill 1618

username+Machine_1@username MINGW64 ~
$ ps aux | grep ssh-agent
     1535       1    1535      25996  ?         197108 11:23:07 /usr/bin/ssh-agent

username+Machine_1@username MINGW64 ~
$ ssh-add -l
256 SHA256:ssh_private_key_stored_in_machine_1 Machine_1 (ECDSA)

username+Machine_1@username MINGW64 ~
$ echo $SSH_AGENT_PID
1535

```















#### d. ssh-agent

##### 介绍

1. `ssh-agent`

   用于存储私钥的临时性的 session 服务

2. `ssh-add`

   不是用于永久记忆私钥，只是把指定私钥添加到 ssh-agent 管理的一个 session 中

3. 因此，当重启窗口后，ssh-agent 服务就重置了



##### ssh-add

选项

```bash
-D：删除ssh-agent中的所有密钥.
-d：从ssh-agent中的删除密钥
-e pkcs11：删除PKCS#11共享库pkcs1提供的钥匙。
-s pkcs11：添加PKCS#11共享库pkcs1提供的钥匙。
-L：显示ssh-agent中的公钥
-l：显示ssh-agent中的密钥
-t life：对加载的密钥设置超时时间，超时ssh-agent将自动卸载密钥
-X：对ssh-agent进行解锁
-x：对ssh-agent进行加锁
```



##### 相关命令

- 开启 openssh 的 ssh-agent 服务

  powershell (× cmd)

  ```powershell
  Get-Service -Name ssh-agent # 查看服务是否起来
  Start-Service ssh-agent 	# 启动服务
  Stop-Service ssh-agent 		# 关闭服务
  Get-Service -Name ssh-agent | Set-Service -StartupType Manual	# 将该服务设置为手动启动
  ```

- 将私钥添加到 ssh-agent

  ```powershell
  ssh-add ~/.ssh/id_ecdsa		# 添加私钥
  ssh-add -l					# 查询添加哪些私钥
  ssh-add -D					# 删除所有私钥
  ```

- 配置 ssh 允许使用 ssh-agent

  ```powershell
  ~/.ssh/config				# 修改配置文件
  ```

- Attention

  ```
  Host *
  ForwardAgent yes
  ```

  1. windows 系统，需要检查 git for windows 是不是使用了自带的 ssh

     如果是的话，需要修改

     ```powershell
     git config --global core.sshcommand='C:\Windows\System32\OpenSSH\ssh.exe'
     ```

  2. 如果还有问题，检查客户端是不是有多个 git for windows 客户端



#### e. command

##### clone

```bash
git clone 
```

- 默认下载位置

  C:/Users/用户名/项目名称

  e.g. `C:/Users/%username%/GCI-main`

- 指定下载位置

  ```bash
  git clone git@... D:/GCI-main
  ```



##### push

- 主要流程命令如下

  ```bash
  # 进入要提交的文件夹内 (!!! 需要使用斜杠/, 不能使用反斜杠\)
  cd path/to/directory
  
  # 初始化当前文件夹
  git init
  
  # 添加当前文件夹下的所有文件到缓存
  git add .
  
  # 将文件提交到本地仓库
  # -m 为添加注释
  git commit -m "comment"
  
  # 关联 GitHub 仓库 (仅首次需要)
  git remote add origin git@github.com:github/repository/path
  
  # 上传本地代码
  git push -u origin main
  ```
  
- HTTPS 进行 push 操作

  需要使用如下步骤进行账号密码登录

  1. git push后会弹出
     <img src="assets/git/learning/002.png" style="zoom:50%;" />
  2. 点击链接后浏览器弹出
     <img src="assets/git/learning/003.png" style="zoom:50%;" />
  3. 填写认证码
     <img src="assets/git/learning/004.png" style="zoom:50%;" />
  4. 执行认证
     <img src="assets/git/learning/005.png" style="zoom:50%;" />
  5. 认证完成
     <img src="assets/git/learning/006.png" style="zoom:50%;" />

- 回滚并删除历史记录

  > [清除Github提交历史记录](https://zhuanlan.zhihu.com/p/35078876)






#### f. proxy

- 设置代理

    ```bash
    //http || https
    git config --global http.proxy 127.0.0.1:7890
    git config --global https.proxy 127.0.0.1:7890

    //sock5代理
    git config --global http.proxy socks5 127.0.0.1:7891
    git config --global https.proxy socks5 127.0.0.1:7891
    ```


​    
- 查看代理

    ```bash
    git config --global --get http.proxy
    git config --global --get https.proxy
    ```

    

- 取消代理

    ```bash
    git config --global --unset http.proxy
    git config --global --unset https.proxy
    ```

    











#### Error / Question

1. 运行 `ssh-add` 提示 `Could not open a connection to your authentication agent.`

   **原因**: `ssh-agent`  没有运行

   **解决方法**: 启动该服务

   ```bash
   # macOS/Linux
   eval `ssh-agent`
   ssh-add ~/.ssh/other_id_rsa
   
   # 在Windows中的git-bash中
   eval $(ssh-agent) 
   ssh-add ~/.ssh/other_id_rsa
   ```

   > eval 命令是对字符串参数进行求值，执行字符串表达的命令。比如 eval "ls -lha" 就等同于直接运行 ls -lha 命令

   

2. 在 `powershell` 中配置的 SSH-Agent 在 `git bash` 中不生效

   在 Windows 系统中，`powershell` 和 `git bash` 的 SSH-Agent 进程是相互独立的，且 **环境变量不共享**。

   在 `powershell` 中配置的 SSH-Agent 密钥仅在当前 `powershell` 会话中有效，而 `git bash` 需要单独启动自己的 SSH-Agent 进程并添加密钥。

3. windows 中每次启动 `git bash` 都需要启动 ssh-agent 并用 ssh-add 添加密钥

   - 原因

     

   修改文件 `bash.bashrc` [location: `D:\A_APP\Git\etc\bash.bashrc`]

   > may useful
   >
   > [解决 Windows 下 git 需要每次都要 ssh-add 的问题-CSDN 博客](https://blog.csdn.net/baoba84620/article/details/101068761)

4. error in libcrypto

   ```bash
   $ ssh-add ~/.ssh/id_ecdsa.pub
   Error loading key "/c/Users/%username%/.ssh/id_ecdsa.pub": error in libcrypto
   ```

   **ATT**: 不是添加公钥，是添加无后缀名的私钥 `id_ecdsa`

   如果出现此类问题：

   **==未试验==**

   - 原因: Windows 下，git 使用 MSYS2 兼容的 POSIX 标准编译。POSIX 标准换行符为 `\n`, 因此 git 无法识别 Windows 换行符 `\r\n`

   - 解决方案：修改文件编码方式

     VSCode 打开密钥文件，右下角选择 `CRLF`，弹出窗口选择 `LF` 保存

   - references

     > [github 使用 ssh 密钥访问出现 error in libcrypto 等问题-CSDN 博客](https://blog.csdn.net/Wxx1213383851/article/details/137590435)
     >
     > [Error loading key id_ed25519: error in libcrypto-CSDN 博客](https://blog.csdn.net/Bing_Lee/article/details/130769279)

   

5. repository '' not exist

   ```bash
   $ git clone git@github.com:xxxiaol/GCI.git
   fatal: repository '' does not exist
   ```

   原因：bash 命令行界面粘贴时直接使用 Ctrl + V 后，再输入 git 链接，会导致这句命令带有隐藏的 `^` 字符

   解决：

   - 快捷键

     copy: ctrl + insert
     paste: shift + insert

   - 右键粘贴

   - 手动输入

   

6. clone 失败

   ```bash
   $ git clone git@github.com:xxxiaol/GCI.git D:/gitRepo
   Cloning into 'GCI'...
   Connection closed by 20.205.243.160 port 443
   fatal: Could not read from remote repository.
   
   Please make sure you have the correct access rights
   and the repository exists.
   ```

   原因：unknown (怀疑可能是公司内网问题)

   解决方案：

   1. ~~重新生成ssh密钥并添加~~

   2. ~~修改端口 22 —> 443~~

      修改 config 文件 (original)

      ```bash
      Host regixxxxx.com
        HostName regixxxxx.com
        Port 45455
        User root
      ```

      - 修改方式1

          ```bash
          Host github.com
          User git
          Port 443
          Hostname ssh.github.com
          PreferredAuthentications publickey
          IdentityFile ~/.ssh/id_ecdsa

          Host gitlab.com
          User git
          Port 443
          Hostname altssh.gitlab.com
          PreferredAuthentications publickey
          IdentityFile ~/.ssh/id_ecdsa
          ```

      - 修改方式2

          ```bash
          # github
          Host github.com
          Port 443
          HostName ssh.github.com
          PreferredAuthentications publickey
          IdentityFile ~/.ssh/id_ecdsa
          ```

   3. ~~修改 git 用户邮箱设置~~

   4. 删除 `known_hosts` 中有关 Github相关行 (未测试)

   5. 将网络切换为手机热点 (未测试)

   6. ~~修改clone方式为https~~

      报错如下

      ```bash
      git clone https://github.com/xxxiaol/GCI.git
      Cloning into 'GCI'...
      fatal: unable to access 'https://github.com/xxxiaol/GCI.git/': TLS connect error: error:0A0000C6:SSL routines::packet length too long
      ```

   > [使用Git时报错Connection reset by 20.205.243.166 port 22_connection reset by 20.205.243.166 port 22 fatal: -CSDN博客](https://blog.csdn.net/Wrysmile0308/article/details/128801870)

7. failed to push

   ```bash
   username+Machine_1@username MINGW64 /d/C_git (main)
   $ git push origin master
   error: src refspec master does not match any
   error: failed to push some refs to 'https://github.com/SO-ia/test_git.git'
   ```

   **原因**: 分支命名错误

   **解决方案**: 修改命令为

   ```bash
   git push origin main
   ```

8. 

> https://blog.csdn.net/yoona333/article/details/144175578
>





















## Excel

#### 快捷键

1. 新建工作表

   shift + F11

















## LaTex

#### texlive

##### installation

- download

  [Index of /CTAN/systems/texlive/Images/ | 清华大学开源软件镜像站 | Tsinghua Open Source Mirror](https://mirrors.tuna.tsinghua.edu.cn/CTAN/systems/texlive/Images/)

  选择 texlive.iso
  <img src="assets/latex/001.png" style="zoom:33%;" />

  > 下载链接
  >
  > https://mirrors.tuna.tsinghua.edu.cn/CTAN/systems/texlive/Images/texlive.iso

- install

  1. 右键 iso, 在文件资源管理器中打开
     ![1](assets/latex/002.png)

  2. 右键以 管理员 身份运行 `install-tl-windows.bat`
     <img src="assets/latex/003.png" alt="003" style="zoom:40%;" />
     同意运行
     <img src="assets/latex/004.png" alt="004" style="zoom:40%;" />

  3. 稍后弹出 TeXLive Installer
     <img src="assets/latex/005.png" alt="005" style="zoom:50%;" />

  4. 修改安装地址
     <img src="assets/latex/006.png" alt="006" style="zoom:50%;" />

     修改后显示地址
     <img src="assets/latex/007.png" alt="007" style="zoom:50%;" />

  5. 本次安装的 Advance 设置如下
     <img src="assets/latex/009.png" alt="009" style="zoom:50%;" />

  6. 开始安装弹窗
     <img src="assets/latex/010.png" alt="010" style="zoom: 50%;" />

     > 要一个多小时我也是服了

  7. 



##### references

> [Visual Studio Code (vscode)配置 LaTeX - 知乎](https://zhuanlan.zhihu.com/p/166523064)

###### log

see in 03_Tools_log.txt





### Grammer

#### 1. 空格

##### 基础空格

| 命令   | 效果描述             | 示例代码  | 渲染效果 |
| :----- | :------------------- | :-------- | :------- |
| \      | 单个空格             | a\ b      | a b      |
| \,     | 小空格（约1/6个em）  | a\,b      | a b      |
| \;     | 中空格（约5/18个em） | a\;b      | a b      |
| \quad  | 等宽空格（1em）      | a\quad b  | a b      |
| \qquad | 双倍等宽空格（2em）  | a\qquad b | a  b     |

##### 弹性水平间距

`\hspace{}`命令支持自定义宽度，支持`em`、`cm`等单位：

```latex
a\hspace{1cm}b % 1厘米水平间距
```

> [LaTeX中空格与换行的精准控制方法](https://comate.baidu.com/zh/page/UpqYCmQvcg)





#### 2. 表格

##### 整体居中

有时文档为两列格式，需要将表格居于两列中间显示，可使用

```latex
\begin{table*}
\end{table*}
```

##### 表格内容整体居中

```latex
\centering
```

> [LaTeX：表格内换行与各种居中完美解决](https://www.jianshu.com/p/b6b45402d8b2/)





#### 3. 中文







#### 4. 换行





# Bottom