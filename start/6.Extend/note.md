# 继承

```scss
//编译前
.error {
  border: 1px solid red;
  background-color: #fdd;
}
.error a{
  color: red;
  font-weight: 100;
}
h1.error {
  font-size: 1.2rem;
}

.seriousError {
  @extend .error;
  border-width: 4px;
}
```

```css
//编译后
.error, .seriousError { border: 1px solid red; background-color: #fdd; }
.error a, .seriousError a { color: red; font-weight: 100; }
h1.error, h1.seriousError { font-size: 1.2rem; }
.seriousError { border-width: 4px; }
```

* `.seriousError``@extend``.important.error` ， 那么`.important.error` 和`h1.important.error` 的样式都会被`.seriousError`继承， 但是`.important`或者`.error`下的样式则不会被继承。
* 一个选择器序列（`#main .seriousError`）`@extend`另一个选择器（`.error`），那么只有完全匹配`#main .seriousError`这个选择器的元素才会继承`.error`的样式，就像单个类名继承那样。拥有`class="seriousError"`的`#main`元素之外的元素不会受到影响。

**不要用后代选择器去继承。**