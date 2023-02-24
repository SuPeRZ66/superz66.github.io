---
title: 扩展插件的ts类型
date: 2023-02-22 21:59:42
tags: typescript
---

## 为插件配置 ts 定义

在日常开发中会碰到一些仓库没有定义 ts 类型。
以 vite 为例，在 src 目录新建 xxx.d.ts

```
declare module "foo" {
  namespace bar {
    function xxx(type: string, opt?)
  }
}
```

假如碰到部分插件没有 ts 定义，但它是基于其他插件的，其他插件有 ts 定义。
这边以 jquery 为例子，假设有个插件为$("foo").bar()
我们需要为$对象扩展 bar 的定义,只需要在 xxx.d.ts 添加

```
declare global {
  interface JQuery { //这边的JQuery要和Jquery.d.ts文件里定义的名字一样
    bar(arg?: any): JQuery
  }
}
```
