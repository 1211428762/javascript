# React学习

源于facebook,于2013年发布

1. 什么是**模块化**:从**代码**角度将可复用代码抽离出来(如函数),以便下次使用
2. 什么是**组件化**:从**UI界面**角度将可复用的UI组件(如轮播)封装,使用时调用即可

**ReactNative**面向移动端开发,使用面比较广,语法基于React,

Vue的**weex**也是面向移动端,但属于阿里内部框架

React中一切行为,结构,样式,均由JS控制,ES6+语法要求高

## React核心概念

真实DOM:页面上的元素,浏览器提供的操作api

#### **虚拟DOM的原理**

程序员建立新旧DOM树,进行数据对比,实现按需更新,因为无法直接获取DOM数,需要模拟

用JS对象模拟DOM嵌套关系,寻找发生变化的元素,实现局部更新

例子:

```
<div id="word" title="这是div">哈哈哈
<p>这是段落</p>
</div>

var div={
	tagName:"div",
	attrs:{
	id:"word",
	title:"这是div",
	childrens:[
	"哈哈哈",
	{
		tagName:"p",
		attrs:{},
		childrens:["这是段落"]
	}
	]
	}
}
//程序员通过模拟DOM树,新旧对象对比属性差异,获取变化的元素,进行按需渲染
```

#### diff算法

1. **tree diff**: 新旧dom树,逐层对比,整棵DOM树逐层对比完毕,找到按需更新的元素
2. **component diff**: 进行tree diff 时,每层组件级别的对比,叫做Component diff
   - 如果组件类型相同,则进行element diff
   - 不同,则删除旧组件,创建新组件
3. **element diff** :进行元素级别的diff

## React语法

**JSX**语法

需要安装babel插件

```jsx
var div=<div className="ele">这是div</div>
```

jsx执行速度快,编译为js代码,

类型安全,编译过程出错,就不能编译

必须要有根节点

普通元素要小些,大写默认为组件

prop属性永远是只读

{在这里写js表达式,或者变量}

**创建组件**

构造函数创建组件,叫 无状态组件,无state属性

没有私有数据,生命周期

```jsx
function Hello(prop){
	return <div>{prop}</div>
}
ReactDom.render(<div>213<Hello name={prop.name}></Hello></div>,document.getElementById("app"))
```

使用Class关键字创建组件,有状态组件,有state属性

有私有数据,生命周期	

```jsx
// class定义组件
class Hello extends React.Component {
    // 自己的私有数据
    constructor() {
        super() //必须先调用一次super,才能使用this
        // 类似vue的data
        this.state = {
            msg: "React 类定义组件",
            list: [
                {
                    id: 1,
                    name: "张三"
                },
                {
                    id: 2,
                    name: "李四"
                },
                {
                    id: 3,
                    name: "王五"
                },
            ]
        }
    }
    render() {

        return <div>
            类定义的组件 --{this.state.msg}--
        {this.props.name}
            {this.state.list.map(item =>  <Son  key={item.id}  {...item} />)}
          
        </div>
    }
}
```

**CSS语法**

:global(.class){

}

样式不会被模块化,即全局样式,样式最好使用scss,less

建立组件样式文件时,

```jsx
 // filename.module.css文件名
import cssobj from "@/css/filename.module.css"

//使用时
<div className={cssobj.box}></div>
```

**箭头函数的this永远指向他外界的this**

**点击事件**

点击事件触发箭头函数,箭头函数触发绑定的内部事件

```jsx
import React from "react";

export default class Click extends React.Component {

    constructor() {
        super()
        this.state = {
            msg: "hello react"
        }
    }
    render() {
        return <div>
            <button onClick={() => { this.clickEvent(2) }}>
                按钮
            </button>
            <p>{this.state.msg}</p>
        </div>
    }
    clickEvent(d) {
        console.log(d); //2
        this.setState({msg:"click react"+d},function(){
            console.log(this.state.msg)
        })//这个方法是异步的,如果想要操作修改完的的值,可以加个回调函数
   //     this.state.msg="click react" //修改页面上的值,这种方法不行
    }
}
```

**实现双向绑定**

原理是在input绑定onChange事件,获取当前value值,调用this.setState({msg:newVal}).实现

```jsx
import React from "react"
// 实现双向绑定
export default class Vmodel extends React.Component{
    constructor(){
        super()
        this.state={
            msg:123
        }
        this.insert=React.createRef()
    }
    componentDidMount(){
        console.log(this.insert);
    }
    render(){
        return <div>
        <input type="text"  ref={this.insert} onChange={(e)=>this.change(e)} value={this.state.msg}/><p>{this.state.msg}</p>
    </div>
    }
    change(e){
        console.log(this.refs);
        var newVal=e.target.value
        this.setState({msg:newVal})
    }
}
```

## React项目文件结构

![image-20200828110346047](D:\javascript\mulu.png)

public 用于放静态文件

manifest 用于将页面变成桌面快捷方式,里面有路径,图标

robots 用于防止爬虫,添加爬虫规则

src 放开发文件目录

​		index.js引导页

## 组件传值

主要思路就是子组件绑定事件, 触发事件A,传递给父组件.父组件引入子组件时,在props绑定了事件B, A-->B 实现子组件调用父组件的方法,进行修改

```jsx
import React from 'react';
import ReactDOM from 'react-dom';
// 子组件
class Son extends React.Component {
  constructor() {
    super()
    this.state = {
      child: "子组件的数据"
    }
  }
  render() {
    return (
      <div>
          {/* 子组件触发点击事件 */}
        <button onClick={() => this.change()}>传递</button>
         {/* 可以简化,无需在定义函数 <button onClick={() =>this.props.deliver(this.state.child)}>传递</button>        */}
        <p>{this.props.msg}</p>
      </div>
    )
  }
  change() {
    //   寻找父级调用子组件时绑定的事件
    // 子组件 触发事件A(只触发事件,没有操作) -->触发父组件的事件B(实际操作)
    this.props.deliver(this.state.child)
  }
}

export default class Father extends React.Component {
  constructor() {
    super()
    this.state = {
      msg: "父组件的数据"
    }
  }
  render() {
    return (
      <div>
        <p>{this.state.msg}</p>
        {/* 显示父组件传递的数据 ,以及绑定的方法*/}
        <Son msg={this.state.msg} deliver={(data) => this.deliver(data)}> </Son>
      </div>
    )
  }
  // 子组件调用父组件的方法
  deliver(data) {
    this.setState({ msg: data })
  }
}

ReactDOM.render(
  <Father />
  ,
  document.getElementById('root')
);
```

## React事件

事件内放函数

```jsx
onClick={(e)=>this.fun(e,param)}

fun(e,param){
	e.preventDefault()//阻止原生事件
}
```

