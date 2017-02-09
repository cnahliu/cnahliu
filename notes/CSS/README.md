##Normalize VS Reset
1. 保护了有价值的默认值
2. 修正了一些bug及主流浏览器在渲染上的不一致。
##display
> inline-block

 inline-block设置后默认会有4px或8px的间距，通常设置父级的font-size：0来清除间距。

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

##transform 

CSS中transform 属性允许你修改CSS可视化模型的坐标空间。通过transform，可以让元素进行移动（translate）、旋转（rotate）、缩放（scale）、倾斜（skew）

##transition

>transition-property:all
为指定属性设置动画效果

>transition-duration:2s
设置动画过渡时间

>transition-timing-function:ease

-设置动画过渡方式

-linea
 
 动画从头到尾的速度是相同的。

-ease
	
  动画从头到尾的速度是相同的。

-ease-in
  
  动画以低速开始。

-ease-out
  
  动画以低速结束。

-ease-in-out
  
  动画以低速开始和结束。

-cubic-bezier(n,n,n,n)

  自定义从 0 到 1 的数值。
  
>transition-delay:0s
  
  设置动画延时

>transition:all 2s ease 0s;

  简写形式

##animation

>animation-name:keyframe

  自定义keyframe的名称

>animation-duration:过渡时间
  
  设置动画过渡时间

>animation-timing-function:ease

  设置动画过渡方式

linea

  动画从头到尾的速度是相同的。

ease
	
   动画从头到尾的速度是相同的。

ease-in
  
  动画以低速开始。

ease-out

  动画以低速结束。

ease-in-out
  
   动画以低速开始和结束。

cubic-bezier(n,n,n,n)

>animation-delay:0s

  设置动画延时

>animation-iteration-count:0

  设置动画循环次数

>animation-direction:normal

normal
  动画正常播放
alternate
  动画轮流反向播放(更加自然)。


##代码片段
> 通过缩放0.5倍的方式，来让浏览器显示0.5px的边框

```less
.header{
	position:relative;
	&:after{
		content: '';
		position: absolute;
		width: 200%;
		bottom: 0;
		left: 0;
		transform: scale(.5);
		transform-origin: 0 0;
		box-sizing: border-box;
		border-bottom: 1px solid #eee;	
	}
}
```
> CSS实现单行文本溢出显示省略号

```less
span{
	width:200px;
	overflow: hidden;
	text-overflow:ellipsis;
	white-space: nowrap;
}

```