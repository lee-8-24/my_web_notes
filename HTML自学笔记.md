# HTML自学笔记

## 摘要

> 本片是在老师理论知识的指导下进行自己尝试总结(理论有部分搬运了[老师](https://qige.io/)的教程)，自己并做了一些尝试，最后结果还是很丑陋。但是我会不断完善的。

[toc]



## 一、HTML简介

**HTML**是超文本标记语言（HyperText Markup Language）的缩写。我们用 HTML 来构建 Web 页面即所谓的网页。

在我看来相当于Web的框架。需要与之后学习的CSS(起到修饰作用)，JS(内部行为)共同构建我们所说的网页。

我们可以将这些内容跟上传到互联网，然后让它和别人创建的相链接。

> 右键单击网页，可以查看网络源码，可以看到HTML文档



## 二、HTML文档结构

基本结构：

```html
<!DOCTYPE html>
<html>

<head> 
</head>

<body>

</body>
```

> 总结其基本构架：
>
> - html：元素。这个元素包裹了整个完整的页面，是一个根元素，它元素都嵌套到其中。
> - head：表示标签头，可以加入图标； 这个元素是一个容器，它包含了所有你想包含在HTML页面中但不想在HTML页面中显示的内容。这些内容包括你想在搜索结果中出现的关键字和页面描述，CSS样式，字符集声明等等。
> - body：含你能在页面看到的所有内容，包括文本，图片，音频，游戏等等



相关的一些练习：

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <link rel="shortcut icon" href="./images/ICO.svg" type="image/x-icon" />
    <title>LEE</title>
  </head>
  <body>
    <h2><mark>这是我的第一次练习</mark></h2>
    <h4>现在开始了:)</h4>
  </body>
</html>
```

> 相关解释
>
> - meta：这个元素设置文档使用utf-8字符集编码，utf-8字符集包含了人类大部分的文字。基本上他能识别你放上去的所有文本内容。毫无疑问要使用它，并且它能在以后避免很多其他问题。
> - link：指定页面的图标，出现在浏览器标签上。(试一试：你可随意下载一个`.ico`图标文件到工作目录中)
> - h1为一级标题，从一级到六级，包括了h1，h2...h6
> - p表示段落
> - mark为高亮



### :fire: HTML元素

HTML 使用"标记"（markup）来注明文本、图片和其他内容，以便于在浏览器中显示。HTML 标记包含一些规定的"元素"如 `<head>，<title>，<body>，<header>，<footer>，<article>，<section>，<p>，<div>，<span>，<img>，<aside>，<audio>，<canvas>，<d`atalist>，<details>，<embed>，<nav>，<output>，<progress>，<video> 等等。

检查我们刚创建的 HTML 文档你会发现，整个 HTML 就由一个个元素组成（可以嵌套），而元素则一般由一对标签（tag）构成。

> 注释：==ctrl+/==

**空元素**

元素都拥有**开始标签，内容，结束标签**。但有一些元素只有一个开始标签，通常用来在此元素所在位置插入/嵌入一些东西，如`<br>, <hr>, <input>, <img>, <a>`等等。我们称其为空元素，如下：

> br：换行
>
> input：输入框

**元素的属性**

元素是可以有相关属性的。属性包含元素的额外信息，这些信息不会在浏览器中显示出来。

```html
    <p><br /><br /><mark>元素属性</mark><br /><br /></p>
    <p title="这是title的属性">鼠标放置显示</p>
    <input title="请输入用户名" type="text" />
    <input title="密码" type="password" />
```

>一个属性必须包含如下内容：
>
>1. 一个空格，在属性和元素名称之间。(如果已经有一个或多个属性，就与前一个属性之间有一个空格。)
>2. 属性名称，后面跟着一个 = 号。
>3. 一个属性值，由一对引号 "" 引起来。



### :fire: 文本格式

```html
<p>您可以使用mark标记来<mark> highlight </ mark>文本。</ p>
<p> <del>此行文本应视为已删除的文本。</ del> </ p>
<p> <s>此行文本已被视为不再准确。</ s> </ p>
<p> <ins>此行文本应被视为文档的补充。</ ins> </ p>
<p> <u>此行文本将显示为带下划线的</ u> </ p>
<p> <small>此行文本应视为精美文字。</ small> </ p>
<p> <strong>此行以粗体显示。</ strong> </ p>
<p> <em>此行呈现为斜体文本。</ em> </ p>
```

> `<mark>highlight</mark>`高亮
>
> `<del>This line of text is meant to be treated as deleted text.</del>`划掉



### :fire: 超链接

没有超链接就没有万维网（World Wide Web）。基本上，我们可以把任何东西加上超链接，不过常用的是文本、图片等。

这里我设计了一个重庆交通大学的超链接

```html
<a href="http://www.cqjtu.edu.cn/" target="_blank"><em>重庆交通大学</em></a>
```

说明：

1. `href`即为要跳转去的地址 ==URL（Uniform Resorce Locator )==
2. `target`属性为`_blank`表示在==新的页面==打开超链接（默认是在当前页面打开即`_self`）
3. 超链接标签包含的内容（当前为文字"百度一下"）即为显示在页面上供用户点击的

**锚点**

锚点，也称为书签，用于标记页面的某个元素或位置。通过锚点，我们可以轻易的在==长页面内==实现跳转。

先使用`id`属性生成某元素的锚点，然后再使用超链接指向该锚点即可。

```html
<h3 id="C1">这是一个锚点</h3>
<a href="#C1"><br />返回头部</a>
```

>**注意：**
>
>1. 元素的`id`值必须是唯一的，也即页面不能再有其它元素的`id`值为`C4`
>2. 超链接中的地址需要有`#`符号



### :fire: 图片及文件路径

```html
    <!-- 图片及文件路径，这个是绝对路径img -->
    <img src="https://riyugo.com/i/2021/03/02/nt32k2.png" alt="MDB Logo" />
    <p>
      <mark><br />CLIMB!!<br /></mark>
    </p>
```

```html
 <!-- 相对路径 -->
    <img src="./images/test1.jpg" alt="MDB Logo" width="400" height="400" />
```



> 图片URL获取需要==图床==，可以采用空间和微博生成，当然也可以用一些免费图床
>
> 以下都可以采用
>
> [薄荷图床](https://riyugo.com/)(国内免费的图床)
>
> [国外免费图床](https://sm.ms/)
>
> [IO图床](https://www.imageoss.com/)

说明：

1. `src`属性为要显示图片文件的位置 URL，即图片文件的路径
2. `alt`属性当获取图片出现问题时显示的文字（占位符）
3. 可为图片指定高宽度，但不建议（可能导致图片变形）

**提示：** 对于小尺寸的图片，现在可采用 **base64** 编码进行，可提高页面加载速度，提升用户体验。[可前往一试](https://c.runoob.com/front-end/59)。(小图比较合适)

```html
<!-- 生成base64编码后的引用方式 -->
<p><br /><mark>ICON</mark><br /><br /></p>
<img
      src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAMgAAADI.../>
```

**文件路径**

为获取图片文件，我们需要指定该文件位于何处，这称为文件路径。文件路径有相对路径和绝对路径两种。

上面图片的例子即为绝对路径。下面是相对路径的例子：

- `<img src="picture.jpg">`  该图片文件与当前文档在同一目录中  
- `<img `src="./images/picture.jpg">`  该图片文件在当前目录下的`images`目录中 
-  `<img src="../picture.jpg">`  该图片文件在上一级目录中

### :fire: 表格

```html
  <table>
    <tr>
      <th>Firstname</th>
      <th>Lastname</th>
      <th>Age</th>
    </tr>
    <tr>
      <td>Jill</td>
      <td>Smith</td>
      <td>50</td>
    </tr>
    <tr>
      <td>Eve</td>
      <td>Jackson</td>
      <td>94</td>
    </tr>
  </table>
```

代码中，`<tr>`表示行, `<td>`表示行中的单元, `<th>`是表头的单元（将会加粗显示）

**说明：** 当前这个表格比较丑陋，有关表格的美化我们在 CSS 部分学习。



### :fire: 列表

我们也可以使用列表来呈现内容，分为无序列表和有序列表。

**无序列表**

```html
<ul>
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ul>
```

无序列表使用`<ul>`标签，默认使用**实心圆点**作为每项的标志，其它的标志可以是空心圆`circle`，实心方块`square`以及不出现标志。

```html
<ul type="square">
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ul>
```

**有序列表**

```html
<ol>
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ol>
```

有序列表使用`<ol>`标签，默认使用**数字**作为每项的标志，其它的标志可以是大写字母`A`，小写字母`a`，罗马字母`i`等。

```html
<ol type="a">
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ol>
```



### :fire:表单 Form

当网站需要获取我们的一些信息如：用户名、密码、选择买什么、买多少、提出意见等等时，我们就需要使用表单（form）来让用户填写或选择。

请输入如下代码进行学习：

```html
<form>
  <!-- 文本框，注意有 placeholder 提示符 -->
  用户名：<br>
  <input type="text" name="name" placeholder="请输入用户名"><br>
  <!-- 密码框 -->
  密码：<br>
  <input type="password" name="ps" placeholder="请输入密码"><br>
  年龄：<br>
  <!-- 数字输入框，注意 min 和 value 属性-->
  <input type="number" name="age" min="18" value="18"><br>
  <!-- 单选按钮, 注意 checked 属性 -->
  性别：<br>
  <input type="radio" name="gender" value="male" checked> 男<br>
  <input type="radio" name="gender" value="female"> 女<br>
  <input type="radio" name="gender" value="other"> 其它<br>
  <!-- 下拉列表，注意 selected 属性 -->
  党派：<br>
  <select name="party">
    <option value="D">民主党</option>
    <option value="R" selected>共和党</option>
    <option value="N">无党派</option>
  </select><br>
  <!-- 多选框 -->
  您有哪些交通工具：<br>
  <input type="checkbox" name="vehicle1" value="Bike"> 自行车<br>
  <input type="checkbox" name="vehicle2" value="Motocycle" checked> 摩托车<br>
  <input type="checkbox" name="vehicle3" value="Car"> 轿车<br>
  <input type="checkbox" name="vehicle4" value="Jet"> 飞机<br>
  <!-- 日期选择器 -->
  您的工作日期：<br>
  <input type="date"><br>
  <!-- 文件选择器 -->
  上传您的照片:<br>
  <input type="file" name="photo"><br>
  <!-- 文本输入区域，注意 rows 和 cols 属性 -->
  您的建议：<br>
  <textarea name="message" rows="5" cols="30">
    The cat was playing in the garden.
  </textarea><br><hr>
  <!-- 表单提交/重置按钮，将表单中的数据取消或传输给服务器端进行处理 -->
  <input type="submit" value="提 交">
  <input type="reset" value="重 置">
</form>
```

**提示：** 当提交时，表单中没有`name`属性的元素将不会提交，比如上面工作日期的选择器。有`name`属性的元素其`value`的值将提交给服务器。

> 这里我创建了一个超链接`<a href="./FIRST_3_2_2.html" target="_blank">点击跳转至表单</a>`





### :fire: 其它

HTML 的元素可以以称为**区块** 或 **内联**的方式进行显示。

**区块元素**

区块元素在浏览器显示时，通常会以**新行**来开始（和结束）。如：`<h1>, <pre>, <ul>, <table>，<`div> 等。

```html
<h2>区块元素</h2>
<div>Hello</div>
<div>World</div>
<p>单独一行</p>
```

**内联元素**

内联元素相反，他们总是一个接一个进行显示，不会新起一行。如： `<span>, <input>, <td>, <a>, <img>`等。

```html
<h3>下面的元素将在一行中显示</h3>
<span>姓名：</span>
<input name="username">
<span>哈哈哈</span>
<a href="https://google.com/">Google</a>
<img src="https://mdbootstrap.com/img/logo/mdb192x192.jpg">
```

**预设格式**

如果你想在网页中展示一首诗或一些特别格式的文本，那么请使用`pre`标签。

```html
<!-- pre标签中的内容将保持格式不变 -->
<pre>
....
              
</pre>
```

**特殊字符**

考虑下面的代码将显示成什么？

```html
<p>有多          远，滚                         多远！</p>
```

或者你希望在页面显示一段 HTML 的源代码，你打算用标签`<pre>`:

```html
<pre>
  <h1>这是个一级标题</h1>
  <p>这是一个段落<p>
  <a href="https://twitter.com/">眼见何事，情系何处，身处何方，心思何人</a>
<pre>
```

以上代码将得不到你想要的结果。
原因是：在 HTML 中，某些字符是预留的。
在 HTML 中不能使用小于号（<）和大于号（>），这是因为浏览器会误认为它们是标签。
如果希望正确地显示预留字符，我们必须在 HTML 源代码中使用字符实体（character entities）

```html
<p>有多&nbsp;&nbsp;&nbsp;远，滚&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;多远！</p>
<hr>
<h2>test.html</h2>
<pre>
  &lt;h1&gt;这是个一级标题&lt;/h1&gt;
  &lt;p&gt;这是一个段落&lt;p&gt;
  &lt;a href="https://twitter.com/"&gt;眼见何事，情系何处，身处何方，心思何人&lt;/a&gt;
<pre>
```



## 三、结果

这个结果还是很丑陋的，没有CSS的修饰确实没有很好的效果，暂且借用了老师的css文件，实现稍微好看一点儿的效果，这时第一次。

![](https://img2020.cnblogs.com/blog/2024970/202103/2024970-20210309105612766-1215822592.png)

![](https://img2020.cnblogs.com/blog/2024970/202103/2024970-20210309105620352-2053462496.png)

![](https://img2020.cnblogs.com/blog/2024970/202103/2024970-20210309105624956-1850957642.png)



## 四、补充视频学习

### :star: meta标签

写在head，设置网页的元数据，不是给用户看，爬虫用户看(搜索引擎可以看到)

- charset 网页的字符集
- name数据的名称
- content数据的内容
- keywords 表示网站的关键字，可以使用多个关键字(可以直接看网站学习)
- description：用于指定网站的描述，会显示再搜索引擎中的搜索结果中 
- 对网页重定向

> title标签的作用会作为搜索记过的超链接显示

==MDN==--文档

```html
<metal http-eqiv="refresh" content="3;ur;=https://www.baidu.com">
```

请求重定向

### :star: 图片

使用img

img属于替换元素，介于块元素与行元素之间，具有两种元素的特点

alt 属性是对图片的说明，这个描述，默认情况下不会显示，但是图片无法加载时会显示。搜索引擎根据alt来找到图片。

width图片宽度，height表示高度

移动端经尝需要对图片缩放（大变小）

**图片格式**

jpeg==jpg

- 颜色多，不支持透明，不止动图
- 显示照片

gif

- 颜色少，支持简单透明，支持动图

png

- 支持颜色丰富，支持复杂透明，不支持透明
- 专为网页而生

webp

- 谷歌新推出的，专门用来表示网页中图片的
- 缺点，兼容性不好

一种格式。所有优点，文件也小

效果一样用小的。效果不同用效果好的，logo大多都是gif



base64，将图片进行编码



### :star:内联框架

iframe

当前页面中引入了其它网页

```
 <iframe src="https://www.baidu.com/" width="800" height="600"></iframe>
```

大部分用不到，把一个网页当作一个窗口引入到当前网页

### :star: 音频视频文件播放

**音频**

audio 标签用来向网页中引入一个外部的音频文件

音视频文件引入时，默认情况下不允许用户控制播放停止。

加入**controls**，就加入了控制组件

```html
<audio src="./source/王北车 - 陷阱.flac" controls autoplay></audio>
```

**autoplay** 打开音乐时自动播放，但是大部分浏览器不能自动播放

**loop**从头播放

除了以上方式，还可以通过

```html
<audio controls>
    对不起，您的浏览器不支持播放音频！
    <source src="./source/王北车 - 陷阱.flac">
</audio>
```



**视频**

```
<video src="./source/最短路径.mp4" controls loop></video>
```

video和音频的使用方式是一样的



买服务器，一是服务器，二是带宽



音频和视频一般不放本地，可以引别人的，就比如用aframe来引，分享得出连接即可。

==26看完了==

### :star:块元素与行内元素

一般通过块元素对页面进行布局

- 一般在块元素内放行内元素内
- 但是不会在行内元素放块元素
- 块元素基本上什么都能放
- p元素内不能任何块元素

> 浏览器会自动把不符合规范的内容进行修正

行内元素主要来包裹文字

### :star: 标签

```html
	 <!-- 头部 -->
      	<head>

        </head>
        <!-- 主体，只有一个main -->
        <main>

        </main>
        <!-- footer，表示底部 -->
        <footer>
            
        </footer>
```

`<nav>`表示网页中的导航

`<aside>` 表示边的解释，不是主要内容但是是相关内容,侧边栏

`<article>`表示文章

本身显示效果并没有任何区别，css来修饰

`<section>`表示一个独立的区块，上面的标签都不能表示使用section

`<div>`万用，div是==最常用的==，可以代替上面所有

`<span>`是行内元素，用于在网页中选取文字

> 这些标签显示效果都是一样的就是语义的差别