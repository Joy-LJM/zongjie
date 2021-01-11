### router
- 引人react-router-dom的
    HashRouter =>包裹app
    NavLink =>生成导航菜单，改变url
    Route =>视图容器，根据path渲染对应的组件
    Switch =>switch包裹所有的route，当有多个相同匹配时，从上到下取最先匹配到的
    Redirect =>重定向



1. react路由常用的一些组件配置项有哪些？

![img](file:///C:\Users\张伟\AppData\Local\Temp\ksohtml6828\wps1.jpg)  

8. reatc路由中Route渲染组件的方法有哪几种？区别是什么？

答：component 每次都会触发组件的对应的生命周期 

  	Render 内联模式渲染 性能会更高， props需要传递到函数内

​	children 会一直渲染 不管匹配模式

