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

在将详细调教之前，先透露一个小妙招，刚刚copy的主题文件中，有一个_config.yml ，加下来的主题调教和其分不开，我们可以copy出来此主题配置文件，后续在上面做修改即可。

在主题修改之前，先在blog根目录下建立一个_config_volantis.yml，它的优先级会高于 _config.yml，后续主题修改可以在 _config_volantis.yml 上进行，这样不会改坏原本的配置，示例如下：
![](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250318085053191.png)

## volantis主题调教1--网站主页修改

首先安装完volantis之后，进入配置好的网页就是主页，主页主要有如下部分组成：
![image-20250318090050687](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250318090050687.png)



接下来就来修改一些配件内容，做一个示范介绍，用到的样例参考上面介绍的volantis主题下的_config.yml以及官方学习文档之[网站与文章封面](https://volantis.js.org/v6/theme-settings/#网站与文章封面) 、[侧边栏配置 ](https://volantis.js.org/v6/theme-settings/#侧边栏配置) 、 [设置网站页脚](https://volantis.js.org/v6/theme-settings/#设置网站页脚)

### 网站主页修改之一：title、subtitle、feature、background 修改

主题的title 、 描述 以及feature都是放在cover下的，我们首先从volantis主题下的_config.yml copy处 `cover` 整个字段到新建的 _config.volantis.yml文件里面，如下分别是各个部分的内容：
![image-20250319084456381](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250319084456381.png)

1. 文件配置从上到下进行说明，首先是`backgroand` ，这个后面就是跟的一个网络图片，你可以自己找到一个图片进行url替换，即可完成背景图片替换，如果想用自己上传的图片，可以配置图床，然后上传上去，获取url即可做到，详情可以参考以下连接：

2. `title` 字段后面就是主题title了，默认是volantis，也就是上面网页显示的volantis，我们在这里修改成 `Tom's blog` ，后续看成果图；

3. `subtitle` 就是描述了，可以对写一段自己想说的话；

4. 接下来就是feature了，这里默认已经有了多个，可以根据个人情况进行增加或删除，接下来我会举例说明如何修改：
  #### feature修改介绍

feature每个块有四个部分组成，分别是：

```
name / icon / img / url
```

 `name`就是你需要显示feature的名字，`icon`就是图标，`image`就是上面的图片，`url` 就是对应要跳转的地方；

接下来来做一些增删改查的实例：

#### feature修改之：增

   我们新增一个test到主页上的feature里面，当点击test的时候，显示这里什么都没有，应该如何做？

1. 首先自然是显示出来这个feature，按照上面所说的，我们新增如下部分代码：

   ```
   - name: test
     icon: #
     img: https://cdn.jsdelivr.net/gh/twitter/twemoji@13.0/assets/svg/1f9ec.svg
     url: /test/
   ```

   新增完毕后整体feature情况如下：
   ![image-20250319083440147](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250319083440147.png)
2. 修改完成后使用 `hexo s` 就可以重新部署，然后访问 `http://localhost:4000/` 即可看到修改后的效果：
   ![image-20250319084802046](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250319084802046.png)
3. 这个时候聪明的你会发现，点击测试没有任何反应，那是因为没有将其修改响应创建出来，因为我们填写的是`/test/` ，这代表他会去 `\source\test`下面去找结果，这个时候我们需要生成对应的文件目录和`index.md`给它，使用如下命令可以生成：

   ```
   hexo new page "test" #test 可以替换
   ```

   命令运行完成后，你可以在 `source` 目录下面发现如下结果：
   ![image-20250319085330969](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250319085330969.png)
4. 这个时候，在重新 `hexo s` + 浏览器访问 `http://localhost:4000/ ` ，再去点击测试就会有响应，进入到生产的`index.md`界面里面，在这个里面可以显示一些其他想显示的东西，后续的就看如何发挥了
   ![image-20250319085523490](https://gcore.jsdelivr.net/gh/tom-li-520/blogImage@main/Image/image-20250319085523490.png)
#### feature修改之：删



