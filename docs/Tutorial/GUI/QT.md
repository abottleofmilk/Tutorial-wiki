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

主窗口的最上面是 Window Title，也就是标题栏，通常用于显示标题和控制按钮，比如最大化、最小化和关闭等。通常，各个图形界面框架都会使用操作系统本地代码来生成一个窗口。所以，你会看到在 KDE 上面，主窗口的标题栏是 KDE 样式的；在 Windows 平台上，标题栏是 Windows 风格的。如果你不喜欢本地样式，比如 QQ 这种，它其实是自己将标题栏绘制出来，这种技术称为 DirectUI，也就是无句柄绘制，这不在本文的讨论范畴。Window Title 下面是 Menu Bar，也就是菜单栏，用于显示菜单。窗口最底部是 Status Bar，称为状态栏。当我们鼠标滑过某些组件时，可以在状态栏显示某些信息，比如浏览器中，鼠标滑过带有链接的文字，你会在底部看到链接的实际 URL。除去上面说的三个横向的栏，中间是以矩形区域表示。我们可以看出，最外层称为 Tool Bar Area，用于显示工具条区域。之所以是矩形表示，是因为，Qt 的主窗口支持多个工具条。你可以将工具条拖放到不同的位置，因此这里说是 Area。我们可以把几个工具条并排显示在这里，就像 Word2003 一样，也可以将其分别放置，类似 Photoshop。在工具条区域内部是 Dock Widget Area，这是停靠窗口的显示区域。所谓停靠窗口，就像 Photoshop 的工具箱一样，可以停靠在主窗口的四周，也可以浮动显示。主窗口最中间称为 Central Widget，就是我们程序的工作区。通常我们会将程序最主要的工作区域放置在这里，类似 Word 的稿纸或者 Photoshop 的画布等等。
### QAction
## 事件与槽
所有GUI应用程序都是事件驱动的。事件主要由应用程序的用户生成，但也可以通过其他方式生成，例如Internet连接、窗口管理器或计时器。当调用exec方法时，应用程序进入主循环。主循环获取事件并将其发送到对象。

+ Qt具有独特的信号和插槽机制。这种信号和插槽机制是对C++编氇语言的扩展。
+ 信号和槽用于对象之间的通信。
+ slot是一种普通的C++函数;当与之相连的信号发出时，调用它。

### 基本概念
信号（Signal）就是在**特定情况下被发射的事件**，例如PushButton最常见的信号就是鼠标单击时发射的clicked()信号，一个ComboBox最常见的信号是选择的列表项变化时发射的CurrentIndexChanged()信号。GUI程序设计的主要内容就是对界面上各组件的信号的响应，只需要知道什么情况下发射哪些信号，合理地去响应和处理这些信号就可以了。

槽（Slot）就是**对信号响应的函数**。槽就是一个函数，与一般的C++函数是一样的，可以定义在类的任何部分（public、private或protected），可以具有任何参数，也可以被直接调用。槽函数与一般的函数不同的是：槽函数可以与一个信号关联，当信号被发射时，关联的槽函数被自动执行。


### 属性系统

### 容器

## Model&View
+ 数据:如数据库的一个数据表或SQL查询结果，内存中的一个StringList，或磁盘文件结构等。
+ Model:与数据通信，并为视图组件提供数据接口。
+ View:是屏幕上的界面组件，视图从数据模型获得每个数据项的模型索引（ model index），通过模型索引获取数据
+ 代理:定制数据的界面显示和编辑方式。在标准的视图组件中，代理功能显示一个数据，当数据被编辑时，提供一个编辑器，一般是QLineEdit 。

## 参考
1. [Qt 学习之路 2](https://www.bookstack.cn/read/qt-study-road-2/ddf84b4ac149953f.md)
2. [Qt 5 基础教程](https://www.bookstack.cn/read/qter-qt5-basic/554e1debc728bf9c.md)
3. [Qt教程，Qt5编程入门教程](http://c.biancheng.net/qt/)
4. [QT docs](https://doc.qt.io/)
5. [阿西拜-南昌|BiliBili](https://space.bilibili.com/412587130)
6. [Qt 5.9 C++开发指南|`王维波，栗宝鹃，侯春望`](https://weread.qq.com/web/reader/53d42262a43425f444a67387a4938767741546936634536636426ekc4c329b011c4ca4238a0201)
7. [Python Qt GUI与数据可视化编程|`王维波，栗宝娟，张晓东`](https://weread.qq.com/web/reader/6393267071ccfa97639f573kc81322c012c81e728d9d180)