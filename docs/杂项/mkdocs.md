
使用 [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) 创建wiki .

# [安装](https://squidfunk.github.io/mkdocs-material/getting-started/#installation)

使用 `pip` 安装 : `pip install mkdocs-material` .

# 创建网站

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

# [详细配置](https://squidfunk.github.io/mkdocs-material/setup/)

##

# 发布

通过 github action 将内容发布到 github pages.

将如下代码添加到 `.github/workflows/cl.yml` 中:



# 边写边预览

`mkdocs serve` 可以做到边写边实时预览内容.
