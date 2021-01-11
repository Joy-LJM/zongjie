### vue组件通信到几种方式
组件中的数据有三种形式，自身自定义的data；从父组件接受存放的props；有计算属性的computed
- 父子组件之间的通信
  - 父子组件间数据是单向数据流,父组件通过props给子组件传递数据，子组件不能直接修改props
  - 子组件通过emit发送事件传递数据给父组件，通知父组件修改数据

  - 父组件向子组件传数据写法：在使用子组件绑定上父组件的数据；子组件的props里接收传过来的数据
  - 子组件向父组件传谁写法：
    - 1、给子组件传递数据的事件函数添加内容，用this.$emit()传递自定义事件和数据
    - 2、在父组件的子模板标签添加自定义事件和处理函数fn，这个fn是父组件的函数，里面接可以接收到子组件传过来的数据

- 亲兄弟组件之间的通信
  - 使用共同的父组件来实现数据的传递

  写法:
  - 父组件定义共享的数据，子组件1 通过props来接收父组件的数据；
  	 子组件2 通过this.$emit给父组件传递数据，父组件接收到后更新共享的数据，数据一更新，子组件的props也会跟着更新	

- 跨多层次的组件之间的通信
		- 可以通过事件总线eventbus，也叫中间件来事件通信；
		- 思路:
      - 在全局创建一个空的vue实例，通过vue.$emit()传入可以发送数据的自定义事件和要传递的数据；
      - 再通过vue.$on()传入用来接收数据的自定义事件和接收到的数据

		- 写法：
      - 1、创建一个空的vue实例，在子组件1中发送数据的函数里面用vue.$emit()传入自定义事件和要发送的数据 
      - 2、在子组件2中用vue.$on()传入自定义事件和处理函数，这个处理函数默认接收到的data就是子组件1传过来的数据 
      - 3、$on可以实现监听自定义事件，一般有时不确定何时会触发事件，所有vue.$on一般都是放在mounted或者created钩子中来监听

- 使用vuex 全局状态管理
  - vuex实现了一个单向数据流；在全局中拥有一个store来存放数据
  - 当组件需要更改state中的数据时，必须通过mutation进行，而当异步操作的修改需要从action，但action也是无法直接修改state的，还是需要通过mutation来修改state数据，最后，通过state的变化渲染到视图上

1**props / $emit**（用于父子）

8 **$attrs与 $listeners**   (A组件包含B组件，B组件包含C组件，在C组件中使用v-bind="$attrs"  v-on="$listener"   ，就可以A组件传递的props)

2**$children / $parent**（　**$parent** 可以访问到当前组件的父组件实例，$children 可以访问到当前组件的子组件实例 ，$parent 和 $children 得到的值不一样，**$children 的值是数组，而 $parent 是个对象** ）

3**provide/ reject**（父组件中通过provider来提供变量，然后在子组件中通过inject来注入变量 ，provide 是一个**对象**或返回一个对象的**函数**。inject 是一个**数组**或**对象** ，这里不论子组件嵌套有多深, 只要调用了inject 那么就可以注入provide中的数据，而不局限于只能从当前父组件的props属性中获取数据 ）

4**ref / refs**（用来给元素或者子组件注册引用信息，引用信息会在父组件的$refs对象上）

5**eventBus*（首先要创建一个事件总线，事件机制$on(eventname,数据)监听触发事件，$emit(eventname,数据)触发事件）可以用于父子，兄弟

6**Vuex**

7**localStorage / sessionStorage**



常见使用场景可以分为三类：

父子通信：
父向子传递数据是通过 props，子向父是通过 events（$emit）；通过父链 / 子链也可以通信（$parent / $children）；ref 也可以访问组件实例；provide / inject API；$attrs/$listeners
兄弟通信：
Bus；Vuex
跨级通信：
Bus；Vuex；provide / inject API、$attrs/$listeners



