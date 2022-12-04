## 前言

### 环境

操作系统版本Win11 22H2(OS内部版本 22621.819)

软件版本为1.9.20

![image-20221125215511085](https://cdn.staticaly.com/gh/abottleofmilk/CDN@master/img/image-20221125215511085.png)



### 安装



### 一些基本概念

+ OPF（开放打包格式）： EPUB  文件如何相互关联，元数据详细信息(content.opf)。
+ OPS（开放出版结构）：描述 EPUB  文件中所有内容的关键规范。
+ OCF（OEBPS 容器格式）：如何将文件打包成.epub文件。

## 基础

### 一般的操作流程

### 编辑器

+ 如果在外部程序中编辑文件时在 Sigil 中更改文件，则可能会丢失数据。
+ 使用外部编辑器操作完保存后，再在sigil中编辑。

### 自定义用户界面

要将工具栏移动到其他位置，请将光标悬停在工具栏左侧的抓取栏上。当您这样做时，将出现一个移动光标。左右移动控制大小，直接拖动移动到其他位置。



![image-20221125222320730](https://cdn.staticaly.com/gh/abottleofmilk/CDN@master/img/image-20221125222320730.png)

如果您使工具栏小于将显示所有图标的大小，则工具栏右侧将出现一个箭头。当您单击该箭头时，将出现一个子菜单，允许访问工具栏中的所有按钮。



![image-20221125222247724](https://cdn.staticaly.com/gh/abottleofmilk/CDN@master/img/image-20221125222247724.png)



面板同样可以拖动，拖到你想放置的位置，松开鼠标即可。自定义图标可以控制其样式和大小。



### 导入文件

#### 文本文件

文本文件不是理想的来源，但它们仍然比某些格式更好，因为它们具有更少的不必要的HTML 标记。如果您对其他格式有很多问题，它们可能值得使用。有时向干净的文档添加样式比尝试清理转换后的文件更快。

## 高级技巧

### 插件

支持  Python 插件，允许用户自定义 Sigil 的使用方式并将其集成到自己的工作流程中，并独立于  Sigil 添加他们需要或想要的工具。可以下载并安装这些插件以添加对 Sigil 的扩展支持。这些插件包括 epubcheck、Access‑Aide、KindleImport、Kindlegen、FlightCrew、ePub3‑itizer、DOCX Import 插件等。Sigil  嵌入了自己的 Python 解释器（在撰写本文时为 v3.9.9，以支持基于 Python 3  的插件）。

### 自动化列表



## 其他工具

### 可能有用的网址

[Word to ePub Tutorial | ePubble](https://www.epubble.com/word-to-epub-tutorial/)

[Writing A Book Description By Thinking Like A Copywriter (justpublishingadvice.com)](https://justpublishingadvice.com/how-a-copywriter-would-write-a-book-description/)

[MobileRead Forums](https://www.mobileread.com/)

[Sigil Plugin Index - MobileRead Forums](https://www.mobileread.com/forums/showthread.php?t=247431)

### 可能有用的工具

| 名称                   | 简单描述              |
| ---------------------- | --------------------- |
| Word to ePub Converter | word转PDF工具 windows |
| The Document Converter | word转PDF工具 apple   |
|                        |                       |



### 翻译sigil

  Sigil 使用 Qt 的  Linguist 工具来创建和编辑翻译。



## 参考
1. [Sigil User Guide](https://sigil-ebook.com/sigil/guide/)
2. [Epub指南--从入门到放弃|`赤霓`编著]
3. [Sigil_Plugin_Framework_rev14.epub](https://github.com/Sigil-Ebook/Sigil/blob/master/docs/Sigil_Plugin_Framework_rev14.epub)