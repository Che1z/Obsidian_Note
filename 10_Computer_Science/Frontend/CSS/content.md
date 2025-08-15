content用法：

![[Pasted image 20231130193446.png]]

上述例子中，content內容是由@include pad{ }中內容所取代。
content可保留一個給外部寫入的空間。
```
.header {
  width: 500px;
  @include pad{
  /// 取代content內容
  };
}
```

