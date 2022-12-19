## 3D场景 3D Scene

- [`add_scene_3d_camera`]

  将相机添加到 3D 场景。

- [`add_scene_3d_instance`]

  将 3D 对象模型的实例添加到 3D 场景。

- [`add_scene_3d_label`]

  向 3D 场景添加文本标签。

- [`add_scene_3d_light`]

  向 3D 场景添加光源。

- [`clear_scene_3d`]

  删除 3D 场景并释放所有分配的内存。

- [`create_scene_3d`]

  创建可视化 3D 对象集合所需的数据结构。

- [`display_scene_3d`]

  显示 3D 场景。

- [`get_display_scene_3d_info`]

  获取显示的 3D 场景中实例的深度或索引。

- [`remove_scene_3d_camera`]

  从 3D 场景中移除相机。

- [`remove_scene_3d_instance`]

  从 3D 场景中移除对象实例。

- [`remove_scene_3d_label`]

  从 3D 场景中删除文本标签。

- [`remove_scene_3d_light`]

  从 3D 场景中移除灯光。

- [`render_scene_3d`]

  渲染 3D 场景的图像。

- [`set_scene_3d_camera_pose`]

  在 3D 场景中设置相机的姿势。

- [`set_scene_3d_instance_param`]

  在 3D 场景中设置实例的参数。

- [`set_scene_3d_instance_pose`]

  在 3D 场景中设置实例的姿势。

- [`set_scene_3d_label_param`]

  在 3D 场景中设置文本标签的参数。

- [`set_scene_3d_light_param`]

  设置 3D 场景中灯光的参数。

- [`set_scene_3d_param`]

  设置 3D 场景的参数。

- [`set_scene_3d_to_world_pose`]

  设置 3D 场景的姿势。

## 绘画 Drawing

- [`drag_region1`]

  区域的交互式移动。

- [`drag_region2`]

  具有固定点规范的区域的交互式移动。

- [`drag_region3`]

  具有位置限制的区域的交互式移动。

- [`draw_circle`]

  圆形的交互式绘图。

- [`draw_circle_mod`]

  圆形的交互式绘图。

- [`draw_ellipse`]

  椭圆的交互式绘图。

- [`draw_ellipse_mod`]

  椭圆的交互式绘图。

- [`draw_line`]

  画一条线。

- [`draw_line_mod`]

  画一条线。

- [`draw_nurbs`]

  NURBS 曲线的交互式绘图。

- [`draw_nurbs_interp`]

  使用插值法交互式绘制 NURBS 曲线。

- [`draw_nurbs_interp_mod`]

  使用插值法交互式修改 NURBS 曲线。

- [`draw_nurbs_mod`]

  NURBS 曲线的交互式修改。

- [`draw_point`]

  画一个点。

- [`draw_point_mod`]

  画一个点。

- [`draw_polygon`]

  多边形行的交互式绘图。

- [`draw_rectangle1`]

  画一个平行于坐标轴的矩形。

- [`draw_rectangle1_mod`]

  画一个平行于坐标轴的矩形。

- [`draw_rectangle2`]

  任何定向矩形的交互式绘图。

- [`draw_rectangle2_mod`]

  任何定向矩形的交互式绘图。

- [`draw_region`]

  封闭区域的交互式绘图。

- [`draw_xld`]

  轮廓的交互式绘图。

- [`draw_xld_mod`]

  轮廓的交互式修改。

##  查找表 LUT

- [`get_lut`]

  获取当前查找表 。

- [`query_lut`]

  查询所有可用的查找表 。

- [`set_lut`]

  设置“查找表”（lut）。

## 鼠标 mouse

- [`get_mbutton`]

  等到按下鼠标按钮。

- [`get_mbutton_sub_pix`]

  等到按下鼠标按钮并获取亚像素鼠标位置。

- [`get_mposition`]

  查询鼠标位置。

- [`get_mposition_sub_pix`]

  查询亚像素鼠标位置。

- [`get_mshape`]

  查询当前鼠标指针形状。

