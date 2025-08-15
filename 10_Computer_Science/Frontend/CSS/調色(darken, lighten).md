sass內建調色功能，可調亮或調暗
```
$base-color : #008000; //主色系綠色
.box{
  width: 100px;
  height: 100px;
  margin: 20px;
}

.box1{
  background: $base-color;
}

.box2{
  background: darken($base-color, 40%)
}

.box3{
  background: lighten($base-color, 40%)
}
```