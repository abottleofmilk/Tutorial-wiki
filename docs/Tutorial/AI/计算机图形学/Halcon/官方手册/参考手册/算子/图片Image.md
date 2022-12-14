## 访问 Access

- [`get_grayval`]

  访问图像对象的灰度值。

- [`get_grayval_contour_xld`]

  返回图像在 XLD 轮廓位置的灰度值。

- [`get_grayval_interpolated`]

  在行和列的元组给定的位置返回图像的灰度值。

- [`get_image_pointer1`]

  访问通道的指针。

- [`get_image_pointer1_rect`]

  访问图像数据指针和输入图像域的最小矩形内的图像数据。

- [`get_image_pointer3`]

  访问彩色图像的指针。

- [`get_image_size`]

  返回图像的大小。

- [`get_image_time`]

  创建图像的请求时间。

- [`get_image_type`]

  返回图像的类型。

##  获取 Acquisition

- [`close_framegrabber`]

  关闭指定的图像采集设备。

- [`get_framegrabber_callback`]

  图像采集设备的查询回调函数。

- [`get_framegrabber_lut`]

  查询图像采集设备的查找表。

- [`get_framegrabber_param`]

  查询图像采集设备的具体参数。

- [`grab_data`]

  从指定的图像采集设备同步抓取图像和预处理图像数据。

- [`grab_data_async`]

  从指定的图像采集设备异步抓取图像和预处理图像数据。

- [`grab_image`]

  从指定的图像采集设备同步抓取图像。

- [`grab_image_async`]

  从指定的图像采集设备异步抓取图像。

- [`grab_image_start`]

  从指定的图像采集设备开始异步抓取。

- [`info_framegrabber`]

  查询指定图像采集接口的信息。

- [`open_framegrabber`]

  打开并配置图像采集设备。

- [`set_framegrabber_callback`]

  为图像采集设备注册回调函数。

- [`set_framegrabber_lut`]

  设置图像采集设备的查找表。

- [`set_framegrabber_param`]

  设置图像采集设备的具体参数。

## 渠道 channel

- [`access_channel`]

  访问多通道图像的通道。

- [`append_channel`]

  将附加矩阵（通道）附加到图像。

- [`channels_to_image`]

  将单通道图像转换为多通道图像

- [`compose2`]

  将两个图像转换为双通道图像。

- [`compose3`]

  将 3 张图像转换为三通道图像。

- [`compose4`]

  将 4 张图像转换为四通道图像。

- [`compose5`]

  将 5 张图像转换为五通道图像。

- [`compose6`]

  将 6 张图像转换为六通道图像。

- [`compose7`]

  将 7 张图像转换为七通道图像。

- [`count_channels`]

  计算图像的通道数。

- [`decompose2`]

  将双通道图像转换为两个图像。

- [`decompose3`]

  将三通道图像转换为三幅图像。

- [`decompose4`]

  将四通道图像转换为四张图像。

- [`decompose5`]

  将五通道图像转换为五幅图像。

- [`decompose6`]

  将六通道图像转换为六幅图像。

- [`decompose7`]

  将七通道图像转换为七幅图像。

- [`image_to_channels`]

  将多通道图像转换为单通道图像

## 创建 Creation

- [`copy_image`]

  复制图像并为其分配新内存。

- [`gen_image1`]

  从指向像素的指针创建图像。

- [`gen_image1_extern`]

  使用存储管理从像素上的指针创建图像。

- [`gen_image1_rect`]

  从像素上的指针创建具有矩形域的图像（使用存储管理）。

- [`gen_image3`]

  从指向像素（红/绿/蓝）的三个指针创建图像。

- [`gen_image3_extern`]

  使用存储管理从像素上的三个指针创建三通道图像。

- [`gen_image_const`]

  创建具有恒定灰度值的图像。

- [`gen_image_gray_ramp`]

  创建一个灰度值渐变。

- [`gen_image_interleaved`]

  从指向交错像素的指针创建三通道图像。

- [`gen_image_proto`]

  创建具有指定常量灰度值的图像。

- [`gen_image_surface_first_order`]

  使用一阶多项式创建倾斜的灰色曲面。

