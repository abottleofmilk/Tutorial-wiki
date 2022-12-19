## 二维转换 3D Transformations

- [`affine_trans_pixel`]

  对像素坐标应用任意仿射二维变换。

- [`affine_trans_point_2d`]

  对点应用任意仿射二维变换。

- [`deserialize_hom_mat2d`]

  反序列化序列化的齐次二维变换矩阵。

- [`hom_mat2d_compose`]

  将两个齐次二维变换矩阵相乘。

- [`hom_mat2d_determinant`]

  计算齐次二维变换矩阵的行列式。

- [`hom_mat2d_identity`]

  生成相同二维变换的齐次变换矩阵。

- [`hom_mat2d_invert`]

  反转齐次二维变换矩阵。

- [`hom_mat2d_reflect`]

  向齐次二维变换矩阵添加反射。

- [`hom_mat2d_reflect_local`]

  向齐次二维变换矩阵添加反射。

- [`hom_mat2d_rotate`]

  向齐次二维变换矩阵添加旋转。

- [`hom_mat2d_rotate_local`]

  向齐次二维变换矩阵添加旋转。

- [`hom_mat2d_scale`]

  向齐次二维变换矩阵添加缩放。

- [`hom_mat2d_scale_local`]

  向齐次二维变换矩阵添加缩放。

- [`hom_mat2d_slant`]

  向齐次二维变换矩阵添加倾斜。

- [`hom_mat2d_slant_local`]

  向齐次二维变换矩阵添加倾斜。

- [`hom_mat2d_to_affine_par`]

  从齐次二维变换矩阵计算仿射变换参数。

- [`hom_mat2d_translate`]

  将平移添加到齐次二维变换矩阵。

- [`hom_mat2d_translate_local`]

  将平移添加到齐次二维变换矩阵。

- [`hom_mat2d_transpose`]

  转置齐次二维变换矩阵。

- [`hom_mat3d_project`]

  将仿射 3D 变换矩阵投影到 2D 投影变换矩阵。

- [`hom_vector_to_proj_hom_mat2d`]

  使用给定的点对应关系计算齐次变换矩阵。

- [`point_line_to_hom_mat2d`]

  从点到线的对应近似仿射变换。

- [`projective_trans_pixel`]

  使用齐次投影变换矩阵投影像素坐标。

- [`projective_trans_point_2d`]

  使用投影变换矩阵投影一个均匀的 2D 点。

- [`serialize_hom_mat2d`]

  序列化齐次二维变换矩阵。

- [`vector_angle_to_rigid`]

  从点和角度计算刚性仿射变换。

- [`vector_field_to_hom_mat2d`]

  从位移矢量场近似仿射映射。

- [`vector_to_aniso`]

  从点对应近似各向异性相似变换。

- [`vector_to_hom_mat2d`]

  从点对应近似仿射变换。

- [`vector_to_proj_hom_mat2d`]

  使用给定的点对应计算投影变换矩阵。

- [`vector_to_proj_hom_mat2d_distortion`]

  使用给定的图像点对应关系计算投影变换矩阵和径向畸变系数。

- [`vector_to_rigid`]

  从点对应近似刚性仿射变换。

- [`vector_to_similarity`]

  从点对应近似相似变换。

## 三D转换 3D Transformations

- [`affine_trans_point_3d`]

  对点应用任意仿射 3D 变换。

- [`deserialize_hom_mat3d`]

  反序列化序列化的齐次 3D 变换矩阵。

- [`hom_mat3d_compose`]

  将两个齐次 3D 变换矩阵相乘。

- [`hom_mat3d_determinant`]

  计算齐次 3D 变换矩阵的行列式。

- [`hom_mat3d_identity`]

  生成相同 3D 变换的齐次变换矩阵。

- [`hom_mat3d_invert`]

  反转齐次 3D 变换矩阵。

- [`hom_mat3d_rotate`]

  向齐次 3D 变换矩阵添加旋转。

- [`hom_mat3d_rotate_local`]

  向齐次 3D 变换矩阵添加旋转。

- [`hom_mat3d_scale`]

  向齐次 3D 变换矩阵添加缩放。

- [`hom_mat3d_scale_local`]

  向齐次 3D 变换矩阵添加缩放。

