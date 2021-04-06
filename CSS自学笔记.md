> 本文主要是由理论知识，设计实践两大部分组成，理论知识中有关于对相关重点的理解，结合自己的想法做了一个游乐场排队系统的简单界面。还是很丑陋，会不断完善



## 一、CSS简介

**CSS**是级联样式表（Cascading Style Sheets）的缩写。HTML 用于撰写页面的内容，而 CSS 将决定这些内容该如何在屏幕上呈现。

它包含了如：整个页面的布局，元素的位置、距离、颜色、大小、是否显示、是否浮动、透明度等等。

内容HTML和表现CSS的分离在代码的撰写与维护过程中，内容如果和修饰分离，便于维护。



## 二、CSS 语法

### :fire: 基本语法及解释

一条CSS样式规则由两个主要的部分构成：选择器，以`{}`包裹的一条或多条声明:

> `h1 {color:blue;front-size:12px}`
>
> - h1是选择器
> - color；front-size：为属性
> - blue；12-px：值
>
> 这条规则表明，页面中所有的一级标题都显示为蓝色，字体大小为12像数。

- 选择器是您需要改变样式的对象（上图的规则就一级标题生效）。
- 每条声明由一个属性和一个值组成。（无论是一条或多条声明，都需要用`{}`包裹，且声明用`;`分割）
- 属性）是您希望设置的样式属性。每个属性有一个值。属性和值被冒号分开。
- `/*`。。。。`*/`为注释，其注释跟C语言中的注释一样，不同于HTML的注释

>  对于color，可以如上面所示选取颜色，当然也可以通过RGB来组件自己的颜色比如#ffffff，没两位代表一个颜色分别是红绿蓝，可以设置==16进制rgb==来给颜色
>
>  对于font-size：分为像素点大小和%大小，一般对我们来说采取百分比更好一点，方便我们对图片的整体浏览。对于默认的像素点来说是16px

### :fire: 选择器

有两种id和class，一般来说==class==用得更多一点儿(我在这里调试了class选择器)

==id选择器是以#开头==


> id选择器适用范围只有一个元素

==class选择器是以.开头==

```css
/*线路规划与排队状态 */
.state{
    background: chocolate;
    color: cyan;

}
.line{
    background-color: crimson;
    color:gold;

}
```

上面的代码给了背景和字体颜色
如下所示的页面：

```html
  <div class="state"><a href="#" target="_blank">各项目等待人数与等待时</a></div>
  <div class='line'><a href="#" target="_blank">路线规划</a></div>>
```

 由上例可看出，元素的class值可以多个，也可以重复。因此，实际应用中，class 选择器应用非常普遍。




## 三、 CSS 如何生效

==三种方法：外部样式表，内部样式表，内联样式==

当然，我们最需要学会的就是外部样式表，这种便于维护

### :fire: 外部样式表

新建如下内容的一个 HTML文件（后缀为.html)：

```html
<!DOCTYPE html>
<html>

    <head>
        <!-- Basic -->
        <meta charset="utf-8">
        <!-- 基本css -->
        <link rel="stylesheet" href="./css/prj_1.css">
        <!-- 特殊css -->
        <link rel="stylesheet" href="./css/prj_2.css">

        <!-- Site Meta -->
        <title>游乐场排队系统</title>
        <link rel="shortcut icon" href="./image/游乐场.ico" type="image/x-icon" />
    </head>

    <body>
        <h1>游乐场排队系统</h1>
        <img src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2F5b0988e595225.cdn.sohucs.com%2Fq_70%2Cc_zoom%2Cw_640%2Fimages%2F20190223%2F50eb818b909347e8acd6b64456608966.jpeg&refer=http%3A%2F%2F5b0988e595225.cdn.sohucs.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1617867560&t=09596d465805e13e2a28a6fe9e4eb805" alt="error" width="50%" height="400px"  >
        <div class="state"><a href="#" target="_blank">各项目等待人数与等待时间</a></div>
        <div class='line'><a href="#" target="_blank">路线规划</a></div>
    </body>

</html>
```

> 我在同一个目录下建立了css文件夹，下面放了两个文件prj_1.css和prj_2.css一个存放基本的css修饰，一个存放class选择器
>
> **提示：** 文件时路径就变为 `./css/mycss.css`之类的。

==很重要的是，通过这种操作，我们可以复用==

> 接下来的两种样式，我就是复制了教程里面的代码，实现了一下，并未做出什么修改

### :fire: 内部样式表

