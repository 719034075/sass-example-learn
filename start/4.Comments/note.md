# 静默注释

```scss
// 编译前
body {
  color: #333; // 这种注释内容不会出现在生成的css文件中
  padding: 0; /* 这种注释内容会出现在生成的css文件中 */
}
```


```scss
// 编译前
body {
  color /* 这块注释内容不会出现在生成的css中 */: #333;
  padding: 1 /* 这块注释内容也不会出现在生成的css中 */ 0;
}
```

如果在编译的过程中`scss`文件中出现了非 ASCII 字符时，需要在`scss`的开头使用`@charset "encoding-name"`来规定编码格式。

```scss
//按照给出的UTF-8编码格式编译文件
@charset "UTF-8";
```