机器学习算法是从数据中产生模型，也就是进行学习的算法（下文也简称为算法）。我们把经验提供给算法，它就能够根据经验数据产生模型。在面对新的情况时，模型就会为我们提供判断（预测）结果。从数据中学得模型的过程称为学习（learning）或者训练（training）。在训练过程中所使用的数据称为训练数据，其中的每个样本称为训练样本，训练样本所组成的集合称为训练集。
## 理论基础
K近邻算法的本质是将指定对象**根据已知特征值分类**。例如，看到一对父子，一般情况下，通过判断他们的年龄，能够马上分辨出哪位是父亲，哪位是儿子。这是通过年龄属性的特征值来划分的。为了确定分类，需要定义特征。

实际的分类数据中往往参数非常多，判断起来也不会如此简单。因此，为了提高算法的可靠性，在实施时会取k个近邻点，这k个点中属于哪一类的较多，然后将当前待识别点划分为哪一类。为了方便判断，**k值通常取奇数**。

T={(1,y1),(X2,y2),... , (XN,yN)} 待分类样本(x,y)

1.根据T中的样本构建kd树。
2.根据距离度量，运行k次kd树搜索，计算Nk(X)。
3.根据分类决策规则，计算新样本的类别y。

## 计算

### 归一化
归一化：就是让数值差异过大的几组数据缩小至同一数量级。（0-1归化、零-均值规范化z-score标准化)


对于简单的情况，直接计算与特征值的距离（差距）即可。当有多个参数时，一般将这些参数构成列表（数组）进行综合判断。常情况下，由于各个参数的量纲不一致等原因，需要对参数进行处理，让所有参数具有相等的权值。一般情况下，对参数进行归一化处理即可。做归一化时，通常使用特征值除以所有特征值中的最大值（或者最大值与最小值的差）。
### 距离计算
有多种距离算法，选择一种来作为依据。
## 手写数字识别的原理
### 特征值提取
将数字图像分割成很多小块，然后计算每个小块黑的个数。记录下来，然后新的数字就可以用记录下的特征值来比对。

我们把数字图像划分成很多小块，图中每个数字被分成5行4列，共计5×4=20个小块。此时，每个小块是由很多个像素点构成的。当然，也可以将每一个像素点理解为一个更小的子块。将这些小块表示为B（Bigger），将B内的像素点，记为S（Smaller）。因此，待识别的数字“8”的图像可以理解为：● 由5行4列，共计5×4=20个小块B构成。● 每个小块B内其实是由M×N个像素（更小块S）构成的。为了描述上的方便，假设每个小块大小为10×10=100个像素。

![](https://s2.loli.net/2022/12/16/eGLoREdgymYvqf2.png "每个小块B内黑色像素点的个数")

### 数字识别
数字识别要做的就是比较待识别图像与图像集中的哪个图像最近。这里，最近指的是二者之间的欧氏距离最短。根据计算的距离，待识别的数字“8”图像与数字“8”特征图像的距离更近。所以，将待识别的数字“8”图像识别为数字“8”特征图像所代表的数字“8”。

##  自定义函数手写数字识别
OpenCV提供了函数cv2.KNearest()用来实现K近邻算法，在OpenCV中可以直接调用该函数。为了进一步了解K近邻算法及其实现方式，本节首先使用Python和OpenCV实现一个识别手写数字的实例。
## K近邻模块的基本使用
在OpenCV中，不需要自己编写复杂的函数实现K近邻算法，直接调用其自带的模块函数即可。

> 演示OpenCV自带的K近邻模块的使用方法。

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
# 用于训练的数据
# rand1数据位于(0,30)
rand1 = np.random.randint(0, 30, (20, 2)).astype(np.float32)
# rand2数据位于(70,100)
rand2 = np.random.randint(70, 100, (20, 2)).astype(np.float32)
# 将rand1和rand2拼接为训练数据
trainData = np.vstack((rand1, rand2))
# 数据标签，共两类：0和1
# r1Label对应着rand1的标签，为类型0
r1Label=np.zeros((20,1)).astype(np.float32)
# r2Label对应着rand2的标签，为类型1
r2Label=np.ones((20,1)).astype(np.float32)
tdLable = np.vstack((r1Label, r2Label))
# 使用绿色标注类型0
g = trainData[tdLable.ravel() == 0]
plt.scatter(g[:,0], g[:,1], 80, 'g', 'o')
# 使用蓝色标注类型1
b = trainData[tdLable.ravel() == 1]
plt.scatter(b[:,0], b[:,1], 80, 'b', 's')
# plt.show()
# test为用于测试的随机数，该数在0到100之间
test = np.random.randint(0, 100, (1, 2)).astype(np.float32)
plt.scatter(test[:,0], test[:,1], 80, 'r', '*')
# 调用OpenCV内的K近邻模块，并进行训练
knn = cv2.ml.KNearest_create()
knn.train(trainData, cv2.ml.ROW_SAMPLE, tdLable)
# 使用K近邻算法分类
ret, results, neighbours, dist = knn.findNearest(test, 5)
# 显示处理结果
print("当前随机数可以判定为类型：", results)
print("距离当前点最近的5个邻居是：", neighbours)
print("5个最近邻居的距离： ", dist)
# 可以观察一下显示，对比上述输出
plt.show()
运行上述程序，显示的运行结果（因为是随机数，每次结果会略有不同）为：
当前随机数可以判定为类型： [[1.]]
距离当前点最近的5个邻居是： [[1. 1. 1. 1. 1.]]
5个最近邻居的距离：  [[313. 324. 338. 377. 405.]]
```

![](https://s2.loli.net/2022/12/15/xRYABOkfcFJdIoM.png)

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

## 个人总结
1. 对几组数据来说，加入一个新的数据判断其属于哪一种的问题我们先对数据分类的依据做出判断即（特征）
2. 选择合适的权重来组成一个合适的函数，并作出归一化处理
3. 选择合适的距离算法，最终通过极值来判断

[常用数据规范化方法: min-max规范化，零-均值规范化等](https://blog.csdn.net/zxiang_123/article/details/104423402)