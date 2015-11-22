Protocol
====================

### HTTP基本认证 
* 基本认证是一种用来允许Web浏览器或其他客户端程序在请求时提供用户名和口令形式的身份凭证的一种登录验证方式。
* 优点
  - 所有主流浏览器都支持
  - 实现容易
* 缺点
  - 明文传输
  - 没有登出方法
* 例子
  1. 客户端请求：
      - GET index.html HTTP/1.0
  2. 服务器返回401
      - HTTP/1.0 401 Authorization Required
      - WWW-Authenticate: Basic realm="Secure Area"
  3. 客户端提交帐号
      - GET index.html HTTP/1.0
      - Authorization: Basic base64(username:password)

### 相关书籍


### 相关资料
[HTTP基本认证](https://zh.wikipedia.org/wiki/HTTP基本认证)


