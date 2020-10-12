## freemarker

#### 布尔类型输出

```js
${boo?c}    //需要加?c
${boo?string} 
${boo?string("好","不好")} //将布尔值进行转义
${boo?then("好","不好")} //将布尔值进行转n
```

#### 日期类型输出

```
${date?date}    //输出时间
${boo?time} 
${boo?datetime("好","不好")} //

```

