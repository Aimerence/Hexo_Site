---
title: Icarus 主题网站优化（bug记录）
date: 2020-03-13 15:27:31
toc: true
top: 101
categories: Blog
tags: [icarus,hexo]
article-thumbnail: true
thumbnail: /images/display.jpg
keywords: [Machine Learning, css, Word Embedding, CJ Sun, Caijun Sun, IOVI]
---
**记录我的网站目标及优化之路，感谢以下大佬的创作与开发（不分先后）：**

<!-- more -->

## Thanks 大佬

- [ppoffice](https://github.com/ppoffice "ppoffice")

- [Ray’s Blog](https://raycoder.me "Ray's Blog")

- [dp2px](https://dp2px.com/ "dp2px")

- [removeif](https://removeif.github.io/ "removeif")

- [jitwxs](https://www.jitwxs.cn/ "jitwxs")

- [imaegoo](https://www.imaegoo.com/ "imaegoo")

- [alphalxy](https://www.alphalxy.com/ "alphalxy")

- [Evan](https://nave.work/"Evan")

- [zazdream](https://zazdream.com/)

- [cxy35](https://www.cxy35.com/)

- [Anne Wu](https://annewqx.top/)

- [yafine](https://yafine-blog.cn/)

## ToDo 计划 

- [x] 粒子时钟（加强版）

- [x] 文章页 双栏布局 /减少不必要的部件

- [x] 自动刷新md内容方便预览

- [x] 底部备案、文章版权、永久链接格式

- [x] 黑夜模式

- [x] 主页添加bio(一句话)

- [x] 图片居中/相册间隙

- [x] 友链页布局修改（三栏）

- [ ] 关于页面内容更新(加音乐)

- [ ] 主页添加部件 最新评论

- [ ] 主页添加部件 添加推荐文章

- [x] 增加页面 豆瓣电影

- [x] 增加页面 豆瓣书单

- [ ] ~~增加电子书阅读页面(gitbook)~~

- [x] ~~增加网易云音乐页面~~

- [ ] 关于页面加入时间线

- [ ] 归档页添加文章贡献概览

- [x] ~~置顶文章功能~~

- [ ] ~~加密文章功能（鸡肋）~~

- [ ] 文章列表评论数显示

- [ ] ~~增加页面 碎碎念（个人吐槽、心情页）~~

- [ ] ~~增加页面 留言墙（区）~~

- [x] 增加相册页（包括美图展示）

- [ ] ~~添加网盘~~

- [ ] 增加体系页（思维导图）

- [x] RSS订阅

- [x] 增加个人导航页（工具、网站、影视等）

- [x] 图像logo 更改 （适应黑夜模式）

- [x] ~~评论管理~~

- [x] 关注我改成公众号（公众号还未准备）**

- [x] 网站运行时间

- [ ] ~~pv/uv~~

- [ ] ~~图片懒加载 （以及与相册的bug)~~

## Bug 修复

- [ ] 关注 Follow 弹出二维码在移动设备未在中间弹出

- [x] 黑夜模式下 底部刷新变黑明显慢于其他部分

- [x] night.js初次加载报Cannot read property 'toString' of null的问题

- [x] 黑夜下valine 评论 代码格式形式白

  

## Display 布局

- 三栏展示：Home 、Archives、Categories、Tags、Movies
- 双栏展示： Post、
- 单栏展示： About 、Gallery、Links
- ~~纯静态/未渲染：Tricks :  navs(先不弄了)~~

## Record 记录

- `page.layout` 判断  `type`

- 将主题所用的字体放到本地，弃用 `loli` CDN
- 在黑夜模式作者imaegoo的帮助下解决 night.js 报错问题
- 将相册图片放到了又拍云cdn 上了 图片资源放在又拍云 

## Plan 期望

- [ ] 音乐部件

- [ ] 除文章页外不加载不必要插件

- [x] 友链页整改

  
## Profile 文档
- [hexo官方文档里对于变量的说明](https://hexo.io/zh-cn/docs/variables)

- [hexo官方文档里对于辅助函数的说明](https://hexo.io/zh-cn/docs/helpers)

- [ejs嵌入开发各个标签的含义](https://ejs.bootcss.com/)

- [bulma框架中文文档](https://bulma.zcopy.site/documentation/)
