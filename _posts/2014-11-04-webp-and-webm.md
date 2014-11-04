---
layout: post
title: 解决七牛webp和webm格式文件显示问题
---

* 由于webp和webm都是有Google提出的图片和视频的编码格式，所以在Chrome浏览器上能得到很好的支持，其他浏览器不一定支持。

* 若Chrome浏览器无法正常打开webp或者webm文件，可以去七牛的<https://portal.qiniu.com>通过前缀搜索资源，检查资源的mimeType，若不正确则手动将其修改为`image/webp`或者`video/webm`（修改方法可以参考下图）。
![mimeType修改](http://weloveqiniu.qiniudn.com/Snip20141104_2.png)