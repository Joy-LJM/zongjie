#### node.js

1创建一个web服务器，首先引入http模块，再创建个服务实例（http.createserver（回调函数，里面有req，res俩个参数）），监听服务（server.listen）

1-1 进程管理工具  supervior （实现文件的热加载，当返回的数据发生变化，不需要再node运行文件）

2.使用了common.js规范

3导出全部模块为 module.exports={}    

   				引入模块用require（文夹）

4部分导出  ： exports.方法=对象.方法

​			require.方法

5.使用脚手架 express-generator 生成骨架应用

5.1创建项目，创建不带视图模板的项目，( express demo --no-view // demo 是项目名称 --no-view 代表生成的项目不带视图模板),如果不带视图，就去加载public文夹下的index.html，如果有视图模板，就去加载views文夹下的文夹。

5.2进入项目，下载依赖(npm install)，在运行项目npm run start

5.3 express-generator框架中的热加载 ，安装npm install node-dev -D，在在 `package.json` 文件中添加

```
 "scripts": {
    "dev": "node-dev ./bin/www"
  },
  
 然后运行npm run dev
```

5.4在路由中配置返回信息。res.send  或者res.json