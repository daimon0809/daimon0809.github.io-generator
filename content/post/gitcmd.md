---
title: "git常用命令"
date: 2020-04-28T20:01:07+08:00
draft: false
---

# git常用命令

## git本地仓库命令

### git六行配置
1. git config --global user.name 你的英文名
2. git config --global user.email 你的邮箱
3. git config --global push.default simple
4. git config --global core.quotepath false
5. git config --global core.editor "code --wait"
6. git config --global core.autocrlf input

git init	创建.git仓库

git add	标记文件将要被提交

.gitignore	标记不需要提交的文件

### git 提交代码
* git add ***
* git commit -v / -m(简化日志)	跳转到VSCode

### git不同版本直接切换
* git log	查看当前所有版本号
* git reset --hard d9711a(版本号，至少是前6位，需唯一不重复)	跳转到历史版本
* git reflog	查看所有版本号（包括reset之前的）
* git reset --hard ***(版本号) <font color="#660000"><b>此操作需保证所有代码都是commit状态，不然会被git永久丢弃</b></font>
<br>
## git远程仓库命令

### ssh 生成密钥（公钥，私钥）
1. ssh-keygen -t rsa -b 4096 -C 你的邮箱
2. cat ~/.ssh/id_rsa.pub  得到公钥内容
3. ssh -T git@github.com 测试连接

### 上传远程仓库
* git remote add origin git@xxxxxxx	（往远程仓库添加代码）
* git push -u origin master	（上传远程仓库）

<br>

## git高级操作
### 设置方言,简化命令
```shell
touch ~/.bashrc

echo 'alias ga="git add"'>> ~/.bashrc
echo 'alias gc="git commit -v"'>> ~/.bashrc
echo 'alias gl="git pull"'>> ~/.bashrc
echo 'alias gp="git push"'>> ~/.bashrc
echo 'alias gco="git checkout"'>> ~/.bashrc
echo 'alias gst="git status -sb"'>> ~/.bashrc
```
<font color="#660000">source ~/.bashrc</font>  方可生效

## 美化git提交记录

### git rebase -i XXXX	(上一次的提交记录)
```
# r, reword = use commit, but edit the commit message	(采用，但是改写message)
# s, squash = use commit, but melt into previous commit	(采用，但是合并到上一个提交)
```

![](/images/1.png)

<br>

### 隐藏文件(通灵术)
* git stash		(隐藏文件)
* git stash pop	(展示隐藏文件)


[五岛的博客](https://daimon0809.github.io/)

