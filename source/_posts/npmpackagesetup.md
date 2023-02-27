---
title: 如何创建一个基于vue的npm包
date: 2023-02-27 19:32:57
tags: npm
---

##前言
说来惭愧写了这么多年前端，用了这么多别人的包。最近项目中用到一个库没有 vue3 的版本所以打算在业余时间造个轮子。先来说下 npm 包的发布流程吧。后续会更新我的 npm 包的具体文档。

## 正文

### 1.创建 npm 账号

想要创建 npm 包首先得创建一个 npm 账号
`https://www.npmjs.com/`
期间可能会被墙需要挂梯子

### 2.创建一个 vue3 项目

`npm create vite@latest my-vue-app -- --template vue`

### 3.修改 vite.config.js

修改 vite 打包的相关配置

```
  build: {
    lib: {
      entry: path.resolve(__dirname, "src/your_enter_file_path/index.js"), //这边的路径为npm包的入口文件
      name: "your_global_name",//暴露的全局变量名称
      fileName: "your_file_name", //输出的包文件名
    },
    rollupOptions: {
      // 确保外部化处理那些你不想打包进库的依赖
      external: ["vue",],
      output: {
        // 在 UMD 构建模式下为这些外部化的依赖提供一个全局变量
        globals: {
          vue: "Vue",
        },
      },
    },
  }
```

### 3.修改 package.json

```
"name": "your_npm_name", //这边是上传到npm的包名也就是npm i <your_npm_package_name> 最好不要起以@开头的包
"private": false,//需要设置非私有包 不然需要付费
"files": [
    "dist" //打包文件所在文件夹
  ],
 "main": "./dist/your_file_name.umd.cjs", //   使用require规范引入会响应该对象
 "module": "./dist/your_file_name.js",// es module规范使用import能导入
 "types": "dist/your_file_name.d.ts",//如果是ts要加这个
 "exports": {
    ".": {
      "import": "./dist/your_file_name.js", //指定导出模块 es module
      "require": "./dist/your_file_name.umd.cjs" //指定导出模块 require模式
    },
    "./dist/style.css": "./dist/style.css" //导出css
  }
```

通过`npm run build` 会在根目录的 dist 文件夹下面出现
1.your_file_name.umd.cjs
2.your_file_name.js
3.style.css
4.your_file_name.d.ts //如果用 ts

## 4.发布到 npm

在项目根目录执行
`npm login`
输入账号密码登陆成功后执行
`npm publish --access=publish`
等待发布成功

## 5.如何测试 npm 包

首先在 vue1 项目根目录执行`npm link`
然后在测试 vue2 项目根目录执行 `npm link vue1`

## 完结 撒花 🎉🎉🎉
