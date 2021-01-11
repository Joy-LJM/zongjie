### mobx 定义数据store
- mobx6版本提供了三个比较重要中API用来存储和更新状态：observable、action和makeObservable

- observable 是可观察的，用来定义可共享的数据，相当于vuex中的state

- action 相当于vuex中的mutations+actions，用来定义改变state的方法

- 写法示例：mobx6版本只支持es6的类的写法
```
export default class TodoStore {
  constructor() {
    makeObservable(this,{ // 对数据和方法进行配置
      list: observable,
      addTodo: action
    })
  }
  addTodo(payload) {
    this.list.push({
      id: Date.now()
      task: payload
    })
  }
}
```
- 写法示例：mobx5版本要使用修饰器的语法
```
export default class TodoStore {
  @observable list = [
    { id: Date.now(),task: payload }
    ]
  @action addTodo(payload) {
    this.list.push({
      id: Date.now()
      task: payload
    })
  }
}
```
### 引入 mobx-react 来使用数据
- 在app.js中引入Provider和store，用provider标签包裹组件和注册store

```
import { Provider } from 'mobx-react'
import store from '@/store'
<Provider store={store}>

</Provider>
```
- 在需要使用store中的组件引入observer和inject，
- 使用@inject('store')注入刚刚注册的store，使用@observer修饰当前组件
【也可以在抛出组件的时候用高阶函数的写法：export default inject('store')(observer(TodoList))】
- 通过组件的props.store就可以访问到定义的数据和方法了