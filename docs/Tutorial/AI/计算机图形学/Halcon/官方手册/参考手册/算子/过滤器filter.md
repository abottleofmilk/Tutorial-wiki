## 算术

- [`abs_diff_image`](abs_diff_image.html)

  计算两幅图像的绝对差值。

- [`abs_image`](abs_image.html)

  计算图像的绝对值（模数）。

- [`acos_image`](acos_image.html)

  计算图像的反余弦。

- [`add_image`](add_image.html)

  添加两个图像。

- [`asin_image`](asin_image.html)

  计算图像的反正弦值。

- [`atan2_image`](atan2_image.html)

  计算两个图像的反正切。

- [`atan_image`](atan_image.html)

  计算图像的反正切。

- [`cos_image`](cos_image.html)

  计算图像的余弦。

- [`div_image`](div_image.html)

  划分两个图像。

- [`exp_image`](exp_image.html)

  计算图像的指数。

- [`gamma_image`](gamma_image.html)

  执行图像的伽玛编码或解码。

- [`invert_image`](invert_image.html)

  反转图像。

- [`log_image`](log_image.html)

  计算图像的对数。

- [`max_image`](max_image.html)

  逐像素计算两个图像的最大值。

- [`min_image`](min_image.html)

  逐像素计算两幅图像中的最小值。

- [`mult_image`](mult_image.html)

  将两个图像相乘。

- [`pow_image`](pow_image.html)

  将形象提升为力量。

- [`scale_image`](scale_image.html)

  缩放图像的灰度值。

- [`sin_image`](sin_image.html)

  计算图像的正弦。

- [`sqrt_image`](sqrt_image.html)

  计算图像的平方根。

- [`sub_image`](sub_image.html)

  减去两个图像。

- [`tan_image`](tan_image.html)

  计算图像的正切。

## 位 Bit

- [`bit_and`](bit_and.html)

  输入图像的所有像素的逐位与运算。

- [`bit_lshift`](bit_lshift.html)

  图像所有像素的左移。

- [`bit_mask`](bit_mask.html)

  使用位掩码的每个像素的逻辑“与”。

- [`bit_not`](bit_not.html)

  补充像素的所有位。

- [`bit_or`](bit_or.html)

  输入图像的所有像素的逐位或。

- [`bit_rshift`](bit_rshift.html)

  图像所有像素的右移。

- [`bit_slice`](bit_slice.html)

  从像素中提取一点。

- [`bit_xor`](bit_xor.html)

  输入图像的所有像素的逐位异或。

## 颜色 Color

- [`apply_color_trans_lut`](apply_color_trans_lut.html)

  使用预先生成的查找表进行色彩空间转换。

- [`cfa_to_rgb`](cfa_to_rgb.html)

  将单通道滤色器阵列图像转换为 RGB 图像。

- [`clear_color_trans_lut`](clear_color_trans_lut.html)

  释放颜色空间转换所需的查找表。

- [`create_color_trans_lut`](create_color_trans_lut.html)

  创建用于将图像从 RGB 颜色空间转换为任意颜色空间的查找表。

- [`gen_principal_comp_trans`](gen_principal_comp_trans.html)

  计算多通道图像主成分分析的变换矩阵。

- [`linear_trans_color`](linear_trans_color.html)

  计算多通道图像颜色值的仿射变换。

- [`principal_comp`](principal_comp.html)

  计算多通道图像的主要成分。

- [`rgb1_to_gray`](rgb1_to_gray.html)

  将 RGB 图像转换为灰度图像。

- [`rgb3_to_gray`](rgb3_to_gray.html)

  将 RGB 图像转换为灰度图像。

- [`trans_from_rgb`](trans_from_rgb.html)

  将图像从 RGB 颜色空间转换为任意颜色空间。

- [`trans_to_rgb`](trans_to_rgb.html)

  将图像从任意颜色空间转换为 RGB 颜色空间。

## 边缘 edges

- [`close_edges`](close_edges.html)

  使用边缘幅度图像关闭边缘间隙。

- [`close_edges_length`](close_edges_length.html)

  使用边缘幅度图像关闭边缘间隙。

- [`derivate_gauss`](derivate_gauss.html)

  将图像与高斯导数进行卷积。

- [`diff_of_gauss`](diff_of_gauss.html)

  近似 LoG 算子（高斯拉普拉斯）。

