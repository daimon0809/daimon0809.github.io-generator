---
title: "如何用 hugo 搭建个人博客"
date: 2020-05-04T11:00:07+08:00
draft: false
---

# 如何用 hugo 搭建个人博客

<br>

## 安装hugo

### Windows安装方式：（本文只讲述Windows安装）
1. 去[Hugo releases 页面](https://github.com/gohugoio/hugo/releases)下载 hugo_xxx_Windows-64.bit.zip；
2. 解压，把hugo.exe放到 D:\Software\hugo\hugo.exe；
3. 把 D:\Software\hugo 加入到PATH中；
4. 重启终端，运行 hugo version 查看版本号。

<br>

## 如何快速搭建hugo博客

### 看文档搞出网站
1. 进入[hugo 官网](https://gohugo.io/)，点击quick start，从step开始到step7；
2. hugo new site quickstart（你自己的博客生成器，名称自定义，通常用yourname.github.io-generator）
3. cd quickstart （去到你的博客路径下面）
4. git init （生成本地仓库）
5. git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke （下载主题，主题可更换）
6. echo 'theme = "ananke"' >> config.toml （添加主题）
7. hugo new post/my-first-post.md (创建博客)
8. hugo server -D （启动本地服务）
9. hugo -D （生成可推送GitHub的博客，quickstart路径下会多个public目录）
10. 创建 .gitignore 文件，添加 /public/ 当前仓库不储存public（即public要单独成立仓库）
11. cd public 
12. git init
13. git add .
14. git commit
15. GitHub中新建目录quickstart（创建远端仓库必须对应你自己的博客生成器，yourname.github.io-generator）
16. git remote add origin git@github.com:daimon0809/quickstart.git (本地和远端仓库建立联系)
17. git push -u origin master （推送到远端仓库）
18. 打开GitHub个人主页，去到quickstart路径，打开setting
![](/images/setting.png)
19. 找到GitHub Pages
![](/images/site.png)





