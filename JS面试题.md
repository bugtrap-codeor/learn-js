# js面试题

```javascript
1.
var f = function g(){return 23;};
typeof g();
//g is not defined
2.
var y=1,x=y=typeof x;
console.log(x);
//undefined
3.
var foo={
    bar:function(){console.log(this.baz)},
    baz:1
};
(function(){return typeof arguments[0]();})(foo.bar);
//"undefined"
4.
(function f(){
    function f(){console.log(1);}
    return f();
    function f(){console.log(2);}
})();
//2
5.
function Foo(){
    getName = function () {console.log(1); };
    return this;
}
Foo.getName = function () {console.log(2);};
Foo.prototype.getName = function () {console.log(3);};
var getName = function(){ console.log(4);}
function getName() {consolelog(5);}
Foo.getName();
getName()
Foo().getName()
getName();
new Foo.getName()
new Foo().getName();
new new Foo().getName();
//2 4 1 1 2 3 3
6.
setTimeout(function(){
    console.log("timeout1");
})
new Promise(function(resolve){
    console.log('promise1');
    for(var i=0;i<1000;i++){
        i==99&&resolve();
    }
    console.log('promise2');
}).then(function(){
    console.log('then1');
})
console.log('global1')
//promise1 promise2 global1 then1 undefined timeout1
7.
至少列举5种ES6特性
8.
function showBiBao(){
    for(var i=0;i<5;i++){
        setTimeout(function timer(){
            console.log(i)
        }, 1000);
    }
    console.log(i)
}
showBiBao()
//5 undefined 5 5 5 5 5
```
