## 高斯混合模型  Gaussian Mixture Models

- [`add_class_train_data_gmm`]

  将训练数据添加到高斯混合模型 。

- [`add_sample_class_gmm`]

  将训练样本添加到高斯混合模型的训练数据中。

- [`classify_class_gmm`]

  通过高斯混合模型计算特征向量的类别。

- [`clear_class_gmm`]

  清除高斯混合模型。

- [`clear_samples_class_gmm`]

  清除高斯混合模型的训练数据。

- [`create_class_gmm`]

  创建用于分类的高斯混合模型

- [`deserialize_class_gmm`]

  反序列化序列化的高斯混合模型。

- [`evaluate_class_gmm`]

  通过高斯混合模型评估特征向量。

- [`get_class_train_data_gmm`]

  获取高斯混合模型  的训练数据。

- [`get_params_class_gmm`]

  返回高斯混合模型的参数。

- [`get_prep_info_class_gmm`]

  计算 GMM 的预处理特征向量的信息内容。

- [`get_sample_class_gmm`]

  从高斯混合模型  的训练数据中返回训练样本。

- [`get_sample_num_class_gmm`]

  返回存储在高斯混合模型  训练数据中的训练样本数。

- [`read_class_gmm`]

  从文件中读取高斯混合模型。

- [`read_samples_class_gmm`]

  从文件中读取高斯混合模型的训练数据。

- [`select_feature_set_gmm`]

  从一组特征中选择最佳组合以对提供的数据进行分类。

- [`serialize_class_gmm`]

  序列化高斯混合模型 。

- [`train_class_gmm`]

  训练高斯混合模型。

- [`write_class_gmm`]

  将高斯混合模型写入文件。

- [`write_samples_class_gmm`]

  将高斯混合模型的训练数据写入文件。

## K近邻 K-Nearest Neighbors

- [`add_class_train_data_knn`]

  将训练数据添加到 k 最近邻  分类器。

- [`add_sample_class_knn`]

  将样本添加到 k 最近邻  分类器。

- [`classify_class_knn`]

  搜索给定特征向量的下一个邻居。

- [`clear_class_knn`]

  清除 k-NN 分类器。

- [`create_class_knn`]

  创建一个 k 最近邻  分类器。

- [`deserialize_class_knn`]

  反序列化序列化的 k-NN 分类器。

- [`get_class_train_data_knn`]

  获取 k 最近邻  分类器的训练数据。

- [`get_params_class_knn`]

  获取 k-NN 分类的参数。

- [`get_sample_class_knn`]

  从 k 最近邻  分类器的训练数据中返回训练样本。

- [`get_sample_num_class_knn`]

  返回存储在 k 最近邻  分类器训练数据中的训练样本数。

- [`read_class_knn`]

  从文件中读取 k-NN 分类器。

- [`select_feature_set_knn`]

  从一组特征中选择一个最优子集来解决某个分类问题。

- [`serialize_class_knn`]

  序列化 k-NN 分类器。

- [`set_params_class_knn`]

  为 k-NN 分类设置参数。

- [`train_class_knn`]

  为 k-NN 分类器创建搜索树。

- [`write_class_knn`]

  将 k-NN 分类器保存在文件中。

## 查找表 Look-Up Table

- [`clear_class_lut`]

  清除查找表分类器。

- [`create_class_lut_gmm`]

  使用高斯混合模型创建查找表以对字节图像进行分类。

- [`create_class_lut_knn`]

  使用 k 最近邻分类器  创建查找表以对字节图像进行分类。

- [`create_class_lut_mlp`]

  使用多层感知器创建查找表以对字节图像进行分类。

- [`create_class_lut_svm`]

  使用支持向量机创建查找表以对字节图像进行分类。

##  杂项 Misc

- [`add_sample_class_train_data`]

  将训练样本添加到训练数据中。

- [`clear_class_train_data`]

  清除分类器的训练数据。

- [`create_class_train_data`]

  为分类器的训练数据创建句柄。

- [`deserialize_class_train_data`]

  反序列化分类器的序列化训练数据。

- [`get_sample_class_train_data`]

  从训练数据中返回训练样本。

- [`get_sample_num_class_train_data`]

  返回训练数据中存储的训练样本数。

- [`read_class_train_data`]

  从文件中读取分类器的训练数据。

