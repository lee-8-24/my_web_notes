# Bootstrap

## 一、Bootstrap

Bootsrtrap为我们提供设计框架，我的理解就是模板，让我们不懂美学设计的人员能够设计出很多漂亮的网页。

我跟着教程做了一个公司首页，主要包含以下三个部分：

- `header`元素放置导航
- `main`元素是页面主要内容
- `footer`元素是一些版权和其它链接

然后按照步骤进行填充，设计出了如下界面，当然大多数还是模板的功劳，这是一个游乐场排队系统的界面：

![](https://img2020.cnblogs.com/blog/2024970/202103/2024970-20210316111911321-1892581995.png)

下面是总结的我认为重要的点



## 二、导航条

### 自己总结如下：

```html
<nav>
</nav>
```

**:fire: nav格式设置**

- 在nav格式设置中出现了如下几条
- `.navbar`：这是导航条必须的样式, 去掉后便没有需要的样式
- `.navbar-expand-md`：表明当处于中等屏幕及以上尺寸(>768px)时, 导航条==扩展开==, 否则导航超链接不显示, 而显示一个折叠按钮.，==去掉之后会使得其始终为按钮==。
- success-color：表示主题颜色为绿色，当然还用`warning`表示黄色，`indigio`深蓝，
- `primary-color`表示天蓝

**:fire: 整体结构**

> 为什么要引入区块，并且要用container属性？
>
> 因为要不让导航条偏左放置，适合屏幕，符合美学。



:fire: **按钮设置**

> - `navbar-toggler`：用于我们折叠插件及其它行为
> - `datatarget`：定义了数据目标，也即折叠对象，这里是一个id设置。
> - `navbar-toggler-icon`：表示调用了三线图标

> 至于具体区域，使用了u1无序列表，设置好了相应的id；也设置了下拉方式。

:fire: **其它解释**

- `navbar-nav`：表明是导航条中的导航链接, 取消后将出现黑点，且字体颜色发生变化，不为超链接。
- `mr-auto`：该样式将会把其后的项(即搜索框`<form>`靠右对齐), 用到了自浮动，mr，表示margin-right，右边外边距
- `active`：注意这个样式, 它表明哪个超链接当前是激活的, 点击会有白色的框
- `sr-only`：意思是 `screen read only`, 为盲人上网设置的



### 代码如下：

```html
<header>
      <!--Navbar-->
      <nav class="navbar navbar-expand-md navbar-dark success-color">
        <div class="container">
          <!-- Navbar brand -->
          <a class="navbar-brand" href="#">犇犇大创</a>
          <!-- Collapse button -->
          <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#basicExampleNav"
            aria-controls="basicExampleNav" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>
          <!-- Collapsible content -->
          <div class="collapse navbar-collapse" id="basicExampleNav">
            <!-- Links -->
            <ul class="navbar-nav mr-auto">
              <li class="nav-item">
                <a class="nav-link" href="#">投诉与建议</a>
              </li>

              <!-- Dropdown -->
              <li class="nav-item dropdown">
                <a class="nav-link dropdown-toggle" id="navbarDropdownMenuLink" data-toggle="dropdown"
                  aria-haspopup="true" aria-expanded="false">关于我们</a>
                <div class="dropdown-menu dropdown-primary" aria-labelledby="navbarDropdownMenuLink">
                  <a class="dropdown-item" href="#">电话</a>
                  <a class="dropdown-item" href="#">邮箱</a>
                  <a class="dropdown-item" href="#">微信公众号</a>
                </div>
              </li>
            </ul>
            <!-- Links -->
            <form class="form-inline">
              <div class="md-form my-0">
                <input class="form-control mr-sm-2" type="text" placeholder="Search" aria-label="Search">
              </div>
            </form>
          </div>
          <!-- Collapsible content -->
        </div>
      </nav>
```



## 三、主体内容

### 自己总结如下

:fire:  **采用container来控制​**

对于属性右container的区块来说，默认分配为==12个==列

具体占据几列可以右col-6等标志来完成；

而在不同的状态下，比如中屏占据几列，小屏几列可以由col-md-6...来设置



:fire: **视觉深度**

刚巧在学习机器视觉，这个我可以解释一下

在机器视觉中，如何把三维的画面给压缩成二维提取呢，就是因为少了深度这个概念，把三维画面投影即得到了二维图。人眼在看周围环境的时候因为有深度所有有了视觉上三维的概念。

而在`view overlay z-depth-1-half`这个属性，使图片有了深度，可以让人们感觉到有一定的立体感。



:fire: **反白字体**

`mask rgba-white-light` 可以让字体反白



### 代码如下

```html
 <main class="mt-5">
      <!--Main container-->
      <div class="container">
        <!--Grid row 1-->
        <div class="row">
          <!--Grid column 1-->
          <div class="col-md-7 mb-4">
            <div class="view overlay z-depth-1-half">
              <img src="./img/乐园.jpg" class="card-img-top" alt="">
              <div class="mask rgba-white-light"></div>
            </div>
          </div>
          <!--Grid column-->
          <!--Grid column 2-->
          <div class="col-md-5 mb-4">
            <h2>游乐场排队系统</h2>
            <hr>
            <p>我们是一家专注于游乐场排队系统设计的公司。为客户提供数据分析，系统设计，等多维度，全方面的服务。致力于帮助管理人员合理规划、提升游客游玩体验</p>
            <a href="#" class="btn btn-primary">更多相关</a>
          </div>
          <!--Grid column-->
        </div>
        <!--Grid row-->
        <!--Grid row 2-->
        <div class="row">

          <!--Grid column-->
          <div class="col-lg-4 col-md-12 mb-4">

            <!--Card-->
            <div class="card">

              <!--Card image-->
              <div class="view overlay">
                <img src="./img/数据分析.jpg" class="card-img-top" alt="">
                <a href="#">
                  <div class="mask rgba-white-slight"></div>
                </a>
              </div>

              <!--Card content-->
              <div class="card-body">
                <!--Title-->
                <h4 class="card-title">面向管理者</h4>
                <!--Text-->
                <p class="card-text">我们提供定制数学建模，数据分析，策略建议与规划建议等方面的服务</p>
                <a href="#!" class="btn btn-indigo">了解更多</a>
              </div>

            </div>
            <!--/.Card-->

          </div>
          <!--Grid column-->

          <!--Grid column-->
          <div class="col-lg-4 col-md-6 mb-4">

            <!--Card-->
            <div class="card">

              <!--Card image-->
              <div class="view overlay">
                <img src="./img/乐园3.jpg" class="card-img-top" alt="">
                <a href="#">
                  <div class="mask rgba-white-slight"></div>
                </a>
              </div>

              <!--Card content-->
              <div class="card-body">
                <!--Title-->
                <h4 class="card-title">面向游客</h4>
                <!--Text-->
                <p class="card-text">我们提供路线规划，项目实时排队人数，预计排队时长等方面服务</p>
                <a href="./passanger.html" class="btn btn-indigo">功能展示</a>
              </div>

            </div>
            <!--/.Card-->

          </div>
          <!--Grid column-->

          <!--Grid column-->
          <div class="col-lg-4 col-md-6 mb-4">

            <!--Card-->
            <div class="card">

              <!--Card image-->
              <div class="view overlay">
                <img src="./img/产品.jpg" class="card-img-top" alt="">
                <a href="#">
                  <div class="mask rgba-white-slight"></div>
                </a>
              </div>

              <!--Card content-->
              <div class="card-body">
                <!--Title-->
                <h4 class="card-title">相关产品</h4>
                <!--Text-->
                <p class="card-text">针对排队系统，我们设计了实时排队人数统计装置、系统操作界面等相关产品</p>
                <a href="#" class="btn btn-indigo">了解更多</a>
              </div>

            </div>
            <!--/.Card-->

          </div>
          <!--Grid column-->

        </div>
        <!--Grid row-->
      </div>
      <!--Main container-->
    </main>

```



**至于footer就没什么特别说明的，但是其格式也是放在container中根据列来设置即可**





