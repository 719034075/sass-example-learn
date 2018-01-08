# 导入sass文件

`sass`中可以用`@import`来引入其他的sass文件。而且可以省略`.sass`或`.scss`文件后缀和约定的局部文件前缀`_`

导入themes/_night-sky.scss这个局部文件里的变量，只需在样式表中写@import "themes/night-sky";。