- [`select_sub_feature_class_train_data`]

  从训练数据中选择某些特征来创建包含较少特征的训练数据。

- [`serialize_class_train_data`]

  序列化分类器的训练数据。

- [`set_feature_lengths_class_train_data`]

  在训练数据中定义子特征。

- [`write_class_train_data`]

  将分类器的训练数据保存在文件中。

## 神经网络 Neural Nets

- [`add_class_train_data_mlp`]

  将训练数据添加到多层感知器 。

- [`add_sample_class_mlp`]

  将训练样本添加到多层感知器的训练数据中。

- [`classify_class_mlp`]

  通过多层感知器计算特征向量的类别。

- [`clear_class_mlp`]

  清除多层感知器。

- [`clear_samples_class_mlp`]

  清除多层感知器的训练数据。

- [`create_class_mlp`]

  创建用于分类或回归的多层感知器。

- [`deserialize_class_mlp`]

  反序列化序列化的多层感知器。

- [`evaluate_class_mlp`]

  计算多层感知器对特征向量的评估。

- [`get_class_train_data_mlp`]

  获取多层感知器  的训练数据。

- [`get_params_class_mlp`]

  返回多层感知器的参数。

- [`get_prep_info_class_mlp`]

  计算多层感知器的预处理特征向量的信息内容。

- [`get_regularization_params_class_mlp`]

  返回多层感知器的正则化参数。

- [`get_rejection_params_class_mlp`]

  获取拒绝类的参数。

- [`get_sample_class_mlp`]

  从多层感知器的训练数据中返回训练样本。

- [`get_sample_num_class_mlp`]

  返回存储在多层感知器训练数据中的训练样本数。

- [`read_class_mlp`]

  从文件中读取多层感知器。

- [`read_samples_class_mlp`]

  从文件中读取多层感知器的训练数据。

- [`select_feature_set_mlp`]

  选择最佳的特征组合来对提供的数据进行分类。

- [`serialize_class_mlp`]

  序列化多层感知器 。

- [`set_regularization_params_class_mlp`]

  设置多层感知器的正则化参数。

- [`set_rejection_params_class_mlp`]

  设置拒绝类的参数。

- [`train_class_mlp`]

  训练多层感知器。

- [`write_class_mlp`]

  将多层感知器写入文件。

- [`write_samples_class_mlp`]

  将多层感知器的训练数据写入文件。

## 支持向量机 Support Vector Machines

- [`add_class_train_data_svm`]

  将训练数据添加到支持向量机 。

- [`add_sample_class_svm`]

  将训练样本添加到支持向量机的训练数据中。

- [`classify_class_svm`]

  通过支持向量机对特征向量进行分类。

- [`clear_class_svm`]

  清除支持向量机。

- [`clear_samples_class_svm`]

  清除支持向量机的训练数据。

- [`create_class_svm`]

  创建用于模式分类的支持向量机。

- [`deserialize_class_svm`]

  反序列化序列化支持向量机 。

- [`evaluate_class_svm`]

  通过支持向量机评估特征向量。

- [`get_class_train_data_svm`]

  获取支持向量机  的训练数据。

- [`get_params_class_svm`]

  返回支持向量机的参数。

- [`get_prep_info_class_svm`]

  计算支持向量机预处理特征向量的信息内容

- [`get_sample_class_svm`]

  从支持向量机的训练数据中返回训练样本。

- [`get_sample_num_class_svm`]

  返回存储在支持向量机训练数据中的训练样本数。

- [`get_support_vector_class_svm`]

  从经过训练的支持向量机返回支持向量的索引。

- [`get_support_vector_num_class_svm`]

  返回支持向量机的支持向量数。

- [`read_class_svm`]

  从文件中读取支持向量机。

- [`read_samples_class_svm`]

  从文件中读取支持向量机的训练数据。

- [`reduce_class_svm`]

  通过简化的支持向量机来近似经过训练的支持向量机，以实现更快的分类。

- [`select_feature_set_svm`]

  选择最佳的特征组合来对提供的数据进行分类。

- [`serialize_class_svm`]

  序列化支持向量机 。

- [`train_class_svm`]

  训练支持向量机。

- [`write_class_svm`]

  将支持向量机写入文件。

- [`write_samples_class_svm`]

  将支持向量机的训练数据写入文件。