#### webpack

const path = require("path")
var HtmlWebpackPlugin = require('html-webpack-plugin');
module.exports = {
    devtool:"eval-source-map",
    mode: "development",
    entry: "./index.js",
    output: {
        path: path.resolve(__dirname, "dist"),
        filename: "bundle.js"
    },
    module: {
        rules: [
            {
                test: /\.css$/,
                use: ['style-loader', 'css-loader']
            }
        ]
    },
    plugins: [new HtmlWebpackPlugin()]
}
```

1.引入路径模块

2.**入口起点(entry point)**指示 webpack 应该使用哪个模块，来作为构建其内部 [依赖图(dependency graph)](https://webpack.docschina.org/concepts/dependency-graph/) 的开始

3.输出**output** 属性告诉 webpack 在哪里输出它所创建的 *bundle*，以及如何命名这些文件。主要输出文件的默认值是 `./dist/main.js`，其他生成文件默认放置在 `./dist` 文件夹中

4.load: webpack 只能理解 JavaScript 和 JSON 文件，这是 webpack 开箱可用的自带能力。**loader** 让 webpack 能够去处理其他类型的文件，并将它们转换为有效 [模块](https://webpack.docschina.org/concepts/modules)，以供应用程序使用，以及被添加到依赖图中.

​	loader 有两个属性：('样式使用   style-loader',  'css-loader')

1. `test` 属性，识别出哪些文件会被转换。
2. `use` 属性，定义出在进行转换时，应该使用哪个 loader。



5.引入插件  如 'html-webpack-plugin'，你只需要 `require()` 它，然后把它通过使用 `new` 操作符来创建它的一个实例添加到 `plugins` 数组中。多数插件可以通过选项(option)自定义。

运行 `webpack`后，就能在dist文件下生成index.html文件，并且把js文件注入到index.html文件里

6.模式（mode）:通过选择 `development`, `production` 或 `none` 之中的一个，来设置 `mode` 参数，你可以启用 webpack 内置在相应环境下的优化。其默认值为 `production`。

7.Devtool 的配置选项

​	开发环境    ：`eval-source-map` - 每个模块使用 `eval()` 执行，并且 source map 转换为 DataUrl 后添加到 `eval()` 中。初始化 source map 时比较慢，但是会在重新构建时提供比较快的速度，并且生成实际的文件。行数能够正确映射，因为会映射到原始代码中。`它会生成用于开发环境的最佳品质的 source map`。
 
​	eval-source-map 初始化的时候比较慢，重新构建的速度快。	

​	生产环境：  ` (none)`（省略 `devtool` 选项） - 不生成 source map。这是一个不错的选择



怎么用webpack进行优化
答：1压缩代码uglifyJsPlugin 压缩js代码， mini-css-extract-plugin 压缩css代码
    2 提取公共代码。webpack4移除了CommonsChunkPlugin (提取公共代码)，用optimization.splitChunks和optimization.runtimeChunk来代替
    3. 删除死代码（tree shaking），css需要使用Purify-CSS


loader 和 plugin 不同
答：1.loader是使wenbpack拥有加载和解析非js文件的能力
    2.plugin 可以扩展webpack的功能，使得webpack更加灵活。可以在构建的过程中通过webpack的api改变输出的结果



webpack怎么实现懒加载，怎么进行代码分割的
答：代码分割和懒加载不是通过webpack配置来实现的，而是通过webpack的写法和内置函数实现的，
目前webpack针对此项功能提供 2 种函数：
import(): 引入并且自动执行相关 js 代码
require.ensure(): 引入但需要手动（require）执行相关 js 代码在

1.1 import()编写page.js文件，import()可以通过注释的方法来指定打包后的 chunk 的名字
import(/* webpackChunkName: 'subPageA'*/ "./subPageA").then(function(subPageA) {
  console.log(subPageA);
});
1.2我们创建index.html文件，通过<script>标签引入我们打包结果，

2.1require.ensure(),引进后需要手动在去执行，require

提取公共的代码？
单页面：require.include
多页面：CommonsChunkPlugin