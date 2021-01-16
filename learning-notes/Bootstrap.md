# Bootstrap

## 响应式所具有的特点

1. 网页的宽度自动调整

2. 尽量少用绝对宽度
3. 字体要使用rem、em作为单位
4. 布局要使用浮动、弹性布局
5. 媒体查询（@media） ：根据一个或多个基于设备类型、具体特点和环境来应用样式

@规则

@chartset	定义编码

@import 	 引入样式

@font-face	自定义字体

@keyframes	animation 里的关键字

@media		媒体查询



rem：相对于html元素的font-size大小

em：相对于本身的font-size大小，font-sez是属性可以继承的

vw/vh：相对于视口（viewport），会把视口分成100份

vmax：取视口宽高中最大的一边分为100份

vmin：取视口宽高中最小的一边分为100份



响应式开发：先移动端再PC端，移动端先以iphone6为原型开发，再兼容其他设备

### 1.媒体查询（@media）

1**、媒体类型**

	1. all	所有设备
	2. print   打印机设备
	3. screen  彩色的电脑屏幕
	4. 听觉设备（针对有实力障碍的人士，可以把页面的内容一语音的方式呈现的设备）
注意：tty、tv、projection、handheld、braille、embossed、aural等几种类型在媒体查询4中已废弃

**2、媒体特性**

 - width  宽度
   	- min-width	最小宽度，宽度只能比这个大
      	- max-width    最大宽度，宽度只能比这个小
- height  高度
  - min-height	最小高度，高度只能比这个大
  - max-height    最大高度，高度只能比这个小
- orientation   方向
  - landscope	横屏（宽度大于高度）
  - portrait        竖屏（高度大于宽度）
- aspect-ratio  宽高比
- -webkit-device-pixel-ratio   像素比（webkit内核的私有属性）

**3、媒体运算符**:用来做条件判断

	- and	合并多个媒体类型（并且）
	- ,     匹配某个媒体类型（或者）
	- not   对媒体查询结果取反
	- only  仅在媒体查询匹配成功后应用样式（防范老旧浏览器）



**引入媒体查询的方式**

```html
//外联引入：满足媒体查询条件，Css文件才生效
<link rel="stylesheet" media="screen and (max-width:375px)" href="index.css">
//import导入
<style>
	@import 'index.css' screen and (max-width:375px)
</style>
//内联引入，直接在css文件里写
```

注意点：媒体查询没有权重，所以一般写在最后

### 2. 栅格系统

```javascript
    <!-- 100&%的宽度 -->
    <div class="container-fluid"></div>
    <!-- 具体的数值 1140px -->
    <div class="container"></div>
```

#### 尺寸

**col-xl-***：XL表示为超大屏，屏幕宽度>=1200，容器(container)的宽度固定为1140px，一行可以设置12个列，尺寸 < 1200的时候，一行只能设置一列

**col-lg-***：lg表示为大屏，屏幕宽度 >= 992，容器(container)的宽度固定为960px，一行可以设置12列，尺寸 < 992的时候，一行只能设置一列

**col-md-***：xl为中等屏，屏幕宽度 >=768，容器(container)的宽度固定为720px，一行可以设置12列，尺寸 < 768的时候，一行只能设置一列

**col-sm***：xl为小屏，屏幕宽度 >=576，容器(container)的宽度固定为540px，一行可以设置12列，尺寸 < 576的时候，一行只能设置一列

**col-***：xl为超小屏，屏幕宽度 < 576，容器(container)的宽度为auto，一行永远可以设置12列。



col一行永远都可以设置12列跟它的特性有关，**col-*永远都能均分列**

```javascript
<!-- 等宽列 -->
<div class="row mt-5">
    <div class="col">均分列</div>
    <div class="col">均分列</div>
    <div class="col">均分列</div>
</div>
```

上面的就表示一行分12列，每个占4列，无论宽度如何缩减，三者比例永远都是不变的。



#### 等宽列

如果想设置**多行等宽列**，在希望断开的地方添加一个**.w-100的class,**能够让后面的列换行(.w-100)的意思是设置一个宽度为100%的块。然后我们再通过设置高度为0达到换行的效果



#### 内容撑开高度

