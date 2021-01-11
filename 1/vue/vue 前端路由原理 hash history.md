### 前端路由 实现原理
- 前端路由有两个模式，Hash模式和History模式；

- 前端路由本质上就是监控url地址栏的变化，然后根据url信息匹配路由规则，显示相应的页面，实现在无刷新的前提下进行组件切换

- hash模式下的url地址栏上有带个#号，history模式地址栏没有#号，看起来比较干净
- hash模式下，当#后面的哈希值发生变化时，可以通过hashchange事件来监听到url的变化，从而进行页面的跳转

- history模式主要是通过history.pushState和history.replaceState改变url实现跳转，同样也不会引起页面的刷新
- history模式上线后会出现404找不到页面的问题，在重定向会有些问题，可能不会出定义好的页面。需要这个页面文件名改成index.html

- 之前用的默认hash模式，虽然有个#号看着比较变扭，但很少人几乎没人会管这个区别，默认的好用就用了，
	- 如果觉得不好看要改用history模式，那也可以改，只不过需要运维在上线部署时添加一段配置就行了，配置：mode：‘history

hash模式：通过window.location.hash 来进行切换。Window.onhashchange来监听路由，（可以使用事件监听addEventlisten 来监听onhashchange,这样就不影响其他的事件）

 History模式：通过h5history新添加pushState() 和 replaceState() 方法来 进行切换。监听路经的切换要用window.onpopstate()

注意一点：调用history.pushstate()不会触发indow.onpopstate()事件，只有浏览器有动作时才会触发监听事件，（history.go /back /forward）

Hash优点：(1) 只需要前端配置路由表, 不需要后端的参与
(2) 兼容性好, 浏览器都能支持
(3) hash值改变不会向后端发送请求, 完全属于前端路由

History的缺点 ：(1) 在用户手动输入地址或刷新页面时会发起url请求, 后端需要配置index.html页面，用户匹配不到静态资源的情况, 否则会出现404错误
(2) 兼容性比较差, 是利用了 HTML5 History对象中新增的 pushState() 和 replaceState() 方法,需要特定浏览器的支持.