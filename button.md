### 1.移动端底部固定样式
```
<div class="btn-wrp">
  <button></button>
  <button></button>  
</div>

<style>
.btn-wrp {
  position: fixed;
  width: 100%; // 占满一行
  height: 148px;
  justify-content: space-between;
  button {
    flex: 1 1 auto;
  }
}
</style>
```
