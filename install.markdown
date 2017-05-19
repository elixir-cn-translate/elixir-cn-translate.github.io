---
title: "安装 Elixir"
section: install
layout: default
---
{% assign stable = site.data.elixir-versions[site.data.elixir-versions.stable] %}

# {{ page.title }}

{% include toc.html %}

安装 Elixir 最快的方法是通过发行版或使用其中一个可用的安装程序。如果发行版和安装程序都不可用，那么我们建议使用预编译包或者手动编译。

注意，Elixir 需要 Erlang 18.0 或更高版本。 下面的很多说明将会为你自动安装 Erlang。 如果没有，请阅读下面的 “安装 Erlang” 部分。

## 发行版

安装 Elixir 的首选方案。 选择你的操作系统和工具。

如果你的发行版包含旧的 Elixir/Erlang 版本，请参阅下面的部分从版本管理器或源码安装 Elixir/Erlang。

### macOS

  * Homebrew
    * 更新你的 homebrew 到最新版：`brew update`
    * 运行：`brew install elixir`
  * Macports
    * 运行：`sudo port install elixir`

### Unix (and Unix-like)

  * Arch Linux（社区仓库）
    * 运行：`pacman -S elixir`
  * openSUSE（以及 SUSE 企业版 11 SP3+）
    * 添加 Erlang 开发仓库：`zypper ar -f http://download.opensuse.org/repositories/devel:/languages:/erlang/openSUSE_Factory/ erlang`
    * 运行：`zypper in elixir`
  * Gentoo
    * 运行：`emerge --ask dev-lang/elixir`
  * GNU Guix
    * 运行：`guix package -i elixir`
  * Fedora 21（以及更老的版本）
    * 运行：`yum install elixir`
  * Fedora 22（以及更新的版本）
    * 运行：`dnf install elixir`
  * FreeBSD
    * 通过 ports：`cd /usr/ports/lang/elixir && make install clean`
    * 通过 pkg：`pkg install elixir`
  * Ubuntu 12.04/14.04/16.04 或者 Debian 7
    * 添加 Erlang Solutions 仓库：`wget https://packages.erlang-solutions.com/erlang-solutions_1.0_all.deb && sudo dpkg -i erlang-solutions_1.0_all.deb`
    * 运行：`sudo apt-get update`
    * 安装 Erlang/OTP 平台及其所有应用程序：`sudo apt-get install esl-erlang`
    * 安装 Elixir：`sudo apt-get install elixir`

