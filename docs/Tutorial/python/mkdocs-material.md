---
hide:
  - tags
tags:
  - Document
---
## 前言
教程中的用例可以直接在下方中的配置文件示例中复制。
### 版本与插件信息
+ python 3.11.0
+ mkdocs 1.4.2
+ mkdocs-material 8.5.10
+ jieba 0.42.1
## 基础
### mkdocs常用命令
+ `mkdocs new [dir-name]`- Create a new project.
+ `mkdocs serve` - Start the live-reloading docs server
+ `mkdocs build` - Build the documentation site.
+ `mkdocs help` - Print this help message.
### 安装
```python
pip install mkdocs
pip install mkdocs-material
```
### 发布
#### 使用 GitHub Action
使用GitHub Actions，您可以自动部署项目文档。在您的存储库的根目录下，创建一个新的 GitHub Actions 工作流，例如.github/workflows/ci.yml。
```yml
name: ci 
on:
  push:
    branches:
      - master 
      - main
permissions:
  contents: write
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-python@v4
        with:
          python-version: 3.x
      - run: pip install mkdocs-material 
      - run: mkdocs gh-deploy --force
```
现在，当新提交被推送到master或main分支时，静态站点会自动构建和部署。推送您的更改以查看正在运行的工作流程。您的文档应该很快出现在<username>.github.io/<repository>.
#### 手动式
如果您更喜欢手动部署项目文档，则可以从包含该mkdocs.yml文件的目录中调用以下命令。
```
mkdocs gh-deploy --force
```
#### GitLab
如果您在 GitLab 上托管代码，则可以使用GitLab CI任务运行器将代码部署到GitLab Pages 。在存储库的根目录中，创建名为的任务定义并复制并粘贴以下内容：.gitlab-ci.yml。
```yml
image: python:latest
pages:
  stage: deploy
  script:
    - pip install mkdocs-material
    - mkdocs build --site-dir public
  artifacts:
    paths:
      - public
  rules:
    - if: '$CI_COMMIT_BRANCH == $CI_DEFAULT_BRANCH'
```
### 定制
MkDocs提供了几种自定义主题的方法。为了对 MkDocs 的 Material 进行一些小的调整，您可以将 CSS 和 JavaScript 文件添加到docs目录中。
#### 延伸主题
如果您想更改 HTML 源代码（例如添加或删除某些部分），您可以扩展主题。MkDocs 支持theme extension，这是一种简单的方法来覆盖 MkDocs 的 Material 部分。
```yml
theme:
  name: material
  custom_dir: overrides
```
请保持overrides文件夹和原始主题目录结构一致，因为目录中的任何文件overrides都将替换作为原始主题一部分的同名文件。
```
├─ .icons/                             # Bundled icon sets
├─ assets/
│  ├─ images/                          # Images and icons
│  ├─ javascripts/                     # JavaScript files
│  └─ stylesheets/                     # Style sheets
├─ partials/
│  ├─ integrations/                    # Third-party integrations
│  │  ├─ analytics/                    # Analytics integrations
│  │  └─ analytics.html                # Analytics setup
│  ├─ languages/                       # Translation languages
│  ├─ actions.html                     # Actions
│  ├─ comments.html                    # Comment system (empty by default)
│  ├─ consent.html                     # Consent
│  ├─ content.html                     # Page content
│  ├─ copyright.html                   # Copyright and theme information
│  ├─ feedback.html                    # Was this page helpful?
│  ├─ footer.html                      # Footer bar
│  ├─ header.html                      # Header bar
│  ├─ icons.html                       # Custom icons
│  ├─ language.html                    # Translation setup
│  ├─ logo.html                        # Logo in header and sidebar
│  ├─ nav.html                         # Main navigation
│  ├─ nav-item.html                    # Main navigation item
│  ├─ pagination.html                  # Pagination (used for blog)
│  ├─ palette.html                     # Color palette
│  ├─ post.html                        # Blog post excerpt
│  ├─ search.html                      # Search interface
│  ├─ social.html                      # Social links
│  ├─ source.html                      # Repository information
│  ├─ source-file.html                 # Source file information
│  ├─ tabs.html                        # Tabs navigation
│  ├─ tabs-item.html                   # Tabs navigation item
│  ├─ tags.html                        # Tags
│  ├─ toc.html                         # Table of contents
│  └─ toc-item.html                    # Table of contents item
├─ 404.html                            # 404 error page
├─ base.html                           # Base template
├─ blog.html                           # Blog index page
├─ blog-archive.html                   # Blog archive index page
├─ blog-category.html                  # Blog category index page
├─ blog-post.html                      # Blog post page
└─ main.html                           # Default page
```
#### 覆盖块
为了覆盖部分文件，我们可以用目录中同名同位置的文件替换它overrides。例如，要替换原来的部分，在目录中footer.html创建一个新的部分：footer.html 
```
.
├─ overrides/
│  └─ partials/
│     └─ footer.html
└─ mkdocs.yml
```
MkDocs 现在将在呈现主题时使用新的部分。这可以用任何文件来完成。

除了覆盖部分之外，还可以覆盖（和扩展）模板块，这些块在模板内部定义并包装特定功能。为了设置块覆盖，main.html在目录中创建一个文件overrides：
```
├─ overrides/
│  └─ main.html
└─ mkdocs.yml
```
例如，要覆盖站点标题，请将以下行添加到main.html:
```html
{% extends "base.html" %}

{% block htmltitle %}
  <title>Lorem ipsum dolor sit amet</title>
{% endblock %}
```
如果您打算向块中添加某些内容而不是用新内容完全替换它，{{ super() }}请在块内部使用以包含原始块内容。
```html
{% extends "base.html" %}

{% block scripts %}
  <!-- Add scripts that need to run before here -->
  {{ super() }}
  <!-- Add scripts that need to run afterwards here -->
{% endblock %}

```
主题提供了以下模板块：

