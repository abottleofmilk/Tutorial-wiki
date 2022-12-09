Blitting 通过将所有不变的图形元素渲染到背景图像中一次来加速重复绘制。然后，对于每次绘制，只需要将变化的元素绘制到这个背景上。

策略是
    准备常量背景：
        绘制图形，但通过将他们标记为动画来排除所有您想要动画的艺术家(Artist.set_animated)。
        保存 RBGA 缓冲区的副本。
    渲染单个图像：
        恢复 RGBA 缓冲区的副本。
        Axes.draw_artist使用/ 重新绘制动画艺术家Figure.draw_artist。
        在屏幕上显示生成的图像。

此过程的一个结果是您的动画艺术家总是绘制在静态艺术家之上。

并非所有后端都支持 blitting。您可以检查给定的画布是否通过FigureCanvasBase.supports_blit属性。