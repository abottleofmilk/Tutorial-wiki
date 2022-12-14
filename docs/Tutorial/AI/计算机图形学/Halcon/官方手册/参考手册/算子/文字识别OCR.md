## 卷积神经网络 Convolutional Neural Networks

- [`clear_ocr_class_cnn`]

  清除基于 CNN 的 OCR 分类器。

- [`deserialize_ocr_class_cnn`]

  反序列化基于 CNN 的序列化 OCR 分类器。

- [`do_ocr_multi_class_cnn`]

  使用基于 CNN 的 OCR 分类器对多个字符进行分类。

- [`do_ocr_single_class_cnn`]

  使用基于 CNN 的 OCR 分类器对单个字符进行分类。

- [`do_ocr_word_cnn`]

  使用基于 CNN 的 OCR 分类器对一组相关字符进行分类。

- [`get_params_ocr_class_cnn`]

  返回基于 CNN 的 OCR 分类器的参数。

- [`query_params_ocr_class_cnn`]

  获取可在 get_params_ocr_class_cnn 中用于给定的基于 CNN 的 OCR 分类器的参数名称。

- [`read_ocr_class_cnn`]

  从文件中读取基于 CNN 的 OCR 分类器。

- [`serialize_ocr_class_cnn`]

  序列化基于 CNN 的 OCR 分类器

## K近邻 K-Nearest Neighbors

- [`clear_ocr_class_knn`]

  清除 OCR 分类器。

- [`create_ocr_class_knn`]

  使用 k 最近邻  分类器创建 OCR 分类器。

- [`deserialize_ocr_class_knn`]

  反序列化序列化的基于 k-NN 的 OCR 分类器。

- [`do_ocr_multi_class_knn`]

  使用 k-NN 分类器对多个字符进行分类。

- [`do_ocr_single_class_knn`]

  使用 OCR 分类器对单个字符进行分类。

- [`do_ocr_word_knn`]

  使用 OCR 分类器对一组相关字符进行分类。

- [`get_features_ocr_class_knn`]

  计算字符的特征。

- [`get_params_ocr_class_knn`]

  返回 OCR 分类器的参数。

- [`read_ocr_class_knn`]

  从文件中读取 OCR 分类器。

- [`select_feature_set_trainf_knn`]

  选择最佳特征组合对 OCR 数据进行分类。

- [`serialize_ocr_class_knn`]

  序列化基于 k-NN 的 OCR 分类器。

- [`trainf_ocr_class_knn`]

  为 OCR 任务训练 k-NN 分类器。

- [`write_ocr_class_knn`]

  将 OCR 任务的 k-NN 分类器写入文件。

## 词典 Lexica

- [`clear_lexicon`]

  清空一个词库。

- [`create_lexicon`]

  从单词元组创建词典。

- [`import_lexicon`]

  从文本文件创建词典。

- [`inspect_lexicon`]

  查询词典中的所有单词。

- [`lookup_lexicon`]

  检查词典中是否包含单词。

- [`suggest_lexicon`]

  在词典中查找相似的词。

## 神经网络 Neural Nets

- [`clear_ocr_class_mlp`]

  清除 OCR 分类器。

- [`create_ocr_class_mlp`]

  使用多层感知器创建 OCR 分类器。

- [`deserialize_ocr_class_mlp`]

  反序列化基于 MLP 的序列化 OCR 分类器。

- [`do_ocr_multi_class_mlp`]

  使用 OCR 分类器对多个字符进行分类。

- [`do_ocr_single_class_mlp`]

  使用 OCR 分类器对单个字符进行分类。

- [`do_ocr_word_mlp`]

  使用 OCR 分类器对一组相关字符进行分类。

- [`get_features_ocr_class_mlp`]

  计算字符的特征。

- [`get_params_ocr_class_mlp`]

  返回 OCR 分类器的参数。

- [`get_prep_info_ocr_class_mlp`]

  计算 OCR 分类器的预处理特征向量的信息内容。

- [`get_regularization_params_ocr_class_mlp`]

  返回 OCR 分类器的正则化参数。

- [`get_rejection_params_ocr_class_mlp`]

  返回 OCR 分类器的拒绝类参数。

- [`read_ocr_class_mlp`]

  从文件中读取 OCR 分类器。

- [`select_feature_set_trainf_mlp`]

  选择最佳特征组合来对 OCR 数据进行分类。

