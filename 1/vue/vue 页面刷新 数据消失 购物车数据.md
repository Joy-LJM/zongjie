### vue页面刷新 数据没有 做购物车时怎么处理
- 例如：通过选中一个商品进入第二个页面展示选中内容的详细信息，这个时候选中的信息保存在vuex
- 在第二个页面通过浏览器刷新，数据清空，购物车中没数据

- 原因：store里的数据是保存在运行内存中的，当页面刷新时，页面会重新加载vue实例，store里面的数据就会被重新赋值

### 处理方法：sessionStorage
- 选择sessionStorage
  - 原因：vue是单页面应用，操作都是在一个页面跳转路由，另一个原因是sessionStorage可以保证打开页面时sessionStorage的数据为空，而如果是localStorage则会读取上一次打开页面的数据

- 方案一：mutation修改state的同时修改sessionStorage对应存储的属性
  - 由于state里的数据是响应式，所以sessionStorage存储也要跟随变化。
  - 这种方法很明显让人觉得怪异，都这样了，那不如直接用sessionStorage来做状态管理
- 方案二：思路：只有在刷新页面时才会丢失state里的数据，可以在点击页面刷新时先将state数据保存到sessionStorage,然后才真正刷新页面
  - beforeunload这个事件在页面刷新时先触发的
  - 可以在app.vue这个入口组件中，添加事件。这样就可以保证每次刷新页面都可以触发
```
window.addEventListener("beforeunload",()=>{
  sessionStorage.setItem("store",JSON.stringify(this.$store.state))
})
```