---
title: vue hooks
date: 2023-02-24 21:05:59
tags: vue
---

### 什么是 hooks？

字面意思是”钩子“，其实是指系统运行到某一时期时，会调用被注册到该时机的回调函数。

### vue 中的 hooks

在 vue 中代表 hooks 的就是组合式 api。以 “use” 作为开头的，提供方法复用、组件状态管理等功能的合集。

### hooks 的好处

在 vue2 中，要抽离公共逻辑以及相关的生命周期只能用 mixin，而 mixin 的缺点是不知道方法来自哪的。
比如

```
mixins:[a,b,c]
created(){
    let from_mixin = this.abc
    this.foo()
    this.bar() //我们并不知道变量abc以及foo，bar方法是从哪个mixin调用的，如果mixin数量众多，可能会引起变量重名等问题，那将会是可怕的。
}
```

### 相比 vue2，组合式 api 的好处

vue2 的 class 写法导致代码块是分散的，比如定义方法，以及生命周期以及各种 this 指向问题。这在单页应用中如果功能复杂并且引入了很多 mixin 的话可读性非常差。
vue3 中使用函数式编程配合组合式 api 可以让代码逻辑更加清晰

```
//首先以vue2为例
export default{
    mixins: [amixins],
    data(){
        return{
            a:1,
            b:2
        }
    }
    mounted(){
        this.foo(this.c)
        this.bar()
    },
    method:{
        foo(){
            let d = this.a+this.b
        }
    }
}
```

```
//vue3组合式api写法
const a= ref(1)
const b = ref(2)
const {c,bar} = useHooks()
const foo = ()=>{
    let d = a.value+b.value
}
onMounted(()=>{
    foo(c)
    bar()
})

```

结果一目了然
