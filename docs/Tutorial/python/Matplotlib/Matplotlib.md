## 介绍

### 快速指南

![image-20221129150554489](https://s2.loli.net/2022/11/29/NbIChzKBqEpQlHx.png)

#### 图的组件

##### [`Figure`](https://matplotlib.org/stable/api/figure_api.html#matplotlib.figure.Figure)

指整个画面（可以包含多个坐标系）

创建新图形的最简单方法是使用 pyplot：

```python
fig = plt.figure()  # an empty figure with no Axes
fig, ax = plt.subplots()  # a figure with a single Axes
fig, axs = plt.subplots(2, 2)  # a figure with a 2x2 grid of Axes
facecolor #背景，edgecolor #边缘背景
```

与图形一起创建轴通常很方便，但您也可以稍后手动添加轴。请注意，许多 [Matplotlib 后端](https://matplotlib.org/stable/users/explain/backends.html)支持在图形窗口上缩放和平移。

##### [`Axes`](https://matplotlib.org/stable/api/axes_api.html#matplotlib.axes.Axes)

指坐标系

Axes 是附加到 Figure 的 Artist，它包含一个用于绘制数据的区域，通常包括两个（或三个在 3D 情况下 ）提供刻度和刻度标签的对象（注意**Axes**和**Axis**[`Axis`](https://matplotlib.org/stable/api/axis_api.html#matplotlib.axis.Axis)之间的区别）轴中数据的比例。每个还有一个标题（通过 设置）、一个 x 标签（通过 设置 ）和一个 y 标签（通过 设置 ）。[`Axes`](https://matplotlib.org/stable/api/axes_api.html#matplotlib.axes.Axes)[`set_title()`](https://matplotlib.org/stable/api/_as_gen/matplotlib.axes.Axes.set_title.html#matplotlib.axes.Axes.set_title)[`set_xlabel()`](https://matplotlib.org/stable/api/_as_gen/matplotlib.axes.Axes.set_xlabel.html#matplotlib.axes.Axes.set_xlabel)[`set_ylabel()`](https://matplotlib.org/stable/api/_as_gen/matplotlib.axes.Axes.set_ylabel.html#matplotlib.axes.Axes.set_ylabel)

该类[`Axes`](https://matplotlib.org/stable/api/axes_api.html#matplotlib.axes.Axes)及其成员函数是使用 OOP 接口的主要入口点，并且在其上定义了大部分绘图方法（例如`ax.plot()`，如上所示，使用该[`plot`](https://matplotlib.org/stable/api/_as_gen/matplotlib.axes.Axes.plot.html#matplotlib.axes.Axes.plot)方法）

##### [`Axis`](https://matplotlib.org/stable/api/axis_api.html#matplotlib.axis.Axis)

指单个数轴

这些对象设置比例和限制并生成刻度（轴上的标记）和刻度标签（标记刻度的字符串）。刻度的位置由[`Locator`](https://matplotlib.org/stable/api/ticker_api.html#matplotlib.ticker.Locator)对象确定，刻度标签字符串由[`Formatter`](https://matplotlib.org/stable/api/ticker_api.html#matplotlib.ticker.Formatter). [`Locator`](https://matplotlib.org/stable/api/ticker_api.html#matplotlib.ticker.Locator)正确的组合可以[`Formatter`](https://matplotlib.org/stable/api/ticker_api.html#matplotlib.ticker.Formatter)很好地控制刻度位置和标签。

##### [`Artist`](https://matplotlib.org/stable/api/artist_api.html#matplotlib.artist.Artist)

画面中所有可以看到的东西

基本上，图形上可见的所有内容都是艺术家（甚至 [`Figure`](https://matplotlib.org/stable/api/figure_api.html#matplotlib.figure.Figure)、[`Axes`](https://matplotlib.org/stable/api/axes_api.html#matplotlib.axes.Axes)和[`Axis`](https://matplotlib.org/stable/api/axis_api.html#matplotlib.axis.Axis)对象）。这包括 [`Text`](https://matplotlib.org/stable/api/text_api.html#matplotlib.text.Text)对象、[`Line2D`](https://matplotlib.org/stable/api/_as_gen/matplotlib.lines.Line2D.html#matplotlib.lines.Line2D)对象、[`collections`](https://matplotlib.org/stable/api/collections_api.html#module-matplotlib.collections)对象、[`Patch`](https://matplotlib.org/stable/api/_as_gen/matplotlib.patches.Patch.html#matplotlib.patches.Patch) 对象等。当 Figure 被渲染时，所有的 Artists 都被绘制到**画布**上。大多数艺术家都与轴相关；这样的艺术家不能由多个轴共享，或从一个轴移动到另一个轴。

#### 编码风格

##### 显式和隐式接口

- 显式创建图和轴，并调用它们的方法（“面向对象 (OO) 风格”）。
- 依靠 pyplot 隐式创建和管理图形和坐标轴，并使用 pyplot 函数进行绘图。

> 面向对象

```python
x = np.linspace(0, 2, 100)  # Sample data.

# Note that even in the OO-style, we use `.pyplot.figure` to create the Figure.
fig, ax = plt.subplots(figsize=(5, 2.7), layout='constrained')
ax.plot(x, x, label='linear')  # Plot some data on the axes.
ax.plot(x, x**2, label='quadratic')  # Plot more data on the axes...
ax.plot(x, x**3, label='cubic')  # ... and some more.
ax.set_xlabel('x label')  # Add an x-label to the axes.
ax.set_ylabel('y label')  # Add a y-label to the axes.
ax.set_title("Simple Plot")  # Add a title to the axes.
ax.legend();  # Add a legend.
```

> 命令式

```python
x = np.linspace(0, 2, 100)  # Sample data.

plt.figure(figsize=(5, 2.7), layout='constrained')
plt.plot(x, x, label='linear')  # Plot some data on the (implicit) axes.
plt.plot(x, x**2, label='quadratic')  # etc.
plt.plot(x, x**3, label='cubic')
plt.xlabel('x label')
plt.ylabel('y label')
plt.title("Simple Plot")
plt.legend();
```

Matplotlib 的文档和示例同时使用 OO 和 pyplot 样式。一般来说，我们建议使用 OO 风格，特别是对于复杂的绘图，以及旨在作为更大项目的一部分重复使用的函数和脚本。但是，pyplot 样式对于快速交互工作来说非常方便。您可能会找到使用该`pylab`接口的旧示例，通过. 强烈反对这种方法。`from pylab import *`

##### GUI式

> QT

```python
import sys
import time

import numpy as np

from matplotlib.backends.qt_compat import QtWidgets
from matplotlib.backends.backend_qtagg import (
    FigureCanvas, NavigationToolbar2QT as NavigationToolbar)
from matplotlib.figure import Figure


class ApplicationWindow(QtWidgets.QMainWindow):
    def __init__(self):
        super().__init__()
        self._main = QtWidgets.QWidget()
        self.setCentralWidget(self._main)
        layout = QtWidgets.QVBoxLayout(self._main)

        static_canvas = FigureCanvas(Figure(figsize=(5, 3)))
        # Ideally one would use self.addToolBar here, but it is slightly
        # incompatible between PyQt6 and other bindings, so we just add the
        # toolbar as a plain widget instead.
        layout.addWidget(NavigationToolbar(static_canvas, self))
        layout.addWidget(static_canvas)

        dynamic_canvas = FigureCanvas(Figure(figsize=(5, 3)))
        layout.addWidget(dynamic_canvas)
        layout.addWidget(NavigationToolbar(dynamic_canvas, self))

        self._static_ax = static_canvas.figure.subplots()
        t = np.linspace(0, 10, 501)
        self._static_ax.plot(t, np.tan(t), ".")

        self._dynamic_ax = dynamic_canvas.figure.subplots()
        t = np.linspace(0, 10, 101)
        # Set up a Line2D.
        self._line, = self._dynamic_ax.plot(t, np.sin(t + time.time()))
        self._timer = dynamic_canvas.new_timer(50)
        self._timer.add_callback(self._update_canvas)
        self._timer.start()

    def _update_canvas(self):
        t = np.linspace(0, 10, 101)
        # Shift the sinusoid as a function of time.
        self._line.set_data(t, np.sin(t + time.time()))
        self._line.figure.canvas.draw()


if __name__ == "__main__":
    # Check whether there is already a running QApplication (e.g., if running
    # from an IDE).
    qapp = QtWidgets.QApplication.instance()
    if not qapp:
        qapp = QtWidgets.QApplication(sys.argv)

    app = ApplicationWindow()
    app.show()
    app.activateWindow()
    app.raise_()
    qapp.exec()
```

#### 多个图形和轴



### Pyplot教程

[`matplotlib.pyplot`](https://matplotlib.org/stable/api/pyplot_summary.html#module-matplotlib.pyplot)是使 matplotlib 像 MATLAB 一样工作的函数集合。每个`pyplot`函数都会对图形进行一些更改。在[`matplotlib.pyplot`](https://matplotlib.org/stable/api/pyplot_summary.html#module-matplotlib.pyplot)函数调用中保留各种状态，以便它跟踪当前图形和绘图区域等内容，并且绘图函数指向当前轴图片教程。

```python
import matplotlib.pyplot as plt
import matplotlib.image as mpimg
```

#### 格式化

对于每对 x, y 参数，都有一个可选的第三个参数，它是指示图的颜色和线型的格式字符串。格式字符串的字母和符号来自 MATLAB，您将颜色字符串与线条样式字符串连接起来。默认格式字符串是“b-”，它是一条蓝色实线。

```python
plt.plot([1, 2, 3, 4], [1, 4, 9, 16], 'ro')
plt.axis([0, 6, 0, 20])
plt.show()
```



### 修改配置

#### 定义自己的风格

```python
plt.style.use('./images/presentation.mplstyle')
```

#### 临时类型

如果您只想对特定代码块使用一种样式，但不想更改全局样式，则样式包提供了一个上下文管理器，用于将您的更改限制在特定范围内。

```python
with plt.style.context('dark_background'):
    plt.plot(np.sin(np.linspace(0, 2 * np.pi)), 'r-o')
plt.show()
```

在运行时设置 rcParams 优先于样式表，样式表优先于`matplotlibrc`文件。示例：

```python
import numpy as np
import matplotlib.pyplot as plt
import matplotlib as mpl
from cycler import cycler
mpl.rcParams['lines.linewidth'] = 2
mpl.rcParams['lines.linestyle'] = '--'
data = np.random.randn(50)
plt.plot(data)
```

[`matplotlib.rcdefaults`](https://matplotlib.org/stable/api/matplotlib_configuration_api.html#matplotlib.rcdefaults)将恢复标准的 Matplotlib 默认设置。

#### matplotlibrc

要显示当前活动`matplotlibrc`文件的加载位置

```python
import matplotlib
matplotlib.matplotlib_fname()
```

## 进阶

### Artist教程

Matplotlib API 分为三层。

- `matplotlib.backend_bases.FigureCanvas`是绘制图形的区域
- `matplotlib.backend_bases.Renderer`是知道如何绘制的对象`FigureCanvas`
- [`matplotlib.artist.Artist`](https://matplotlib.org/stable/api/artist_api.html#matplotlib.artist.Artist)知道如何使用渲染器在画布上绘画的对象。

有两种类型`Artists`：图元和容器。图元表示我们要在画布上绘制的标准图形对象： [`Line2D`](https://matplotlib.org/stable/api/_as_gen/matplotlib.lines.Line2D.html#matplotlib.lines.Line2D)、[`Rectangle`](https://matplotlib.org/stable/api/_as_gen/matplotlib.patches.Rectangle.html#matplotlib.patches.Rectangle)、 [`Text`](https://matplotlib.org/stable/api/text_api.html#matplotlib.text.Text)、[`AxesImage`](https://matplotlib.org/stable/api/image_api.html#matplotlib.image.AxesImage)等，容器是放置它们的地方（[`Axis`](https://matplotlib.org/stable/api/axis_api.html#matplotlib.axis.Axis)、 [`Axes`](https://matplotlib.org/stable/api/axes_api.html#matplotlib.axes.Axes)和[`Figure`](https://matplotlib.org/stable/api/figure_api.html#matplotlib.figure.Figure)）。标准用途是创建一个[`Figure`](https://matplotlib.org/stable/api/figure_api.html#matplotlib.figure.Figure)实例，使用`Figure`创建一个或多个[`Axes`](https://matplotlib.org/stable/api/axes_api.html#matplotlib.axes.Axes)实例 `Subplot`，并使用`Axes`实例辅助方法创建原语。

### legend指南

```python
plt.legend() #添加图例(查找每条线的label)
plt.grid()# 背景的表格
plt.xlim # 调整范围
plt.figure(figsize=())#大小单位英尺
```



## 高级

### 转换教程

| Coordinate system | Description                                                  | Transformation object from system to display                 |
| ----------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| "data"            | The coordinate system of the data in the Axes.               | `ax.transData`                                               |
| "axes"            | The coordinate system of the [`Axes`](https://matplotlib.org/stable/api/axes_api.html#matplotlib.axes.Axes); (0, 0) is bottom left of the axes, and (1, 1) is top right of the axes. | `ax.transAxes`                                               |
| "subfigure"       | The coordinate system of the [`SubFigure`](https://matplotlib.org/stable/api/figure_api.html#matplotlib.figure.SubFigure); (0, 0) is bottom left of the subfigure, and (1, 1) is top right of the subfigure. If a figure has no subfigures, this is the same as `transFigure`. | `subfigure.transSubfigure`                                   |
| "figure"          | The coordinate system of the [`Figure`](https://matplotlib.org/stable/api/figure_api.html#matplotlib.figure.Figure); (0, 0) is bottom left of the figure, and (1, 1) is top right of the figure. | `fig.transFigure`                                            |
| "figure-inches"   | The coordinate system of the [`Figure`](https://matplotlib.org/stable/api/figure_api.html#matplotlib.figure.Figure) in inches; (0, 0) is bottom left of the figure, and (width, height) is the top right of the figure in inches. | `fig.dpi_scale_trans`                                        |
| "xaxis", "yaxis"  | Blended coordinate systems, using data coordinates on one direction and axes coordinates on the other. | `ax.get_xaxis_transform()`, `ax.get_yaxis_transform()`       |
| "display"         | The native coordinate system of the output ; (0, 0) is the bottom left of the window, and (width, height) is top right of the output in "display units". The exact interpretation of the units depends on the back end. For example it is pixels for Agg and points for svg/pdf. | [`None`](https://docs.python.org/3/library/constants.html#None), or [`IdentityTransform()`](https://matplotlib.org/stable/api/transformations.html#matplotlib.transforms.IdentityTransform) |

## 颜色

### 指定颜色

| Format                                                       | Example                                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| RGB or RGBA (red, green, blue, alpha) tuple of float values in a closed interval [0, 1]. | `(0.1, 0.2, 0.5)` `(0.1, 0.2, 0.5, 0.3)`                     |
| Case-insensitive hex RGB or RGBA string.                     | `'#0f0f0f'` `'#0f0f0f80'`                                    |
| Case-insensitive RGB or RGBA string equivalent hex shorthand of duplicated characters. | `'#abc'` as `'#aabbcc'` `'#fb1'` as `'#ffbb11'`              |
| String representation of float value in closed interval `[0, 1]` for grayscale values. | `'0'` as black `'1'` as white `'0.8'` as light gray          |
| Single character shorthand notation for some basic colors. The colors green, cyan, magenta, and yellow do not coincide with X11/CSS4 colors. Their particular shades were chosen for better visibility of colored lines against typical backgrounds. | `'b'` as blue `'g'` as green `'r'` as red `'c'` as cyan `'m'` as magenta `'y'` as yellow `'k'` as black `'w'` as white |
| Case-insensitive X11/CSS4 color name with no spaces.         | `'aquamarine'` `'mediumseagreen'`                            |
| Case-insensitive color name from [xkcd color survey](https://xkcd.com/color/rgb/) with `'xkcd:'` prefix. | `'xkcd:sky blue'` `'xkcd:eggshell'`                          |
| Case-insensitive Tableau Colors from 'T10' categorical palette.  This is the default color cycle. | `'tab:blue'` `'tab:orange'` `'tab:green'` `'tab:red'` `'tab:purple'` `'tab:brown'` `'tab:pink'` `'tab:gray'` `'tab:olive'` `'tab:cyan'` |
| "CN" color spec where `'C'` precedes a number acting as an index into the default property cycle. Note Matplotlib indexes color at draw time and defaults to black if cycle does not include color. | `'C0'` `'C1'`                                                |
| `Matplotlib indexes color at draw time and defaults to black if cycle does not include color.rcParams["axes.prop_cycle"]` (default: `cycler('color', ['#1f77b4', '#ff7f0e', '#2ca02c', '#d62728', '#9467bd', '#8c564b', '#e377c2', '#7f7f7f', '#bcbd22', '#17becf'])`) | rcParams["axes.prop_cycle"]`（默认：）`cycler('color', ['#1f77b4', '#ff7f0e', '#2ca02c', '#d62728', '#9467bd', '#8c564b', '#e377c2', '#7f7f7f', '#bcbd22', '#17becf']) |

## 临时

[`Figure.subplot_mosaic`](https://matplotlib.org/stable/api/figure_api.html#matplotlib.figure.Figure.subplot_mosaic)旨在提供一个界面来直观地布置您的轴（作为 ASCII 艺术或嵌套列表）以简化此过程。

## 文本

### 文本属性和布局

```python
import matplotlib.pyplot as plt
import matplotlib.patches as patches

# build a rectangle in axes coords
left, width = .25, .5
bottom, height = .25, .5
right = left + width
top = bottom + height

fig = plt.figure()
ax = fig.add_axes([0, 0, 1, 1])

# axes coordinates: (0, 0) is bottom left and (1, 1) is upper right
p = patches.Rectangle(
    (left, bottom), width, height,
    fill=False, transform=ax.transAxes, clip_on=False
    )

ax.add_patch(p)

ax.text(left, bottom, 'left top',
        horizontalalignment='left',
        verticalalignment='top',
        transform=ax.transAxes)
ax.set_axis_off()
plt.show()
```



### 注释

```python
annotate
```

### 数学表达式

任何文本元素都可以使用数学文本。您应该使用原始字符串（在引号前加上`'r'`），并用美元符号 ($) 将数学文本括起来。

```python
# math text
plt.title(r'$\alpha > \beta$')
```

## 工具包

## 应用程序接口（API)







## 字体



## 交互式图像和异步编程

## 参考

1. [matplotlib](https://matplotlib.org/stable/tutorials/index.html)
2. [matplotlib教程](https://matplotlib.net/stable/tutorials/index.html)
3. [matplotlib中文网](https://www.matplotlib.org.cn/tutorials/#%E5%BA%8F%E8%A8%80)
4. [Matplotlib 用户指南](http://mpl.apachecn.org/#/)