- [`query_mshape`]

  查询所有可用的鼠标指针形状。

- [`send_mouse_double_click_event`]

  将事件发送到缓冲区窗口，发出鼠标双击事件信号。

- [`send_mouse_down_event`]

  向窗口缓冲区发送一个事件，发出鼠标按下事件的信号。

- [`send_mouse_drag_event`]

  将事件发送到缓冲区窗口，发出鼠标拖动事件信号。

- [`send_mouse_up_event`]

  将事件发送到缓冲区窗口，发出鼠标松开事件信号。

- [`set_mshape`]

  设置当前的鼠标指针形状。

## 对象 Object

- [`attach_background_to_window`]

  将背景图像附加到 HALCON 窗口。

- [`attach_drawing_object_to_window`]

  将现有绘图对象附加到 HALCON 窗口。

- [`clear_drawing_object`]

  删除绘图对象。

- [`create_drawing_object_circle`]

  创建一个可以交互修改的圆。

- [`create_drawing_object_circle_sector`]

  创建一个可以交互修改的圆形扇区。

- [`create_drawing_object_ellipse`]

  创建一个可以交互修改的椭圆。

- [`create_drawing_object_ellipse_sector`]

  创建一个可以交互修改的椭圆扇区。

- [`create_drawing_object_line`]

  创建可以交互修改的行。

- [`create_drawing_object_rectangle1`]

  创建一个平行于坐标轴的矩形，可以交互修改。

- [`create_drawing_object_rectangle2`]

  创建一个可以交互修改的任意方向的矩形。

- [`create_drawing_object_text`]

  创建一个可以交互移动的文本对象。

- [`create_drawing_object_xld`]

  创建一个可以交互修改的 XLD 轮廓。

- [`detach_background_from_window`]

  从 HALCON 窗口中分离背景图像。

- [`detach_drawing_object_from_window`]

  从 HALCON 窗口中分离现有绘图对象。

- [`get_drawing_object_iconic`]

  返回绘图对象的图标对象。

- [`get_drawing_object_params`]

  获取绘图对象的参数。

- [`get_window_background_image`]

  获取 HALCON 窗口背景图像的副本。

- [`set_content_update_callback`]

  设置缓冲区窗口中内容更新的回调。

- [`set_drawing_object_callback`]

  向绘图对象添加回调函数。

- [`set_drawing_object_params`]

  设置绘图对象的参数。

- [`set_drawing_object_xld`]

  设置交互式绘图 XLD 的轮廓。

## 输出 Output

- [`disp_arc`]

  在窗口中显示圆弧。

- [`disp_arrow`]

  在窗口中显示箭头。

- [`disp_channel`]

  显示具有多个通道的图像。

- [`disp_circle`]

  在窗口中显示圆圈。

- [`disp_color`]

  显示彩色  图像

- [`disp_cross`]

  在窗口中显示十字。

- [`disp_ellipse`]

  显示省略号。

- [`disp_image`]

  显示灰度值图像。

- [`disp_line`]

  在窗口中绘制线条。

- [`disp_obj`]

  显示图像对象（图像、区域、XLD）。

- [`disp_object_model_3d`]

  显示 3D 对象模型。

- [`disp_polygon`]

  显示折线。

- [`disp_rectangle1`]

  显示与坐标轴对齐的矩形。

- [`disp_rectangle2`]

  显示任意方向的矩形。

- [`disp_region`]

  在窗口中显示区域。

- [`disp_xld`]

  显示一个 XLD 对象。

## 参数 Parameters

- [`convert_coordinates_image_to_window`]

  将图像坐标转换为窗口坐标

- [`convert_coordinates_window_to_image`]

  将窗口坐标转换为图像坐标

- [`get_contour_style`]

  获取当前轮廓显示填充样式。

- [`get_draw`]

  获取当前区域填充模式。

- [`get_hsi`]

  获取当前颜色的 HSI 编码。

- [`get_icon`]

  查询区域输出的图标

- [`get_line_style`]

  获取轮廓的当前图形模式。

- [`get_line_width`]

  获取轮廓显示的当前线宽。

