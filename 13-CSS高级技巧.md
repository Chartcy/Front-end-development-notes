# 1.元素的显示与隐藏

- 目的

  让一个元素在页面中消失，但是不在文档源码中删除

- 场景

  是网站广告，当我们点击类似关闭不健康，但是我们重新刷新页面，会重新出现！

## 1.1 display显示（重点）

- display设置或检查对象是否及如何显示

  ```css
  display: none; 隐藏对象
  display: block; 除了转换为块级元素外，同时还有显示元素的意思。
  ```

- 特点：隐藏之后，不再保留位置。

## 1.2 visibility 可见性（了解）

- 设置或检索是否显示对象

  ```css
  visibility: visible; 对象可见
  visibility: hidden; 对象隐藏
  ```

- 特点：对象隐藏之后，继续保留原有的位置。（停职滞留）

## 1.3 overflow 溢出（重点）

- 检索或设置当对象的内容超过其指定高度及宽度时如何管理内容。

| 属性值  | 描述                                     |
| ------- | ---------------------------------------- |
| visible | 不剪切内容也不添加滚动条                 |
| hidden  | 不显示超过对象尺寸的内容，超出部分隐藏掉 |
| scroll  | 不管超出内容，总是显示滚动条             |
| auto    | 超出自动显示滚动条，不超出不显示         |

# 2.CSS用户界面样式

- 所谓界面样式，就是更改一些用户操作样式，以便提高更好的用户样式。
  - 更改用户的鼠标样式（滚动条因为兼容性非常差，我们不研究）
  - 表单轮廓等
  - 防止表单拖拽

## 2.1 鼠标样式cursor

设置或检索在对象上移动的鼠标指针采用何种系统预定义的光标形状。

| 属性值      | 描述      |
| ----------- | --------- |
| default     | 小白 默认 |
| pointer     | 小手      |
| move        | 移动      |
| text        | 文本      |
| not-allowed | 禁止      |

```css
<ul>
<li style="cursor: default;">默认的</li>
</ul>
```

## 2.2 轮廓线 outline

是绘制于元素周围的一条线，位于边框边缘的外围，可起到突出元素的作用。

```css
outline: outline-color || outline-style || outline-width
```

但是我们都不关系可以设置多少，我们平时都是去掉的。

最直接的写法是： outline: 0;  或者 outline: none;

```css
<input tupe="text" style="outline: 0;"/>
```

## 2.3  防止拖拽文本域 resize

```css
<textarea style="resize: none;"></textarea>
```

## 2.4 用户界面总结

省略

# 3. vertical-align 垂直对齐

- 有宽度的块级元素居中对齐，是margin: 0 auto;
- 让文字居中对齐 text-align: center;

vertical-align 垂直对齐，它只针对**行内元素或行内块元素**

```css
vertical-align: baseline | top |middle | bottom
```

设置或检索对象内容的垂直对齐方式。

- 注意：

  vertical-align  不影响块级元素中的内容，它只针对于行内元素或行内块元素。

  特别是行内块元素，**通常用来控制图片/表单与文字的对齐**

- baseline 基线对齐 默认的是文字和图片的基线对齐
- middle 垂直居中 默认的是文字和图片的中心线对齐
- top 顶部对齐 默认的是文字和图片的顶线对齐

## 3.1 图片、表单和文字对齐

默认文字与图片基线（图片底边 汉字最下面的那条线）对齐

## 3.2 去除图片地测空白缝隙

父盒子由图片撑开，图片下面会多出缝隙。

因为默认的是基线对齐，所以底侧有空白缝隙。

- 原因：

  图片或表单等行内块元素，他们的底线会和父级盒子的基线对齐，就是图片底侧会有一个空白缝隙。

- 解决方法：

  - 给vertical-align: middle | top 等，让图片不要和基线对齐。

  - 给img添加 display: block;转换为块级元素。

    块级元素 vertical-align无效，就不会有基线对齐的问题了。

# 4 溢出的文字省略号显示

## 4.1 white-space

设置或检索对象内文本显示方式。通常我们使用强制一行显示内容。

```css
white-space: normal;默认处理方式

white-space: nowrap;强制在同一行内显示所有文本，直到文本结束或遭遇br标签对象才换行。
```

## 4.2 text-overflow 文字溢出

设置或检索是否使用一个省略标记(...)标示对象文本的溢出

```css
text-overflow: clip; 不显示省略标记(...)，而是简单的被切

text-overflow: ellipsis; 当对象文本溢出时显示省略标记(...)
```

- 注意：

  一定要首先强制一行显示，再次和overflow属性 搭配使用

## 4.3 总结三部曲

```css
/*1.先强制一行内显示文本*/
	white-space: nowrap;
/*2.超出部分隐藏*/
	overflow: hidden;
/*3.文字用省略号替代超出部分*/
	text-overflow: ellipsis;
```

# 5. CSS精灵技术（sprite）重点

## 5.1 为什么需要精灵技术

为了有效地减少服务器接收和发送请求的次数，提高页面的加载速度。

## 5.2 精灵技术讲解

CSS精灵骑士是将网页中的一些背景图像整合到一张大图中（精灵图），然鹅，各个网页元素通常只需要精灵图中不同位置的某个小图，要想精确定位到精灵图中的某个小图。

这样，当用户访问该页面时，只需向服务器发送一次请求，网页中的背景图像即可全部显示出来。

我们需要使用CSS的

- background-image
- background-repeat
- background-position 属性进行背景定位
- 其中最关键的是使用background-position属性精确地定位

## 5.3 精灵技术使用的核心总结

首先我们知道，CSS精灵技术主要针对于背景图片，插入的图片img是不需要这个技术的。

1. 精确测量，每个小背景图片的大小和位置。
2. 给盒子指定小背景图片时，背景定位基本都是 负值。

## 5.4 制作精灵图

一般是网页美工做。

保存为.png格式，透明背景会更好。

# 6. 滑动门

为了使各种特殊形状的背景能够自适应元素中文本内容的多少，出现了CSS滑动门技术。它从新的角度构建页面，使各种特殊形状的背景能够自由拉伸滑动，以适应元素内部的文本内容，可用性更强，最常见于各种导航栏的滑动门。

http://weiixn.qq.com/

**核心技术**

核心技术就是利用CSS精灵（主要是背景位置）和盒子padding撑开宽度，以便能适应不同字数的导航栏。

一般的经典布局时这样的：

1.a 是设置左侧背景 （左门）。

2.span 是设置右侧背景 （右门）。

3.因为整个导航栏都是链接，所以a要包含span。

4.因为我们是滑动门，左右推拉 跟文字内容多少有关系，此时需要用文字撑开盒子，就要用到行内块。

```HTML
<li>
	<a href="#">
		<span>导航栏内容</span>
	</a>
<li>
```

CSS样式

```css
* {
    padding: 0;
    margin: 0;
}
body {
    background: url(images/wx.png) repeat-x;
}
.father {
    padding-top: 20px;
}
li {
    padding-left: 10px;
    height: 33px;
    float: left;
    line-height: 33px;
    margin: 0 10px;
    background: url(./images/to.png) no-repeat left;
}
a {
    padding-right: 10px;
    height: 33px;
    display: inline-block;
    color: #fff;
    background: url(./images/to.png) no-repeat right;
    text-decoration: none;
}
li:hover,
li:hover a {
    background-image: url(./images/ao.png);
}
```

总结：

1. a设置背景左侧，padding撑开合适宽度。
2. span设置背景右侧，padding撑开合适宽度 剩下的由文字继续撑开宽度
3. 之所以a包含span是因为整个导航栏都是可以点击的。

