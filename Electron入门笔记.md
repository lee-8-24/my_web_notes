# Electron

[toc]

## 一、简介

Electron是由`Github`开发，用HTML，CSS和JavaScript来构建跨平台桌面应用程序的一个开源库。 Electron通过将Chromium和Node.js合并到同一个运行时环境中，并将其打包为Mac，Windows和Linux系统下的应用来实现这一目的。

Electron用 web 页面作为它的 GUI，而不是绑定了 GUI 库的 JavaScript。它结合了 Chromium、Node.js 和用于调用操作系统本地功能的 APIs（如打开文件窗口、通知、图标等）。

<img src="https://pic2.zhimg.com/v2-0f66348b64acbd3c150fbfb7882344a1_r.jpg">

## 二、配置

**配置Node.js**

默认已经配置好了

**安装electron**

> 建议修改electron的源为国内源

```
export ELECTRON_MIRROR="https://npm.taobao.org/mirrors/electron/"
```

安装

```
npm install electron -g
```



## 三、进程

Electron进程分为主进程和渲染进程

**主进程**

electron里，运行`package.json`里main脚本的进程围殴主进程。主进程控制应用的生命周期，主进程创建Web形式的GUI，而整个Node API内置其中

**渲染进程**

每个electron页面运行自己的进程，称为渲染进程

主进程使用` BrowserWindow` 实例创建页面。每个 BrowserWindow 实例都在自己的渲染进程里运行页面。当一个 BrowserWindow 实例被销毁后，相应的渲染进程也会被终止。

主进程管理所有页面和与之对应的渲染进程。每个渲染进程都是相互独立的，并且只关心他们自己的页面。

在 electron 中，页面不直接调用底层 APIs，而是通过主进程进行调用。所以如果你想在网页里使用 GUI 操作，其对应的渲染进程必须与主进程进行通讯，请求主进程进行相关的 GUI 操作。



## 三、创建应用

```
electron-demo/
├── package.json
├── main.js
└── index.html
```

`main.js`

```
const electron = require('electron');

const {
  app, // 控制应用生命周期的模块
  BrowserWindow, // 创建原生浏览器窗口的模块
} = electron;

// 保持一个对于 window 对象的全局引用，如果不这样做，
// 当 JavaScript 对象被垃圾回收， window 会被自动地关闭
let mainWindow;

function createWindow() {
  // 创建浏览器窗口。
  mainWindow = new BrowserWindow({width: 800, height: 600});

  // 加载应用的 index.html。
  // 这里使用的是 file 协议，加载当前目录下的 index.html 文件。
  // 也可以使用 http 协议，如 mainWindow.loadURL('http://nodejh.com')。
  mainWindow.loadURL(`file://${__dirname}/index.html`);

  // 启用开发工具。
  mainWindow.webContents.openDevTools();

  // 当 window 被关闭，这个事件会被触发。
  mainWindow.on('closed', () => {
    // 取消引用 window 对象，如果你的应用支持多窗口的话，
    // 通常会把多个 window 对象存放在一个数组里面，
    // 与此同时，你应该删除相应的元素。
    mainWindow = null;
  });
}

// Electron 会在初始化后并准备
// 创建浏览器窗口时，调用这个函数。
// 部分 API 在 ready 事件触发后才能使用。
app.on('ready', createWindow);

// 当全部窗口关闭时退出。
app.on('window-all-closed', () => {
  // 在 macOS 上，除非用户用 Cmd + Q 确定地退出，
  // 否则绝大部分应用及其菜单栏会保持激活。
  if (process.platform !== 'darwin') {
    app.quit();
  }
});
```

`加入要显示的index.html文件`

直接运行下面命令`我直接git bash`

```
electron . 
```

![image-20210406145955133](https://img2020.cnblogs.com/blog/2024970/202104/2024970-20210406145958460-473190157.png)

## 四、打包

安装electron-packager

```
npm install electron-packager -g
```

目录中安装electron

```
npm install electron --save-dev
```

打包

```
electron-packager . electron-demo
```

![image-20210406150235577](https://img2020.cnblogs.com/blog/2024970/202104/2024970-20210406150235695-1957946457.png)

这样就做成了windows平台的客户端了



## 五、总结

本文主要参考https://github.com/nodejh/nodejh.github.io/issues/39，在此表示感谢。学习并初步入门Electron，把自己做的一个界面做成了app。确实十分有趣。