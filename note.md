# 第一章

## 1.1 js组成

|                  |        JavaScript        |                                |
| ---------------- | :----------------------: | ------------------------------ |
| ECMAscipt        |           BOM            | DOM                            |
| 提供核心语言功能 | 与浏览器交互的方法与接口 | 访问和操作网页内容的方法和接口 |

# 第二章

## 2.1 script标签

- `<srcipt async="async"> 立即下载脚本,不妨碍页面的其他操作,只对外部脚本有效.`

- `<srcipt defer="defer"> 在<html>后面解析,延迟解析,只对外部脚本有效.`

- <script type="text/javascript" src="test.js"></script>

<script></script>加了src属性后即便在标签内写脚本也不会解析.放在</body>前面,利用页面快速加载

<noscipt>只有不支持脚本或者禁用脚本时才显示</noscript>

# 第三章

## 3.1

js中变量,函数,操作符均区分大小写

标识符的开头由 **字母(_或者$)**+字母/数字/下划线/$

**注释**

//单行

/*

多行注释

*/

**变量**

 test=1 全局变量

function fun(){

var test=1 局部变量

}

## 3.2 **数据类型**

undefined 声明但未初始化

null 空对象指针 (typeof 返回object)     null==undefined(true) 

boolean 是否 

number 数字 包含所有类型的数字

string 字符

object 对象 var obj=new object()  ; 

  constructor：构造函数

  hasOwnProperty(propertyName)：检查给定的属性在当前对象中是否存在

  isPrototypeOf(object)：检查传入的对象是否是传入对象的原型

  propertyIsEnumerable(propertyName)：检查给定的属性是否能够使用for-in语句来枚举，与hasOwnProperty一样，给定的属性名必须以字符串的形式指定

  toLocalString()：返回对象的字符串表示，与执行环境的地区对应

  toString()：返回对象的字符串表示

  valueOf()：返回对象的字符串、数值或布尔值表示。通常与toString返回相同

**操作符**

"," 逗号用于声明多个变量.除此以外逗号可以用于赋值,总是 返回表达式的最后的一项

var num =(0,2,3,41,4) 值 是4   ,返回最后一项

## 3.3 语句

### **if语句**

if(condition){

xxx

}else{

yyy

}

### **do-while 常用在代码在循环中最少执行一次的情况**

var i=0

do{

i++

}

while(i>10)

alert(i)

### **while 是前测试循环语句,循环体执行前必须先满足前置条件**

var i=0 

while(i<10){

i++

alert(i)

}

### **for循环与while类似,上面的循环转换成for循环如下**

for(var i=0;i++;i<10){

alert(i)

}

### 不建议使用with语句

## 3.4函数

函数的参数可以看作成数组,可以通过arguments对象访问,

fun(){

alert(arguments.length,arguments[0])

}

fun(name,12)

返回 2(长度),name(第一个参数元素)

函数没有重载只有后者覆盖前者

# 第四章

## 4.1基本类型和引用类型 

基本类型指五大基本数据类型  (不能给它加属性)

引用类型的值保存在内存中的对象

typeof确定是哪种基本类型

instanceof 确定是哪种引用类型

arr instanceof Array  arr是Array吗

所有引用类型都是对象,基本类型都不是对象

一对大括号是一个作用域

symbol类型定义一个独一无二的标识符,可传入字符串作为参数用来对该对象进行描述

let sym=Symbol("des"),可用来调试代码

垃圾回收

1.标记清除(常用)

2.引用技术(不常用)

# 第五章

### 5.1object类型

创建实例

(1) var obj =new  Object()

​     obj.name="joy"

(2) var obj ={     (常用)

name:"joy"

}

### 5.2Array类型

var arr=Array(3)  长度为3   

var arr=Array("jot")  数组只包含 "jot"  ==> var arr=["jot"]

##### 判断数组

Array.isArray(arr) ==>布尔

var color=["red","blue"]

color.valueOf()  ==>返回数组

color.toString()==>返回字符串

color.join(",") ==>转换字符串

##### 操作数组

push尾部添加

pop尾部删除

shift头部删除

unshift头部添加

reverse数组倒序

sort数组按首字母ascII码升序排列

arr.sort((a,b)=>a-b) 数组升序排列

slice(a,b) a是数组起始位置 b是结尾 ,并不会影响原数组  (切割数组)

如参数有负数则把两个参数加上数组长度再进行判断

splice

删除splice(0,2)删除数组索引从0开始的2个元素

插入splice(2,0,"ab","cd")从数组索引2开始插入两个元素

替换splice(2,1,"ab","cd")从数组索引2开始删除一个元素再添加两个元素

splice(n,m,c) 

n起始位置,m删除项数,c替换元素

var arr =[1,2,34,5,2]

arr.indexOf(2) ==>1  返回第一次出现的索引

##### 数组迭代

