---
hide:
  - tags
tags:
  - WPF
  - GUI
  - Csharp
---
## 初始WPF
wpf是微软推出的一项基于windows操作系统、.net平台的c/s客户端构建技术（比如腾讯QQ这种软件就是客户端）。最大的特征就是可以快速构建项目从而达到节约项目成本的目的。在众多中小型企业比较受欢迎。
## XAML布局
1. 布局控件：可以理解为容器，可以嵌套N层。
2. 常用布局空间: Grid,StackPanel,WrapPanel,Canvas(不常用)

Gird ：可以理解为一个表格，类似于HTML中的Table标签。它是由行和列组成。

StackPanel：是一个可以将自身内容横向或纵向排列的容器。

WrapPanel：控件自动的在一行里，如果需要换行则规定好WrapPanel的布局控件的宽度，如果布局内容超出了这个宽度则会自动换行。

Canvas:  它比较特殊。它属于“任意布局”的一种概念，就是你拖控件到UI上的时候你把它放在哪里它就在那里了。

## 控件、依赖项属性

### 控件

在 WPF 中， 控件 是一个涵盖性术语，适用于在窗口中可视化、可交互、具有用户界面并实现某些行为，设计好的控件能给用户带来更好的交互体验。

控件的基础属性宽、高、背景色、字体颜色、字体大小、禁用、启用、显示、隐藏等、控件显示的值内容有的叫Content、Text、Value等这一些东西基本上不会随着wpf的版本迭代有面目全非的变化所以是可以通过长期使用慢慢积累到控件属性。从而掌握它们的使用方式或重写、编写自定义控件。（**工具箱里面有常用控件**）

### 内置控件

