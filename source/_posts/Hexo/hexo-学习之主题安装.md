---
title: hexo 学习之个人博客创建与调教
tags:
- hexo
categories:
- Hexo
- Hexo 学习记录
date: 2025-03-15 22:15:03
---

## 前言

hexo + github 搭配好个人blog之后，可能会觉得有时候主题看起来没有那么帅气，需要更改以下风格才能适应自己，但是自己又不是做前端的，怎么办？这个时候就需要白嫖了，在 [hexo 主题界面](https://hexo.io/themes/) 上可以挑选各种主题，总有一款适合你自己。
![image-20250315222151960](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250315222151960.png)



回归正题，本文主要介绍如何使用hexo 生成一个 个人blog 并将volantis主题安装到个人blog中：
相关环境准备参考：

## hexo 搭建个人blog

1. 随便创建一个文件夹，我这里以MyBlogSample为例子，进入文件夹中，右键选择Open git bash here，如下：
   ![image-20250315223757185](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250315223757185.png)
   我本地因为使用VS 挂了git bash，因此是使用VS 的Terminal：
   ![image-20250315223907490](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250315223907490.png)

2. 输入以下命令创建个人blog；

   ```
   hexo init
   ```

   如果hexo init 执行比较慢的话，可以使用以下命令代替：

   ```
   git clone https://github.com/hexojs/hexo-starter myblog
   cd myblog
   ```

   当出现如下这些文件，代表拉取成功了：
   ![image-20250315225051081](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250315225051081.png)

3. 测试个人blog是否成功，使用如下命令;

   ```
   hexo s
   ```

   会得到如下结果：

   ![image-20250315230521531](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250315230521531.png)

   如果在运行过程中出现如下错误，就按照提示输入命令即可：

   ```
   rm -rf node_modules && npm install --force
   ```

   运行完毕后会出现如下结果：
   ![image-20250315230450040](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250315230450040.png)

   然后在个人浏览器中输入 http://localhost:4000/ 即可访问部署好的blog，后续debug都将采用此方法。初始blog界面如下，如果看到这个界面，就代表你已经成功部署了个人blog了。
   ![image-20250315230802719](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250315230802719.png)



## volantis主题安装与修改



