> **2022/5/17：新版教程已发布，[点此查看](https://gitee.com/FeignClaims/vscode-llvm-cpp-starter#https://gitee.com/link?target=https%3A%2F%2Fblog.csdn.net%2FtyKuGengty%2Farticle%2Fdetails%2F124828372 "点此查看")。**
> 
> **2022/5/17：新版教程已发布，**[点此查看](https://gitee.com/FeignClaims/vscode-llvm-cpp-starter#https://gitee.com/link?target=https%3A%2F%2Fblog.csdn.net%2FtyKuGengty%2Farticle%2Fdetails%2F124828372 "点此查看")**。**
> 
> **2022/5/17：新版教程已发布，**[点此查看](https://gitee.com/FeignClaims/vscode-llvm-cpp-starter#https://gitee.com/link?target=https%3A%2F%2Fblog.csdn.net%2FtyKuGengty%2Farticle%2Fdetails%2F124828372 "点此查看")**。**
> 
> 2022/2/4：本文章不再予以更新

___

## \-1- 前言

## ①目的

        我于 2021 年4月开始学习 CS，前几月一直使用 [VSCode](https://so.csdn.net/so/search?q=VSCode&spm=1001.2101.3001.7020) + GCC + GDB + Git 进行学习，翻阅韩骏老师的**《Visual Studio Code 权威指南》**时，发现他在 C++ 栏目里推荐了名为**「vscode-clangd」**的插件（已改名为**clangd**）。

        后配置相关插件时遇到诸多问题，查阅不少文章、文档，经几天才配置满意。想到可能有同道会遇到同样的问题，故而写下本文章。

        文章主旨是**为****初学 C++ 的人简易地配置出一个满意的编程环境，不会有 CMake、Git 等的详细教程。**我认为这就像婴儿学步一样：婴儿练习的是跑步，经历多次跌倒后很快便学会了走路，借助学步车的反而学得很慢。

>         **——我想提供的是「助跑器」，而不是「学步车」。**

        由于仅从今年4月开始学习，会存在很多疏漏和不够专业的地方，还望海涵。

## ②与按照[官方文档](https://code.visualstudio.com/docs/cpp/config-mingw "官方文档")配置好的 VSCode 相比拥有的优势

-   **代码拥有更加丰富的颜色。**我利用 VSCode Default Dark+ 主题自带的代码颜色的互补色、相近色，为「类型参数」、「成员函数」、「成员变量」、「函数参数」等与「类」、「自动变量」的颜色作了区分。

![代码拥有更加丰富的颜色](https://img-blog.csdnimg.cn/20210905203427492.gif)

**代码拥有更加丰富的颜色**

-   **相对更加精准的「功能」、「转到定义」、「重命名符号」等功能。**
-   **Clang-Tidy提供了强大的「静态检查」支持，并对于部分代码提供「快速修复」。**具体请见Clang-Tidy Checks。这里我主要添加了对于「[Google 开源项目风格指南](https://google.github.io/styleguide/cppguide.html# "Google 开源项目风格指南")(有中文版，但翻译版本滞后，需注意)」「[Cpp Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines "Cpp Core Guidelines")」和性能、潜在的bug、移植性、现代C++的检查。

![](https://img-blog.csdnimg.cn/20210905210211226.jpg?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBARmVpZ25DbGFpbXM=,size_20,color_FFFFFF,t_70,g_se,x_16)

**静态检查**

-   **自动添加头文件。**对于建议中的项会即时自动添加头文件，导航条会自动下移（观察行号）隐藏添加的头文件。

![自动添加头文件](https://img-blog.csdnimg.cn/20210905204417891.gif)

**自动添加头文件**

-   **利用「Git」进行版本管理。**
-   **通过「CMake」实现项目管理。**

## ③未解决的问题

-   **用 LLDB 调试时，无法正确跳转到「系统头文件」而显示为「未知源」，使用 GDB 调试同一个文件则没有此问题。**尝试过「[vscode-lldb 在 GitHub 的 Issues](https://github.com/vadimcn/vscode-lldb/issues "vscode-lldb 在 GitHub 的 Issues") 中给出的静态链接相关库」和「[Clang 编译器用户手册](https://clang.llvm.org/docs/UsersManual.html "Clang 编译器用户手册")中给出的将 -g 改为 -glldb」等方法，最终无果。

___

## \-1- 安装

## ①安装 VSCode

### 通过[官方网站](https://code.visualstudio.com/ "官方网站")获取

下载安装包并安装即可，略。

### 下载慢？请参考[《VSCode官网下载缓慢或下载失败的解决办法》](https://blog.csdn.net/zhaomengszu/article/details/112261258 "《VSCode官网下载缓慢或下载失败的解决办法》")

这里给出 x86\_64 1.60.0 版本的[下载链接](https://vscode.cdn.azure.cn/stable/e7d7e9a9348e6a8cc8c03f877d39cb72e5dfb1ff/VSCodeUserSetup-x64-1.60.0.exe "下载链接")。

## ②安装 MSYS2

### 通过[官方网站](https://www.msys2.org/ "官方网站")获取

下载安装包并安装即可，略。

### 下载慢？通过[清华大学开源软件镜像站](https://mirrors.tuna.tsinghua.edu.cn/ "清华大学开源软件镜像站")获取

进入[清华大学开源软件镜像站](https://mirrors.tuna.tsinghua.edu.cn/ "清华大学开源软件镜像站")，点击右侧的「获取下载链接」，切换到「应用软件」即可找到。

![](https://img-blog.csdnimg.cn/20210905215154553.jpg?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBARmVpZ25DbGFpbXM=,size_20,color_FFFFFF,t_70,g_se,x_16)

清华大学开源软件镜像站

## ③安装 Git

### 通过[官方网站](https://git-scm.com/ "官方网站")获取

下载安装包并安装即可，略。

### 下载慢？通过[清华大学开源软件镜像站](https://mirrors.tuna.tsinghua.edu.cn/ "清华大学开源软件镜像站")获取

进入[清华大学开源软件镜像站](https://mirrors.tuna.tsinghua.edu.cn/ "清华大学开源软件镜像站")，点击右侧的「获取下载链接」，切换到「应用软件」即可找到。

 安装时，切换 Git 的默认编辑器为 VSCode。

![](https://img-blog.csdnimg.cn/20210906093326435.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBARmVpZ25DbGFpbXM=,size_14,color_FFFFFF,t_70,g_se,x_16)

切换 Git 的默认编辑器为 VSCode

## ④配置环境变量

右键「开始」菜单，选择「系统」，在「系统」中点击「高级系统设置」，选择「环境变量(N)...」，在上方的「用户变量」或下方的「系统变量」，找到「Path」并选中编辑。

如果得到的是图一样式，在原「变量值」尾部加入英语输入法下的分号「;」后，加入「MSYS2 安装路径\\clang64\\bin」（默认为 C:\\msys64\\clang64\\bin）。

![](https://img-blog.csdnimg.cn/20210906090526349.jpg)

图一

如果得到的是图二样式，点击「新建」，并输入「MSYS2 安装路径\\clang64\\bin」（默认为 C:\\msys64\\clang64\\bin）即可。

![](https://img-blog.csdnimg.cn/20210906090630484.jpg?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBARmVpZ25DbGFpbXM=,size_15,color_FFFFFF,t_70,g_se,x_16)

图二

同样的我们也可以把C:\\msys64\\mingw64\\bin加入其中，但我并没有用上。

## ⑤利用 MSYS2 安装「Clang」「CMake」「Git」等软件

通过「开始」菜单，或路径（默认为 C:\\msys64 ）打开「MSYS2.exe」

以下是会用到的指令：

```
pacman -Syu    pacman -Su    pacman -Ss 关键字    pacman -S 包名    pacman -Rs 包名    pacman -R 包名    
```

比如**《C++程序设计：原理与实践》**一书中提到 FLTK 库。输入「pacman -Ss fltk」进行搜索，会查找到众多包名。由于使用的是clang64，所以需要安装以clang64/开头的「mingw-w64-clang-x86\_64-fltk」。可以通过右键进行复制，接着输入「pacman -S mingw-w64-clang-x86\_64-fltk」即可安装。

![](https://img-blog.csdnimg.cn/20210906091132470.jpg?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBARmVpZ25DbGFpbXM=,size_16,color_FFFFFF,t_70,g_se,x_16)

pacman -Ss fltk

这里我直接列出需要执行的指令：

```
pacman -S mingw-w64-clang-x86_64-toolchain mingw-w64-clang-x86_64-cninja mingw-w64-clang-x86_64-python-six mingw-w64-clang-x86_64-python-pippip install cmake_formatpacman -Syupacman -Syu
```

> **题外话：**笔者最近使用 cpan 安装 Perl 模块时发现，需要使用的是 Clang64.exe，来安装对应 perl 的模块，而非 msys2.exe.

## ⑥在 VSCode 中安装需要的插件

打开「VSCode」点击左边栏上方最后一项「Extensions」以进行插件安装，必需的插件请见**快速安装我所推荐插件。**

当然，我们也可以搜索「Chinese」安装汉化界面插件，**后面的表述也会用汉化后的界面**，更多插件请见**「-4-（可选）我所使用的VSCode插件」。**

### 快速安装我所推荐插件 

用「VSCode」打开一个文件夹，在该文件夹中新建名为「.vscode」的文件夹，在其中新建全名为「extensions.json」的文件，并在其中加入如下代码。

```
{"recommendations": ["jeff-hykin.better-cpp-syntax","danielpinto8zz6.c-cpp-project-generator","twxs.cmake","ms-vscode.cmake-tools","guyutongxue.cpp-reference","llvm-vs-code-extensions.vscode-clangd","ms-vscode.cpptools","cheshirekow.cmake-format"  ]}
```

如图所示

![](https://img-blog.csdnimg.cn/20210906095447479.jpg?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBARmVpZ25DbGFpbXM=,size_20,color_FFFFFF,t_70,g_se,x_16)

extensions.json

同样的，由左边栏进入「Extensions」，在搜索框中输入「@recommended」，即可得到我所推荐的插件。（然而还是只能一个一个点击安装）

> **注意：**
> 
> -   先安装「C/C++」再安装「clangd」安装完成后，会提示发生冲突（见下图），请选择「Disable IntelliSense」。
> -   MSYS2 中安装的 clangd 存在一定问题，请在 VSCode 中通过「Ctrl + Shift + P」打开命令菜单，输入 clangd 并 选择「clangd: Download language server」安装插件提供的版本。

![](https://img-blog.csdnimg.cn/20210906095707789.jpg?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBARmVpZ25DbGFpbXM=,size_9,color_FFFFFF,t_70,g_se,x_16)

输入「@recommended」

![](https://img-blog.csdnimg.cn/20210906100951555.jpg)

冲突

___

## \-2- 配置配置文件

「VSCode」界面下，点击左下角的齿轮，选择「设置」，我们可以通过切换「用户」/「工作区」等，决定是为整个软件还是为单个工作区更改设置。

在右上角点击「打开设置」，可以切换到设置对应的 「settings.json」 文件。

这里我倾向于将尽量多的设置置于 VSCode 的配置文件中，以便于用账号同步设置，没有给 Clangd 等单独新建配置文件。

![](https://img-blog.csdnimg.cn/20210906103029295.jpg?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBARmVpZ25DbGFpbXM=,size_20,color_FFFFFF,t_70,g_se,x_16)

设置界面

如果阅读了**安装插件**并按照**注意**进行了操作，那么在 settings.json 中已经存在以下配置（路径可能不同）：

```
{"clangd.path": "c:\\Users\\FeignClaims\\AppData\\Roaming\\Code\\User\\globalStorage\\llvm-vs-code-extensions.vscode-clangd\\install\\12.0.1\\clangd_12.0.1\\bin\\clangd.exe","C_Cpp.intelliSenseEngine": "Disabled"}
```

我们可以看到，配置行之间以英语输入法下的逗号「,」间隔，整个配置文件之外还会有一对大花括号，**我们可以将鼠标停在"clangd.path"上，以查看配置说明**。

针对**"clangd.path"**一项，你也可以使用 「MSYS2 安装路径\\\\clang64\\\\bin\\\\clangd.exe」。

接下来我将贴出我的各插件及 VSCode 的部分配置及注释（注意添加逗号），你可以选择性地后附到自己的 settings.json 中。

我所使用的通用插件和 C/C++ 插件及其配置请见 **\-4-（可选）我所使用的VSCode插件**，**\-5-（可选）我所使用的VSCode配置。**

## VSCode

```
"editor.unicodeHighlight.ambiguousCharacters": false,"debug.console.acceptSuggestionOnEnter": "on","debug.internalConsoleOptions": "neverOpen","editor.acceptSuggestionOnEnter": "off","editor.autoClosingOvertype": "always","editor.detectIndentation": false,"editor.formatOnPaste": true,"editor.formatOnSave": true,"editor.inlineSuggest.enabled": true,"editor.parameterHints.enabled": true,"editor.quickSuggestions": {"comments": false,"other": true,"strings": false  },"editor.quickSuggestionsDelay": 0,"editor.renderWhitespace": "none","editor.snippetSuggestions": "bottom","editor.stickyTabStops": true,"editor.suggest.insertMode": "replace","editor.suggest.localityBonus": true,"editor.suggest.shareSuggestSelections": true,"editor.suggest.showStatusBar": true,"editor.suggestOnTriggerCharacters": true,"editor.suggestSelection": "first","editor.tabSize": 2,"editor.wordBasedSuggestions": true,"explorer.confirmDelete": false,"explorer.confirmDragAndDrop": false,"explorer.incrementalNaming": "smart","extensions.ignoreRecommendations": true,"files.autoSave": "afterDelay","files.autoSaveDelay": 1000,"files.exclude": {"**/.classpath": true,"**/.factorypath": true,"**/.project": true,"**/.settings": true  },"files.hotExit": "onExitAndWindowClose","grunt.autoDetect": "on","gulp.autoDetect": "on","notebook.cellToolbarLocation": {"default": "right","jupyter-notebook": "left"  },"notebook.lineNumbers": "on","search.exclude": {  },"search.showLineNumbers": true,"search.smartCase": true,"terminal.integrated.defaultProfile.windows": "PowerShell","terminal.integrated.enableBell": true,"terminal.integrated.env.windows": {"LC_ALL": "zh_CN.UTF-8"  },"terminal.integrated.gpuAcceleration": "on","terminal.integrated.profiles.windows": {"Command Prompt": {"args": [],"icon": "terminal-cmd","path": ["${env:windir}\\Sysnative\\cmd.exe","${env:windir}\\System32\\cmd.exe"      ]    },"Git Bash": {"source": "Git Bash"    },"Msys2": {"args": ["-defterm", "-no-start", "-here"],"env": {"CHERE_INVOKING": "1","MSYS2_PATH_TYPE": "inherit","MSYSTEM": "CLANG64"      },"path": ["C:\\msys64\\msys2_shell.cmd"]    },"PowerShell": {"icon": "terminal-powershell","source": "PowerShell"    }  },"terminal.integrated.rightClickBehavior": "selectWord","vsintellicode.modify.editor.suggestSelection": "automaticallyOverrodeDefaultValue","workbench.iconTheme": "vscode-icons","workbench.startupEditor": "none","workbench.view.alwaysShowHeaderActions": true,"editor.largeFileOptimizations": false,"window.zoomLevel": 1
```

## Clangd

```
"C_Cpp.intelliSenseEngine": "Disabled","clangd.onConfigChanged": "restart","clangd.arguments": ["--clang-tidy","--compile-commands-dir=build","--completion-style=bundled","--enable-config","--fallback-style=Google","--function-arg-placeholders=false","--header-insertion-decorators","--header-insertion=iwyu","--log=verbose","--pch-storage=memory","--pretty","--ranking-model=heuristics","-j=12"  ],"clangd.checkUpdates": true,"clangd.path": "C:\\msys64\\clang64\\bin\\clangd.exe","editor.suggest.snippetsPreventQuickSuggestions": false,
```

> 2021/10/20: 升级到「Clangd 13.0.0」后，「--clang-tidy-checks=<string>」已被废弃，请添加参数「--enable-config」，并在「%USERPROFILE%\\AppData\\Local\\clangd」处创建文件**「config.YAML」**，并保存以下信息：

```
Diagnostics:  ClangTidy:Add: ["*"]    Remove:      [        abseil*,        fuchsia*,        llvmlib*,        zircon*,        altera*,        google-readability-todo,        readability-braces-around-statements,        hicpp-braces-around-statements,        modernize-use-trailing-return-type,      ]Index:  Background: Build
```

## CMake

```
"cmake.configureOnEdit": false,"cmake.configureOnOpen": true,"cmake.copyCompileCommands": "",
```

## LLDB（详见 [vscode-lldb 用户手册](https://github.com/vadimcn/vscode-lldb/blob/master/MANUAL.md "vscode-lldb 用户手册")）

```
"lldb.commandCompletions": true,"lldb.dereferencePointers": true,"lldb.evaluateForHovers": true,"lldb.launch.expressions": "simple","lldb.showDisassembly": "never","lldb.verboseLogging": true,
```

## Git

```
"git.autofetch": true,"git.confirmSync": false,"git.enableSmartCommit": true,
```

## （可选）Fira Code 连字体及界面

效果图：

![preview](https://img-blog.csdnimg.cn/img_convert/1ae5d011031119e8b67424978458e821.png)

首先，我们需要安装 [Fira Code 字体](https://github.com/tonsky/FiraCode " Fira Code 字体")。

然后配置如下：

```
"[Log]": {"editor.fontSize": 15  },"editor.codeLensFontFamily": "Fira Code Retina","editor.fontFamily": "Fira Code Retina","editor.fontLigatures": true,"editor.fontSize": 16,"terminal.integrated.fontSize": 14,
```

## （可选）多彩代码

```
"editor.bracketPairColorization.enabled": true,"editor.guides.bracketPairs": true,"editor.semanticHighlighting.enabled": true,"editor.semanticTokenColorCustomizations": {"enabled": true,"rules": {"*.abstract": {"fontStyle": "italic"      },"readonly": "#4FC1FF","*.static": {"fontStyle": "bold"      },"macro": {"foreground": "#4FC1FF"      },"method": {"fontStyle": "underline"      },"namespace": {"foreground": "#00D780"      },"parameter": {"foreground": "#C8ECFF"      },"parameter.readonly": {"foreground": "#7BD1FF"      },"property": {"fontStyle": "underline","foreground": "#C8ECFF"      },"typeParameter": "#31A567","comment": "#767BA6"    }  },"workbench.colorCustomizations": {"[Default Dark+]": {"editorBracketHighlight.foreground3": "#9CDCFE","editorBracketHighlight.foreground4": "#F3FD00","editorBracketHighlight.foreground5": "#F47D9F","editorBracketHighlight.foreground6": "#A5ADFE"    }  },
```

___

## \-3- 建立一个C++专用学习文件夹

> 还没完！如果我们现在编写一个 .cpp 文件，会发现连系统头文件都查找不了，原因在于我们没有告诉 Clangd 我们的编译器是什么，会有什么参数——更别提系统头文件路径了！

当然我们可以打开「设置」，在「Clangd: Fallback Flags」一项里告诉 Clangd 未找到「compile\_commands.json」时编译器的默认参数应该是什么。

——但这样做无法成功让 Clangd 分析多文件项目。

我会在**用 CMake 支撑框架**一节介绍如何用 CMake 生成 compile\_commands.json。

## ①建立文件结构

思路来自[VSCode 配置 C/C++ 终极解决方案：vs code + clang + clangd + lldb （MacOS利用完整 clang-llvm 工具链）](https://zhuanlan.zhihu.com/p/398790625 "VSCode 配置 C/C++ 终极解决方案：vs code + clang + clangd + lldb （MacOS利用完整 clang-llvm 工具链）")。 

文件夹命名规范源自 [Google 开源项目代码指南](https://google.github.io/styleguide/cppguide.html# "Google 开源项目代码指南")，戳此为[中文版](https://google-styleguide.readthedocs.io/zh_CN/latest/ "中文版")，但翻译版本滞后，需注意。

> 当然，未用**粗体**标出的所有文件/文件夹名都可自定义。

我们在电脑某处新建一个文件夹「code」，专用于编程；在「code」文件夹中新建一个文件夹「cpp」，用于C++编程。

在「VSCode」中选择「文件」-「将文件夹添加到工作区...」，将「cpp」文件夹添加进来，此后我们可以通过「文件」-「工作区另存为...」来保存该工作区以便后序使用以及单独配置、安装插件等。

接下来我们按照自己的需要新建文件夹，比如：

我打算新建一个「practice」文件夹用于学习书上例题、习题，在「practice」内按照再书籍名称、目录细分子文件夹。

同时新建一个「gsl」文件夹，在里面存放「Cpp Core Guidelines」使用的轻量库[GSL: Guidelines support library](https://github.com/microsoft/GSL/releases/tag/v3.1.0 "GSL: Guidelines support library")——一个只需包含头文件，无需链接的库。

（这里是为了说明，碰巧这个库在 MSYS2 中无法下载，你也可以下载后把「gsl」文件夹放在「MSYS2 安装路径\\clang64\\include」里作为「系统头文件」）

![](https://img-blog.csdnimg.cn/20210906163342269.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBARmVpZ25DbGFpbXM=,size_10,color_FFFFFF,t_70,g_se,x_16)

接下来我们考虑一件事：**如何编译链接、调试代码？**

虽然接下来会用 CMake 来管理整个工作区，但我并不打算借助CMake来负责编译链接代码（这也是个一旦入门就很简单的问题），CMake 在这里的作用仅仅是支撑框架、为 Clangd 提供「compile\_commands.json」以分析多文件项目。

如果你想要学习如何通过CMake来进行编译、链接，请在**看完本文章**后，浏览最后的**\-7- 参考**。

我们在根目录新建文件夹**「.vscode」**，在其内新建全名为**「tasks.json」**（任务）和全名为**「launch.json」**（调试配置）的文件。

![](https://img-blog.csdnimg.cn/2021090618035735.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBARmVpZ25DbGFpbXM=,size_10,color_FFFFFF,t_70,g_se,x_16)

老样子，我会附出代码和对应注释，**如果你想真正理解，就需要翻阅更多资料了**。

tasks.json：

> 额外的，对于 gsl 库，在参数中加入"-I${workspaceFolder}\\\\gsl"(-大写的i)(include)
> 
> 由于 gsl 库只有头文件，故无需再参数中加入"-lgsl"(-小写的L)(link)来链接

```
{"tasks": [    {"type": "shell","label": "Clang++: 编译单文件","command": "clang++","args": ["${fileDirname}\\${fileBasenameNoExtension}.cpp","-o","${workspaceFolder}\\build\\test.exe","-g","-pedantic","-Wall","-Wextra","-pthread","-fuse-ld=lld","-fsanitize=address","-fsanitize=undefined","-stdlib=libc++","-std=c++20","--target=x86_64-w64-mingw"      ],"options": {"cwd": "${workspaceFolder}"      },"problemMatcher": ["$gcc"],"group": {"kind": "build","isDefault": true      },"presentation": {"echo": true,"reveal": "always","focus": false,"panel": "shared"      },"detail": "Clang++: 编译单个文件"    },    {"type": "shell","label": "Clang++: 编译多文件","command": "clang++","args": ["${fileDirname}\\*.cpp","-o","${workspaceFolder}\\build\\test.exe","-g","-pedantic","-Wall","-Wextra","-pthread","-fuse-ld=lld","-fsanitize=address","-fsanitize=undefined","-stdlib=libc++","-std=c++20","--target=x86_64-w64-mingw"      ],"options": {"cwd": "${workspaceFolder}"      },"problemMatcher": ["$gcc"],"group": {"kind": "build","isDefault": true      },"presentation": {"echo": true,"reveal": "always","focus": false,"panel": "shared"      },"detail": "Clang++: 编译当前文件所在目录里所有文件"    }  ],"version": "2.0.0"}
```

launch.json：

```
{"version": "0.2.0","configurations": [    {"name": "LLDB: 生成和调试单文件","type": "lldb","request": "launch","program": "${workspaceFolder}\\build\\test","args": [],"stopOnEntry": false,"cwd": "${fileDirname}","internalConsoleOptions": "neverOpen","environment": [],"externalConsole": false,"setupCommands": [        {"text": "settings set target.process.thread.step-avoid-regexp","description": "Enable stepping into STL"        },        {"text": "settings set target.process.thread.step-avoid-libraries","description": "Avoid stepping into libraries"        }      ],"preLaunchTask": "Clang++: 编译单文件"    },    {"name": "LLDB: 生成和调试多文件","type": "lldb","request": "launch","program": "${workspaceFolder}\\build\\test","args": [],"stopOnEntry": false,"cwd": "${fileDirname}","internalConsoleOptions": "neverOpen","environment": [],"externalConsole": false,"setupCommands": [        {"text": "settings set target.process.thread.step-avoid-regexp","description": "Enable stepping into STL"        },        {"text": "settings set target.process.thread.step-avoid-libraries","description": "Avoid stepping into libraries"        }      ],"preLaunchTask": "Clang++: 编译多文件"    },    {"name": "LLDB: 调试已编译的 test.exe","type": "lldb","request": "launch","program": "${workspaceFolder}\\build\\test","args": [],"stopOnEntry": false,"cwd": "${fileDirname}","internalConsoleOptions": "neverOpen","environment": [],"externalConsole": false,"setupCommands": [        {"text": "settings set target.process.thread.step-avoid-regexp","description": "Enable stepping into STL"        },        {"text": "settings set target.process.thread.step-avoid-libraries","description": "Avoid stepping into libraries"        }      ]    }  ]}
```

配置好后，你可以点击「终端」-「运行生成任务...」或Ctrl + Shift + B运行任务，这会同注释一样，编译你打开的文件，并输出为工作区根目录下的 debug.exe。

之后（或你可以同时进行），你可以点击「运行」-「启动调试」或 F5 进行调试，要更换调试配置，点击左侧「运行和调试」即可在侧边栏上方更改了。

更多的参数请参考 [Visual Studio Code Variables Reference](https://code.visualstudio.com/docs/editor/variables-reference "Visual Studio Code Variables Reference") 和 [Clang 编译器用户手册](https://clang.llvm.org/docs/UsersManual.html "Clang 编译器用户手册")。

## ②用 CMake 支撑框架

在我的理解下，「CMake」的配置是通过在各目录里添加名为**「CMakeLists.txt」**的文件，并在该文件中定义所在文件夹的信息完成的，所有信息都会被分析后储存在「build」文件夹中，同时生成编译器用以分析文件结构的「compile\_commands.json」。

> 我们本节要做的事，就是借助 CMake 得到 compile\_commands.json，以让 Clangd 发挥全部作用。

我们首先在工作区根目录新建一个这样的文件，并保存以下内容。在**「CMakeLists.txt」**中，注释是以「#」开头的。

```
#要求 CMake 最低版本cmake_minimum_required(VERSION 3.0.0)#工程名称（根目录必须设置工程名称，设置相同工程名的文件将会被视作同一工程）project(cpp)#添加源外构建，增加 include 的搜索路径（类似于 C++ 添加头文件搜索路径）set(CMAKE_MODULE_PATH    ${CMAKE_MODULE_PATH}    ${CMAKE_CURRENT_SOURCE_DIR}/cmake_modules    )#添加 basicEnv 文件中的内容（类似于 C++ 中的 #include）include(basic_env)#添加子目录 practice，要求子目录也创建有 CMakeLists.txt#由于 gsl 目录中只含有头文件，不含有源文件，我们无需添加add_subdirectory(practice)
```

正如 6-9 行**要求**的，我们在工作区根目录下新建文件夹「cmake\_modules」，在其中新建全名为「basic\_env.cmake」的文件，在这里我们如**「tasts.json」**一样添加编译器参数。

```
set(CMAKE_CXX_FLAGS"${CMAKE_CXX_FLAGS} -g -pthread -pedantic -Wall -Wextra -fsanitize=address -fsanitize=undefined -std=c++20 --target=x86_64-w64-mingw")
```

![](https://img-blog.csdnimg.cn/20210906182943598.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBARmVpZ25DbGFpbXM=,size_9,color_FFFFFF,t_70,g_se,x_16)

进入「practice」文件夹中。每当我们进入一个文件夹，就询问自己：

> 这个文件夹里的内容，是属于同一个工程吗？

显然，「practice」文件夹是用于包含我们的读书子目录的，并不算作一个工程。

但基于根目录**「CMakeLists.txt」**的内容「add\_subdirectory(practice)」，我们仍要为其新建一个**「CMakeLists.txt」**。

就像前面说的，「practice」不是一个工程，我们也没必要给它一个工程名称。在**「CMakeLists.txt」**中我们唯一需要做的，就是通过「add\_subdirectory(文件夹名)」将子目录加入 CMake 框架里。

![](https://img-blog.csdnimg.cn/20210906183527388.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBARmVpZ25DbGFpbXM=,size_20,color_FFFFFF,t_70,g_se,x_16)

我们已经到达概念上的「工程目录」了。

如果是真正的工程，我们可能需要深入每个目录，一个个添加上**「CMakeLists.txt」**。

但我们只是为了获取「compile\_commands.json」而已，而一本书与另一本书的例题、习题代码不太可能发生交互。所以我们在「工程目录」根目录下简单地添加**「CMakeLists.txt」**，并要求：

-   **这是一个工程**
-   **目录里所有的源文件（这里是以 .cc 为后缀名的源文件）都会被编译成工程的执行文件**
-   **目录里所有的头文件都可能被包含**

例如，对于「c++\_primer\_plus」工程目录，我要求它的工程名为「c++\_primer\_plus」：

```
#工程名称project(c++_primer_plus)#将所有以 .cpp 为后缀名的源文件添加到变量 src 中file(GLOB_RECURSE src "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp")#添加头文件可能的路径(系统头文件在 Clangd 知道编译器是什么的时候就确定了路径)include_directories(    #根目录的 gsl 库    ${CMAKE_SOURCE_DIR}/gsl)#将 src 对应的文件作为最终生成可执行文件的部分源文件#add_executable(工程名称 参数1 参数2 ...)#变量需要以${变量名}的形式引用add_executable(c++_primer_plus ${src})
```

> 如果你想偷点懒，也可以在「practice」文件夹下的**「CMakeLists.txt」**中配置这些内容。
> 
> 但可能更麻烦。

关闭「VS Code」，重新打开该工作区，CMake将会自动搜索编译器，并对整个工作区进行配置。

如果没有搜索到，Ctrl + Shift + P 打开命令菜单，搜索「cmake」，并选择「CMake: 编辑用户本地 CMake 工具包」，并添加/替换以下信息：（其中编译器路径应当改为MSYS2安装路径）

```
[  {"name": "Clang 12.0.1 x86_64-w64-windows-gnu","compilers": {"C": "C:\\msys64\\Clang64\\bin\\clang.exe","CXX": "C:\\msys64\\Clang64\\bin\\clang++.exe"    }  }]
```

> 由于我在设置中禁用了 CMake「保存时自动配置」（你也可以打开），当我们需要更新配置时，Ctrl + Shift + P 打开命令菜单，搜索「cmake」，并选择「CMake: 配置」。
> 
> **此外，别忘了搜索「clangd」并选择「clangd: Restart language server」，让 Clangd 读取新的配置。**

如果想要学习如何通过CMake来进行编译、链接，请在**看完本文章**后，浏览最后的**\-7- 参考**。

## ③用 Git 实现版本管理

什么是版本管理？你暂时可以认为版本管理是在备份我们的每一次修改，如果哪次修改不如意，你可以很简单地从中恢复过来。当然**版本管理远不止这个用途**。

### 让 Git 忽略文件/文件夹

由**用 CMake 支撑框架**一节，我们已经知道「.cache」文件夹是用于**缓存 Clangd 分析出的信息**，而每当我们启动「VSCode」或通过命令菜单手动「配置」时，「build」文件夹都会**基于其他文件**更新。——这两个文件夹根本没有备份的必要。

所以我们在工作区根目录新建全名为「.gitignore」的文件。在其中加入：

```
/.cache//build/
```

关于 .gitignore 的更多信息请参考 [.gitignore](https://www.jianshu.com/p/699ed86028c2 ".gitignore")

### 配置我们的 Git

首先我们要让 Git 认识我们。

新建一个终端（可参考**\-4- 常用快捷键 其他**），键入以下内容：

```
git config --global user.name "你的昵称"git config --global user.email "你的邮箱"
```

点击左侧「源代码管理」-「初始化存储库」。

**你现在已经拥有一个接近专业的C++工作区了。**

___

## \-4- 常用快捷键

**越少从键盘切换到鼠标，我们****的效率越高。**

以下是部分常用快捷键（更多请参考 [VSCode 快捷键](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf "VSCode 快捷键") 或 「文件」-「首选项」-「键盘快捷方式」）：

## 插入行

-   Ctrl + Enter：在该行下方插入一行
-   Ctrl + Shift + Enter：在该行上方插入一行

![](https://img-blog.csdnimg.cn/20210906141712434.gif)

## 行操作（可与 多光标和选取 搭配使用）

-   Ctrl + Shift + K：删除行
-   Alt + ↑/↓：移动行
-   Shift + Alt + ↑/↓：复制行

![](https://img-blog.csdnimg.cn/2021090614300725.gif)

## 多光标和选取

-   Shift + ←/→：单字选取
-   Ctrl + Shift + ←/→：单词选取
-   Shift + Alt + ←/→：缩小/扩展选区
-   Ctrl + Alt + ↑/↓：在上/下方添加光标（无法撤销添加）
-   Ctrl + Shift + Alt + ↑/↓/←/→：块选择（也能添加光标且能撤销，选择到行尾后不会跳转到下一行）
-   Shift + Alt + i：在选择区域的各行末添加一个光标

![](https://img-blog.csdnimg.cn/20210906143625602.gif)

## 其他

-   Ctrl + .：查看选中部分的快速修复（可配合 Ctrl + A 全选使用，也可以考虑直接使用 clang-tidy -fix，具体见[官方文档](https://clang.llvm.org/extra/clang-tidy/index.html "官方文档")）
-   Shift + Alt + .：如果选中部分仅有一个可修复项，对选中部分自动修复
-   Ctrl + S：保存当前文件
-   Ctrl + Shift + P：打开命令菜单
-   Ctrl + B：切换侧边栏的可见性
-   Ctrl + Shift + B：运行生成任务
-   Ctrl + Space：手动触发建议
-   Ctrl + Shift + Space：手动触发参数提示
-   Ctrl + \`(Tab上方的那个键)：切换终端的可见性（如果没有终端，会新建一个）
-   F2：重命名符号
-   F5：使用当前配置调试
-   F12：转到定义
-   Ctrl + ↑/↓：上/下滚编辑器
-   Ctrl + F/H：搜索/替换
-   按住Ctrl，鼠标左键：转到定义、跳转到对应文件
-   ……

___

## \-5-（可选）我所使用的VSCode插件

使用方法请见**快速安装我所推荐的插件**

## 通用插件

```
{"recommendations": ["ms-vscode.azure-account","ms-azuretools.vscode-azureappservice","ms-azuretools.vscode-azureresourcegroups","hookyqr.beautify","aaron-bond.better-comments","samuelcolvin.jinjahtml","auchenberg.vscode-browser-preview","ms-ceintl.vscode-language-pack-zh-hans","formulahendry.code-runner","adpyke.codesnap","bierner.color-info","randomfractalsinc.vscode-data-preview","hediet.debug-visualizer","ms-azuretools.vscode-docker","cschlosser.doxdocgen","editorconfig.editorconfig","redvanworkshop.explorer-exclude-vscode-extension","mkxml.vscode-filesize","mhutchie.git-graph","github.vscode-pull-request-github","eamodio.gitlens","kisstkondoros.vscode-gutter-preview","wix.vscode-import-cost","oderwat.indent-rainbow","leetcode.vscode-leetcode","ritwickdey.liveserver","yzhang.markdown-all-in-one","webfreak.debug","eg2.vscode-npm-script","christian-kohler.npm-intellisense","techer.open-in-browser","ibm.output-colorizer","quicktype.quicktype","christian-kohler.path-intellisense","johnpapa.vscode-peacock","esbenp.prettier-vscode","chrmarti.regex","humao.rest-client","shan.code-settings-sync","tyriar.sort-lines","gruntfuggly.todo-tree","chakrounanas.turbo-console-log","visualstudioexptteam.vscodeintellicode","deerawan.vscode-faker","mikey.vscode-fileheader","vscode-icons-team.vscode-icons","jaspernorth.vscode-pigments","wasteamaccount.webtemplatestudio-dev-nightly","redhat.vscode-yaml","appulate.filewatcher","dbaeumer.vscode-eslint","vadimcn.vscode-lldb","codeinchinese.englishchinesedictionary","alefragnani.bookmarks","hbybyyang.gitee-vscode-plugin","bbenoist.doxygen","jbockle.jbockle-format-files","njpwerner.autodocstring","richie5um2.vscode-sort-json","ms-toolsai.jupyter-keymap","albymor.increment-selection","shd101wyy.markdown-preview-enhanced","nmsmith89.incrementor","ms-toolsai.jupyter","ms-toolsai.jupyter-renderers","jkjustjoshing.vscode-text-pastry","octref.vetur","asvetliakov.vscode-neovim"  ]}
```

## C++插件

```
{"recommendations": ["jeff-hykin.better-cpp-syntax","danielpinto8zz6.c-cpp-project-generator","twxs.cmake","ms-vscode.cmake-tools","guyutongxue.cpp-reference","llvm-vs-code-extensions.vscode-clangd","ms-vscode.cpptools","cheshirekow.cmake-format","jbenden.c-cpp-flylint"  ]}
```

___

## \-6-（可选）我所使用的VSCode配置

使用方法请见**配置配置文件**

**注意**：配置中并没有给出Clangd的路径，请自行复制粘贴相关配置。

```
{"editor.unicodeHighlight.ambiguousCharacters": false,"debug.console.acceptSuggestionOnEnter": "on","debug.internalConsoleOptions": "neverOpen","editor.acceptSuggestionOnEnter": "off","editor.autoClosingOvertype": "always","editor.detectIndentation": false,"editor.formatOnPaste": true,"editor.formatOnSave": true,"editor.inlineSuggest.enabled": true,"editor.parameterHints.enabled": true,"editor.quickSuggestions": {"comments": false,"other": true,"strings": false  },"editor.quickSuggestionsDelay": 0,"editor.renderWhitespace": "none","editor.snippetSuggestions": "bottom","editor.stickyTabStops": true,"editor.suggest.insertMode": "replace","editor.suggest.localityBonus": true,"editor.suggest.shareSuggestSelections": true,"editor.suggest.showStatusBar": true,"editor.suggestOnTriggerCharacters": true,"editor.suggestSelection": "first","editor.tabSize": 2,"editor.wordBasedSuggestions": true,"explorer.confirmDelete": false,"explorer.confirmDragAndDrop": false,"explorer.incrementalNaming": "smart","extensions.ignoreRecommendations": true,"files.autoSave": "afterDelay","files.autoSaveDelay": 1000,"files.exclude": {"**/.classpath": true,"**/.factorypath": true,"**/.project": true,"**/.settings": true  },"files.hotExit": "onExitAndWindowClose","grunt.autoDetect": "on","gulp.autoDetect": "on","notebook.cellToolbarLocation": {"default": "right","jupyter-notebook": "left"  },"notebook.lineNumbers": "on","search.exclude": {  },"search.showLineNumbers": true,"search.smartCase": true,"terminal.integrated.defaultProfile.windows": "PowerShell","terminal.integrated.enableBell": true,"terminal.integrated.env.windows": {"LC_ALL": "zh_CN.UTF-8"  },"terminal.integrated.gpuAcceleration": "on","terminal.integrated.profiles.windows": {"Command Prompt": {"args": [],"icon": "terminal-cmd","path": ["${env:windir}\\Sysnative\\cmd.exe","${env:windir}\\System32\\cmd.exe"      ]    },"Git Bash": {"source": "Git Bash"    },"Msys2": {"args": ["-defterm", "-no-start", "-here"],"env": {"CHERE_INVOKING": "1","MSYS2_PATH_TYPE": "inherit","MSYSTEM": "CLANG64"      },"path": ["C:\\msys64\\msys2_shell.cmd"]    },"PowerShell": {"icon": "terminal-powershell","source": "PowerShell"    }  },"terminal.integrated.rightClickBehavior": "selectWord","vsintellicode.modify.editor.suggestSelection": "automaticallyOverrodeDefaultValue","workbench.iconTheme": "vscode-icons","workbench.startupEditor": "none","workbench.view.alwaysShowHeaderActions": true,"editor.largeFileOptimizations": false,"window.zoomLevel": 1"[Log]": {"editor.fontSize": 15  },"editor.codeLensFontFamily": "Fira Code Retina","editor.fontFamily": "Fira Code Retina","editor.fontLigatures": true,"editor.fontSize": 16,"terminal.integrated.fontSize": 14,"editor.bracketPairColorization.enabled": true,"editor.guides.bracketPairs": true,"editor.semanticHighlighting.enabled": true,"editor.semanticTokenColorCustomizations": {"enabled": true,"rules": {"*.abstract": {"fontStyle": "italic"      },"readonly": "#4FC1FF","*.static": {"fontStyle": "bold"      },"macro": {"foreground": "#4FC1FF"      },"method": {"fontStyle": "underline"      },"namespace": {"foreground": "#00D780"      },"parameter": {"foreground": "#C8ECFF"      },"parameter.readonly": {"foreground": "#7BD1FF"      },"property": {"fontStyle": "underline","foreground": "#C8ECFF"      },"typeParameter": "#31A567","comment": "#767BA6"    }  },"workbench.colorCustomizations": {"[Default Dark+]": {"editorBracketHighlight.foreground3": "#9CDCFE","editorBracketHighlight.foreground4": "#F3FD00","editorBracketHighlight.foreground5": "#F47D9F","editorBracketHighlight.foreground6": "#A5ADFE"    }  },"[jsonc]": {"editor.defaultFormatter": "esbenp.prettier-vscode"  },"git.autofetch": true,"git.confirmSync": false,"git.enableSmartCommit": true,"C_Cpp.intelliSenseEngine": "Disabled","clangd.onConfigChanged": "restart","clangd.arguments": ["--clang-tidy","--compile-commands-dir=build","--completion-style=bundled","--enable-config","--fallback-style=Google","--function-arg-placeholders=false","--header-insertion-decorators","--header-insertion=iwyu","--log=verbose","--pch-storage=memory","--pretty","--ranking-model=heuristics","-j=12"  ],"clangd.checkUpdates": true,"clangd.path": "C:\\msys64\\clang64\\bin\\clangd.exe","editor.suggest.snippetsPreventQuickSuggestions": false,"cmake.configureOnEdit": false,"cmake.configureOnOpen": true,"cmake.copyCompileCommands": "","lldb.commandCompletions": true,"lldb.dereferencePointers": true,"lldb.evaluateForHovers": true,"lldb.launch.expressions": "simple","lldb.showDisassembly": "never","lldb.verboseLogging": true,"better-comments.highlightPlainText": true,"better-comments.multilineComments": true,"better-comments.tags": [    {"backgroundColor": "transparent","bold": false,"color": "#DC143C","italic": false,"strikethrough": false,"tag": "bug:","underline": false    },    {"backgroundColor": "transparent","bold": false,"color": "#DC143C","italic": false,"strikethrough": false,"tag": "\\$","underline": false    },    {"backgroundColor": "transparent","bold": false,"color": "#008000","italic": false,"strikethrough": false,"tag": "done:","underline": false    },    {"backgroundColor": "transparent","bold": false,"color": "#008000","italic": false,"strikethrough": false,"tag": "\\;","underline": false    },    {"backgroundColor": "transparent","bold": false,"color": "#4169E1","italic": false,"strikethrough": false,"tag": "fixme:","underline": false    },    {"backgroundColor": "transparent","bold": false,"color": "#4169E1","italic": false,"strikethrough": false,"tag": "\\%","underline": false    },    {"backgroundColor": "transparent","bold": false,"color": "#DEB887","italic": false,"strikethrough": false,"tag": "note:","underline": false    },    {"backgroundColor": "transparent","bold": false,"color": "#DEB887","italic": false,"strikethrough": false,"tag": "\\]","underline": false    },    {"backgroundColor": "transparent","bold": false,"color": "#FFD700","italic": false,"strikethrough": false,"tag": "star:","underline": false    },    {"backgroundColor": "transparent","bold": false,"color": "#FFD700","italic": false,"strikethrough": false,"tag": "\\*","underline": false    },    {"backgroundColor": "transparent","bold": false,"color": "#FF2C00","italic": false,"strikethrough": false,"tag": "alert:","underline": false    },    {"backgroundColor": "transparent","bold": false,"color": "#FF2C00","italic": false,"strikethrough": false,"tag": "\\!","underline": false    },    {"backgroundColor": "transparent","bold": false,"color": "#3498DB","italic": false,"strikethrough": false,"tag": "question:","underline": false    },    {"backgroundColor": "transparent","bold": false,"color": "#3498DB","italic": false,"strikethrough": false,"tag": "\\?","underline": false    },    {"backgroundColor": "transparent","bold": false,"color": "#FF8C00","italic": false,"strikethrough": false,"tag": "todo:","underline": false    },    {"backgroundColor": "transparent","bold": false,"color": "#FF8C00","italic": false,"strikethrough": false,"tag": "\\>","underline": false    }  ],"code-runner.executorMap": {"cpp": "cd $dir && clang++ $fileName -pedantic -Wall -Wextra -pthread -fuse-ld=lld -fsanitize=address -fsanitize=undefined -stdlib=libc++ -std=c++20 --target=x86_64-w64-mingw -o $workspaceRoot\\build\\test && $workspaceRoot\\build\\test"  },"code-runner.runInTerminal": true,"doxdocgen.generic.useGitUserEmail": true,"doxdocgen.generic.useGitUserName": true,"indentRainbow.updateDelay": 0,"jake.autoDetect": "on","redhat.telemetry.enabled": true,"todo-tree.filtering.excludeGlobs": ["build", "data"],"todo-tree.general.tagGroups": {"ALERT": ["ALERT:"],"BUG": ["BUG:"],"DONE": ["DONE:"],"FIXME": ["FIXME:"],"NOTE": ["NOTE:"],"QUESTION": ["QUESTION:"],"STAR": ["STAR:"],"TODO": ["TODO:", "TODO(www41):"]  },"todo-tree.general.tags": ["ALERT:","QUESTION:","TODO:","TODO(www41):","DONE:","FIXME:","BUG:","NOTE:","STAR:","alert:","question:","todo:","done:","fixme:","bug:","note:","star:"  ],"todo-tree.highlights.customHighlight": {"ALERT": {"background": "#FF2C00","foreground": "#FFFAFA","icon": "alert","iconColour": "#FF2C00","rulerColour": "#FF2C00"    },"BUG": {"background": "#DC143C","foreground": "#FFFAFA","iconColour": "#DC143C","rulerColour": "#DC143C"    },"DONE": {"background": "#008000","foreground": "#FFFAFA","icon": "check-circle-fill","iconColour": "#008000","rulerColour": "#008000"    },"FIXME": {"background": "#4169E1","foreground": "#FFFAFA","icon": "gear","iconColour": "#4169E1","rulerColour": "#4169E1"    },"NOTE": {"background": "#DEB887","foreground": "#000000","icon": "bookmark-fill","iconColour": "#DEB887","rulerColour": "#DEB887"    },"QUESTION": {"background": "#3498DB","foreground": "#FFFAFA","icon": "question","iconColour": "#3498DB","rulerColour": "#3498DB"    },"STAR": {"background": "#FFD700","foreground": "#3E13AF","icon": "star-fill","iconColour": "#FFD700","rulerColour": "#FFD700"    },"TODO": {"background": "#FF8C00","foreground": "#FFFAFA","iconColour": "#FF8C00","rulerColour": "#FF8C00"    },"alert:": {"background": "#FF2C00","foreground": "#FFFAFA","hideFromTree": true,"icon": "alert","iconColour": "#FF2C00","rulerColour": "#FF2C00"    },"bug:": {"background": "#DC143C","foreground": "#FFFAFA","hideFromTree": true,"iconColour": "#DC143C","rulerColour": "#DC143C"    },"done:": {"background": "#008000","foreground": "#FFFAFA","hideFromTree": true,"icon": "check-circle-fill","iconColour": "#008000","rulerColour": "#008000"    },"fixme:": {"background": "#4169E1","foreground": "#FFFAFA","hideFromTree": true,"icon": "gear","iconColour": "#4169E1","rulerColour": "#4169E1"    },"note:": {"background": "#DEB887","foreground": "#000000","hideFromTree": true,"icon": "bookmark-fill","iconColour": "#DEB887","rulerColour": "#DEB887"    },"question:": {"background": "#3498DB","foreground": "#FFFAFA","hideFromTree": true,"icon": "question","iconColour": "#3498DB","rulerColour": "#3498DB"    },"star:": {"background": "#FFD700","foreground": "#3E13AF","hideFromTree": true,"icon": "star-fill","iconColour": "#FFD700","rulerColour": "#FFD700"    },"todo:": {"background": "#FF8C00","foreground": "#FFFAFA","hideFromTree": true,"iconColour": "#FF8C00","rulerColour": "#FF8C00"    }  },"todo-tree.highlights.defaultHighlight": {"rulerLane": "left","type": "tag"  },"todo-tree.regex.regex": "((\\**|//|#|<!--|;|/\\*|^)\\s*($TAGS)(\\([\\w]+\\))?:?|^\\s*- \\[ \\])"}
```

___

## \-7- 参考

+ [VSCode 配置 C++：VSCode + Clang + Clangd + LLDB + CMake + Git_FeignClaims的博客-CSDN博客_vscode配置clang](https://blog.csdn.net/tyKuGengty/article/details/120119820)

-   [Get Started with C++ and Mingw-w64 in Visual Studio Code](https://code.visualstudio.com/docs/cpp/config-mingw "Get Started with C++ and Mingw-w64 in Visual Studio Code")
-   [Clang 编译器用户手册](https://clang.llvm.org/docs/UsersManual.html "Clang 编译器用户手册")
-   [Clang-Format 风格配置](https://clang.llvm.org/docs/ClangFormatStyleOptions.html "Clang-Format 风格配置")
-   [Clang-Format 文档](https://clang.llvm.org/docs/ClangFormat.html "Clang-Format 文档")
-   [vscode-lldb 用户手册](https://github.com/vadimcn/vscode-lldb/blob/v1.6.5/MANUAL.md "vscode-lldb 用户手册")
-   [在windows上通过msys2/mingw来安装gcc / clang\_茶佬牛逼](https://blog.csdn.net/yuejisuo1948/article/details/105333354?utm_medium=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromMachineLearnPai2~default-4.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromMachineLearnPai2~default-4.control "在windows上通过msys2/mingw来安装gcc / clang_茶佬牛逼")
-   [配置VSCode的C/C++语言功能 - literalkernel](https://www.cnblogs.com/sinx/p/12410619.html "配置VSCode的C/C++语言功能 - literalkernel")
-   [最终，我看向了clangd](https://zhuanlan.zhihu.com/p/364518020 "最终，我看向了clangd")
-   [CMake 简介和 CMake 模板 - 米罗西](https://www.cnblogs.com/zhehan54/p/5668285.html "CMake 简介和 CMake 模板 - 米罗西")
-   [CMake在多级目录项目中的简单使用](https://www.jianshu.com/p/2eb8a8d7b2b0 "CMake在多级目录项目中的简单使用")
-   [VSCode 配置 C/C++ 终极解决方案：vs code + clang + clangd + lldb （MacOS利用完整 clang-llvm 工具链）](https://zhuanlan.zhihu.com/p/398790625 "VSCode 配置 C/C++ 终极解决方案：vs code + clang + clangd + lldb （MacOS利用完整 clang-llvm 工具链）")
-   [CMake简明教程 实例工程演示（含字幕）](https://www.bilibili.com/video/BV1A7411f7jT "CMake简明教程 实例工程演示（含字幕）")