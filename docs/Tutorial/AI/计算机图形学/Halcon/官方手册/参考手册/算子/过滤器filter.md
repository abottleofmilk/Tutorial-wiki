## 算术 Arithmetic

- [`abs_diff_image`]

  计算两幅图像的绝对差值。

- [`abs_image`]

  计算图像的绝对值（模数）。

- [`acos_image`]

  计算图像的反余弦。

- [`add_image`]

  添加两个图像。

- [`asin_image`]

  计算图像的反正弦值。

- [`atan2_image`]

  计算两个图像的反正切。

- [`atan_image`]

  计算图像的反正切。

- [`cos_image`]

  计算图像的余弦。

- [`div_image`]

  划分两个图像。

- [`exp_image`]

  计算图像的指数。

- [`gamma_image`]

  执行图像的伽玛编码或解码。

- [`invert_image`]

  反转图像。

- [`log_image`]

  计算图像的对数。

- [`max_image`]

  逐像素计算两个图像的最大值。

- [`min_image`]

  逐像素计算两幅图像中的最小值。

- [`mult_image`]

  将两个图像相乘。

- [`pow_image`]

  将形象提升为力量。

- [`scale_image`]

  缩放图像的灰度值。

- [`sin_image`]

  计算图像的正弦。

- [`sqrt_image`]

  计算图像的平方根。

- [`sub_image`]

  减去两个图像。

- [`tan_image`]

  计算图像的正切。

## 位 Bit

- [`bit_and`]

  输入图像的所有像素的逐位与运算。

- [`bit_lshift`]

  图像所有像素的左移。

- [`bit_mask`]

  使用位掩码的每个像素的逻辑“与”。

- [`bit_not`]

  补充像素的所有位。

- [`bit_or`]

  输入图像的所有像素的逐位或。

- [`bit_rshift`]

  图像所有像素的右移。

- [`bit_slice`]

  从像素中提取一点。

- [`bit_xor`]

  输入图像的所有像素的逐位异或。

## 颜色 Color

- [`apply_color_trans_lut`]

  使用预先生成的查找表进行色彩空间转换。

- [`cfa_to_rgb`]

  将单通道滤色器阵列图像转换为 RGB 图像。

- [`clear_color_trans_lut`]

  释放颜色空间转换所需的查找表。

- [`create_color_trans_lut`]

  创建用于将图像从 RGB 颜色空间转换为任意颜色空间的查找表。

- [`gen_principal_comp_trans`]

  计算多通道图像主成分分析的变换矩阵。

- [`linear_trans_color`]

  计算多通道图像颜色值的仿射变换。

- [`principal_comp`]

  计算多通道图像的主要成分。

- [`rgb1_to_gray`]

  将 RGB 图像转换为灰度图像。

- [`rgb3_to_gray`]

  将 RGB 图像转换为灰度图像。

- [`trans_from_rgb`]

  将图像从 RGB 颜色空间转换为任意颜色空间。

- [`trans_to_rgb`]

  将图像从任意颜色空间转换为 RGB 颜色空间。

## 边缘 edges

- [`close_edges`]

  使用边缘幅度图像关闭边缘间隙。

- [`close_edges_length`]

  使用边缘幅度图像关闭边缘间隙。

- [`derivate_gauss`]

  将图像与高斯导数进行卷积。

- [`diff_of_gauss`]

  近似 LoG 算子（高斯拉普拉斯）。

- [`edges_color`]

  使用 Canny、Deriche 或 Shen 过滤器提取颜色边缘。

- [`edges_color_sub_pix`]

  使用 Deriche、Shen 或 Canny 过滤器提取亚像素精确的颜色边缘。

- [`edges_image`]

  使用 Deriche、Lanser、Shen 或 Canny 过滤器提取边缘。

- [`edges_sub_pix`]

  使用 Deriche、Lanser、Shen 或 Canny 过滤器提取亚像素级精确边缘。

- [`frei_amp`]

  使用 Frei-Chen 运算符检测边缘（振幅）。

- [`frei_dir`]

  使用 Frei-Chen 运算符检测边缘（振幅和方向）。

- [`highpass_image`]

  从图像中提取高频成分。

