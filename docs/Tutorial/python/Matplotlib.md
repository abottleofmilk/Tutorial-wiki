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



## 后端

Matplotlib 针对许多不同的用例和输出格式。有些人在 Python shell 中以交互方式使用 Matplotlib，并在键入命令时弹出绘图窗口。有些人运行 Jupyter笔记本并绘制内联图以进行快速数据分析。其他人将 Matplotlib 嵌入到 PyQt 或 PyGObject 等图形用户界面中以构建丰富的应用程序。有些人在批处理脚本中使用 Matplotlib 从数值模拟中生成 postscript 图像，还有一些人运行 Web 应用程序服务器来动态提供图形。

为了支持所有这些用例，Matplotlib 可以针对不同的输出，并且这些功能中的每一个都称为后端；**“前端”是面向用户的代码，即绘图代码，而“后端”则在幕后完成所有艰苦的工作以制作图形**。后端有两种类型：用户界面后端（用于 PyQt/PySide、PyGObject、Tkinter、wxPython 或 macOS/Cocoa）；也称为“交互式后端”）和制作图像文件的硬拷贝后端（PNG、SVG、PDF、PS；也称为“非交互式后端”）。

### 选择后端

- 文件中的`rcParams["backend"]`参数`matplotlibrc`
- 这[`MPLBACKEND`](https://matplotlib.org/stable/users/faq/environment_variables_faq.html#envvar-MPLBACKEND)环境变量
- 功能[`matplotlib.use()`](https://matplotlib.org/stable/api/matplotlib_configuration_api.html#matplotlib.use)

### 内置后端

#### 非交互式

| Renderer | Filetypes         | Description                                                  |
| -------- | ----------------- | ------------------------------------------------------------ |
| AGG      | png               | [raster](https://en.wikipedia.org/wiki/Raster_graphics) graphics -- high quality images using the [Anti-Grain Geometry](http://agg.sourceforge.net/antigrain.com/) engine. |
| PDF      | pdf               | [vector](https://en.wikipedia.org/wiki/Vector_graphics) graphics -- [Portable Document Format](https://en.wikipedia.org/wiki/Portable_Document_Format) output. |
| PS       | ps, eps           | [vector](https://en.wikipedia.org/wiki/Vector_graphics) graphics -- [PostScript](https://en.wikipedia.org/wiki/PostScript) output. |
| SVG      | svg               | [vector](https://en.wikipedia.org/wiki/Vector_graphics) graphics -- [Scalable Vector Graphics](https://en.wikipedia.org/wiki/Scalable_Vector_Graphics) output. |
| PGF      | pgf, pdf          | [vector](https://en.wikipedia.org/wiki/Vector_graphics) graphics -- using the [pgf](https://ctan.org/pkg/pgf) package. |
| Cairo    | png, ps, pdf, svg | [raster](https://en.wikipedia.org/wiki/Raster_graphics) or [vector](https://en.wikipedia.org/wiki/Vector_graphics) graphics -- using the [Cairo](https://www.cairographics.org) library (requires [pycairo](https://www.cairographics.org/pycairo/) or [cairocffi](https://pythonhosted.org/cairocffi/)). |

要使用非交互式后端保存绘图，请使用该 `matplotlib.pyplot.savefig('filename')`方法。

#### 交互式

| Backend   | Description                                                  |
| --------- | ------------------------------------------------------------ |
| QtAgg     | Agg rendering in a [Qt](https://qt.io/) canvas (requires [PyQt](https://riverbankcomputing.com/software/pyqt/intro) or [Qt for Python](https://doc.qt.io/qtforpython/), a.k.a. PySide). This backend can be activated in IPython with `%matplotlib qt`. |
| ipympl    | Agg rendering embedded in a Jupyter widget (requires [ipympl](https://www.matplotlib.org/ipympl)). This backend can be enabled in a Jupyter notebook with `%matplotlib ipympl`. |
| GTK3Agg   | Agg rendering to a [GTK](https://www.gtk.org/) 3.x canvas (requires [PyGObject](https://wiki.gnome.org/action/show/Projects/PyGObject) and [pycairo](https://www.cairographics.org/pycairo/)). This backend can be activated in IPython with `%matplotlib gtk3`. |
| GTK4Agg   | Agg rendering to a [GTK](https://www.gtk.org/) 4.x canvas (requires [PyGObject](https://wiki.gnome.org/action/show/Projects/PyGObject) and [pycairo](https://www.cairographics.org/pycairo/)). This backend can be activated in IPython with `%matplotlib gtk4`. |
| macosx    | Agg rendering into a Cocoa canvas in OSX. This backend can be activated in IPython with `%matplotlib osx`. |
| TkAgg     | Agg rendering to a [Tk](https://www.tcl.tk/) canvas (requires [TkInter](https://docs.python.org/3/library/tk.html)). This backend can be activated in IPython with `%matplotlib tk`. |
| nbAgg     | Embed an interactive figure in a Jupyter classic notebook. This backend can be enabled in Jupyter notebooks via `%matplotlib notebook`. |
| WebAgg    | On `show()` will start a tornado server with an interactive figure. |
| GTK3Cairo | Cairo rendering to a [GTK](https://www.gtk.org/) 3.x canvas (requires [PyGObject](https://wiki.gnome.org/action/show/Projects/PyGObject) and [pycairo](https://www.cairographics.org/pycairo/)). |
| GTK4Cairo | Cairo rendering to a [GTK](https://www.gtk.org/) 4.x canvas (requires [PyGObject](https://wiki.gnome.org/action/show/Projects/PyGObject) and [pycairo](https://www.cairographics.org/pycairo/)). |
| wxAgg     | Agg rendering to a [wxWidgets](https://www.wxwidgets.org/) canvas (requires [wxPython](https://www.wxpython.org/) 4). This backend can be activated in IPython with `%matplotlib wx`. |

内置后端的名称不区分大小写；例如，'QtAgg' 和 'qtagg' 是等价的。

## 互动

### 互动模式

| [`pyplot.ion`](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.ion.html#matplotlib.pyplot.ion) | 启用交互模式。                     |
| ------------------------------------------------------------ | ---------------------------------- |
| [`pyplot.ioff`](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.ioff.html#matplotlib.pyplot.ioff) | 禁用交互模式。                     |
| [`pyplot.isinteractive`](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.isinteractive.html#matplotlib.pyplot.isinteractive) | 返回绘图是否在每个绘图命令后更新。 |

| [`pyplot.show`](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.show.html#matplotlib.pyplot.show) | 显示所有打开的图形。            |
| ------------------------------------------------------------ | ------------------------------- |
| [`pyplot.pause`](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.pause.html#matplotlib.pyplot.pause) | 运行 GUI 事件循环*interval*秒。 |

如果您处于非交互模式（或在非交互模式下创建图形），您可能需要显式调用[`pyplot.show`](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.show.html#matplotlib.pyplot.show) 以在屏幕上显示窗口。如果只想在固定的时间内运行 GUI 事件循环，则可以使用[`pyplot.pause`](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.pause.html#matplotlib.pyplot.pause). 这将阻止您的代码进度，就好像您调用了 一样 [`time.sleep`](https://docs.python.org/3/library/time.html#time.sleep)，确保显示当前窗口并在需要时重新绘制，并在指定的时间段内运行 GUI 事件循环。与您的命令提示符集成的 GUI 事件循环和处于交互模式的图形彼此独立。如果你使用[`pyplot.ion`](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.ion.html#matplotlib.pyplot.ion)但没有安排事件循环集成，你的数字会出现但不会在提示等待输入时交互。您将无法平移/缩放并且图形甚至可能无法呈现（窗口可能显示为黑色、透明或作为其下方桌面的快照）。相反，如果您配置事件循环集成，则显示的图形将在提示时等待输入时做出响应，而不管 pyplot 的“交互模式”如何。无论交互模式设置和事件循环集成的组合如何，如果您使用 、 或以其他方式运行 GUI 主循环，图形都会`pyplot.show(block=True)`响应[`pyplot.pause`](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.pause.html#matplotlib.pyplot.pause)。

### 导航键盘快捷键

创建的窗口[`pyplot`](https://matplotlib.org/stable/api/pyplot_summary.html#module-matplotlib.pyplot)有一个带有导航按钮的交互式工具栏和光标指向的数据值的读数。默认情况下注册了许多有用的键绑定。

| Command                          | Default key binding and rcParam                              |
| -------------------------------- | ------------------------------------------------------------ |
| Home/Reset                       | `rcParams["keymap.home"]` (default: `['h', 'r', 'home']`)    |
| Back                             | `rcParams["keymap.back"]` (default: `['left', 'c', 'backspace', 'MouseButton.BACK']`) |
| Forward                          | `rcParams["keymap.forward"]` (default: `['right', 'v', 'MouseButton.FORWARD']`) |
| Pan/Zoom                         | `rcParams["keymap.pan"]` (default: `['p']`)                  |
| Zoom-to-rect                     | `rcParams["keymap.zoom"]` (default: `['o']`)                 |
| Save                             | `rcParams["keymap.save"]` (default: `['s', 'ctrl+s']`)       |
| Toggle fullscreen                | `rcParams["keymap.fullscreen"]` (default: `['f', 'ctrl+f']`) |
| Toggle major grids               | `rcParams["keymap.grid"]` (default: `['g']`)                 |
| Toggle minor grids               | `rcParams["keymap.grid_minor"]` (default: `['G']`)           |
| Toggle x axis scale (log/linear) | `rcParams["keymap.xscale"]` (default: `['k', 'L']`)          |
| Toggle y axis scale (log/linear) | `rcParams["keymap.yscale"]` (default: `['l']`)               |
| Close Figure                     | `rcParams["keymap.quit"]` (default: `['ctrl+w', 'cmd+w', 'q']`) |
| Constrain pan/zoom to x axis     | hold **x** when panning/zooming with mouse                   |
| Constrain pan/zoom to y axis     | hold **y** when panning/zooming with mouse                   |
| Preserve aspect ratio            | hold **CONTROL** when panning/zooming with mouse             |

## 字体

在 Matplotlib 内部使用字体是一个三步过程：

1. 创建[`FontProperties`](https://matplotlib.org/stable/api/font_manager_api.html#matplotlib.font_manager.FontProperties)对象（显式或隐式）
2. 基于[`FontProperties`](https://matplotlib.org/stable/api/font_manager_api.html#matplotlib.font_manager.FontProperties)对象，方法[`FontManager`](https://matplotlib.org/stable/api/font_manager_api.html#matplotlib.font_manager.FontManager)用于选择 Matplotlib 知道的最接近的“最佳”字体（SVG 模式除外 `'none'`）。
3. 后端代码使用字体对象的 Python 代理来呈现文本——具体细节取决于后端通过[`font_manager.get_font`](https://matplotlib.org/stable/api/font_manager_api.html#matplotlib.font_manager.get_font).

| Type 1 (PDF)                                                 | Type 3 (PDF/PS)                                              | TrueType (PDF)                                               |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| One of the oldest types, introduced by Adobe                 | Similar to Type 1 in terms of introduction                   | Newer than previous types, used commonly today, introduced by Apple |
| Restricted subset of PostScript, charstrings are in bytecode | Full PostScript language, allows embedding arbitrary code (in theory, even render fractals when rasterizing!) | Include a virtual machine that can execute code!             |
| These fonts support font hinting                             | Do not support font hinting                                  | Hinting supported (virtual machine processes the "hints")    |
| Non-subsetted through Matplotlib                             | Subsetted via external module [ttconv](https://github.com/sandflow/ttconv) | Subsetted via external module [fonttools](https://github.com/fonttools/fonttools) |

## 事件处理

### 事件连接

```python
fig, ax = plt.subplots()
ax.plot(np.random.rand(10))

def onclick(event):
    print('%s click: button=%d, x=%d, y=%d, xdata=%f, ydata=%f' %
          ('double' if event.dblclick else 'single', event.button,
           event.x, event.y, event.xdata, event.ydata))

cid = fig.canvas.mpl_connect('button_press_event', onclick) # 返回连接id
fig.canvas.mpl_disconnect(cid)  #断开连接
```

当连接到 'key_press_event' 和 'key_release_event' 事件时，您可能会遇到 Matplotlib 使用的不同用户界面工具包之间的不一致。这是由于用户界面工具包的不一致/限制造成的。

| Event name             | Class                                                        | Description                                               |
| ---------------------- | ------------------------------------------------------------ | --------------------------------------------------------- |
| 'button_press_event'   | [`MouseEvent`](https://matplotlib.org/stable/api/backend_bases_api.html#matplotlib.backend_bases.MouseEvent) | mouse button is pressed                                   |
| 'button_release_event' | [`MouseEvent`](https://matplotlib.org/stable/api/backend_bases_api.html#matplotlib.backend_bases.MouseEvent) | mouse button is released                                  |
| 'close_event'          | [`CloseEvent`](https://matplotlib.org/stable/api/backend_bases_api.html#matplotlib.backend_bases.CloseEvent) | figure is closed                                          |
| 'draw_event'           | [`DrawEvent`](https://matplotlib.org/stable/api/backend_bases_api.html#matplotlib.backend_bases.DrawEvent) | canvas has been drawn (but screen widget not updated yet) |
| 'key_press_event'      | [`KeyEvent`](https://matplotlib.org/stable/api/backend_bases_api.html#matplotlib.backend_bases.KeyEvent) | key is pressed                                            |
| 'key_release_event'    | [`KeyEvent`](https://matplotlib.org/stable/api/backend_bases_api.html#matplotlib.backend_bases.KeyEvent) | key is released                                           |
| 'motion_notify_event'  | [`MouseEvent`](https://matplotlib.org/stable/api/backend_bases_api.html#matplotlib.backend_bases.MouseEvent) | mouse moves                                               |
| 'pick_event'           | [`PickEvent`](https://matplotlib.org/stable/api/backend_bases_api.html#matplotlib.backend_bases.PickEvent) | artist in the canvas is selected                          |
| 'resize_event'         | [`ResizeEvent`](https://matplotlib.org/stable/api/backend_bases_api.html#matplotlib.backend_bases.ResizeEvent) | figure canvas is resized                                  |
| 'scroll_event'         | [`MouseEvent`](https://matplotlib.org/stable/api/backend_bases_api.html#matplotlib.backend_bases.MouseEvent) | mouse scroll wheel is rolled                              |
| 'figure_enter_event'   | [`LocationEvent`](https://matplotlib.org/stable/api/backend_bases_api.html#matplotlib.backend_bases.LocationEvent) | mouse enters a new figure                                 |
| 'figure_leave_event'   | [`LocationEvent`](https://matplotlib.org/stable/api/backend_bases_api.html#matplotlib.backend_bases.LocationEvent) | mouse leaves a figure                                     |
| 'axes_enter_event'     | [`LocationEvent`](https://matplotlib.org/stable/api/backend_bases_api.html#matplotlib.backend_bases.LocationEvent) | mouse enters a new axes                                   |
| 'axes_leave_event'     | [`LocationEvent`](https://matplotlib.org/stable/api/backend_bases_api.html#matplotlib.backend_bases.LocationEvent) | mouse leaves an axes                                      |

### 事件属性

所有 Matplotlib 事件都继承自 [`matplotlib.backend_bases.Event`](https://matplotlib.org/stable/api/backend_bases_api.html#matplotlib.backend_bases.Event)存储属性的基类。作为事件处理的基础的最常见事件是按键/释放事件以及鼠标按下/释放和移动事件。处理这些事件的[`KeyEvent`](https://matplotlib.org/stable/api/backend_bases_api.html#matplotlib.backend_bases.KeyEvent)和[`MouseEvent`](https://matplotlib.org/stable/api/backend_bases_api.html#matplotlib.backend_bases.MouseEvent)类都派生自 LocationEvent。[`MouseEvent`](https://matplotlib.org/stable/api/backend_bases_api.html#matplotlib.backend_bases.MouseEvent)我们刚刚使用的 是，因此我们可以通过和[`LocationEvent`](https://matplotlib.org/stable/api/backend_bases_api.html#matplotlib.backend_bases.LocationEvent)访问数据和像素坐标。除了属性，它还有`(event.x, event.y)``(event.xdata, event.ydata)``LocationEvent`。

## 交互式图像和异步编程

## 参考

1. [matplotlib](https://matplotlib.org/stable/tutorials/index.html)
2. [matplotlib教程](https://matplotlib.net/stable/tutorials/index.html)
3. [matplotlib中文网](https://www.matplotlib.org.cn/tutorials/#%E5%BA%8F%E8%A8%80)