如果想设置由**内容撑开宽度**，可以使用，使用**.col-{breakpoint}-autod**的类，breakpont表示在什么屏幕下，（Xl,lg,md,sm）



#### 对齐

##### 垂直对齐

- 行的对齐方式
  - align-items-start  顶对齐(默认)
  - align-items-center 中间对齐
  - align-items-end 低对齐

- 列的单独对齐方式

  - align-self-start  顶对齐(默认)
  - align-self-center  中间对齐
  -  align-self-end   底部对齐

  ​                    

##### 水平对齐

- justify-content-start  左对齐
- justfy-content-center   中间对齐
- justify-content-end    右对齐
- justify-content-around  分散居中对齐（每个元素的两侧的间距都想相等的）
- justify-content-between  左右两端对齐（元素之间的间距是自动平方的）



#### 列排序

>  使用.order-{breakpoint}-* order默认为0，越大越靠后
>
>   3.x的版本使用的 是-col-{breakpoint}-push-*,col-{breakpoint}-pull-*来排序



#### 列偏移

> 使用 offset-{breakpoint}-*

注意点：

	1. 前面方块的偏移会导致后边的也跟着偏移，否则第二个会跑到第一个前面
 	2. 偏移是相对于当前所在的位置开始偏移的



#### 间距

> 使用margin工具可以在列之间产生间距

​      mr-{breakpoint}-auto  使右侧的列远离到最右边   

​      ml-{breakpoint}-auto  使左侧的列远离到最左边 



#### 嵌套

> 每一个列里面可以继续换行，拿嵌套里面的元素就会以父元素的宽度作为基准，再分12列 

以上所有案例都在栅格系统/栅格系统2中



## 3. 重置，排版，代码





#### 重置

> 所谓重置，就是替换掉默认样式，再用上新的样式

**根节点(html)的重置**

1. 默认在根节点（html）下有一些预设的变量，分别是一些颜色颜色和5个响应层，Css使用变量的方式是

var(变量名)

2. 把伪元素（::after ，::before）变成了怪异盒模型（box-sizing:border-box）

**body的重置**

1. 字体预设为1rem
2. 文字默认左对齐
3. 外边距默认为0；
4. 字体粗细为400；
5. 字体颜色为#212529（浅黑色）



**标题（h1...）和段落（p）**

1. 标题和段落干掉了margin-top，统一添加margin-bottom，标题为0.5rem,段落为1rem，目的是为了解决混合使用这两种导致margin重叠问题

2. **h1**：2.5rem、**h2**：2rem、**h3**：1.75rem、**h4**：1.5rem、**h5**：1.25rem、**h6**：1rem、**p**:1rem



**列表的重置**（dl、dt、dd）

1. dt字体粗细变为700

2. dd的margin-left变为0，margin-bottom变为0.5rem



**Pre的重置**

> pre 元素可定义预格式化的文本。被包围在 pre 元素中的文本通常会保留空格和换行符。而文本也会呈现为等宽字体。
>
> <pre> 标签的一个常见应用就是用来表示计算机的源代码。

	1. 字体大小重置为87.5%
 	2. magin-top重置为0、margin-bottom重置为1rem;
 	3. 字体颜色重置为#212529（浅黑色）



**表格的重置**（table、caption、tr、td）

1. 将caption(表格的标题)放到了表格的下面



**表单的重置**

1. label的display变为inline-block
2. input标签的overflow变为visible，字体和行高和字体类型都变为继承（inherit）父级别
3. 多文本框textarea只能改变高度了，不能同时改变高度和宽度



#### 排版

**标题**

1. 新增了4个超大标题，用class="display-1"...class="display-4"

2. 新增了一个小标题<small></small>，字体大小为80%
3. initialism类可以让字体变得小一点



**引言**（突出段落）

1. 新增了引言类（lead）,用于突出文章重要段落文字

```
<p class="lead">我们的宗旨是为人民服务</p>
```



**内联文本**

<mark>	文字添加黄色背景色用于重点标记

<del>	文字中间添加划线，表示需要删除

<ins>	文字添加下划线，表示新增的

<strong>	加粗

<em>	倾斜文本

<small>	文本变小

**bootstrap也对<small>和<mark>添加了类，也可用类实现**



