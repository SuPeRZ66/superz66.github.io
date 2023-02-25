---
title: mbp(m1芯片)前端开发环境配置
date: 2023-02-25 15:05:08
tags: mbp
---

## mac 必备包管理工具 homebrew

```
/bin/zsh -c "$(curl -fsSL https://gitee.com/huwei1024/HomebrewCN/raw/master/Homebrew.sh)"
```

按照脚本提示安装好 homebrew 后在命令行中输入
`brew -- version
`
提示版本信息后表示安装成功

## nodejs 版本管理工具 nvm

对于前端来说不同项目对于 node 的版本依赖会有不同所以需要一个管理 node 版本的工具来方便切换 node 环境。其实 docker 也可以实现类似需求但我更推荐使用 nvm
我们使用 homebrew 来安装 nvm
`brew install nvm`
安装完成后在我们的～/.zshrc 文件中加入

```
export NVM_DIR="$HOME/.nvm"
  [ -s "/opt/homebrew/opt/nvm/nvm.sh" ] && \. "/opt/homebrew/opt/nvm/nvm.sh"  # This loads nvm
  [ -s "/opt/homebrew/opt/nvm/etc/bash_completion.d/nvm" ] && \. "/opt/homebrew/opt/nvm/etc/bash_completion.d/nvm"  # This loads nvm bash_completion
```

这样就可以在 zsh 中使用愉快的使用 node 命令或者 npm 全局安装的命令了。

## 打造舒适的终端

1、item2
`https://iterm2.com/downloads.html`
2、oh my zsh

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

```

3、spaceship(oh my zsh 美化)
4、git autojump zsh-autosuggestions zsh-syntax-highlighting（oh my zsh 插件）
5、fortune + cowsay 打造有趣的命令行界面
![](/img/cowsay.png)

## vscode 插件推荐

1.  auto close tag
2.  auto import
3.  auto rename tag
4.  docker
5.  error lens
6.  gitlens
7.  image preview
8.  live server
9.  power mode
10. prettier
