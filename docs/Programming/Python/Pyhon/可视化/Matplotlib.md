# Matplotlib
## 简介
Matplotlib 是一款用于数据可视化的 Python 软件包，支持跨平台运行，它能够根据 NumPy  ndarray 数组来绘制 2D 图像。Matplotlib 提供了一个套面向绘图对象编程的 API 接口，能够很轻松地实现各种图像的绘制，并且它可以配合 Python GUI 工具（如 PyQt、Tkinter 等）在应用程序中嵌入图形。
### 架构

![](https://s2.loli.net/2022/11/24/nOPHg31RAifvGe6.png)

1) 脚本层
脚本层是 Matplotlib 结构中的最顶层。我们编写的绘图代码大部分代码都在该层运行，它的主要工作是负责生成图形与坐标系。
2) 美工层
美工层是结构中的第二层，它提供了绘制图形的元素时的给各种功能，例如，绘制标题、轴标签、坐标刻度等。
3) 后端层
后端层是 Matplotlib 最底层，它定义了三个基本类，首先是 FigureCanvas（图层画布类），它提供了绘图所需的画布，其次是 Renderer（绘图操作类），它提供了在画布上进行绘图的各种方法，最后是 Event（事件处理类），它提供了用来处理鼠标和键盘事件的方法。

### Matplotlib图形组成
Matplotlib 生成的图形主要由以下几个部分构成：

![](https://s2.loli.net/2022/11/24/DSpPTi7b5asvmjF.png)

- Figure：指整个图形，您可以把它理解成一张画布，它包括了所有的元素，比如标题、轴线等；
- Axes：绘制 2D 图像的实际区域，也称为轴域区，或者绘图区；
- Axis：指坐标系中的垂直轴与水平轴，包含轴的长度大小（图中轴长为 7）、轴标签（指 x 轴，y轴）和刻度标签；
- Artist：您在画布上看到的所有元素都属于 Artist 对象，比如文本对象（title、xlabel、ylabel）、Line2D 对象（用于绘制2D图像）等。

### Matplotlib功能扩展包

许多第三方工具包都对 Matplotlib 进行了功能扩展，其中有些安装包需要单独安装，也有一些允许与 Matplotlib 一起安装。常见的工具包如下：

- Basemap：这是一个地图绘制工具包，其中包含多个地图投影，海岸线和国界线；
- Cartopy：这是一个映射库，包含面向对象的映射投影定义，以及任意点、线、面的图像转换能力；
- Excel tools： 这是 Matplotlib 为了实现与 Microsoft Excel 交换数据而提供的工具；
- Mplot3d：它用于 3D 绘图；
- Natgrid：这是 Natgrid 库的接口，用于对间隔数据进行不规则的网格化处理。

## 快速入门
pip安装
```
 pip install matplotlib
```
### pyplot
Matplotlib 中的 pyplot 模块是一个类似命令风格的函数集合，这使得 Matplotlib 的工作模式和 MATLAB 相似。

#### 绘图类型

| 函数名称  | 描述                                       |
| --------- | ------------------------------------------ |
| Bar       | 绘制条形图                                 |
| Barh      | 绘制水平条形图                             |
| Boxplot   | 绘制箱型图                                 |
| Hist      | 绘制直方图                                 |
| his2d     | 绘制2D直方图                               |
| Pie       | 绘制饼状图                                 |
| Plot      | 在坐标轴上画线或者标记                     |
| Polar     | 绘制极坐标图                               |
| Scatter   | 绘制x与y的散点图                           |
| Stackplot | 绘制堆叠图                                 |
| Stem      | 用来绘制二维离散数据绘制（又称为“火柴图”） |
| Step      | 绘制阶梯图                                 |
| Quiver    | 绘制一个二维按箭头                         |

#### Image函数

| 函数名称 | 描述                               |
| -------- | ---------------------------------- |
| Imread   | 从文件中读取图像的数据并形成数组。 |
| Imsave   | 将数组另存为图像文件。             |
| Imshow   | 在数轴区域内显示图像。             |

#### Axis函数

| 函数名称 | 描述                          |
| -------- | ----------------------------- |
| Axes     | 在画布(Figure)中添加轴        |
| Text     | 向轴添加文本                  |
| Title    | 设置当前轴的标题              |
| Xlabel   | 设置x轴标签                   |
| Xlim     | 获取或者设置x轴区间大小       |
| Xscale   | 设置x轴缩放比例               |
| Xticks   | 获取或设置x轴刻标和相应标签   |
| Ylabel   | 设置y轴的标签                 |
| Ylim     | 获取或设置y轴的区间大小       |
| Yscale   | 设置y轴的缩放比例             |
| Yticks   | 获取或设置y轴的刻标和相应标签 |

#### Figure函数

| 函数名称 | 描述             |
| -------- | ---------------- |
| Figtext  | 在画布上添加文本 |
| Figure   | 创建一个新画布   |
| Show     | 显示数字         |
| Savefig  | 保存当前画布     |
| Close    | 关闭画布窗口     |
### PyLab
PyLab 是一个面向 Matplotlib 的绘图库接口，其语法和 MATLAB 十分相近。它和 Pyplot 模快都够实现 Matplotlib 的绘图功能。PyLab 是一个单独的模块，随 Matplotlib 软件包一起安装。