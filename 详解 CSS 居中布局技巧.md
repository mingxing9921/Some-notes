## 水平居中元素：

-  通用办法,元素的宽高未知

  Html部分
```
<div class="parent">
	<span class="child">hello world</span>
</div>
```
```
<div class="parent">
	<div class="child">hello world</div>
</div>
```

方法一:CSS3 transform

```
.parent {
    position: relative;
}
.child {
    position: absolute;
    left: 50%;
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
	
  Html部分
```
<div class="parent">
	<span class="child">hello world</span>
</div>
```

```
.parent {
    text-align: center;
}
```

此方法同样适用于 display: inline-block 的元素。

-  居中的元素为常规文档流中的块元素(display: block)

常见的块元素：div, h1~h6, table, p, ul, li 等等

  Html部分
```
<div class="parent">
	<div class="child">hello world</div>
</div>
```

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

## 垂直居中元素 

-  通用方法，元素的宽高未知

方式一：CSS3 transform

```
.parent {
    position: relative;
}
.child {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
}
```

方式二：Flex 布局

```
.parent {
    display: flex;
    align-items: center;
}
```
适用于子元素为浮动，绝对定位，内联元素，均可垂直居中。

-  居中元素为单行文本

```
.text {
    line-height: 200px;
    height: 200px;
}
```
把文字的 line-height 设为文字父容器的高度，适用于只有一行文字的情况。

-  已知元素宽高

方式一：

```
.parent {
    position: relative;
}
.child{
    position: absolute;
    top: 50%;
    height: 100px;
    margin-top: -50px;
}
```
方式二:

```
.parent {
    position: relative;
}
.child{
    position: absolute;
    top: 0;
    bottom: 0;
    height: 100px;
    margin: auto 0;
}
```

## 水平垂直居中元素

-  1.绝对居中定位

```
div {
    width: 100px;
    height: 100px;
    margin: auto;
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
}
```

优点:
    1.不仅可以实现在正中间，还可以在正左方，正右方
    2.元素的宽高支持百分比 % 属性值和 min-/max- 属性
    3.可以封装为一个公共类，可做弹出层
    4.浏览器支持性好

-  2.负边距居中

```
.child {
    width: 100px;
    height: 100px;
    position: absolute;
    top: 50%;
    left: 50%;
    margin-left: -50px;
    margin-top: -50px;
}
```

特点:
    1.良好的跨浏览器特性,兼容 IE6 - IE7
    2.灵活性差，不能自适应，宽高不支持百分比尺寸和 min-/max- 属性

-  3.Transform 定位

```
.child {
    width: 100px;
    height: 100px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);  
}
```

特点：

    1.内容可自适应，可以封装为一个公共类，可做弹出层
    2.可能干扰其他 transform 效果

-  4.Flexbox布局

```
.parent {
    display: flex;
    justify-content: center;
    align-items: center;
}
```

这是 CSS 布局未来的趋势。Flexbox 是 CSS3 新增属性，设计初衷是为了解决像垂直居中这样的常见布局问题。

-  5. table-cell 居中

```
.parent {
    display: table-cell;
    vertical-align: middle;
    text-align: center;
    width: 200px;
    height: 200px;
    border: 1px solid red;
}
.child {
    width: 100px;
    height: 100px;
    display: inline-block;
    background-color: #03f;
}
```
适用于子元素 display 为 inline-block, inline 类型的元素，需要已知父元素的宽高，且父元素的宽高不能设为百分比数。

-  6. font-size 配合 vertical-align 实现垂直居中

```
.parent {
    font-size: 175.4px;
    height: 200px;
    text-align: center;
}

.child {
    vertical-align: middle;
    display: inline-block;
    font-size: 12px;
    width: 50px;
    height: 50px;
    background-color: #00f;
}
```

该方法的要点是给父元素设一个合适的 font-size 的值，这个值的取值为该父元素的高度除以 1.14 得到的值，并且子元素必须 是一个 inline 或 inline-block 元素，需要加上 vertical-align: middle 属性。使用这种方法，子元素的宽度或高度都不必知道。

具体原理可以上网搜 vertical-align 垂直居中。

-  7.文本内容居中

```
text {
    height: 100px;
    line-height: 100px;
    text-align: center;
}
```
