### display

**没有布局**
<div style='display: none'>
如果你只想把所有内容都塞进一栏里，那么不用设置任何布局也是OK的。然而，如果用户把浏览器窗口调整的很大，这时阅读网页会非常难受：读完每一行之后，你的视觉焦点要从右到左移动一大段距离。试着调整下浏览器窗口大小你就明白我的意思了！
</div>

`display`是CSS中最重要的控制布局的属性，每一个元素都有一个默认的display之，这与元素类型有关。对于大多数元素它们的默认值通常是`block`或`inline`,分别为块级元素和行内元素

**block**

<div style='display: block; border:1px solid #6ac5ab'>
`div`是一个标准的块级元素，一个块级元素会新开始一行，并且尽可能撑满容器，其他常用的块级元素包括p、form和HTML5中的新元素：header、footer、section等等。
</div>

**inline**

`span`是一个标准的行内元素，一个行内元素可以在段落中<span>像这样</span>包裹一些文字而不会打乱段落的布局。`a`元素是最常用的行内元素，可以被用作链接

**none**

另一个常用的display值是`none`。一些特殊元素的默认值是它。如`script`。`display:none`通常会被JavaScript用来在不删除元素的情况下隐藏或显示元素。它和`visibility`属性不一样。把`display`设置成`none`元素不会占据它本来应该显示的空间，但是设置成`visibility: hidden;`还会占据空间。

**其他**

`inline-block`和`flex`

每一个元素都有一个默认的display类型。你可以随时随地重写它。例如把`li`元素修改为inline，制作成水平菜单

-------
```
#main {
  width: 600x;
  margin: 0 auto;
}

<div id="main">
  设置块级元素的with可以防止它从左到右撑满整个容器。然后你就可以设置左右外边距为auto使其水平居中。元素会占据你所指定的宽度，然后剩余的宽度会一分为二成为左右外边距
  唯一的问题是，当浏览器窗口比元素的宽度还要窄时，浏览器会显示一个水平滚动条来容纳页面，可以再改进一下这个方案
</div>
```
```
#main {
  max-width: 600x;
  margin: 0 auto;
}

<div id="main">
在这种情况下使用max-width代替width可以使浏览器更好地处理小窗口的情况。这点在移动设备上显得尤为重要。所有主流浏览器包括IE7+都支持
</div>
```

**盒模型**

在我们讨论宽度的时候，我们应该讲下与它相关的另外一个重点知识：盒模型。当你设置了元素的宽度，实际展现的元素却超出你的设置：这是因为元素的边框和内边距会撑开元素。看下面的例子，两个相同宽度的元素显示的实际宽度却不一样。

```
.simple {
  width: 500px;
  margin: 20px auto;
}

.fancy {
  width: 500px;
  margin: 20px auto;
  padding: 50px;
  border-width: 10px;
}
```
以前有一个代代相传的解决方案是通过数学计算。CSS开发者需要用比他们实际想要的宽度小一点的宽度，需要减去内边距和边框的宽度。值得庆幸地是你不需要再这么做了...

**box-sizing**

当你设置一个元素为`box-sizing: border-box;`时，此元素的内边距和边框不会增加它的宽度
```
.simple {
  width: 500px;
  margin: 20px auto;
  -webkit-box-sizing: border-box;
     -moz-box-sizing: border-box;
          box-sizing: border-box;
}

.fancy {
  width: 500px;
  margin: 20px auto;
  padding: 50px;
  border: solid blue 10x;
  -webkit-box-sizing: border-box;
     -moz-box-sizing: border-box;
          box-sizing: border-box;
}
```
如果希望页面上打所有元素都有如此表现，可以把以下代码放在它们的页面上
```
* {
  -webkit-box-sizing: border-box;
     -moz-box-sizing: border-box;
          box-sizing: border-box;
}
```

------

### position

**static**

`position: static;`是默认值，该值的元素不会被特殊定位，一个static元素表示它不会被positioned，一个position属性被设置为其他值的元素表示它会被positioned

**relative**

```
.relative1 {
  position: relative;
}
.relative2 {
  position: relative;
  top: -20x;
  left: 20x;
  width: 500px;
}
```
relative表现和static一样，除非你添加了一些额外的属性。
设置top，bottom，left，right属性会使其偏离正常位置，其他元素的位置不会受该元素的影响发生位置改变来弥补它偏离后剩下的空隙。

**fixed**

该元素相对于视窗来定位，这意味着即便页面滚动，它还是会停留在相同的位置。
```

.fixed {
  position: fixed;
  bottom: 0;
  right: 0;
  width: 200px;
  background-color: white;
}
```
移动浏览器对fix支持很差

**absolute**

该属性是相对于最近的“positioned”祖先元素定位，如果没有祖先元素，就相对于文档body元素，并且它会随着页面滚动而移动。
```
.relative {
  position: relative;
  width: 600px;
  height: 400px;
}
.absolute {
  position: absolute;
  top: 120px;
  right: 0;
  width: 300px;
  height: 200px;
}
```

```
.container {
  position: relative;
}
nav {
  position: absolute;
  left: 0px;
  width: 200px;
}
section {
  /* position is static by default */
  margin-left: 200px;
}
footer {
  position: fixed;
  bottom: 0;
  left: 0;
  height: 70px;
  background-color: white;
  width: 100%;
}
body {
  margin-bottom: 120px;
}
```
![position_example.png](https://upload-images.jianshu.io/upload_images/15578663-8c3bea5618a72e85.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### float

另一个布局中常用的CSS属性是float。可以用于实现文字环绕图片。
```
img {
  float: right;
  margin: 0 0 1em 1em;
}
```

### clear

![clear.png](https://upload-images.jianshu.io/upload_images/15578663-24fef33dc261429d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 清除浮动（clearfix hack）

如果图片是float的，并且比包含它的元素还高，就会溢出到容器外面。
`overflow: auto;` 就可以解决这个问题

![float_example.png](https://upload-images.jianshu.io/upload_images/15578663-f690784361887dbd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 媒体查询

用百分比宽度来布局，然后在浏览器变窄到无法容纳侧边栏中的菜单时，把布局显示成一列：
```
@media screen and (min-width:600px) {
  nav {
    float: left;
    width: 25%;
  }
  section {
    margin-left: 25%;
  }
}
@media screen and (max-width:599px) {
  nav li {
    display: inline;
  }
} 
```
![media_screen1.png](https://upload-images.jianshu.io/upload_images/15578663-8ddb5dc3b0e5e9bb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![media_screen2.png](https://upload-images.jianshu.io/upload_images/15578663-6483a2462c3ed551.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### inline-block

![inline-block.png](https://upload-images.jianshu.io/upload_images/15578663-d46961aaea3dfaa2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### flexbox

flex居中
```
.vertical-container {
  height: 300px;
  display: -webkit-flex;
  display:         flex;
  -webkit-align-items: center;
          align-items: center;
  -webkit-justify-content: center;
          justify-content: center;
}
```
