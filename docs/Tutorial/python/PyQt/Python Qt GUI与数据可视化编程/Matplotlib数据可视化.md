## 三维数据绘图
只能在mpl_toolkits.mplot3d.axes3d.Axes3D类型的子图上绘制三维图，要创建Axes3D类型的子图，需要在Figure.add_subplot()函数创建子图时设置参数projection='3d'。

FigureCanvas类的源程序，可以发现它的上层父类之一是QWidget，所以，它是用于在PyQt5 GUI界面上显示Matplotlib绘图结果的Widget组件。要在PyQt5 GUI窗体上显示Matplotlib绘图结果，必须创建一个FigureCanvas界面组件，就如同使用PyQtChart模块绘制图表时需要先创建一个QChartView界面组件。

## 图的主要元素的面向对象操作
### 其他元素
图上所有可见元素都有对应的类，例如文字是Text类，坐标轴线、刻度线、网格线、绘制的曲线都是Line2D类，Axes.bar()函数绘制的柱状图的各个矩形是Rectangle类等。所有这些图形元素的抽象父类都是matplotlib.artist.Artist类，在程序中只要获得这些对象，就可以通过类的接口函数对此对象进行操作。

![](https://s2.loli.net/2022/12/05/Bo7HJc59lROXExY.png)