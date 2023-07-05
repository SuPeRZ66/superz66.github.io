---
title: element plus部分组件在zoom下位置偏移问题
date: 2023-07-05 20:27:59
tags: elementplus zoom
---

## 问题描述

在高分屏的 win 系统中设置了系统缩放会使网页显示出现异常,所以我使用 zoom 属性根据系统的 dpr 进行缩放。在 zoom 的值不为 1 并且不在 body 或 html 元素上的时候，element plus 的日期组件以及 select 组件的弹窗位置会偏移。因为这些组件生成的 dom 是在 body 下的，所以无法通过父元素进行修正。

## 解决方法

设置 teleported 属性让生成的元素在 body 下，这样就可以通过父元素进行修正了。
