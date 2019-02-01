---
title: Mac下多Python环境
toc: true
date: 2018-04-28 09:46:53
tags: Python
categories: 配置

---



# 多版本python的安装路径识别

```bash
# xiny @ XinY in ~ [9:52:55]
$ which python
/Users/xiny/anaconda2/bin/python

# xiny @ XinY in ~ [9:53:04]
$ which python2.7
/Users/xiny/anaconda2/bin/python2.7

# xiny @ XinY in ~ [9:53:09]
$ which python3
/usr/local/bin/python3

# xiny @ XinY in ~ [9:53:15]
$ which python3.6
/usr/local/bin/python3.6
```

```bash
# xiny @ XinY in ~ [9:53:20]
$ ll /Users/xiny/anaconda2/bin/python
lrwxr-xr-x  1 xiny  staff     9B  1 17 15:58 /Users/xiny/anaconda2/bin/python -> python2.7

# xiny @ XinY in ~ [9:53:49]
$ ll /Users/xiny/anaconda2/bin/python2.7
-rwxrwxr-x  1 xiny  staff    12K  1 17 15:53 /Users/xiny/anaconda2/bin/python2.7
# xiny @ XinY in ~ [9:54:06]
$ ll /usr/local/bin/python3
lrwxr-xr-x  1 xiny  admin    34B  3  6 16:41 /usr/local/bin/python3 -> ../Cellar/python/3.6.4/bin/python3

# xiny @ XinY in ~ [9:54:36]
$ ll /usr/local/bin/python3.6
lrwxr-xr-x  1 xiny  admin    36B  3  6 16:41 /usr/local/bin/python3.6 -> ../Cellar/python/3.6.4/bin/python3.6
```

# 删除Python

Python安装后自动生成：

- Python framework，即Python框架；
- Python应用目录；
- 指向Python的连接

## 常见Python安装目录

对于Mac自带的Python，其框架目录为：

```bash
/System/Library/Frameworks/Python.framework
```

官网Python，其默认目录框架为：

```bash
/Library/Frameworks/Python.framework
```

brew安装的Python，其默认目录框架为：

```bash
/usr/local/Cellar
```

anaconda安装的Python，目录为用户指定目录：

```bash
/Users/xiny/anaconda
```



## 系统与官网Python删除

删除Python就要删除以上3部分：

1. 删除框架：

   ```bash
   sudo rm -rf /Library/Frameworks/Python.framework/Versions/x.x
   ```

2. 删除应用目录

   ```bash
   sudo rm -rf "/Applications/Python x.x"​
   ```

3. 删除指向Python的连接

   ```bash
   cd /usr/local/bin/
   ls -l /usr/local/bin | grep '../Library/Frameworks/Python.framework/Versions/x.x' | awk '{print $9}' | tr -d @ | xargs rm
   ```

## brew卸载Python

```bash
brew uninstall python
```

## conda卸载Python

直接删除anaconda，并在用户配置文件中删除anaconda的路径