- [`gen_image_surface_second_order`]

  使用二阶多项式创建一个灰色曲面。

- [`interleave_channels`]

  从多通道图像创建交错图像。

- [`region_to_bin`]

  将区域转换为二进制字节图像。

- [`region_to_label`]

  将区域转换为标签图像。

- [`region_to_mean`]

  用平均灰度值绘制区域。

##  领域 Domain

- [`add_channels`]

  向区域添加灰度值。

- [`change_domain`]

  更改图像的定义域。

- [`full_domain`]

  将图像的域扩展到最大。

- [`get_domain`]

  获取图像的域。

- [`rectangle1_domain`]

  将图像的域缩小为矩形。

- [`reduce_domain`]

  缩小图像的域。

## 特性 Features

- [`area_center_gray`]

  计算灰度值图像中区域的面积和重心。

- [`cooc_feature_image`]

  计算共生矩阵并导出其灰度值特征。

- [`cooc_feature_matrix`]

  从共现矩阵计算灰度值特征。

- [`elliptic_axis_gray`]

  计算灰度值图像中区域的方向和主轴。

- [`entropy_gray`]

  确定图像的熵和各向异性。

- [`estimate_noise`]

  估计单个图像的图像噪声。

- [`fit_surface_first_order`]

  通过一阶曲面（平面）计算灰度值矩和近似值。

- [`fit_surface_second_order`]

  通过二阶曲面计算灰度值矩和近似值。

- [`fuzzy_entropy`]

  确定区域的模糊熵。

- [`fuzzy_perimeter`]

  计算区域的模糊周长。

- [`gen_cooc_matrix`]

  计算图像中某个区域的共现矩阵。

- [`gray_features`]

  计算一组区域的灰度值特征。

- [`gray_histo`]

  计算灰度值分布。

- [`gray_histo_abs`]

  计算灰度值分布。

- [`gray_histo_range`]

  计算单通道图像在一定灰度值范围内的灰度值分布。

- [`gray_projections`]

  计算水平和垂直灰度值投影。

- [`histo_2dim`]

  计算双通道灰度值图像的直方图。

- [`intensity`]

  计算灰度值的均值和偏差。

- [`min_max_gray`]

  确定区域内的最小和最大灰度值。

- [`moments_gray_plane`]

  通过平面计算灰度值矩和近似值。

- [`plane_deviation`]

  计算灰度值与近似图像平面的偏差。

- [`select_gray`]

  根据灰度值特征选择区域。

- [`shape_histo_all`]

  确定沿所有阈值的特征直方图。

- [`shape_histo_point`]

  确定沿所有阈值的特征直方图。

## 格式 Format

- [`change_format`]

  更改图像大小。

- [`crop_domain`]

  切出定义的灰度值。

- [`crop_domain_rel`]

  裁剪出一个与域相关的图像区域。

- [`crop_part`]

  裁剪出一个或多个矩形图像区域。

- [`crop_rectangle1`]

  裁剪出一个或多个矩形图像区域。

- [`tile_channels`]

  将多个图像平铺成一个大图像。

- [`tile_images`]

  将多个图像对象平铺成一个大图像。

- [`tile_images_offset`]

  将多个图像对象平铺成具有显式定位信息的大图像。

## 操纵  Manipulation

- [`overpaint_gray`]

  覆盖图像的灰度值。

- [`overpaint_region`]

  覆盖图像中的区域。

- [`paint_gray`]

  将一幅图像的灰度值绘制到另一幅图像中。

- [`paint_region`]

  将区域绘制成图像。

- [`paint_xld`]

  将 XLD 对象绘制成图像。

- [`set_grayval`]

  在图像中设置单个灰度值。

## 类型转换 Type Conversion

- [`complex_to_real`]

  将复数图像转换为两个实数图像。

- [`convert_image_type`]

  转换图像的类型。

- [`real_to_complex`]

  将两个实图像转换为复图像。

- [`real_to_vector_field`]

  将两个实值图像转换为矢量场图像。

- [`vector_field_to_real`]

  将矢量场图像转换为两个实值图像。