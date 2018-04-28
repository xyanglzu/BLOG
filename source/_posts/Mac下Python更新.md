---
title: Mac下Python更新及conda操作
toc: true
date: 2018-04-28 10:43:38
tags:
categories: Python

---

0.0

<!--more-->

# conda操作

## conda更新

```bash
# 更新anaconda
conda update anaconda

# 更新conda
conda update conda

# 更新python
conda update python

# 更新包
conda update -all
```

## conda环境管理

```bash
# 创建一个名为python34的环境，指定Python版本是3.4（不用管是3.4.x，conda会为我们自动寻找3.4.x中的最新版本）
conda create --name python34 python=3.4
 
# 安装好后，使用activate激活某个环境
activate python34 # for Windows
source activate python34 # for Linux & Mac
# 激活后，会发现terminal输入的地方多了python34的字样，实际上，此时系统做的事情就是把默认2.7环境从PATH中去除，再把3.4对应的命令加入PATH
 
# 此时，再次输入
python --version
# 可以得到`Python 3.4.5 :: Anaconda 4.1.1 (64-bit)`，即系统已经切换到了3.4的环境
 
# 如果想返回默认的python 2.7环境，运行
deactivate python34 # for Windows
source deactivate python34 # for Linux & Mac
 
# 删除一个已有的环境
conda remove --name python34 --all

# 在当前环境下安装anaconda包集合
conda install anaconda
```

## conda包管理

```bash
# 查看当前环境下已安装的包
conda list

# 查看某个指定环境的已安装包
conda list -n python34

# 查找package信息
conda search numpy

# 安装package
conda install -n python34 numpy
# 如果不用-n指定环境名称，则被安装在当前活跃环境
# 也可以通过-c指定通过某个channel安装

# 更新package
conda update -n python34 numpy

# 删除package
conda remove -n python34 numpy
```

## conda源配置

```bash
# 配置路径
~/.condarc

# 添加Anaconda的TUNA镜像
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
# TUNA的help中镜像地址加有引号，需要去掉

# 设置搜索时显示通道地址
conda config --set show_channel_urls yes
```



# pip操作

## pip配置源

```bash
# 配置文件路径
~/.pip/pip.conf

# 修改配置文件内容
[global] 
trusted-host=pypi.tuna.tsinghua.edu.cn 
index-url = https://pypi.tuna.tsinghua.edu.cn/simple

#全部更新pip的安装包
# mac ubuntu
pip freeze --local | grep -v '^\-e' | cut -d = -f 1  | xargs -n1 pip install -U
# windows
pip freeze > requirements.txt 
pip install -r requirements.txt –upgrade 
del requirements.txt
```