- [`hom_mat3d_to_pose`]

  将齐次变换矩阵转换为 3D 姿势。

- [`hom_mat3d_translate`]

  将平移添加到齐次 3D 变换矩阵。

- [`hom_mat3d_translate_local`]

  将平移添加到齐次 3D 变换矩阵。

- [`hom_mat3d_transpose`]

  转置齐次 3D 变换矩阵。

- [`pose_to_hom_mat3d`]

  将 3D 姿势转换为齐次变换矩阵。

- [`projective_trans_hom_point_3d`]

  使用投影变换矩阵投影同质 3D 点。

- [`projective_trans_point_3d`]

  使用投影变换矩阵投影 3D 点。

- [`serialize_hom_mat3d`]

  序列化齐次 3D 变换矩阵。

- [`vector_to_hom_mat3d`]

  从点对应近似 3D 变换。

## 双四元数 Dual Quaternions

- [`deserialize_dual_quat`]

  反序列化序列化的双四元数。

- [`dual_quat_compose`]

  将两个对偶四元数相乘。

- [`dual_quat_conjugate`]

  共轭对偶四元数。

- [`dual_quat_interpolate`]

  对两个对偶四元数进行插值。

- [`dual_quat_normalize`]

  规范化对偶四元数。

- [`dual_quat_to_hom_mat3d`]

  将单位对偶四元数转换为齐次变换矩阵。

- [`dual_quat_to_screw`]

  将单位对偶四元数转换为螺旋。

- [`dual_quat_trans_line_3d`]

  使用单位对偶四元数转换 3D 线。

- [`screw_to_dual_quat`]

  将一个螺丝转换成一个对偶四元数。

- [`serialize_dual_quat`]

  序列化一个双四元数。

## 杂项 Misc

- [`convert_point_3d_cart_to_spher`]

  将 3D 点的笛卡尔坐标转换为球坐标。

- [`convert_point_3d_spher_to_cart`]

  将 3D 点的球坐标转换为笛卡尔坐标。

## 姿势 Poses

- [`convert_pose_type`]

  更改 3D 姿势的表示类型。

- [`create_pose`]

  创建一个 3D 姿势。

- [`deserialize_pose`]

  反序列化序列化姿势。

- [`dual_quat_to_pose`]

  将双四元数转换为 3D 姿势。

- [`get_circle_pose`]

  从透视 2D 投影确定圆的 3D 姿态。

- [`get_pose_type`]

  获取 3D 姿势的表示类型。

- [`get_rectangle_pose`]

  从透视 2D 投影确定矩形的 3D 姿态

- [`pose_average`]

  计算一组姿势的平均值。

- [`pose_compose`]

  组合两个元组中给出的 3D 姿势。

- [`pose_invert`]

  反转 3D 姿势元组中的每个姿势。

- [`pose_to_dual_quat`]

  将 3D 姿势转换为单位对偶四元数。

- [`pose_to_quat`]

  将 3D 姿势的旋转部分转换为四元数。

- [`proj_hom_mat2d_to_pose`]

  根据描述世界坐标和图像坐标之间关系的单应性计算姿势。

- [`quat_to_pose`]

  将四元数转换为相应的 3D 姿势。

- [`read_pose`]

  从文本文件中读取 3D 姿势。

- [`serialize_pose`]

  序列化姿势。

- [`set_origin_pose`]

  转换 3D 姿势的原点。

- [`vector_to_pose`]

  根据世界坐标和图像坐标之间的点对应计算绝对姿态。

- [`write_pose`]

  将 3D 姿势写入文本文件。

## 四元数 Quaternions

- [`axis_angle_to_quat`]

  创建一个旋转四元数。

- [`deserialize_quat`]

  反序列化序列化的四元数。

- [`quat_compose`]

  将两个四元数相乘。

- [`quat_conjugate`]

  生成四元数的共轭。

- [`quat_interpolate`]

  两个四元数的插值。

- [`quat_normalize`]

  规范化四元数。

- [`quat_rotate_point_3d`]

  按单位四元数执行旋转。

- [`quat_to_hom_mat3d`]

  将四元数转换为相应的旋转矩阵。

- [`serialize_quat`]

  序列化一个四元数。