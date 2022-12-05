Qt中用于项（Item）处理的组件有两类，一类是Item Views，包括QListView、QTreeView、QTableView、QColumnView等；另一类是Item Widgets，包括QListWidget、QTreeWidget和QTableWidget。

Item Views基于模型/视图（Model/View）结构，视图（View）与模型数据（Model Data）关联实现数据的显示和编辑。

Item Widgets是直接将数据存储在每一个项里，例如，QListWidget的每一行是一个项，QTreeWidget的每个节点是一个项，QTableWidget的每一个单元格是一个项。一个项存储了文字、文字的格式、自定义数据等。