## 双目立体 Binocular Stereo

- [`binocular_disparity`]

  使用相关技术计算校正图像对的视差。

- [`binocular_disparity_mg`]

  使用多重网格方法计算校正后的立体图像对的视差。

- [`binocular_disparity_ms`]

  使用多扫描线优化计算校正立体图像对的视差。

- [`binocular_distance`]

  使用相关技术计算校正立体图像对的距离值。

- [`binocular_distance_mg`]

  使用多重网格方法计算校正立体图像对的距离值。

- [`binocular_distance_ms`]

  使用多扫描线优化计算校正立体图像对的距离值。

- [`disparity_image_to_xyz`]

  在校正立体系统中将视差图像转换为 3D 点。

- [`disparity_to_distance`]

  在整流双目立体系统中将视差值转换为距离值。

- [`disparity_to_point_3d`]

  将图像点及其视差转换为校正立体系统中的 3D 点。

- [`distance_to_disparity`]

  从距离值转换为校正立体系统中的视差。

- [`essential_to_fundamental_matrix`]

  从基本矩阵计算基本矩阵。

- [`gen_binocular_proj_rectification`]

  计算弱校准双目立体图像的投影校正。

- [`gen_binocular_rectification_map`]

  生成描述双目相机对图像到公共校正图像平面的映射的变换图。

- [`intersect_lines_of_sight`]

  从双目相机系统内两条视线的交点获取 3D 点。

- [`match_essential_matrix_ransac`]

  通过自动查找图像点之间的对应关系来计算一对立体图像的基本矩阵。

- [`match_fundamental_matrix_distortion_ransac`]

  通过自动查找图像点之间的对应关系，计算一对立体图像的基本矩阵和径向畸变系数。

- [`match_fundamental_matrix_ransac`]

  通过自动查找图像点之间的对应关系来计算一对立体图像的基本矩阵。

- [`match_rel_pose_ransac`]

  通过自动查找图像点之间的对应关系来计算两个相机之间的相对方向。

- [`reconst3d_from_fundamental_matrix`]

  基于基本矩阵计算点的投影 3d 重建。

- [`rel_pose_to_fundamental_matrix`]

  从两个相机的相对方向计算基本矩阵。

- [`vector_to_essential_matrix`]

  计算给定图像点对应关系和已知相机矩阵的基本矩阵并重建 3D 点。

- [`vector_to_fundamental_matrix`]

  计算给定一组图像点对应关系的基本矩阵并重建 3D 点。

- [`vector_to_fundamental_matrix_distortion`]

  给定一组图像点对应关系并重建 3D 点，计算基本矩阵和径向畸变系数。

- [`vector_to_rel_pose`]

  计算给定图像点对应关系和已知相机参数的两个相机之间的相对方向，并重建 3D 空间点。

## 焦点深度 Depth From Focus

- [`depth_from_focus`]

  使用多个焦点级别提取深度。

- [`select_grayvalues_from_channels`]

  使用索引图像选择多通道图像的灰度值。

## 多视图立体 Multi-View Stereo

- [`clear_stereo_model`]

  释放立体模型的内存。

- [`create_stereo_model`]

  创建 HALCON 立体模型。

- [`get_stereo_model_image_pairs`]

  返回立体模型中设置的图像对列表。

- [`get_stereo_model_object`]

  获得立体重建的中间标志性结果。

- [`get_stereo_model_object_model_3d`]

  获取立体重建的中间 3D 对象模型

- [`get_stereo_model_param`]

  获取立体模型参数。

- [`reconstruct_points_stereo`]

  从校准的多视图立体图像重建 3D 点。

- [`reconstruct_surface_stereo`]

  从校准的多视图立体图像重建表面。

- [`set_stereo_model_image_pairs`]

  指定用于表面立体重建的图像对。

- [`set_stereo_model_param`]

  设置立体模型参数。

## 光度立体 Photometric Stereo

- [`estimate_al_am`]

  估计表面的反照率和环境光量。

- [`estimate_sl_al_lr`]

  估计光源的倾斜度和表面的反照率。

- [`estimate_sl_al_zc`]

  估计光源的倾斜度和表面的反照率。

- [`estimate_tilt_lr`]

  估计光源的倾斜度。

- [`estimate_tilt_zc`]

  估计光源的倾斜度。

- [`photometric_stereo`]

  根据光度立体技术重建表面。

- [`reconstruct_height_field_from_gradient`]

  从表面梯度重建表面。

- [`sfs_mod_lr`]

  从灰度值图像重建表面。

- [`sfs_orig_lr`]

  从灰度值图像重建表面。

- [`sfs_pentland`]

  从灰度值图像重建表面。

- [`shade_height_field`]

  遮蔽高度场。

- [`uncalibrated_photometric_stereo`]

  从几个不同照明的图像重建一个表面。

## 光片 Sheet of Light

- [`apply_sheet_of_light_calibration`]

  将校准变换应用于输入视差图像。

- [`calibrate_sheet_of_light`]

  使用 3D 校准对象校准光片设置。

- [`clear_sheet_of_light_model`]

  删除光片模型并释放分配的内存。

- [`create_sheet_of_light_calib_object`]

  创建用于光片校准的校准对象。

- [`create_sheet_of_light_model`]

  使用光片技术创建模型以执行 3D 测量。

- [`deserialize_sheet_of_light_model`]

  反序列化光片模型。

- [`get_sheet_of_light_param`]

  获取已在光片模型中设置的参数值。

- [`get_sheet_of_light_result`]

  获得使用光片技术执行的测量的标志性结果。

- [`get_sheet_of_light_result_object_model_3d`]

  获取使用光片技术执行的校准测量结果作为 3D 对象模型。

- [`measure_profile_sheet_of_light`]

  处理作为输入提供的配置文件图像，并将产生的差异存储到光片模型中。

- [`query_sheet_of_light_params`]

  对于给定的光片模型，获取可在不同光片运算符中使用的通用图标或控制参数的名称。

- [`read_sheet_of_light_model`]

  从文件中读取光片模型并创建新模型。

- [`reset_sheet_of_light_model`]

  重置光片模型。

- [`serialize_sheet_of_light_model`]

  序列化光片模型。

- [`set_profile_sheet_of_light`]

  通过测量的差异设置光配置文件表。

- [`set_sheet_of_light_param`]

  设置光片模型的选定参数。

- [`write_sheet_of_light_model`]

  将光片模型写入文件。