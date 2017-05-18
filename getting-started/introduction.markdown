---
layout: getting-started
title: 简介
redirect_from: /getting_started/1.html
---

# {{ page.title }}

{% include toc.html %}

欢迎！

通过这个教程你会领略到 Elixir 的基础，语言的语法，怎么样去定义一个模块，怎么样操作常见的数据结构等等。本章内容着重于确保你安装完成 Elixir 并能成功运行 Elixir 的交互命令行：IEx。

我们所需要的是：

  * Elixir - 版本 1.4.0 或更高
  * Erlang - 版本 18.0 或更高

让我们开始吧！

> 如果你在教程或网站上发现了任何问题，[请给我们提 PR 或者报 Bug](https://github.com/elixir-cn-translate/elixir-cn-translate.github.io)。

## 安装

如果你还没有安装 Elixir ，请访问我们的[安装页面](/install.html)。安装完成后你可以运行 `elixir --version` 来查看当前 Elixir 的版本。

## 交互模式

当你安装 Elixir ，你会得到三个新的命令：`iex` ，`elixir` ，`elixirc` 。如果你是通过源码编译或者打包好的 Elixir 来安装，你能在 `bin` 目录里找到这几个命令。

现在让我们开始，运行 `iex` (如果在 Windows 上就是 `iex.bat`)。在交互模式中，我们可以输入任何 Elixir 表达式并得到结果。让我们通过几个简单的表达式来热个身：

运行 `iex` 并输入下面的表达式：

```iex
Erlang/OTP 19 [erts-8.1] [source] [64-bit] [smp:4:4] [async-threads:10] [hipe] [kernel-poll:false] [dtrace]

Interactive Elixir (1.4.0) - press Ctrl+C to exit (type h() ENTER for help)
iex(1)> 40 + 2
42
iex(2)> "hello" <> " world"
"hello world"
```

请注意一些细节比如版本号之类的可能会跟你电脑上显示的不一样，请不要在意。从现在开始我们在 `iex` 界面里只专注于代码。要想退出 `iex` 按两次 `Ctrl+C` 就行。

看起来我们已经准备好继续了！从下一章开始我们会非常频繁的使用交互命令行，来学习语言的更多方面。

> 注意：如果你用的是 Windows ，你可以试试 `iex.bat --wel` 命令，取决于你使用的控制台，这个命令有可能给你提供更好的使用体验。

## 运行脚本

在对语言的基础熟悉了之后，你可能想写点儿简单的程序。可以把下面的 Elixir 代码放到一个文件里：

```elixir
IO.puts "Hello world from Elixir"
```

保存为 `simple.exs` 并通过 `elixir` 命令来运行：

```bash
$ elixir simple.exs
Hello world from Elixir
```

之后我们会学习如何编译 Elixir 代码（[第8章](/getting-started/modules-and-functions.html)）。如何使用构建工具 Mix （[Mix & OTP 指南](/getting-started/mix-otp/introduction-to-mix.html)）。现在让我们移步到[第2章](/getting-started/basic-types.html)。

## 有问题要问

在学习指南的过程中，通常会产生一些问题，毕竟这也是学习的一部分嘛！下面是一些你可以提问并学到更多 Elixir 知识的地方：

  * [#elixir-lang on freenode IRC](irc://irc.freenode.net/elixir-lang)
  * [Elixir on Slack](https://elixir-slackin.herokuapp.com/)
  * [Elixir Forum](http://elixirforum.com)
  * [elixir tag on StackOverflow](https://stackoverflow.com/questions/tagged/elixir)

当你提问的时候，记住下面两个忠告：

  * 不要问诸如“用 Elixir 怎么做 X”，而是问“如何用 Elixir 解决 Y”。换句话说，不要问如何实现一个具体的解决方案，而是描述问题的本质。描述问题的时候要不带偏见的给出足够的上下文，这有助于你得到正确答案。

  * 当情况不像期待的那样运行良好，在你上报问题的时候请尽可能多的提供相关信息，比如：你的 Elixir 版本，报错信息或堆栈追踪信息。可以使用 [Gist](https://gist.github.com/) 等网站粘贴这些信息。
