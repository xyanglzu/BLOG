title: git及github配置
toc: true
date: 2019-02-01 10:53:44
tags:
categories: 配置

# 本地与github远程仓库配置

# 本地生成ssh密钥

1. 打开终端，输入命令`cd`进入用户目录

2. 输入以下命令生成ssh密钥

   ```bash
   ssh-keygen -t rsa -C "你的邮箱" # 一路回车即可
   ```
3. 之后在用户目录`~/.ssh/id_rsa.pub`就是你的ssh key公钥了

## github添加本地密钥公钥

1. 打开GitHub个人配置

   ![image-20190201111007971](https://ws1.sinaimg.cn/large/006tNc79ly1fzqqz1olm9j306t09ht8y.jpg)

2. ![image-20190201111202502](https://ws1.sinaimg.cn/large/006tNc79ly1fzqr1100ubj30zj0mjadl.jpg)
3. ![image-20190201111324019](https://ws2.sinaimg.cn/large/006tNc79ly1fzqr2ffsf8j30yg0id76e.jpg)

# git常用命令

## 初始化本地仓库，生成隐藏.git文件夹

```bash
git init # 初始化本地仓库
touch test.txt # 创建文件
git status test.txt # 查看状态  (红色 表示没有添加到暂缓区)
git add test.txt  # 或者git add  (添加到暂缓去,提交所有文件到暂缓区)
git commit test.txt  
# 这时候会进入编辑模式,让我们添加做了哪些事情,写完之后,esc 退出编辑模式,:wq 保存并退出
git commit -m "初始化项目"  //直接提交 
```

## 本地用户信息配置

```bash
git config -l  # 查看当前配置信息
git config user.name xyanglzu
git config user.email 1******00@qq.com /# 配置本地

# 信息保存位置:chengaojian(用户名)
# /Users/Xiny/.git/config

# 打开config信息如下:
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
    ignorecase = true
    precomposeunicode = true
[user]
    name = xiny
    email = 1******00@qq.com
```

## 全局用户信息配置

```bash
git config --global user.name J_mialbox
git config --global user.email J_mialbox@163.com

# 信息保存位置:chengaojian(用户名)
# /Users/chengaojian/.gitconfig

# 打开gitconfig信息如下:
[user]
	name = xiny
	email = 1******00@qq.com
[core]
	autocrlf = input
[filter "lfs"]
	process = git-lfs filter-process
	required = true
	clean = git-lfs clean -- %f
	smudge = git-lfs smudge -- %f

git log  # 查看历史
```