every（）数组元素给定函数（或者判断条件），数组元素都返回true则返回true
filter（）数组元素给定函数（或者判断条件） ，将返回true的元素组成数组
forEach（）数组元素给定函数，没有返回值
map（）数组元素给定函数，返回每次函数调用的结果组成的数组
some（）数组元素给定函数，数组元素对函数任意项返回true，则返回true
some和every类似||和&&
以上都不修改数组包含的值

### 5.3Date类型

创建日期对象
var time=new Date（）
根据特定日期创建日期对象
Date.parse()和 Date.UTC()
var newTime=new Date（"May 20"）可以省略 Date.parse("May 20")
var newTime=new Date（Date.UTC(2020,1(月份实际显示要加一)，30,15,45,55 )）
参数分别是年月日时分秒
var date =new Date（2020,1,2）
console.log(valueOf(date))返回日期的毫秒数可以用来比较

### 5.4RegExp类型

var reg=/pattern/flags    pattern可以是任何简单或复杂的正则表达式, flags表示匹配模式

/g全局匹配

/i不区分大小写

/m多行匹配

^ xx开头

$ xx结尾

[a-zA-Z] 包含字母不区分大小写

[0-9]匹配数字  /\d/

{n,m}至少匹配n次最多m次

判断方法

test()判断是否匹配

exec()返回字符串

match()找到检索指定的值

### 函数类型

函数可以作为参数传递

fun call(fun1,param){

return fun1(param)

}

fun1(param){

return param+10

}

call(fun1,10)  =>20

函数没有重载,只会覆盖前者

### 函数内部属性

arguments是一个类数组对象,包含函数内的所有参数

this 指针全局函数指向windows

局部函数调用时指向触发事件对象

##### boolean类型

创建boolean对象.调用boolean构造函数传入true或false

var boo=new Boolean(true)

##### number类型

var num=new Number(1)

num.toFixed(2) 保留两位小数

##### string类型

var str1=new String("hello")

console.log(str.charAt(1)) 返回 "e"第二个字符

var str2="world"  str1.concat(` ${str2}`)

str1 =>"hello world"

字符串方法

- slice(*start*, *end*)提取字符串的某个部分并在新字符串中返回被提取的部分,接受负数时加上字符串长度再判断
- substring(*start*, *end*)与slice类似但不接受负数
- substr(*start*, *length*)
- indexOf("h") 返回字符串是否包含"h",有则返回索引,没有返回"-1",接受第二个参数时从那个索引开始寻找
- trim()删除前置后缀的空格
- search()返回字符串的匹配项

### 内置对象

global对象

许多方法时global对象的内置方法

encodeURI()常规格式 <=>decodeURI()

encodeURIComponent() 将部分变成%数字组合<=>decodeURIComponent()

eval() 将参数解析并运行返回结果

Math对象

ceil向上取整

floor向下取整

round四舍五入

random取随机数

# 第六章

##### 数据属性

[configurable]表示能否操作.delete可以删除属性

[enumerable]能被for-in遍历

 [writeable]能否修改

[value]表示对象的属性值.默认是undefined

将一个对象设置不可修改

var son={}

Object.defineProperty(son,"name",{

writable:false,

value:"jack"

})

son.name="newName" 不生效

##### 工厂模式

创建一个轻松构建对象的函数

function creator(name,sex,gender){

var obj =new Object()

obj.name=name

obj.sex=sex

obj.gender=gender

obj.say=function(){

alert(this.name)

}

return obj

}

实例化对象

var obj1=creator("张三",20,"male") 无法区分是那个对象的实例,每调用这个构造函数都会创建一个新对象.

##### 构造函数

函数名首字母要大写

function Person(name,sex,gender){

this.name=name

this.sex=sex

this.gender=gender

this.say=function(){

alert(this.name)

}

}

实例化

var person1=new Person("李四",20,"male")

区别:

工厂模式内部创建了对象,需要定义一个原型函数(creator)

构造函数实例化对象时,需要使用new 关键字,没有返回

##### 原型链

js对象都有proto属性指向构造该对象的构造函数原型()

function才有prototype属性,这个属性指向这个函数的

![](C:\Users\yzw\Desktop\20180909114030465.png)

函数的prototype指向该函数的构造函数

函数的_proto_指向 其构造函数的函数原型

Object.prototype.construction===Object 等于本身

##### 原型继承

//  原型继承

let a ={

  x:10,

  cal(z){

​    return this.x+this.y+z

  }

}

let b={

  y:20,

`__proto__:a //继承a的函数`

}

console.log(b.cal(10));

##### 原型链的面向对象

 function Foo(y) {

   this.y=y

 }

 Foo.prototype.x=100

 Foo.prototype.cal=function(z){

   return this.x+this.y+z

 }

 //在构造函数Foo的函数原型上加属性和方法后，以后每次实例化的对象都自带这两个属性和方法

 var b=new Foo(20)

// 此时对象b已经有x 和cal函数了

b.cal(10)

// x=100 y=20 x=10