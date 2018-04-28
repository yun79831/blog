---
title: hexo+github博客搭建
date: 2018-04-28 16:29:49
tags: hexo github 博客
---

## Hexo博客搭建优势

1. 无需域名和服务器就能挂在外网
2. 搭建快速 分分钟钟搞定(ps:前提你家伙事齐全)
3. 样式选择自由,可以自己选择主题(ps:我个人就有选择困难综合征)



## 搭建步骤

大致可以分为以下几个步骤:

1. 准备环境(Git,nodejs,Github账户,hexo)
2. 部署到Github Page 上
3. 选择主题
4. 添加插件



## 环境准备 

针对windows环境

1. 点击 [安装Git](https://git-scm.com/downloads)

   Git Path 选择 use Git from the Windows Command Prompt

   控制台执行 git --version 确认是否安装成功

   ```
   git config --global user.name "你的名字"
   git config --global user.email "你的邮箱"
   ssh-keygen -t rsa -C "你的邮箱"	##一路确定,C:\Users\用户\.ssh\id_rsa.pub
   ```

   ​

   ​

2. 点击 [安装Node.js](https://nodejs.org/dist/v4.2.3/node-v4.2.3-x64.msi)
   Node.js安装之后自动安装了npm
   控制台执行

   ```
   node -v
   npm -v
   ```

3. 安装Hexo

   ``` 
   npm install hexo-cli -g
   npm install hexo --save
   npm install hexo-deployer-git --save		##安装hexo git扩展 以便hexo d
   npm install hexo-generator-feed -save
   npm install hexo-generator-sitemap -save
   hexo -v 		##查看版本
   hexo init		##初始化Hexo
   npm install  	## 安装所需要的插件
   hexo g			##生成hexo html文件
   hexo s			##启动hexo INFO Hexo is running at http://0.0.0.0:4000/. 
   ```

   ```
   ##Hexo 常用命令
   hexo g		##生成
   hexo s		##启动
   hexo d		##部署 			需要在_config.yml中 deploy: 配置 git和github地址 
   hexo d -g	##生成之后部署	  需要在_config.yml中 deploy: 配置 git和github地址 
   ```

   ​

   ​

4. 点击 [去准备Github账户](https://github.com/)

   创建 yourname.github.io的仓库   仓库名字必须是 **你用户名.github.io**.否则github无法给你分配相应的域名

   项目的setting -->GitHub Pages-->source 选 master 就可以看到你的域名

   将前面git生成的C:\Users\用户\.ssh\id_rsa.pub 添加到github的 用户-->settings-->SSH and GPG keys-->New SSH key 

   本地执行 

   ```
   ssh -T git@github.com
   yes
   ```

   这样你Git提交到GItHub就不用密码了.

   ​

## 配置Hexo

1. 主题配置
   我本人用的yilia,你也可以自行搜索主题  [主题](https://www.zhihu.com/question/24422335)

   $ git clone https://github.com/litten/hexo-theme-yilia.git themes/yilia

   在hexo的根目录下_config.yml配置文件

   ```
   theme: yilia    //默认为landscape
   ```

   ​

2. 配置deployment

```
deploy:
  type: git
  repo: git@github.com:yun79831/yun79831.github.io.git    //换成你自己的刚才生成的github仓库地址
  branch: master
```





## 插件

1. 流量插件
2. 评论插件

先写到这...