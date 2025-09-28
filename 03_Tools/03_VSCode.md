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
	at m.Create (c:\Users\%username%\.vscode\extensions\ms-vscode-remote.remote-ssh-0.102.0\out\extension.js:1:584145)
	at t.handleInstallOutput (c:\Users\%username%\.vscode\extensions\ms-vscode-remote.remote-ssh-0.102.0\out\extension.js:1:582705)
	at t.tryInstall (c:\Users\%username%\.vscode\extensions\ms-vscode-remote.remote-ssh-0.102.0\out\extension.js:1:681881)
	at async c:\Users\%username%\.vscode\extensions\ms-vscode-remote.remote-ssh-0.102.0\out\extension.js:1:644110
	at async t.withShowDetailsEvent (c:\Users\%username%\.vscode\extensions\ms-vscode-remote.remote-ssh-0.102.0\out\extension.js:1:647428)
	at async t.resolve (c:\Users\%username%\.vscode\extensions\ms-vscode-remote.remote-ssh-0.102.0\out\extension.js:1:645160)
	at async c:\Users\%username%\.vscode\extensions\ms-vscode-remote.remote-ssh-0.102.0\out\extension.js:1:720916
[09:36:52.582]
```

solution

- remote.SSH: Config File

  填入以下绝对路径

  ```
  C:\Users\%username%\.ssh\config
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







### Jupyter

#### Cell命令模式

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

#### Cell编辑模式

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



### HTML

#### Live Server

页面实时预览插件

#### 头部注释