| 区块名称    | 目的                             |
| ----------- | -------------------------------- |
| `analytics` | 包装 Google Analytics 集成       |
| `announce`  | 包裹公告栏                       |
| `config`    | 包装 JavaScript 应用程序配置     |
| `container` | 包装主要内容容器                 |
| `content`   | 包装主要内容                     |
| `extrahead` | 用于添加自定义元标记的空块       |
| `fonts`     | 包装字体定义                     |
| `footer`    | 用导航和版权包裹页脚             |
| `header`    | 包装固定标题栏                   |
| `hero`      | 包装英雄预告片（如果有）         |
| `htmltitle` | 包装`<title>`标签                |
| `libs`      | 包装 JavaScript 库（标头）       |
| `outdated`  | 包装版本警告                     |
| `scripts`   | 包装 JavaScript 应用程序（页脚） |
| `site_meta` | 将元标记包装在文档头部           |
| `site_nav`  | 包装站点导航和目录               |
| `styles`    | 包装样式表（也是额外的来源）     |
| `tabs`      | 包装选项卡导航（如果可用）       |


## 设置
### 颜色
### 搜索
内置搜索插件与 Material for MkDocs 无缝集成，添加了带有lunr和lunr-languages的多语言客户端搜索。mkdocs.yml它默认启用，但必须在使用其他插件时重新添加：
```yml
plugins:
  - search
```
#### 多语言
此选项允许包含lunr-languages提供的特定于语言的词干分析器。
```yml
plugins:
  - search:
      lang: 
        - en
        - ru
```
#### 中文分词器
> 安装jieba分词器
```
pip install jieba
```
更改默认的search插件mkdocs.contrib.search.search_index.py
```python
def _add_entry(self, title, text, loc):
        text = text.replace('\u3000', ' ') # 替换中文全角空格
        text = text.replace('\u00a0', ' ')
        text = re.sub(r'[ \t\n\r\f\v]+', ' ', text.strip())

        # 给正文分词
        text_seg_list = jieba.cut_for_search(text) # 结巴分词，搜索引擎模式，召回率更高
        text = " ".join(text_seg_list) # 用空格连接词语

        # 给标题分词
        title_seg_list = jieba.cut(title, cut_all=False) # 结巴分词，精确模式，更可读
        title = " ".join(title_seg_list) # 用空格连接词语

        self._entries.append({
            'title': title,
            'text': str(text.encode('utf-8'), encoding='utf-8'),
            'location': loc
        })
```
- search.highlight # 搜索内容匹配高亮
- search.share # 当用户单击共享按钮时，URL 会自动复制到剪贴板。
- search.suggest # 搜索建议
- separator: `'[\s\-\.]+'` # 设置分割符号
#### 搜索提升
```yml
search:
  boost: 2 
```
#### 搜索排除
```yml
search:
  exclude: true
```
### 使用tag（标签）
#### 配置文件
```yml
plugins:
  - tags:   
        enabled # 默认开启
        tags_file # 置顶标签网页的映射文件 （可通过导航页显示）
theme:
  icon:
    tag:
      <identifier>: <icon> # 配置标识符标签对应的icon，Icons, Emojis中去查找想要的icon,输入一对冒号中的内容(:xxx:)，并将-改为/，例如 :simple-qt: =》 simple/qt
extra:
  tags:
    <tag>: <identifier>  # 配置 tag 匹配标识符
```
#### 用法
> 当启用内置标签插件时，可以为具有 front mattertags属性的文档添加标签。在 Markdown 文件的顶部添加以下行：
```yml
---
tags:
  - HTML5
  - JavaScript
  - CSS
---
```
> 隐藏头部的tags
```yml
---
hide:
  - tags
---
```
#### 配置标签页
[TAGS]用来配置标签列表在文章中的位置，标记指定标签索引的[TAGS]位置，即在呈现页面时将其替换为实际标签索引。
```
# Tags

Following is a list of relevant tags:

[TAGS]

```


## Material配置文件示例
```yml
theme:
  name: material
  icon:
    tag: 
       CSS3: simple/css3   
       Python: simple/python
       default: material/robot-happy # 修改默认的icon
       document: material/file-document
       Qt: simple/qt
  features:
    - navigation.tracking
    - navigation.tabs # 上方
    - navigation.prune # 自动隐藏导航栏
    - search.highlight # 搜索内容匹配高亮
    - search.share #  当用户单击共享按钮时，URL 会自动复制到剪贴板。
    - search.suggest # 搜索建议
plugins:
  - tags:
         tags_file: tags.md
  - search:
         separator: '[\s\-\.]+' # 设置分隔规则
         lang:  
            - en # 支持英语
            - ja # 支持日语
extra:
  tags:
    CSS3: CSS3
    Python: Python
    Document: document
    Qt: Qt
```
## 参考
1. [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/getting-started/)
2. [MkDocs](https://www.mkdocs.org/getting-started/)
3. [Mkdocs Material使用记录](https://shafish.cn/blog/mkdocs/)
4. [mkdocs-material - 中文搜索支持](https://blog.csdn.net/LostSpeed/article/details/127192971)
5. [4行代码为Mkdocs实现简单中文搜索](https://zhuanlan.zhihu.com/p/411854801)