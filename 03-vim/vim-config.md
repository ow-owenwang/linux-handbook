# Vim 配置

## 常用场景
- 自定义 Vim
- 提高编辑效率
- 设置编辑器行为

## 配置文件位置
- `~/.vimrc`: 用户配置
- `/etc/vim/vimrc`: 系统配置

## set 指令

### 行号显示
- `:set nu` 或 `:set number`: 显示行号
- `:set nonu` 或 `:set nonumber`: 不显示行号

### 搜索设置
- `:set ic` 或 `:set ignorecase`: 搜寻时忽略大小写
- `:set noic` 或 `:set noignorecase`: 搜寻时不忽略大小写

### 其他常用设置
- `:set hlsearch`: 高亮搜索结果
- `:set incsearch`: 增量搜索（输入时实时搜索）
- `:set tabstop=4`: Tab 宽度为 4
- `:set expandtab`: Tab 转空格
- `:syntax on`: 语法高亮

## 跳转到指定行
- `:n`: 跳转到第 n 行（例如 `:100` 跳转到第 100 行）
- `nG` 或 `ngg`: 在普通模式下跳转到第 n 行

## 永久配置

如果你希望每次启动 Vim 时都默认显示行号，可以将以下命令添加到你的 `~/.vimrc` 配置文件中：

```vim
set number              " 显示行号
set tabstop=4           " Tab 宽度
set expandtab           " Tab 转空格
set hlsearch            " 高亮搜索
set incsearch           " 增量搜索
syntax on               " 语法高亮
set ignorecase          " 搜索时忽略大小写
```

## 延伸阅读
- [vim-basics.md](./vim-basics.md)
- [vim-shortcuts.md](./vim-shortcuts.md)
