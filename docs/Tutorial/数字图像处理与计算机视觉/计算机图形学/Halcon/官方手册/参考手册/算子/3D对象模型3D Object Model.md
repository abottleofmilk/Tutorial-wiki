## 创建 Creation

- [`clear_object_model_3d`]

  释放 3D 对象模型的内存。

- [`copy_object_model_3d`]

  复制 3D 对象模型。

- [`deserialize_object_model_3d`]

  反序列化序列化的 3D 对象模型。

- [`gen_box_object_model_3d`]

  创建一个代表盒子的 3D 对象模型。

- [`gen_cylinder_object_model_3d`]

  创建代表圆柱体的 3D 对象模型。

- [`gen_empty_object_model_3d`]

  创建一个空的 3D 对象模型。

- [`gen_object_model_3d_from_points`]

  创建代表一组 3D 点的点云的 3D 对象模型。

- [`gen_plane_object_model_3d`]

  创建表示平面的 3D 对象模型。

- [`gen_sphere_object_model_3d`]

  创建表示球体的 3D 对象模型。

- [`gen_sphere_object_model_3d_center`]

  创建一个表示 x,y,z 坐标球体的 3D 对象模型。

- [`read_object_model_3d`]

  从文件中读取 3D 对象模型。

- [`remove_object_model_3d_attrib`]

  删除 3D 对象模型的属性。

- [`remove_object_model_3d_attrib_mod`]

  删除 3D 对象模型的属性。

- [`serialize_object_model_3d`]

  序列化 3D 对象模型。

- [`set_object_model_3d_attrib`]

  设置 3D 对象模型的属性。

- [`set_object_model_3d_attrib_mod`]

  设置 3D 对象模型的属性。

- [`union_object_model_3d`]

  将多个 3D 对象模型组合成一个新的 3D 对象模型。

- [`write_object_model_3d`]

  将 3D 对象模型写入文件。

## 特性 Features

- [`area_object_model_3d`]

  计算 3D 对象模型所有面的面积。

- [`distance_object_model_3d`]

  计算一个 3D 对象模型的点到另一个 3D 对象模型的距离。

- [`get_object_model_3d_params`]

  返回 3D 对象模型的属性。

- [`max_diameter_object_model_3d`]

  计算 3D 对象模型的最大直径。

- [`moments_object_model_3d`]

  计算 3D 对象模型的二阶均值或中心矩。

- [`select_object_model_3d`]

  根据全局特征从 3D 对象模型数组中选择 3D 对象模型。

- [`smallest_bounding_box_object_model_3d`]

  计算 3D 对象模型的点周围的最小边界框。

- [`smallest_sphere_object_model_3d`]

  计算 3D 对象模型的点周围的最小球体。

- [`volume_object_model_3d_relative_to_plane`]

  计算 3D 对象模型的体积。

## 分割 Segmentation

- [`fit_primitives_object_model_3d`]

  将 3D 基元拟合到一组 3D 点中。

- [`reduce_object_model_3d_by_view`]

  通过将 3D 对象模型投影到虚拟视图并删除给定区域之外的所有点，从 3D 对象模型中删除点。

- [`segment_object_model_3d`]

  将一组 3D 点分割成具有相似特征的子集。

- [`select_points_object_model_3d`]

  将阈值应用于 3D 对象模型的属性。

## 转换 Transformations

- [`affine_trans_object_model_3d`]

  将任意仿射 3D 变换应用于 3D 对象模型。

- [`connection_object_model_3d`]

  确定 3D 对象模型的连接组件。

- [`convex_hull_object_model_3d`]

  计算 3D 对象模型的凸包。

- [`edges_object_model_3d`]

  在 3D 对象模型中查找边。

- [`fuse_object_model_3d`]

  将 3D 对象模型融合到表面中。

- [`intersect_plane_object_model_3d`]

  将 3D 对象模型与平面相交。

- [`object_model_3d_to_xyz`]

  将 3D 点从 3D 对象模型转换为图像。

- [`prepare_object_model_3d`]

  为某个操作准备一个 3D 对象模型。

- [`project_object_model_3d`]

  将 3D 对象模型投影到图像坐标中。

- [`projective_trans_object_model_3d`]

  将任意投影 3D 变换应用于 3D 对象模型。

- [`register_object_model_3d_global`]

  根据重叠改进 3D 对象模型之间的相对转换。

- [`register_object_model_3d_pair`]

  搜索两个 3D 对象模型之间的转换。

- [`render_object_model_3d`]

  渲染 3D 对象模型以获取图像。

- [`rigid_trans_object_model_3d`]

  将刚性 3D 变换应用于 3D 对象模型。

- [`sample_object_model_3d`]

  采样 3D 对象模型。

- [`simplify_object_model_3d`]

  简化三角化 3D 对象模型。

- [`smooth_object_model_3d`]

  平滑 3D 对象模型的 3D 点。

- [`surface_normals_object_model_3d`]

  计算 3D 对象模型的 3D 表面法线。

- [`triangulate_object_model_3d`]

  为 3D 对象模型创建表面三角测量。

- [`xyz_to_object_model_3d`]

  将 3D 点从图像转换为 3D 对象模型。