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