- [`edges_color`](edges_color.html)

  使用 Canny、Deriche 或 Shen 过滤器提取颜色边缘。

- [`edges_color_sub_pix`](edges_color_sub_pix.html)

  使用 Deriche、Shen 或 Canny 过滤器提取亚像素精确的颜色边缘。

- [`edges_image`](edges_image.html)

  使用 Deriche、Lanser、Shen 或 Canny 过滤器提取边缘。

- [`edges_sub_pix`](edges_sub_pix.html)

  使用 Deriche、Lanser、Shen 或 Canny 过滤器提取亚像素级精确边缘。

- [`frei_amp`](frei_amp.html)

  使用 Frei-Chen 运算符检测边缘（振幅）。

- [`frei_dir`](frei_dir.html)

  使用 Frei-Chen 运算符检测边缘（振幅和方向）。

- [`highpass_image`](highpass_image.html)

  从图像中提取高频成分。

- [`info_edges`](info_edges.html)

  返回 中滤波器的滤波器系数。[`edges_image`](edges_image.html)

- [`kirsch_amp`](kirsch_amp.html)

  使用 Kirsch 运算符检测边缘（振幅）。

- [`kirsch_dir`](kirsch_dir.html)

  使用 Kirsch 算子检测边缘（振幅和方向）。

- [`laplace`](laplace.html)

  使用有限差分计算拉普拉斯算子。

- [`laplace_of_gauss`](laplace_of_gauss.html)

  LoG 算子（高斯拉普拉斯）。

- [`prewitt_amp`](prewitt_amp.html)

  使用 Prewitt 运算符检测边缘（振幅）。

- [`prewitt_dir`](prewitt_dir.html)

  使用 Prewitt 运算符检测边缘（振幅和方向）。

- [`roberts`](roberts.html)

  使用 Roberts 过滤器检测边缘。

- [`robinson_amp`](robinson_amp.html)

  使用 Robinson 运算符检测边缘（振幅）。

- [`robinson_dir`](robinson_dir.html)

  使用 Robinson 运算符检测边缘（振幅和方向）。

- [`sobel_amp`](sobel_amp.html)

  使用 Sobel 运算符检测边缘（振幅）。

- [`sobel_dir`](sobel_dir.html)

  使用 Sobel 运算符检测边缘（振幅和方向）。

## 强化

- [`coherence_enhancing_diff`](coherence_enhancing_diff.html)

  执行图像的连贯性增强扩散。

- [`emphasize`](emphasize.html)

  增强图像的对比度。

- [`equ_histo_image`](equ_histo_image.html)

  图像的直方图线性化

- [`illuminate`](illuminate.html)

  照亮图像。

- [`mean_curvature_flow`](mean_curvature_flow.html)

  将平均曲率流应用于图像。

- [`scale_image_max`](scale_image_max.html)

  *最大灰度值分布在0*到*255 的*取值范围内 。

- [`shock_filter`](shock_filter.html)

  对图像应用震动过滤器。

## 快速傅里叶变换

- [`convol_fft`](convol_fft.html)

  在频域中使用滤波器对图像进行卷积。

- [`convol_gabor`](convol_gabor.html)

  在频域中使用 Gabor 滤波器对图像进行卷积。

- [`correlation_fft`](correlation_fft.html)

  计算两个图像在频域中的相关性。

- [`deserialize_fft_optimization_data`](deserialize_fft_optimization_data.html)

  反序列化 FFT 速度优化数据。

- [`energy_gabor`](energy_gabor.html)

  计算双通道图像的能量。

- [`fft_generic`](fft_generic.html)

  计算图像的快速傅立叶变换。

- [`fft_image`](fft_image.html)

  计算图像的快速傅立叶变换。

- [`fft_image_inv`](fft_image_inv.html)

  计算图像的快速傅里叶逆变换。

- [`gen_bandfilter`](gen_bandfilter.html)

  生成一个理想的带状滤波器。

- [`gen_bandpass`](gen_bandpass.html)

  生成一个理想的带通滤波器。

- [`gen_derivative_filter`](gen_derivative_filter.html)

  在频域中生成导数滤波器。

- [`gen_filter_mask`](gen_filter_mask.html)

  将空间域中的过滤器掩码存储为真实图像。

