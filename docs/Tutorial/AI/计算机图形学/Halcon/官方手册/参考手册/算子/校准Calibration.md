## 双目 Binocular

[`binocular_calibration`](binocular_calibration.html)

确定双目立体系统的所有相机参数。

## 标准对象  Calibration Object

- [`caltab_points`](caltab_points.html)

  从校准板描述文件中读取标记中心点。

- [`create_caltab`](create_caltab.html)

  为具有六边形排列标记的校准板生成校准板描述文件和相应的 PostScript 文件。

- [`disp_caltab`](disp_caltab.html)

  在图像中投射和可视化校准板的 3D 模型。

- [`find_calib_object`](find_calib_object.html)

  找到 HALCON 校准板并将提取的点和轮廓设置在校准数据模型中。

- [`find_caltab`](find_caltab.html)

  在图像中用矩形排列的标记分割标准校准板的区域。

- [`find_marks_and_pose`](find_marks_and_pose.html)

  从图像中提取矩形排列的 2D 校准标记，并计算外部相机参数的初始值。

- [`gen_caltab`](gen_caltab.html)

  为具有矩形排列标记的校准板生成校准板描述文件和相应的 PostScript 文件。

- [`sim_caltab`](sim_caltab.html)

  用校准板模拟图像。

## 相机参数 Camera Parameters

- [`cam_mat_to_cam_par`](cam_mat_to_cam_par.html)

  从相机矩阵计算内部相机参数。

- [`cam_par_to_cam_mat`](cam_par_to_cam_mat.html)

  从相机内部参数计算相机矩阵。

- [`deserialize_cam_par`](deserialize_cam_par.html)

  反序列化序列化的相机内部参数。

- [`read_cam_par`](read_cam_par.html)

  从文件中读取相机内部参数。

- [`serialize_cam_par`](serialize_cam_par.html)

  序列化相机内部参数。

- [`write_cam_par`](write_cam_par.html)

  将相机内部参数写入文件。

## 手眼 Hand-Eye

- [`calibrate_hand_eye`](calibrate_hand_eye.html)

  执行手眼校准。

- [`get_calib_data_observ_pose`](get_calib_data_observ_pose.html)

  从校准数据模型中获取观察到的校准对象姿势。

- [`hand_eye_calibration`](hand_eye_calibration.html)

  执行手眼校准。

- [`set_calib_data_observ_pose`](set_calib_data_observ_pose.html)

  在校准数据模型中设置观察到的校准对象姿势。

## 逆投影 Inverse Projection

- [`get_line_of_sight`](get_line_of_sight.html)

  计算对应于图像中的点的视线。

## 单筒 Monocular

[`camera_calibration`](camera_calibration.html)

通过同步最小化过程确定所有相机参数。

## 多视图 Multi-View

- [`calibrate_cameras`](calibrate_cameras.html)

  通过同步最小化过程确定所有相机参数。

- [`clear_calib_data`](clear_calib_data.html)

  释放校准数据模型的内存。

- [`clear_camera_setup_model`](clear_camera_setup_model.html)

  释放校准设置模型的内存。

- [`create_calib_data`](create_calib_data.html)

  创建 HALCON 校准数据模型。

- [`create_camera_setup_model`](create_camera_setup_model.html)

  为校准相机的设置创建模型。

- [`deserialize_calib_data`](deserialize_calib_data.html)

  反序列化序列化校准数据模型。

- [`deserialize_camera_setup_model`](deserialize_camera_setup_model.html)

  反序列化序列化相机设置模型。

- [`get_calib_data`](get_calib_data.html)

  查询校准数据模型中存储或计算的数据。

- [`get_calib_data_observ_contours`](get_calib_data_observ_contours.html)

  从校准数据模型中获取基于轮廓的观测数据。

- [`get_calib_data_observ_points`](get_calib_data_observ_points.html)

  从校准数据模型中获取基于点的观测数据。

- [`get_camera_setup_param`](get_camera_setup_param.html)

  获取通用相机设置模型参数。

