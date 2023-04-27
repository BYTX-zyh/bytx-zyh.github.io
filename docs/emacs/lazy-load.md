
## 简介

emacs 启动缓慢主要有两个原因：

1. 启动时垃圾回收阈值过小，导致插件加载时触发垃圾回收,拖慢启动速度。
2. 启动时加载过多插件，导致启动时花费过多时间在插件加载上，而某些插件可能并不会用到(例如在编写golang时应该是用不到css相关的插件的)。

对于第一个原因可以通过增大启动时GC阈值来缓解：

```elisp
(let (;; temporarily increase `gc-cons-threshold' when loading to speed up startup.
      (gc-cons-threshold most-positive-fixnum)
      ;; Empty to avoid analyzing files when loading remote files.
      (file-name-handler-alist nil))

    ;; Emacs configuration file content is written below.

)
```

而第二个原因可以采用[lazy-load](https://github.com/manateelazycat/lazy-load)来做到，其核心思路为：

1. 定义keymap与对应的调用函数。
2. 告知emacs该函数对应的插件的文件名(或配置文件名)，以便调用函数时加载提供该函数的插件。
3. 默认情况下， Emacs 只加载很少的插件。加载完成后，当第一次按下某个键时, Emacs 会动态加载插件和相应的功能。

建议通过 lazy-load 管理快捷键，而非快捷键管理散落在不同的插件配置文件中，难以管理调整。

## 使用方法

## 全局设置快捷键

```elisp
(lazy-load-global-keys
 '(("M-g" . goto-line-preview))
 "goto-line-preview")
```

全局设置了一个绑定的快捷键，并将其绑定到文件 `goto-line-preview` 中。

### 为某个 mode 设置快捷键

```elisp
(lazy-load-local-keys
 '(("C-c t" . ruby-hash-syntax-toggle))
 Ruby-mode-map
 "ruby-extension")
```

### 使用前缀键

```elisp
(lazy-load-global-keys
 '(("p" . sdcv-search-pointer)
   ("y" . sdcv-search-pointer+)
   ("i" . sdcv-search-input)
   (";" . sdcv-search-input+))
 "init-sdcv"
 "C-z")
```

### 卸载emacs默认按键

通常有些默认的快捷键已经被其余功能占用，则不在需要这些默认的快捷键绑定，可以采用如下方式卸载:

```elisp
(lazy-load-unset-keys '("C-x C-f" "C-z" "C-q" "s-W" "s-z" "M-h" "C-x C-c" "C-\\" "s-c" "s-x" "s-v"))
```

### 为已经加载的内容设置快捷键

此设置可用于对应在emacs启动时默认加载的插件/功能，为其设置快捷键:

```elisp
(lazy-load-set-keys
 '(("M-;" . comment-dwim-with-haskell-style))
 Haskell-mode-map)
```
