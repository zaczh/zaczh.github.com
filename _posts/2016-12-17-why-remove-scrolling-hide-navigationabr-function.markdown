---
layout: post
title:  "为什么移除了滚动隐藏导航栏的功能？"
date:   2016-12-17 22:44:01 +0800
categories: jekyll update
---
说起这个问题，我们应该先想想：我们为什么要隐藏导航栏？原因是隐藏了之后，页面的展示空间变得更大了，用户可以看到更多内容。但是这个页面并不是完整的，隐藏了导航栏，会给人一种不知身在何处的错觉。
因此，这个功能最好用在导航控制器的第一个页面上，因为第一个页面无需返回按钮，所以即使不展示导航栏，也是OK的。Music应用就是这么做的。

如果非要这么做的话，那就要注意这种“隐藏”状态只是一个临时的中间状态，其他非浏览操作都必须恢复原始的状态，这就是为什么当你在全屏状态下的时候，无法通过左侧的边缘滑动手势返回到上一个页面，而必须先通过一次下滑操作使导航栏显示出来。

非开发人员可能会问：为什么要多此一举，这个时候右滑返回有什么问题吗？这里有几点要说明一下。首先，从交互设计上来看，这种滑动返回很难提供一致性的体验。当前页面隐藏了导航栏，但是上一个页面却不一定。如果不一致，那样就会有一个过渡效果，那样不太好看。另外一点，iOS系统禁止在导航栏隐藏情况下右滑返回。当然，开发者也可以使用自己添加手势的方式绕过这个问题（实际上在saralin 1.8.2的开发前期我已经实现了这个），但是依然无法回避前述第一个问题，效果比较拙劣。

导航栏的变化还有另一种方式，那就是改变透明度。效果如下：刚打开页面的时候，导航栏正常显示，当页面往上滚动到一定位置的时候，导航栏变的透明（有时候会有个渐变效果）。手机QQ里面的空间就是用的这种效果。
