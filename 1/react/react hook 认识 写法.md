### hook
- hook是跟函数式组件一起使用的；
  - 对于函数式组件，它只接受props传过来的数据，并没有而且一般也不需要有state数据。
  - 但是如果需要在不改写成class类组件的情况下要使用state和其它类组件的特性，就需要使用hook
- hook本质上就是一套api，可以让函数式组件拥有类组件相似的特征：拥有state状态、生命周期、ref等特性
- 
useState 用法：const[msg, setMsg] = useState('初始化数据')
-  用来引入状态的，类组件修改state用this.setstate（）方法，但是用了usestate，就不需要用this啦，直接用set（）方法
-
 useEfffect(fn,[])完整语法：（`useEffect` Hook 看做 `componentDidMount`，`componentDidUpdate` 和 `componentWillUnmount` 这三个函数的组合）
  - 其中[]里面可以写要监控的数据，这个数据变化时才启动当前这个useEffect，类似 componentDidUpdate() 的作用
  - 第二个参数不传的时候表示这个useEffect里面的代码在每次状态改变的时候都会执行，****
  - 第二个参数[]传空数组时，表示这个useEffect里面的代码只会在初始化的时候执行一次，类似 componentDidMount() 的功能

  在useEffect 在第一个函数中返回一个函数是 （在组件销毁时被调用和组件更新前被调用返回的函数）

- 其他hook:这两个不了解

  - useContext允许订阅React上下文而不引入嵌套(减少组件的层级关系，层级之间的传值)
  function Example() {
  const locale = useContext(LocaleContext);
  const theme = useContext(ThemeContext);
  }


  -  useReducer 可以让你通过 reducer 来管理组件本地的复杂 state
  function Todos() {
  const [todos, dispatch] = useReducer(reducer，initialState);
  1.要初始化一下initialState
  2.定义一下reducer，定义一下里面的actions （type,payload）


  usecallback 与useMero(作为优化，当数据没有发生变化，就不需要执行函数)
```
useEffect(()=>{
  // 类似 componentDidMount() 的功能
  // 开启定时器、调接口、开启长连接
  timer = setInterval(()=>{
      console.log(1)
  }, 1000)
  return ()=>{
    // 类似 componentWillUnmount()
    // 关闭定时器、关闭长连接
    clearInterval(timer)
  }
},[count])
// [count]，类似 componentDidUpdate() 的作用
```