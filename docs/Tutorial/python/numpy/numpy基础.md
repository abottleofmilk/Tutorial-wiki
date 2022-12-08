## 保存
ndarray 对象可以使用处理普通文本文件的函数和处理普通文本文件的函数，以及处理具有.npy文件扩展名的 NumPy 二进制文件的函数，以及处理具有.npz文件扩展名的NumPy 文件的函数，保存到磁盘文件loadtxt和从磁盘文件加载。
```python
np.save('filename', a)
b = np.load('filename.npy')
```
您可以将 NumPy 数组保存为纯文本文件，如.csv或.txt文件，后缀为np.savetxt.