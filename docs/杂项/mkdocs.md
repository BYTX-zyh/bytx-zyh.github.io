
[TOC]

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

[详细配置](https://squidfunk.github.io/mkdocs-material/setup/)查看此处,包括有设置颜色、语言、导航、页眉页脚等.


# 发布

将[此处](https://squidfunk.github.io/mkdocs-material/publishing-your-site/#material-for-mkdocs) 代码添加到 `.github/workflows/cl.yml` 中,而后从 github 中转到 settings-pages ,将其设置为从 gh-pages 分支发布网站即可(可能需要清空缓存重新打开).

# 边写边预览

`mkdocs serve` 可以做到边写边实时预览内容.
