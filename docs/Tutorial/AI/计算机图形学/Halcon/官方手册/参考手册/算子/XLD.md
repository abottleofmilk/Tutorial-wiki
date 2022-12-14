eXtended Line Descriptions.XDL就是一个轮廓函数，它不是基于[像素]，人们通常称他为亚像素，只不过它比像素更精确，可以精确到像素内部的一种描述。

在Halcon中，**使用XLD表示亚像素的轮廓和多边形**。常用edges_sub_pix[算子]来提取亚像素轮廓。

## 访问 Access

- [`get_contour_xld`]

  返回 XLD 轮廓的坐标。

- [`get_lines_xld`]

  返回 XLD 多边形的数据（作为线）。

- [`get_parallels_xld`]

  返回 XLD 并行数据（作为行）。

- [`get_polygon_xld`]

  返回 XLD 多边形的数据。

## 创建 creation

- [`gen_circle_contour_xld`]

  创建对应于圆或圆弧的 XLD 轮廓。

- [`gen_contour_nurbs_xld`]

  将 NURBS 曲线转换为 XLD 轮廓。

- [`gen_contour_polygon_rounded_xld`]

  从多边形（以元组形式给出）生成带圆角的 XLD 轮廓。

- [`gen_contour_polygon_xld`]

  从多边形（以元组形式给出）生成 XLD 轮廓。

- [`gen_contour_region_xld`]

  从区域生成 XLD 轮廓。

- [`gen_contours_skeleton_xld`]

  将骨架转换为 XLD 轮廓。

- [`gen_cross_contour_xld`]

  为每个输入点生成一个十字形的 XLD 轮廓。

- [`gen_ellipse_contour_xld`]

  创建对应于椭圆弧的 XLD 轮廓。

- [`gen_nurbs_interp`]

  创建内插给定点的 NURBS 曲线的控制数据。

- [`gen_parallels_xld`]

  提取平行 XLD 多边形。

- [`gen_polygons_xld`]

  通过多边形近似 XLD 轮廓。

- [`gen_rectangle2_contour_xld`]

  创建矩形形状的 XLD 轮廓。

- [`mod_parallels_xld`]

  提取包含均匀区域的平行 XLD 多边形。

## 特性 Features

- [`area_center_points_xld`]

  被视为点云的轮廓和多边形的面积和重心（质心）。

- [`area_center_xld`]

  等高线和多边形的面积和重心（质心）。

- [`circularity_xld`]

  等高线或多边形的圆度（与圆的相似度）的形状因子。

- [`compactness_xld`]

  轮廓或多边形紧凑度的形状因子。

- [`contour_point_num_xld`]

  返回 XLD 轮廓中的点数。

- [`convexity_xld`]

  等高线或多边形凸度的形状因子。

- [`diameter_xld`]

  两个轮廓或多边形点之间的最大距离。

- [`dist_ellipse_contour_points_xld`]

  计算所有轮廓点到椭圆的距离。

- [`dist_ellipse_contour_xld`]

  计算轮廓到椭圆的距离。

- [`dist_rectangle2_contour_points_xld`]

  计算所有轮廓点到矩形的距离。

- [`eccentricity_points_xld`]

  被视为点云的等高线或多边形的等轴测图。

- [`eccentricity_xld`]

  从等高线或多边形的椭圆参数导出的形状特征。

- [`elliptic_axis_points_xld`]

  被视为点云的等值线或多边形等效椭圆的参数。

- [`elliptic_axis_xld`]

  等高线或多边形的等效椭圆的参数。

- [`fit_circle_contour_xld`]

  通过圆圈近似 XLD 轮廓。

- [`fit_ellipse_contour_xld`]

  通过椭圆或椭圆弧近似 XLD 轮廓。

- [`fit_line_contour_xld`]

  按线段近似 XLD 轮廓。

- [`fit_rectangle2_contour_xld`]

  使矩形适合 XLD 轮廓。

- [`get_contour_angle_xld`]

  计算每个轮廓点的 XLD 轮廓的方向。

- [`get_contour_attrib_xld`]

  返回 XLD 轮廓的点属性值。

- [`get_contour_global_attrib_xld`]

  返回 XLD 轮廓的全局属性值。

- [`get_regress_params_xld`]

  返回 XLD 轮廓参数。

- [`height_width_ratio_xld`]

  计算平行于等高线或多边形坐标轴的封闭矩形的宽度、高度和纵横比。

- [`info_parallels_xld`]

  返回有关 XLD 纬线所包围区域的灰度值的信息。

- [`length_xld`]

  等高线或多边形的长度。

- [`local_max_contours_xld`]

  选择具有局部最大灰度值的 XLD 轮廓。

- [`max_parallels_xld`]

  加入位于同一多边形上的修改后的 XLD 纬线。