- [`info_edges`]

  返回 中滤波器的滤波器系数。[`edges_image`]

- [`kirsch_amp`]

  使用 Kirsch 运算符检测边缘（振幅）。

- [`kirsch_dir`]

  使用 Kirsch 算子检测边缘（振幅和方向）。

- [`laplace`]

  使用有限差分计算拉普拉斯算子。

- [`laplace_of_gauss`]

  LoG 算子（高斯拉普拉斯）。

- [`prewitt_amp`]

  使用 Prewitt 运算符检测边缘（振幅）。

- [`prewitt_dir`]

  使用 Prewitt 运算符检测边缘（振幅和方向）。

- [`roberts`]

  使用 Roberts 过滤器检测边缘。

- [`robinson_amp`]

  使用 Robinson 运算符检测边缘（振幅）。

- [`robinson_dir`]

  使用 Robinson 运算符检测边缘（振幅和方向）。

- [`sobel_amp`]

  使用 Sobel 运算符检测边缘（振幅）。

- [`sobel_dir`]

  使用 Sobel 运算符检测边缘（振幅和方向）。

## 强化 Enhancement

- [`coherence_enhancing_diff`]

  执行图像的连贯性增强扩散。

- [`emphasize`]

  增强图像的对比度。

- [`equ_histo_image`]

  图像的直方图线性化

- [`illuminate`]

  照亮图像。

- [`mean_curvature_flow`]

  将平均曲率流应用于图像。

- [`scale_image_max`]

  *最大灰度值分布在0*到*255 的*取值范围内 。

- [`shock_filter`]

  对图像应用震动过滤器。

## 快速傅里叶变换 FFT

- [`convol_fft`]

  在频域中使用滤波器对图像进行卷积。

- [`convol_gabor`]

  在频域中使用 Gabor 滤波器对图像进行卷积。

- [`correlation_fft`]

  计算两个图像在频域中的相关性。

- [`deserialize_fft_optimization_data`]

  反序列化 FFT 速度优化数据。

- [`energy_gabor`]

  计算双通道图像的能量。

- [`fft_generic`]

  计算图像的快速傅立叶变换。

- [`fft_image`]

  计算图像的快速傅立叶变换。

- [`fft_image_inv`]

  计算图像的快速傅里叶逆变换。

- [`gen_bandfilter`]

  生成一个理想的带状滤波器。

- [`gen_bandpass`]

  生成一个理想的带通滤波器。

- [`gen_derivative_filter`]

  在频域中生成导数滤波器。

- [`gen_filter_mask`]

  将空间域中的过滤器掩码存储为真实图像。

- [`gen_gabor`]

  生成 Gabor 滤波器。

- [`gen_gauss_filter`]

  在频域中生成高斯滤波器。

- [`gen_highpass`]

  生成一个理想的高通滤波器。

- [`gen_lowpass`]

  生成一个理想的低通滤波器。

- [`gen_mean_filter`]

  在频域中生成均值滤波器。

- [`gen_sin_bandpass`]

  生成具有正弦形状的带通滤波器。

- [`gen_std_bandpass`]

  生成具有高斯或正弦形状的带通滤波器。

- [`optimize_fft_speed`]

  优化 FFT 的运行时间。

- [`optimize_rft_speed`]

  优化实值 FFT 的运行时间。

- [`phase_correlation_fft`]

  计算频域中两个图像的相位相关性。

- [`phase_deg`]

  以度为单位返回复杂图像的相位。

- [`phase_rad`]

  以弧度返回复杂图像的相位。

- [`power_byte`]

  返回复杂图像的功率谱。

- [`power_ln`]

  返回复杂图像的功率谱。

- [`power_real`]

  返回复杂图像的功率谱。

- [`read_fft_optimization_data`]

  从文件加载 FFT 速度优化数据。

- [`rft_generic`]

  计算图像的实值快速傅里叶变换。

- [`serialize_fft_optimization_data`]

  序列化 FFT 速度优化数据。

- [`write_fft_optimization_data`]

  将 FFT 速度优化数据存储在文件中。

## 几何变换 Geometric Transformations

- [`affine_trans_image`]

  对图像应用任意仿射二维变换。

