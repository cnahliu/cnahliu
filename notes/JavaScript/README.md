#JavaScript

##Array

>var box=['a','b','c',11,2,3]

  1. 通过字面量的方式创建数组box

>box.join('||')

  1. 使用join方法更改连接符为'||',返回'a||b||c||11||2||3'
  2. 不影响原数组

>box.push('aaa')

  1. 向数组添加向后一个'a',返回数组长度7
  2. 原数组值发生变化:['a','b','c',11,2,3,'aaa']

>box.shift()

  1. 从数组前端删除一个元素,返回被移除的元素'a'
  2. 原数组值发生变化:['b','c',11,2,3,'aaa']

>box.pop()

  1. 从数组后端删除一个元素,返回被移除的元素'aaa'
  2. 原数组值发生变化:['b','c',11,2,3]

>box.unshift('1','2',3)

  1. 从数组前端添加一个元素,返回box的长度8
  2. 原数组值发生变化:[1,2,3,'b','c',11,2,3]

>box.reverse()

  1. 将对数组逆向排序,返回排序后结果[ 3, 2, 11, 'c', 'b', 3, 2, 1 ]
  2. 原数组值发生变化:[ 3, 2, 11, 'c', 'b', 3, 2, 1 ]

>box.sort()

  1. 对数组进行Unicode码位点(code point)排序,返回排序后结果[ 1, 111, 2, 2, 3, 3, 'b', 'c' ]
  2. 原数组值发生变化:[ 1, 111, 2, 2, 3, 3, 'b', 'c' ]


>box.concat('end')

  1. 在原数组追加'end',返回[ 1, 111, 2, 2, 3, 3, 'b', 'c' ,'end']
  2. 不影响原数组

>box.splice(7)

  1. 在移除box 索引为7之后的部分，返回移除部分['c']
  2. 原数组值发生变化:[ 1, 111, 2, 2, 3, 3,'b' ]

>box.splice(5,2,'new')

  1. 效果如同将3,b替换为new，返回移除部分['3','b']
  2. 原数组值发生变化:[ 1, 111, 2, 2, 3, 'new' ]

>box.map(function(x){return x+1 })

>box.reduce(function(prev,currentValue,currentIndex,array){return prev+current},initialValue)

  1. 从左到右遍历整个数组进行数组
      1. prev 数据处理后返回的结果
      2. currentValue 当前数值
      3. currentIndex 当前索引
      4. array 原数组（保持不变）
      5. initialValue 初始值
  2. 不影响元数组


##Function

>.call(thisArg,args1,args2)

1. 方法在使用一个指定的this值和若干个指定的参数值的前提下调用某个函数或方法.

>.apply(thisArg,argsArray)

1.apply() 方法在指定 this 值和参数（参数以数组或类数组对象的形式存在）的情况下调用某个函数。

>.bind(thisArg,argsArray)

1.方法会创建一个新函数。当这个新函数被调用时，bind()的第一个参数将作为它运行时的 this, 之后的一序列参数将会在传递的实参前传入作为它的参数。
2.ECMAScript 5.1 新增。


##Object
var object ={
  id:1,
  name:['m','n']
  age:'666'
}
```JavaScript
//1.ES6中对象可以是省略function关键字及对象的键(前提是键跟值引用的变量的值是同一个名字)
//ES6
function createObject(a,b){
    return{
        a,
        b,
        eventA{
            console.log(this.a)
        }
    }
}
//ES5
function createObject(a,b){
    return{
        a:a,
        b:b
        eventA:function(){
            console.log(this.a)
        }
    }
}
```

> Object.assign(target,sources)

  1. 用于将所有可枚举的属性的值从一个或多个源对象复制到目标对象,并返回目标对象
  2. target的原始指将发生变化

> Obejct.key(target)

  1. 返回对象的索引
  2. 原对象不发生变化
##Arrow Function(箭头函数)

箭头函数相当于匿名函数，并且简化函数定义，并且它拥有词法作用域的this值（即不会新产生自己作用域下的this。箭头函数有两种格式，一种是只包含一个表达式，连`{}`和`return`都省略掉了，还有一格式可以包含多条语句，这个时候就不能省略{...}和return,
```JavaScript
//单个参表达式
//ES5
funciton (x){
	return x*x;
}
//ES6
x> x*x

//返回对象
x=>({foo:x})

//多参数表达式
//ES5
z=2
a=function (x,y){
	return x*y+z;
}
a(2,3) //8
//ES6
z=2
a=(x,y)=>{return x*y+this.z}
a(2,3) //8


```

##匿名函数(anonymous function)

> 即没有名字的函数，常见于一些只执行一次的函数。

```JavaScript
var x = function (a, b) {return a * b};

```

##立即执行函数(Immediately-Invoked Function Expression)

```JavaScript
function(){
  console.log('666')
}()
!function(){
  console.log('666')
}()

```
##闭包(Closure)

> 保护私有变量，避免变量污染


```JavaScript
//一般写法
var increasing=function(number) {
  var number = number;
  return function() {
    return ++number;
  }
}
var aa=increasing(0)
aa()
//结合立即执行函数
var number=(function() {
  var number = 1;
  return {
    increment: function(){
      return ++number
    },
    decrement: function() {
      return --number;
    },
    get: function() {
      return number;
    }
  }
})()
var getNumber=number.get()
var incrementNumber=number.increment()
var decrementNumber=number.decrement()
```

##Tip

```JavaScript
//开启页面的编辑模式
document.body.contentEditable='true'; document.designMode='on';
```