- [`gen_gabor`](gen_gabor.html)

  生成 Gabor 滤波器。

- [`gen_gauss_filter`](gen_gauss_filter.html)

  在频域中生成高斯滤波器。

- [`gen_highpass`](gen_highpass.html)

  生成一个理想的高通滤波器。

- [`gen_lowpass`](gen_lowpass.html)

  生成一个理想的低通滤波器。

- [`gen_mean_filter`](gen_mean_filter.html)

  在频域中生成均值滤波器。

- [`gen_sin_bandpass`](gen_sin_bandpass.html)

  生成具有正弦形状的带通滤波器。

- [`gen_std_bandpass`](gen_std_bandpass.html)

  生成具有高斯或正弦形状的带通滤波器。

- [`optimize_fft_speed`](optimize_fft_speed.html)

  优化 FFT 的运行时间。

- [`optimize_rft_speed`](optimize_rft_speed.html)

  优化实值 FFT 的运行时间。

- [`phase_correlation_fft`](phase_correlation_fft.html)

  计算频域中两个图像的相位相关性。

- [`phase_deg`](phase_deg.html)

  以度为单位返回复杂图像的相位。

- [`phase_rad`](phase_rad.html)

  以弧度返回复杂图像的相位。

- [`power_byte`](power_byte.html)

  返回复杂图像的功率谱。

- [`power_ln`](power_ln.html)

  返回复杂图像的功率谱。

- [`power_real`](power_real.html)

  返回复杂图像的功率谱。

- [`read_fft_optimization_data`](read_fft_optimization_data.html)

  从文件加载 FFT 速度优化数据。

- [`rft_generic`](rft_generic.html)

  计算图像的实值快速傅里叶变换。

- [`serialize_fft_optimization_data`](serialize_fft_optimization_data.html)

  序列化 FFT 速度优化数据。

- [`write_fft_optimization_data`](write_fft_optimization_data.html)

  将 FFT 速度优化数据存储在文件中。

## 几何变换

- [`affine_trans_image`](affine_trans_image.html)

  对图像应用任意仿射二维变换。

- [`affine_trans_image_size`](affine_trans_image_size.html)

  对图像应用任意仿射二维变换并指定输出图像大小。

- [`convert_map_type`](convert_map_type.html)

  将图像地图转换为其他地图类型。

- [`map_image`](map_image.html)

  对图像应用一般变换。

- [`mirror_image`](mirror_image.html)

  镜像图像。

- [`polar_trans_image_ext`](polar_trans_image_ext.html)

  将图像中的环形弧转换为极坐标。

- [`polar_trans_image_inv`](polar_trans_image_inv.html)

  将极坐标中的图像转换回笛卡尔坐标

- [`projective_trans_image`](projective_trans_image.html)

  对图像应用投影变换。

- [`projective_trans_image_size`](projective_trans_image_size.html)

  对图像应用投影变换并指定输出图像大小。

- [`rotate_image`](rotate_image.html)

  围绕其中心旋转图像。

- [`zoom_image_factor`](zoom_image_factor.html)

  按给定因子缩放图像。

- [`zoom_image_size`](zoom_image_size.html)

  将图像缩放到给定大小。

## 修复 Inpainting

- [`harmonic_interpolation`](harmonic_interpolation.html)

  对图像区域执行谐波插值。

- [`inpainting_aniso`](inpainting_aniso.html)

  通过各向异性扩散进行修复。

- [`inpainting_ced`](inpainting_ced.html)

  通过连贯性增强扩散进行修复。

- [`inpainting_ct`](inpainting_ct.html)

  通过相干传输执行修复。

- [`inpainting_mcf`](inpainting_mcf.html)

  通过平滑水平线来执行修复。

- [`inpainting_texture`](inpainting_texture.html)

  通过纹理传播执行修复。

## 线条 Lines

- [`bandpass_image`](bandpass_image.html)

  使用带通滤波器进行边缘提取。

- [`lines_color`](lines_color.html)

  检测彩色线条及其宽度。

- [`lines_facet`](lines_facet.html)

  使用小平面模型检测线。

- [`lines_gauss`](lines_gauss.html)

  检测线条及其宽度。

## 匹配 Match

- [`exhaustive_match`](exhaustive_match.html)

  模板和图像的匹配。