**缩写**

```html
<abbr title="attrbute" class="initialism">attr</abbr>	//光标放在字上会显示浮层的内容（attrbute）,(initialism)表示可以让字体变得小一点
```



**引用跟署名**

```html
<blockquote class="blockquote">
    <p>时间就像海绵里的水，只要愿意挤，总还是有的</p>
    <footer class="blockquote-footer">来自鲁迅</footer>
</blockquote>
```

添加了blockquote类，会放大字体

添加了blockquote-footer，会在字体前面加一段横线，并把字体颜色变为浅灰



**对齐**

添加了左对齐，居中对齐，右对齐，三个对齐方式的类，分别为

1. text-left
2. text-center
3. text-right





**以上所有的都跟文本相关**



**列表**（ul li）

1. 新增list-unstyled类用于去除子列表的小圆点，但无法取出孙子列表的小圆点
2. 新增list-inline和list-inline-item类，父子级配合适用能将列表横排，在3.x版本中子类不需要在Li添加

```html
<ul class="list-unstyled">
    <li>小红薯</li>
    <li>
        <ul  class="list-unstyled">
            <li>小黄塑</li>
        </ul>
    </li>
</ul>

<ul class="list-inline">
    <li class="list-inline-item">大哥</li>
    <li class="list-inline-item">二哥</li>
    <li class="list-inline-item">小哥</li>
</ul>
```



**描述列表**（dl,dt,dd）

新增了文字省略类 **text-truncate**，超出不换行，而是省略，注意在3.x版本使用的是text-overflow



#### 代码

**行内代码**

新增<code>标签，可用于标红标签



**大段引用**

新增pre-scrollable类：	和code标签配合使用会在高度超出长度340px后出现滚动条



**按钮**	

新增<kbd>标签，将文字变成按钮

```html	
<p>要保存的化，请按<kbd>ctrl+s</kbd></p>
```

![1582861578557](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1582861578557.png)

##  4. 图片、表格、图文

#### 图片

**1. 响应式图片**

添加 一个类 class="img-fluid"，根据的就是5**个响应层实现的**，如果要实现一个响应式图片也很简单，用max-width:100%和height:auto即可

**2.缩略图**

class= "img-thunbnail"，缩略图也是响应式图片，也有圆角的特点

**3.圆角图片**

添加类class="rounded"	圆角图片不是响应式图片，需要自己设置，圆角度为0.25rem



**图片对齐方式**

父级：父级使用文本的对齐方式——text-left，text-center，text-right，让子级达到对齐的效果

子级：子级使用class="float-left"或class="float-right"的方式

自己居中：图片默认是inline-block，需要变成block再margin:0 auto，对应的默认类是**d-block**，和

"mx-auto"



##### Picture标签<picture>

> 这个标签可以存放很多图片资源，可以实现高清屏的用户只加载高清的图片，普通屏的用户只加载普通的图片

```html
<picture>
    <source media="(min-width:1200px)" srcset="images/xxx,jpg">
    <source media="(min-width:992px)" srcset="images/xxx,jpg">
    <source media="(min-width:768px)" srcset="images/xxx,jpg">
    <source media="(min-width:576px)" srcset="images/xxx,jpg">
    <img src="xxx.jpg">	/*当尺寸小于576px时使用该图片*/
</picture>
//对于不同尺寸的屏幕，加载不同的图片
```



#### 表格

**表格**、表列 工具类(class)：table-info、table-primary、table-success、table-dark、table-light...

**表头**工具类(class)：thead-light、thead-dark



**隔行换色类**

隔行换色类（class）：table-striped。配合table-info等可以做出各种颜色的隔行换色



**带边框类**

table-bordered



**去除边框类**（默认样式下底部有横线）

table-borderless



**高亮类**

table-hover



**更小的表格**

table-sm



**响应式的表格**

在表格的前面套一个div，里面的类写table-responsive(-sm|md|lg|xl)





以上没有特别指明，类都是针对表格的，并且都可以添加不同的颜色类





#### 图文区

> 展示图片及说明

```html
<figure class="figure">
    <img src="./img/banner1@2x.png" class="img-fluid figure-img">
    <figcaption class="figure-caption text-center">一叶知秋</figcaption>
</figure>
```



