

使用 [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)创建面向（技术）项目文档的静态站点。

## 快速入门

### 安装

使用 `pip` 安装 : `pip install mkdocs-material` .

### 创建网站

在希望最为项目根目录的位置使用 `mkdocs new .` 初始化内容，其文件结构如下:

```
.
├─ docs/
│  └─ index.md
└─ mkdocs.yml
```

可以在配置文件 `mkdocs.yml` 中添加如下字段以启用主题 material:
```yaml
theme:
  name: material
```

### 预览与构建

如果需要编辑时预览内容（即所见即所得），可以运行如下命令：

```bash
mkdocs serve
```

即可在[localhost:8000](http://127.0.0.1:8000)查看对应的渲染内容。

在构建完成后，可以运行如下指令生成静态页面：

```bash
mkdocs build
```

### 发布到github

> https://squidfunk.github.io/mkdocs-material/publishing-your-site/#github-pages

使用 [github action](https://github.com/features/actions) 创建自动化工作流：

```yaml
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
      - run: echo "cache_id=$(date --utc '+%V')" >> $GITHUB_ENV 
      - uses: actions/cache@v3
        with:
          key: mkdocs-material-${{ env.cache_id }}
          path: .cache
          restore-keys: |
            mkdocs-material-
      - run: pip install mkdocs-material 
      - run: mkdocs gh-deploy --force
```

当新的修改提交到 main / master 分支后将会自动生成和部署静态站点。

## 配置与自定义

如果需要添加一些例如css/js或者其他资源，可以查看[此处](https://squidfunk.github.io/mkdocs-material/customization/)。

关于详细的配置和一些特定语法的内容查看[material setup](https://squidfunk.github.io/mkdocs-material/setup/)部分，以下只对其重要配置或需要注意的语法进行简述。

- [修改主题的颜色/亮色暗色模式](https://squidfunk.github.io/mkdocs-material/setup/changing-the-colors/#changing-the-colors)
- [字体](https://squidfunk.github.io/mkdocs-material/setup/changing-the-fonts/)
- [语言](https://squidfunk.github.io/mkdocs-material/setup/changing-the-language/)
- [logo与icon](https://squidfunk.github.io/mkdocs-material/setup/changing-the-logo-and-icons/#icon-bundled)
- 

[详细配置](https://squidfunk.github.io/mkdocs-material/setup/)查看此处,包括有设置颜色、语言、导航、页眉页脚等.

如果设置 TOC 后未显示,请注意 HTML 只能有一个 H1 ,即只能有一个一级标题.



## 语法

### 代码块相关内容

#### 代码块注释

``` yaml
theme:
  features:
    - content.code.annotate # (1)
```

1.  :man_raising_hand: I'm a code annotation! I can contain `code`, __formatted
    text__, images, ... basically anything that can be written in Markdown.

#### 代码块行号

``` py linenums="1"
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
```

#### 高亮特定行

``` py hl_lines="2 3"
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
```

#### 高亮内联代码块

The `#!python range()` function is used to generate a sequence of numbers.

### [数学公式](https://squidfunk.github.io/mkdocs-material/reference/mathjax/)