- [`exhaustive_match_mg`](exhaustive_match_mg.html)

  在分辨率金字塔中匹配模板和图像。

- [`gen_gauss_pyramid`](gen_gauss_pyramid.html)

  计算高斯金字塔。

- [`monotony`](monotony.html)

  计算单调操作。

## 杂项 Misc

- [`convol_image`](convol_image.html)

  Calculate the correlation between an image and an arbitrary filter mask

- [`deviation_n`](deviation_n.html)

  Calculate standard deviation over several channels.

- [`expand_domain_gray`](expand_domain_gray.html)

  Expand the domain of an image and set the gray values in the expanded domain.

- [`gray_inside`](gray_inside.html)

  Calculate the lowest possible gray value on an arbitrary path to the image border for each point in the image.

- [`gray_skeleton`](gray_skeleton.html)

  Thinning of gray value images.

- [`lut_trans`](lut_trans.html)

  Transform an image with a gray-value look-up-table

- [`symmetry`](symmetry.html)

  Symmetry of gray values along a row.

- [`topographic_sketch`](topographic_sketch.html)

  Compute the topographic primal sketch of an image.

##  噪音 Noise

- [`add_noise_distribution`](add_noise_distribution.html)

  为图像添加噪点。

- [`add_noise_white`](add_noise_white.html)

  为图像添加噪点。

- [`gauss_distribution`](gauss_distribution.html)

  生成高斯噪声分布。

- [`noise_distribution_mean`](noise_distribution_mean.html)

  确定图像的噪声分布。

- [`sp_distribution`](sp_distribution.html)

  生成椒盐噪声分布。

##  光流 Optical Flow

- [`derivate_vector_field`](derivate_vector_field.html)

  将矢量场与高斯导数进行卷积。

- [`optical_flow_mg`](optical_flow_mg.html)

  计算两个图像之间的光流。

- [`unwarp_image_vector_field`](unwarp_image_vector_field.html)

  使用矢量场反扭曲图像。

- [`vector_field_length`](vector_field_length.html)

  计算矢量场的矢量长度。

## 点 Points

- [`corner_response`](corner_response.html)

  搜索图像中的角点。

- [`dots_image`](dots_image.html)

  增强图像中的圆点。

- [`points_foerstner`](points_foerstner.html)

  使用 Förstner 运算符检测兴趣点。

- [`points_harris`](points_harris.html)

  使用 Harris 运算符检测兴趣点。

- [`points_harris_binomial`](points_harris_binomial.html)

  使用 Harris 算子的二项式近似检测兴趣点。

- [`points_lepetit`](points_lepetit.html)

  使用 Lepetit 运算符检测兴趣点。

- [`points_sojka`](points_sojka.html)

  使用 Sojka 运算符查找角点。

## 场景流程 Scene Flow

- [`scene_flow_calib`](scene_flow_calib.html)

  计算两个立体图像对之间的校准场景流。

- [`scene_flow_uncalib`](scene_flow_uncalib.html)

  计算两个立体图像对之间的未校准场景流。

## 

- [`anisotropic_diffusion`](anisotropic_diffusion.html)

  执行图像的各向异性扩散。

- [`bilateral_filter`](bilateral_filter.html)

  图像的双边滤波。

- [`binomial_filter`](binomial_filter.html)

  使用二项式滤波器平滑图像。

- [`eliminate_min_max`](eliminate_min_max.html)

  平滑空间域中的图像以抑制噪声。

- [`eliminate_sp`](eliminate_sp.html)

  用平均值替换阈值之外的值。

- [`fill_interlace`](fill_interlace.html)

  插值 2 个视频半图像。

- [`gauss_filter`](gauss_filter.html)

  使用离散高斯函数平滑。

- [`guided_filter`](guided_filter.html)

  图像的引导过滤。

- [`info_smooth`](info_smooth.html)

  有关平滑滤波器的信息。[`smooth_image`](smooth_image.html)

- [`isotropic_diffusion`](isotropic_diffusion.html)

  执行图像的各向同性扩散。

- [`mean_image`](mean_image.html)

  通过平均平滑。

- [`mean_n`](mean_n.html)

  多个通道的平均灰度值。

- [`mean_sp`](mean_sp.html)

  抑制椒盐噪声。

- [`median_image`](median_image.html)

  计算具有各种掩码的中值滤波器。

