## 水平居中元素：

- [通用办法,元素的宽高未知]
方法一:CSS3 transform
```
.parent {
    position: relative;
}
.child {
    position: absolute;
    left: 50%:
    transform: translateX(-50%);
}
```
