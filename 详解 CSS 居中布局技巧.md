## 水平居中元素：

-  通用办法,元素的宽高未知

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

方法二:Flex 布局
```
.parent {
    display: flex;
    justify-content: center;
}
```

适用于子元素为浮动，绝对定位，内联元素，均可水平居中。

-  居中的元素为常规文档流中的内联元素(display: inline)

常见的内联元素有：span, a, img, input, label 等等

```
.parent {
    text-align: center;
}
```

此方法同样适用于 display: inline-block 的元素。

-  居中的元素为常规文档流中的块元素(display: block)

常见的块元素：div, h1~h6, table, p, ul, li 等等

方式一：设置 margin

```
.parent {
    width: 100%;
}
.child {
    width: 600px;
    height: 50px;
    margin: 0 auto;
    background: #999;
}
```

此方法只能进行水平的居中，且对浮动元素或绝对定位元素无效。

方式二：修改为 inline-block 属性

```
.parent {
    text-align: center;
}
.child {
    display: inline-block;
}
```

-  居中的元素为浮动元素

```
.child {
    width: 100px;
    float: left;
    position: relative;
    left: 50%;
    margin-left: -50px;
}
```

-  居中的元素为绝对定位元素

方式一:

```
.parent {
    position: relative;
}
.child {
    position: absolute;
    width: 100px;
    left: 50%;
    margin-left: -50px;
}
```

方式二:

```
.parent {
    position: relative;
}
.child {
    position: absolute;
    width: 100px;
    left: 0;
    right: 0;
    margin: 0 auto;
}
```
