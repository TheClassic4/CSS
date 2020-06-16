### display: flex;
```
{
  flex: auto;
  
  flex-grow: 1;
  flex-shrink: 1;
  flex-basis: auto;
}
```
上述两种表达方式相同

flex-basis根据主轴方向不同优先级大于`width`、`height`

例如: 
```
<div class="box">
  <div class="inner"></div>
  <div class="inner2"></div>
</div>


<style>
.box {
  width: 400px;
  height: 200px;
  flex-direction: row;
  display: flex;
  .inner {
    flex-basis: 100px;
    flex-grow: 1;
    height: 100px;
  }
  .inner2 {
    flex-basis: 200px; 
    height: 100px;
  }
}
</style>
```
inner的宽度是100px(basis)+(400-200-100) * 1(grow) = 200px 

inner2的宽度是200px

```
<div class="box">
  <div class="inner"></div>
  <div class="inner2"></div>
</div>


<style>
.box {
  width: 400px;
  height: 200px;
  flex-direction: row;
  display: flex;
  .inner {
    flex-basis: 200px;
    flex-shrink: 3;
    height: 100px;
  }
  .inner2 {
    flex-basis: 300px; 
    flex-shrink: 2;
    height: 100px;
  }
}
</style>
```
inner的宽度是 200 - 100 * (200 * 3/(200 * 3 + 300 * 2)) = 150 px  

inner2的宽度是 300 - 100 * (300 * 2/(200 * 3 + 300 * 2)) = 250 px

如果`flex-shrink: 0;`即flex布局中不进行缩放

### 容器属性

`flex-direction: row | row-reverse | column | column-reverse;`

// 换行 默认为nowrap
`flex-wrap: nowrap | wrap | wrap-reverse;`

// flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap。
`flex-flow: <flex-direction> || <flex-wrap>;`

// space-between两端对齐，space-around两边的间隔都相等，所以中间的项目间隔会是周围的边框间隔的两倍
`justify-content: flex-start | flex-end | center | space-between | space-around;`
![justyfy-content.png](https://upload-images.jianshu.io/upload_images/15578663-62ed39f0a3f7c997.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

// align-items定义在交叉轴上如何对齐
`align-items: flex-start | flex-end | center | baseline | stretch;`
![align-items.png](https://upload-images.jianshu.io/upload_images/15578663-2ce8ae636efc60f3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

// align-content属性定义了多根轴线的对齐方式，如果项目只有一根轴线，该属性不起作用
`align-content: flex-start | flex-end | center | space-between | space-around | stretch;`
![align-content.png](https://upload-images.jianshu.io/upload_images/15578663-b638848507a4186c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
