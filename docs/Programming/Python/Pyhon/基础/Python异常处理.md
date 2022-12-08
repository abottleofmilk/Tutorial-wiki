# Python异常处理
## 基本语法
### 捕捉异常
```python
try:
    #...
except Exception:
    #...
```
### 其他语法
+ 在原本的try except结构的基础上，Python 异常处理机制还提供了一个 else 块，也就是原有 try except 语句的基础上再添加一个 else 块，即try except else结构。
+ 和 else 语句不同，finally 只要求和 try 搭配使用，而至于该结构中是否包含 except 以及 else，对于 finally 不是必须的（else 必须和 try except 搭配使用）。
### 抛出异常
1. raise：单独一个 raise。该语句引发当前上下文中捕获的异常（比如在 except 块中），或默认引发 RuntimeError 异常。
2. raise 异常类名称：raise 后带一个异常类名称，表示引发执行类型的异常。
3. raise 异常类名称(描述信息)：在引发指定类型的异常的同时，附带异常的描述信息。
### 异常链
## 自定义异常
由于大多数 Python 内置异常的名字都以 "Error" 结尾，所以实际命名时尽量跟标准的异常命名一样。
虽然所有类同时继承自 BaseException，但它是为系统退出异常而保留的，假如直接继承 BaseException，可能会导致自定义异常不会被捕获，而是直接发送信号退出程序运行，脱离了我们自定义异常类的初衷。通常应继承自 Exception 类（直接继承）

系统自带的异常只要触发会自动抛出（比如 NameError、ValueError 等），但用户自定义的异常需要用户自己决定什么时候抛出。也就是说，自定义的异常需要使用 raise 手动抛出。
### assert表达式
```
assert 条件表达式 [,描述信息]
```
assert 语句的作用是：当条件表达式的值为真时，该语句什么也不做，程序正常运行；反之，若条件表达式的值为假，则 assert 会抛出 AssertionError 异常。其中，[,描述信息] 作为可选参数，用于对条件表达式可能产生的异常进行描述。

