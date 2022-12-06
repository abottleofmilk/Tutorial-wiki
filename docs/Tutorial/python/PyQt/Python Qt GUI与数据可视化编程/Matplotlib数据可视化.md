

## 图的主要元素的面向对象操作
### 类解释

![](https://s2.loli.net/2022/12/06/LNyemrWjgRK3UhC.png)

（1）Figure图（或图表），对应类matplotlib.figure.Figure

Figure就是画布上的整个图，一个图可以有多个子图（Axes）, Figure管理这些子图，可以添加、删除子图，也可以清除整个图形区域。

（2）Axes子图，对应类matplotlib.axes.Axes

Axes就是Figure上的一个子绘图区域，一个Figure上可以有多个Axes，但是一个Axes只能属于某个Figure。一个Axes对象被创建时，会自动创建x轴和y轴，它们是Axis类对象，Axes有一些函数对坐标轴的宏观属性进行设置，如set_xlim()和set_ylim()分别设置x轴和y轴的坐标范围，set_xlabel() 和 set_ylabel()分别设置x轴和y轴的标题。

Axes提供了很多绘图函数在子图上绘图，如Axes.plot()函数绘制一般的曲线，Axes.scatter()函数绘制散点图。绘图函数会生成对象实例，例如Axes.plot()函数绘制曲线返回的结果是Line2D类型的对象，Axes.scatter()函数绘制散点图返回的是PathCollection类型对象。Axes有一些容器变量对子图上的这些对象进行管理，如Axes.get_lines()返回子图上由plot()函数生成的Line2D对象的列表。

（3）Axis坐标轴，对应类matplotlib.axis.Axis

Axis是管理坐标轴的类，它管理坐标轴的标题、刻度、刻度标签、网格线等。

+  轴标题（axis label）：坐标轴的标题字符串，如图中的“X axis label”。
+  主刻度（major tick）：坐标轴上的主分度的短线，如图中x轴的0、1、2、3、4等数值处的刻度。
+  主刻度标签（major tick label）：在主刻度处的文字标签，一般是坐标数值。
+  次刻度（minor tick）：相邻两个主刻度之间的细分刻度，次刻度默认是不显示的。
+  次刻度标签（minor tick label）：与次刻度对应的文字标签，默认是不显示的。
+  网格线（grid line）：与主刻度、次刻度对应的都有网格线。

Axis有两个子类，XAxis和YAxis，分别用于表示x轴和y轴。通过x轴和y轴对象及其管理的刻度、标签、网格线等对象可以完全定制坐标轴和网格线的显示效果。

（4）Legend图例，对应类matplotlib.legend.Legend

使用Axes.legend()函数可以为一个子图自动生成图例，获取图例对象后，可以使用Legend类的接口函数对图例的显示内容和效果进行完全的控制，例如控制图例显示位置、图例文字内容等。

（5）其他图形元素类
图上所有可见元素都有对应的类，例如文字是Text类，坐标轴线、刻度线、网格线、绘制的曲线都是Line2D类，Axes.bar()函数绘制的柱状图的各个矩形是Rectangle类等。所有这些图形元素的抽象父类都是`matplotlib.artist.Artist`类，在程序中只要获得这些对象，就可以通过类的接口函数对此对象进行操作。

+ Axes（笛卡尔坐标区）
+ Axis（单指轴）
+ Subplot（子图）
+ Plot(线图)
+ Figure（图窗）
### 其他元素
图上所有可见元素都有对应的类，例如文字是Text类，坐标轴线、刻度线、网格线、绘制的曲线都是Line2D类，Axes.bar()函数绘制的柱状图的各个矩形是Rectangle类等。所有这些图形元素的抽象父类都是matplotlib.artist.Artist类，在程序中只要获得这些对象，就可以通过类的接口函数对此对象进行操作。

![](https://s2.loli.net/2022/12/05/Bo7HJc59lROXExY.png)

## 交互

![](https://s2.loli.net/2022/12/06/QTsBwdtFL9irPnj.png)

## 典型二维图的绘制

## 三维数据绘图
只能在mpl_toolkits.mplot3d.axes3d.Axes3D类型的子图上绘制三维图，要创建Axes3D类型的子图，需要在Figure.add_subplot()函数创建子图时设置参数projection='3d'。

FigureCanvas类的源程序，可以发现它的上层父类之一是QWidget，所以，它是用于在PyQt5 GUI界面上显示Matplotlib绘图结果的Widget组件。要在PyQt5 GUI窗体上显示Matplotlib绘图结果，必须创建一个FigureCanvas界面组件，就如同使用PyQtChart模块绘制图表时需要先创建一个QChartView界面组件。