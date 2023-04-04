---
title: 良好的git commit
date: 2023-04-04 20:20:52
tags:git
---

在实际开发中我们可能会忽视 git commit 的作用，仅仅以为它就是代码提交的一个注释。
良好的 commit 有助于代码查阅，对于开发或者管理都是非常有益的。

借鉴一些优秀开源项目的提交规范总结如下
[commit-type]:[content]

```
feat：新功能、新特性；
fix:  bug fix；
perf：更改代码，以提高性能；
refactor：代码重构（重构，在不影响代码内部行为、功能下的代码修改）；
docs：文档修改；
style：代码格式修改, 此处不指代css之类的样式，而是格式或者排版；
test：测试用例新增、修改；
build：影响项目构建或依赖项修改；
revert：恢复上一次提交；
ci：持续集成相关文件修改；
chore：其他修改（不在上述类型中的修改）；
release：发布新版本；
workflow：工作流相关文件修改。
```

例如 `feat:用户注册`就代表新增了用户注册功能，通过 commit 的类型前缀来快速判断这个功能干了什么

如果分的更加仔细可以在 commit 上带上模块信息
[commit-type] ([module]):[content]
例如`fix(user):修复登录异常`