- [`median_rect`](median_rect.html)

  计算具有矩形掩码的中值滤波器。

- [`median_separate`](median_separate.html)

  使用矩形掩码分离中值过滤。

- [`median_weighted`](median_weighted.html)

  具有不同秩掩码的加权中值过滤。

- [`midrange_image`](midrange_image.html)

  计算任何掩码内的最大值和最小值的平均值。

- [`rank_image`](rank_image.html)

  计算具有任意掩码的等级过滤器。

- [`rank_n`](rank_n.html)

  从多个通道返回具有给定等级的灰度值。

- [`rank_rect`](rank_rect.html)

  计算带有矩形掩码的等级过滤器。

- [`sigma_image`](sigma_image.html)

  使用 sigma 滤波器进行非线性平滑。

- [`smooth_image`](smooth_image.html)

  使用各种过滤器平滑图像。

- [`trimmed_mean`](trimmed_mean.html)

  使用任意等级掩码平滑图像。

## 平滑 Smoothing

- [`anisotropic_diffusion`](anisotropic_diffusion.html)

  执行图像的各向异性扩散。

- [`bilateral_filter`](bilateral_filter.html)

  图像的双边滤波。

- [`binomial_filter`](binomial_filter.html)

  使用二项式滤波器平滑图像。

- [`eliminate_min_max`](eliminate_min_max.html)

  平滑空间域中的图像以抑制噪声。

- [`eliminate_sp`](eliminate_sp.html)

  用平均值替换阈值之外的值。

- [`fill_interlace`](fill_interlace.html)

  插值 2 个视频半图像。

- [`gauss_filter`](gauss_filter.html)

  使用离散高斯函数平滑。

- [`guided_filter`](guided_filter.html)

  图像的引导过滤。

- [`info_smooth`](info_smooth.html)

  有关平滑滤波器的信息。[`smooth_image`](smooth_image.html)

- [`isotropic_diffusion`](isotropic_diffusion.html)

  执行图像的各向同性扩散。

- [`mean_image`](mean_image.html)

  通过平均平滑。

- [`mean_n`](mean_n.html)

  多个通道的平均灰度值。

- [`mean_sp`](mean_sp.html)

  抑制椒盐噪声。

- [`median_image`](median_image.html)

  计算具有各种掩码的中值滤波器。

- [`median_rect`](median_rect.html)

  计算具有矩形掩码的中值滤波器。

- [`median_separate`](median_separate.html)

  使用矩形掩码分离中值过滤。

- [`median_weighted`](median_weighted.html)

  具有不同秩掩码的加权中值过滤。

- [`midrange_image`](midrange_image.html)

  计算任何掩码内的最大值和最小值的平均值。

- [`rank_image`](rank_image.html)

  计算具有任意掩码的等级过滤器。

- [`rank_n`](rank_n.html)

  从多个通道返回具有给定等级的灰度值。

- [`rank_rect`](rank_rect.html)

  计算带有矩形掩码的等级过滤器。

- [`sigma_image`](sigma_image.html)

  使用 sigma 滤波器进行非线性平滑。

- [`smooth_image`](smooth_image.html)

  使用各种过滤器平滑图像。

- [`trimmed_mean`](trimmed_mean.html)

  使用任意等级掩码平滑图像。

## 质地检验 Texture Inspection

- [`deviation_image`](deviation_image.html)

  计算矩形窗口内灰度值的标准偏差。

- [`entropy_image`](entropy_image.html)

  计算矩形窗口内灰度值的熵。

- [`texture_laws`](texture_laws.html)

  使用 Laws 纹理过滤器过滤图像。

##  维纳滤波器 Wiener Filter

- [`gen_psf_defocus`](gen_psf_defocus.html)

  生成均匀散焦模糊的脉冲响应。

- [`gen_psf_motion`](gen_psf_motion.html)

  生成（线性）运动模糊的脉冲响应。

- [`simulate_defocus`](simulate_defocus.html)

  模拟图像的均匀散焦模糊。

- [`simulate_motion`](simulate_motion.html)

  模拟（线性）运动模糊。

- [`wiener_filter`](wiener_filter.html)

  通过维纳滤波进行图像复原。

- [`wiener_filter_ni`](wiener_filter_ni.html)

  通过维纳滤波进行图像复原。
