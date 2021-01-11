
- this指向：this总是指向函数的直接调用者，而非间接调用者；
  - 定义在全局window下的函数：直接调用函数的this是指向window
    - 在严格模式下"use strict"，用function定义的函数this是undefined{严格模式下无法创建全局变量}
  
  - 1.new关键字：也就是创建了一个实例，这里的this就是指向new出来的那个实例对象

  - 2.在事件中：this指向触发这个事件的对象，例如onclick的事件处理函数，this指向的就是被点击的元素
    - 在IE中添加事件attachEvent中的this总是指向全局对象window

  - 3.定时器：定时器函数里面this是指向window
    4.直接以函数名调用，this指的是window
  - 
  箭头函数：箭头函数内部的this指向，取决于箭头函数定义的位置，而非箭头函数的调用对象；
    - 箭头函数内部其实是没有this的，这个函数的this只取决于函数外面的第一个不是箭头函数的this，
    - 具体：寻找箭头函数外层代码块的this，没有就再往外找，直到window对象

- 保存this
    - 在开发中，当我们想使用某一层的this，而进入了内层代码块之后，this会发生改变，这个时候，我们可以var一个变量把当前的this存起来，例如vat _this = this

- 改变this call apply bind
  - 箭头函数的this指向可以用call、apply、bind来强制改变，作用都是一样的，只是传参方式不一样
  - 第一个形参都是传的是要指向的新的this对象

  - call和bind的传参从第二个参数开始可以传很多个参数；
  - 而apply最多只能有两个参数，第二个参数是一个数组，要传的多个参数可以放在数组里

  - call和apply是立即执行函数，改变this后就执行；
  - bind不是立即执行函数：bind改变函数this指向后，返回的是一个新的函数