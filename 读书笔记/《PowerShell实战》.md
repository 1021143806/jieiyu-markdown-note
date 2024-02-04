# 《PowerShell 实战》

## 推荐序

PowerShell 的特点

- 一致性的设计，语法、命名清晰明了
- 简单易学，能兼容现有的脚本程序和命令行工具
- 内置丰富的标准命令（cmd-let），在默认环境下即可完成常见的系统管理工作
- 具备完整的拓展体系（PowerShellGet）、庞大的模块和脚本市场（PowerShell Gallery）
- 完整的强类型支持。它构建在 .NET CLR 基础之上，能接受并返回.NET对象。对象甚至能在管道和进程之间传递。
- 最新的 PowerShell 7 是开源和跨平台的，其推动的不仅是一家企业的产品，二十整个行业。

## 前言

### 为什么使用 PowerShell

PowerShell 的目标是让用户通过脚本自动执行任务，无需学习计算机编程。

### 目标读者

IT 专业人士或系统管理员，每日疲于在一成不变的GUI中四处点击。

### 内容简介

实践教学法，具有大量示例和真实案例。
三部分

- 讲解 PowerShell 新手要掌握的知识
  - 第 1 ~ 7 章 介绍了 PowerShell语言本身
  - 第 8 章 价绍了如何用PowerShell远程处理功能连接远程计算机来执行命令
  - 第 9 章 ==介绍了留下的 PowerShell 测试框架 Pester==。这个框架贯穿本书，经常使用。

- 利用第一部分所学的知识来自动执行一些常见的任务
  - 第 10 ~ 13 章 讨论了如何解析结构化数据，以及很多IT管理员经常使用的服务。
  - 第 14 章 展示了如何构建工具，以便在自己的环境中清点服务器
- 重点构建了名为 PowerLab 的 PowerShell 模块，借此演示了 PowerShell 的功能。这部分涵盖优秀的模块设计方式以及与函数相关的最佳实践。
  - 第 15 ~ 20 章 介绍了如何使用 PowerShell 实现整个实验室的自动化，以及如何自动测试服务器环境。

## 第一部分 基础知识

### 第 1 章 上手体验

#### 1.1 打开 PowerShell 控制台

#### 1.2 使用 DOS 命令

命令|注释
:---:|:----:
TAB | 键补齐
cd | 进入目录
dir | 显示当前目录内容
cls | 清空屏幕

#### 1.3 探索 PowerShell 命令

命令分类

1. cmdlet
2. 函数
3. 别名
4. 外部脚本

Get-Command 命令

``` powershell
PS C:\Users\375563> get-command -name get-alias

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-Alias                                          3.1.0.0    Microsoft.PowerShell.Utility
```

#### 1.4 获取帮助

##### 1.4.1 显示文档

``` powershell
PS C:\Users\375563> get-help add-content

名称
    Add-Content

摘要
    Adds content to the specified items, such as adding words to a file.


语法
    Add-Content [-Value] <System.Object[]> [-Credential <System.Management.Automation.PSCredential>] [-Encoding {AS
    CII | BigEndianUnicode | BigEndianUTF32 | Byte | Default | OEM | String | Unicode | Unknown | UTF7 | UTF8 | UTF
    32}] [-Exclude <System.String[]>] [-Filter <System.String>] [-Force] [-Include <System.String[]>] -LiteralPath
    <System.String[]> [-NoNewline] [-PassThru] [-Stream <System.String>] [-UseTransaction] [-Confirm] [-WhatIf] [<C
    ommonParameters>]

    Add-Content [-Path] <System.String[]> [-Value] <System.Object[]> [-Credential <System.Management.Automation.PSC
    redential>] [-Encoding {ASCII | BigEndianUnicode | BigEndianUTF32 | Byte | Default | OEM | String | Unicode | U
    nknown | UTF7 | UTF8 | UTF32}] [-Exclude <System.String[]>] [-Filter <System.String>] [-Force] [-Include <Syste
    m.String[]>] [-NoNewline] [-PassThru] [-Stream <System.String>] [-UseTransaction] [-Confirm] [-WhatIf] [<Common
    Parameters>]


说明
    The `Add-Content` cmdlet appends content to a specified item or file. Content can be passed in from the pipelin
    e or specified by using the Value parameter.

    If you need to create files or directories for the following examples, see New-Item (New-Item.md).

```

##### 1.4.2 学习一般主题

#### 1.5 更新文档

update-help

### 第 2 章 PowerShell 基本概念

“一切皆对象”

#### 2.1 变量

变量用于存储值

##### 2.1.1 显示及修改变量

变量以（$）开头
显示变量值

``` powershell
PS C:\Users\375563> $MaximumHistoryCount
4096
```

$MaximumHistoryCount 是一个内置变量，指明了 PowerShell 在命令历史中最多存储多少个命令，默认为4096个。

修改变量的值

``` powershell
PS C:\Users\375563> $MaximumHistoryCount = 200
PS C:\Users\375563> $MaximumHistoryCount
200
```

在 PowerShell 中变量分为两大类：

1. 用户定义的变量
2. 自动变量，即 PowerShell 自带的变量

##### 2.1.2 用户定义的变量

启用严格模式

```powershell
set-strictmode -version latest
```

严格模式下，倘若违背良好的编程实践，PowerShell 将抛出错误。一般不启用
帮助

```powershell
get-help set-strictmode -examples
```

创建变量

```powershell
#color = 'bulu'
```

用 Set-Variable 命令创建一个变量
用 Get-Variavle 命令显示该变量的值

```powershell
PS C:\Users\375563> Set-Variable -name color1 -value bule1
PS C:\Users\375563> get-Variable -name color1

Name                           Value
----                           -----
color1                         bule1
```

Set-Variable 还可以返回所有可用变量
