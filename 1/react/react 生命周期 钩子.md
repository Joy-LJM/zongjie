### 生命周期 
- react生命周期有三个阶段：挂载、更新、卸载

- 挂载阶段常用的三个钩子：
  - constructor：是组件被实例化时调用；用this.state来初始化，而不用this.setstate（）方法
  - getDerivedStateFromProps()  用来实现props和state的同步的
  - render（）负责将模板渲染到页面，返回一段dom结构，一般来说说，当`props`和`state`发生改变时，都会重新出发`render`，需要注意的是，不要在render函数中 修改`props`和`state`，否则会导致死循环！
  - componentDidMount：会在组件挂载后（插入 `DOM` 树中）立即调用。依赖于 DOM 节点的初始化应该放在这里。一般用来在这里发送异步请求，

- 更新阶段两个钩子：
  - shouldComponentUpdate：控制着组件的更新能力，（性能优化的）
    - 当返回false的时候就表示不能更新；返回true的时候可以更新
  - render（）
  - componentDidUpdate：当state发生变化时，DOM重新渲染并更新完成时被调用
    - setState传入函数用来根据上一次状态修改数据的需求也可以用这个钩子来完成

- componentWillUnmoun，当组件销毁时被调用