- [`select_feature_set_trainf_mlp_protected`]

  选择最佳特征组合以对来自（受保护的）培训文件的 OCR 数据进行分类。

- [`serialize_ocr_class_mlp`]

  序列化基于 MLP 的 OCR 分类器。

- [`set_regularization_params_ocr_class_mlp`]

  设置 OCR 分类器的正则化参数。

- [`set_rejection_params_ocr_class_mlp`]

  设置 OCR 分类器的拒绝类参数。

- [`trainf_ocr_class_mlp`]

  训练 OCR 分类器。

- [`trainf_ocr_class_mlp_protected`]

  使用来自（受保护的）训练文件的数据训练 OCR 分类器。

- [`write_ocr_class_mlp`]

  将 OCR 分类器写入文件。

## 分隔 Segmentation

- [`clear_text_model`]

  清除文本模型。

- [`clear_text_result`]

  清除文本结果。

- [`create_text_model_reader`]

  创建文本模型。

- [`find_text`]

  在图像中查找文本。

- [`get_text_model_param`]

  文本模型的查询参数。

- [`get_text_object`]

  查询文本分词结果的标志值。

- [`get_text_result`]

  查询文本分词结果的控制值。

- [`segment_characters`]

  分割图像给定区域中的字符。

- [`select_characters`]

  从给定区域中选择字符。

- [`set_text_model_param`]

  设置文本模型的参数。

- [`text_line_orientation`]

  确定文本行或段落的方向。

- [`text_line_slant`]

  确定文本行或段落的字符倾斜度。

## 支持向量机  Support Vector Machines

- [`clear_ocr_class_svm`]

  清除基于 SVM 的 OCR 分类器。

- [`create_ocr_class_svm`]

  使用支持向量机创建 OCR 分类器。

- [`deserialize_ocr_class_svm`]

  反序列化基于 SVM 的序列化 OCR 分类器。

- [`do_ocr_multi_class_svm`]

  使用基于 SVM 的 OCR 分类器对多个字符进行分类。

- [`do_ocr_single_class_svm`]

  使用基于 SVM 的 OCR 分类器对单个字符进行分类。

- [`do_ocr_word_svm`]

  使用 OCR 分类器对一组相关字符进行分类。

- [`get_features_ocr_class_svm`]

  计算字符的特征。

- [`get_params_ocr_class_svm`]

  返回 OCR 分类器的参数。

- [`get_prep_info_ocr_class_svm`]

  计算基于 SVM 的 OCR 分类器的预处理特征向量的信息内容。

- [`get_support_vector_num_ocr_class_svm`]

  返回 OCR 分类器的支持向量数。

- [`get_support_vector_ocr_class_svm`]

  从基于支持向量机的经过训练的 OCR 分类器返回支持向量的索引。

- [`read_ocr_class_svm`]

  从文件中读取基于 SVM 的 OCR 分类器。

- [`reduce_ocr_class_svm`]

  通过简化的 SVM 逼近经过训练的基于 SVM 的 OCR 分类器。

- [`select_feature_set_trainf_svm`]

  选择最佳特征组合来对 OCR 数据进行分类。

- [`select_feature_set_trainf_svm_protected`]

  选择最佳特征组合以对来自（受保护的）培训文件的 OCR 数据进行分类。

- [`serialize_ocr_class_svm`]

  序列化基于 SVM 的 OCR 分类器

- [`trainf_ocr_class_svm`]

  训练 OCR 分类器。

- [`trainf_ocr_class_svm_protected`]

  使用来自（受保护的）训练文件的数据训练 OCR 分类器。

- [`write_ocr_class_svm`]

  将 OCR 分类器写入文件。

## 训练文件 Training Files

- [`append_ocr_trainf`]

  将字符添加到训练文件中。

- [`concat_ocr_trainf`]

  Concat 训练文件。

- [`protect_ocr_trainf`]

  保护训练数据。

- [`read_ocr_trainf`]

  从文件中读取训练字符并转换为图像。

- [`read_ocr_trainf_names`]

  查询训练文件中存储了哪些字符。

- [`read_ocr_trainf_names_protected`]

  查询哪些字符存储在（受保护的）训练文件中。

- [`read_ocr_trainf_select`]

  从文件中读取训练特定字符并转换为图像。

- [`write_ocr_trainf`]

  将训练字符存储到文件中。

- [`write_ocr_trainf_image`]

  将字符写入训练文件。