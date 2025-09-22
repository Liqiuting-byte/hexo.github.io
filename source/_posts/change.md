---
title: 更改本blog为stellar
published: 2025-09-21
description: 更改本blog为stellar
tags:
  - 技术
  - 思考
category: 前端
draft: false
---
改了 因为原主题在文章杂乱的情况下不适合知识的归纳与整理。
似乎失去了一些特色组件，不过尚且还在可以接受的范围之内。
之后会进行迁移

详细记录一下吧

复制的官方教程

## 安装 hexo 框架:
打开 cmd 运行

```
 $ npm install -g hexo-cli 
```

- 新建一个文件夹，如 MyBlog ，进入该文件夹内，右击运行 git ，输入：

```
$ hexo init
```

- 生成完 hexo 模板，安装 npm ，运行：

```
$ npm install
```

运行：

```
$ hexo server
```

这时候打开浏览器，输入 localhost:4000 就可以看到博客目前的样子了

## 一些坑

### 幽灵依赖
幽灵依赖这个是别人对这个的称呼
	Error: Cannot find module '...'
原因是主题作者忘记添加依赖包导致的 
解决方法:
```
pnpm add hexo-util glob hexo-fs
```

### pnpm和npm混淆
	TypeError: Cannot read properties of null (reading 'matches')
原因就是在这个 pnpm 创建的结构上运行 npm install 或 npm up 时，npm 瞎理解 pnpm 的目录结构，然后给之前搞的文件夹全部破坏掉了。
解决方法:
1. 删除 node_modules 文件夹
2. 打开 package.json 文件。
3. 在文件中添加 pnpm.overrides 字段，强制 strip-ansi 的版本为 6.0.1
4. 然后运行：
```
pnpm install
```
  5.~~然后忘掉pnpm，全神贯注使用我们的npm~~

## back link
似乎这个hexo对于反向链接适配的不错
在黑曜石这个Ob软件当中 可以直接使用[[]]来进行引用我之前写的文章
例如[Wiki search and Wikilinks](/Wiki%20search%20and%20Wikilinks)

但是前面必须加一个/，代表着网站的根目录

千万记得备份哈，我是幸好之前提交GitHub了，要不然快捷键就死了