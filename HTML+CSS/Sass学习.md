#### @extend 与 @mixin的区别  ：
- 使两者之间的关系非常清晰

- 无论你在样式表的哪里使用`.error`,`.seriousError`都会继承其中的样式

`@include` 指令引用混合样式，格式是在其后添加混合名称，以及需要的参数（可选）







## 变量 (variables)

sass使用$符号来标识变量，可以把反复使用的css属性值定义成变量，然后通过变量名引用它们

**编译前**：

```scss
$bgColor: #00bcd4;
.nav {
　　color:  $bgColor;
    border: 1px solid $bgColor;
}
```

**编译后**：

```css
.nav {
　　color:  #00bcd4;
    border: 1px solid $bgColor;
}
```







## 嵌套 (nested rules)

> CSS许多属性都位于相同的命名空间（例如font-family、font-size、font-weight都位于font命名空间下），Scss当中只需要编写命名空间一次，后续嵌套的子属性都将会位于该命名空间之下，请看下面的代码：

```scss

```



## 混合 (mixins)

```scss
混合器使用@mixin标识符定义。

在样式表中通过@include来使用这个混合器，@include调用会把混合器中的所有样式提取出来放在@include被调用的地方。
```



## 导入 (inline imports) 

```scss
@import '../../style/common'; //必须加分号，不然会报错
```



## 引用父级选择器  &

> scss使用"&"关键字在CSS规则中引用父级选择器
>

**编译前：**

```scss
a {
  font-weight: bold;
  text-decoration: none;
  &:hover { text-decoration: underline; }
  body.firefox & { font-weight: normal; }
}
```

**编译后：**

```css
a {font-weight: bold;
  text-decoration: none; }
  a:hover {
    text-decoration: underline; }
  body.firefox a {
    font-weight: normal; }
```



## 其他小结：

- `sass`局部文件的文件名以下划线开头。编译时不编译这个文件输出`css`，而只把这个文件用作导入
- 