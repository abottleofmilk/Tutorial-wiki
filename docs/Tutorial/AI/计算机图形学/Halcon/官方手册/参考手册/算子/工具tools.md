## 背景估计 Background Estimator

- [`close_bg_esti`]

  删除背景估计数据集。

- [`create_bg_esti`]

  生成并初始化用于背景估计的数据集。

- [`get_bg_esti_params`]

  返回数据集的参数。

- [`give_bg_esti`]

  返回估计的背景图像。

- [`run_bg_esti`]

  估计背景并返回前景区域。

- [`set_bg_esti_params`]

  更改数据集的参数。

- [`update_bg_esti`]

  更改估计的背景图像。

## 功能 Function

- [`abs_funct_1d`]

  y 值的绝对值。

- [`compose_funct_1d`]

  组合两个函数。

- [`create_funct_1d_array`]

  从一系列 y 值创建一个函数。

- [`create_funct_1d_pairs`]

  从一组  对创建一个函数。

- [`derivate_funct_1d`]

  计算函数的导数。

- [`distance_funct_1d`]

  计算两个函数的距离。

- [`funct_1d_to_pairs`]

  访问函数的 x/y 值。

- [`get_pair_funct_1d`]

  使用控制点的索引访问函数值。

- [`get_y_value_funct_1d`]

  返回任意位置的函数值。

- [`integrate_funct_1d`]

  计算函数的正面积和负面积。

- [`invert_funct_1d`]

  计算函数的反函数。

- [`local_min_max_funct_1d`]

  计算函数的局部最小值和最大值点。

- [`match_funct_1d_trans`]

  计算两个函数之间的转换参数。

- [`negate_funct_1d`]

  否定 y 值。

- [`num_points_funct_1d`]

  函数的控制点数。

- [`read_funct_1d`]

  从文件中读取函数。

- [`sample_funct_1d`]

  在一个区间内对函数进行等距采样。

- [`scale_y_funct_1d`]

  y 值的乘法和加法。

- [`smooth_funct_1d_gauss`]

  使用高斯函数平滑等距一维函数。

- [`smooth_funct_1d_mean`]

  通过平均其值来平滑等距一维函数。

- [`transform_funct_1d`]

  使用给定的转换参数转换函数。

- [`write_funct_1d`]

  将函数写入文件。

- [`x_range_funct_1d`]

  函数的最小和最大 x 值。

- [`y_range_funct_1d`]

  函数的最小和最大 y 值。

- [`zero_crossings_funct_1d`]

  计算函数的过零点。

## 几何学 Geometry

- [`angle_ll`]

  计算两条线之间的角度。

- [`angle_lx`]

  计算一条线与水平轴之间的角度。

- [`apply_distance_transform_xld`]

  使用 XLD 距离变换确定两个轮廓的逐点距离。

- [`area_intersection_rectangle2`]

  计算定向矩形的交集面积。

- [`clear_distance_transform_xld`]

  清除 XLD 距离变换。

- [`create_distance_transform_xld`]

  创建 XLD 距离变换。

- [`deserialize_distance_transform_xld`]

  反序列化 XLD 距离变换。

- [`distance_cc`]

  计算两个轮廓之间的距离。

- [`distance_cc_min`]

  计算两个轮廓之间的最小距离。

- [`distance_cc_min_points`]

  计算两个轮廓和用于计算的点之间的最小距离。

- [`distance_contours_xld`]

  计算从一个轮廓到另一个轮廓的逐点距离。

- [`distance_lc`]

  计算一条线和一个轮廓之间的距离。

- [`distance_lr`]

  计算一条线和一个区域之间的距离。

- [`distance_pc`]

  计算一个点和一个轮廓之间的距离。

- [`distance_pl`]

  计算一点和一条线之间的距离。

- [`distance_pp`]

  计算两点之间的距离。

- [`distance_pr`]

  计算一个点和一个区域之间的距离。

- [`distance_ps`]

  计算点和线段之间的距离。

- [`distance_rr_min`]

  两个区域的轮廓像素之间的最小距离。

- [`distance_rr_min_dil`]

  在膨胀的帮助下两个区域之间的最小距离。

- [`distance_sc`]

  计算线段和一个轮廓之间的距离。

- [`distance_sl`]

  计算线段和直线之间的距离。

- [`distance_sr`]

  计算线段与一个区域之间的距离。

- [`distance_ss`]

  计算两条线段之间的距离。

- [`get_distance_transform_xld_contour`]

  获取用于构建 XLD 距离变换的参考轮廓。

