# Angular学习1

### 一、需要知识

==html+css+js+es6+Typescript==



### 二、安装配置

下载nodejs

下载npm

下载cnpm

建议如下代码，换成淘宝源

`npm install -g cnpm --registry=https://registry.npm.taobao.org`



### 三、下载

输入`cnpm install -g @angular/cli`后开始下载

![](https://img2020.cnblogs.com/blog/2024970/202104/2024970-20210408161928587-1500347670.png)

下载完成后输入 `ng v`，出现如下安装成功

![](https://img2020.cnblogs.com/blog/2024970/202104/2024970-20210408162210909-885363673.png)

### 四、创建新的项目

`ng new angular01`

(如果出现如下错误)

![](https://img2020.cnblogs.com/blog/2024970/202104/2024970-20210408163814784-256393378.png)

建议，回到C盘，卸载angular

用下面的命令

`npm uninstall -g @angular/cli`

然后重新用npm安装

`npm insatll -g @angular/cli`



安装后重新执行命令(下面是跳过安装以来)

`ng new angular02 --skip-install`

> npm有点慢，可以用cnpm

创建好如下依赖库

![image-20210408164033185](https://img2020.cnblogs.com/blog/2024970/202104/2024970-20210408164033402-32428969.png)



打开项目

`ng serve --open`

结果如下：

![image-20210408164344083](https://img2020.cnblogs.com/blog/2024970/202104/2024970-20210408164344414-1426891068.png)

### 五、项目导入VS code

用vs code 打开刚刚创建的项目

下载Angular相关插件

![image-20210408164857359](https://img2020.cnblogs.com/blog/2024970/202104/2024970-20210408164858191-692789545.png)

然后就可以进行相关开发了

![image-20210408165434724](https://img2020.cnblogs.com/blog/2024970/202104/2024970-20210408165435890-1971595686.png)