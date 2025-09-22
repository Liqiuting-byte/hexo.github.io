---
title: 反向链接适配汇总
date: 2025-09-21
description: 汇总性质文章
tags:
  - 技术
  - 思考
  - 汇总
category: 教程
draft: false
---
### 前记
上个月的时候，我尝试为本博客适配反向链接，由于时间限制，还有自己的一切事情暂时放弃了
在此文当中我表明了本人的决心，因为这可以增强本博客知识的关联性[FUCK](/FUCK.md)
在此之后进行了一些尝试，那就是给黑曜石【Obsidian】的`[[]]`进行重写，于是便有下面这篇文章的探索[Wiki search and Wikilinks](/Wiki%20search%20and%20Wikilinks.md)，并且在看国外论坛的时候，也看到了这一篇文章，具体出处我已经忘掉了但是我当时转载了一下[wiki-links-post-in-stackoverflow](/wiki-links-post-in-stackoverflow.md)，失败的原因就是我太执着于找到一个可以自动对`[[]]`进行处理的玩意了，今天也是终于解决了这个烦恼，遂发一篇教程详细记录过程
### Obsidian设置
在这里进入设置
![](https://image.342191.xyz/file/AgACAgUAAyEGAASrPZpLAAMiaND9mZeyE1rSLuC9qm4bk8CVkUIAAtvDMRvs24hWWsNiqP50jfwBAAMCAAN4AAM2BA.png)

然后进入文件与链接
![](https://image.342191.xyz/file/AgACAgUAAyEGAASrPZpLAAMjaNEJKkNjLz6aLz5GHYm0jV3dTwsAAu_DMRvs24hWXzYwz3tgtp8BAAMCAAN5AAM2BA.png)

![](https://image.342191.xyz/file/AgACAgUAAyEGAASrPZpLAAMkaNEJaFNtz4NDiCFK2B_L9wjMZ8gAAvHDMRvs24hWWuUI1FN1FNsBAAMCAAN5AAM2BA.png)

在引用`[hello-world](hello-world.md)`的时候，同样需要修改两个地方，否则对于 hexo，是会出错的
1. `[hello-world](hello-world.md)`当中的路径应该换为 `[hello-world](/hello-world.md)`，一定要记得加/,否则路径会报错

2. 打开文件_config，然后找到下面这行代码
```yml
permalink: :title.md/ #这里改成这个
permalink_defaults:
pretty_urls:
  trailing_index: true # Set to false to remove trailing 'index.html' from permalinks
  trailing_html: true # Set to false to remove trailing '.html' from permalinks
```
然后就可以引用了