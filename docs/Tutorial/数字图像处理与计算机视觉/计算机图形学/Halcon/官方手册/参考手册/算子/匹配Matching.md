## 基于组件 Component-Based

- [`clear_component_model`]

  释放组件模型的内存。

- [`clear_training_components`]

  释放组件训练结果的内存。

- [`cluster_model_components`]

  在训练结果中采用用于创建模型组件的新参数。

- [`create_component_model`]

  根据显式指定的组件和关系准备用于匹配的组件模型。

- [`create_trained_component_model`]

  根据训练好的组件准备一个组件模型进行匹配。

- [`deserialize_component_model`]

  反序列化序列化组件模型。

- [`deserialize_training_components`]

  反序列化组件训练结果。

- [`find_component_model`]

  在图像中找到组件模型的最佳匹配。

- [`gen_initial_components`]

  提取组件模型的初始组件。

- [`get_component_model_params`]

  返回组件模型的参数。

- [`get_component_model_tree`]

  返回组件模型的搜索树。

- [`get_component_relations`]

  返回训练结果中包含的模型组件之间的关系。

- [`get_found_component_model`]

  返回已找到的组件模型实例的组件。

- [`get_training_components`]

  返回特定图像中的初始或模型组件。

- [`inspect_clustered_components`]

  检查从训练中获得的刚性模型组件。

- [`modify_component_relations`]

  修改训练结果中的关系。

- [`read_component_model`]

  从文件中读取组件模型。

- [`read_training_components`]

  从文件中读取组件训练结果。

- [`serialize_component_model`]

  序列化组件模型。

- [`serialize_training_components`]

  序列化组件训练结果。

- [`train_model_components`]

  为基于组件的匹配训练组件和关系。

- [`write_component_model`]

  将组件模型写入文件。

- [`write_training_components`]

  将组件训练结果写入文件。

## 基于相关性 Correlation-Based

- [`clear_ncc_model`]

  释放 NCC 模型的内存。

- [`create_ncc_model`]

  准备一个 NCC 模型进行匹配。

- [`deserialize_ncc_model`]

  反序列化 NCC 模型。

- [`determine_ncc_model_params`]

  确定 NCC 模型的参数。

- [`find_ncc_model`]

  在图像中找到 NCC 模型的最佳匹配。

- [`find_ncc_models`]

  找到多个 NCC 模型的最佳匹配。

- [`get_ncc_model_origin`]

  返回 NCC 模型的原点（参考点）。

- [`get_ncc_model_params`]

  返回 NCC 模型的参数。

- [`get_ncc_model_region`]

  返回用于创建 NCC 模型的区域。

- [`read_ncc_model`]

  从文件中读取 NCC 模型。

- [`serialize_ncc_model`]

  序列化 NCC 模型。

- [`set_ncc_model_origin`]

  设置 NCC 模型的原点（参考点）。

- [`set_ncc_model_param`]

  设置 NCC 模型的选定参数。

- [`write_ncc_model`]

  将 NCC 模型写入文件。

## 可变形 Deformable

- [`clear_deformable_model`]

  释放可变形模型的内存。

- [`create_local_deformable_model`]

  为局部可变形匹配创建可变形模型。

- [`create_local_deformable_model_xld`]

  为 XLD 轮廓的局部可变形匹配准备可变形模型。

- [`create_planar_calib_deformable_model`]

  创建用于校准透视匹配的可变形模型。

- [`create_planar_calib_deformable_model_xld`]

  为 XLD 轮廓的平面校准匹配准备一个可变形模型。

- [`create_planar_uncalib_deformable_model`]

  为未校准的透视匹配创建可变形模型。

- [`create_planar_uncalib_deformable_model_xld`]

  为 XLD 轮廓的平面未校准匹配准备一个可变形模型。

- [`deserialize_deformable_model`]

  反序列化可变形模型。

- [`determine_deformable_model_params`]

  确定可变形模型的参数。

- [`find_local_deformable_model`]

  在图像中找到局部可变形模型的最佳匹配。

- [`find_planar_calib_deformable_model`]

  在图像中找到校准的可变形模型的最佳匹配并返回它们的 3D 姿势。

- [`find_planar_uncalib_deformable_model`]

  在图像中找到平面投影不变变形模型的最佳匹配。

- [`get_deformable_model_contours`]

  返回可变形模型的轮廓表示。

- [`get_deformable_model_origin`]

  返回可变形模型的原点（参考点）。

