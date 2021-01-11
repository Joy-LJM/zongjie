### vuex 数据管理 状态管理（数据缓存，和多组件的数据共享）

- vuex和localstorage的区别：
  - vuex存储的数据在内存中,localStorage的数据以文件形式存储在本地
  - 当我们刷新页面时，vuex的数据将会丢失，localStorage的数据不会丢失
  - vuex用于多组件之间共享数据，localStorage用于多页面之间共享数据

- 如何使用vuex
  - 1、在store文件夹下创建index.js;引入Vuex模块；使用Vue.use(Vuex);再使用new Vuex.Store()创建一个仓库实例对象，并抛出
  - 2、在main.js入口文件引入并注册使用store模块，所以的子组件都可以使用store
  - 3、store配置项里面有五个对象：
    管理状态的state
    管理改变状态方法的mutations
    管理异步操作的actions
    全局的计算属性getters,类似组件中的计算属性
    用于拆分数据模块的modules

  - mutations:存放了操作state数据的方法（同步修改）
    - 在组件中通过this.$store.commit(mutations中的方法，数据)来修改state
  mutions与actions都能修改状态，官方推荐用mutations来修改，可以在devtools插件中查看修改记录，
  acrions修改状态不能再detvools中查看修改记录

  - actions修改state状态是间接修改（异步行为，）
    - 在组件中通过this.$store.dispatch()来调用actions中的方法
    - action函数会接收到一个和store有相同的属性和方法的context
    - 而在actions中定义的方法会通过store.commit()来触发mutations中定义好的函数，从而修改state中的数据

  - getters里面定义的函数可以对state的数据做一些处理，
    - 在组件中使用this.$store.getters.fn来获取处理后的数据

  - 给子store模块添加命名空间namespace:true后，组件要访问store中这个子数据模块，就需要加上子模块名

  ## vuex辅助函数
- vuex辅助函数作用是方便操作数据
- vuex辅助函数不是必须的！！
- 如果你不觉得之前的操作麻烦，你完全可以不用辅助函数！

1. mapState
  - mapState放在组件的计算属性中，映射到组件的计算属性中
  - ...mapState([])只能获取外层state 
  - ...mapState({})外层和模块内的state都可以获取
  - 访问数据：this.计算属性名
2. mapGetters
  - mapGetters放在组件的计算属性中，映射到组件的计算属性中
  - ...mapGetters([]) 外层和模块中的getters都可以获取
  - ...mapGetters({}) 外层和模块中的getters都可以获取，需要改名时用
  - 访问数据：this.计算属性名

3. mapMutations
  - mapMutations放在组件的 methods 中映射
  - mapMutations映射mutations中的方法到methods中
  - ...mapMutations([])
  - ...mapMutations({}) 需要改名时用
4. mapActions
  - mapActions放在组件的 methods 中映射
  - mapActions映射actions中的方法到methods中
  - ...mapActions([])
  - ...mapActions({}) 需要改名时用