- [`moments_any_points_xld`]

  被视为点云的轮廓或多边形的任意几何矩。

- [`moments_any_xld`]

  轮廓或多边形的任意几何矩。

- [`moments_points_xld`]

  被视为点云的轮廓或多边形的几何矩 M20、M02 和 M11。

- [`moments_xld`]

  等高线或多边形的几何矩 M20、M02 和 M11。

- [`orientation_points_xld`]

  被视为点云的轮廓或多边形的方向。

- [`orientation_xld`]

  轮廓或多边形的方向。

- [`query_contour_attribs_xld`]

  返回 XLD 轮廓的已定义属性的名称。

- [`query_contour_global_attribs_xld`]

  返回 XLD 轮廓定义的全局属性的名称。

- [`rectangularity_xld`]

  轮廓或多边形矩形的形状因子。

- [`select_contours_xld`]

  根据几个特征选择 XLD 轮廓。

- [`select_shape_xld`]

  使用形状特征选择轮廓或多边形。

- [`select_xld_point`]

  选择包含给定点的所有轮廓或多边形。

- [`smallest_circle_xld`]

  等高线或多边形的最小外接圆。

- [`smallest_rectangle1_xld`]

  平行于轮廓或多边形坐标轴的封闭矩形。

- [`smallest_rectangle2_xld`]

  具有任意方向的轮廓或多边形的最小封闭矩形。

- [`test_closed_xld`]

  测试轮廓或多边形是否闭合。

- [`test_self_intersection_xld`]

  测试 XLD 轮廓或多边形的自相交。

- [`test_xld_point`]

  测试一个或多个轮廓或多边形是否包含给定的点。

## 几何变换 Geometric Transformations

- [`affine_trans_contour_xld`]

  对 XLD 轮廓应用任意仿射二维变换。

- [`affine_trans_polygon_xld`]

  对 XLD 多边形应用任意仿射变换。

- [`gen_parallel_contour_xld`]

  计算 XLD 轮廓的平行轮廓。

- [`polar_trans_contour_xld`]

  将环形弧中的轮廓转换为极坐标。

- [`polar_trans_contour_xld_inv`]

  将极坐标中的轮廓转换回笛卡尔坐标

- [`projective_trans_contour_xld`]

  对 XLD 轮廓应用投影变换。

## 集合运算 Sets

- [`difference_closed_contours_xld`]

  计算闭合轮廓的差异。

- [`difference_closed_polygons_xld`]

  计算闭合多边形的差异。

- [`intersection_closed_contours_xld`]

  相交闭合轮廓。

- [`intersection_closed_polygons_xld`]

  相交封闭的多边形。

- [`symm_difference_closed_contours_xld`]

  计算闭合轮廓的对称差。

- [`symm_difference_closed_polygons_xld`]

  计算闭合多边形的对称差。

- [`union2_closed_contours_xld`]

  计算闭合轮廓的并集。

- [`union2_closed_polygons_xld`]

  计算闭合多边形的并集。

## 转换 Transformations

- [`add_noise_white_contour_xld`]

  向 XLD 轮廓添加噪声。

- [`clip_contours_xld`]

  剪辑 XLD 轮廓。

- [`clip_end_points_contours_xld`]

  剪裁 XLD 轮廓的端点。

- [`close_contours_xld`]

  关闭 XLD 轮廓。

- [`combine_roads_xld`]

  结合来自两个分辨率级别的道路假设。

- [`crop_contours_xld`]

  裁剪 XLD 轮廓。

- [`merge_cont_line_scan_xld`]

  合并来自连续线扫描图像的 XLD 轮廓。

- [`regress_contours_xld`]

  计算回归线到 XLD 轮廓的参数。

- [`segment_contour_attrib_xld`]

  局部属性满足给定条件的分段 XLD 轮廓部分。

- [`segment_contours_xld`]

  将 XLD 轮廓分割成线段和圆弧或椭圆弧。

- [`shape_trans_xld`]

  变换轮廓或多边形的形状。

- [`smooth_contours_xld`]

  平滑 XLD 轮廓。

- [`sort_contours_xld`]

  根据轮廓的相对位置对轮廓进行排序。

- [`split_contours_xld`]

  在主导点处分割 XLD 轮廓。

- [`union_adjacent_contours_xld`]

  计算端点靠得很近的等高线的并集。

- [`union_cocircular_contours_xld`]

  计算属于同一圆的轮廓的并集。

- [`union_collinear_contours_ext_xld`]

  计算共线轮廓的并集（具有扩展功能的运算符）。

- [`union_collinear_contours_xld`]

  联合近似共线的轮廓。

- [`union_cotangential_contours_xld`]

  计算余切轮廓的并集。

- [`union_straight_contours_xld`]

  计算具有相似方向的相邻直线轮廓的并集。