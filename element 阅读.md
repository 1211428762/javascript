# element 阅读

## slot妙用

#### 为什么要用slot? 	

[官方说明](https://cn.vuejs.org/v2/guide/components-slots.html)

一般运用组件,不会在标签内写文字,写了也不会渲染,让组件内容生效需要使用slot

`<mypart> 文字 </mypart>`

```vue
<navigation-link url="/profile">
  {{ url }}
  <!--
  `url` 是 undefined，因为其 (指该插槽的) 内容是
  _传递给_ <navigation-link> 的而不是
  在 <navigation-link> 组件*内部*定义的。
这对标签内部的内容全部以子组件作用域为准
  -->
</navigation-link>
```



**父级模板里的所有内容都是在父级作用域中编译的；子模板里的所有内容都是在子作用域中编译的。**

#### slot默认内容

```vue
//子组件内
<button>
  <slot>Submit</slot>
</button>
//父组件

<Btn></Btn>   ==><button> Submit</button>  //默认
<Btn>test</Btn>    ==><button> test</button>  //若有会覆盖
```

#### 多个插槽时需要name

```vue
<base-layout>
    <template v-slot:header>         // 子组件<slot name="header"></slot>
    <h1>Here might be a page title</h1>  
  </template>

  <template v-slot:default>
    <p>A paragraph for the main content.</p>
    <p>And another one.</p>
  </template>

  <template  #footer>    v-slot:==>#(缩写)
    <p>Here's some contact info</p>
  </template>

</base-layout>
```

#### 插值slot

```vue
<todo-list :todos="todos">
  <template #todo="{ todo }">    //建议用这种解构赋值的写法,todo
    <span v-if="todo.isComplete">✓</span>  //接受prop传到子组件的todo数据
    {{ todo.text }}
  </template>
</todo-list>

```

