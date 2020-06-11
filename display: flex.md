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
inner的宽度是100px(basis)+(400-200-100)*1(grow) = 200px  
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
inner的宽度是 200-100*(200*3/(200*3+300*2)) = 150 px  
inner2的宽度是 300 - 100*(300*2/O(200*3+300*2)) =250 px

如果`flex-shrink: 0;`即flex布局中不进行缩放