- **按钮**：[Button](https://msdn.microsoft.com/zh-cn/library/ms609089(v=vs.100)) 和 [RepeatButton](https://msdn.microsoft.com/zh-cn/library/ms595189(v=vs.100))。
- **数据显示**：[DataGrid](https://msdn.microsoft.com/zh-cn/library/cc189753(v=vs.100))、[ListView](https://msdn.microsoft.com/zh-cn/library/ms611074(v=vs.100)) 和 [TreeView](https://msdn.microsoft.com/zh-cn/library/ms595700(v=vs.100))。
- **日期显示和选择**：[Calendar](https://msdn.microsoft.com/zh-cn/library/cc189757(v=vs.100)) 和 [DatePicker](https://msdn.microsoft.com/zh-cn/library/cc189204(v=vs.100))。
- **对话框**：[OpenFileDialog](https://msdn.microsoft.com/zh-cn/library/ms653561(v=vs.100))、[PrintDialog](https://msdn.microsoft.com/zh-cn/library/ms612630(v=vs.100)) 和 [SaveFileDialog](https://msdn.microsoft.com/zh-cn/library/ms653573(v=vs.100))。
- **数字墨迹**：[InkCanvas](https://msdn.microsoft.com/zh-cn/library/ms610988(v=vs.100)) 和 [InkPresenter](https://msdn.microsoft.com/zh-cn/library/ms611029(v=vs.100))。
- **文档**：[DocumentViewer](https://msdn.microsoft.com/zh-cn/library/ms609859(v=vs.100))、[FlowDocumentPageViewer](https://msdn.microsoft.com/zh-cn/library/ms610525(v=vs.100))、[FlowDocumentReader](https://msdn.microsoft.com/zh-cn/library/ms610531(v=vs.100))、[FlowDocumentScrollViewer](https://msdn.microsoft.com/zh-cn/library/ms610538(v=vs.100)) 和 [StickyNoteControl](https://msdn.microsoft.com/zh-cn/library/ms612977(v=vs.100))。
- **输入**：[TextBox](https://msdn.microsoft.com/zh-cn/library/ms617604(v=vs.100))、[RichTextBox](https://msdn.microsoft.com/zh-cn/library/ms612650(v=vs.100)) 和 [PasswordBox](https://msdn.microsoft.com/zh-cn/library/ms611638(v=vs.100))。
- **布局**：[Border](https://msdn.microsoft.com/zh-cn/library/ms609067(v=vs.100))、[BulletDecorator](https://msdn.microsoft.com/zh-cn/library/ms611645(v=vs.100))、[Canvas](https://msdn.microsoft.com/zh-cn/library/ms609101(v=vs.100))、[DockPanel](https://msdn.microsoft.com/zh-cn/library/ms609853(v=vs.100))、[Expander](https://msdn.microsoft.com/zh-cn/library/ms609881(v=vs.100))、[Grid](https://msdn.microsoft.com/zh-cn/library/ms610550(v=vs.100))、[GridView](https://msdn.microsoft.com/zh-cn/library/ms610560(v=vs.100))、[GridSplitter](https://msdn.microsoft.com/zh-cn/library/ms610553(v=vs.100))、[GroupBox](https://msdn.microsoft.com/zh-cn/library/ms616554(v=vs.100))、[Panel](https://msdn.microsoft.com/zh-cn/library/ms611631(v=vs.100))、[ResizeGrip](https://msdn.microsoft.com/zh-cn/library/ms595197(v=vs.100))、[Separator](https://msdn.microsoft.com/zh-cn/library/ms612946(v=vs.100))、[ScrollBar](https://msdn.microsoft.com/zh-cn/library/ms595205(v=vs.100))、[ScrollViewer](https://msdn.microsoft.com/zh-cn/library/ms612678(v=vs.100))、[StackPanel](https://msdn.microsoft.com/zh-cn/library/ms612971(v=vs.100))、[Thumb](https://msdn.microsoft.com/zh-cn/library/ms612587(v=vs.100))、[Viewbox](https://msdn.microsoft.com/zh-cn/library/ms617883(v=vs.100))、[VirtualizingStackPanel](https://msdn.microsoft.com/zh-cn/library/ms617901(v=vs.100))、[Window](https://msdn.microsoft.com/zh-cn/library/ms590112(v=vs.100)) 和 [WrapPanel](https://msdn.microsoft.com/zh-cn/library/ms617907(v=vs.100))。
- **媒体**：[Image](https://msdn.microsoft.com/zh-cn/library/ms610982(v=vs.100))、[MediaElement](https://msdn.microsoft.com/zh-cn/library/ms611595(v=vs.100)) 和 [SoundPlayerAction](https://msdn.microsoft.com/zh-cn/library/ms612957(v=vs.100))。
- **菜单**：[ContextMenu](https://msdn.microsoft.com/zh-cn/library/ms609810(v=vs.100))、[Menu](https://msdn.microsoft.com/zh-cn/library/ms611602(v=vs.100)) 和 [ToolBar](https://msdn.microsoft.com/zh-cn/library/ms617622(v=vs.100))。
- **导航**：[Frame](https://msdn.microsoft.com/zh-cn/library/ms610544(v=vs.100))、[Hyperlink](https://msdn.microsoft.com/zh-cn/library/ms601132(v=vs.100))、[Page](https://msdn.microsoft.com/zh-cn/library/ms611620(v=vs.100))、[NavigationWindow](https://msdn.microsoft.com/zh-cn/library/ms615518(v=vs.100)) 和 [TabControl](https://msdn.microsoft.com/zh-cn/library/ms612994(v=vs.100))。
- **选择**：[CheckBox](https://msdn.microsoft.com/zh-cn/library/ms609112(v=vs.100))、[ComboBox](https://msdn.microsoft.com/zh-cn/library/ms609785(v=vs.100))、[ListBox](https://msdn.microsoft.com/zh-cn/library/ms611062(v=vs.100))、[RadioButton](https://msdn.microsoft.com/zh-cn/library/ms612644(v=vs.100)) 和 [Slider](https://msdn.microsoft.com/zh-cn/library/ms612951(v=vs.100))。
- **用户信息**：[AccessText](https://msdn.microsoft.com/zh-cn/library/ms609043(v=vs.100))、[Label](https://msdn.microsoft.com/zh-cn/library/ms611056(v=vs.100))、[Popup](https://msdn.microsoft.com/zh-cn/library/ms612207(v=vs.100))、[ProgressBar](https://msdn.microsoft.com/zh-cn/library/ms612638(v=vs.100))、[StatusBar](https://msdn.microsoft.com/zh-cn/library/ms595241(v=vs.100))、[TextBlock](https://msdn.microsoft.com/zh-cn/library/ms617591(v=vs.100)) 和 [ToolTip](https://msdn.microsoft.com/zh-cn/library/ms617634(v=vs.100))。

### 依赖属性

依赖属性在wpf主要扮演数据驱动中的重要角色，它能配合绑定一起实时数据更新UI显示、动画、自定义控件等。

1. DependencyProperty依赖属性，它能配合绑定一起实时数据更新UI显示、动画帧数、自定义控件等。
2. 普通属性也能实现实时数据更新，但是需要额外实现一套通知机制叫做INotifyPropertyChanged。不支持其他操作。

## 绑定

绑定顾名思义，是将我们获取到的数据和UI上的控件绑定起来利用数据的变化来更新界面所看到的内容。那如何实现绑定呢？

1.绑定目标 2.绑定属性 3.绑定模式 4.绑定数据源 5.关联资源

### 1 绑定目标

绑定目标很好理解，其实就是你要操作绑定的控件。例如：Button，TextBox。

### 2 绑定属性（依赖项属性）

`<TextBox Width="200" Height="25" Text="{Bingding Name}"></TextBox>`

绑定语法介绍：

如上代码块中，Text就是绑定属性了， **Bingding** 是绑定关键字，而后面的Name就是你要绑定的数据源的变量名。 (逗号分隔，mode设置模式默认twoway)

### 3 绑定模式

+ TwoWay 无论是目标属性还是源属性，只要发生了更改，TwoWay 就会更新目标属性或源属性。
+ OneWay 仅当源属性发生更改时更新目标属性。
+ OneTime 仅当应用程序启动时或 DataContext 进行更改时更新目标属性。
+ OneWayToSource 在目标属性更改时更新源属性。
+ Default：模式根据实际情况来定，如果是可编辑的就是TwoWay,只读的就是OneWay。

### 4 绑定数据源

一般来说可以是单个变量（int , double,string）、也可以是一个数据集（List）。根据需求和场景去定义。

### 5 关联资源

在每一个窗体中，都有一个DataContext ，它是一个object类型主要用来存储绑定资源。

### 绑定和窗体xaml.cs操作的区别在哪里？

区别在于，窗体后台文件直接访问控件的操作是事件驱动。比如说我上一个视频讲到的button的click事件，如果没有事件的存在是改变不了界面的。绑定操作，是以数据本身的变化来通知界面显示改变的。UI代码和逻辑代码实现前后端分离。

## 命令

命令有许多可变的部分组成，但它们都具有以下4个重要元素：

命令：命令表示应用程序任务，并且跟踪任务是否能够被执行。然而，命令实际上不包含执行应用程序任务的代码。

命令绑定：每个命令绑定针对用户界面的具体元素，将命令连接到相关的应用程序逻辑。这种分解的设计是非常重要的，因为单个命令可用于应用程序中的多个地方，并且在每个地方具有不同的意义。为处理这一问题，需要将同一命令与不同的命令绑定。

命令源：命令源触发命令。例如，button就是命令源。单击它们都会执行绑定命令。

命令目标：命令目标是在其中执行命令的元素。

ICommandSource接口定义了三个属性:

+ Command : 指向连接的命令，这是唯一必须的细节。
+ CommandParameter: 提供其他希望随命令发送的数据
+ CommandTarget: 确定将在其中执行命令的元素。

## MVVM模式

MVVM是一种开发模式，是一种开发标准。在WPF中应用到MVVM是非常常见的，MVVM全称为Model、View、ViewModel。

View:代表窗体、控件等可视化资源。

ViewModel:代表View的业务处理类，将获取到的数据处理好与View进行关联绑定。

Model：通常代表数据模型，它将支持ViewModel中所使用的到的。还有一种用法就是在Model里完成业务逻辑的编写ViewModel只需要写出关联逻辑代码，具体的使用方式视情况而定。毕竟MVVM只是一个规范我们尽量遵守即可。

优点：前后端逻辑分离，解耦，代码配置灵活，易维护，为数据驱动奠定基础。

缺点：开发耗时较长，对于新手掌握起来略微有难度。基于MVVM再实现绑定难度会有一个小幅度的提升。需多实践积累经验即可。

1.注意文件夹、文件的命名，每个文件的摆放都是有讲究的切勿乱放。

2.ViewModel可以聚合N个Model，ViewModel可以对应多个View。

3.MainWindow稍微特殊点，因为它是主窗体作为整个程序的起始点，它放文件的话可放可不放。

App.xaml是程序启动配置文件，如果需要更换起始运行窗体则需要修改StartupUri=“xxxView.xaml”即可。

## 资源、样式

WPF资源系统是一种保管一系列有用对象（如常用的画刷、样式和模板）的简单方法，从而使您可以更容易地重用这些对象。每个元素都有Resources属性，该属性存储了一个资源字典集合（它是ResourceDictionary类的实例）。资源集合可包含任意类型的对象，根据字符串编写索引。

### 样式

样式是修改View（窗体、控件）样式的主要手段，主要作用更改控件的外观以及增强用户体验。

Style类的属性：

Setterts：设置属性值以及自动关联事件处理程序的Setter对象或EventSetter对象的集合是Style类中最重要的属性，但并非唯一属性。

Triggers: 继承自TriggerBase类能自动改变样式设置的对象集合。例如，当另一个属性改变时，或者当发生某个时间时，可以修改样式。

Resources: 希望用于样式的资源集合。

BasedOn：通过该属性可创建继承自其它样式设置的更具体的样式。

TargetType：该属性标识应用样式的元素类型。通过该属性可创建只影响特定类型元素的设置器，还可以创建能够为恰当的元素类型自动起作用的设置器。

DynamicResource与StaticResource的区别：静态资源在第一次编译后即确定其对象或值，之后不能对其进行修改。动态资源则是在运行时决定，当运行过程中真正需要时，才到资源目标中查找其值。

## Convert

Convert可以将源数据和目标数据之间进行特定的转化。定义转换器，需要继承接口IValueConverter。Convert：会进行源属性传给目标属性的特定转化
ConvertBack：会进行目标属性传给源属性的特定转化

## 模板

模板应用在View层，它的主要作用是修改控件的样式、交互、数据展示。

模板主要分为，DataTemplate 和 ControlTemplate。

+ ControlTemplate它决定了控件“长成什么样子”，并让开发者有机会在控件原有的内部逻辑基础上扩展自己的逻辑。
+ DataTemplate是数据内容的展示方式，一条数据显示成什么样子，是简单的文本还是直观的图形就由它来决定了。

## 线程

### 前台后台

前台线程和后台线程。前台线程在没有执行完成函数代码时，在程序关闭时是不会退出进程的。后台线程不管有没有执行完成函数代码，都会直接退出进程。

### 主线程和子线程

主线程（UI线程）：在c/s应用程序中指的是拥有界面逻辑处理能力的线程，通常界面上的更新都由它专门来负责处理。界面上的数据变化（数据的增删改查）、控件变化（删除控件）、（模板，样式里包含的）事件触发等。

子线程：协助主线程进行工作的线程称为子线程，例如Thread或Task创建的线程。
