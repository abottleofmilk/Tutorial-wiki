## 分类 Classification

- [`add_samples_image_class_gmm`]

  将图像中的训练样本添加到高斯混合模型的训练数据中。

- [`add_samples_image_class_knn`]

  将图像中的训练样本添加到 k 最近邻分类器的训练数据中。

- [`add_samples_image_class_mlp`]

  将图像中的训练样本添加到多层感知器的训练数据中。

- [`add_samples_image_class_svm`]

  将图像中的训练样本添加到支持向量机的训练数据中。

- [`class_2dim_sup`]

  使用二维像素分类分割图像。

- [`class_2dim_unsup`]

  通过聚类分割两个图像。

- [`class_ndim_norm`]

  使用超球体或超立方体对像素进行分类。

- [`classify_image_class_gmm`]

  使用高斯混合模型对图像进行分类。

- [`classify_image_class_knn`]

  使用 k 最近邻分类器对图像进行分类。

- [`classify_image_class_lut`]

  使用查找表对字节图像进行分类。

- [`classify_image_class_mlp`]

  使用多层感知器对图像进行分类。

- [`classify_image_class_svm`]

  使用支持向量机对图像进行分类。

- [`learn_ndim_norm`]

  为 构建类。[`class_ndim_norm`]

## 边缘 edges

- [`detect_edge_segments`]

  检测直边段。

- [`hysteresis_threshold`]

  对图像执行滞后阈值操作。

- [`nonmax_suppression_amp`]

  抑制边缘上的非最大点。

- [`nonmax_suppression_dir`]

  使用方向图像抑制边缘上的非最大点。

## 最稳定的极值区域 Maximally Stable Extremal Regions

[`segment_image_mser`]

使用最大稳定极值区域  分割图像。

## 区域增长 Region Growing

- [`expand_gray`]

  填充区域之间的间隙（取决于灰度值或颜色）或拆分重叠区域。

- [`expand_gray_ref`]

  填充区域之间的间隙（取决于灰度值或颜色）或拆分重叠区域。

- [`regiongrowing`]

  使用 regiongrowing 分割图像。

- [`regiongrowing_mean`]

  使用平均灰度值执行区域增长。

- [`regiongrowing_n`]

  使用 regiongrowing 对多通道图像进行图像分割。

## 阈值 Threshold

- [`auto_threshold`]

  使用从直方图确定的阈值对图像进行分割。

- [`binary_threshold`]

  使用二进制阈值分割图像。

- [`char_threshold`]

  执行阈值分割以提取字符。

- [`check_difference`]

  逐个像素地比较两个图像。

- [`dual_threshold`]

  签名图像的阈值运算符。

- [`dyn_threshold`]

  使用局部阈值分割图像。

- [`fast_threshold`]

  使用全局阈值对图像进行快速阈值处理。

- [`histo_to_thresh`]

  从直方图中确定灰度值阈值。

- [`local_threshold`]

  使用局部阈值分割图像。

- [`threshold`]

  使用全局阈值分割图像。

- [`threshold_sub_pix`]

  以亚像素精度从图像中提取平交道口。

- [`var_threshold`]

  通过局部均值和标准差分析对图像进行阈值处理。

- [`zero_crossing`]

  从图像中提取过零点。

- [`zero_crossing_sub_pix`]

  以亚像素精度从图像中提取零交叉点。

##  地形 Topography

- [`critical_points_sub_pix`]

  图像中关键点的亚像素精确检测。

- [`local_max`]

  检测图像中的所有局部最大值。

- [`local_max_sub_pix`]

  图像中局部最大值的亚像素精确检测。

- [`local_min`]

  检测图像中的所有局部最小值。

- [`local_min_sub_pix`]

  图像中局部最小值的亚像素精确检测。

- [`lowlands`]

  检测所有灰度值低地。

- [`lowlands_center`]

  检测所有灰度值低地的中心。

- [`plateaus`]

  检测所有灰度值平台。

- [`plateaus_center`]

  检测所有灰度值平台的中心。

- [`pouring`]

  通过在图像上“倒水”来分割图像。

- [`saddle_points_sub_pix`]

  图像中鞍点的亚像素精确检测。

- [`watersheds`]

  从图像中提取分水岭和盆地。

- [`watersheds_marker`]

  提取流域并根据标记组合流域。

- [`watersheds_threshold`]

  使用阈值从图像中提取流域盆地。