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