```json
{
    // 头部注释
    "fileheader.customMade": {
        // 头部注释默认字段
        "Author": "your name",
        "Date": "Do not edit", // 设置后默认设置文件生成时间
        "LastEditTime": "Do not edit", // 设置后，保存文件更改默认更新最后编辑时间
        "LastEditors": "your name", // 设置后，保存文件更改默认更新最后编辑人
        "Description": "",
        "FilePath": "Do not edit", // 设置后，默认生成文件相对于项目的路径
        "custom_string_obkoro1": "可以输入预定的版权声明、个性签名、空行等"
    },
    // 函数注释
    "fileheader.cursorMode": {
    // 默认字段
    "description":"",
    "param":"",
    "return":""
    },
    // 插件配置项
    "fileheader.configObj": {
    
        "autoAdd": false, // 检测文件没有头部注释，自动添加文件头部注释
        "autoAddLine": 100, // 文件超过多少行数 不再自动添加头部注释
        "autoAlready": true, // 只添加插件支持的语言以及用户通过`language`选项自定义的注释
        "supportAutoLanguage": [], // 设置之后，在数组内的文件才支持自动添加
    // 自动添加头部注释黑名单
    "prohibitAutoAdd": [
        "json"
        ],
    "prohibitItemAutoAdd": [ "项目的全称禁止项目自动添加头部注释, 使用快捷键自行添加" ],
    "folderBlacklist": [ "node_modules" ], // 文件夹或文件名禁止自动添加头部注释
    "wideSame": false, // 头部注释等宽设置
    "wideNum": 13,  // 头部注释字段长度 默认为13
        "functionWideNum": 0, // 函数注释等宽设置 设为0 即为关闭
    // 头部注释第几行插入
        "headInsertLine": {
        "php": 2 // php文件 插入到第二行
        },
        "beforeAnnotation": {}, // 头部注释之前插入内容
        "afterAnnotation": {}, // 头部注释之后插入内容
        "specialOptions": {}, // 特殊字段自定义
        "switch": {
        "newlineAddAnnotation": true // 默认遇到换行符(\r\n \n \r)添加注释符号
        },
        "moveCursor": true, // 自动移动光标到Description所在行
        "dateFormat": "YYYY-MM-DD HH:mm:ss",
        "atSymbol": ["@", "@"], // 更改所有文件的自定义注释中的@符号
        "atSymbolObj": {}, //  更改单独语言/文件的@
        "colon": [": ", ": "], // 更改所有文件的注释冒号
        "colonObj": {}, //  更改单独语言/文件的冒号
        "filePathColon": "路径分隔符替换", // 默认值： mac: / window是: \
        "showErrorMessage": false, // 是否显示插件错误通知 用于debugger
        "writeLog": false, // 错误日志生成
        "CheckFileChange": false, // 单个文件保存时进行diff检查
        "createHeader": false, // 新建文件自动添加头部注释
        "useWorker": false, // 是否使用工作区设置
        "designAddHead": true, // 添加注释图案时添加头部注释
        "headDesignName": "random", // 图案注释使用哪个图案 
        /* 
            'random', // 随机
            'buddhalImg', // 佛祖
            'buddhalImgSay', // 佛祖+佛曰
            'buddhalSay', // 佛曰
            'totemDragon', // 龙图腾
            'belle', // 美女
            'coderSong', // 程序员之歌
            'loitumaGirl', // 甩葱少女
            'keyboardAll', // 全键盘
            'keyboardSmall', // 小键盘
            'totemWestDragon', // 喷火龙
            'jesus', // 耶稣
            'dog', // 狗
            'grassHorse', // 草泥马
            'grassHorse2', // 草泥马2
            'totemBat', // 蝙蝠
        */
        "headDesign": true, // 是否使用图案注释替换头部注释
        // 自定义配置是否在函数内生成注释 不同文件类型和语言类型
        "cursorModeInternalAll": {}, // 默认为false 在函数外生成函数注释
        "openFunctionParamsCheck": true, // 开启关闭自动提取添加函数参数
        "functionParamsShape": ["{", "}"], // 函数参数外形自定义 
        // "functionParamsShape": "no type" 函数参数不需要类型
        "functionBlankSpaceAll": {}, // 函数注释空格缩进 默认为空对象 默认值为0 不缩进
        "functionTypeSymbol": "*", // 参数没有类型时的默认值
        "typeParamOrder": "type param", // 参数类型 和 参数的位置自定义
        // 自定义语言注释，自定义取消 head、end 部分
        // 不设置自定义配置language无效 默认都有head、end
        "customHasHeadEnd": {}, // "cancel head and function" | "cancel head" | "cancel function" 
        "throttleTime": 60000, // 对同一个文件 需要过1分钟再次修改文件并保存才会更新注释
        // 自定义语言注释符号，覆盖插件的注释格式
        "language": {
            // js后缀文件
            "js": {
                "head": "/$$",
                "middle": " $ @",
                "end": " $/",
                // 函数自定义注释符号：如果有此配置 会默认使用
                "functionSymbol": {
                "head": "/******* ", // 统一增加几个*号
                "middle": " * @",
                "end": " */"
                },
                "functionParams": "typescript" // 函数注释使用ts语言的解析逻辑
            },
        // 一次匹配多种文件后缀文件 不用重复设置
        "h/hpp/cpp": {
            "head": "/*** ", // 统一增加几个*号
            "middle": " * @",
            "end": " */"
            },
            // 针对有特殊要求的文件如：test.blade.php
            "blade.php":{
            "head": "<!--",
            "middle": " * @",
            "end": "-->",
            }
        },
    // 默认注释  没有匹配到注释符号的时候使用。
    "annotationStr": { 
        "head": "/*",
        "middle": " * @",
        "end": " */",
        "use": false
        },
    },
    "files.associations": {
        "adc.h": "c"
    }
        
}
```



#### references

