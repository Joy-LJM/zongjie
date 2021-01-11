### 深拷贝、浅拷贝
- 浅拷贝(浅拷贝为拷贝引用地址)
  - Object的assign方法可以实现浅拷贝，可以拷贝对象的key value到新的对象中
  ```
  let a = {age: 1}
  let b = Object.assign({}, a)
  console.log(a==b) // false
  console.log(b.age) //1
  ```
  - 使用ES6的展开运算符，也可以实现浅拷贝：...展开对象的key value给新对象
  ```
  let a = {age: 1}
  let b = {...a}
  console.log(b.age) //1
  ```
- 浅拷贝局限场景：a对象里面的某个key的value值是c，c也是一个对象，对a进行浅拷贝成b；此时通过对象a来改变对象c；那么b里面的c也会跟着一起改
- 原因：c是一个对象，引用数据类型，浅拷贝后b的那个value值是一个地址，对象c的地址
- 要求：对象a和对象b弄成两个独立的个体，互不干扰

- 深拷贝：(对象的复制对象)

使用JSON的方法来实现，JSON.parse(JSON.stringify(object))
  - JSON.stringify把a对象转成JSON字符串格式
  - JSON.parse再把JSON字符串转为js对象
  - 局限:Number,String,Boolean,Array,可以转为JSON对象,但是undefined、function、RegExp这种不行
        无法拷贝copyObj对象原型链上的属性和方法
- 
深拷贝方法2:递归实现 =》待查
  1.首先声明一个递归函数
  2.在递归函数里判断是不是一个对象，不是则为基本数据类型，直接赋值
  3，在进行判断是不是数组，如果是数组的话，先声明一个空数组，直接用for in 遍历数组每一项，通过调用push方法去拷贝数组中的每一项。
  4如果是正则，就直接就行赋值
  5如果是普通对象，直接for in循环，递归赋值对象的所有值

  深拷贝方法3：