### Windows

  * Web 安装程序
    * [下载安装程序](https://repo.hex.pm/elixir-websetup.exe)
    * 点击下一个，下一个...完成
  * Chocolatey
    * `cinst elixir`

### Raspberry Pi

如果需要，使用你 Raspbian 版本的名称替换 “jessie”。

  * Erlang Solutions 仓库有用于 armhf 的预构建软件包。这相比本地重新编译节省了大量的时间。

  * 获取 Erlang 钥匙

    * `echo "deb http://packages.erlang-solutions.com/debian jessie contrib" | sudo tee /etc/apt/sources.list.d/erlang-solutions.list`
    * 运行：`wget http://packages.erlang-solutions.com/debian/erlang_solutions.asc`
    * 添加到钥匙扣：`sudo apt-key add erlang_solutions.asc`

  * 安装 Elixir
    * 更新 apt 到最新版：`sudo apt update`
    * 运行：`sudo apt install elixir`

### Docker

如果你熟悉 Docker，你可以使用官方 Docker 镜像快速开始使用 Elixir。

  * 进入交互模式
    * 运行：`docker run -it --rm elixir`
  * 在安装有 `elixir` 的容器内进入 Bash
    * 运行：`docker run -it --rm elixir bash`

这些发行版有可能也会自动为你安装 Erlang。 如果没有，请检查下面的 [安装 Erlang](/install.html#安装-erlang) 部分。

### Nanobox

对于使用 [Nanobox](https://nanobox.io) 的开发人员，只需在 `boxfile.yml` 中指定 `elixir` 引擎并执行 `nanobox run` 即可。

```yaml
run.config:
  engine: elixir
```

## 预编译包

Elixir 为每个版本提供了一个预编译的包。首先安装 Erlang，然后下载并解压缩 [最新版本的 Precompiled.zip 文件](https://github.com/elixir-lang/elixir/releases/download/v{{ stable.version }}/Precompiled.zip)。

一旦解压缩完成，你就可以从 `bin` 目录运行 `elixir` 和 `iex` 命令，但是我们建议你 [将 Elixir 的 bin 路径添加到 PATH 环境变量中](#设置-path-环境变量) 以简化开发。

## 使用版本管理器进行编译

有很多工具允许开发人员安装和管理多个 Erlang 和 Elixir 版本。如果你不能如上所述安装 Erlang 或 Elixir，或者你的软件包管理器已经过时，它们将非常有用。以下是其中的一些工具：

  * [asdf](https://github.com/asdf-vm/asdf) - 安装和管理不同的 Elixir 和 Erlang 版本
  * [exenv](https://github.com/mururu/exenv) - 安装和管理不同的 Elixir 版本
  * [kiex](https://github.com/taylor/kiex) - 安装和管理不同的 Elixir 版本
  * [kerl](https://github.com/yrashk/kerl) - 安装和管理不同的 Erlang 版本

如果你更希望手动从源码编译，不用担心，我们也将为你提供指导！

## 从源码编译 (Unix and MinGW)

你需要几个步骤来下载和编译 Elixir。 第一步是 [安装 Erlang](/install.html#安装-erlang)。

接下来，你应该下载 [最新版本](https://github.com/elixir-lang/elixir/releases/tag/v{{ stable.version }}) 的源码（[.zip](https://github.com/elixir-lang/elixir/archive/v{{ stable.version }}.zip)、[.tar.gz](https://github.com/elixir-lang/elixir/archive/v{{ stable.version }}.tar.gz)），解压缩，然后在解压缩后的目录中运行 `make`（注意：如果你在 Windows 上运行，[请阅读此页面设置你的编译环境](https://github.com/elixir-lang/elixir/wiki/Windows)）。

编译后，你可以从 `bin` 目录运行 `elixir` 和 `iex` 命令。建议你 [将 Elixir 的 bin 路径添加到 PATH 环境变量中](#设置-path-环境变量) 以简化开发。

如果你想冒险一点，你也可以从主分支编译：

```bash
$ git clone https://github.com/elixir-lang/elixir.git
$ cd elixir
$ make clean test
```

如果测试通过，你就准备好了。否则，请随时在 [Github 的问题跟踪器](https://github.com/elixir-lang/elixir) 中提出问题。

## 安装 Erlang

Elixir 唯一的先决条件是 Erlang，18.0 或更高版本，可以轻松地使用 [预编译包](https://www.erlang-solutions.com/resources/download.html) 安装。如果你想直接从源码安装，可以在 [Erlang 官网](http://www.erlang.org/download.html) 上找到，或者依照 [Riak 文档](https://docs.basho.com/riak/latest/ops/building/installing/erlang/) 中提供的优秀教程。

对于 Windows 开发人员，我们建议使用预编译包。那些在 Unix 平台上的或许可以通过许多软件包分发工具之一来安装 Erlang。

安装 Erlang 后，你应该可以打开命令行（或命令提示符），并通过键入 `erl` 来检查 `Erlang` 版本。你会看到一些信息如下：

    Erlang/OTP 18 (erts-7) [64-bit] [smp:2:2] [async-threads:0] [hipe] [kernel-poll:false]

注意，这取决于你如何安装 Erlang，Erlang 可执行文件也许不在你的 PATH 中。确保在你的 [PATH](https://en.wikipedia.org/wiki/Environment_variable) 中有 Erlang 可执行文件，否则 Elixir 将无法工作！

## 设置 PATH 环境变量

强烈建议将 Elixir 的 bin 路径添加到 PATH 环境变量中以简化开发。

在 **Windows** 上，有 [不同版本的说明](http://www.computerhope.com/issues/ch000549.htm) 解释这个过程。

在 **Unix 系统** 上，你需要 [找到你的 Shell 配置文件](https://unix.stackexchange.com/a/117470/101951)，然后将下面这行添加到这个配置文件的末尾，以反映你的 Elixir 安装路径：

```bash
export PATH="$PATH:/path/to/elixir/bin"
```

## 检查安装的 Elixir 版本

一旦安装了 Elixir，你就可以通过运行 `elixir --version` 来检查它的版本。