- [`get_paint`]

  获取灰度值的当前显示模式。

- [`get_part`]

  获取图像部分。

- [`get_part_style`]

  获取当前灰度值显示的插值方式。

- [`get_rgb`]

  获取 RGB 编码中的当前颜色。

- [`get_rgba`]

  获取 RGBA 编码中的当前颜色。

- [`get_shape`]

  获取当前区域输出形状。

- [`get_window_param`]

  获取窗口参数。

- [`query_all_colors`]

  查询所有颜色名称。

- [`query_color`]

  查询窗口中所有可显示的颜色名称。

- [`query_colored`]

  查询颜色输出的颜色数。

- [`query_gray`]

  查询可显示的灰度值。

- [`query_line_width`]

  查询可能的线宽。

- [`query_paint`]

  查询灰度值显示方式。

- [`query_shape`]

  查询区域显示模式。

- [`set_color`]

  设置输出颜色。

- [`set_colored`]

  设置多种输出颜色。

- [`set_contour_style`]

  定义轮廓显示填充样式。

- [`set_draw`]

  定义区域填充模式。

- [`set_gray`]

  定义区域输出的灰度值。

- [`set_hsi`]

  定义输出颜色（HSI 编码）。

- [`set_icon`]

  区域输出的图标定义。

- [`set_line_style`]

  定义轮廓输出模式。

- [`set_line_width`]

  定义区域轮廓输出的线宽。

- [`set_paint`]

  定义灰度值输出方式。

- [`set_part`]

  修改显示的图像部分。

- [`set_part_style`]

  定义灰度值输出的插值方法。

- [`set_rgb`]

  通过 RGB 值设置颜色定义。

- [`set_rgba`]

  通过 RGBA 值设置颜色定义。

- [`set_shape`]

  定义区域输出形状。

- [`set_window_param`]

  设置窗口参数。

## 文本 text

- [`disp_text`]

  在窗口中显示文本。

- [`get_font`]

  获取当前字体。

- [`get_font_extents`]

  获取字体所有字符的最大大小。

- [`get_string_extents`]

  获取字符串的空间大小。

- [`get_tposition`]

  获取光标位置。

- [`new_line`]

  将文本光标的位置设置为下一行的开头。

- [`query_font`]

  查询可用字体。

- [`read_char`]

  从窗口读取一个字符。

- [`read_string`]

  在文本窗口中读取字符串。

- [`set_font`]

  设置用于文本输出的字体。

- [`set_tposition`]

  设置文本光标的位置。

- [`write_string`]

  在窗口中打印文本。

## 窗口 windows

- [`clear_window`]

  删除输出窗口的内容。

- [`close_window`]

  关闭输出窗口。

- [`copy_rectangle`]

  复制输出窗口之间矩形内的所有像素。

- [`dump_window`]

  将窗口内容写入文件。

- [`dump_window_image`]

  在图像对象中写入窗口内容。

- [`flush_buffer`]

  刷新窗口的内容。

- [`get_disp_object_model_3d_info`]

  获取显示的 3D 对象模型的深度或索引。

- [`get_os_window_handle`]

  获取操作系统窗口句柄。

- [`get_window_attr`]

  获取窗口特征。

- [`get_window_extents`]

  有关窗口大小和位置的信息。

- [`get_window_pointer3`]

  访问窗口的像素数据。

- [`get_window_type`]

  获取窗口类型。

- [`new_extern_window`]

  在Windows下创建一个虚拟图形窗口。

- [`open_window`]

  打开图形窗口。

- [`query_window_type`]

  查询所有可用的窗口类型。

- [`set_window_attr`]

  设置窗口特性。

- [`set_window_dc`]

  设置虚拟图形窗口  的设备上下文。

- [`set_window_extents`]

  修改窗口的位置和大小。

- [`set_window_type`]

  指定窗口类型。

- [`unproject_coordinates`]

  计算 3D 绘图窗口中某个点的图像坐标。

- [`update_window_pose`]

  修改 3D 图的姿势。