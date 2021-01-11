### BFC作用 高度塌陷、清除浮动、.Margin垂直重叠，二栏布局
- BFC：是块级格式上下文的意思，(渲染出一片独立的区域，不受外界影响)
  - 特点1：触发了BFC模式的容器有个特点，这个容器内的子元素在布局上的变化都不会对外面的元素有任何的影响。这个特点，就好比在布局上有个概念叫做脱离文档流，脱离文档流的元素是一个漂浮独立的个体。
  - 特点2：bfc容器是一个独立的容器，不同bfc的margin值不会发生折叠，一个bfc容器里面的两个相邻的box的margin值会发生折叠合并；
  - 特点3：BFC容器的高度包含了浮动子元素的高度

- 触发bfc方式：
  - 浮动：给容器设置了浮动float属性，float-left或者float-right，都可以使容器脱离文档流
  - 定位：给容器设置定位属性position为绝对定位absolute或者固定定位fixed，也可以实现脱离文档流的效果，   而  relative和static不行；
  - overflow属性：只要不为visible也可以触发bfc，可以设置属性为hidden、auto，scroll；
  - display属性：设置为table-cell\table-caption\inline-block\flex



- 利用BFC容器高度的特点解决布局上出现的高度塌陷
  - 1.父元素加上固定高度
  - 2..父元素加上overflow-hidden
  -3. 清除浮动clear-both:
    - 在浮动元素末尾添加一个空的div，高度设置为0，clear设置为both，加上overflow-hidden；

  -4. 利用伪类伪元素把刚刚清除浮动的方法提取出来成公共样式：
    - 冒号:after可以在父元素子元素末尾添加content，将公共样式类名设置.clearfix:after
    - 里面设置content:"", display：block，clear: both，height: 0，overflow: hidden，visibility: hidden
    font-size:1px(解决老的浏览器问题)
    - 在需要清除浮动解决高度塌陷的地方，父元素样式加上clearfix


  