## 5. 边框、颜色、显示、嵌入

#### 边框

**添加边框类**

```html
<div class="row mt-5 justify-content-around" >
    <span class="border"></span>
    <span class="border-top"></span>
    <span class="border-left"></span>
    <span class="border-right"></span>
    <span class="border-bottom"></span>
</div>
```

删除边框类

```html
<div class="row mt-5 justify-content-around" >
    <span class="border border-0"></span>
    <span class="border-top border-top-0"></span>
    <span class="border-left border-left-0"></span>
    <span class="border-right border-right-0"></span>
    <span class="border-bottom border-bottm-0"></span>
</div>
```

边框颜色类

```html
border-primary border-info....
```

边框圆角类

```html
rounded —— rounded-top	rounded-bottom	rounede-left	rounede-right	//边框圆角
		   rounded-circle	圆形	rounded-pill	胶囊状
```



#### 颜色

>  颜色在哪个工具需要的地方都可以用到，区别是颜色的前缀不同

字体颜色、和标签颜色

.text-primary		蓝色

.text-secondary	灰色

.text-success		 绿色

.text-danger		  红色

.text-warning		 黄色

.text-info				 浅蓝色

.text-light				白色

.text-dark				黑色

.text-body				灰色

.text-muted			 灰色

.text-white				白色

.text-black-50			黑色（0.5透明度）标签没有该颜色

.text-white-50			白色（0.5透明度）标签没有该颜色



背景颜色

.bg-primary				蓝色

.bg-secondary			灰色

.bg-success				 绿色

.bg-danger				  红色

.bg-warning				黄色

.bg-info						浅蓝色

.bg-light						浅白色

.bg-dark						黑色

.bg-white						白色

.bg-transparent			透明色



#### 显示

> 把元素显示成各种类型，3.x版本中只有三种、block、inline、inline-block，并且在3.x版本中
>
> 显示 为vbisible-*-block
>
> 隐藏为 .hidden-*
>
> 打印为.visible-print-block

```html
d-block		//块级元素
d-inline	//行内元素
d-inline-block	//行内块级元素
d-flex			//flex布局
d-none			
d-inline-flex	//行内flex布局
...
```



显示隐藏元素

![1582878992672](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1582878992672.png)



仅在打印的时候显示类

d-none ,d-print-block



#### 嵌入

> 通过创建可在任何设备上缩放的内在比率，根据父对象的宽度创建自适应视频或幻灯片嵌入。 规则被直接施加到`iframe`，`embed`，`video`，和`object`元件 

让视频响应式的类

 .embed-responsive 

改变视频的分辨率,默认情况下是21:9

```html
embed-responsive-16by9	//屏幕分辨率修改为16:9
embed-responsive-4by3	//屏幕分辨率修改为4:3
embed-responsive-1by1	//屏幕分辨率修改为1:1
```



## 6.flex

>  .row类本身就是默认flex容器



**子元素的排列方向**

- flex-row
- flex-row-reverse
- flex-column
- flex-column-reverse

响应式的排列

flex-{breakpoint}-row/column/row-reverse/column-reverse



**元素的对齐方式**

1. 主轴的对齐方式-水平对齐

   1. justify-content-start
   2. justify-ceontent-end
   3. justify-content-center
   4. justify-content-between
   5. justify-content-around

   响应式对齐方式：justify-content-{breakpoint}-between

2. 交叉轴（纵轴）的对齐方式-垂直对齐

   1. align-items-start	顶对齐
   2. align-items-end      低对齐
   3. align-items-center  中间对齐
   4. align-items-baseline 基线对齐
   5. align-item-strech 如果子元素没有高度或高度为auto,子容器将占满容器的高度

   响应式对齐方式：align-items-{breakpoint}-start



**元素自身的对齐方式**

1. align-self-start
2. align-self-end
3. align-self-center
4. align-self-baseline
5. align-self-strech

响应式：align-self-{breakpoint}-start



**填充**

> 瓜分剩余空间

flex-fill

响应式：flex-{breakpoint}-fill



**伸缩值（子元素添加）**

flex-grow：扩展比例，默认数字0表示不扩展，数字1 表示扩展，只有这两个数字

