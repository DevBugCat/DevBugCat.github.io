---
title: hexo 学习之文章界面配置
tags:
  - hexo
categories:
  - Hexo
  - Hexo 学习记录
date: 2025-03-22 11:39:05
---

# 前言

当你配置好主页之后，就会想着将文章的内容进行配置了，那么应该如何做？
别担心，本文会叫你如何开始写`blog`，以及写完之后在`blog`页面的一些配置，还有就是如何开发评论区共他人评论指导~}
好了，废话不多说，开始教程了！



# 如何生产一篇文章

当我们主页配置好了以后，就可以开始写blog了，基本上我们只需要熟练使用以下cmd就可以了：

```
#新建一篇文章：
hexo new "文章名"

#预览文章：
hexo s

#部署文章到网页
hexo clean && hexo g && hexo d
```

我们首先建立一个 `myFirstTestBlog` 的文章，在bash界面，输入 `hexo new "myFirstTestBlog" `，运行之后结果如下：

![image-20250324224241591](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250324224241591.png)

你可以在 `source\_post` 目录下找到你新建的文件：

![image-20250324224340854](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250324224340854.png)

好了，到这里就新建好了一篇 `blog`了。

新增一下 `tags` 和 `categories` ，然后就可以开始写了，我简单做一个demo:

![image-20250324225042089](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250324225042089.png)

然后我们去浏览器上面看看效果如下：

![image-20250324225200926](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250324225200926.png)

看到这个截图，你就会想，好好好，这菜单是个啥，有用吗？文章作者也没有，评论去也没有，这怎么行，不要慌，我来带你继续往下看；

# 如何修改菜单栏





