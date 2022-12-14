机器学习算法是从数据中产生模型，也就是进行学习的算法（下文也简称为算法）。我们把经验提供给算法，它就能够根据经验数据产生模型。在面对新的情况时，模型就会为我们提供判断（预测）结果。从数据中学得模型的过程称为学习（learning）或者训练（training）。在训练过程中所使用的数据称为训练数据，其中的每个样本称为训练样本，训练样本所组成的集合称为训练集。
## 理论基础
K近邻算法的本质是将指定对象**根据已知特征值分类**。例如，看到一对父子，一般情况下，通过判断他们的年龄，能够马上分辨出哪位是父亲，哪位是儿子。这是通过年龄属性的特征值来划分的。为了确定分类，需要定义特征。

实际的分类数据中往往参数非常多，判断起来也不会如此简单。因此，为了提高算法的可靠性，在实施时会取k个近邻点，这k个点中属于哪一类的较多，然后将当前待识别点划分为哪一类。为了方便判断，k值通常取奇数。

## 计算

### 归一化

### 距离计算

## 手写数字识别的原理
### 特征值提取

### 数字识别

##  自定义函数手写数字识别

## K近邻模块的基本使用
在OpenCV中，不需要自己编写复杂的函数实现K近邻算法，直接调用其自带的模块函数即可。

### 

## K近邻手写数字识别

> 使用OpenCV自带的函数完成对手写数字的识别

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
# 读取样本（特征）图像的值
s='image\\'  # 图像所在的路径
num=100 # 共有的样本数量
row=240 # 特征图像的行数
col=240 # 特征图像的列数
a=np.zeros((num, row, col)) # 用来存储所有样本的数值
#print(a.shape)
n=0 # 用来存储当前图像的编号
for i in range(0,10):
    for j in range(1,11):
        a[n, :, :]=cv2.imread(s+str(i)+'\\'+str(i)+'-'+str(j)+'.bmp',0)
        n=n+1
# 提取样本图像的特征
feature=np.zeros((num, round(row/5), round(col/5))) # 用来存储所有样本的特征值
#print(feature.shape)  # 看看特征值的形状是什么样子
#print(row)            # 看看row的值，有多少个特征值（100）
for ni in range(0, num):
    for nr in range(0, row):
        for nc in range(0, col):
            if a[ni, nr, nc]==255:
                feature[ni, int(nr/5), int(nc/5)]+=1
f=feature   # 简化变量名称
# 将feature处理为单行形式
train = feature[:, :].reshape(-1,
                        round(row/5)*round(col/5)).astype(np.float32)
#print(train.shape)
# 贴标签，要注意，是range(0,100)而非range(0,101)
trainLabels = [int(i/10)  for i in range(0,100)]
trainLabels=np.asarray(trainLabels)
#print(*trainLabels)   # 打印测试看看标签值
##读取图像值
o=cv2.imread('image\\test\\5.bmp',0)     # 读取待识别图像
of=np.zeros((round(row/5), round(col/5))) # 用来存储待识别图像的特征值
for nr in range(0, row):
    for nc in range(0, col):
        if o[nr, nc]==255:
            of[int(nr/5), int(nc/5)]+=1

test=of.reshape(-1, round(row/5)*round(col/5)).astype(np.float32)
# 调用函数识别图像
knn=cv2.ml.KNearest_create()
knn.train(train, cv2.ml.ROW_SAMPLE, trainLabels)
ret, result, neighbours, dist = knn.findNearest(test, k=5)
print("当前随机数可以判定为类型：", result)
print("距离当前点最近的5个邻居是：", neighbours)
print("5个最近邻居的距离： ", dist)
```