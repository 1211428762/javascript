## lua语法

```lua
print("hello world") 输出语句

b=10

print(b)  --  =>10

 --单行注释  
--[[多行注释]]
--删除变量 
b=nil 
--for循环
for var=exp1,exp2,exp3 do  
    <执行体>  
end  
如果exp2是函数只执行函数一次,exp3可选
-------
tab1 = { key1 = "val1", key2 = "val2", "val3" }
for k, v in pairs(tab1) do
    print(k .. " - " .. v)
end
-------
--循环 10 -->1 每次递增加 -1
for i=10,1,-1 do
    print(i)
end
----
--[[boolean 类型只有两个可选值：true（真） 和 false（假），Lua 把 false 和 nil 看作是 false，其他的都为 true，数字 0 也是 true]]
--if else
if false or nil then
    print("至少有一个是 true")
else
    print("false 和 nil 都为 false")
end
--lua的 算术操作"+ - * /"会进行隐式转换再加求和
--连接符 是  ..  类似js的+
--  print(#"hello")	 ==> 5计算字符串长度
--lua的数组索引从1开始
--table数据类型,类似js对象
--local 定义局部变量,不加关键字就是全局变量
--交换赋值  x,y=y,x  
--同时赋值 x,y=10,100   变量赋值必须要依个赋值
-- a,b,c=1 此时只有a=1. b c 均等于nil
--循环
a=10
while( a < 20 )
do
   print("a 的值为:", a)
   a = a+1
end
-----
-- select(n,...)返回 第n个值和n以后的值
--~=不等于
-- 与 and,或or,非 not
```

# lua-resty-template

编译模版

```lua
local template = require "resty.template"
template.render("view.html", {
  title   = "Testing lua-resty-template",
  message = "Hello, World!",
  names   = { "James", "Jack", "Anne" },
  jquery  = '<script src="js/jquery.min.js"></script>' 
})
```

html内容

```lua
{(header.html)}   -- 加载头部html模版
<h1>{{message}}</h1>
<ul>
{% for _, name in ipairs(names) do %}  --执行lua代码,渲染li
    <li>{{name}}</li>
{% end %}
</ul>
{*jquery*}   --加载jq脚本, 加*用于解析标签
{(footer.html)}
```

