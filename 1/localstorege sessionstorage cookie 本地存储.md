### cookie localStorage sessionStorage 区别
- 生命时间
  - 服务器生成的cookie可设置失效时间，浏览器生成的cookie，浏览器关闭时就失效
  - localStorage 除非被清除，否则永久保存
  - sessionStorage 当前会话下有效，关闭页面或浏览器后被清除

- 存储空间大小：Cookie 4K左右；Storage一般为5MB

- 与服务器端通信时
 - cookie：每次都会携带在HTTP头中，如果使用cookie保存过多数据会带来性能问题
 - Storage：仅在客户端（即浏览器）中保存，不参与和服务器的通信，需开发者手动存取


