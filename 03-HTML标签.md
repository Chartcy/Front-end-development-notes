# 1.HTML常用标签

## 1.1 排版标签

### 1) 标题标签h（熟记）

单词缩写：head

**标题标签语义：**作为标题使用，并且重要性依次递减

```html
<h1> 标题文本 </h1>
<h2> 标题文本 </h2>
<h3> 标题文本 </h3>
<h4> 标题文本 </h4>
<h5> 标题文本 </h5>
<h6> 标题文本 </h6>
```

### 2) 段落标签p（熟记）

单词缩写：paragraph

**作用语义：**把HTML文档分割成若干段落

```html
<p> 文本内容 </p>
```

### 3) 水平线标签hr（认识）

单词缩写：horizontal

```html
<hr/>是单标签
```

### 4) 换行标签br（熟记）

单词缩写：break

```html
<br/>
```

### 5) div 和 span标签（重点）

div span 是没有语义的    是我们网页布局主要的2个盒子

```html
<div>这是头部</div>    <span>今日价格</span>
```

他们都是两个盒子，用来装网页元素的，有区别。

- div标签 用来布局的，但是现在一行只能放一个div
- span标签 用来布局的，一行上可以放好多个span

### 排版标签总结

| 标签名        | 定义       | 说明                                  |
| ------------- | ---------- | ------------------------------------- |
| <hx></hx>     | 标题标签   | 作为标题使用，并且依据重要性递减      |
| <p></p>       | 段落标签   | 把HTML文档划分为若干个段落            |
| <hr/>         | 水平线标签 | 就是一条线                            |
| <br/>         | 换行标签   |                                       |
| <div></div>   | div标签    | 用来布局的，但是现在一行只能放一个div |
| <span></span> | span标签   | 用来布局的，一行上可以放好多个span    |

## 1.2 文本格式化标签

|           标签           | 显示效果                     |
| :----------------------: | ---------------------------- |
| <b></b><strong></strong> | 粗体（XHTML推荐使用strong）  |
|    <i></i>和<em></em>    | 斜体（XHTML推荐使用em）      |
|   <s></s>和<del></del>   | 加删除线（XHTML推荐使用del） |
|   <u></u>和<ins></ins>   | 加下划线（XHTML不赞成使用u） |

**区别：**

b 只是加粗        strong除了加粗还有强调的意思，语义更强烈。

剩下的同理。。。

## 1.3 标签属性

```html
<标签名 属性1="属性值1" 属性2="属性值2" ...>内容</标签名>
```

## 1.4 图像标签img（重点）

 **<img/>标记属性**

| 属性   | 属性值                         | 描述                     |
| ------ | ------------------------------ | ------------------------ |
| src    | URL                            | 图像的路径               |
| alt    | 文本                           | 图像不能显示时的替换文字 |
| title  | 文本                           | 鼠标悬停时的内容         |
| width  | 像素（XHTML不支持%页面百分比） | 设置图像的宽度           |
| height | 像素（XHTML不支持%页面百分比） | 设置图像的高度           |
| border | 数字                           | 设置图像边框的宽度       |

## 1.5 链接标签（重点）

单词缩写：anchor

```html
<a href="跳转目标" target="目标窗口的弹出方式">文本或图像</a>
```

| 属性   | 作用                                                         |
| ------ | ------------------------------------------------------------ |
| href   | 用作指定链接目标的url地址，（必须属性）当为标签应用href属性时，它就具有了超链接的功能 |
| target | 用于指定链接页面的打开方式，其取值有self和blank两种，其中self为默认值，blank为在新窗口中打开方式 |

**注意：**

1. 外部链接 需要添加 http:// www.baidu.com
2. 内部链接 直接链接内部页面名称即可 比如<a href=“index.html"> 首页 </a>
3. 没有确切的连接目标时，通常将href定义为空链接"#"(即href="#")

## 1.6 注释标签

```html
<!-- 注释语句 -->    快捷键是   Ctrl+/ 或者 Ctrl+shift+/
```

# 2.路径

## 相对路径

| 路径分类   | 符号  | 说明                                                         |
| ---------- | ----- | ------------------------------------------------------------ |
| 同一级路径 |       | 只需输入图像文件的名称即可，如<img src="baidu.gif"/>。       |
| 下一级路径 | "/"   | 图像文件位于HTML文件同级文件夹下（例如文件夹名称为：images）如<img src="images/baidu.gif">。 |
| 上一级路径 | "../" | 在文件名之前加"../"，如果是上两级则"../../"，以此类推，如<img src="../baidu.gif"/>。 |

## 绝对路径

绝对路径以Web站点根目录为参考基础的目录路径 。之所以称为绝对，意指当所有网页引用同一个文件时，所使用的路径都是一样的。

"D:\web\img\logo.gif"，或完整的网络地址，如"http://www.itcast.cn/images/logo.gif"。

**注意：**

绝对路径使用较少，理解即可。但要注意，它的写法 特别是符号 \ 并不是相对路径的 /  

# 3.拓展阅读

## 3.1 锚点定位（难点）

通过创建锚点链接，用户能够快速定位到目标内容。

创建锚点链接分为两步：

```html
1.使用相应的id名标注跳转目标的位置。（找目标）
  <h3 id="two">第二集</h3>

2.使用 <a href="#id名">链接文本</a> 创建链接文本（被点击的） （拉关系）
  <a href="#two">被点击的元素</a>
```

## 3.2 base标签

1. base可以**设置整体链接的打开状态**
2. base写到 <head></head>之间
3. 把所有的链接 都默认添加 target="__blank"

## 3.3 预格式化文本pre标签

<pre> 标签可定义预格式化的文本。

被包围在<pre>标签 元素中的文本通常会保留空格和换行符。而文本也会呈现为等宽字体。

```html
<pre>
	此例演示如何使用 pre 标签
	
	对空行和 空格 
	
	进行控制
	
</pre>
```

## 3.4 特殊字符（理解）

**总结：**

1. 以运算符&开头，以分号运算符;结尾。
2. 不是标签，而是符号。
3. HTML中不能使用小于号"<"和大于号">"特殊字符，浏览器会将他们作为标签解析，若要正确显示，在HTML源代码中要使用字符实体。

**团队约定**

推荐

```html
<a href="#">more &gt;&gt;</a>
```

不推荐

```html
<a href="#">more >> </a>
```