flex-shrink：收缩比例，默认数字1表示收缩，数字1表示不收缩，只有这两个数值

响应式：flex-{}



**自动间距**

水平方向

​	mr-auto： 向右推 

​	ml-auto

垂直方向

​	mb-auto	向下推 其他项目

​	mt-auto	向上推 其他项目

没有响应式



**wrap**

> bootstrap默认换行

flex-wrap

flex-wrap-reverse

flex-nowrap

flex-nowrap-reverse

响应式：flex-{breakpoint}-wrap



**排序（子项目添加）**

默认为0

order-{数字}

响应式排序：order-{breakpoint}-{}



**多行对齐（容器添加）**

> 仅在多行的时候才生效

align-content-start

align-content-end-

align-content-center

align-content-between

align-content-around

align-content-stretch（默认）

响应式：align-content-{breakpoint}-start



## 7.剩余工具集合

#### 浮动

>  浮动在flex容器中无效，还有clean和vertical-align

- float-left
- float-right
- float-none

在3.x版本中，左浮动是puil-left，右浮动是puil-right

响应式：float-{breakpoint}-left



清除浮动——cleafix



#### 关闭图标

```html
<div class="row">
    <button type="button" class="close">
        <span>&times;</span>
    </button>
</div>
```

#### 图形替换

> 便于seo，隐藏字，让用户看到图片，爬虫看到文本

text-hide



#### 内容溢出

- overflow-auto
- overflow-hidden



#### 定位（类）

- position-static	
- position-relative  相对定位
- position-position  绝对定位
- position-fixed  固定定位
- fixed-top  固定在顶部
- fixed-bottom 固定在底部
- position-sticky  黏性定位  （走到即将滚动离开屏幕时，停住）需要放在body下面的第一层
-  sticky-top 黏性置顶（兼容性很差）



#### 屏幕阅读器

> 针对特殊人群，把字读出来



#### 阴影

- shadow-none	没有阴影
- shadow-sm小阴影
- shadow正常阴影
- shadow-lg   大阴影



#### 尺寸

**宽度**

- w-25	占25%的宽度
- w-50   占25%的宽度
- w-75   占父级100%的宽度
- w-100   占父级100%的宽度

**高度**

- h-25	占25%的高度
- h-50   占25%的高度
- h-75   占父级100%的高度
- h-100   占父级100%的高度

宽度的最大值

mw-100	占父级的全部宽度

高度的最大值

mh-100：占父级的全部高度



#### 间距

**属性**

- `m` -对于设置的类 `margin`
- `p` -对于设置的类 `padding`

**边**

- `t`-对于设置`margin-top`或`padding-top`
- `b`-对于设置`margin-bottom`或`padding-bottom`
- `l`-对于设置`margin-left`或`padding-left`
- `r`-对于设置`margin-right`或`padding-right`
- `x`-对于同时设置`*-left`和`*-right`(x轴)
- `y`-对于同时设置`*-top`和`*-bottom`（y轴）
- 空白-用于在元素的所有4侧设置a `margin`或`padding`4的类

**大小**

- `0`-对于消除`margin`或`padding`通过将其设置为的类`0`
- `1`-0.25rem
- `2`-0.5rem
- `3`-1rem
- `4`-1.5rem
- `5`-3rem
- `auto`-对于将设为`margin`自动的类

3.x版本中是是用.center-block

响应式：{属性}{边}-{breakpoint}-{尺寸}



#### 文本（类）

- text-justify	文本两端对齐
- text-center   文本居中
- text-left  文本左对齐
- text-right  文本右对齐

响应式：text-{breakpoint}-center



**换行和溢出处理**

text-wrap：溢出换行

text-nowrap：溢出不换行

text-truncate 溢出换行 （ **但必须是 `display: inline-block` 或 `display: block` 类型。** ）



**文本转换**

- text-lowercase	转为小写的文本
- text-uppercase   转为大写的文本。
- text-capitalize   转为首字母大写的文本。



**字体粗细**

- font-weight-bold	加粗
- font-weight-bolder   
- font-weight-normal   正常字体
- font-weight-light    细字体
- font-weight-lighter  更细字体
- font-italic   倾斜字体



