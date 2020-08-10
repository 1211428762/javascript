## vuex学习心得

cnpm i vuex --save 安装vuex

main.js 引入 

import Vuex from "vuex"

Vue.use(Vuex)

```js
const app = {
    // 全局状态
    state: {
        count: 0
    },
    getters: {
        //对state进行包装处理,需要return
        myCount(state) {
            return `当前值是${state.count}`
        }
    },
    mutations: {
        // 写状态逻辑
        increment(state, n) {
            state.count += n
        },
        // 传递自定义参数
        decrement(state, n) {
            state.count -= n
        }

    },
    actions: {
        // 数据业务逻辑
        myIncrease(content, obj) {
            content.commit("increment", 2)
                // 调用mutations的方法
            console.log(obj);
        },
        myDecrease(content) {
            content.commit("decrement", 3)
                // 传入mutation的自定义参数
        },
    }
}
export default app
```

挂载到Vue实例上

```js
new Vue({
  el: '#app',
  router,
  components: { App },
  template: '<App/>',
  store
})
```

在APP.vue

```js
import {mapState} from "vuex"
export default {
  name: "App",
  data() {
    return {};
  },
  computed:{
    ...mapState(["count"])
  },
  //导入对应的方法
  },
};

```

在应用的页面

```js
import { mapMutations, mapActions } from "vuex";
export default {
  name: "HelloWorld",
  data() {
    return {
      msg: "Welcome to Your Vue.js App",
    };
  },
  methods: {
      //引入方法
    ...mapMutations(["increment", "decrement"]),
    ...mapActions(["myIncrease", "myDecrease"]),
    increment() {
      // this.$store.commit("increment");
        //commit 类似与call
      this.myIncrease();
      console.log(this.myIncrease);
    },
    decrement() {
      // this.$store.commit("decrement");
      this.myDecrease();
    },
  },
};
```

一般来说,会新建一个vuex专门的状态管理文件

index.js负责引入其他状态管理模块

```js
import Vue from 'vue'
import Vuex from "vuex"
import app from "./app"
import user from "./user"
Vue.use(Vuex);
const store = new Vuex.Store({
    modules: {
        app,
        user
    }
})
export default store
```

...mapState 是store里state的映射

...mapState(['num'])=>state[num]

...mapGetters是store里getters的映射

...mapGetters(['num'])=>getNum,

两者都写在computed里面

...mapMutations和...mapActions写在methods里面

#### MUTATION_TYPE

将mutations的方法全部 放到MUTATIONS_TYPE里

```js
export const MUTATIONS_TYPE = {
    INCREASE: "increase",
    DECREASE: "decrease"
}
export default {

    // 加一的函数
    [MUTATIONS_TYPE.INCREASE](state, payload) {
        state.num += payload ? payload : 1
    },
    [MUTATIONS_TYPE.DECREASE](state) {
        state.num--
    }

}
```

mutations.js

```
export default {

    // 加一的函数
    increase(state, payload) {
        state.num += payload ? payload : 1
    },
    decrease(state) {
        state.num--
    }

}
```

调用

import { MUTATIONS_TYPE } from "../store/mutations_type";

 ...mapMutations([MUTATIONS_TYPE.INCREASE]),

如果要获取stroe文件下组件的值,在调用的组件内加上computed属性返回即可

