## Linux

### Bash

#### 复制文件

##### 1. cp

```python
cp -a /root/xxx /root/xxx

mv /root/xxx /root/xxx

cp -r /root/xxx /root/xxx

cp /root/xxx /autodl-fs/xxx

cp /root/xxx /autodl-fs/xxx
```

- `-a`：归档模式，相当于`-dR --preserve=all`，递归复制并保留文件属性。
- `-f`：强制复制，如果目标文件已存在，不提示直接覆盖。
- `-i`：交互模式，如果目标文件已存在，会提示是否覆盖。
- `-p`：保留文件的权限、用户、组和时间戳。
- `-r`：递归复制目录。
- `-R`：与`-r`相同，递归复制目录。
- `-u`：仅在源文件比目标文件新，或者目标文件不存在时，才进行复制。
- `-v`：详细模式，显示复制过程中的详细信息。



#### 删除

##### 1. rm

删除空文件夹

```bash
rmdir 文件夹名称
```

删除非空文件夹（递归删除）

```python
rm -r 文件夹名称
```

- `-r` 选项表示递归删除，会删除指定文件夹及其所有内容（包括子文件夹和文件）。

强制删除文件夹（不提示确认）

```bash
rm -rf 文件夹名称
```

- `-f` 选项表示强制删除，不会提示确认，即使文件夹中有只读文件或需要管理员权限的文件也会被删除。

交互模式删除文件夹（逐个确认）

```bash
rm -ri 文件夹名称
```

- `-i` 选项表示交互模式，删除每个文件和文件夹之前都会提示确认。



#### mv

```bash
mv [选项] 源文件或文件夹 目标位置
```

- 移动文件或文件夹
- 重命名文件或文件夹

##### 参数

- `-i`：交互模式，移动文件或文件夹前会提示用户确认，避免覆盖目标位置的文件。
- `-f`：强制模式，不提示用户确认，直接覆盖目标位置的文件。
- `-v`：详细模式，显示移动过程中的详细信息。

##### 示例

1. 将文件 `file.txt` 移动到 `/home/user/documents` 目录

    ```bash
    mv file.txt /home/user/documents/
    ```
    
2. 文件夹 `folder1`，你想将其移动到 `/home/user/projects` 目录

    ```bash
    mv folder1 /home/user/projects/
    ```

3. 将文件 `oldname.txt` 重命名为 `newname.txt`

    ```bash
    mv oldname.txt newname.txt
    ```

4. 将文件夹 `oldfolder` 重命名为 `newfolder`

    ```bash
    mv oldfolder newfolder
    ```

5. 在移动文件时避免覆盖目标位置的文件，可以使用 `-i` 选项，进入交互模式

    ```bash
    mv -i file.txt /home/user/documents/
    ```

    如果目标位置已经存在 `file.txt`，系统会提示是否覆盖

6. 在移动文件时直接覆盖目标位置的文件，可以使用 `-f` 选项

    ```bash
    mv -f file.txt /home/user/documents/
    ```

7. 查看移动过程中的详细信息，可以使用 `-v` 选项

    ```bash
    mv -v file.txt /home/user/documents/
    ```

    

#### 压缩

##### tar

```bash
tar -czvf archive_name.tar.gz file1 file2 directory1
```

- `-c`：创建一个新的归档文件
- `-z`：通过 `gzip` 压缩归档文件 /解压
- `-v`：在压缩过程中显示详细信息
- `-f`：指定归档文件的名称
- `-j`：使用 `bzip2` 压缩/解压
- `-x`：解压归档文件

###### 打包文件和目录

```bash
tar -cvf archive.tar file1 file2 directory1
```

###### 打包并压缩

- 使用 `gzip`

    ```bash
    tar -czvf archive.tar.gz file1 file2 directory1
    ```

- 使用 `bzip2`

    ```bash
    tar -cjvf archive.tar.bz2 file1 file2 directory1
    ```

###### 解压归档文件

```bash
tar -xzvf archive.tar.gz
```

