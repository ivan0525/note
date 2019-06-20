通过设置以下css样式，可以改变所有文本的选中颜色
```css
::selection {
  background: orangered;
  color: #fff;
}
```
当然也可以通过选择器指定特定标签文本选中的颜色
```css
.example::selection {
  background: orangered;
  color: #fff;
}
```
