#JavaScript

##

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
##箭头函数