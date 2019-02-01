---
title: Mac下iterm2快捷键及配置
toc: true
date: 2018-12-13 15:40:16
tags: iterm2
categories: 配置
---

# 语法高亮

1. 使用homebrew包管理工具安装 zsh-syntax-highlighting 插件

```bash
brew install zsh-syntax-highlighting`
# 如果电脑上还没有安装homebrew，请先安装homebrew
`/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

2. 配置.zshrc文件，插入一行

`source   source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh`

3. 加载.zshrc配置

```bash
source ~/.zshrc
```

4. 重新打开iTerm2窗口（或新打开一个iTerm2窗口）即可以看到效果

## 自动提示及命令补全

1. 克隆仓库到本地 ~/.oh-my-zsh/custom/plugins 路径下

```
git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
```

2. 用 vim 编辑 .zshrc 文件，找到插件设置命令，默认是 `plugins=(git)` ，我们把它修改为`plugins=(zsh-autosuggestions git)`

PS：当你重新打开终端时可能看不到变化，可能你的字体颜色太淡了，我们把其改亮一些：

1. `cd ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions`
2. 用 vim 编辑 zsh-autosuggestions.zsh 文件，修改`ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE='fg=10'`

# 快捷键

## 标签

```
新建标签: command + t
关闭标签: command + w
切换标签: command + 数字 / command + 左右方向键
切换全屏: command + enter
查找: command + f
```

## 分屏

```
垂直分屏: command + d
水平分屏: command + shift + d
```

## 命令

```
查看剪切板历史: command + shift + h
上一条命令: ctrl + p
搜索命令: ctrl + r
```

## 光标控制

```
清除当前行: ctrl + u
到行首: ctrl + a
到行尾: ctrl + e
前进后退: ctrl + f/b
删除当前光标的字符: ctrl + d
删除光标之前的字符: ctrl + h
删除光标之前的单词: ctrl + w
删除到文本末尾: ctrl + k
```

## 其他

```
清屏: command + r / ctrl + l / clear
```



