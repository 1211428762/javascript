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

**数据类型**

undefined 声明但未初始化

null 空对象指针 (typeof 返回object)     null==undefined(true) 

boolean 是否 

number 数字

string 字符

object 对象 var obj=new object()  ; valueOf()返回对象的字符串.数值或布尔值 通常与toString返回值相同

**操作符**

"," 逗号用于声明多个变量.除此以外逗号可以用于赋值,总是 返回表达式的最后的一项

var num =(0,2,3,41,4) 值 是4   ,返回最后一项