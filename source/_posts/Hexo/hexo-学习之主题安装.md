---
title: hexo 学习之个人博客创建与调教
tags:
- hexo
categories:
- Hexo
- Hexo 学习记录
date: 2025-03-15 22:15:03
---

# 前言

hexo + github 搭配好个人blog之后，可能会觉得有时候主题看起来没有那么帅气，需要更改以下风格才能适应自己，但是自己又不是做前端的，怎么办？这个时候就需要白嫖了，在 [hexo 主题界面](https://hexo.io/themes/) 上可以挑选各种主题，总有一款适合你自己。
![image-20250315222151960](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250315222151960.png)



回归正题，本文主要介绍如何使用hexo 生成一个 个人blog 并将volantis主题安装到个人blog中：
相关环境准备参考：

# hexo 搭建个人blog

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
   ![image-20250315231531040](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250315231531040.png)
   
   ```
   rm -rf node_modules && npm install --force
   ```
   
   运行完毕后会出现如下结果：
   ![image-20250315230450040](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250315230450040.png)
   
   然后在个人浏览器中输入 http://localhost:4000/ 即可访问部署好的blog，后续debug都将采用此方法。初始blog界面如下，如果看到这个界面，就代表你已经成功部署了个人blog了。
   ![image-20250315230802719](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250315230802719.png)



# volantis主题安装

从 [hexo 主题界面](https://hexo.io/themes/) 搜索到volantis之后，可以进入[volantis文档](https://volantis.js.org/v6/getting-started/) 查看如何安装volantis 主题；
首先在文件夹中找到_config.yml 修改主题为volantis:

```
theme: volantis
```

![image-20250317232629429](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250317232629429.png)

然后在bash界面输入以下cmd：

```
npm i hexo-theme-volantis
```

出现这个结果就证明安装对了：
![image-20250317232831375](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250317232831375.png)

然后统一运行`hexo s`打开本地浏览器访问 ` http://localhost:4000/` 即可看到更新后的主题：
![image-20250317233615980](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250317233615980.png)



PS:因为我最后将博客的源码也会保管在github上面，所以我多了一个步骤，会将安装好的volantis主题放在theme 文件夹下，其主题文件在这个位置：

```
node_modules\hexo-theme-volantis
```

copy hexo-theme-volantis整个文件放在 `\themes` 下重命名为 `volantis` 即可；

# volantis主题调教

当你白嫖了一个主题之后，可能会有点难受，因为直接用别人的感觉不太顺手，有些功能不想要，有些功能想有他没有，怎么办？哎~ 没关系，开发主题的大佬们已经想到了，留了很多接口供你调教，接下来我会捡一些重要的部分share出来，后续更多的细节就靠自己挖取了；

在将详细调教之前，先透露一个小妙招，刚刚copy的主题文件中，有一个_config.yml 

## volantis主题调教1--菜单栏调教





