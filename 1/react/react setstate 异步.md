### setState 异步 上一个状态state
- setState是作用:用来更新state中的数据

- 异步:它是一个异步的API =>> setState的调用并不会马上引起state的改变

- 是异步原因到猜想:setState在设计的时候弄成异步的有可能是基于这样的考虑，
  - setState改变state中的数据，是绝对有可能会导致DOM的重绘的，
  - 如果调用一次就马上进行一次重绘,那么需要调用多次就会造成不必要的性能损失。
  - 设计成异步的话，就可以将多次调用放入一个队列中，在恰当的时候一次性进行更新，一次性重绘

- 传入函数到场景:
  - 如果此次调用setState改变的新值是跟上一次的state状态有关，可以在setState传入函数 
  - 这个函数的入参prevState是上一次的状态state，这样就可以保证准确获取到上一次到state
  - 也可以使用钩子componentDidUpdate等待更新完成后再赋新值,同样可以保证准确获取到上一次到state


2.1React中constructor是唯一可以初始化state的地方，也可以把它理解成一个钩子函数，该函数最先执行且只执行一次。即直接通过this.state = {}来对state进行初始化，在其他位置需要通过this.setState函数来更新状态。直接修改this.state虽然状态可以改变，但不会触发组件的更新。
   2.2：state的赋值是异步的，如果我们需要获取最新的state值，需要在this.setstate()方法里，添加一个回调函数，在回调函数获取最新值

   
    2.3setState执行后会发生什么：
在调用 setState 函数之后，React 会将传入的参数对象与组件当前的状态合并，然后触发所谓的调和过程（Reconciliation）。经过调和过程，React 会新的状态构建 React 元素树并重新渲染整个 UI 界面。在 React 得到元素树之后，React 会自动计算出新的树与老树的节点差异，然后根据差异对界面进行最小化重渲染。这就保证了按需更新，而不是全部重新渲染。