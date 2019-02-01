---
title: Mac下brew使用
toc: true
date: 2019-01-03 11:23:36
tags:
categories: 配置
---

Homebrew将工具安装在自己创建的`/usr/local/Cellar`目录下，并在`/usr/local/bin`建立这些工具的符号链接。

# 安装brew

打开终端，执行下面的命令。

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

# 使用命令

## 通用

| 命令                                  | 说明                         |
| :------------------------------------ | :--------------------------- |
| brew search [TEXT\|/REGEX/]           | 搜索软件                     |
| brew (info\|home\|options) [FORMULA…] | 查询软件信息                 |
| brew install [FORMULA…]               | 安装软件                     |
| brew update                           | 更新brew和所有软件包         |
| brew upgrade [FORMULA…]               | 更新软件包                   |
| brew uninstall [FORMULA…]             | 卸载软件包                   |
| brew list [FORMULA…]                  | 罗列所有已安装的软件包       |
| brew outdated                         | 查看哪些软件包需要更新       |
| brew deps [FORMULA]                   | 显示包依赖                   |
| brew cleanup                          | 删除所有不需要的版本及其缓存 |

## 帮助

| 命令                | 说明                                         |
| ------------------- | -------------------------------------------- |
| man brew            | 查询brew命令的使用手册                       |
| brew help [COMMAND] | 查询brew子命令的使用帮助，如brew help search |

## 排查

| 命令                     | 说明                                      |
| ------------------------ | ----------------------------------------- |
| brew config              | 查看brew的全局配置                        |
| brew doctor              | 检查系统的潜在问题                        |
| brew install -vd FORMULA | 安装软件包打印详细信息，并开启debug功能。 |

# 卸载brew

在终端执行命令：

```bash
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/uninstall)"
```

# 扩展

通过`Homebrew Cask`优雅、简单、快速的安装和管理`OS X`图形界面程序，比如`Google Chrome`和`Dropbox`。安装目录在`/usr/local/Caskroom`

## 安装

```bash
brew install caskroom/cask/brew-cask
```

## 使用

基本用法与`brew`相同，只不过在`brew`后面加了一个`cask`单词。

```bash
# 安装软件
brew cask install google-chrome

# 卸载软件
brew cask uninstall google-chrome
```