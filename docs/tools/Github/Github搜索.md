## Github上开始搜索

### 关于再Github上搜索

您可以在所有 GitHub 中进行全局搜索，也可以将搜索范围限定为特定的存储库或组织。

 ### GitHub 上的搜索类型

- [Repositories](https://docs.github.com/en/search-github/searching-on-github/searching-for-repositories) 存储库
- [Topics](https://docs.github.com/en/search-github/searching-on-github/searching-topics) 主题
- [Issues and pull requests](https://docs.github.com/en/search-github/searching-on-github/searching-issues-and-pull-requests) 问题与请求
- [Discussions](https://docs.github.com/en/search-github/searching-on-github/searching-discussions) 讨论
- [Code](https://docs.github.com/en/search-github/searching-on-github/searching-code) 代码
- [Commits](https://docs.github.com/en/search-github/searching-on-github/searching-commits) 提交
- [Users](https://docs.github.com/en/search-github/searching-on-github/searching-users) 用户
- [Packages](https://docs.github.com/en/search-github/searching-on-github/searching-for-packages) 包
- [Wikis](https://docs.github.com/en/search-github/searching-on-github/searching-wikis) 维基

### 可视化搜索



### 搜索语法

#### 表达式

| Query  | Example                                                      |
| ------ | ------------------------------------------------------------ |
| `>n`   | **[cats stars:>1000](https://github.com/search?utf8=✓&q=cats+stars%3A>1000&type=Repositories)** matches repositories with the word "cats" that have more than 1000 stars. |
| `>=n`  | **[cats topics:>=5](https://github.com/search?utf8=✓&q=cats+topics%3A>%3D5&type=Repositories)** matches repositories with the word "cats" that have 5 or more topics. |
| `<n`   | **[cats size:<10000](https://github.com/search?utf8=✓&q=cats+size%3A<10000&type=Code)** matches code with the word "cats" in files that are smaller than 10 KB. |
| `<=n`  | **[cats stars:<=50](https://github.com/search?utf8=✓&q=cats+stars%3A<%3D50&type=Repositories)** matches repositories with the word "cats" that have 50 or fewer stars. |
| `n..*` | **[cats stars:10..\*](https://github.com/search?utf8=✓&q=cats+stars%3A10..\*&type=Repositories)** is equivalent to and matches repositories with the word "cats" that have 10 or more stars.`stars:>=10` |
| `*..n` | **[cats stars:\*..10](https://github.com/search?utf8=✓&q=cats+stars%3A"\*..10"&type=Repositories)** is equivalent to and matches repositories with the word "cats" that have 10 or fewer stars.`stars:<=10` |

#### 范围

| 查询   | 例                                                           |
| :----- | :----------------------------------------------------------- |
| `n..n` | **[cats stars:10..50](https://github.com/search?utf8=✓&q=cats+stars%3A10..50&type=Repositories)** matches repositories with the word "cats" that have between 10 and 50 stars. |

#### 日期

| Query                                       | Example                                                      |
| :------------------------------------------ | :----------------------------------------------------------- |
| `>*YYYY*-*MM*-*DD*`                         | **[cats created:>2016-04-29](https://github.com/search?utf8=✓&q=cats+created%3A>2016-04-29&type=Issues)** matches issues with the word "cats" that were created after April 29, 2016. |
| `>=*YYYY*-*MM*-*DD*`                        | **[cats created:>=2017-04-01](https://github.com/search?utf8=✓&q=cats+created%3A>%3D2017-04-01&type=Issues)** matches issues with the word "cats" that were created on or after April 1, 2017. |
| `<*YYYY*-*MM*-*DD*`                         | **[cats pushed:<2012-07-05](https://github.com/search?q=cats+pushed%3A<2012-07-05&type=Code&utf8=✓)** matches code with the word "cats" in repositories that were pushed to before July 5, 2012. |
| `<=*YYYY*-*MM*-*DD*`                        | **[cats created:<=2012-07-04](https://github.com/search?utf8=✓&q=cats+created%3A<%3D2012-07-04&type=Issues)** matches issues with the word "cats" that were created on or before July 4, 2012. |
| `*YYYY*-*MM*-*DD*..*YYYY*-*MM*-*DD*`        | **[cats pushed:2016-04-30..2016-07-04](https://github.com/search?utf8=✓&q=cats+pushed%3A2016-04-30..2016-07-04&type=Repositories)** matches repositories with the word "cats" that were pushed to between the end of April and July of 2016. |
| `*YYYY*-*MM*-*DD*..*`                       | **[cats created:2012-04-30..\*](https://github.com/search?utf8=✓&q=cats+created%3A2012-04-30..\*&type=Issues)** matches issues created after April 30th, 2012 containing the word "cats." |
| `*..*YYYY*-*MM*-*DD*`                       | **[cats created:\*..2012-07-04](https://github.com/search?utf8=✓&q=cats+created%3A\*..2012-07-04&type=Issues)** matches issues created before July 4th, 2012 containing the word "cats." |
| `*YYYY*-*MM*-*DD*T*HH*:*MM*:*SS*+*00*:*00*` | **[cats created:2017-01-01T01:00:00+07:00..2017-03-01T15:30:15+07:00](https://github.com/search?utf8=✓&q=cats+created%3A2017-01-01T01%3A00%3A00%2B07%3A00..2017-03-01T15%3A30%3A15%2B07%3A00&type=Issues)** matches issues created between January 1, 2017 at 1 a.m. with a UTC offset of and March 1, 2017 at 3 p.m. with a UTC offset of .`07:00``07:00` |
| `*YYYY*-*MM*-*DD*T*HH*:*MM*:*SS*Z`          | **[cats created:2016-03-21T14:11:00Z..2016-04-07T20:45:00Z](https://github.com/search?utf8=✓&q=cats+created%3A2016-03-21T14%3A11%3A00Z..2016-04-07T20%3A45%3A00Z&type=Issues)** matches issues created between March 21, 2016 at 2:11pm and April 7, 2016 at 8:45pm. |

#### 排除结果

您可以使用语法排除包含特定单词的结果。运算符只能用于字符串关键字。它不适用于数字或日期。

| Query        | Example                                                      |
| :----------- | :----------------------------------------------------------- |
| `-QUALIFIER` | **[`cats stars:>10 -language:javascript`](https://github.com/search?q=cats+stars%3A>10+-language%3Ajavascript&type=Repositories)** matches repositories with the word "cats" that have more than 10 stars but are not written in JavaScript. |
| `NOT`        | **[hello NOT world](https://github.com/search?q=hello+NOT+world&type=Repositories)** matches repositories that have the word "hello" but not the word "world." |

#### 带空格的查询

如果搜索查询包含空格，则需要用引号将其括起来。

- [cats NOT "hello world"](https://github.com/search?utf8=✓&q=cats+NOT+"hello+world"&type=Repositories) matches repositories with the word "cats" but not the words "hello world."
- [build label:"bug fix"](https://github.com/search?utf8=✓&q=build+label%3A"bug+fix"&type=Issues) matches issues with the word "build" that have the label "bug fix."

#### 使用用户名的查询

| Query                | Example                                                      |
| :------------------- | :----------------------------------------------------------- |
| `QUALIFIER:USERNAME` | [`author:nat`](https://github.com/search?q=author%3Anat&type=Commits) matches commits authored by @nat |
| `QUALIFIER:@me`      | [`is:issue assignee:@me`](https://github.com/search?q=is%3Aissue+assignee%3A@me&type=Issues) matches issues assigned to the person viewing the results |

### 常见问题

在极少数情况下，当查询超过时间限制时，搜索将返回在超时之前找到的所有匹配项，并通知您发生了超时。达到超时并不一定意味着搜索结果不完整。这只是意味着查询在搜索所有可能的数据之前已停止。

- 不支持超过 256 个字符的查询
- 不能使用五个以上的运算符构造查询`AND``OR``NOT`

### 对搜索结果排序

#### 按交互排序

#### 按反应排序



## 某个仓库搜索文件

1. 在 GitHub.com 上，导航到存储库的主页。
2. 在文件列表上方，单击go to file。
3. 在搜索字段中，输入您要查找的文件的名称。
4. 在结果列表中，单击要查找的文件。

#### 自定义排除的文件
默认情况下，文件查找器结果不包括以下目录中的文件（如果这些文件存在于存储库根目录中）：

- `.git`
- `.hg`
- `.sass-cache`
- `.svn`
- `build`
- `dot_git`
- `log`
- `tmp`
- `vendor`

您可以使用文件覆盖这些默认排除项。`.gitattributes`
