---
title: "Thinking About Url"
date: 2021-01-20T20:38:13+08:00
draft: true
---

# 初探URL

1. URL 包含哪几部分，每部分分别有什么作用
* 全称： HyperText Transfer Protocol （超文本传输协议）
* 协议 + 域名或IP + 端口号 + 路径 + 查询字符串 + 锚点 

    例如： https://www.baidu.com/s?word=hello&rsv_spt=1#5

    * 协议：http/https,指定应用层协议类型
    * 域名/IP：用于寻址，区分服务器
    * 端口号：和域名/IP一起使用
    * 路径：请求地址，默认为根路径
    * 查询字符串：查询条件
    * 锚点：跳转到指定id所在位置

1. DNS 的作用是什么，nslookup 命令怎么用
* 全称：Domain Name System（域名系统）
* nslookup 域名

3. IP 的作用是什么，ping 命令怎么用
* 确定服务器地址以及寻址
* ping IP/域名 ，根据相应信息判断是否能够建立链接

4. 域名是什么，分别哪几类域名
* 域名即IP别名（存于文件hosts）