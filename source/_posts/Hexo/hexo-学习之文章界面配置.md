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

菜单栏被放在 `Navigation Bar` 下面，同样的手法，我们从 `volantis` 主题下的 `_config.yml` copy下这部分内容，即可开始菜单栏的修改；

```
 ############################### Navigation Bar ############################### > start
# 注意事项：建议规范全站路径 URL 最后带一个 "/" 例如 "about/"
navbar:
  visiable: auto # always, auto
  logo: # choose [img] or [icon + title]
    img: volantis-static/media/org.volantis/blog/Logo-NavBar@3x.png # https://cdn.jsdelivr.net/gh/volantis-x/cdn-org/blog/Logo-NavBar@3x.png
    icon:
    title:
  menu:
    - name: 博客
      icon: fa-solid fa-rss
      url: /
    - name: 分类
      icon: fa-solid fa-folder-open
      url: categories/
    - name: 标签
      icon: fa-solid fa-tags
      url: tags/
    - name: 归档
      icon: fa-solid fa-archive
      url: archives/
    - name: 友链
      icon: fa-solid fa-link
      url: friends/
    - name: 关于
      icon: fa-solid fa-info-circle
      url: about/
  search: Search...   # Search bar placeholder
############################### Navigation Bar ############################### > end
```

最开始可以发现只有点击博客会有反馈，其他的分类，标签，归档，友链，关于都没有反应，那需要如何做才能有效果呢？

首先我们需要明白下面这个格式是一个功能：

```
 	- name: 博客
      icon: fa-solid fa-rss
      url: /
```

`name` 就是功能名字，`icon` 就是要显示的图标，这部分可以参考前面的描述，`url`就是对应的地址；

问题接着来了，`url` 如何获取，你可以贴一个网址来跳转过去，也可以访问本地位置，需要怎么做，看看示例里面，对应的就是本地的位置；比如 `categories/` 就是在 `source`下面建立对应文件夹即index文件；

我们可以采取如下方式做到：

```
hexo new page "XXX"
#示例
hexo new page "categories"
hexo new page "tags"
hexo new page "archives"
hexo new page "friends"
hexo new page "about"
```

当你运行完上述命令后会得到如下几个文件夹：

![image-20250401224315035](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250401224315035.png)

同样 `hexo s`访问一下 `http://localhost:4000/`，点击你就会发现已经出来对应的页面了，如下：

![image-20250401224504283](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250401224504283.png)

当然还有更多的玩法，比如你可以增加一个栏目：`更多` ，在 `更多`里面增加一些栏目，怎么做？参考如下示例：

```
     -name: 更多
      icon: fa-solid fa-ellipsis-v
      rows:
        - name: 主题源码
          url: https://github.com/volantis-x/hexo-theme-volantis/
        - name: 更新日志
          url: https://github.com/volantis-x/hexo-theme-volantis/releases/
        - name: hr
        - name: 有疑问？
```

解释一下就是多了一个 `rows`，这个下面就是你可以下拉更多栏目，其中 ` - name: hr` 代表分割线，同样展示一下这一块的结果：

![image-20250401225001121](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250401225001121.png)



在这里，特别指出友链相关的配置参考教程在这里 ： [友链页面](https://volantis.js.org/v6/page-settings/?keyword=友链#友链页面)

# 如何添加评论区

菜单栏修改完毕后，就是如何添加评论区了，这部分主要参考如下连接 [评论系统](https://volantis.js.org/v6/theme-settings/?keyword=评论#选择评论系统)；

我们主打一个白嫖，就用`giscus`了，借用github评论功能，具体做法如下：

## 1. 创建github仓库

在个人仓库创建一个repo，选择public：
![image-20250401231111621](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250401231111621.png)

仓库需要满足以下三个条件：

1. **该仓库是[公开的](https://docs.github.com/en/github/administering-a-repository/managing-repository-settings/setting-repository-visibility#making-a-repository-public)**，否则访客将无法查看 discussion。
2. **[giscus](https://github.com/apps/giscus) app 已安装**，否则访客将无法评论和回应。
3. **Discussions** 功能已[在你的仓库中启用](https://docs.github.com/en/github/administering-a-repository/managing-repository-settings/enabling-or-disabling-github-discussions-for-a-repository)。

第一个条件在创建repo的时候就已经满足，接下来就是安装`giscus app`到`repo`中；

访问 [GitHub Apps - giscus](https://github.com/apps/giscus) 选择对应仓库即可安装到repo中。

首先在仓库设置中找到github apps：
![image-20250401231848903](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250401231848903.png)

然后点击Configure:
![image-20250401231943549](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250401231943549.png)

输入密码后进入配置对应repo权限，如下：
![image-20250401232203496](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250401232203496.png)

设置完成后重新进入setting，并开启Discussion
![image-20250402214715498](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250402214715498.png)

## 2.获取评论系统配置信息

访问 `https://giscus.app/`，找到仓库，填写 `用户名/仓库名`，例如我这里就是 `DevBugCat/testDiscuss`

![image-20250402214843392](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250402214843392.png)



然后选择分类为 `Announcements`
![image-20250402214907340](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250402214907340.png)

随后就继续往下就可以看见如下配置：
![image-20250402215120005](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250402215120005.png)



## 3.yml配置开启评论区

我们将如下部分的设定copy到 `_config.volantis.yml`中

```
comments:
  service: giscus
  # giscus
  # https://giscus.app
  # https://github.com/laymonage/giscus
  giscus:
    # 以下配置按照 yml 格式增删填写即可
    repo: xxx/xxx
    repo-id: xxx
    category: xxx
    category-id: xxx
    mapping: "pathname"
    reactions-enabled: "1"
    emit-metadata: "0"
    lang: "zh-CN"
    # 以上配置按照 yml 格式增删填写即可
    theme:
      light: "light" # https://gcore.jsdelivr.net/gh/volantis-x/cdn-volantis@master/css/giscus/light.css
      dark: "dark" # https://gcore.jsdelivr.net/gh/volantis-x/cdn-volantis@master/css/giscus/dark.css
```

其中，`xxx`部分就是我们在giscus里面生成的数据，直接按照内容copy过去即可了；这个时候重新部署一下就可以使用评论系统了：

![image-20250402215721725](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250402215721725.png)

## 4.评论区管理

当评论区开启之后，可能有时候会需要管理评论区，那去哪里可以找到呢？
我们首先新增一个测试一下的评论，然后找到自己放评论区的仓库；

点击 `Discussion`就可以找到评论：
![image-20250402215949305](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250402215949305.png)



比如我这里的测试一下：
![image-20250402220022754](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250402220022754.png)



后期就可以进行评论区的管理了。



# 结语

其他的一些细枝末节的设计就不再赘述，相信有了上面的功能demo，后续大家也可以自行按照volantis 主题文档进行修改了，搭建个人博客系列到这里就结束了！
