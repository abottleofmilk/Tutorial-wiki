## 基础
### 前言
Qt 是一个跨平台的框架。跨平台 GUI 通常有三种实现策略：

- **API 映射**：API 映射是说，界面库使用同一套  API，将其映射到不同的底层平台上面。大体相当于将不同平台的 API 提取公共部分。比如说，将 Windows 平台上的按钮控件和 Mac OS 上的按钮组件都取名为 Button。当你使用 Button 时，如果在 Windows 平台上，则编译成按钮控件；如果在 Mac OS  上，则编译成按钮组件。这么做的好处是，所有组件都是原始平台自有的，外观和原生平台一致；缺点是，编写库代码的时候需要大量工作用于适配不同平台，并且，**只能提取相同部分的 API**。比如 Mac OS 的文本框自带拼写检测，但是 Windows 上面没有，则不能提供该功能。这种策略的典型代表是  wxWidgets。这也是一个标准的 C++ 库，和 Qt 一样庞大。它的语法看上去和 MFC 类似，有大量的宏。据说，一个 MFC  程序员可以很容易的转换到 wxWidgets 上面来。
- **API 模拟**：前面提到，API  映射会“缺失”不同平台的特定功能，而 API 模拟则是解决这一问题。不同平台的有差异  API，将使用工具库自己的代码用于模拟出来。按照前面的例子，Mac OS 上的文本框有拼写检测，但是 Windows  的没有。那么，工具库自己提供一个拼写检测算法，让 Windows 的文本框也有相同的功能。API 模拟的典型代表是 wine —— 一个  Linux 上面的 Windows 模拟器。它将大部分 Win32 API 在 Linux 上面模拟了出来，让 Linux 可以通过 wine  运行 Windows 程序。由此可以看出，API 模拟最大优点是，应用程序无需重新编译，即可运行到特定平台上。另外一个例子是微软提供的  DirectX，这个开发库将屏蔽掉不同显卡硬件所提供的具体功能。使用这个库，你无需担心硬件之间的差异，如果有的显卡没有提供该种功能，SDK  会使用软件的方式加以实现。*（关于举例，可以参考文末一段精彩的讨论。）*
- **GUI 模拟**：任何平台都提供了图形绘制函数，例如画点、画线、画面等。有些工具库利用这些基本函数，在不同绘制出自己的组件，这就是 GUI 模拟。GUI  模拟的工作量无疑是很大的，因为需要使用最基本的绘图函数将所有组件画出来；并且这种绘制很难保证和原生组件一模一样。但是，这一代价带来的优势是，可以很方便的修改组件的外观——只要修改组件绘制函数即可。很多跨平台的 GUI 库都是使用的这种策略，例如 gtk+（这是一个 C 语言的图形界面库。使用 C  语言很优雅地实现了面向对象程序设计。不过，这也同样带来了一个问题——使用大量的类型转换的宏来模拟多态，并且它的函数名一般都比较长，使用下划线分割单词，看上去和 Linux 如出一辙。gtk+ 并不是模拟的原生界面，而有它自己的风格，所以有时候就会和操作系统的界面格格不入。），Swing 以及我们的  Qt。
  

Qt 和 wxWidgets 一样，也是一个标准的 C++ 库。但是它的语法类似于 Java 的  Swing，十分清晰，而且使用信号槽（signal/slot）机制，让程序看起来很明白——这也是很多人优先选择 Qt  的一个很重要的原因。不过，所谓“成也萧何，败也萧何”。这种机制虽然很清楚，但是它所带来的后果是你需要使用 Qt 的 moc  对程序进行预处理，才能够再使用标准的 make 或者 nmake 进行正常的编译，并且信号槽的调用要比普通的函数调用慢大约一个数量级（Qt 4  文档中说明该数据，但 Qt 5 尚未有官方说明）。Qt 的界面也不是原生风格的，尽管 Qt 使用 style  机制十分巧妙地模拟了原生界面。另外值得一提的是，Qt 不仅仅能够运行在桌面环境中，还可以运行在嵌入式平台以及手机平台。
### 入门
Qt具有其他编程语言的扩展，但Qt本身是用C++开发的。

