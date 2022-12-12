## 术语
+ Python Package Index 是一个开源许可的软件包公共存储库，可供所有 Python 用户使用
+ Python Packaging Authority 是负责标准打包工具以及相关元数据和文件格式标准维护与改进的开发人员和文档作者团队。 他们基于 GitHub 和 Bitbucket 这两个平台维护着各种工具、文档和问题追踪系统。
+ distutils 是 1998 年首次添加到 Python 标准库的原始构建和分发系统。 虽然直接使用 distutils 正在逐步淘汰，但它仍然为当前的打包和分发基础架构奠定了基础它不仅仍然是标准库的一部分，而且它的名称还以其他方式存在（例如用于协调 Python 打包标准开发的邮件列表的名称）。
+ setuptools （在很大程度上）是作为 distutils 的取代者，于 2004 年首次发布。 它对未经修改的 distutils 工具最重要的补充是能够声明对其他包的依赖。 目前它被推荐用来替代 distutils，其更新更为频繁，在更为多样的 Python 版本之上为最新的打包标准提供持续支持。
+ wheel （在此上下文中）是一个将 bdist_wheel 命令添加到 distutils/setuptools 的项目。这产生了一个跨平台的二进制打包格式（称为“轮子”或“轮子文件”，并在 PEP 427 中定义），它允许在系统上安装Python库，甚至包括二进制扩展的库，而不需在本地进行构建。

```python
python -m pip install setuptools wheel twine
```