- [`query_calib_data_observ_indices`](query_calib_data_observ_indices.html)

  查询相机、标定物、标定物位姿的关系信息。

- [`read_calib_data`](read_calib_data.html)

  从文件恢复校准数据模型。

- [`read_camera_setup_model`](read_camera_setup_model.html)

  从文件恢复相机设置模型。

- [`remove_calib_data`](remove_calib_data.html)

  从校准数据模型中删除数据集。

- [`remove_calib_data_observ`](remove_calib_data_observ.html)

  从校准数据模型中删除观测数据。

- [`serialize_calib_data`](serialize_calib_data.html)

  序列化校准数据模型。

- [`serialize_camera_setup_model`](serialize_camera_setup_model.html)

  序列化相机设置模型。

- [`set_calib_data`](set_calib_data.html)

  在校准数据模型中设置数据。

- [`set_calib_data_calib_object`](set_calib_data_calib_object.html)

  在校准模型中定义校准对象。

- [`set_calib_data_cam_param`](set_calib_data_cam_param.html)

  在校准数据模型中设置相机的类型和初始参数。

- [`set_calib_data_observ_points`](set_calib_data_observ_points.html)

  在校准数据模型中设置基于点的观测数据。

- [`set_camera_setup_cam_param`](set_camera_setup_cam_param.html)

  在相机设置模型中定义相机的类型、参数和相对位姿。

- [`set_camera_setup_param`](set_camera_setup_param.html)

  设置通用相机设置模型参数。

- [`write_calib_data`](write_calib_data.html)

  将校准数据模型存储到文件中。

- [`write_camera_setup_model`](write_camera_setup_model.html)

  将相机设置模型存储到文件中。

## 投影 Projection

- [`cam_par_pose_to_hom_mat3d`](cam_par_pose_to_hom_mat3d.html)

  将内部相机参数和 3D 姿势转换为 3×4 投影矩阵。

- [`project_3d_point`](project_3d_point.html)

  将 3D 点投影到（子）像素图像坐标中。

- [`project_hom_point_hom_mat3d`](project_hom_point_hom_mat3d.html)

  使用 3×4 投影矩阵投影同质 3D 点。

- [`project_point_hom_mat3d`](project_point_hom_mat3d.html)

  使用 3×4 投影矩阵投影 3D 点。

## 整改 Rectification

- [`change_radial_distortion_cam_par`](change_radial_distortion_cam_par.html)

  根据指定的径向畸变确定新的相机参数。

- [`change_radial_distortion_contours_xld`](change_radial_distortion_contours_xld.html)

  改变轮廓的径向扭曲。

- [`change_radial_distortion_image`](change_radial_distortion_image.html)

  更改图像的径向失真。

- [`change_radial_distortion_points`](change_radial_distortion_points.html)

  改变像素坐标的径向扭曲。

- [`contour_to_world_plane_xld`](contour_to_world_plane_xld.html)

  将 XLD 轮廓转换为世界坐标系的平面 z=0。

- [`gen_image_to_world_plane_map`](gen_image_to_world_plane_map.html)

  生成一个投影图，描述图像平面与世界坐标系的 z=0 平面之间的映射。

- [`gen_radial_distortion_map`](gen_radial_distortion_map.html)

  生成一个投影图，描述与不断变化的径向畸变相对应的图像映射。

- [`image_points_to_world_plane`](image_points_to_world_plane.html)

  将图像点变换到世界坐标系的平面 z=0。

- [`image_to_world_plane`](image_to_world_plane.html)

  通过将图像变换到世界坐标系的 z=0 平面来校正图像。

## 自校准 Self-Calibration

- [`radial_distortion_self_calibration`](radial_distortion_self_calibration.html)

  校准径向畸变。

- [`radiometric_self_calibration`](radiometric_self_calibration.html)

  执行相机的辐射自校准。

- [`stationary_camera_self_calibration`](stationary_camera_self_calibration.html)

  执行固定投影相机的自校准。