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

----
每一个元素都有一个默认的display类型。你可以随时随地重写它。例如把`li`元素修改为inline，制作成水平菜单
