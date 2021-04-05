---
title: Windows 下 Node.js 和 npm 的升级
date: 2020-10-01 13:14:00
categories:
  - 技术爆炸
tags:
  - node
  - npm
---

> Node.js 在 Windows 下无法通过命令行升级，去官网下载最新版重装是唯一的方式。并且，当你重装 Node.js 时，npm 也会一并更新。推荐**直接重装**，除非特殊需求。

## 升级 Node.js

1.  检查当前 node 版本

    ```
    node -v
    ```

2.  打开 [Node.js 官网](https://nodejs.org/zh-cn/) 对比是否需要更新
<!-- more -->
3.  下载 LTS 最新版(推荐)
4.  安装

## 升级 npm

> 推荐直接重装 Node.js，这也是 [npm 官网](https://www.npmjs.com/get-npm) 推荐的安装/升级方式

### 一般升级

1. 检查当前 npm 版本

   ```
   npm -v
   ```

2. 官方升级命令

   ```
   npm install npm@latest -g
   ```

   > 如果报错 `npm ERR! code EEXIST` 先执行 `npm cache clean -f` 并再次尝试。如果没有解决请使用备选升级方式

### 备选方式

1. 将 Node.js 安装目录下的 `\node_modules\npm` 文件夹复制到另外的位置 如：`D:\npmTemp`
2. 删除 Node.js 安装目录下的 `npm npm.cmd npx npx.cmd` 文件 和 `\node_modules\npm` 文件夹
3. 在 `D:\npmTemp\bin` 中打开 cmd 运行以下命令

   ```
   node npm-cli.js i -g npm@latest
   ```

   npm 即可以顺利完成安装：

   ```
   D:\npmTemp\bin>node npm-cli.js i -g npm@latest
   D:\Program Files\nodejs\npm -> D:\Program Files\nodejs\node_modules\npm\bin\npm-cli.js
   D:\Program Files\nodejs\npx -> D:\Program Files\nodejs\node_modules\npm\bin\npx-cli.js
   + npm@6.14.8
   added 434 packages from 885 contributors in 40.387s
   ```
