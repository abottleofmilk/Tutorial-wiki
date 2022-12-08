# PyQT
## Model和View
Model/View（模型/视图）结构是进行数据显示与编辑的一种编程结构，在这种结构里，源数据由模型（Model）读取，然后在视图（View）组件上显示和编辑，在界面上编辑修改的数据又通过模型保存到源数据。源数据可以是内存中的字符串列表或二维表格型数据，也可以是数据库中的数据表。视图就是界面上的视图类组件，如QListView、QTreeView、QTableView等。Model/View结构是显示和编辑数据的一种有效结构，将数据模型和用户界面分离开来，分别用不同的类实现。
## 事件处理
基于窗体（Widget）的应用程序都是由事件（event）驱动的，鼠标单击、按下某个按键、重绘某个组件、最小化窗口都会产生相应的事件，应用程序对这些事件作出相应的响应处理以实现程序的功能。

![](https://s2.loli.net/2022/11/24/MuvFdeoUCNsOWtY.png)
## 文件
Python内建了文件读写操作的功能模块和函数，例如前面章节的一些例子中使用os.gtcwd()函数获取当前路径，在Demo6_3中使用内建函数open()打开文本文件并读取文件内容。在读写一般的文本文件时，使用Python自带的功能函数是很方便的，但是对于一些复杂的二进制文件，Python虽然也可以读写，但是实现起来比较麻烦。例如，Python的整数类型只有int，不区分8位、16位、32位、64位有符号或无符号整数，浮点数只有float，不区分single和double，而一些通用的二进制数据文件可能包含各种基本数据类型，用Python读写起来就比较麻烦，需要进行各种转换。
## 参考
1. [Python Qt GUI与数据可视化编程](https://weread.qq.com/web/reader/6393267071ccfa97639f573kc81322c012c81e728d9d180)
2. [PyQT中文教程](https://maicss.gitbook.io/pyqt-chinese-tutoral/pyqt6)
3. [PyQt Documentation v6.4.0](https://www.riverbankcomputing.com/static/Docs/PyQt6/)
4. [PyQt - 教程](https://iowiki.com/pyqt/pyqt_index.html)