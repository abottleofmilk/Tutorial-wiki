## 简介
### 概述
HALCON 的IDE有2种模式：HDevelop 和HDevelop XL。

hdevelop 适用于普通分辨率的图像，小于等于 32k x 32k；

hdevelop xl适用于大分辨率的图像，大于 32k x 32k 。

![](https://s2.loli.net/2022/12/07/6SwKqnHP1AUsOrN.png)

### 工具介绍

导出：导出脚本

### 基本数据
HALCON有两种基本的数据型态:
+ 图像数据(iconic HObject，例如lmage,Region,Xld )
+ 控制数据(control HTuple，例如浮点数，整数，字符串,handle 等等)

所有运算子的参数都是
以相同的方式排列:
输入图像:输出图像:输入控制:输出控制

并非：所有的运算子都具有上列四类参数，不过参数排列的次序依旧相同

threshold(Image:Region:MinGray,MaxGray:) threshold(Image,Region,190,255)
## HDevelop Language

## 图形参数
### image
图像由一个或多个通道组成，即，大小相同的矩阵包含各种像素类型的灰度值。

+ 1黑白图一个通道像素点存放在一个矩阵中
+ 2彩色图
+ 3通道 像素点存放在通道矩阵中

lmage type
'byte', 'complex', 'cyclic', 'direction', 'int1', 'int2', 'int4', 'int8', 'real', 'uint2', 'vector field absolute', 'vector field relative'

常用的：  
+ byte 2的8次方最大值255
+ Real 2的32或64次方3d中计算的多

### region

+ 1，像素坐标值的存储方式，有广泛的应用
+ 2,类似于游程编码，可用于压缩，eg:用a2b3c4代表abbbccccget_region_runs (Region : : : Row,ColumnBegin,ColumnEnd)
+ 3,像素点保存，而像素点是整型的halcon.com
+ 4，ROl (region of interest)，感兴趣区域

### XLD
1,亚像素(subpixel)描述几何轮廓的对象
2,xld在模板匹配、图形校准等多方面有重要的用途

XLD有两种:
Contours 轮廓是一系列的点连接。点之间的距离大约是一个像素
polygons 多边形,点之间的距离较大,是用最少的线来描述这个轮廓
## Region
### Region操作
![](https://s2.loli.net/2022/12/07/ivLs2rgjuRfx7ZB.png)

### Region转换

![](https://s2.loli.net/2022/12/07/zdMoE6DGRVSxag1.png)

### XLD
![](https://s2.loli.net/2022/12/07/Cydx2sJL7N5oZHV.png)

### XLD转换
![](https://s2.loli.net/2022/12/07/wmWjQ6Ha4SIBYqK.png)

### 筛选
根据特征值来选择范围

### region特征
#### 圆度（Circularity）
![](https://s2.loli.net/2022/12/07/8jdMmQPJy36e5wC.png)
#### 矩形度(rectangularity )
![](https://s2.loli.net/2022/12/07/JPUYubCyhacW26f.png)
#### 长度（contlength）
![](https://s2.loli.net/2022/12/07/BMGeosXWwcyiTSq.png)
#### 精密度（compactness）
![](https://s2.loli.net/2022/12/07/VlF8BjMmbHTWzAd.png)
#### 凸性（convexity）
![](https://s2.loli.net/2022/12/07/Ljt9GmIAqWXRcOQ.png)
## 变化
### 仿射变换（hom）
![](https://s2.loli.net/2022/12/07/AJpjd4mKLTcsXaP.png)
### 刚性变换（rigid transformation）
平移(translation）和旋转(rotation)

刚体变换(rigid transformation).

### 存储到本地
+ write_
+ read_

（序列化）
+ serialize_
+ deserialize_
## 常见误区
### 图像坐标系
![](https://s2.loli.net/2022/12/07/oBWw3QSNAfjcYyi.png)

![](https://s2.loli.net/2022/12/07/kKzdsOPNRihD7mc.png)
### 角度范围
![](https://s2.loli.net/2022/12/07/OI27adZDmWwxSUp.png)

![](https://s2.loli.net/2022/12/07/mngz3T5XBcHEpYF.png)
### orientation_region的角度
![](https://s2.loli.net/2022/12/07/qBDsaHN3ZebCEkS.png)
## 参考
1. [Halcon快速入门系列](https://www.bilibili.com/video/BV1ZE41177MQ?p=1&vd_source=d48f281ea63ee780abaa65c5ecb35e14)
2. [halcon学习网](http://www.ihalcon.com/)
3. [仿射变换及其变换矩阵的理解](https://www.cnblogs.com/shine-lee/p/10950963.html)

