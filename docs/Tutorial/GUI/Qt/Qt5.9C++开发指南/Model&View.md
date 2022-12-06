odel/View（模型/视图）结构是Qt中用界面组件显示与编辑数据的一种结构，视图（View）是显示和编辑数据的界面组件，模型（Model）是视图与原始数据之间的接口。Model/View结构的典型应用是在数据库应用程序中，例如数据库中的一个数据表可以在一个QTableView组件中显示和编辑。主要的视图组件有QListView、QTreeView和QTableView。QListWidget、QTreeWidget和QTableWidget分别是这3个类的便利类，它们不使用数据模型，而是将数据直接存储在组件的每个项里。

## Model&View结构
Model/View（模型/视图）结构是Qt中用界面组件显示与编辑数据的一种结构，视图（View）是显示和编辑数据的界面组件，模型（Model）是视图与原始数据之间的接口。Model/View结构的典型应用是在数据库应用程序中，例如数据库中的一个数据表可以在一个QTableView组件中显示和编辑。主要的视图组件有QListView、QTreeView和QTableView。
### 基本原理

![](https://s2.loli.net/2022/12/06/hfCFyJ2SnXvGgra.png)

数据（Data）是实际的数据，如数据库的一个数据表或SQL查询结果，内存中的一个StringList，或磁盘文件结构等。

视图或视图组件（View）是屏幕上的界面组件，视图从数据模型获得每个数据项的模型索引（model index），通过模型索引获取数据，然后为界面组件提供显示数据。Qt提供一些现成的数据视图组件，如QListView、QTreeView和QTableView等。

模型或数据模型（Model）与实际数据通信，并为视图组件提供数据接口。它从原始数据提取需要的内容，用于视图组件进行显示和编辑。Qt中有一些预定义的数据模型，如QStringListModel可作为StringList的数据模型，QSqlTableModel可以作为数据库中一个数据表的数据模型。

模型、视图和代理之间使用信号和槽通信。当源数据发生变化时，数据模型发射信号通知视图组件；当用户在界面上操作数据时，视图组件发射信号表示这些操作信息；当编辑数据时，代理发射信号告知数据模型和视图组件编辑器的状态。
### 数据模型
所有的基于项数据（item data）的数据模型（Model）都是基于QAbstractItemModel类的，这个类定义了视图组件和代理存取数据的接口。数据无需存储在数据模型里，数据可以是其他类、文件、数据库或任何数据源。

![](https://s2.loli.net/2022/12/06/psM73wNtIxSD9nR.png)

### 视图组件

+ QListView：用于显示单列的列表数据，适用于一维数据的操作。
+ QTreeView：用于显示树状结构数据，适用于树状结构数据的操作。
+ QTableView：用于显示表格状数据，适用于二维表格型数据的操作。
+ QColumnView：用多个QListView显示树状层次结构，树状结构的一层用一个QListView显示。
+ QHeaderView：提供行表头或列表头的视图组件，如QTableView的行表头和列表头。

### 代理
