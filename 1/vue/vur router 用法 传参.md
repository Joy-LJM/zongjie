### vue router
- 如何使用vue-router
  - 1、在router文件夹下创建router.js；引入VueRouter模块，使用Vue.use(VueRouter);再使用new VueRouter()创建路由router，引入需要配置路由的组件，并抛出
  - 2、在routes配置路由映射表：配置path信息和要渲染的组件
  - 3、在maxin.js入口文件引入并注册使用router模块，

- 关键组件
  - <router-link>作用是改变地址栏的地址，to是要跳转的地址
  - <router-view>是用来渲染组件的容器，根据路由映射表中path信息对应的组件会渲染在这里

- 路由相关对象$router和$route（操作路由地址和获取路由信息）
  - this.$router是路由操作对象，用来操作路由地址
  - this.$route是路由信息对象，里面存放了路由信息，包括传过来的数据

- 路由传参和接收的几种类型写法
  - 类似于get的格式：通过path写路径，query传数据，通过this.$route.query获取数据
    - this.$router.push({
    	path: '/details',
    	query: { id:3 }
    	})
    - this.$route.query.id =>获取路由信息
  - 类似于post的格式：通过name写组件，params传数据，通过this.$route.params获取数据
    - this.$router.push({
    	name: 'Details',
    	params: { id: 2 }
    })
    - this.$route.params.id =>获取路由信息

  - 动态路由的传参，例如在点击去到商品详情是会把商品id带过去
    - 第一种：路由配置path动态参数，this.$router.push中携带path路径和动态数据，再通过this.$route.params.id 来获取数据
      - {
      		path: '/details/:id', // 路由配置表path中冒号:id
      		name: 'Details',
      		component: () => import(/* webpackChunkName: "box" */ '../views/Details.vue')
      	},
      - this.$router.push('/details/'+goodsId) 
      		this.$route.params.id  接收参数
    - 第二种：路由配置中添加props:true，表示在组件中可以通过props来接收参数
      - {
         path: '/details/:id', // 路由配置表path中冒号:id
         	name: 'Details',
         	props: true,
         	component: () => import(/* webpackChunkName: "box" */ '../views/Details.vue')
         }
      - 动态路由的参数可以在Details组件中直接通过props接收



1. 怎么定义 vue-router 的动态路由? 怎么获取传过来的值？

答：在path属性加上/: id，通过$route.params.id 来获取

27$router与$route的区别

答：$router是VueRouter的实例，可以使用里面的方法。使用$router.push方法。$router.to()

$route为当前router跳转对象。里面可以获取当前路由的name,path,query,parmas等属性。

28vue-router 有哪几种导航钩子?（当路由发生变化，导航守卫通过跳转或者取消的方式来进行守卫导航）

答：3种。全局导航守卫，路由导航守卫，组件导航守卫，

第一种：是全局导航钩子：router.beforeEach(to,from,next)，作用：跳转前进行判断拦截

To为要跳到的页面，from为来自的页面，next（）回调函数。

第二种：单独路由独享组件router.beforeEnter(to,from,next)

第三种：组件内的钩子。router.beforerRouterEnter(to,from,next)

​                      router.beforerRouterupdate(to,from,next)

​                       router.beforerRouterupLeave(to,from,next)

 

完整的导航流程：组件内的 router.beforerRouterupLeave  ==>全局的router.beforeEach===>

组件内的更新  router.beforerRouterupdate ===>路由的导航 router.beforeEnter  ==>组件内的  router.beforerRouterEnter