# 嵌套css规则

```scss
//编译前
#content {
  article {
    h1 { color: #333 }
    p { margin-bottom: 1.4em }
  }
  aside { background-color: #EEE }
}
```

```css
//编译后
#content article h1 { color: #333 }
#content article p { margin-bottom: 1.4em }
#content aside { background-color: #EEE }
```

sass在解开一个嵌套规则时就会把父选择器（`#content`）
通过**一个空格**连接到子选择器的前边（`article`和`aside`）
形成（`#content article`和`#content aside`）。
这种在CSS里边被称为后代选择器。

## 父选择器的标识符&

大多数情况下用上述的简单嵌套是没有什么问题的。
但是有些场景却不行，比如我们要在嵌套的选择器中应用一个`:hover`的伪类。

如果我们依旧沿用简单嵌套
```scss
//编译前
article a {
  color: blue;
  :hover { color: red }
}
```

```css
//编译后（但是这并不是我们预想的效果,‘a’和‘:hover’之间有个空格）
article a { color: blue; }
article a :hover { color: red; }
```
这种编译后的css，让`article`元素中的`a`元素内的所有子元素在`hover`时会变成红色。

但是我们如果要把这条规则应用到`a`本身就需要用到`&`符号。
```scss
//编译前
article a {
  color: blue;
  &:hover { color: red }
}
```

```css
//编译后（‘a’和‘:hover’之间没有空格）
article a { color: blue; }
article a:hover { color: red; }
```
`&`的本质是，在编译时,`&`被选择器直接替代。所以`&`除了为父选择器添加伪类之外，还可以为父选择器前添加选择器。
```scss
//编译前
#content aside {
  color: red;
  body.ie & { color: green }
}
```

```css
//编译后
#content aside {color: red};
body.ie #content aside { color: green }
```

## 群组选择器的嵌套

```scss
//编译前
.container {
  h1, h2, h3 {margin-bottom: .8em}
}
```

```css
//编译后
.container h1, .container h2, .container h3 { margin-bottom: .8em; }
```

## 子组合选择器和同层组合选择器：>、+和~

```scss
//编译前
article {
  ~ article { border-top: 1px dashed #ccc }
  > section { background: #eee }
  dl > {
    dt { color: #333 }
    dd { color: #555 }
  }
  nav + & { margin-top: 0 }
}
```

```css
//编译后
article ~ article { border-top: 1px dashed #ccc }
article > footer { background: #eee }
article dl > dt { color: #333 }
article dl > dd { color: #555 }
nav + article { margin-top: 0 }
```

## 嵌套属性

```scss
//编译前
nav {
  border: {
  style: solid;
  width: 1px;
  color: #ccc;
  }
}
```

```css
//编译后
nav {
  border-style: solid;
  border-width: 1px;
  border-color: #ccc;
}
```