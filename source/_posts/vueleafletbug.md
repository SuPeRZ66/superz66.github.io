---
title: vue3 leaflet undefined bug
date: 2023-03-01 19:23:50
tags: leaflet
---

## 问题复现

在 vue3 中初始化 leaflet 后如果对地图实例进行监听，那么地图在添加覆盖物的时候会出现报错比如 xxx is undefined，xxx is null,缩放异常等问题。

## 问题原理

leaflet 在元素添加到地图上后会在 map 实例上增加一个元素实例，而然 vue3 的 proxy 会深度监听动态添加的属性，原方法中 this 指向到了 proxy 代理来的属性上导致原方法丢失。

## 如何解决

添加到地图对象的时候使用 toRaw 方法让元素添加到原始地图对象上并且不触发更改。
[相关资料](https://cn.vuejs.org/api/reactivity-advanced.html#toraw)