- [`affine_trans_image_size`]

  对图像应用任意仿射二维变换并指定输出图像大小。

- [`convert_map_type`]

  将图像地图转换为其他地图类型。

- [`map_image`]

  对图像应用一般变换。

- [`mirror_image`]

  镜像图像。

- [`polar_trans_image_ext`]

  将图像中的环形弧转换为极坐标。

- [`polar_trans_image_inv`]

  将极坐标中的图像转换回笛卡尔坐标

- [`projective_trans_image`]

  对图像应用投影变换。

- [`projective_trans_image_size`]

  对图像应用投影变换并指定输出图像大小。

- [`rotate_image`]

  围绕其中心旋转图像。

- [`zoom_image_factor`]

  按给定因子缩放图像。

- [`zoom_image_size`]

  将图像缩放到给定大小。

## 修复 Inpainting

- [`harmonic_interpolation`]

  对图像区域执行谐波插值。

- [`inpainting_aniso`]

  通过各向异性扩散进行修复。

- [`inpainting_ced`]

  通过连贯性增强扩散进行修复。

- [`inpainting_ct`]

  通过相干传输执行修复。

- [`inpainting_mcf`]

  通过平滑水平线来执行修复。

- [`inpainting_texture`]

  通过纹理传播执行修复。

## 线条 Lines

- [`bandpass_image`]

  使用带通滤波器进行边缘提取。

- [`lines_color`]

  检测彩色线条及其宽度。

- [`lines_facet`]

  使用小平面模型检测线。

- [`lines_gauss`]

  检测线条及其宽度。

## 匹配 Match

- [`exhaustive_match`]

  模板和图像的匹配。

- [`exhaustive_match_mg`]

  在分辨率金字塔中匹配模板和图像。

- [`gen_gauss_pyramid`]

  计算高斯金字塔。

- [`monotony`]

  计算单调操作。

## 杂项 Misc

- [`convol_image`]

  Calculate the correlation between an image and an arbitrary filter mask

- [`deviation_n`]

  Calculate standard deviation over several channels.

- [`expand_domain_gray`]

  Expand the domain of an image and set the gray values in the expanded domain.

- [`gray_inside`]

  Calculate the lowest possible gray value on an arbitrary path to the image border for each point in the image.

- [`gray_skeleton`]

  Thinning of gray value images.

- [`lut_trans`]

  Transform an image with a gray-value look-up-table

- [`symmetry`]

  Symmetry of gray values along a row.

- [`topographic_sketch`]

  Compute the topographic primal sketch of an image.

##  噪音 Noise

- [`add_noise_distribution`]

  为图像添加噪点。

- [`add_noise_white`]

  为图像添加噪点。

- [`gauss_distribution`]

  生成高斯噪声分布。

- [`noise_distribution_mean`]

  确定图像的噪声分布。

- [`sp_distribution`]

  生成椒盐噪声分布。

##  光流 Optical Flow

- [`derivate_vector_field`]

  将矢量场与高斯导数进行卷积。

- [`optical_flow_mg`]

  计算两个图像之间的光流。

- [`unwarp_image_vector_field`]

  使用矢量场反扭曲图像。

- [`vector_field_length`]

  计算矢量场的矢量长度。

## 点 Points

- [`corner_response`]

  搜索图像中的角点。

- [`dots_image`]

  增强图像中的圆点。

- [`points_foerstner`]

  使用 Förstner 运算符检测兴趣点。

- [`points_harris`]

  使用 Harris 运算符检测兴趣点。

- [`points_harris_binomial`]

  使用 Harris 算子的二项式近似检测兴趣点。

- [`points_lepetit`]

  使用 Lepetit 运算符检测兴趣点。

- [`points_sojka`]

  使用 Sojka 运算符查找角点。

## 场景流程 Scene Flow

- [`scene_flow_calib`]

  计算两个立体图像对之间的校准场景流。

- [`scene_flow_uncalib`]

  计算两个立体图像对之间的未校准场景流。

## 

- [`anisotropic_diffusion`]

  执行图像的各向异性扩散。

- [`bilateral_filter`]

  图像的双边滤波。

