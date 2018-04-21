---
layout: post
title: javascript之apply，bind，call
date: 2018-04-01 13:00:00 +0800
description: 对apply，bind，call有一定了解，但是每次使用都需要查阅资料，今天小记一篇。
img: software.jpg # Add image post (optional)
tags: [javascript, js, apply, bind, call]
---

### 描述

apply：在调用一个存在的函数时，你可以为其指定一个 this 对象。 this 指当前对象，也就是正在调用这个函数的对象。 使用 apply， 你可以只写一次这个方法然后在另一个对象中继承它，而不用在新对象中重复写该方法。

call：可以让call()中的对象调用当前对象所拥有的function。你可以使用call()来实现继承：写一个方法，然后让另外一个新的对象来继承它（而不是在新对象中再写一次这个方法）。

bind：bind() 函数会创建一个新函数（称为绑定函数），新函数与被调函数（绑定函数的目标函数）具有相同的函数体（在 ECMAScript 5 规范中内置的call属性）。当新函数被调用时 this 值绑定到 bind() 的第一个参数，该参数不能被重写。绑定函数被调用时，bind() 也接受预设的参数提供给原函数。一个绑定函数也能使用new操作符创建对象：这种行为就像把原函数当成构造器。提供的 this 值被忽略，同时调用时的参数被提供给模拟函数。

### 使用

```javascript
// 1、借鸡生蛋
function fn_bind(){
  console.log(arguments);
  // console.log(arguments.join());  报错没有join方法
  // 给arguments添加join方法
  console.log(Array.prototype.join.apply(arguments));
  console.log(Array.prototype.join.call(arguments));
  console.log(Array.prototype.join.bind(arguments)());
}
fn_bind('a','b','c','d');


// 2、和this一起使用，绑定上下文,this指向apply和call的第一个参数，不传参默认为全局对象（浏览器：window）
var word='this is window';
var duck={
  word:'嘎嘎嘎嘎'
}
var cat={
  word:'喵喵喵喵'
}
function speak(){
  console.log(this);
  console.log(this.word);
}
speak.apply(duck);
speak.apply(cat);
speak.call(duck);
speak.call(cat);
speak.apply(window);
speak.call();

// 3、执行函数
function fn (who, word) {
  console.log(who + ':' + word);
}

fn.apply(null, ['duck', '嘎嘎嘎嘎']);
fn.call(null, 'cat', '喵喵喵喵');
fn.bind(null, 'dog', '汪汪汪汪')();
```

### 区别

call()和apply()，只有一个区别，就是 call()方法接受的是若干个参数的列表，而apply()方法接受的是一个包含多个参数的数组，参照使用3-执行函数。
call()和bind()，bind()返回的是一个函数需要执行一下，参照使用3-执行函数。