## 条形码 Bar code

- [`clear_bar_code_model`]

  删除条码模型并释放分配的内存

- [`create_bar_code_model`]

  创建条形码阅读器的模型。

- [`decode_bar_code_rectangle2`]

  解码矩形内的条形码符号。

- [`deserialize_bar_code_model`]

  反序列化条形码模型。

- [`find_bar_code`]

  检测和读取图像中的条形码符号。

- [`get_bar_code_object`]

  访问在条形码符号的搜索或解码过程中创建的图标对象。

- [`get_bar_code_param`]

  获取描述条码模型的一个或多个参数。

- [`get_bar_code_param_specific`]

  获取条码阅读器在处理特定条码类型时使用的参数。

- [`get_bar_code_result`]

  获取条形码符号解码过程中累积的字母数字结果。

- [`query_bar_code_params`]

  获取可在给定条码模型的 set_bar_code* 和 get_bar_code* 运算符中使用的参数名称

- [`read_bar_code_model`]

  从文件中读取条码模型并创建新模型。

- [`serialize_bar_code_model`]

  序列化条形码模型。

- [`set_bar_code_param`]

  设置条码模型的选定参数。

- [`set_bar_code_param_specific`]

  为选定的条码类型设置条码模型的选定参数

- [`write_bar_code_model`]

  将条码模型写入文件。

## 数据码 Data code

- [`clear_data_code_2d_model`]

  删除二维数据代码模型并释放分配的内存。

- [`create_data_code_2d_model`]

  创建二维数据代码类的模型。

- [`deserialize_data_code_2d_model`]

  反序列化序列化的二维数据代码模型。

- [`find_data_code_2d`]

  检测并读取图像中的二维数据码符号或训练二维数据码模型。

- [`get_data_code_2d_objects`]

  访问在搜索二维数据代码符号期间创建的图标对象。

- [`get_data_code_2d_param`]

  获取描述二维数据代码模型的一个或多个参数。

- [`get_data_code_2d_results`]

  获取在搜索二维数据代码符号期间累积的字母数字结果。

- [`query_data_code_2d_params`]

  为给定的二维数据代码模型获取可在其他二维数据代码运算符中使用的通用参数或对象的名称。

- [`read_data_code_2d_model`]

  从文件中读取二维数据代码模型并创建新模型。

- [`serialize_data_code_2d_model`]

  序列化二维数据代码模型。

- [`set_data_code_2d_param`]

  设置二维数据代码模型的选定参数。

- [`write_data_code_2d_model`]

  将二维数据代码模型写入文件。

## 基于样本 Sample-Based

- [`add_sample_identifier_preparation_data`]

  将制备数据添加到现有样品标识符中。

- [`add_sample_identifier_training_data`]

  将训练数据添加到现有样本标识符中。

- [`apply_sample_identifier`]

  使用示例标识符识别对象。

- [`clear_sample_identifier`]

  释放样本标识符的内存。

- [`create_sample_identifier`]

  创建一个新的示例标识符。

- [`deserialize_sample_identifier`]

  反序列化序列化样本标识符。

- [`get_sample_identifier_object_info`]

  检索有关样本标识符对象的信息。

- [`get_sample_identifier_param`]

  获取样本标识符的选定参数。

- [`prepare_sample_identifier`]

  使样本标识符的内部数据结构适应待识别的对象。

- [`read_sample_identifier`]

  从文件中读取样本标识符。

- [`remove_sample_identifier_preparation_data`]

  从样本标识符中删除准备数据。

- [`remove_sample_identifier_training_data`]

  从样本标识符中删除训练数据。

- [`serialize_sample_identifier`]

  序列化样本标识符。

- [`set_sample_identifier_object_info`]

  为样品标识符的对象定义名称或描述。

- [`set_sample_identifier_param`]

  设置样本标识符的选定参数。

- [`train_sample_identifier`]

  训练样本标识符。

- [`write_sample_identifier`]

  将样本标识符写入文件。