- [`get_distance_transform_xld_param`]

  获取用于构建 XLD 距离变换的参数。

- [`get_points_ellipse`]

  计算椭圆周长上的点。

- [`intersection_circle_contour_xld`]

  计算圆或圆弧与 XLD 轮廓的交点

- [`intersection_circles`]

  计算两个圆或圆弧的交点

- [`intersection_contours_xld`]

  计算两个 XLD 轮廓的交点

- [`intersection_line_circle`]

  计算直线与圆或圆弧的交点

- [`intersection_line_contour_xld`]

  计算直线和 XLD 轮廓的交点

- [`intersection_lines`]

  计算两条直线的交点

- [`intersection_segment_circle`]

  计算线段与圆或圆弧的交点

- [`intersection_segment_contour_xld`]

  计算线段和 XLD 轮廓的交点

- [`intersection_segment_line`]

  计算线段和直线的交点

- [`intersection_segments`]

  计算两条线段的交点

- [`projection_pl`]

  计算点在直线上的投影。

- [`read_distance_transform_xld`]

  从文件中读取 XLD 距离变换。

- [`serialize_distance_transform_xld`]

  序列化 XLD 距离变换。

- [`set_distance_transform_xld_param`]

  为 XLD 距离变换设置新参数。

- [`write_distance_transform_xld`]

  将 XLD 距离变换写入文件。

## 网格连接 Grid Rectification

- [`connect_grid_points`]

  建立整流网格的网格点之间的连接。

- [`create_rectification_grid`]

  生成描述整流网格的 PostScript 文件。

- [`find_rectification_grid`]

  分割图像中的整流网格区域。

- [`gen_arbitrary_distortion_map`]

  生成描述任意扭曲图像和校正图像之间映射的投影图。

- [`gen_grid_rectification_map`]

  根据规则网格的点计算失真图像和校正图像之间的映射。

## 霍夫 Hough

- [`hough_circle_trans`]

  返回具有给定半径的圆的霍夫变换。

- [`hough_circles`]

  特定半径的圆心。

- [`hough_line_trans`]

  为区域内的线生成霍夫变换。

- [`hough_line_trans_dir`]

  使用局部梯度方向计算直线的霍夫变换。

- [`hough_lines`]

  在 Hough 变换的帮助下检测边缘图像中的线并将其返回到 HNF 中。

- [`hough_lines_dir`]

  在 Hough 变换的帮助下使用局部梯度方向检测边缘图像中的线条，并以正常形式返回它们。

- [`select_matching_lines`]

  从一组线（在 HNF 中）中选择最适合某个区域的那些线。

## 内插 Interpolation

- [`clear_scattered_data_interpolator`]

  清除分散的数据插值器。

- [`create_scattered_data_interpolator`]

  创建用于插值分散数据的插值器。

- [`interpolate_scattered_data`]

  使用散点数据插值器对散点数据进行插值。

- [`interpolate_scattered_data_image`]

  图像的插值。

- [`interpolate_scattered_data_points_to_image`]

  从散乱数据的插值创建图像。

## 线条 Lins

- [`line_orientation`]

  计算线的方向。

- [`line_position`]

  计算直线的重心、长度和方向。

## 马赛克 Mosaicking

- [`adjust_mosaic_images`]

  对全景图像应用自动色彩校正。

- [`bundle_adjust_mosaic`]

  执行图像马赛克的束调整。

- [`gen_bundle_adjusted_mosaic`]

  将多个图像组合成一个马赛克图像。

- [`gen_cube_map_mosaic`]

  创建球形马赛克的 6 个立方体贴图图像。

- [`gen_projective_mosaic`]

  将多个图像组合成一个马赛克图像。

- [`gen_spherical_mosaic`]

  创建球形马赛克图像。

- [`proj_match_points_distortion_ransac`]

  通过自动查找点之间的对应关系来计算两个图像之间的投影变换矩阵和径向畸变系数。

- [`proj_match_points_distortion_ransac_guided`]

  通过基于投影变换矩阵和径向畸变系数的已知近似值找到点之间的对应关系，计算两个图像之间的投影变换矩阵和径向畸变系数。

- [`proj_match_points_ransac`]

  通过查找点之间的对应关系来计算两个图像之间的投影变换矩阵。

- [`proj_match_points_ransac_guided`]

  通过基于投影变换矩阵的已知近似值查找点之间的对应关系，计算两个图像之间的投影变换矩阵。