**等宽字体**

- text-monospace 	等宽字体



#### 垂直对齐

>（类似vertical-align）
>
>改变inline、inline-block、inline-table、和table元素的垂直对齐

- align-baseline	基线对齐
- align-top   顶部
- align-middle  中间
- align-bottom   底部
- align-text-top   文字顶部
- align-text-bottom   文字底部



#### 可见性（visible）

> 和display的区别的消失后依旧占据空间

- visible	可以看见

- invisible   看不见，位置依旧存在

  

## 组件

#### 1.警告框、徽章、面包屑导航、按钮、按钮组



#### 警告框(alert)



**警告框 和样式类**

class = "alert"	这个类主要是做了一些定位和调整，还有一些圆角

```css
.alert {
    position: relative;
    padding: .75rem 1.25rem;
    margin-bottom: 1rem;
    border: 1px solid transparent;
    border-radius: .25rem;
}
```

样式类

- alert-primary	蓝色
- alert-secondary   灰色
- alert-success   绿色
- alert-danger   红色
- alert-warning   黄色
- alert-info   浅蓝色
- alert-light   偏白色 
- arert-dark   浅黑色

警告框内还可以添加其他东西，比如**链接**、**标题**、**段落**和**分割符**，在默认情况下，这个子元素的颜色都会继承父元素的颜色，当然颜色也可以自己修改

链接类：

-  .alert-link：可在任何警报中快速提供匹配的彩色链接。 



**JavaScript行为**

方法

- $().alert() ： 使警报监听具有该`data-dismiss="alert"`属性的后代元素上的单击事件。 
-  $().alert('close') ： 通过从DOM中删除警报来关闭警报。如果元素上存在`.fade`和`.show`类，则警报将在消失之前淡出。 

```javascript
<div class="alert alert-warning alert-dismissible fade show">
    这是一个可以关闭的警告框，但是需要引入jq和bs
	<button class="close" data-dismiss="alert">&times;</button>
</div>
//data-dismiss会定位父级的alert类，然后执行JS操作去display

//原生
<div class="alert alert-danger fade show myAlert">
</div>
<button class="closeBtn">关闭警告框</button>
<script>
    $('.closeBtn').click(function(){
    $('.myAlert').alert('close')
})
</script>
```



事件

-  close.bs.alert ： `close`调用实例方法时，将立即触发此事件。 
-  closed.bs.alert ： 警报已关闭时将触发此事件（将等待CSS转换完成）。 



#### 徽章(badge)

.badge类重置样式如下

```css
.badge {
    display: inline-block;
    padding: .25em .4em;
    font-size: 75%;
    font-weight: 700;
    line-height: 1;
    text-align: center;
    white-space: nowrap;
    vertical-align: baseline;
    border-radius: .25rem;
    transition: color .15s ease-in-out,background-color .15s ease-in-	out,border-color .15s ease-in-out,box-shadow .15s ease-in-out;
}
```

样式类

- badge-primary	蓝色
- badge-secondary   灰色
- badge-success   绿色
- badge-danger   红色
- badge-warning   黄色
- badge-info   浅蓝色
- badge-light   浅白色
- badge-dark  浅黑色



**徽章的大小默认取自于父级的75%，看上面的重置类就知道了，当然也可以自定义大小**



**胶囊徽章**

badge-pill：添加该类即可



徽章也可以嵌套在**按钮**和**超链接**中

```html
 <!-- 超链接+徽章 -->
        <a href="" ><span class="badge badge-primary">有颜色的徽章</span></a>
<!-- 按钮+徽章 -->
<button class="btn btn-info">消息<span class="badge badge-danger">6</span></button>
```



#### 面包屑导航(breadcrumb)

> 指示当前页面在导航层次结构中的位置，该层次结构会通过CSS自动添加分隔符。 

```html
<nav aria-label="breadcrumb">
  <ol class="breadcrumb">
    <li class="breadcrumb-item"><a href="#">Home</a></li>
    <li class="breadcrumb-item active" aria-current="page">Library</li>
  </ol>
</nav>
```

![1582982507172](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1582982507172.png)

面包屑导航的特点就是在当前链接页面是不可点击，父级以上的是可点击的



#### 按钮（btn）

