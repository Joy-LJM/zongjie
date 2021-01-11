### cookie鉴权
- 特点：cookie跟服务器域名相连接，可以确保只有原域名的服务器能够访问其中存储的信息。第三方服务器既不能读取也不能更改用户计算机上该域的cookie内容

- cookie鉴权流程：
  - 1、用户输入登陆凭据
  - 2、服务器验证凭据是否正确，并创建会话，然后把会话数据存储在数据库中
  - 3、具有会话id的cookie被放置在用户浏览器中
  - 4、在后续请求中，服务器会根据数据库验证会话id，如果验证通过，则继续处理
  - 5、一旦用户登出，服务端和客户端同时销毁该会话

- token的验证是无状态的，
  - 既可以加在header中，也可以加在post请求的主体中
  - 优势：基于token的验证是无状态的，后端服务不需要记录token；服务器唯一的工作就是在成功的登陆请求上签署token，并验证传入的token是否有效

- token鉴权流程：
  - 1、用户输入登陆凭据；
  - 2、服务器验证凭据是否正确，然后返回一个经过签名的token；
  - 3、客户端负责存储token，可以存在local storage，或者cookie中；
  - 4、对服务器的请求带上这个token；
  - 5、服务器对JWT进行解码，如果token有效，则处理该请求；
  - 6、一旦用户登出，客户端销毁token。

### token 存放位置
- token放在cookie中：可以防止xss攻击，但是会导致所有请求都会携带token
- token放在请求头中：会有xss风险，可以防止csrf攻击；需要前端保存token并在每次请求的时候携带，可以控制哪些请求携带，哪些不需要携带

csrf攻击（跨站请求攻击）：浏览器请求会自动带上cookie，不会带上token；
  -->> 用户点击链接，cookie未失效，后端以为是用户正常操作
  -->> 用户点击链接，浏览器不会自动带上token，即使发送了请求，token验证不通过

### token存储位置 localStorage sessionStorage和cookie
- 存在localStorage、sessionStorage
  - 缺点：容易受到XSS攻击；Storage可以被JS访问，例如项目中用到的第三方Javascript类库
  - xss跨站脚本攻击：在web页面注入恶意JS代码
  - xss防范：对尖括号<>的输入进行转换编码，浏览器就不会对该标签进行解释执行
  
- 存在cookie中，cookie里面设置httponly比较好
  - 缺点：容易遭受CSRF攻击，
  - csrf跨站请求伪造：黑客引诱客户打开黑网站，在黑网站中利用客户登录状态发起跨站请求

- 推荐使用cookie来存储token：相比较而言，web Storage比cookie更容易受到攻击，