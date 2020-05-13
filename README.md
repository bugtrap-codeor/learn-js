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

### 面向对象的特征主要可以概况为封装性、继承性和多态性

```javascript
//面向过程思想注重的是具体的步骤，只有按照步骤一步一步执行，才能完成任务。
//面向对象注重的是一个个对象，通过对象和对象之间的交互来完成具体的任务。

一、对象的定义
对象的定义是通过“{}”语法实现的，对象的成员以键对值的形式存放在{}中，多个成员之间使用逗号分隔。
var o1={}
var o2={
    name:'bugtrap',
    sayhello:function(){alert('你好')}
}
`JSON(JavaScript Object Notation,JavaScript对象字符）。实际上是一个字符串，字符串可以被任何编程语言读取及作为数据格式传递。
JSON需要使用双引号包裹对象的成员名和字符串的值。`
var json={"name":"Tom","age":20,"work":true}
//JSON.parse():将JSON字符串转换为JavaScript对象
//JSON.stringify():将一个JavaScript对象转换为JSON字符串。
alert(JSON.parse(JSON.stringify(o2)))
二、对象成员的访问
通过‘.’和‘[]’访问对象成员和动态的给对象增加成员。
alert(o2.name);alert(o2['age'])
使用for...in可以遍历对象的成员。
//对象成员的遍历
for(var i in o2){//i是对象02中的成员名字
    document.write(i+'-'+o2[i]+'<br>')
    if(typeof(o2[i])=='function'){
        o2[i]();//如果成员是函数的话，就这样调用函数
    }
}
三、深拷贝和浅拷贝
//浅拷贝：将变量p1赋值给p2后，更改p2的成员，p1的成员也会发生改变

//深拷贝：将变量p1复制给p2后，更改p2的成员，p1的成员不发生改变
function deepcopy(obj) {
    var o={}//先声明一个变量，使得两个对象指向不同的内存
    for(var k in obj)
    o[k]=(typeof(obj[k])==='object')?deepcopy(obij[k]):obj[k];
    return o
}
var o4=deepcopy(o2);

一、JavaScript内置构造函数
//new 构造函数名()：JavaScript提供了Object、String、Date等构造函数。
var arr=new Array();
var obj=new Object({age:19});
obj.name='小米';
//对象的constructor属性指向该对象的构造函数。
var o={name:'Jim',age:20};
var obj=new Object();
document.write(o.constructor);
document.write(obj.constructor);
二、自定义构造函数
1、定义构造函数
function Person(name,a){
    this.name=name;
    var age=a;
    this.getage=function(){
        return age;
        this.sayHi=function(){alert("hello,my name is"+this.name);}
    }
}
2、通过new运算符定义对象实例
var p1=new Person('Jack',18);
alert(p1.getage());
//（1）构造函数命名时推荐将所有的单词首字母大写。
//（2）在构造函数内部，使用this表示刚刚创建的对象。
//（3）使用var关键字定义的变量为私有成员。

三、this的指向
//1、使用new关键字将函数作为构造函数调用时，构造函数内部的this指向新创建的对象。
//2、直接通过函数名调用函数时，this指向的是全局对象（在浏览器中表示window对象）。
//3、如果将函数作为对象的方法调用时，this指向该对象。
function Person(name){
    this.name=name;
    this.getage=function(){this.age=10;}
}
var p1=new Person('Jim');
alert(p1.age);//undefined
p1.getage();//this指向p1
alert(p1.age);//10
Person("Jack");//全局window下
alert(name);//Jack

//内置对象，Array:数组,String:字符串,Math:数值计算,Date:日期,Number:数值对象
一、String对象
利用一对单引号或双引号创建的字符型数据，可以像对象一样使用，这是因为这些对象实际上是构造函数String的实例。String对象提供了一些用于对字符串进行处理的方法和属性
`length、charAt（[指定位置]）、indexOf(要查找的子串[，开始位置]）、lastlndexOf(要查找的子串[，开始位置]）、substring(开始位置[，结束位置]）、substr(开始位置[，长度])、toLowerCase()、toUpperCase()、split(分隔符)、replace(需替代的字符串，新字符串)、concat(字符串1，…）`
var str='i like javascript'
console.log(str.constructor)//ƒ String() { [native code] }
console.log(str.length)//17
console.log(str.charAt(5))//e
console.log(str.indexOf('a',0))//8
console.log(str.lastIndexOf('a',17))//10
console.log(str.substring(2,11))//like java
console.log(str.substr(2,9))//like java
console.log(str.toLowerCase())//i like javascript
console.log(str.toUpperCase())//I LIKE JAVASCRIPT
str.split(' ')//{"i", "like", "javascript"}
console.log(str.replace('a','b'))//i like jbvascript不改变原来字符串
console.log(str.concat(' Good!'))//i like javascript Good!不改变原来字符串
二、Number对象
Number对象用于处理整数、浮点数等数值。
MAX_VALUE//最大数值（对象的静态成员）
MIN_VALUE//最小正数（对象的静态成员）
toFixed(数值)
var num=23.556;
num.toFixed();//24   四舍五入，只保留整数
num.toFixed(4);///23.5560   补0保留4位小数
Number.MAX_VALUE;//1.7976931348623157e+308
Number.MIN_VALUE//5e-324
三、Math对象
Math对象用于对数值进行数学计算，与其他对象不同的是，Math对象不是一个构造函数，不需要实例化就能使用
属性：
    E：欧拉常量，自然对数的底（约等于2.718)
    LN2：2的自然对数（约等于0.693）
    LN10：10的自然对数（约等于2.302)
    LOG2E：以2为底的e的对数（约等于1.442)
    LOG10E:以10为底的e的对数（约等于0.434）
    PI:T的值（约等于3.14159)
    SQRT1_2:0.5的平方根（约等于0.707）
    SQRT2：2的平方根（约等于1.414)
方法：
    abs(x)：返回x的绝对值
    ceil(x)：返回大于或等于x的最小整数，即向上取整
    floor(x)：返回小或等于x的最大整数，即向下取整
    max(al,b..…]):返回所有参数间的最大值
    min(al,b,.…])：返回所有参数间的最小值
    pow(m,n):返回m的n次方（其中m为底，n为指数）
    sqrt(n):返回n的平方根
    random()：返回大于等于0.0且小于1.0之间的一个随机数
    round(x)返回x四舍五入之后的整数
var num = -5.6
Math.abs(num)//5.6
Math.ceil(num)//-5
Math.floor(num)//-6
Math.ceil(Math.random()*10+5,num)//8 返回一个5-15间的随机数并向上取整
四、Date对象
Date对象用于处理日期和时间
var 对象实例名=new Date([日期参数1])
var today=new Date();//当日时间为对象初值。
console.log(today)//Wed May 06 2020 12:36:19 GMT+0800 (中国标准时间)
var today=new Date(2020,05,06,12,35,22);//一律以数字表示：即【年，月，日，时，分，秒】，至少要指定年和月两个参数
console.log(today)//Sat Jun 06 2020 12:35:22 GMT+0800 (中国标准时间)
var today=new Date("2019-03-10 12:00:00");//至少需要指定年份
console.log(today)//Sun Mar 10 2019 12:00:00 GMT+0800 (中国标准时间)
    set/getFullYear()设置/返回年份值，例：2020
    set/getMonth()设置/返回月份值，范围为0~11，0表示一月
    set/getDate()设置/并返回月份中的某天，范围为1～31
    set/getHours()设置/返回小时数，范围为0～23
    set/getMinutes()设置/返回分钟数，范围为0-59
    set/getSeconds()设置/返回秒数，范围为0~59
    getDay()返回星期几，范围为0~6，0表示星期日
    set/getTime()设置/返回从1970-01-01 00:00:00距离Date对象所代表时间的毫秒数

利用JavaScript的内置对象Date对象完成制作年历
1、用户输入年份，弹出一个输入框，提示用户输入年份。在打开网页时弹出一个输入框：prompt，用户输入想要查询的年份。
当用户单击“确定”按钮时，会返回文本框中的内容，如果用户单击“取消”按钮，则返回null。
var year=parselnt(prompt('请输入年份：,2019))
2、利用表格，生成指定年份的年历
（1）利用表格显示每个月的日历
<table>
    <tr><th colspan="7">2020年3月</th></tr>
    <tr><td>一</td><td>二</td><td>三</td><td>四</td><td>五</td><td>六</td><td>日</td></tr>
</table>
（2）获取每个月的天数：
getDate()函数max=new Date(year,m,0).getDate()；注：月份是0-11，日期是1-31，这个函数表示第year年第m+1月1日的前一天的日期，即第m月包含的天数。
（3)获取每天是星期几：getDay()函数w=new Date(year,0).getDay();w=(w+1>6)?0:w+1;注：星期是0-6，只需要获取每一年的1月1日的星期数，其他日期的星期数就知道了
（4）确定每个月的第一天显示在第几个单元格中，将前几个单元格合并，然后将日期顺序显示
if(w!=1&&d==1){
    html+='<td colspan=';
    if(w==0) html+=6;
    else html+=w-1;
    htlm+='></td>';
}
html+='<td>'+d+'</td>';
（5）如果w=0，即星期日，且不是最后一天，则开始新的一行
if(w==0&&d!=max)
    html+='</tr><tr>';
3、样式设置，因为table是块内元素，因此不同月份会显示到不同的行，要想让各个月的日历显示到一行，必须设置<table>
将<th>背景色设置为gray。
将<td>中的文字居中显示的样式。
table{displaysinline;}
th{background-color:gray;}
td{text-align:center}

错误处理
//当发生错误时，JavaScript引擎会抛出一个错误对象，利用异常处理语句try...catch可以对错误对象进行捕获，捕获后可以查看错误信息。
var e=new Error('除数不能为0')
function div(numl,num2){
    try{
        if(num2==0)throw e//throw new Error('除数不能为0')
        document.write(numl/num2)
    }catch(e){
        document.write(e)
    }
}
div(10,0)

一、原型
//原型实现了对象间的联系，利用原型可以提高代码的复用率
    在JavaScript中，每一个函数对象都有一个prototype属性，指向原型对象。原型对象中包含实例共享的方法和属性，也可以为其添加方法或属性。
    利用构造函数创建的每个对象都与这个原型对象连接，因为JavaScript中的每个对象都有一个属性 `_proto_（双）指向它的原型对象`，也就是 `构造函数的prototype指向的对象`，当访问对象中的不存在的属性或方法时，会自动调用该 `对象的原型对象`的属性和方法。
function Person(name){this.name=name;}
Person.prototype.name='bugtrap';
Person.prototype.sayhi=function(){document.write("我叫"+this.name);}
var p1=new Person("java");
p1.__proto__.sayhi();//我叫bugtrap
var p2=new Person('script');
p2.sayhi()//我叫script           利用原型实现继承
二、继承
//继承是在已有对象的基础上进行扩展，增加一些新的功能，得到一个新的对象。
利用原型实现继承
替换原型实现继承
function Person(name){this.name=name;}
Person.prototype={sayHi:function(){document.write("你好，我是新对象")}}
var p=new Person('liu')
p.sayHi()//你好，我是新对象
利用Object.create()实现继承
//Object.create(obj[,properties])obj：新创建的对象的原型，表示要继承的对象。properties:可选，也是一个对象，用于对新创建的对象进行初始化。
var obj={name:'bugtrap'};
var obj1=Object.create(obj);
document.write(obj1.name);//bugtrap
混入继承
var o1={}
var o2={name:"liu", age:16}
function extend(o1,o2){
    for(var i in o2)
    o1[i]=o2[i];
}
extend(o1,o2)
document.write(o1.name);
//混入式继承和原型继承可以组合在一起使用，以对象的方式传递参数，或以对象的方式扩展原型对象的成员。
function extend(o1,o2){
    for(var i in o2)
    o1[i]=o2[i];
}
function Person(option){extend(this, option)}//调用extend函数
Person.prototype.extend=function(obj){extend(this, obj);}
Person.prototype.extend({//调用原型方法
    sayhi:function(){document.write('你好，我是'+(this.name||'无名'));}})
var p=new Person({name:"jack"})
p.sayhi();//你好，我是jack
三、静态成员
静态成员是指由构造函数所使用的成员
1、静态成员只能通过 `构造函数`访问，而不能通过对象来访问。
`静态方法中的this`是指构造函数这个函数对象。
2、实例成员只能由 `构造函教创建的对象`所使用的成员
function Person(name){
    var name=name;
    this.sex='男';
    this.sayhello=function(){document.write(name);}
}
Person.age=123;
Person.sayhi=function(){document.write(this.sex+','+this.age);}
Person.sayhi();
var p=new Person('bugtrap');
document.write(p.age);//undefined,123undefined

利用HTML的表单和JavaScript的对象完成表单生成器的练习。
//1、定义表单项存储格式 姓名:<input type='text' name='user'>,如
{text:'姓名:'//提示文本
tag:'input',//标签名
attr: {type:'text',name:'user')//标签属性
option:null//选项}
//2、保存所有的表单对象利用一个数组保存所有的表单对象var data=[{},{},{},{},{},{}];
//3、编写表单生成器
    1、创建一个构造函数，他包含一个成员，该成员表示要创建的表单项
function FormBuilder(data)
    this.data=data;
    2、为构造函数的原型对象添加一个create()方法，该方法用于生成表单项的html代码。
FormBuilder.prototype.create=function(){
    var html='';
    for(var i in data)
        html+='<tr>'+toHTML(data[i])+'</tr>';
    return'</form><table>'+html+'</form></table>';
}
function toHTML(item){
    var html='<th>'+item.text+'</th><td>';
    if(item.tag=='input')
        return html+inputHTML(item)+'</td>'
    else
        return html+textareaHTML(item)+'</td>';
    return html;
}
//4、将html字符串嵌入页面中
var formbuild=new FormBuilder(data);
document.write(formbuild.create());
```

## BOM（Brower Object Model）指的是浏览器对象模型

```javascript
窗口对象（window)：代表当前打开的浏览器窗口，定义在全局作用域中的变量、函数以及JavaScript中的内置函数都 `可以被window对象调用`。
    指定窗口：窗口名.属性
             窗口名.方法（参数群）
    返回创建该窗口的窗口：opener.属性
                    opener.方法（参数群）
    当前窗口：self.属性
            self.方法（参数群）
    属性
        name窗口的名字。
        closed判断窗口是否已经被关闭，返回布尔值。
        document包含当前文档的信息，(该属性本身是对象)。
        history当前窗口最近浏览过的网页(该属性本身是对象)。
        location窗口所显示文档的完整URL(该属性本身是对象)
        length窗口内的框架个数。
        opener代表使用open打开当前窗口的脚本所在的窗口。
        self代表当前窗口。
        top代表当前框架的最顶层窗口。
        parent代表当前窗口的父窗口。
        弹出对话框
            alert()：显示带有一段消息和确认按钮的对话框。
            prompt()：显示可提示用户输入的对话框。
            confirm()：显示带有一段消息以及确认按钮和取消按钮的对话框
    方法
        open( URL, name, specs,replace ) 打开一个新窗口
        URL：指定页面的url，如果没有指定，则打开一个新的空白窗口。
        name可选值：
        _blank: URL加载到一个新的窗口
        _parent: URL加载到父框架
        _self: URL替换当前页面
        _top: URL替换任何可加载的框架集
        name: 窗口名称
        replace参数
            值为true时，表示替换浏览历史中的当前条目。
            值为false时（默认值），表示在浏览历史中创建新的条目。
        close() 关闭窗口

    定时器：
    setTimeout(function () {
        scrollBy(10,20)
    }, 1000);
    clearTimeout();
    setInterval(function () {
        scrollBy(10,20)
    }, 1000);
    clearInterval();

文档对象（document)：代表当前打开窗口中的文档
```

![window](./img/window.png)

```js
位置对象（location)：代表特定窗口的URL信息
    location.assign(网址)//载入新的文档，可以退回到旧网页
    location.replace('https://www.baidu.com/')//不可退回
    location.reload()//重新加载(刷新)当前的网页（true为从服务器刷新）
历史对象（history)：代表当前打开窗口的前进后退记录
    history.go(0)//刷新
    history.forward() / history.go(1)//前进
    history.back() / history.go(-1)//后退
浏览器对象（navigator)：管理浏览器基本信息
    属性和方法
        appCodeName 浏览器的内部名称
        appName 浏览器的名称
        appVersion 浏览器的平台和版本信息
        cookieEnabled 浏览器是否启用cookie的布尔值
        platform 浏览器的操作系统平台
        userAgent 它包含在客户端向服务器发送的请求的头字符串中，用于识别用户
        javaEnabled() 是否在浏览器中启用Java
屏幕对象（screen）屏幕相关的属性信息
    属性
        height 整个屏幕的最大高度
        width 整个屏幕的最大宽度
        availHeight 浏览器窗口在屏幕上可占用的最大垂直空间
        availWidth 浏览器窗口在屏幕上可占用的最大水平空间
        colorWidth 屏幕的颜色深度
        pixelDepth 屏幕的位深度/色彩浓度
```
