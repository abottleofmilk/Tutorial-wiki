## Autoit基础教程

### 安装与目录

双击是运行脚本还是编辑脚本，建议安装86版。

| 名称        | 描述                                     |
| ----------- | ---------------------------------------- |
| Autoit3Help | 帮助文档                                 |
| AutoIT3.exe | 运行对应的脚本                           |
| Au3Info.exe | 提供编写脚本对于的一些参数，像元素选择器 |

### 编辑器汉化

打开[Localised SciTE (sourceforge.io)](https://scintilla.sourceforge.io/SciTETranslation.html) , 选择[Chinese 1.73](https://scintilla.sourceforge.io/locale.zh_gb.properties) (Simplified - GB2312) 另存为文件，文件名保存为locale.properties，保存到对应的SciTE目录下。打开User options文件，复制下面内容。

```
code.page=936

output.code.page=936

character.set=134
```

### 工具介绍

- **AutoIt**程序文件，文档和示例。
- **Aut2Exe**–脚本到可执行转换器。将您的脚本转换为独立的.exe文件！

- **AutoItX**– DLL/COM 控件。将自动功能添加到您喜欢的编程和脚本语言中！还具有C#程序集和PowerShell CmdLets。

- **编辑器** – SciTE 脚本编辑器包的精简版本，用于入门。下载下面的软件包以获取完整版本！

### 运算符

=、==。单等于号不区分大小写。深入字符串时，单引号双引号区分开，不然要敲两遍。&连接两个字符串。

### 注释

#### 单行注释

**在脚本中分号(;) 的身份是注释符**. 一旦某条语句里出现了分号,则除非它在某个字符串内,否则跟在其后的所有同行语句都将被脚本解释器/编译器忽略而不起任何作用.

```au3
; 下面这行语句的结尾带有一条有助于别人更好理解程序的注释
Sleep(5000)  ;暂停 5 秒
```

#### 多行注释

[#comments-start](https://www.autoitx.com/Doc/html/keywords/comments-start.htm) 和 [#comments-end](https://www.autoitx.com/Doc/html/keywords/comments-start.htm) 关键字.你可以使用缩写的关键字 **#cs** 和 **#ce** 代替.不能注释它们自己!

```au3
#comments-start
    MsgBox(4096, "", "这是不执行的")
    MsgBox(4096, "", "或者这样")
#comments-end

; #cs
MsgBox(4096, "", "如果取消上下行任意的注释将出现警告:没有发现匹配的 '#cs/#ce'.")
; #ce
```

### 鼠标操作

#### 鼠标点击

MouseClick、MouseDown、MouseUp

#### 鼠标拖拽

MouseClickDrag

#### 鼠标移动

MouseMove

#### 鼠标滚动

MouseWheel

#### 获取当前位置

MouseGetPos

### 键盘

#### 模拟键击

一将标识置为1，二将特殊符号放{}里面。组合键与其他键组合时中间无须任何连接符，直接跟在后面即可。windows不允许模拟crtl+alt+del组合键。

![image-20221116211913370](https://cdn.staticaly.com/gh/abottleofmilk/CDN@master/img/image-20221116211913370.png)



![image-20221116212720337](https://cdn.staticaly.com/gh/abottleofmilk/CDN@master/img/image-20221116212720337.png)

功能键全部为大写。重复操作后面加上数字即可。

### 复制和粘贴

ClipPut、ClipGet

### 程序流程控制



## 语言相关

### 变量类型

#### 变量声明

**必须以英文 字符"$"开头**,其中只能包含 **字母**, **数字** 和下划线**_**字符.Dim、local、Global。一次可以声明多个变量用逗号分隔开，可以直接声明且赋值。函数内部尽量使用Local，避免污染。

#### 变量的作用域

某个变量的作用域要看您是何时以及如何声明该变量的. 如果您在脚本开头且在所有函数之外声明了某个变量 则该变量将在**Global(全局)**范围内存在,此时您就可以在脚本的任意位置读取或更改该变量, 我们把这种变量称为全局变量.

如果您是在某个 [函数](https://www.autoitx.com/Doc/html/intro/lang_functions.htm) 内部声明一个变量则该变量就只在该函数的 **Local(局部)** 范围内有效,我们把这种变量称为局部变量. 在函数内创建的变量将在函数结束时 自动被销毁.

在默认情况下,使用 [Dim](https://www.autoitx.com/Doc/html/keywords/Dim.htm) 声明的变量或在函数内部直接赋值而成的变量都是 **Local(局部)变量**,**除非** 有同名的全局变量存在(此时将视此变量为该全局变量). 另外我们可以使用关键字 [Local](https://www.autoitx.com/Doc/html/keywords/Dim.htm) 和 [Global](https://www.autoitx.com/Doc/html/keywords/Dim.htm) 来声明变量以 **强制** 变量的作用域.

#### 宏

AutoIt 提供了一系列[宏(Macros)](https://www.autoitx.com/Doc/html/macros.htm),它们是具有常量属性的(不可修改). 为与普通的变量区分开来,AutoIt 使用 **@** 字符而不是 **$** 字符来表示宏. 和普通的变量一样您可以在表达式中使用它们 但却不可以进行赋值操作.

#### 用户函数

所谓函数是指可在脚本中调用并实现特定"功能"的代码片段. 在 AutoIt 中有两种函数, 包括**内建函数**和**用户函数**.

用户可通过使用 [Func...EndFunc ](https://www.autoitx.com/Doc/html/keywords/Func.htm)语句来自定义函数.可按需要定义函数的参数及其返回值.**函数名必须用字母或下划线"_"开头**, 剩下的部分(非首字符)则可在字母,数字或下划线中随意选择。

```
$val = 10 
For $i = 1 To 10
     $doubled = MyDouble($val)
     MsgBox(0, "", $val & " 的两倍是 " & $doubled)
     $val = $doubled
Next

Exit


Func MyDouble($value)
     $value = $value * 2
     Return $value
EndFunc
```

### 函数

函数先声明后调用。

### 进程管理

Run、RunWait、shutdown。ProcessList、ProcessClose、ProcessExist、ProcessWait、ProcessWaitClose、

### GUI

GUI由一个或多个窗口构成，这些窗口又带有一个或多个控件。

![image-20221116222925377](https://cdn.staticaly.com/gh/abottleofmilk/CDN@master/img/image-20221116222925377.png)

#### 基本函数

#### GUI事件模式

消息循环模式默认、OnEvent模式。

Opt("GUIOnEventMode", 1)

### 文件操作

## 参考

1. [AutoIt (autoitscript.com)](https://www.autoitscript.com/autoit3/docs/)
2. [AutoIt 在线文档 (autoitx.com)](https://www.autoitx.com/Doc/)
3. [autoit 在线手册中文版_脚本之家 (jb51.net)](https://www.jb51.net/shouce/autoit/?tdsourcetag=s_pctim_aiomsg)
4. [autoit脚本编程办公自动化_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV127411F75C/?spm_id_from=333.337.search-card.all.click)
5. [AU3教程，AU3从零开始（IT天空wang754782072大神制作）_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1pE411K77h/)
6. [AutoIT操作Windows标准控件的方法 - 十零 - 博客园 (cnblogs.com)](https://www.cnblogs.com/wlei5206/p/15955276.html)