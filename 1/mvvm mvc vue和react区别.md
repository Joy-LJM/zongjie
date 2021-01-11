### MVVM、MVC的区别
- MVC开发模式分三个部分，model数据模型、view视图、controller控制器，
  - 传统的mvc架构是通过控制器去更新模型，
  - 视图从模型中获取数据去渲染，
  - 用户的输入是通过控制器来更新模型，并通知视图重新获取数据来更新；
  - 控制器承担了很大部分任务

- MVVM架构引入了视图模型viewmodel的概念，
  - 视图模型负责监听model中的数据改变，并且控制view的更新和处理用户的交互
  - 在mvvm架构中，数据模型model和视图view是独立对,它们不能直接进行通信,而是要通过视图模型viewmodel来执行

- 两者的区别,就是controller和viewmodel的区别,mvvm摆脱了更多操作DOM的环节,开发中只需要关注业务逻辑和数据维护即可，不需要自己操作DOM

### vue 和 react 的比较 {都是做组件话开发的,主要是设计思路不同}
- 数据流:两个都是单向数据传递{例如:数据是从父组件传给子组件,子组件不能直接修改父组件对状态}
  - react是单向绑定
    - react整体是函数式的思想,状态和逻辑通过参数传入
    - react在setState之后会重新走渲染的流程,如果shouldComponentUpdate返回的是true,就继续渲染,如果返回了false,就不会重新渲染
  - vue是双向绑定
    - vue的思想是数据双向绑定的响应式,通过对每一个属性建立watcher来监听;当属性变化对时候,响应式对更新对应对虚拟dom
  - 总结1:react的性能优化需要手动去做,而vue的性能优化是自动的
  - 总结2:vue的响应机制也会带来问题:当state特别多的时候,watcher也会很多,导致卡顿,所以大型应用(状态特别多)一般用react,更加可控

- 书写思路不同
  - react的思路是all in js,通过js来生成html,所以设计了jsx,还可以通过js来定义css样式对象
  - vue是把html,css,js组合到一起;vue有单文件组件,可以把html,css,js写到一个文件中,用模版引擎来处理

- 扩展:react通过高阶组件来扩展,而vue需要通过mixins来扩展(这个不太懂,没处理过)

- 方便性:react做的事情很少,很多功能都是社区来做;而vue很多东西都是内置的,写起来更方便
  - 例如redux的combineReducer对应vuex的modules
  - redux的reducer是返回一个全新的state,vuex的mutation是直接改变原始数据

