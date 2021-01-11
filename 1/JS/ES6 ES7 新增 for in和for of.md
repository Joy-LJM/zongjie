### ES6 ES7 新增特性 for in 和 for of 区别
- let const 关键字
  - let\const关键字声明的变量可以产生块级作用域，也不会存在变量提升的问题
  - const声明的常量不能被修改
  - 变量在let声明之前就使用会报错

- 解构赋值 {从对象中提取key时，自定义的变量和key同名的话，可以省略自定义的，直接用key}

- 展开运算符 ...

- 在函数定义时可以直接给形参传默认值 function fn(num=1,name){}

- 箭头函数

- ``模版字符串

- set 数据结构 
  - 类似于数组，set里面的元素是唯一的，不会有重复；
  - 配合...运算符可以轻松实现数据去重

- map 数据结构
  - 类似于对象，键值对的集合；不同的是，各种类型的数据都可以当做键，包括对象

- for of 遍历
  - for in遍历数组时，遍历的是数组的索引，存在如下问题：
    - 索引index是字符串类型，不能直接进行几何运算
    - 遍历顺序有可能不是按照实际数组的内部顺序
    - for in更适合遍历对象，不要使用for in遍历数组
  - for of遍历数组时，遍历的是数组元素的值，更适用于数组，避免了for-in的所有缺陷
  - for of 可以用break来终止整个循环，或者continute来跳出当前循环，继续后面的循环；
  - for...of支持类数组的遍历，例如DOM List、set、map
  - for...of不支持遍历普通的Object对象，会出现obj[Symbol.iterator]不是一个function
  - 只要一个数据结构拥有一个叫[Symbol.iterator]迭代器的方法，就可以被for...of遍历

- 新增promise对象，用来异步代码可以减少嵌套

- 其它的还有class类与继承、模块化语法import和export、装饰器@，用来修改类的行为