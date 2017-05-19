---
title: Elixir 文档
section: docs
layout: default
---

## 文档

选择你想要的文档版本。

{% assign stable = site.data.elixir-versions[site.data.elixir-versions.stable] %}

<h4 id="stable">稳定版
  {% if stable.docs_zip == true %}
    <small>(<a href="https://github.com/elixir-lang/elixir/releases/download/v{{ stable.version }}/Docs.zip">下载</a>)</small>
  {% endif %}
</h4>

* [Elixir](https://hexdocs.pm/elixir/) - 标准库
* [EEx](https://hexdocs.pm/eex/) - 模版库
* [ExUnit](https://hexdocs.pm/ex_unit/) - 单元测试库
* [IEx](https://hexdocs.pm/iex/) - 交互式 Shell
* [Logger](https://hexdocs.pm/logger/) - 内置日志库
* [Mix](https://hexdocs.pm/mix/) - 构建工具

#### 开发版

* [Elixir](https://hexdocs.pm/elixir/master/) - 标准库
* [EEx](https://hexdocs.pm/eex/master/) - 模版库
* [ExUnit](https://hexdocs.pm/ex_unit/master/) - 单元测试库
* [IEx](https://hexdocs.pm/iex/master/) - 交互式 Shell
* [Logger](https://hexdocs.pm/logger/master/) - 内置日志库
* [Mix](https://hexdocs.pm/mix/master/) - 构建工具

{% for version in site.data.elixir-versions reversed %}
  {% if version[0] == 'stable' %}
    {% continue %}
  {% endif %}

<h4 id="{{ version[1].name }}">{{ version[1].name }}
  {% if version[1].docs_zip == true %}<small>(<a href="https://github.com/elixir-lang/elixir/releases/download/v{{ version[1].version }}/Docs.zip">下载</a>)</small>{% endif %}
</h4>

* [Elixir](https://hexdocs.pm/elixir/{{ version[1].version }}/) - 标准库
* [EEx](https://hexdocs.pm/eex/{{ version[1].version }}/) - 模版库
* [ExUnit](https://hexdocs.pm/ex_unit/{{ version[1].version }}/) - 单元测试库
* [IEx](https://hexdocs.pm/iex/{{ version[1].version }}/) - 交互式 Shell
* [Logger](https://hexdocs.pm/logger/{{ version[1].version }}/) - 内置日志库
* [Mix](https://hexdocs.pm/mix/{{ version[1].version }}/) - 构建工具
{% endfor %}