我们也可以将样式放在 HTML 文件中，这称为内部样式表。如：

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <!-- 注意下面这个语句，将导入外部的 mycss.css 样式表文件 -->
  <link rel="stylesheet" type="text/css" href="mycss.css">
  <title>页面标题</title>
  <style>
    body {
      background-color: linen;
      text-align: center;
    }
    h1 {
      color: red;
    }
    .haha {
      margin-top: 100px;
      color: chocolate;
      font-size: 50px;
    }
  </style>
</head>
<body>
  <h1>我是有样式的</h1>
  <hr>
  <p class="haha">还是有点丑：)</p>
</body>
</html>
```

该例子与上述例子一样的效果，但注意在`<head>`元素中引入了`<style>`标签，放入了样式。

> **提示：** 一般而言，只有页面的样式规则较少时可采用这种方式。

### :fire: 内联样式

所谓内联样式，就是直接把样式规则直接写到要应用的元素中，如：

```css
<h3 style="color:green;">I am a heading</h3>
```

> **提示：** 内联样式是最不灵活的一种方式，完全将内容和样式合在一起，实际应用中非常少见。

### :fire: 级联的优先级

优先级的高低如下：

1. 内联样式
2. 内部样式表或外部样式表
3. 浏览器缺省样式

> **提示：** 其实，一句话可总结为哪个样式定义离元素的距离近，哪个就生效。
>
> **思考：** 上面优先级第2项有内部样式表和外部样式表两个，到底哪个优先？





## 四、 盒子模型

盒子模型指的是一个 HTML 元素可以看作一个盒子。从内到外，这个盒子是由**内容 content, 内边距 padding, 边框 border, 外边距 margin**构成的，如下图所示：

![box](https://img-blog.csdnimg.cn/img_convert/c69bd2340558e1d45ee104908ba72d19.png)

> **说明：**
>
> - Content 盒子的内容，如文本、图片等
> - Padding 填充，也叫内边距，即内容和边框之间的区域
> - Border 边框，默认不显示
> - Margin 外边距，边框以外与其它元素的区域

html代码还是如上，但是prj2_css文件里的代码做出以下修改

```css
.img1{
    width:"50%";
    height:"400px";
    padding: 15px;
    margin: 25px;
}
.state{
    height: 200px;
    width: 200px;
    border:  5px solid lightsteelblue;
    padding: 25px;
    margin: 25px;
    background:deepskyblue;
    color:floralwhite;
    font-size: 20px;

}
.line{
    height: 200px;
    width: 200px;
    border: 10px solid gray;
    padding: 25px solid red;
    margin: 25px;
    background-color:forestgreen;
    color:ghostwhite;
    font-size: 20px;
}


```

打开浏览器看看效果。

![](https://img-blog.csdnimg.cn/img_convert/949dc672ffadf49cc78c09ef1d0cde6a.png)

**提示：** 在页面上点击鼠标右键，选择**审查元素**，你可清楚看到如下图所示的布局。

[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-2JHJJiDo-1615282678119)(https://qige.io/web/brief-css/img/4bc1c350e350a023.jpg)]

留意上图，你会发现一个元素真正占据的宽度应该是：
左外边距 + 左边框宽度 + 左内边距 + 内容宽度 + 右内边距 + 右边框宽度 + 右外边距

因此，我们在用`width`属性设置元素的宽度时，实际上只设置了其内容的宽度。



## 五、边框与边距

**提示：** 无论边框、内边距还是外边距，它们都有上下左右四个方向。



```css
.example-1 {
  border: 1px dotted black; /* 上下左右都相同 */
}
.example-2 {
  border-bottom: 1px solid blue; /* 只设置底部边框 */
}
.example-3 {
  border: 1px solid grey;
  border-radius: 15px; /* 边框圆角 */
}
.example-4 {
  border-left: 5px solid purple;
}
```

> - 比如我在当前代码的盒子里设置各圆角
> - 或者只设置左边的颜色，当然和内容之间的距离可以用padding来设置，只要加-left/right/bottom等

:fire: **边距**

下面样式说明了内边距的设置：

```css
padding: 20px; /* 上下左右都相同 */
padding-top: 20px;
padding-bottom: 100px;
padding-right: 50px;
padding-left: 80px;
padding: 25px 50px 75px 100px; /* 简写形式，按上，右，下，左顺序设置 */
padding: 25px 10px; /* 简写形式，上下为25px，左右为10px */
```

> 注意顺序为上下左右，顺时针方向



做出如下修改：

```css
 border-left: 7px solid yellow;
 border-radius: 15px; /* 边框圆角 */

