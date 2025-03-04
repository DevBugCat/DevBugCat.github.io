---
title: Hexo 学习记录
date: 2025-03-03 22:10:56
categories: [Hexo, Hexo学习记录]
---

最近突发奇想，想做一个个人网站记录学习心得，通过hexo + github 的方式做了一个blog，但是奈何页面模板不太理想，想要做一个好看一丢丢的博客网站出来，因此需要学习一些关于hexo的一下，以下部分用于记录学习心得；（PS 搭建网站可以参考如下link : [参考连接](https://blog.csdn.net/yaorongke/article/details/119089190)) 在这里感谢博主的好心分享）

## 安装Hexo

```
npm install -g hexo-cli
```

## 初始化Hexo

```
npm install
```

初始化完成后，会创建如下目录

```
.
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes
```

其中：

1. _config.yml 是配置文件，大部分配置都在此可以配置；

2. scaffolds 里面存放了模板文件，当使用 `hexo new filename`时，会根据此处的模板建立文档

3. themes 里面存放了模板信息，当在 [hexo主题](https://hexo.io/themes/)  找到合适主题之后，可以使用以下cmd 拉取：

```
# 进入Hexo项目的themes目录
cd your-hexo-site/themes
# 克隆主题仓库
git clone https://github.com/theme-next/hexo-theme-next.git 主题名
```

4. source 的_posts里面存放的就是博客内容了，写的博客都可以放在这个里面



## _config.yml相关

大部分内容在如下link ： [_config.yml 介绍](https://hexo.io/zh-cn/docs/configuration)  

常用部分如下：

