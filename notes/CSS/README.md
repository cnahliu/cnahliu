##box-sizing
> content-box(default);

width&&height只包含内容宽高不包含border、padding、margin、其中margin为盒与盒的共享值

> border-box;

width&&height包含content、padding、border宽高不包含margin、其中margin为盒与盒的共享值

##position
>static(default)

static 是默认值，定位属性不可用，占据原有位置。

>relative

- 基于原位置进行相对定位，占据原有位置。

>fixed

- 基于浏览器窗口进行定位，不占据原有位置。
基于浏览器窗口的定位

>absolute

- 基于上是非static属性进行绝对定位,不占据原有位置。