重置样式

```css
.btn {
    display: inline-block;
    font-weight: 400;
    color: #212529;
    text-align: center;
    vertical-align: middle;
    cursor: pointer;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    background-color: transparent;
    border: 1px solid transparent;
    padding: .375rem .75rem;
    font-size: 1rem;
    line-height: 1.5;
    border-radius: .25rem;
    transition: color .15s ease-in-out,background-color .15s ease-in-out,border-color .15s ease-in-out,box-shadow .15s ease-in-out;
}
```



样式类

- btn-primary	蓝色
- btn-secondary   灰色
- btn-success   绿色
- btn-danger   红色
- btn-warning   黄色
- btn-info   浅蓝色
- btn-light   浅白色
- btn-dark  浅黑色



其他类型的按钮：a标签、button标签、input-button类型标签、input-submit类型标签、input-reset标签



**外边框按钮**

btn-outline-颜色



**不同尺寸的按钮**

- btn-lg	
- btn-sm   小按钮



**按钮**

- btn-block



**按钮禁用与启用**

- disabled	
- active   启用（默认）

可以用到a标签、button标签   



**JS交互**

```html
<div class="row d-block mt-5">
    <button class="btn btn-primary active" data-toggle="button">点击切换状态		</button>
</div>
```



**选项卡**

```html
<div class="btn-ground btn-group-toggle" data-toggle="buttons">
    <label class="btn btn-secondary active">
        <input type="radio">Active
    </label>
    <label class="btn btn-secondary active">
        <input type="radio">Radio
    </label>
    <label class="btn btn-secondary active">
        <input type="radio">Radio
    </label>
</div>
```



**切换按钮的active状态**

 $().button('toggle') 



### 按钮组

> 把多个按钮组合在一起，形成一个按钮组

 btn-group重置样式

```css
.btn-group, .btn-group-vertical {
    position: relative;
    display: -ms-inline-flexbox;
    display: inline-flex;
    vertical-align: middle;
}
```

**按钮组**

```html
<div class="btn-group">
                <div class="btn btn-info">left</div>
                <div class="btn btn-info">center</div>
                <div class="btn btn-info">right</div>
            </div>
```



**工具列表**

```html

<div class="row btn-toolbar">
    <div class="btn-group mr-2">
        <div class="btn btn-info">1</div>
        <div class="btn btn-info">2</div>
        <div class="btn btn-info">3</div>
    </div>
    <div class="btn-group mr-2">
        <div class="btn btn-info">4</div>
        <div class="btn btn-info">5</div>
        <div class="btn btn-info">6</div>
    </div>
    <div class="btn-group">
        <div class="btn btn-info">7</div>
    </div>
</div>
```



**按钮与输入框结合**

```html
<div class="row btn-toobar mt-5">
    <div class="btn-group mr-2">
        <button class="btn btn-secondary">1</button>
        <button class="btn btn-secondary">2</button>
        <button class="btn btn-secondary">3</button>
        <button class="btn btn-secondary">4</button>
    </div>
    <div class="input-group">
        <div class="input-group-prepend">
            <div class="input-group-text">@</div>
        </div>
        <input type="text" class="form-control" placeholder="i am a iron man">
    </div>
</div>
```



**按钮组尺寸**

btn-group-lg	

btn-group-sm	小按钮组



**下拉菜单**

![1582988697087](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1582988697087.png)

```html
<!-- 下拉菜单 -->
<div class="row mt-5">
    <div class="btn-group">
        <button class="btn-danger">11111</button>
        <button class="btn-danger">2111</button>
    </div>
    <div class="btn-group">
        <button class="btn btn-secondary dropdown-toggle" data-toggle="dropdown"></button>
        <div class="dropdown-menu">
            <a href="#" class="dropdown-item">北京</a>
            <a href="#" class="dropdown-item">上海</a>
        </div>
    </div>
</div>

// dropdown-toggle表示的是下三角
```

需要引入poper.js



**垂直排列**



```html
<div class="row mt-5">
    <div class="btn-group-vertical">
        <button class="btn btn-success">北京</button>
        <button class="btn btn-success">上海</button>
        <button class="btn btn-success">广州</button>
    </div>
</div>
```



