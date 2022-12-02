## 描述

## 模块机制

 ### commonjs

![](https://cdn.staticaly.com/gh/abottleofmilk/CDN@master/img/20221005183532.png)

由于官方规范（ECMAScript）规范化的时间较早，规范涵盖的范畴非常小。这些规范中包含词法、类型、上下文、表达式、声明（statement）、方法、对象等语言的基本要素。在实际应用中，JavaScript的表现能力取决于宿主环境中的API支持程度JavaScript自身而言，它的规范依然是薄弱的，还有以下缺陷：
❑ 没有模块系统。（ES6中已支持）
❑ 标准库较少。ECMAScript仅定义了部分核心库，对于文件系统，I/O流等常见需求却没有标准的API。就HTML5的发展状况而言，W3C标准化在一定意义上是在推进这个过程，但是它仅限于浏览器端。
❑ 没有标准接口。在 JavaScript 中，几乎没有定义过如 Web 服务器或者数据库之类的标准统一接口。
❑ 缺乏包管理系统。这导致JavaScript应用中基本没有自动加载和安装依赖的能力。

### Node的模块实现

在 Node 中引入模块，需要经历如下 3 个步骤。(1) 路径分析 (2) 文件定位 (3) 编译执行。
模块分为两类：一类是Node提供的模块，称为核心模块；另一类是用户编写的模块，称为文件模块。
❑ 核心模块部分在 Node 源代码的编译过程中，**编译进了二进制执行文件**。在 Node 进程启动时，部分核心模块就被**直接加载进内存**中，所以这部分核心模块引入时，文件定位和编译执行这两个步骤可以省略掉，并且在路径分析中优先判断，所以它的加载速度是最快的。
❑ 文件模块则是在运行时动态加载，需要完整的路径分析、文件定位、编译执行过程，速度比核心模块慢。
Node对引入过的模块都会进行缓存，以减少二次引入时的开销。不同的地方在于，浏览器仅仅缓存文件，而Node**缓存的是编译和执行之后的对象**。

### 路径分析和文件定位

❑ . js 文件。通过 fs 模块同步读取文件后编译执行。
❑ . node 文件。这是用 C/C++编写的扩展文件，通过 dlopen () 方法加载最后编译生成的文件。
❑ . json 文件。通过 fs 模块同步读取文件后，用 JSON. parse () 解析返回结果。
❑ 其余扩展名文件。它们都被当做．js 文件载入。

#### 模块标识符

require()方法**接受一个标识符作为参数**。在Node实现中，正是基于这样一个标识符进行模块查找的。模块标识符在Node中主要分为以下几类。
❑ 核心模块，如http、fs、path等。 
❑ ．或．．开始的相对路径文件模块。 
❑ 以/开始的绝对路径文件模块。 
❑ 非路径形式的文件模块，如自定义的connect模块。  
**模块路径**是 Node 在定位文件模块的具体文件时制定的查找策略，具体表现为一个路径组成的数组。

```javascript
[

  'H:\\work\\test\\node_modules',

  'H:\\work\\node_modules',

  'H:\\node_modules'

]
```

逐级向上直到根目录的 node_modules，在加载的过程中，Node 会逐个尝试模块路径中的路径，直到找到目标文件为止。

#### 文件定位

require () 在分析标识符的过程中，会出现标识符中不包含文件扩展名的情况。CommonJS 模块规范也允许在标识符中不包含文件扩展名，这种情况下，Node 会按．js、. json、. node 的次序补足扩展名，依次尝试。需要调用 fs 模块同步阻塞式地判断文件是否存在。因为 Node 是单线程的，所以这里是一个会引起性能问题的地方。（所以带上文件名速度会更快）

#### 目录分析和包

require()通过分析文件扩展名之后，可能没有查找到对应文件，但却得到一个目录，这在引入自定义模块和逐个模块路径进行查找时经常会出现，此时**Node会将目录当做一个包来处理**。在当前目录下查找package.json（CommonJS包规范定义的包描述文件），通过JSON.parse()解析出包描述对象，从中取出main属性指定的文件名进行定位。而如果main属性指定的文件名错误，或者压根没有package.json文件，Node会将index当做默认文件名，然后依次查找index.js、index.json、index.node。

#### 模板编译

在 Node 中，**每个文件模块都是一个对象**，编译和执行是引入文件模块的最后一个阶段。定位到具体的文件后，Node 会新建一个模块对象，然后根据路径载入并编译。不同文件扩展名处理方式不同： 
❑ .js文件。通过fs模块同步读取文件后编译执行。
❑ .node文件。这是用C/C++编写的扩展文件，通过dlopen()方法加载最后编译生成的文件。
❑ .json文件。通过fs模块同步读取文件后，用JSON.parse()解析返回结果。
❑ 其余扩展名文件。它们都被当做．js文件载入。  
每一个编译成功的模块都会将其文件路径作为**索引缓存**在 Module.\_cache 对象上，以提高二次引入的性能。
Module.\_extensions 会被赋值给 require () 的 extensions 属性，所以通过在代码中访问**require. extensions**可以知道系统中已有的扩展加载方式。

```javascript
[Object: null prototype] {

  '.js': [Function (anonymous)],

  '.json': [Function (anonymous)],

  '.node': [Function (anonymous)]

}
```

如果想对自定义的扩展名进行特殊的加载，可以通过类似require.extensions['.ext']的方式实现。早期的CoffeeScript文件就是通过添加require.extensions['.coffee']扩展的方式来实现加载的。但是从v0.10.6版本开始，官方不鼓励通过这种方式来进行自定义扩展名的加载，而是期望**先将其他语言或文件编译成JavaScript文件后再加载，这样做的好处在于不将烦琐的编译加载等过程引入Node的执行过程中**。
在编译的过程中，Node 对获取的 JavaScript 文件内容进行了头尾包装。在头部添加了 (function (exports, require, module, \_\_filename, \_\_dirname)。这样每个模块文件之间都进行了**作用域隔离**。包装之后的代码会通过 vm 原生模块的 runInThisContext () 方法执行（类似 eval，只是具有明确上下文，不污染全局），**返回一个具体的 function 对象**。最后，将当前模块对象的 exports 属性、require () 方法、module（模块对象自身），以及在文件定位中得到的完整文件路径和文件目录作为参数传递给这个 function () 执行。

#### C/C++模块的编译 &JSON

Node 调用 process. dlopen () 方法进行加载和执行。在 Node 的架构下，dlopen () 方法在 Windows 和\*nix 平台下分别有不同的实现，通过 libuv 兼容层进行了封装。实际上，. node 的模块文件并不需要编译，因为它是编写 C/C++模块之后编译生成的，所以这里只有加载和执行的过程。在执行的过程中，模块的 exports 对象与．node 模块产生联系，然后返回给调用者。
Node利用fs模块同步读取JSON文件的内容之后，调用JSON.parse()方法得到对象，然后将它赋给模块对象的exports，以供外部调用。

### 核心模块

核心模块其实分为 C/C++编写的和 JavaScript 编写的两部分，其中 C/C++文件存放在 Node 项目的 src 目录下，JavaScript 文件存放在 lib 目录下。

#### 核心模块的引入流程

os 原生模块的引入流程可以看到，为了符合 CommonJS 模块规范，从 JavaScript 到 C/C++的过程是相当复杂的，它要经历 C/C++层面的内建模块定义、（JavaScript）核心模块的定义和引入以及（JavaScript）文件模块层面的引入。但是对于用户而言，require () 十分简洁、友好。
![](https://cdn.staticaly.com/gh/abottleofmilk/CDN@master/img/20221025002825.png)

## 异步 I/O

### 异步编程

### 函数式编程

在通常的语言中，函数的参数只接受基本的数据类型或是对象引用，返回值也只是基本数据类型和对象引用。**高阶函数**则是可以把函数作为参数，或是将函数作为返回值的函数。C/C++语言而言，通过指针也可以达到相同的效果。
偏函数用法是指创建一个调用另外一个部分——参数或变量已经预置的函数——的函数的用法。

```javascript
var isType = function (type) {

 return function (obj) {

  return toString.call(obj) == '[object ' + type + ']';

 };

};

var isString = isType('String');

var isFunction = isType('Function');

```

引入isType()函数后，创建isString()、isFunction()函数就变得简单多了。**这种通过指定部分参数来产生一个新的定制函数的形式就是偏函数**。尝试对异步方法进行try/catch操作只能捕获当次事件循环内的异常，对callback执行时抛出的异常将无能为力。Node在处理异常上形成了一种约定，将异常作为回调函数的第一个实参传回，如果为空值，则表明异步调用没有异常抛出。

  ```javascript
async(function (err, results) {

 // TODO

});

  ```

  ###  异步编程解决方案

❑事件发布/订阅模式。
❑ Promise/Deferred模式。
❑ 流程控制库。

  ## 内存控制

### 事件驱动与高性能服务器

![](https://cdn.staticaly.com/gh/abottleofmilk/CDN@master/img/20221025003316.png)

❑ 同步式。对于同步式的服务，一次只能处理一个请求，并且其余请求都处于等待状态。
❑ 每进程/每请求。为每个请求启动一个进程，这样可以处理多个请求，但是它不具备扩展性，因为系统资源只有那么多。
❑ 每线程/每请求。为每个请求启动一个线程来处理。尽管线程比进程要轻量，但是由于每个线程都占用一定内存，当大并发请求到来时，内存将会很快用光，导致服务器缓慢。
每线程/每请求的扩展性比每进程/每请求的方式要好，但对于大型站点而言依然不够。

## 异步编程

## 内存控制

### 高效使用内存

与作用域相关的即是标识符查找。所谓标识符，可以理解为变量名。JavaScript 在执行时会去查找该变量定义在哪里。它最先查找的是当前作用域，如果在当前作用域中无法找到该变量的声明，将会向上级的作用域里查找，直到查到为止。

### V8 的垃圾回收机制与内存限制

### 内存指标

process. memoryUsage () 可以查看内存使用情况。

```node
> process.memoryUsage()
{
  rss: 28127232,
  heapTotal: 6320128,
  heapUsed: 4776680,
  external: 984355,
  arrayBuffers: 59622
}
```

rss 是 resident set size 的缩写，即进程的常驻内存部分。进程的内存总共有几部分，一部分是 rss，其余部分在交换区（swap）或者文件系统（filesystem）中。heapTotal 和 heapUsed 对应的是 V8 的堆内存信息。heapTotal 是堆中总共申请的内存量，heapUsed 表示目前堆中使用中的内存量。这 3 个值的单位都是**字节**。 `external` 是指绑定到由 V8 管理的 JavaScript 对象 C++对象的内存使用情况。`arrayBuffers` **代表分配给 ArrayBuffer 和 SharedArrayBuffer 的内存**，包括所有的 Node. js Buffer。
process. memoryUsage () 不同的是，os 模块中的 totalmem () 和 freemem () 这两个方法用于查看操作系统的内存使用情况，它们分别返回系统的总内存和闲置内存，以**字节**为单位。
堆中的内存用量总是小于进程的常驻内存用量，这意味着 Node 中的内存使用并非都是通过 V8 进行分配的。**我们将那些不是通过 V8 分配的内存称为堆外内存**。Buffer 对象不同于其他对象，它不经过 V8 的内存分配机制，所以也不会有堆内存的大小限制。这在于 Node 并不同于浏览器的应用场景。在浏览器中，JavaScript 直接处理字符串即可满足绝大多数的业务需求，而 Node 则需要处理网络流和文件 I/O 流，操作字符串远远不能满足传输的性能需求。
Node 的内存构成主要由通过 V8 进行分配的部分和 Node 自行分配的部分。受 V8 的垃圾回收限制的主要是 V8 的堆内存。

### 大内存应用

由于 Node 的内存限制，操作大文件也需要小心，好在 Node 提供了 stream 模块用于处理大文件。stream 模块是 Node 的原生模块，直接引用即可。stream 继承自 EventEmitter，具备基本的自定义事件功能，同时抽象出标准的事件和方法。它分可读和可写两种。

## 理解Buffer

 ### Buffer结构

   Buffer是一个像Array的对象，但它主要用于操作字节。Buffer对象类似于数组，它的元素为16进制的两位数，即0到255的数值。Buffer是一个典型的JavaScript与C++结合的模块，它将性能相关部分用C++实现，将非性能相关的部分用JavaScript实现。给元素的赋值如果小于0，就将该值逐次加256，直到得到一个0到255之间的整数。如果得到的数值大于255，就逐次减256，直到得到0~255区间内的数值。如果是小数，舍弃小数部分，只保留整数部分。

![](https://cdn.staticaly.com/gh/abottleofmilk/CDN@master/img/20221005231006.png)


  简单而言，slab就是一块申请好的固定大小的内存区域。slab具有如下3种状态。
❑ full：完全分配状态。
❑ partial：部分分配状态。
❑ empty：没有被分配状态。
真正的内存是在 Node 的 C++层面提供的，JavaScript 层面只是使用它。当进行小而频繁的 Buffer 操作时，采用 slab 的机制进行预先申请和事后分配，使得 JavaScript 到操作系统之间不必有过多的内存申请方面的系统调用。对于大块的 Buffer 而言，则直接使用 C++层面提供的内存，而无需细腻的分配操作。

## 网络编程

## 构建 Web 应用

## 玩转进程

## 测试

## 产品化

## 参考

1. [深入浅出Node.js-朴灵-微信读书 (qq.com)](https://weread.qq.com/web/reader/d1b32290718ff65fd1befcckc81322c012c81e728d9d180)
2. [Introduction · deep-into-node (gitbooks.io)](https://yjhjstz.gitbooks.io/deep-into-node/content/)
3. [Node.js技术栈](https://www.bookstack.cn/read/Nodejs-Roadmap/_coverpage.md)