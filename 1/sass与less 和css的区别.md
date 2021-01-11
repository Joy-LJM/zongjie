#### 38sass与less 和css的区别

传统的css可以直接被html引用，sass和less使用了类似JavaScript的方式去书写，

因为CSS没有变量、函数、SCOPE（作用域），需要书写大量看似没有逻辑的代码，不方便维护及扩展，不利于复用

答

1两者编译环境不一样（Sass的安装需要Ruby环境，是在服务端bai处理的，而Less是需要引入less.js来处理Less，在客户端处理）

2变量符不一样，作用域也不一样（less是@，而scss是$,而且它们的作用域也不一样，less是块级作用域）

3输出设置不一样（Less没有输出设置，sass提供4种输出选项，nested,compact,compressed和expanded nested）

1. Sass支持条件语句，可以使用if{}else{},for{}循环等等。而Less不支持