```

加入圆角元素与设置为左边框

## 六、定位

`position`属性用于对元素进行定位。该属性有以下一些值：

- static 静态
- relative 相对
- fixed 固定
- absolute 绝对

设置了元素的`position`属性后，我们才能使用`top, bottom, left, right`属性，否则定位无效。

:fire: **static**

设置为静态定位`position: static;`，这是元素的默认定位方式，也即你设置与否，元素都将按正常的页面布局进行。
即：按照元素在 HTML出现的先后顺序从上到下，从左到右进行元素的安排。

:fire: **relative**

设置为相对定位`position: relative;`，这将把元素相对于他的静态（正常）位置进行偏移
试试如下的代码：

> 可以用它来设置相对位置



:fire: **fixed**

设置为固定定位`position: fixed;`，这将使得元素固定不动（即使你上下左右拖动浏览器的滚动条）。
此时元素固定的位置仍由`top, bottom, left, right`属性确定，但相对的是视口（viewport，就是浏览器的屏幕可见区域）
然后可以根据可见区域来设置存在位置，我设计了一个关于我们的图标悬浮于右上口，并且根据教程做了一个阴影立体感

```css
.fixed1 {
    position: fixed;
    top: 20px;
    right: 10px;
    padding: 6px 24px;
    border-radius: 4px;
    color: #fff;
    background-color:turquoise;
    cursor: pointer;
    box-shadow: 0 3px 3px 0 rgba(0,0,0,0.3), 0 1px 5px 0 rgba(0,0,0,0.12), 0 3px 1px -2px rgba(0,0,0,0.2);
  }
```

:fire: **absolute**

设置为绝对定位`position: absolute;`，将使元素相对于其**最近设置了定位属性（非static）的父元素**进行偏移。
如果该元素的所有父元素都没有设置定位属性，那么就相对于`<body>`这个父元素。




## 七、浮动

这种用法非常常用对于我们对元素的排列十分有用

在选择器里面加如下

```css
.float_left{
    float: left;
}
```

一个浮动元素会尽量向左移动，直到它的外边缘碰到包含框或另一个浮动框的边框为止。
浮动元素之后的元素将围绕它。

结果就好看很多：

![](https://img-blog.csdnimg.cn/img_convert/a5cc85e49b2bcb244a19757e02211f38.png)

一个元素浮动后，其后的元素将尽可能包围它，或者说出现在这个浮动元素的左或右方。
如果希望浮动元素后面的元素在其下方显示，可使用`clear: both`样式来进行清除。

## 八、最终结果
![](https://img-blog.csdnimg.cn/20210309174953210.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xlZV9nb2k=,size_16,color_FFFFFF,t_70#pic_center)



## 九、补充视频学习

### :flags: id选择器

id是不能重复的，一个用过了另一个就不能再用了

### :flags: class类

class可以重复

### :flags: 交集并集选择器

作用：选中同时符合多个条件的元素

格式：选择器1 选择器2 选择器3....全部满足才行

```css
div.red{
                font-size: 20px;
            }
```

注意：交集选择器中如果有元素选择器必须使用元素选择器开头

```css
 h1,span{
                color: lightcoral;
            }
```

并集选择器，可以同时作用多个选择器

### :flags: 父元素与子元素与祖先元素，兄弟元素

 **父元素**

- 直接包含子元素的元素叫父元素

**祖先元素**

- 祖先元素，直接包含后台带元素的元素叫祖先元素，父元素也属于祖先元素，后代元素也可以定义了

**兄弟元素**

- 兄弟元素，拥有相同父元素的元素

直接被父元素包含的元素是子元素

子元素选择器

作用：选中指定父元素的指定子元素

语法：父元素>子元素，

复合选择器可以混合使用



### :flags: 关系选择器

**子元素选择器**

作用：选择指定元素的指定子元素

结论：父元素>子元素

**后代元素选择器**

作用：选择中指定元素内的指定代元素

语法：祖先 后代

**兄弟元素选择器**

作用：选择下一个兄弟

语法：前一个+下一个

### :flags: 属性选择器

`title`鼠标移上去就会提示

`[属性名] `选择含有指定属性的元素

`[属性名=属性值]` 选择含有指定属性和指定值的元素

`[属性值^=属性值]` 选择属性名与属性值开头的元素，结尾用$

`[属性名*=属性值]`选择属性值中含有某值的元素的元素

### :flags: 伪类选择器

根据ul>li 可以直接生成

```html
ul>li*5
```

vs自带插件，会处理

伪类，不存在的类，用来描述一个元素的特殊状态

比如第一个子元素，背点击的元素，鼠标移入的元素

特点：一般情况下，都是以：开头

```css
            ul>li:first-child{
                color:red;
            }
