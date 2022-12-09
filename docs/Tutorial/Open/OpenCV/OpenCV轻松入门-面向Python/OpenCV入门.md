## 图像处理基本操作
### 读取图像
```python
retval = cv2.imread( filename[, flags] )
```
+ retval是返回值，其值是读取到的图像。如果未读取到图像，则返回“None”。
+ filename表示要读取的图像的完整文件名。
+ flags是读取标记。该标记用来控制读取文件的类型
> flag类型
![](https://s2.loli.net/2022/12/09/aUX3NitrmjYQKMf.png)

> 支持读取的图片类型
![](https://s2.loli.net/2022/12/09/pD4FE6imUCGlsA9.png)
### 显示图像
+ namedWindow函数 用来创建指定名称的窗口
+ imshow函数 用来显示图像
+ waitKey函数 用来等待按键，当用户按下键盘后，该语句会被执行，并获取返回值。
+ destroyWindow函数 用来释放（销毁）指定窗口
+ destroyAllWindows函数 用来释放（销毁）所有窗口
```python
None = cv2.namedWindow( winname )
None = cv2.imshow( winname, mat )
retval = cv2.waitKey( [delay] )
None = cv2.destroyWindow( winname )
None = cv2.destroyAllWindows( )
```
+ winname是窗口名称。
+ mat是要显示的图像。
+ retval表示返回值。如果没有按键被按下，则返回-1；如果有按键被按下，则返回该按键的ASCII码。
+ delay表示等待键盘触发的时间，单位是ms。当该值是负数或者零时，表示无限等待。该值默认为0。(一直等待。直到有按下键盘按键的事件发生时，才会执行后续程序。)
```python
import cv2
lena=cv2.imread("lena.bmp")
cv2.namedWindow("lesson")
cv2.imshow("lesson", lena )
```
1. 如果参数delay的值为0，则程序会一直等待。直到有按下键盘按键的事件发生时，才会执行后续程序。
2. 如果参数delay的值为一个正数，则在这段时间内，程序等待按下键盘按键。当有按下键盘按键的事件发生时，就继续执行后续程序语句；如果在delay参数所指定的时间内一直没有这样的事件发生，则超过等待时间后，继续执行后续的程序语句。
```python
import cv2
lena=cv2.imread("lena.bmp")
cv2.imshow("demo", lena )
key=cv2.waitKey()
if key==ord('A'):
    cv2.imshow("PressA", lena)
elif key==ord('B'):
    cv2.imshow("PressB", lena)
```
### 保存图像
```
retval = cv2.imwrite( filename, img[, params] )
```
+ retval是返回值。如果保存成功，则返回逻辑值真（True）；如果保存不成功，则返回逻辑值假（False）。
+ filename是要保存的目标文件的完整路径名，包含文件扩展名。
+ img是被保存图像的名称。
+ params是保存类型参数，是可选的。

## OpenCV贡献库
OpenCV库包含如下两部分：

1. OpenCV主库：即通常安装的OpenCV库，该库是成熟稳定的，由核心的OpenCV团队维护。
2. 2.OpenCV贡献库：该扩展库的名称为opencv_contrib，主要由社区开发和维护，其包含的视觉应用比OpenCV主库更全面。需要注意的是，OpenCV贡献库中包含非OpenCV许可的部分，并且包含受专利保护的算法。因此，在使用该模块前需要特别注意。

+ bioinspired：生物视觉模块。
+ datasets：数据集读取模块。
+ dnn：深度神经网络模块。
+ face：人脸识别模块。
+ matlab:MATLAB接口模块。
+ stereo：双目立体匹配模块。
+ text：视觉文本匹配模块。
+ tracking：基于视觉的目标跟踪模块。
+ ximgpro：图像处理扩展模块。
+ xobjdetect：增强2D目标检测模块。
+ xphoto：计算摄影扩展模块。