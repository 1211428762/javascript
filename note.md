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

垃圾回收

1.标记清除(常用)

2.引用技术(不常用)