```

`first-child`第一个子元素

`last-child`最后一个元素值

`nth-child()`选中那个填入特殊值即可

`nth-child(2n)`表示选中偶数个2n+1表示奇数位

以上这些伪类，都是根据所有子元素进行排序

`first-of-type`

`last-of-type`

`nth-of-type`

只找相同类型

not()否定伪类，将符合条件的元素从选择器中去除

`ul>li:not(:nth-of-type(3))`{

}

除了的意思



**超链接元素的伪类**

`a:link`：表示没有访问过的连接

`a:visited：`表示访问过的链接

用来表示访问过的连接

> 由于隐私的原因，visited只能改颜色

下面两种都可以用：

`:hover`表示鼠标移入状态 时变化

`:active`表示点击不移开



**伪元素选择器**

首字母下沉效果;

```css
p::first-letter{

​	font-size:50px;

}

p::first-line{

background-color:yellow;

}
div::before{
    content: '('
}
div::before{
    content:')'
}
```

> 前后会加上括号

### :flags: 样式的继承

我们为一个元素设置的样式同时也会应用到它的后代上

继承发生在祖先后代之间

继承的设计是为了方便我们的开发，继承的设计我们可以将一些通用的样式统一设置到共同的祖先元素上，这样只需设置一次即可让所有的元素拥有该样式

并不是所有的样式都会被继承，背景，布局等



### :flags: 选择器的权重

当通过不同的选择器，选中相同的选择器，并且为相同的样式设置不同的值时，样式冲突

由选择器优先级决定

选择器权重：内联样式--id选择器--类选择器--元素选择器



### :flags: em和rem

==em==是相对于元素字体大小来计算的

1em=1front-size

==rem==是相对于根元素的字体大小来计算的



### :flags: HSL值

HSL值/HLSA值

H  色相

S  饱和度

L  亮度

### :flags: 文档流

**layout**

网页是一个多层的结构，一层螺着一层

我们可以用css可以分每一层设置样式

作为用户来说只能看到最上层

文档流是网页的基础

所创建的元素默认在文档流中排列

**元素中两个状态**

- 在文档流中
- 不在文档流

**元素在文档流中有什么特点**

- 块元素
  - 会在页面中独占一行，总会
  - 默认宽度父元素的全部
  - 默认高度是被内容 (子元素)撑开
  - 自下向上垂直排列
- 行内元素
  - `<span>`行内元素不会独占一行
  - 行内元素会在页面从左至右水平排列
  - 行内元素的默认宽度和高度都是被内容撑开



### :flags: 默认样式

通常情况，浏览器都会为元素设置一些默认值

默认样式的存在会影响到页面布局，通常情况下便些网页时必须去除浏览器的默认样式

```
body{
	margin:0%;
	padding:0;
}
```

去掉边距，p与ul等也是一样的

```
*{
	margin:0;
	padding:0;
}
```

全部去掉`*` 表示全部

### :flags: 导航条

```html
<html>
    <head>
        <meta charset="UTF-8">
        <title>导航条</title>
        <link rel="stylesheet" href="../CSS/reset.css">
        <style>
            .nav{
                width: 1210px;
                height: 48px;
                background-color: darkgray;
                margin: 100px auto;
            }
            .nav li{
                float: left;
                /* 设置文字在付元素中垂直居中*/
                line-height: 48px;

                
            }

            .nav a{
                /* 将a转换为快元素 */
                /* display: block; */
                /* 去除下划线 */
                text-decoration: none;
                padding-left:  50px;
                padding-right: 50px;
                padding-top:10px; 
                padding-bottom:12px;
                font-size: 18px;
                color: white;
            }

            .nav a:hover{
                background-color:black;
                color: white;

            }
        </style>
    </head>

    <body>
        <ul class="nav">
            <li>
                <a href="#">HTML/CSS</a>
            </li>
            <li>
                <a href="#">Browser Side</a>
            </li>
            <li>
                <a href="#">Server Side</a>
            </li>
            <li>
                <a href="#">Programming</a>
            </li>
            <li>
                <a href="#">XML</a>
            </li>
            <li>
                <a href="#">Reference</a>
            </li>
        </ul>
        
    </body>
</html>
```