![](https://s2.loli.net/2022/11/30/w1UcgoGYXpDfHSh.png)

+ Qt通过内省数据的使用而启用了许多现代语言特性，从而丰富了C++。这是通过使用**Qobject**基类实现的。这使得我们可以动态获取对象的属性和可用方法。
+ Qt使用元信息来支持信号和插槽机制。发出信号的对象不需要知道关于拥有槽的对象的任何信息，反之亦然。每个信号可以连接到任意数量的插槽，甚至连接到其他信号。

![](https://s2.loli.net/2022/11/30/mFEv9LBtaIRszCV.png)

+ QCoreApplication:为非GUI应用程序提供主事件循环.
+ QGuiApplication:为GU应用程序提供主事件循环 
+ QApplication:为Qt Widgets模块的应用程序提供主事件循环

QCoreApplication包含主事件循环，处理和分发来自操作系统和其他源的所有事件。它还处理应用程序的初始化与终结，以及系统范围和应用程序范围的设置。

QGuiApplication除了继承QCoreApplication的功能以外，还需负责初始化GUI所需的资源;跟踪系统界面属性，保证GUI与系统设置保持一致;提供字符串本地化、剪贴板，鼠标光标处理等功能。

QApplication除了继承QGuiApplication的功能以外，还需负责初始化QtWidgets模块所需的资源，并提供更多的接口。

如果需要使用元对象，就要继承Qobject。Qwindow是使用操作系统默认的Gui支持，功能有限，但比较轻量级。

### 全局定义

`<QtGlobal>`头文件包含了Qt类库的一些全局定义，包括基本数据类型、函数和宏，一般的Qt类的头文件都会包含该文件，所以不用显式包含这个头文件也可以使用其中的定义。

### QT模块与工具
Qt类库里大量的类根据功能分为各种模块，这些模块又分为几大类。
+ Qt基本模块（Qt Essentials）：提供了Qt在所有平台上的基本功能。
+ Qt附加模块（Qt Add-Ons）：实现一些特定功能的提供附加价值的模块。
+ 增值模块（Value-Add Modules）：单独发布的提供额外价值的模块或工具。
+ 技术预览模块（Technology Preview Modules）：一些处于开发阶段，但是可以作为技术预览使用的模块。Qt工具（Qt Tools）：帮助应用程序开发的一些工具。

#### Qt Essentials

Qt基本模块是Qt在所有平台上的基本功能，它们在所有的开发平台和目标平台上都可用，在Qt 5所有版本上是源代码和二进制兼容的。

| Module                                                       | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Qt Core](https://doc.qt.io/qt-6/qtcore-index.html)          | Core non-graphical classes used by other modules.            |
| [Qt D-Bus](https://doc.qt.io/qt-6/qtdbus-index.html)         | Classes for inter-process communication over the D-Bus protocol. |
| [Qt GUI](https://doc.qt.io/qt-6/qtgui-index.html)            | Base classes for graphical user interface (GUI) components.  |
| [Qt Network](https://doc.qt.io/qt-6/qtnetwork-index.html)    | Classes to make network programming easier and more portable. |
| [Qt QML](https://doc.qt.io/qt-6/qtqml-index.html)            | Classes for QML and JavaScript languages.                    |
| [Qt Quick](https://doc.qt.io/qt-6/qtquick-index.html)        | A declarative framework for building highly dynamic applications with custom user interfaces. |
| [Qt Quick Controls](https://doc.qt.io/qt-6/qtquickcontrols-index.html) | Provides lightweight QML types for creating performant user interfaces for  desktop, embedded, and mobile devices. These types employ a simple  styling architecture and are very efficient. |
| [Qt Quick Dialogs](https://doc.qt.io/qt-6/qtquickdialogs-index.html) | Types for creating and interacting with system dialogs from a Qt Quick application. |
| [Qt Quick Layouts](https://doc.qt.io/qt-6/qtquicklayouts-index.html) | Layouts are items that are used to arrange Qt Quick 2 based items in the user interface. |
| [Qt Quick Test](https://doc.qt.io/qt-6/qtquicktest-index.html) | A unit test framework for QML applications, where the test cases are written as JavaScript functions. **Note:** The binary compatibility guarantee does not apply to Qt Quick Test. However, it will remain source compatible. |
| [Qt Test](https://doc.qt.io/qt-6/qttest-index.html)          | Classes for unit testing Qt applications and libraries. **Note:** The binary compatibility guarantee does not apply to Qt Test. However, it will remain source compatible. |
| [Qt Widgets](https://doc.qt.io/qt-6/qtwidgets-index.html)    | Classes to extend Qt GUI with C++ widgets.                   |

#### Qt Add-Ons

Qt附加模块可以实现一些特定目的。这些模块可能只在某些开发平台上有，或只能用于某些操作系统，或只是为了向后兼容。

| Module                                                       | Development Platforms                          | Target Platforms                                             | Description                                                  |
| ------------------------------------------------------------ | ---------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Active Qt](https://doc.qt.io/qt-6/activeqt-index.html)      | [Windows](https://doc.qt.io/qt-6/windows.html) | [Windows](https://doc.qt.io/qt-6/windows.html)               | Classes for applications which use ActiveX and COM           |
| [Qt 3D](https://doc.qt.io/qt-6/qt3d-index.html)              | All                                            | All                                                          | Functionality for near-realtime simulation systems with support for 2D and 3D rendering. |
| [Qt 5 Core Compatibility APIs](https://doc.qt.io/qt-6/qtcore5-index.html) | All                                            | All                                                          | Qt Core APIs that were in Qt 5 but not Qt 6.                 |
| [Qt Bluetooth](https://doc.qt.io/qt-6/qtbluetooth-index.html) | All                                            | [Android](https://doc.qt.io/qt-6/android.html), [iOS](https://doc.qt.io/qt-6/ios.html), [Linux](https://doc.qt.io/qt-6/linux.html), [Boot to Qt](https://doc.qt.io/Boot2Qt/), [macOS](https://doc.qt.io/qt-6/macos.html) and [Windows](https://doc.qt.io/qt-6/windows.html) | Provides access to Bluetooth hardware.                       |
| [Qt Concurrent](https://doc.qt.io/qt-6/qtconcurrent-index.html) | All                                            | All                                                          | Classes for writing multi-threaded programs without using low-level threading primitives. |
| [Qt Help](https://doc.qt.io/qt-6/qthelp-index.html)          | All                                            | All                                                          | Classes for integrating documentation into applications.     |
| [Qt Image Formats](https://doc.qt.io/qt-6/qtimageformats-index.html) | All                                            | All                                                          | Plugins for additional image formats: TIFF, MNG, TGA, WBMP.  |
| [Qt Multimedia](https://doc.qt.io/qt-6/qtmultimedia-index.html) | All                                            | All*                                                         | A rich set of QML types and C++ classes to handle multimedia content. Also includes APIs to handle camera access. |
| [Qt NFC](https://doc.qt.io/qt-6/qtnfc-index.html)            | All                                            | [Android](https://doc.qt.io/qt-6/android.html), [iOS](https://doc.qt.io/qt-6/ios.html), [macOS](https://doc.qt.io/qt-6/macos.html), [Linux](https://doc.qt.io/qt-6/linux.html) and [Windows](https://doc.qt.io/qt-6/windows.html) | Provides access to Near-Field communication (NFC) hardware. On desktop platforms NDEF access is only supported for Type 4 tags. |
| [Qt OPC UA](https://doc.qt.io/qt-6/qtopcua-overview.html)    | All                                            | All (except QNX, WebAssembly)                                | Protocol for data modeling and exchange of data in industrial applications. |
| [Qt OpenGL](https://doc.qt.io/qt-6/qtopengl-index.html)      | All                                            | All                                                          | C++ classes that make it easy to use OpenGL in Qt applications. A separate library of [Qt OpenGL Widgets C++ Classes](https://doc.qt.io/qt-6/qtopenglwidgets-module.html) provides a widget for rendering OpenGL graphics. |
| [Qt PDF](https://doc.qt.io/qt-6/qtpdf-index.html)            | All                                            | [Windows](https://doc.qt.io/qt-6/windows.html), [Linux](https://doc.qt.io/qt-6/linux.html), and [macOS](https://doc.qt.io/qt-6/macos.html). | Classes and functions for rendering PDF documents.           |
| [Qt Positioning](https://doc.qt.io/qt-6/qtpositioning-index.html) | All                                            | [Android](https://doc.qt.io/qt-6/android.html), [iOS](https://doc.qt.io/qt-6/ios.html), [macOS](https://doc.qt.io/qt-6/macos.html), [Linux](https://doc.qt.io/qt-6/linux.html) and [Windows](https://doc.qt.io/qt-6/windows.html) | Provides access to position, satellite info and area monitoring classes. |
| [Qt Print Support](https://doc.qt.io/qt-6/qtprintsupport-index.html) | All                                            | All                                                          | Classes to make printing easier and more portable.           |
| [Qt Quick Widgets](https://doc.qt.io/qt-6/qtquickwidgets-index.html) | All                                            | All                                                          | Provides a C++ widget class for displaying a Qt Quick user interface. |
| [Qt Remote Objects](https://doc.qt.io/qt-6/qtremoteobjects-index.html#qt-remote-objects) | All                                            | All                                                          | Provides an easy to use mechanism for sharing a [QObject](https://doc.qt.io/qt-6/qobject.html)'s API (Properties/Signals/Slots) between processes or devices. |
| [Qt SCXML](https://doc.qt.io/qt-6/qtscxml-index.html)        | All                                            | All                                                          | Provides classes and tools for creating state machines from SCXML files and embedding them in applications. |
| [Qt Sensors](https://doc.qt.io/qt-6/qtsensors-index.html)    | All                                            | [Android](https://doc.qt.io/qt-6/android.html), [iOS](https://doc.qt.io/qt-6/ios.html), and [Windows](https://doc.qt.io/qt-6/windows.html) | Provides access to sensor hardware.                          |
| [Qt Serial Bus](https://doc.qt.io/qt-6/qtserialbus-index.html) | All                                            | [Linux](https://doc.qt.io/qt-6/linux.html), [Boot to Qt](https://doc.qt.io/Boot2Qt/), [macOS](https://doc.qt.io/qt-6/macos.html) and [Windows](https://doc.qt.io/qt-6/windows.html) | Provides access to serial industrial bus interfaces. Currently, the module supports the CAN bus and Modbus protocols. |
| [Qt Serial Port](https://doc.qt.io/qt-6/qtserialport-index.html) | All                                            | [Linux](https://doc.qt.io/qt-6/linux.html), [Boot to Qt](https://doc.qt.io/Boot2Qt/), [macOS](https://doc.qt.io/qt-6/macos.html) and [Windows](https://doc.qt.io/qt-6/windows.html) | Provides classes to interact with hardware and virtual serial ports. |
| [Qt Spatial Audio](https://doc.qt.io/qt-6/qtspatialaudio-index.html) | All                                            | All                                                          | Provides support for spatial audio. Create sound scenes in 3D space containing  different sound sources and room related properties such as reverb. |
| [Qt SQL](https://doc.qt.io/qt-6/qtsql-index.html)            | All                                            | All                                                          | Classes for database integration using SQL.                  |
| [Qt State Machine](https://doc.qt.io/qt-6/qtstatemachine-index.html) | All                                            | All                                                          | Provides classes for creating and executing state graphs.    |
| [Qt SVG](https://doc.qt.io/qt-6/qtsvg-index.html)            | All                                            | All                                                          | Classes for displaying the contents of SVG files. Supports a subset of the [SVG 1.2 Tiny](http://www.w3.org/TR/SVGTiny12/) standard. A separate library of [Qt SVG Widgets C++ Classes](https://doc.qt.io/qt-6/qtsvgwidgets-module.html) provides support for rendering SVG files in a widget UI. |
| [Qt TextToSpeech](https://doc.qt.io/qt-6/qttexttospeech-index.html) | All                                            | All                                                          | Provides support for synthesizing speech from text and playing it as audio output. |
| [Qt UI Tools](https://doc.qt.io/qt-6/qtuitools-index.html)   | All                                            | All                                                          | Classes for loading [QWidget](https://doc.qt.io/qt-6/qwidget.html) based forms created in *Qt Designer* dynamically, at runtime. |
| [Qt WebChannel](https://doc.qt.io/qt-6/qtwebchannel-index.html) | All                                            | All                                                          | Provides access to [QObject](https://doc.qt.io/qt-6/qobject.html) or QML objects from HTML clients for seamless integration of Qt applications with HTML/JavaScript clients. |
| [Qt WebEngine](https://doc.qt.io/qt-6/qtwebengine-index.html) | All                                            | [Windows](https://doc.qt.io/qt-6/windows.html), [Linux](https://doc.qt.io/qt-6/linux.html), and [macOS](https://doc.qt.io/qt-6/macos.html). | Classes and functions for embedding web content in applications using the [Chromium browser project](http://www.chromium.org/Home). |
| [Qt WebSockets](https://doc.qt.io/qt-6/qtwebsockets-index.html) | All                                            | All                                                          | Provides WebSocket communication compliant with [RFC 6455](https://datatracker.ietf.org/doc/html/rfc6455). |
| [Qt WebView](https://doc.qt.io/qt-6/qtwebview-index.html)    | All                                            | Platforms with a native web engine.                          | Displays web content in a QML application by using APIs native to the platform,  without the need to include a full web browser stack. |
| [Qt XML](https://doc.qt.io/qt-6/qtxml-index.html)            | All                                            | All                                                          | Handling of XML in a Document Object Model (DOM) API.        |

> Add-ons available under Commercial Licenses, or GNU General Public License v3

| [Qt Charts](https://doc.qt.io/qt-6/qtcharts-index.html)      | All                                        | All                                                          | UI Components for displaying visually pleasing charts, driven by static or dynamic data models. |
| ------------------------------------------------------------ | ------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Qt CoAP](https://doc.qt.io/qt-6/qtcoap-index.html)          | All                                        | All                                                          | Implements the client side of CoAP defined by RFC 7252.      |
| [Qt Data Visualization](https://doc.qt.io/qt-6/qtdatavisualization-index.html) | All                                        | All                                                          | UI Components for creating stunning 3D data visualizations.  |
| [Qt Lottie Animation](https://doc.qt.io/qt-6/qtlottieanimation-index.html) | All                                        | All                                                          | A QML API for rendering graphics and animations in JSON format, exported by the [Bodymovin](https://aescripts.com/bodymovin/) plugin for Adobe® After Effects. |
| [Qt MQTT](https://doc.qt.io/qt-6/qtmqtt-index.html)          | All                                        | All                                                          | Provides an implementation of the MQTT protocol specification. |
| [Qt Network Authorization](https://doc.qt.io/qt-6/qtnetworkauth-index.html) | All                                        | All                                                          | Provides support for OAuth-based authorization to online services. |
| [Qt Quick 3D](https://doc.qt.io/qt-6/qtquick3d-index.html)   | All                                        | All                                                          | Provides a high-level API for creating 3D content or UIs based on Qt Quick. |
| [Qt Quick Timeline](https://doc.qt.io/qt-6/qtquicktimeline-index.html) | All                                        | All                                                          | Enables keyframe-based animations and parameterization.      |
| [Qt Shader Tools](https://doc.qt.io/qt-6/qtshadertools-index.html) | All                                        | All                                                          | Provides tools for the cross-platform Qt shader pipeline. These enable  processing graphics and compute shaders to make them usable for Qt Quick and other components in the Qt ecosystem. |
| [Qt Virtual Keyboard](https://doc.qt.io/qt-6/qtvirtualkeyboard-index.html) | All                                        | [Linux](https://doc.qt.io/qt-6/linux.html) and [Windows](https://doc.qt.io/qt-6/windows.html) desktop, and [Boot to Qt](https://doc.qt.io/Boot2Qt/) targets. | A framework for implementing different input methods as well as a QML  virtual keyboard. Supports localized keyboard layouts and custom visual  themes. |
| [Qt Wayland Compositor](https://doc.qt.io/qt-6/qtwaylandcompositor-index.html) | [Linux](https://doc.qt.io/qt-6/linux.html) | [Linux](https://doc.qt.io/qt-6/linux.html) and [Boot to Qt](https://doc.qt.io/Boot2Qt/) targets. | Provides a framework to develop a Wayland compositor.        |

> Note: All* refers to all supported platforms except INTEGRITY.
#### Qt Add-Ons in Technical Preview

技术预览模块就是一些还处于开发和测试阶段的模块，一般技术预览模块经过几个版本的发布后会变成正式的模块。

| Module                                                       | Development Platforms | Target Platforms                                  | Description                                                  |
| ------------------------------------------------------------ | --------------------- | ------------------------------------------------- | ------------------------------------------------------------ |
| [Qt HTTP Server](https://doc.qt.io/qt-6/qthttpserver-index.html) | All                   | All                                               | A framework for embedding an HTTP server into a Qt application. |
| [Qt Quick 3D Physics](https://doc.qt.io/qt-6/qtquick3dphysics-index.html) | All                   | All supported platforms except QNX and INTEGRITY. | Qt Quick 3D Physics provides a high-level QML module adding physical simulation capabilities to Qt Quick 3D. |

#### 工具

+ Qt Designer 用于拓展Qt Designer的类
+ Qt help 在应用中集成在线文档的类，实现类似于Qt Assistant的功能
+ Qt UI tools 操作Qt Designer生成的窗口的类

| 工具        | 说明                                                         |
| ----------- | ------------------------------------------------------------ |
| qmake       | 核心的项目构建工具，可以生成跨平台的 .pro 项目文件，并能依据不同操作系统和编译工具生成相应的 Makefile，用于构建可执行程序或链接库。 |
| uic         | User Interface Compiler，用户界面编译器，Qt 使用 XML 语法格式的 .ui 文件定义用户界面，uic 根据 .ui 文件生成用于创建用户界面的 C++ 代码头文件，比如 ui_*****.h 。 |
| moc         | Meta-Object Compiler，元对象编译器，moc 处理 C++ 头文件的类定义里面的 Q_OBJECT  宏，它会生成源代码文件，比如 moc_*****.cpp ，其中包含相应类的元对象代码，元对象代码主要用于实现 Qt  信号/槽机制、运行时类型定义、动态属性系统。 |
| rcc         | Resource Compiler，资源文件编译器，负责在项目构建过程中编译 .qrc 资源文件，将资源嵌入到最终的 Qt 程序里。 |
| qtcreator   | 集成开发环境，包含项目生成管理、代码编辑、图形界面可视化编辑、 编译生成、程序调试、上下文帮助、版本控制系统集成等众多功能， 还支持手机和嵌入式设备的程序生成部署。 |
| assistant   | Qt 助手，帮助文档浏览查询工具，Qt 库所有模块和开发工具的帮助文档、示例代码等都可以检索到，是 Qt 开发必备神器，也可用于自学 Qt。 |
| designer    | Qt 设计师，专门用于可视化编辑图形用户界面（所见即所得），生成 .ui 文件用于 Qt 项目。 |
| linguist    | Qt 语言家，代码里用 tr() 宏包裹的就是可翻译的字符串，开发人员可用 lupdate 命令生成项目的待翻译字符串文件 .ts，用  linguist 翻译多国语言 .ts ，翻译完成后用 lrelease 命令生成 .qm 文件，然后就可用于多国语言界面显示。 |
| qmlscene    | 在 Qt 4.x 里是用 qmlviewer 进行 QML 程序的原型设计和测试，Qt 5 用 qmlscene 取代了旧的 qmlviewer。新的 qmlscene 另外还支持 Qt 5 中的新特性 scenegraph 。 |
| windeployqt | windeployqt 是 Qt 提供的 Windows 平台打包工具，它能找到可执行文件需要的所有动态链接库，并将它们拷贝到当前文件夹中。打包成功后将文件夹发给别人即可。 |

### 元对象系统（Meta-Object System)& Qobject
宏是C/C++系列语言的一大特色，**它将一个标识符定义为一个字符串，在预处理阶段源程序中的该标识符均以指定的字符串来代替，使用宏可以使代码更加简洁和增强可读性**。Qt对标准C++进行了扩展，引入了一些新的概念和功能。QObject类是所有使用元对象系统的类的基类,并不是所有Q开头的类都是Object的派生类，例如QString在一个类的private部分声明Q_OBJECT宏。MoC（元对象编译器）为每个QObject的子类提供必要的代码。

元对象编译器（Meta-Object Compiler，MOC）是一个预处理器，先将Qt的特性程序转换为标准C++程序，在由标准C++编译器进行编译。使用信号与槽机制，只有添加Q_OBJECT宏，moc才能对类里的信号与槽进行预处理,Qt为C++语言增加的特性在Qt Core模块里实现，由Qt的元对象系统实现。包括:信号与槽机制、属性系统、动态类型转换等。

Qt为C++语言增加的特性在Qt Core模块里实现，由Qt的元对象系统实现。包括:信号与槽机制、属性系统、动态类型转换等。元对象系统是一个C++扩展，使该语言更适合真正的组件化GUI编程。

![](https://s2.loli.net/2022/11/30/erUndDKbzo3pZXA.png)

Qobject不支持拷贝，拷贝构造函数和赋值运算符都是私有的，并且使用了Q_DISABLE_COPY()宏。
## 类库概述
### MainWindow简介
QMainWindow是 Qt 框架带来的一个预定义好的主窗口类。所谓主窗口，就是一个普通意义上的应用程序（不是指游戏之类的那种）最顶层的窗口。

![](https://s2.loli.net/2022/11/30/B5URFaEInJmHzYN.png)

主窗口的最上面是 Window Title，也就是标题栏，通常用于显示标题和控制按钮，比如最大化、最小化和关闭等。通常，各个图形界面框架都会使用操作系统本地代码来生成一个窗口。所以，你会看到在 KDE 上面，主窗口的标题栏是 KDE 样式的；在 Windows 平台上，标题栏是 Windows 风格的。如果你不喜欢本地样式，比如 QQ 这种，它其实是自己将标题栏绘制出来，这种技术称为 DirectUI，也就是无句柄绘制，这不在本文的讨论范畴。Window Title 下面是 Menu Bar，也就是菜单栏，用于**显示菜单**。窗口最底部是 Status Bar，称为**状态栏**。当我们鼠标滑过某些组件时，可以在状态栏显示某些信息，比如浏览器中，鼠标滑过带有链接的文字，你会在底部看到链接的实际 URL。除去上面说的三个横向的栏，中间是以矩形区域表示。我们可以看出，最外层称为 Tool Bar Area，用于**显示工具条区域**。之所以是矩形表示，是因为，Qt 的主窗口支持多个工具条。你可以将工具条拖放到不同的位置，因此这里说是 Area。我们可以把几个工具条并排显示在这里，就像 Word2003 一样，也可以将其分别放置，类似 Photoshop。在工具条区域内部是 Dock Widget Area，这是停靠窗口的显示区域。所谓停靠窗口，就像 Photoshop 的工具箱一样，可以停靠在主窗口的四周，也可以浮动显示。主窗口最中间称为 Central Widget，就是我们程序的工作区。通常我们会将程序最主要的工作区域放置在这里，类似 Word 的稿纸或者 Photoshop 的画布等等。



![image-20221201104910073](https://s2.loli.net/2022/12/01/rLkO7o5PVSKNts6.png)



### QAction（动作）

这个类就是代表了窗口的一个“动作”，这个动作可能显示在菜单，作为一个菜单项，当用户点击该菜单项，对用户的点击做出响应；也可能在工具栏，作为一个工具栏按钮，用户点击这个按钮就可以执行相应的操作。有一点值得注意：无论是出现在菜单栏还是工具栏，用户选择之后，所执行的动作应该都是一样的。因此，Qt 并没有专门的菜单项类，只是使用一个`QAction`类，抽象出公共的动作。当我们把`QAction`对象添加到菜单，就显示成一个菜单项，添加到工具栏，就显示成一个工具按钮。用户可以通过点击菜单项、点击工具栏按钮、点击快捷键来激活这个动作。`QAction`包含了图标、菜单文字、快捷键、状态栏文字、浮动帮助等信息。Qt 能够保证把`QAction`对象添加到不同的菜单、工具栏时，显示内容是同步的。也就是说，如果我们在菜单中修改了`QAction`的图标，那么在工具栏上面这个`QAction`所对应的按钮的图标也会同步修改。

## 事件与槽
所有GUI应用程序都是事件驱动的。事件主要由应用程序的用户生成，但也可以通过其他方式生成，例如Internet连接、窗口管理器或计时器。当调用exec方法时，应用程序进入主循环。主循环获取事件并将其发送到对象。

+ Qt具有独特的信号和插槽机制。这种信号和插槽机制是对C++编氇语言的扩展。
+ 信号和槽用于对象之间的通信。
+ slot是一种普通的C++函数;当与之相连的信号发出时，调用它。

### 基本概念
信号（Signal）就是在**特定情况下被发射的事件**，例如PushButton最常见的信号就是鼠标单击时发射的clicked()信号，一个ComboBox最常见的信号是选择的列表项变化时发射的CurrentIndexChanged()信号。GUI程序设计的主要内容就是对界面上各组件的信号的响应，只需要知道什么情况下发射哪些信号，合理地去响应和处理这些信号就可以了。

槽（Slot）就是**对信号响应的函数**。槽就是一个函数，与一般的C++函数是一样的，可以定义在类的任何部分（public、private或protected），可以具有任何参数，也可以被直接调用。槽函数与一般的函数不同的是：槽函数可以与一个信号关联，当信号被发射时，关联的槽函数被自动执行。


### 属性系统



## Model&View
+ 数据:如数据库的一个数据表或SQL查询结果，内存中的一个StringList，或磁盘文件结构等。
+ Model:与数据通信，并为视图组件提供数据接口。
+ View:是屏幕上的界面组件，视图从数据模型获得每个数据项的模型索引（ model index），通过模型索引获取数据
+ 代理:定制数据的界面显示和编辑方式。在标准的视图组件中，代理功能显示一个数据，当数据被编辑时，提供一个编辑器，一般是QLineEdit 。

### 资源文件

Qt  资源系统是一个跨平台的资源机制，用于将程序运行时所需要的资源以二进制的形式存储于可执行文件内部。如果你的程序需要加载特定的资源（图标、文本翻译等），那么，将其放置在资源文件中，就再也不需要担心这些文件的丢失。也就是说，**如果你将资源以资源文件形式存储，它是会编译到可执行文件内部**。

+ 别名：无需关注文件真实名
+ 语言：本地化机制
+ 前缀：相当于分类

```xml
<RCC>
    <qresource prefix="/images">
        <file alias="doc-open">document-open.png</file>
    </qresource>
    <qresource prefix="/images/fr" lang="fr">
        <file alias="doc-open">document-open-fr.png</file>
    </qresource>
</RCC>
```

可以使用`:/images/fr/doc-open`引用到 document-open-fr.png 这个文件。这个“语言”的作用是，如果 Qt 发现，本机的本地化信息是 fr 的话（`QLocale::system().name()`返回 fr_FR），则使用`:/images/fr/doc-open`这个图片；如果不是，则默认使用`:/images/doc-open`这个。

### 对象模型

`QObject`是以对象树的形式组织起来的。当你创建一个`QObject`对象时，会看到`QObject`的构造函数接收一个`QObject`指针作为参数，这个参数就是 parent，也就是父对象指针。这相当于，在创建`QObject`对象时，可以提供一个其父对象，我们创建的这个`QObject`对象会自动添加到其父对象的`children()`列表。当父对象析构的时候，这个列表中的所有对象也会被析构。（**注意，这里的父对象并不是继承意义上的父类！**）这种机制在 GUI 程序设计中相当有用。例如，一个按钮有一个`QShortcut`（快捷键）对象作为其子对象。当我们删除按钮的时候，这个快捷键理应被删除。这是合理的。

`QWidget`**是能够在屏幕上显示的一切组件的父类**。`QWidget`继承自`QObject`，因此也继承了这种对象树关系。一个孩子自动地成为父组件的一个子组件。因此，它会显示在父组件的坐标系统中，被父组件的边界剪裁。例如，当用户关闭一个对话框的时候，应用程序将其删除，那么，我们希望属于这个对话框的按钮、图标等应该一起被删除。事实就是如此，因为这些都是对话框的子组件。

Qt 引入对象树的概念，在一定程度上解决了内存问题。当一个`QObject`对象在堆上创建的时候，Qt 会同时为其创建一个对象树。**不过，对象树中对象的顺序是没有定义的。这意味着，销毁这些对象的顺序也是未定义的**。Qt 保证的是，任何对象树中的 `QObject`对象 delete 的时候，如果这个对象有 parent，则自动将其从 parent 的`children()`列表中删除；如果有孩子，则自动 delete 每一个孩子。Qt 保证没有`QObject`会被 delete 两次，这是由析构顺序决定的。

### 布局管理器

Qt 提供了两种组件定位机制：绝对定位和布局定位。

顾名思义，绝对定位就是一种最原始的定位方法：给出这个组件的坐标和长宽值。这样，Qt  就知道该把组件放在哪里以及如何设置组件的大小。但是这样做带来的一个问题是，如果用户改变了窗口大小，比如点击最大化按钮或者使用鼠标拖动窗口边缘，**采用绝对定位的组件是不会有任何响应的**。这也很自然，因为你并没有告诉 Qt，在窗口变化时，组件是否要更新自己以及如何更新。如果你需要让组件自动更新——这是很常见的需求，比如在最大化时，Word  总会把稿纸区放大，把工具栏拉长——就要自己编写相应的函数来响应这些变化。或者，还有更简单的方法：禁止用户改变窗口大小。但这总不是长远之计。针对这种变化的需求，Qt 提供了另外的一种机制——布局——来解决这个问题。**你只要把组件放入某一种布局，布局由专门的布局管理器进行管理。当需要调整大小或者位置的时候，Qt 使用对应的布局管理器进行调整**。

Qt 提供了几种布局管理器供我们选择：

- `QHBoxLayout`：按照水平方向从左到右布局；
- `QVBoxLayout`：按照竖直方向从上到下布局；
- `QGridLayout`：在一个网格中进行布局，类似于 HTML 的 table；
- `QFormLayout`：按照表格布局，每一行前面是一段文本，文本后面跟随一个组件（通常是输入框），类似 HTML 的 form；
- `QStackedLayout`：层叠的布局，允许我们将几个组件按照 Z 轴方向堆叠，可以形成向导那种一页一页的效果。

### 菜单栏、工具栏和状态栏

工具栏可以设置成固定的、浮动的等等，具体设置可以参考 Qt 文档。

## 对话框

对 话框是 GUI 程序中不可或缺的组成部分。很多不能或者不适合放入主窗口的功能组件都必须放在对话框中设置。对话框通常会是一个顶层窗口，出现在程序最上层，用于实现短期任务或者简洁的用户交互。`QDialog`（及其子类，以及所有`Qt::Dialog`类型的类）的对于其 parent 指针都有额外的解释：如果 parent 为 NULL，则该对话框会作为一个顶层窗口，否则则作为其父组件的子对话框（此时，其默认出现的位置是 parent 的中心）。顶层窗口与非顶层窗口的区别在于，**顶层窗口在任务栏会有自己的位置，而非顶层窗口则会共享其父组件的位置**。

**对话框分为模态对话框和非模态对话框**。所谓模态对话框，就是会阻塞同一应用程序中其它窗口的输入。模态对话框很常见，比如“打开文件”功能。你可以尝试一下记事本的打开文件，当打开文件对话框出现时，我们是不能对除此对话框之外的窗口部分进行操作的。与此相反的是非模态对话框，例如查找对话框，我们可以在显示着查找对话框的同时，继续对记事本的内容进行编辑。

Qt 支持模态对话框和非模态对话框。其中，Qt  有两种级别的模态对话框：应用程序级别的模态和窗口级别的模态，默认是应用程序级别的模态。应用程序级别的模态是指，当该种模态的对话框出现时，用户必须首先对对话框进行交互，直到关闭对话框，然后才能访问程序中其他的窗口。窗口级别的模态是指，该模态仅仅阻塞与对话框关联的窗口，但是依然允许用户与程序中其它窗口交互。窗口级别的模态尤其适用于多窗口模式。**Qt 使用`QDialog::exec()`实现应用程序级别的模态对话框，使用`QDialog::open()`实现窗口级别的模态对话框，使用`QDialog::show()`实现非模态对话框**。

### 对话框数据传递

## 文件

简要说明如下：

- `QIODevice`：所有 I/O 设备类的父类，提供了字节块读写的通用操作以及基本接口；
- `QFlie`：访问本地文件或者嵌入资源；
- `QTemporaryFile`：创建和访问本地文件系统的临时文件；
- `QBuffer`：读写`QByteArray`；
- `QProcess`：运行外部程序，处理进程间通讯；
- `QAbstractSocket`：所有套接字类的父类；
- `QTcpSocket：TCP`协议网络数据传输；
- `QUdpSocket`：传输 UDP 报文；
- `QSslSocket`：使用 SSL/TLS 传输数据；
- `QFileDevice：Qt5`新增加的类，提供了有关文件操作的通用实现。

这其中，`QProcess`、`QTcpSocket`、`QUdpSoctet`和`QSslSocket`是顺序访问设备。所谓“顺序访问”，是指它们的数据只能访问一遍：从头走到尾，从第一个字节开始访问，直到最后一个字节，中途不能返回去读取上一个字节；`QFile`、`QTemporaryFile`和`QBuffer`是随机访问设备，可以访问任意位置任意次数，还可以使用`QIODevice::seek()`函数来重新定位文件访问位置指针。

`QFile`主要提供了有关文件的各种操作，比如打开文件、关闭文件、刷新文件等。我们可以使用`QDataStream`或`QTextStream`类来读写文件，也可以使用`QIODevice`类提供的`read()`、`readLine()`、`readAll()`以及`write()`这样的函数。值得注意的是，有关文件本身的信息，比如文件名、文件所在目录的名字等，则是通过`QFileInfo`获取，而不是自己分析文件路径字符串。

### 二进制文件

二进制文件比较小巧，却不是人可读的格式。而文本文件是一种人可读的文件。为了操作这种文件，我们需要使用`QTextStream`类。`QTextStream`和`QDataStream`的使用类似，只不过它是操作纯文本文件的。另外，像 XML、HTML 这种，虽然也是文本文件，可以由`QTextStream`生成，但 Qt 提供了更方便的 XML 操作类，这里就不包括这部分内容了。

`QTextStream`会自动将 Unicode 编码同操作系统的编码进行转换，这一操作对开发人员是透明的。它也会将换行符进行转换，同样不需要自己处理。`QTextStream`使用 16 位的`QChar`作为基础的数据存储单位，同样，它也支持 C++ 标准类型，如 int 等。实际上，这是将这种标准类型与字符串进行了相互转换。

## 容器

存储容器（containers）有时候也被称为集合（collections），**是能够在内存中存储其它特定类型的对象，通常是一些常用的数据结构，一般是通用模板类的形式**。C++ 提供了一套完整的解决方案，作为标准模板库（Standard Template Library）的组成部分，也就是常说的 STL。Qt 提供了另外一套基于模板的容器类。相比 STL，这些容器类通常更轻量、更安全、更容易使用。如果你对 STL 不大熟悉，或者更喜欢 Qt 风格的 API，那么你就应该选择使用这些类。当然，你也可以在 Qt 中使用 STL 容器，没有任何问题。

Qt 的容器类都不继承`QObject`，都提供了隐式数据共享、不可变的特性，并且为速度做了优化，具有较低的内存占用量等。另外一点比较重要的，它们是**线程安全**的。这些容器类是平台无关的，即不因编译器的不同而具有不同的实现；隐式数据共享，有时也被称作“写时复制（copy on write）”，这种技术允许在容器类中使用传值参数，但却不会出现额外的性能损失。遍历是容器类的重要操作。Qt 容器类提供了类似 Java 的遍历器语法，同样也提供了类似 STL 的遍历器语法，以方便用户选择自己习惯的编码方式。相比而言，Java  风格的遍历器更易用，是一种高层次的函数；而 STL 风格的遍历器更高效，同时能够支持 Qt 和 STL  的通用算法。最后一点，在一些嵌入式平台，STL 往往是不可用的，这时你就只能使用 Qt  提供的容器类，除非你想自己创建。顺便提一句，除了遍历器，Qt 还提供了自己的 foreach 语法

Qt 提供了顺序存储容器：`QList`，`QLinkedList`，`QVector`，`QStack`和`QQueue`。对于绝大多数应用程序，`QList`是最好的选择。虽然它是基于数组实现的列表，但它提供了快速的向前添加和向后追加的操作。如果你需要链表，可以使用`QLinkedList`。如果你希望所有元素占用连续地址空间，可以选择`QVector`。`QStack`和`QQueue`则是 LIFO 和 FIFO 的。

Qt 还提供了关联容器：`QMap`，`QMultiMap`，`QHash`，`QMultiHash`和`QSet`。带有“Multi”字样的容器支持在一个键上面关联多个值。“Hash”容器提供了基于散列函数的更快的查找，而非 Hash 容器则是基于二分搜索的有序集合。

能够存储在容器中的数据必须是**可赋值数据类型**。所谓可赋值数据类型，是指**具有默认构造函数、拷贝构造函数和赋值运算符的类型**。绝大多数数据类型，包括基本类型，比如 int 和 double，指针，Qt 数据类型，例如`QString`、`QDate`和`QTime`，都是可赋值数据类型。但是，`QObject`及其子类（`QWidget`、`QTimer`等）都不是。也就是说，你不能使用`QList<QWidget>`这种容器，因为`QWidget`的拷贝构造函数和赋值运算符不可用。如果你需要这种类型的容器，只能存储其指针，也就是`QList<QWidget *>`。

### 遍历容器

每一种容器都有两种 Java 风格的遍历器：一种提供只读访问，一种提供读写访问：

| 容器                                 | 只读遍历器               | 读写遍历器                      |
| ------------------------------------ | ------------------------ | ------------------------------- |
| `QList<T>`,`QQueue<T>`               | `QListIterator<T>`       | `QMutableListIterator<T>`       |
| `QLinkedList<T>`                     | `QLinkedListIterator<T>` | `QMutableLinkedListIterator<T>` |
| `QVector<T>`,`QStack<T>`             | `QVectorIterator<T>`     | `QMutableVectorIterator<T>`     |
| `QSet<T>`                            | `QSetIterator<T>`        | `QMutableSetIterator<T>`        |
| `QMap<Key, T>`,`QMultiMap<Key, T>`   | `QMapIterator<T>`        | `QMutableMapIterator<T>`        |
| `QHash<Key, T>`,`QMultiHash<Key, T>` | `QHashIterator<T>`       | `QMutableHashIterator<T>`       |

### 使用拖拽

拖放（Drag and Drop），通常会简称为 DnD，是现代软件开发中必不可少的一项技术。它提供了一种能够在应用程序内部甚至是应用程序之间进行信息交换的机制。操作系统与应用程序之间进行的剪贴板内容的交换，也可以被认为是拖放的一部分。**拖放其实是由两部分组成的：拖动和释放**。拖动是将被拖放对象进行移动，释放是将被拖放对象放下。前者是一个按下鼠标按键并移动的过程，后者是一个松开鼠标按键的过程；通常这两个操作之间的鼠标按键是被一直按下的。当然，这只是一种普遍的情况，其它情况还是要看应用程序的具体实现。对于 Qt 而言，一个组件既可以作为被拖动对象进行拖动，也可以作为释放掉的目的地对象，或者二者都是。

## 参考

1. [Qt 学习之路 2](https://www.bookstack.cn/read/qt-study-road-2/ddf84b4ac149953f.md)
2. [Qt 5 基础教程](https://www.bookstack.cn/read/qter-qt5-basic/554e1debc728bf9c.md)
3. [Qt教程，Qt5编程入门教程](http://c.biancheng.net/qt/)
4. [QT docs](https://doc.qt.io/)
5. [阿西拜-南昌|BiliBili](https://space.bilibili.com/412587130)
6. [Qt 5.9 C++开发指南|`王维波，栗宝鹃，侯春望`](https://weread.qq.com/web/reader/53d42262a43425f444a67387a4938767741546936634536636426ekc4c329b011c4ca4238a0201)
7. [Python Qt GUI与数据可视化编程|`王维波，栗宝娟，张晓东`](https://weread.qq.com/web/reader/6393267071ccfa97639f573kc81322c012c81e728d9d180)
8. [Python Qt |白月黑羽](https://www.byhy.net/tut/py/gui/qt_01/)