> [VSCode 插件：KoroFileHeader 深度指南：自动生成注释与代码片段定制-CSDN 博客](https://blog.csdn.net/qq_41972807/article/details/123054532?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-0-123054532-blog-130366752.235^v43^pc_blog_bottom_relevance_base9&spm=1001.2101.3001.4242.1&utm_relevant_index=2)
>
> [VS Code——koroFileHeader 插件：生成头部注释、函数注释-CSDN 博客](https://blog.csdn.net/qq_44170108/article/details/130366752)
>
> 





### Vue

https://marketplace.visualstudio.com/_apis/public/gallery/publishers/Vue/vsextensions/volar/2.2.10/vspackage

#### error

1.80.8 版本 vscode 不支持该版本插件，而且无法选择低版本下载

#### solution

1. 下载 vsix 文件

2. 修改后缀名为 zip

3. 解压

4. 修改 \extension\package.json 中的如下内容

   ```json
   	"engines": {
   		"vscode": "^1.88.0"
   	},
   ```

   为报错版本号

   ```json
   	"engines": {
   		"vscode": "^1.80.0"
   	},
   ```

   

> 解决方案: 将插件文件的 .vsix 后缀更改为 .zip 并解压,在 extensions 文件夹里找到 package.json ,打开进行更改, "engines": { "**vscode**": "^1.54.1" }, 将**vscode**版本号更改为报错的版本号.保存,再将 .zip 改为 .vsix ,继续第二步操作



## settings

### 插件安装位置

https://blog.csdn.net/weixin_43751329/article/details/122506815


### 基础配置
#### CTRL + 鼠标滚轮
1. 通过设置界面启用

    打开 VSCode，点击菜单栏中的 文件 -> 首选项 -> 设置。

    在右上角的搜索框中输入 mouse wheel zoom。

    找到 Editor: Mouse Wheel Zoom 选项，并勾选其前面的复选框。
    
2. 修改 settings.json 文件

    打开 VSCode，点击 文件 -> 首选项 -> 设置。

    点击右上角的 打开 settings.json。

    在文件中添加以下配置：
    "editor.mouseWheelZoom": true
    
    保存文件后重启 VSCode。

    示例代码
    ```json
    {
      "editor.mouseWheelZoom": true
    }
    ```

## clear cache

route: **C:\Users\%username%\AppData\Local\Microsoft\vscode-cpptools**

reference: [link](https://www.52pojie.cn/forum.php?mod=viewthread&tid=1959079)

> 非常感谢该博客的整理，在此引用并在下方粘贴全文

VsCode 是一款 **轻量级** 代码编辑器

可用一段就会很快发现，“轻量级”的 VsCode 并不轻量

不统计不知道，一统计吓一跳，使用了一段时间后，VsCode 占用了我 C 盘 10G+的空间！

好家伙，于是我决定治理一下 VsCode，让 VsCode 变得真正的轻量级。

### VsCode 的空间占用分析

VsCode 所占用的空间，主要包括四大部分（下面是我写此博客时统计的结果）：

1. `程序的安装目录`：大约会占用 350M
2. `%userprofile%\.vscode`：可达 800M。主要为：各个拓展。VsCode 卸载拓展似乎不会删除硬盘上的文件，因此这个里面很大，并且混有很多不用的
3. `%userprofile%\AppData\Local\Microsoft\vscode-cpptools\ipch`：用一段时间能达到 4G 与 C(++)语言有关，关闭程序后可以直接删。不使用 VsCode 编辑 C/C++的用户可能无此痛苦
4. `%userprofile%\AppData\Roaming\Code`：2G+ 存放用户数据、配置等。 （可以通过启动时添加--user-data-dir NewDir 来使其他目录作为配置）

可以定期删除的地方，有 `3. ipch`（可完全删除） 和 `4. Romaing`（不可完全删除）

#### 4. Romaing 中，到底哪些可以定期删除

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

### 定时删除目录

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

### ⚠️Warning

运行脚本后再次运行 VsCode 基本上看不出什么不同，只是当前工作路径下所打开的文件需要重新手动点击打开。

毕竟是一个能删除很多东西的脚本，因此请谨慎使用。

我作为本篇博客的原创博主，只是为大家提供了一个便捷的方法，但是其可能造成的后果，博主并不承担责任。

但是大家可以放心的是，我自己也在定期运行这个脚本。

准备有空的时候将其加入 Windows 计划，以实现定期地自动释放空间。





# Bottom