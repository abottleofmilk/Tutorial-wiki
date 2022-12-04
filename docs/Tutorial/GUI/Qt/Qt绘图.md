
GUI用户界面的优势是通过可视化的界面元素为用户提供便利的操作，界面上的按钮、编辑框等各种界面组件其实都是通过绘图而得到的。Qt的二维绘图基本功能是使用QPainter在绘图设备上绘图，绘图设备包括QWidget、QPixmap等，通过绘制一些基本的点、线、圆等基本形状组成自己需要的图形，得到的图形是不可交互操作的图形。Qt还提供了Graphics View架构，使用QGraphicsView、QGraphicsScene和各种QGraphicsItem类绘图，在一个场景中可以绘制大量图件，且每个图件是可选择、可交互的，如同矢量图编辑软件那样可以操作每个图件。Graphics View架构为用户绘制复杂的组件化图形提供了便利。

## 渐变
渐变是绘图中很常见的一种功能，简单来说就是可以把几种颜色混合在一起，让它们能够自然地过渡，而不是一下子变成另一种颜色。渐变一般是用在填充里面的，所以，设置渐变是在QBrush里面。Qt 提供了三种渐变：线性渐变（QLinearGradient）、辐射渐变（QRadialGradient）和角度渐变（QConicalGradient）。从左到右依次为：线性渐变、辐射渐变、角度渐变。

![](https://cdn.staticaly.com/gh/abottleofmilk/CDN@master/img/20221204155622.png)

### 线性渐变

## 坐标系统