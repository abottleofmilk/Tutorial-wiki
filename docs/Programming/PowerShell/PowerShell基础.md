
## cmdlet
### 什么是 cmdlet？
cmdlet 是本机 PowerShell 命令，而不是独立的可执行文件。 cmdlet 收集在 PowerShell 模块中，可按需加载。 可以用任何编译的 .NET 语言或 PowerShell 脚本语言本身来编写 cmdlet。PowerShell 使用“动词-名词”名称对来命名 cmdlet。

PowerShell 包含 cmdlet，它们可帮助你探索 PowerShell。 通过使用下面三个 cmdlet，可以了解有哪些命令可用、这些命令执行什么操作，以及它们在什么类型上运行。

Get-Verb. 运行此命令时，将返回大多数命令遵循的谓词的列表。 响应包括有关这些谓词的功能的说明。 由于大多数命令都遵循这种命名，因此它对命令的功能设置了预期目标。 如果你要创建命令，这有助于选择适当的命令和命令名称。
Get-Command. 此命令会检索计算机上安装的所有命令的列表。
Get-Member. 它在基于对象的输出上运行，并且能够发现可用于命令的对象、属性和方法。
Get-Help. 以命令名称为参数调用此命令，将显示一个帮助页面，其中说明了命令的各个部分。
### IEX
IEX is an acronym for the PowerShell command Invoke-Expression.
### ISE
Windows PowerShell 集成脚本环境 (ISE) 是 Windows PowerShell 的主机应用程序。 在 ISE 中，可以在单个基于 Windows 的图形用户界面中运行命令并编写、测试和调试脚本。 ISE 提供多行编辑、Tab 自动补全、语法颜色设置、选择性执行、上下文相关帮助以及对从右到左语言的支持。 将菜单项和键盘快捷方式映射到许多将会在 Windows PowerShell 控制台中执行的相同任务。
## PowerShell库
PowerShell 库是 PowerShell 内容的中心存储库。 在 PowerShell 库中，可找到包含 PowerShell cmdlet 和 Desired State Configuration (DSC) 资源的 PowerShell 脚本和模块。 其中一些包由 Microsoft 编写，另一些包由 PowerShell 社区编写。
