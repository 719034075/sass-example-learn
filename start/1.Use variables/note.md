# 使用变量

`sass`为`css`引入了变量，因此可以把反复使用的`css`的属性值定义成有易懂的、表意直白变量名的变量。
`sass`使用`$`标识变量。
老版本使用`!`标识变量。

## 变量声明
```sass
$highlight-color:#F90;
```

任何的`css`属性值的赋值都可以作为`sass`的变量值。
甚至可以是以空格分割的多个属性值。
或者是以逗号分割的多个属性值。

```sass
//1.以空格分割的多个属性值
$basic-border: 1px solid black;

//2.以逗号分割的多个属性值
$plain-font: "Myriad Pro",Myriad,"Helvetica Neue",Helvetica,"Liberation Sans",Arial;
```

变量可以在`css`规则块定义之外存在。
变量也可以定义在规则块内。但是这个变量对应地，也只有这个规则块可以调用。

## 变量名用中划线还是下划线分隔

中划线更普遍，但是下划线也允许，不强求。因此变量`$link-color`和变量`$link_color`是同一个变量。
但是sass中纯`css`不互通，比如：类名，id或者属性名。