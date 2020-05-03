# learn-js

JavaScript学习

## JS输出

·使用window.alert()，弹出警告框

·使用document.write()方法将内容写到HTML文档中

·使用innerHTML写入到HTML元素

·使用console.log()写入到浏览器的控制台。

```javascript
//toFixed()方法可把number四舍五入为指定小数位数的数字，返回值为string类型。
//javascript为Array对象提供了很多内置的方法
//常见数组方法
var arr=[25,10,'bugtrap'];
arr.push('is')//末尾添加元素 'is'
arr.pop();//末尾删除一个元素
arr.unshift('good',5)//开头添加 'good'和5 元素
arr.shift()//开头删除一个元素
//检索方法
arr.includes(q,n)；//从下标n开始判断一个数组是否包含元素q
Array.isArray(arr)；//判断arr是否为Array
arr.indexOf(m,n)；//从位置n开始向后寻找第一个指定元素m的索引，若无返回-1，有则返回索引
lastIndexOf(m,n)；//从位置n开始向前寻找第一个指定元素m的索引，若无返回-1，有则返回索引
//数组转字符串:join(分隔符)；toString();
arr.toString();//用,分隔
arr.join(' ');//用分隔符分隔

arr.sort();//排序，会改变原来数组中的元素顺序,如果排序效果非预期，可以给 sort 函数加一个排序函数的参数
arr.reverse();//逆置，将原数组中的元素顺序逆置
arr.fill(a,m,n);//替换，将原数组中从第m到n-1个元素用元素a替换
arr.concat(a,b);//arr连接a和b，不改变原数组元素
arr.splice(m,n,a);//在原数组中插入、删除、替换数组的元素,从m开始向后n位，用a替代
arr.slice(m,n);//从原数组中返回第m到n-1个元素,不改变原数组

//二维数组的转置：将二维数组的横向元素保存为纵向元素
var arr = [[1,2,3],[4,5,6]];
var res = [];
for(var i=0;i<arr[0].length;i++){//行
    res[i]=[];
    for(var j=0;j<arr.length;j++){//列
        res[i][j]=arr[j][i];
    }
}
for(var i=0;i<arr.length;i++)
    console.log(arr[i])
for(j=0;j<res.length;j++)
    console.log(res[j])

//用javascript数组实现网站导航栏
//1、通过创建两个数组来保存导航选项和导航链接
var navlist=['首页','免费资源','课程中心','TT学院','学员故事','线上学院','技术社区'];
var linklist=['#','#','#','#','#','#','#'];
//2、生成导航栏：列表+超链接、无序列表+超链接
<ul>
    <li><a>列表项1</a></li>
    <li><a>列表项2</a></li>
</ul>
<ol>
    <li><a>列表项1</a></li>
    <li><a>列表项2</a></li>
</ol>
//3、通过遍历数组，生成导航选项和导航链接
var str='<ul>';
for(var i in navlist){
    str+='<li><a href="'+'linklist[i]'+'">'+navlist[i]+'</a><li>';
}
str+='</ul>'
//4、设置样式：设置为行内元素、前导符去掉、超链接去默认格式、设置鼠标滑过时的颜色

//函数的定义和调用
1、Javacript提供的内置函数:例:prompt();parselnt();isNaN();
2、自定义函数
function 函数名([参数1，参数2，..]){
    函数内容;
    [return 返回值;]
}
//参数设置
1、无参函数 调用和声明无序
function myfun(){
    document.write("无参函数");
}
myfun();
2、有参函数
function myfun(name){
    console.log("有参函数"+name);
}
myfun('bugtrap');
3、获取函数调用时传递的所有实参 例：
function MultiParam(){
    document.write(arguments.length);
    document.write("第一个参数:"+arguments[0]);
}
4、含有默认值的参数
function greet(name, say='Hi，I\'m'){
    document.write(say+name);
}
greet('bugtrap');
5、剩余参数
function MultiParam(n,...param){
    param.unshift(n)
    console.log(param);
}

//变量的作用域
1、全局变量：不在任何函数内显式(利用var关键字)声明的变量、在函数内省略var声明的变量、在同一个页面的所有脚本内都有效
2、局部变量：在函数内利用var声明的变量，仅在函数体内有效
3、块级变量：利用let声明的变量，仅在{}中间有效
在函数作用域内 加var定义的变量是局部变量,不加var定义的就成了全局变量
JS中声明全局变量
声明方式一：
使用var（关键字）+变量名(标识符)的方式在function外部声明，即为全局变量，否则在function声明的是局部变量
var test = 5;  //全局变量
function a（）
{
  var cc=3; //局部变量
  alert(test);
}
function b（）{alert(test);}
声明方式二：
没有使用var，直接给标识符test赋值，这样会隐式的声明了全局变量test。即使该语句是在一个function内，当该function被执行后test变成了全局变量
test = 5;//全局变量
function a()
{
  aa=3; //全局变量
  alert(test);
}
声明方式三：
使用window全局对象来声明，全局对象的属性对应也是全局变量
window.test = 5;

var i=3;//全局
function test(){
    var i=4;//局部
    if(i<6){
        let i=5;//块级
        console.log(i);
    }
    console.log(i);
}
console.log(i);
test();

//函数表达式:将声明的函数赋值给一个变量，通过变量完成函数的调用和参数的传递
var m=function maxnum(a, b){
    if(a>=b)
        console.log(a);
    else
        console.log(b);
}
m(3,5);
//函数表达式与函数声明的方式比较:
1、定义调用顺序不同
函数声明的方式：定义和调用顺序不限
函数表达式:先定义，后调用
2、调用方式不同
函数声明的方式：函数名()
函数表达式:变量名()
//匿名函数:没有函数名称的函数，可以有效的避免全局变量的污染以及函数名的冲突
1、函数表达式中省略函数名称
var m=function(a,b){
    alert(a+b);
}
m(3,5);
2、自调用方式
(function(a,b){
    alert(a*b);
})(3,5);
3、处理事件
document.body.onload=function(){alert('hello');}
//回调函数:一个函数A作为参数传递给另一个函数B，然后在B的函数体内调用函数A，将A称为回调函数
function test(a, b, func){alert(func(a, b))};
function func1(a, b){return a;}
function func2(a, b){return b;}
test(3,5, func2);

//利用函数处理用户单击事件，根据用户传递参数的不同，完成字符串大小写的转换

```
