# 混合器

当重用的内容比较少的时候，用`sass`**变量**就可以解决问题。

但是当重用大段大段的内容时，`sass`**变量**就显得有些捉襟见肘了。

因此这里引出`sass`混合器。`@mixin`用来定义，`@include`用来调用。

```scss
//编译前
@mixin rounded-corners {
  -moz-border-radius: 5px;
  -webkit-border-radius: 5px;
  border-radius: 5px;
}
notice {
  background-color: green;
  border: 2px solid #00aa00;
  @include rounded-corners;
}
```

```css
//编译后
.notice {
  background-color: green;
  border: 2px solid #00aa00;
  -moz-border-radius: 5px;
  -webkit-border-radius: 5px;
  border-radius: 5px;
}
```

## 何时使用混合器

滥用混合器会导致生成的`css`过大，导致加载缓慢。

那么何时使用混合器，经验之谈是看你能否为一个混合器想出一个好名字。

## 给混合器传参

混合器也可以像`JavaScript`中的`function`来使用。

```scss
//编译前
@mixin link-colors($normal, $hover, $visited) {
  color: $normal;
  &:hover { color: $hover; }
  &:visited { color: $visited; }
}
a {
  @include link-colors(blue, red, green);
}
```

```css
//编译后
a { color: blue; }
a:hover { color: red; }
a:visited { color: green; }
```

可以按名传参

```scss
a {
    @include link-colors(
      $normal: blue,
      $visited: green,
      $hover: red
  );
}
```

还可以设置默认参数值

```scss
@mixin link-colors(
    $normal,
    $hover: $normal,
    $visited: $normal
  )
{
  color: $normal;
  &:hover { color: $hover; }
  &:visited { color: $visited; }
}
```