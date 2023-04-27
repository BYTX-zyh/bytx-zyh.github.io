

使用 [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) 创建wiki .

## [安装](https://squidfunk.github.io/mkdocs-material/getting-started/#installation)

使用 `pip` 安装 : `pip install mkdocs-material` .

## 创建网站

使用 `mkdocs new .` 初始化内容,其文件结构如下:
```
.
├─ docs/
│  └─ index.md
└─ mkdocs.yml
```

可以在配置文件 `mkdocs.yml` 中添加如下字段以启用主题:
```yaml
theme:
  name: material
```

## 详细配置

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



## 发布

将[此处](https://squidfunk.github.io/mkdocs-material/publishing-your-site/#material-for-mkdocs)代码添加到 `.github/workflows/cl.yml` 中,而后从 github 中转到 settings-pages ,将其设置为从 gh-pages 分支发布网站即可(可能需要清空缓存重新打开).

## 边写边预览

`mkdocs serve` 可以做到边写边实时预览内容.