- [`get_deformable_model_params`]

  返回可变形模型的参数。

- [`read_deformable_model`]

  从文件中读取可变形模型。

- [`serialize_deformable_model`]

  序列化一个可变形模型。

- [`set_deformable_model_origin`]

  设置可变形模型的原点（参考点）。

- [`set_deformable_model_param`]

  设置可变形模型的选定参数。

- [`set_local_deformable_model_metric`]

  设置从 XLD 轮廓创建的局部可变形模型的指标。

- [`set_planar_calib_deformable_model_metric`]

  设置从 XLD 轮廓创建的平面校准可变形模型的指标。

- [`set_planar_uncalib_deformable_model_metric`]

  设置从 XLD 轮廓创建的平面未校准可变形模型的指标。

- [`write_deformable_model`]

  将可变形模型写入文件。

## 基于描述符 Descriptor-Based

- [`clear_descriptor_model`]

  释放描述符模型的内存。

- [`create_calib_descriptor_model`]

  创建用于校准透视匹配的描述符模型。

- [`create_uncalib_descriptor_model`]

  准备用于兴趣点匹配的描述符模型。

- [`deserialize_descriptor_model`]

  反序列化描述符模型。

- [`find_calib_descriptor_model`]

  在图像中找到校准描述符模型的最佳匹配并返回它们的 3D 姿势。

- [`find_uncalib_descriptor_model`]

  在图像中找到描述符模型的最佳匹配。

- [`get_descriptor_model_origin`]

  返回描述符模型的来源。

- [`get_descriptor_model_params`]

  返回描述符模型的参数。

- [`get_descriptor_model_points`]

  查询描述符模型或最后处理的搜索图像的兴趣点。

- [`get_descriptor_model_results`]

  查询在基于描述符的匹配过程中累积的字母数字结果。

- [`read_descriptor_model`]

  从文件中读取描述符模型。

- [`serialize_descriptor_model`]

  序列化描述符模型。

- [`set_descriptor_model_origin`]

  设置描述符模型的来源。

- [`write_descriptor_model`]

  将描述符模型写入文件。

## 基于形状 Shape-Based

- [`clear_shape_model`]

  释放形状模型的内存。

- [`create_aniso_shape_model`]

  准备一个各向异性缩放的形状模型以进行匹配。

- [`create_aniso_shape_model_xld`]

  准备一个各向异性缩放的形状模型，以便从 XLD 轮廓进行匹配。

- [`create_scaled_shape_model`]

  准备一个各向同性缩放的形状模型以进行匹配。

- [`create_scaled_shape_model_xld`]

  准备一个各向同性缩放的形状模型，以便从 XLD 轮廓进行匹配。

- [`create_shape_model`]

  准备形状模型进行匹配。

- [`create_shape_model_xld`]

  准备形状模型以匹配 XLD 轮廓。

- [`deserialize_shape_model`]

  反序列化序列化形状模型。

- [`determine_shape_model_params`]

  确定形状模型的参数。

- [`find_aniso_shape_model`]

  在图像中找到各向异性缩放形状模型的最佳匹配。

- [`find_aniso_shape_models`]

  找到多个各向异性缩放形状模型的最佳匹配。

- [`find_scaled_shape_model`]

  在图像中找到各向同性缩放形状模型的最佳匹配。

- [`find_scaled_shape_models`]

  找到多个各向同性缩放形状模型的最佳匹配。

- [`find_shape_model`]

  在图像中找到形状模型的最佳匹配。

- [`find_shape_models`]

  找到多个形状模型的最佳匹配。

- [`get_shape_model_clutter`]

  获取形状模型的杂波参数。

- [`get_shape_model_contours`]

  返回形状模型的轮廓表示。

- [`get_shape_model_origin`]

  返回形状模型的原点（参考点）。

- [`get_shape_model_params`]

  返回形状模型的参数。

- [`inspect_shape_model`]

  创建形状模型的表示。

- [`read_shape_model`]

  从文件中读取形状模型。

- [`serialize_shape_model`]

  序列化形状模型。

- [`set_shape_model_clutter`]

  设置形状模型的杂波参数。

- [`set_shape_model_metric`]

  设置从 XLD 轮廓创建的形状模型的指标。

- [`set_shape_model_origin`]

  设置形状模型的原点（参考点）。

- [`set_shape_model_param`]

  设置形状模型的选定参数。

- [`write_shape_model`]

  将形状模型写入文件。