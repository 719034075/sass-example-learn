# 导入sass文件

`css`中只有运行到`@import`，浏览器才会去下载相应的`css`文件。但是这会导致页面加载起来特别慢。

`sass`中可以用`@import`来引入其他的sass文件。而且可以省略`.sass`或`.scss`文件后缀和约定的局部文件前缀`_`。
这在生成`css`文件的时候就会导入相应的`sass`文件。所以浏览器无需发起额外的下载请求。

## 使用sass部分文件
导入themes/_night-sky.scss这个局部文件里的变量，只需在样式表中写@import "themes/night-sky";。

## 默认变量值
当反复声明一个变量的时候，只有最后一处的声明有效且会覆盖前面的值。

```scss
//编译前
$link-color: blue;
$link-color: red;
a {
color: $link-color;
}
```

```css
//编译后
a { color: red; }
```

`!default`用于变量，如果含有`!default`的变量之前已经有一个同名变量声明。那么含有`!default`的变量不会覆盖之前变量的值。

```scss
//编译前
$highlight-color: #F90;
$highlight-color: #F80 !default;
.selected {
  border: $highlight-color;
}
```

```css
//编译后
.selected { border: #F90; }
```

## 嵌套导入

通过嵌套导入只对站点中某一特定区域运用某种颜色主题或其他通过变量配置的样式。

```_blue-theme.scss
//编译前
aside {
  background: blue;
  color: white;
}
```

```imput.scss
//编译前
.blue-theme {@import "blue-theme"}
```

```css
//编译后
.blue-theme {
  aside {
    background: blue;
    color: white;
  }
}
```

## 导入原生的css文件

因为`scss`语法完全兼容`css`语法。所以把相应的`css`文件后缀名改成`scss`。当作`scss`文件导入即可。

