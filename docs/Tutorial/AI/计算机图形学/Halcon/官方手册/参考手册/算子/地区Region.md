## 访问 Access

- [`get_region_contour`]

  访问对象的轮廓。

- [`get_region_convex`]

  访问凸包作为轮廓。

- [`get_region_points`]

  访问区域的像素。

- [`get_region_polygon`]

  区域的多边形近似。

- [`get_region_runs`]

  访问一个区域的游程编码。

## 创建 Creation

- [`gen_checker_region`]

  创建一个方格区域。

- [`gen_circle`]

  创建一个圆圈。

- [`gen_circle_sector`]

  创建一个圈子扇区。

- [`gen_ellipse`]

  创建一个椭圆。

- [`gen_ellipse_sector`]

  创建一个椭圆扇区。

- [`gen_empty_region`]

  创建一个空白区域。

- [`gen_grid_region`]

  从线条或像素创建区域。

- [`gen_random_region`]

  创建一个随机区域。

- [`gen_random_regions`]

  创建随机区域，如圆形、矩形和椭圆形。

- [`gen_rectangle1`]

  创建一个平行于坐标轴的矩形。

- [`gen_rectangle2`]

  创建任意方向的矩形。

- [`gen_region_contour_xld`]

  从 XLD 轮廓创建区域。

- [`gen_region_histo`]

  将直方图转换为区域。

- [`gen_region_hline`]

  将以 Hesse 范式描述的输入行存储为区域。

- [`gen_region_line`]

  将输入行存储为区域。

- [`gen_region_points`]

  将单个像素存储为图像区域。

- [`gen_region_polygon`]

  将多边形存储为区域。

- [`gen_region_polygon_filled`]

  将多边形存储为“填充”区域。

- [`gen_region_polygon_xld`]

  从 XLD 多边形创建区域。

- [`gen_region_runs`]

  从游程编码创建一个区域。

- [`label_to_region`]

  从图像中提取具有相同灰度值的区域。

## 特性 Features

- [`area_center`]

  地区的面积和中心。

- [`area_holes`]

  计算区域孔的面积。

- [`circularity`]

  区域圆度（与圆的相似度）的形状因子。

- [`compactness`]

  区域紧密度的形状因子。

- [`connect_and_holes`]

  连接元件及孔数

- [`contlength`]

  区域的轮廓长度。

- [`convexity`]

  区域凸度的形状因子。

- [`diameter_region`]

  区域的两个边界点之间的最大距离。

- [`eccentricity`]

  从椭圆参数导出的形状特征。

- [`elliptic_axis`]

  计算等效椭圆的参数。

- [`euler_number`]

  计算欧拉数。

- [`find_neighbors`]

  搜索直接邻居。

- [`get_region_index`]

  包含给定像素的所有区域的索引。

- [`get_region_thickness`]

  沿主轴访问区域的厚度。

- [`hamming_distance`]

  两个区域之间的海明距离。

- [`hamming_distance_norm`]

  使用标准化的两个区域之间的汉明距离。

- [`height_width_ratio`]

  计算平行于坐标轴的周围矩形的宽度、高度和纵横比。

- [`inner_circle`]

  一个地区最大的内圈。

- [`inner_rectangle1`]

  区域的最大内部矩形。

- [`moments_region_2nd`]

  计算区域的几何矩。

- [`moments_region_2nd_invar`]

  区域的几何矩。

- [`moments_region_2nd_rel_invar`]

  区域的几何矩。

- [`moments_region_3rd`]

  区域的几何矩。

- [`moments_region_3rd_invar`]

  区域的几何矩。

- [`moments_region_central`]

  区域的几何矩。

- [`moments_region_central_invar`]

  区域的几何矩。

- [`orientation_region`]

  区域的方向。

- [`rectangularity`]

  区域矩形的形状因子。

- [`region_features`]

  计算区域的形状特征。

- [`roundness`]

  来自轮廓的形状因素。

- [`runlength_distribution`]

  区域游程编码所需的游程分布。

- [`runlength_features`]

  区域游程编码的特征值。

- [`select_region_point`]

  选择包含给定像素的所有区域。

- [`select_region_spatial`]

  区域的姿势关系。

- [`select_shape`]

  借助形状特征选择区域。

- [`select_shape_proto`]

  选择彼此有一定关系的区域。

- [`select_shape_std`]

  选择给定形状的区域。

- [`smallest_circle`]

  区域的最小包围圈。

- [`smallest_rectangle1`]

  平行于坐标轴的环绕矩形。

- [`smallest_rectangle2`]

  任何方向的最小包围矩形。

- [`spatial_relation`]

  区域相对于坐标轴的姿势关系。

## 几何变换 Geometric Transformations

- [`affine_trans_region`]

  对区域应用任意仿射二维变换。

- [`mirror_region`]

  围绕一个轴反映一个区域。

- [`move_region`]

  翻译一个区域。

- [`polar_trans_region`]

  将环形弧内的区域转换为极坐标。

- [`polar_trans_region_inv`]

  将极坐标中的区域转换回笛卡尔坐标。

- [`projective_trans_region`]

  对区域应用投影变换。

- [`transpose_region`]

  反映关于一个点的区域。

- [`zoom_region`]

  缩放一个区域。

## 集合 sets

- [`complement`]

  返回区域的补码。

- [`difference`]

  计算两个区域的差异。

- [`intersection`]

  计算两个区域的交集。

- [`symm_difference`]

  计算两个区域的对称差异。

- [`union1`]

  返回所有输入区域的并集。

- [`union2`]

  返回两个区域的联合。

## 测试 Tests

- [`test_equal_region`]

  测试两个对象的区域是否相同。

- [`test_region_point`]

  测试该区域是否包含给定点。

- [`test_subset_region`]

  测试一个区域是否包含在另一个区域中。

## 转换 Transformations

- [`background_seg`]

  确定给定区域背景的连通分量。

- [`clip_region`]

  将一个区域裁剪成一个矩形。

- [`clip_region_rel`]

  相对于其最小的周围矩形裁剪区域。

- [`closest_point_transform`]

  计算区域的最近点变换。

- [`connection`]

  计算区域的连通分量。

- [`distance_transform`]

  计算区域的距离变换。

- [`eliminate_runs`]

  消除给定长度的运行。

- [`expand_region`]

  填充区域之间的间隙或拆分重叠区域。

- [`fill_up`]

  填补区域中的漏洞。

- [`fill_up_shape`]

  填充具有给定形状特征的区域中的孔。

- [`junctions_skeleton`]

  查找骨架中的连接点和端点。

- [`merge_regions_line_scan`]

  合并线扫描图像中的区域。

- [`partition_dynamic`]

  在垂直范围较小的位置水平划分一个区域。

- [`partition_rectangle`]

  将一个区域划分为大小大致相等的矩形。

- [`rank_region`]

  区域排名运算符。

- [`remove_noise_region`]

  从区域中移除噪声。

- [`shape_trans`]

  变换区域的形状。

- [`skeleton`]

  计算一个区域的骨架。

- [`sort_region`]

  根据区域的相对位置对区域进行排序。

- [`split_skeleton_lines`]

  由一个像素宽的非分支线表示的分割线。

- [`split_skeleton_region`]

  由一个像素宽的非分支区域表示的分割线。