```bash
tar -xjvf archive.tar.bz2
```



##### 使用历史

###### 压缩包含指定文件名的文件

```
find . -name "example.txt" -print0 | xargs -0 tar -czvf example_files.tar.gz
```

- `find . -name "example.txt"`：从当前目录（`.`）开始递归查找所有名为`example.txt`的文件。

- `|`：管道符号，将`find`命令的输出传递给下一个命令。

- `xargs`：将`find`命令的输出作为参数传递给`tar`命令。

- `tar -czvf example_files.tar.gz`：

  - `-c`：创建一个新的归档文件。
  - `-z`：使用gzip压缩归档文件。
  - `-v`：显示详细信息。
  - `-f`：指定归档文件的名称

- `-print0`和`xargs -0`来处理文件名中可能包含的特殊字符（如空格）

  ```bash
  find . -name "example.txt" -print0 | xargs -0 tar -czvf example_files.tar.gz
  ```

- 如果需要排除某些目录，可以使用`-prune`选项

  ```bash
  find . -path "./exclude_dir" -prune -o -name "example.txt" -print0 | xargs -0 tar -czvf example_files.tar.gz
  ```

     
  
     
  



#### 查找

##### find

```bash
find [搜索路径] [选项] [表达式] -exec 命令 {} \;
```







#### 清缓存

```bash
du -sh /root/miniconda3/pkgs/ && rm -rf /root/miniconda3/pkgs/*      # conda的历史包
du -sh /root/.local/share/Trash && rm -rf /root/.local/share/Trash   # jupyterlab的回收站
du -sh /tmp/         #查看/tmp占用的空间大小
rm -rf /tmp/
du -sh /root/.cache  #查看/root/.cache占用的空间大小
rm -rf /root/.cache
```



#### 环境变量

##### 查看所有

```
env
```

**result**

```python
(base) root@autodl-container-b9224992bb-33b2a2c7:~# env $FORCE_TORCHRUN   =/usr/bin/supervisord
SHELL=/bin/bash
NV_LIBCUBLAS_VERSION=11.11.3.6-1
NVIDIA_VISIBLE_DEVICES=none
NV_NVML_DEV_VERSION=11.8.86-1
NV_CUDNN_PACKAGE_NAME=libcudnn8
NV_LIBNCCL_DEV_PACKAGE=libnccl-dev=2.15.5-1+cuda11.8
CONDA_EXE=/root/miniconda3/bin/conda
_CE_M=
...
_=/usr/bin/env
```

##### 查看某个

```
echo $PATH
```











### Error

#### 1 

```
sudo systemctl daemon-reload
System has not been booted with systemd as init system (PID 1). Can't operate.
Failed to connect to bus: Host is down
```







#### 2 无法安装 systemctl

```
apt-get install systemctl -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libopencv-highgui4.2 : Depends: libgtk-3-0 (>= 3.0.0) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```





## Docker

### installation

#### log

1. 打开 wsl

   系统 -> 可选功能 -> 相关设置: 更多 Windows 功能

   <img src="assets\1.png" alt="1" style="zoom:60%;" />

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



### 清理指南



> https://www.cnblogs.com/jgdabc/p/15803086.html



#### change location

change default `Downloads, Music, Picture, ...`  to D drive

> https://learn.microsoft.com/en-us/answers/questions/4186079/how-do-i-change-and-cleanup-my-default-download-lo



### 系统模块

#### 蓝牙

##### 1 蓝牙键盘无法连接

始终无法连接，且后续弹出 输入键盘的 pin, 如下图

<img src="assets/01-win/000.png" alt="000" style="zoom:50%;" />

###### solution

1. 先用原键盘输入任意数字/字母 (如 000000)
2. 点击连接
3. 在键盘上输入相同内容 (如 000000)
4. 按回车即可

###### reference

> https://mbd.baidu.com/newspage/data/dtlandingsuper?nid=dt_4804260829556682554&sourceFrom=search_a



### Typora

