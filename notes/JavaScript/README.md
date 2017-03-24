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


##词法作用域

#ECMAScript 6 新特性
ES6既是一个历史名词，也是一个泛指，含义是5.1版以后的JavaScript的下一代标准，涵盖了ES2015、ES2016、ES2017等等，而ES2015则是正式名称，特指该年发布的正式版本的语言标准。本书中提到“ES6”的地方，一般是指ES2015标准，但有时也是泛指“下一代JavaScript语言”。

##Object
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
//
function
```
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
