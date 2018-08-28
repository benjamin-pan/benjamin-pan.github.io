---
layout: post
title: 分页
date: 2018-08-26 20:40:00 +0800
description: 分页
tags: [javascript, js, html, css]
---

<link rel="stylesheet" href="http://par5l10v3.bkt.clouddn.com/ued.css" />

<div style="text-align: center"><div id="pagination"></div></div>

<script type="text/javascript" src="http://par5l10v3.bkt.clouddn.com/js/jquery.js"></script>
<script type="text/javascript" src="http://par5l10v3.bkt.clouddn.com/js/pagination.js"></script>
<script type="text/javascript">
  Pagination({
     activeIndex: 1,
     totalPage: 10,
     showNumberOfPage: true,
     father: '#pagination', // 插槽id
     goToPage: function (index) {
         // 切换分页回调函数，index为要去第几页
         alert(index);
     },
     changeNumberOfPage: function (val) {
       // 改变每页显示数量回调函数
       alert(val);
     }
  })
</script>

### 使用环境

有jquery即可，如有后期需要可去除jquery。


### 使用方法

在需要使用分页的页面引入以下资源，路径自行调整。
<a href="http://par5l10v3.bkt.clouddn.com/css/ued.css" download>下载css</a>
<a href="http://par5l10v3.bkt.clouddn.com/js/pagination.js" download>下载js</a>
<a href="https://github.com/benjamin-pan/pagination" download>完整demo下载</a>
```
<link rel="stylesheet" href="http://par5l10v3.bkt.clouddn.com/css/ued.css" />
<script type="text/javascript" src="http://par5l10v3.bkt.clouddn.com/js/pagination.js"></script>
```

提供一个分页的插槽，id尽量唯一，这里是pagination。如果不唯一，会出现问题，而且还不报错，bug很难调试。
```
<div id="pagination"></div>
```

在获取到分页信息之后，调用如下代码。
```
Pagination({
   activeIndex: 当前活动页,
   totalPage: 分页总页数,
   showNumberOfPage: 是否可切换每页数量，boolen类型,
   father: '#pagination', // 插槽id
   goToPage: function (index) {
     // 切换分页回调函数，index为要去第几页
     alert(index);
   },
   changeNumberOfPage: function (val) {
     // 改变每页显示数量回调函数
     alert(val);
   }
})
```

### 后期维护

+ 修改样式：ued.css
+ 修改dom：index.html
+ 修改逻辑：pagination.js
+ 修改之后全局生效