#### Installation

https://ioufev.lanzout.com/iA5J10945l8d

https://www.cnblogs.com/ioufev/articles/15610121.html

普通下载即可

> activation code
> https://www.lanzouh.com/i7j9H26waded
> fkmj

#### 格式插件 pandoc

1. 其他格式转换 —— 需安装 `pandoc`

2. GitHub 最新安装包网址
   https://github.com/jgm/pandoc/releases/lastest

3. Windows 选择 `pandoc-*-window.msi`

   - 本次选择 [pandoc-3.6.4-windows-x86_64.msi](https://github.com/jgm/pandoc/releases/download/3.6.4/pandoc-3.6.4-windows-x86_64.msi)
   - [下载链接](https://objects.githubusercontent.com/github-production-release-asset-2e65be/571770/218b3377-0d49-4ef9-baf0-64272fbc5df0?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=releaseassetproduction%2F20250415%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250415T011103Z&X-Amz-Expires=300&X-Amz-Signature=1dfb4a7344792ffc55c68d977ba830a9dfd7c633266c6e95b6400688b6869344&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B%20filename%3Dpandoc-3.6.4-windows-x86_64.msi&response-content-type=application%2Foctet-stream)

   ```powershell
   C:\Users\%username%>pandoc --version
   pandoc 3.6.4
   Features: +server +lua
   Scripting engine: Lua 5.4
   User data directory: C:\Users\%username%\AppData\Roaming\pandoc
   Copyright (C) 2006-2024 John MacFarlane. Web: https://pandoc.org
   This is free software; see the source for copying conditions. There is no warranty, not even for merchantability or fitness for a particular purpose.
   ```

   ```powershell
   C:\Users\%username%>pandoc --version
   pandoc 3.7.0.2
   Features: +server +lua
   Scripting engine: Lua 5.4
   User data directory: C:\Users\%username%\AppData\Roaming\pandoc
   Copyright (C) 2006-2024 John MacFarlane. Web: https://pandoc.org
   This is free software; see the source for copying conditions. There is no
   warranty, not even for merchantability or fitness for a particular purpose.
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

- <font color=darkred>该项目只适用于 v1.5.x - v1.9.x </font>

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



#### 快捷键

##### 1 编辑（Editing）

- Ctrl + Space  基本的代码完成（类、方法、属性）
- Ctrl + Alt + Space 快速导入任意类
- Ctrl + Shift + Enter  语句完成
- Ctrl + P  参数信息（在方法中调用参数）
- Ctrl + Q  快速查看文档
- F1  外部文档
- Shift + F1  外部文档，进入web文档主页
- Ctrl + Shift + Z --> Redo 重做
- Ctrl + 鼠标  简介/进入代码定义
- Ctrl + F1  显示错误描述或警告信息
  Alt + Insert  自动生成代码
  Ctrl + O  重新方法
  Ctrl + Alt + T  选中
  Ctrl + /  行注释/取消行注释
  Ctrl + Shift + /  块注释
  Ctrl + W  选中增加的代码块
  Ctrl + Shift + W  回到之前状态
  Ctrl + Shift + ]/[   选定代码块结束、开始
  Alt + Enter  快速修正
  Ctrl + Alt + L   代码格式化
  Ctrl + Alt + O  优化导入
  Ctrl + Alt + I  自动缩进
  Tab / Shift + Tab 缩进、不缩进当前行
  Ctrl+X/Shift+Delete  剪切当前行或选定的代码块到剪贴板
  Ctrl+C/Ctrl+Insert  复制当前行或选定的代码块到剪贴板
  Ctrl+V/Shift+Insert  从剪贴板粘贴
  Ctrl + Shift + V  从最近的缓冲区粘贴
  Ctrl + D 复制选定的区域或行
  Ctrl + Y  删除选定的行
  Ctrl + Shift + J 添加智能线
  Ctrl + Enter  智能线切割
  Shift + Enter  另起一行
  Ctrl + Shift + U 在选定的区域或代码块间切换
  Ctrl + Delete  删除到字符结束
  Ctrl + Backspace  删除到字符开始
  Ctrl + Numpad+/-  展开/折叠代码块（当前位置的：函数，注释等）
  Ctrl + shift + Numpad+/-  展开/折叠所有代码块
  Ctrl + F4  关闭运行的选项卡


##### 2 查找/替换(Search/Replace)

- F3  下一个
- Shift + F3  前一个
- Ctrl + R  替换
- Ctrl + Shift + F 或者连续2次敲击shift  全局查找{可以在整个项目中查找某个字符串什么的，如查找某个函数名字符串看之前是怎么使用这个函数的}
- Ctrl + Shift + R  全局替换
- 

##### 3 运行(Running)

Alt + Shift + F10  运行模式配置
Alt + Shift + F9  调试模式配置
Shift + F10  运行
Shift + F9  调试
Ctrl + Shift + F10  运行编辑器配置
Ctrl + Alt + R  运行manage.py任务

##### 4 调试(Debugging)

F8  跳过
F7  进入
Shift + F8  退出
Alt + F9  运行游标
Alt + F8  验证表达式
Ctrl + Alt + F8  快速验证表达式
F9  恢复程序
Ctrl + F8  断点开关
Ctrl + Shift + F8  查看断点

##### 5 导航(Navigation)

Ctrl + N  跳转到类
Ctrl + Shift + N  跳转到符号
Alt + Right/Left  跳转到下一个、前一个编辑的选项卡
F12  回到先前的工具窗口
Esc  从工具窗口回到编辑窗口
Shift + Esc  隐藏运行的、最近运行的窗口
Ctrl + Shift + F4  关闭主动运行的选项卡
Ctrl + G  查看当前行号、字符号
Ctrl + E  当前文件弹出，打开最近使用的文件列表
Ctrl+Alt+Left/Right  后退、前进
Ctrl+Shift+Backspace  导航到最近编辑区域
Alt + F1  查找当前文件或标识
Ctrl+B / Ctrl+Click  跳转到声明
Ctrl + Alt + B  跳转到实现
Ctrl + Shift + I查看快速定义
Ctrl + Shift + B跳转到类型声明
Ctrl + U跳转到父方法、父类
Alt + Up/Down跳转到上一个、下一个方法
Ctrl + ]/[跳转到代码块结束、开始
Ctrl + F12弹出文件结构
Ctrl + H类型层次结构
Ctrl + Shift + H方法层次结构
Ctrl + Alt + H调用层次结构
F2 / Shift + F2下一条、前一条高亮的错误
F4 / Ctrl + Enter编辑资源、查看资源
Alt + Home显示导航条F11书签开关
Ctrl + Shift + F11书签助记开关
Ctrl + #[0-9]跳转到标识的书签
Shift + F11显示书签

##### 6 搜索相关(Usage Search)

Alt + F7/Ctrl + F7文件中查询用法
Ctrl + Shift + F7文件中用法高亮显示
Ctrl + Alt + F7显示用法

##### 7 重构(Refactoring)

F5复制F6剪切
Alt + Delete安全删除
Shift + F6重命名
Ctrl + F6更改签名
Ctrl + Alt + N内联
Ctrl + Alt + M提取方法
Ctrl + Alt + V提取属性
Ctrl + Alt + F提取字段
Ctrl + Alt + C提取常量
Ctrl + Alt + P提取参数

##### 8 控制VCS/Local History

Ctrl + K提交项目
Ctrl + T更新项目
Alt + Shift + C查看最近的变化
Alt + BackQuote(’)VCS快速弹出

##### 9 模版(Live Templates)

Ctrl + Alt + J当前行使用模版
Ctrl +Ｊ插入模版

##### 10 基本(General)

Alt + #[0-9]打开相应的工具窗口
Ctrl + Alt + Y同步
Ctrl + Shift + F12最大化编辑开关
Alt + Shift + F添加到最喜欢
Alt + Shift + I根据配置检查当前文件
Ctrl + BackQuote(’)快速切换当前计划
Ctrl + Alt + S　打开设置页
Ctrl + Shift + A查找编辑器里所有的动作

Ctrl + Tab在窗口间进行切换



#### references

> https://www.cnblogs.com/davidshen/p/10412644.html





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
mklink /d  "C:\Users\%username%\AppData\Local\Google" "D:\A_APP\Google\PersonData"
```

6、安装 chrome

6、安装 chrome

 命令如下 

```powershell
C:\Windows\System32>mklink /d  "C:\Program Files\Google\Chrome"  "D:\A_APP\Google\Chrome"
为 C:\Program Files\Google\Chrome <<===>> D:\A_APP\Google\Chrome 创建的符号链接

C:\Windows\System32>mklink /d  "C:\Program Files (x86)\Google"  "D:\A_APP\Google"
为 C:\Program Files (x86)\Google <<===>> D:\A_APP\Google 创建的符号链接

C:\Windows\System32>mklink /d  "C:\Users\%username%\AppData\Local\Google" "D:\A_APP\Google\PersonData"
为 C:\Users\%username%\AppData\Local\Google <<===>> D:\A_APP\Google\PersonData 创建的 符号链接
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




### anaconda
#### installation
https://www.anaconda.com/download/success
Distribution Installers -> Windows -> Python 3.13

##### process



#### environment variables

```
D:\A_APP\anaconda3
D:\A_APP\anaconda3\Scripts
D:\A_APP\anaconda3\Library\bin
D:\A_APP\anaconda3\Library\mingw-w64\bin
D:\A_APP\anaconda3\Library\usr\bin
```



#### error

在 PowerShell 中，只想“**仅对当前用户**”把执行策略从 **Restricted** 改为 **RemoteSigned**（或任何其他策略），用下面这一条命令即可：

```powershell
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```

- **`-Scope CurrentUser`** → 只改当前登录用户的策略，不会动系统级策略。  
- **`-ExecutionPolicy RemoteSigned`** → 允许本地脚本运行，下载的脚本必须带签名；你也可以换成 `Bypass`、`Unrestricted` 等。

##### 验证结果

```powershell
Get-ExecutionPolicy -Scope CurrentUser
```

应返回 `RemoteSigned`。

> 如果之前是 `Restricted`，再执行 `Get-ExecutionPolicy`（不带参数）也会返回 `RemoteSigned`，因为当前用户策略已生效。

```powershell
(base) PS C:\Users\%username%> Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned

Execution Policy Change
The execution policy helps protect you from scripts that you do not trust. Changing the execution policy might expose
you to the security risks described in the about_Execution_Policies help topic at
https:/go.microsoft.com/fwlink/?LinkID=135170. Do you want to change the execution policy?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): Y
(base) PS C:\Users\%username%> Get-ExecutionPolicy -Scope CurrentUser
RemoteSigned
```



##### references

> 是否需要勾选环境变量
>
> https://blog.csdn.net/weixin_46044549/article/details/104671464
>
> 官网教程
> https://docs.anaconda.com/anaconda/install/windows
>
> 参考教程
>
> https://blog.csdn.net/AV_VA1/article/details/149650588
>
> https://blog.csdn.net/machinelear/article/details/149466359?fromshare=blogdetail&sharetype=blogdetail&sharerId=149466359&sharerefer=PC&sharesource=qq_73921758&sharefrom=from_link
>
> 环境变量内容参考
> https://blog.csdn.net/m0_74055982/article/details/140220250?fromshare=blogdetail&sharetype=blogdetail&sharerId=140220250&sharerefer=PC&sharesource=qq_73921758&sharefrom=from_link

#### 



## Java Web

### Maven (.m2)

https://ask.csdn.net/questions/7548212







## Python

### BBPC

- version
  3.13.6
- link
  https://www.python.org/downloads/windows/

reference

> https://blog.csdn.net/sensen_kiss/article/details/141940274



# Bottom