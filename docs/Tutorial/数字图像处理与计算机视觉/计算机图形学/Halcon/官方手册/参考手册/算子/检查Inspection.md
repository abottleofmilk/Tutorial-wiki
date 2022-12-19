## 珠子检查 Bead Inspection

- [`apply_bead_inspection_model`]

  根据珠子检查模型的定义，检查图像中的珠子。

- [`clear_bead_inspection_model`]

  删除珠子检查模型并释放分配的内存。

- [`create_bead_inspection_model`]

  创建模型以检查图像中的珠子或粘合剂。

- [`get_bead_inspection_param`]

  获取特定珠子检测模型中的参数值。

- [`set_bead_inspection_param`]

  设置珠子检查模型的参数。

## OCV

- [`close_ocv`]

  清除 OCV 工具。

- [`create_ocv_proj`]

  创建一个基于灰度值投影的新 OCV 工具。

- [`deserialize_ocv`]

  反序列化序列化的 OCV 工具。

- [`do_ocv_simple`]

  使用 OCV 工具验证模式。

- [`read_ocv`]

  从文件中读取 OCV 工具。

- [`serialize_ocv`]

  序列化 OCV 工具。

- [`traind_ocv_proj`]

  OCV工具的训练。

- [`write_ocv`]

  将 OCV 工具保存到文件中。

## 结构光 Structured Light

- [`clear_structured_light_model`]

  清除结构光模型并释放分配的内存。

- [`create_structured_light_model`]

  创建结构光模型。

- [`decode_structured_light_pattern`]

  解码使用结构光设置获取的相机图像。

- [`deserialize_structured_light_model`]

  反序列化结构光模型。

- [`gen_structured_light_pattern`]

  生成要在结构光设置中显示的图案图像。

- [`get_structured_light_model_param`]

  查询结构光模型参数。

- [`get_structured_light_object`]

  获得结构光模型的（中间）标志性结果。

- [`read_structured_light_model`]

  从文件中读取结构光模型。

- [`serialize_structured_light_model`]

  序列化结构光模型。

- [`set_structured_light_model_param`]

  设置结构光模型的参数。

- [`write_structured_light_model`]

  将结构光模型写入文件。

## 质地检验 Texture Inspection

- [`add_texture_inspection_model_image`]

  将训练图像添加到纹理检查模型。

- [`apply_texture_inspection_model`]

  检查图像中的纹理。

- [`clear_texture_inspection_model`]

  清除纹理检查模型并释放分配的内存。

- [`clear_texture_inspection_result`]

  清除纹理检查结果句柄并释放分配的内存。

- [`create_texture_inspection_model`]

  创建纹理检查模型。

- [`deserialize_texture_inspection_model`]

  反序列化序列化纹理检查模型。

- [`get_texture_inspection_model_image`]

  获取包含在纹理检查模型中的训练图像。

- [`get_texture_inspection_model_param`]

  查询纹理检测模型的参数。

- [`get_texture_inspection_result_object`]

  查询纹理检查的标志性结果。

- [`read_texture_inspection_model`]

  从文件中读取纹理检查模型。

- [`remove_texture_inspection_model_image`]

  清除纹理检查模型图像的全部或用户定义的子集。

- [`serialize_texture_inspection_model`]

  序列化纹理检查模型。

- [`set_texture_inspection_model_param`]

  设置纹理检测模型的参数。

- [`train_texture_inspection_model`]

  训练纹理检查模型。

- [`write_texture_inspection_model`]

  将纹理检查模型写入文件。

## 变异模型 Variation Model

- [`clear_train_data_variation_model`]

  释放变异模型训练数据的内存。

- [`clear_variation_model`]

  释放变体模型的内存。

- [`compare_ext_variation_model`]

  将图像与变体模型进行比较。

- [`compare_variation_model`]

  将图像与变体模型进行比较。

- [`create_variation_model`]

  创建用于图像比较的变体模型。

- [`deserialize_variation_model`]

  反序列化变体模型。

- [`get_thresh_images_variation_model`]

  返回用于变异模型图像比较的阈值图像。

- [`get_variation_model`]

  通过变体模型返回用于图像比较的图像。

- [`prepare_direct_variation_model`]

  准备一个变体模型以与图像进行比较。

- [`prepare_variation_model`]

  准备一个变体模型以与图像进行比较。

- [`read_variation_model`]

  从文件中读取变体模型。

- [`serialize_variation_model`]

  序列化一个变体模型。

- [`train_variation_model`]

  训练变异模型。

- [`write_variation_model`]

  将变体模型写入文件。