- [`binomial_filter`]

  使用二项式滤波器平滑图像。

- [`eliminate_min_max`]

  平滑空间域中的图像以抑制噪声。

- [`eliminate_sp`]

  用平均值替换阈值之外的值。

- [`fill_interlace`]

  插值 2 个视频半图像。

- [`gauss_filter`]

  使用离散高斯函数平滑。

- [`guided_filter`]

  图像的引导过滤。

- [`info_smooth`]

  有关平滑滤波器的信息。[`smooth_image`]

- [`isotropic_diffusion`]

  执行图像的各向同性扩散。

- [`mean_image`]

  通过平均平滑。

- [`mean_n`]

  多个通道的平均灰度值。

- [`mean_sp`]

  抑制椒盐噪声。

- [`median_image`]

  计算具有各种掩码的中值滤波器。

- [`median_rect`]

  计算具有矩形掩码的中值滤波器。

- [`median_separate`]

  使用矩形掩码分离中值过滤。

- [`median_weighted`]

  具有不同秩掩码的加权中值过滤。

- [`midrange_image`]

  计算任何掩码内的最大值和最小值的平均值。

- [`rank_image`]

  计算具有任意掩码的等级过滤器。

- [`rank_n`]

  从多个通道返回具有给定等级的灰度值。

- [`rank_rect`]

  计算带有矩形掩码的等级过滤器。

- [`sigma_image`]

  使用 sigma 滤波器进行非线性平滑。

- [`smooth_image`]

  使用各种过滤器平滑图像。

- [`trimmed_mean`]

  使用任意等级掩码平滑图像。

## 平滑 Smoothing

- [`anisotropic_diffusion`]

  执行图像的各向异性扩散。

- [`bilateral_filter`]

  图像的双边滤波。

- [`binomial_filter`]

  使用二项式滤波器平滑图像。

- [`eliminate_min_max`]

  平滑空间域中的图像以抑制噪声。

- [`eliminate_sp`]

  用平均值替换阈值之外的值。

- [`fill_interlace`]

  插值 2 个视频半图像。

- [`gauss_filter`]

  使用离散高斯函数平滑。

- [`guided_filter`]

  图像的引导过滤。

- [`info_smooth`]

  有关平滑滤波器的信息。[`smooth_image`]

- [`isotropic_diffusion`]

  执行图像的各向同性扩散。

- [`mean_image`]

  通过平均平滑。

- [`mean_n`]

  多个通道的平均灰度值。

- [`mean_sp`]

  抑制椒盐噪声。

- [`median_image`]

  计算具有各种掩码的中值滤波器。

- [`median_rect`]

  计算具有矩形掩码的中值滤波器。

- [`median_separate`]

  使用矩形掩码分离中值过滤。

- [`median_weighted`]

  具有不同秩掩码的加权中值过滤。

- [`midrange_image`]

  计算任何掩码内的最大值和最小值的平均值。

- [`rank_image`]

  计算具有任意掩码的等级过滤器。

- [`rank_n`]

  从多个通道返回具有给定等级的灰度值。

- [`rank_rect`]

  计算带有矩形掩码的等级过滤器。

- [`sigma_image`]

  使用 sigma 滤波器进行非线性平滑。

- [`smooth_image`]

  使用各种过滤器平滑图像。

- [`trimmed_mean`]

  使用任意等级掩码平滑图像。

## 质地检验 Texture Inspection

- [`deviation_image`]

  计算矩形窗口内灰度值的标准偏差。

- [`entropy_image`]

  计算矩形窗口内灰度值的熵。

- [`texture_laws`]

  使用 Laws 纹理过滤器过滤图像。

##  维纳滤波器 Wiener Filter

- [`gen_psf_defocus`]

  生成均匀散焦模糊的脉冲响应。

- [`gen_psf_motion`]

  生成（线性）运动模糊的脉冲响应。

- [`simulate_defocus`]

  模拟图像的均匀散焦模糊。

- [`simulate_motion`]

  模拟（线性）运动模糊。

- [`wiener_filter`]

  通过维纳滤波进行图像复原。

- [`wiener_filter_ni`]

  通过维纳滤波进行图像复原。
