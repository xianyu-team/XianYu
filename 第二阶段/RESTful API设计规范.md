# RESTful API 设计规范

## 前言
REST 全称是 Representational State Transfer，中文意思是表述性状态转移。它是一种软件架构风格、设计风格，而不是标准，只是提供了一组设计原则和约束条件。它主要用于客户端和服务器交互类的软件，比如 web、android 应用。

REST 指的是一组架构约束条件和原则，满足这些约束条件和原则的应用程序或设计就是 RESTful。

## REST 原则
- 客户端和服务器之间的交互在请求之间是无状态的。即从客户端到服务器的每个请求都必须包含理解请求所必需的信息。如果服务器在请求之间的任何时间点重启，客户端不会得到通知。
- 在服务器端，应用程序状态和功能可以分为各种资源，每一个URL代表一种资源。
- 客户端和服务器之间，传递这种资源的某种表现层。
- 客户端通过标准的 HTTP 动词 (GET、POST、DELETE、PUT)，对服务器端资源进行操作，实现增删改查。
- URL 中通常不出现动词，只有名词。
- 使用 JSON 不使用 XML。

## 资源的理解
REST 全称是表述性状态转移，那究竟指的是什么的表述? 其实指的就是资源。任何事物，只要有被引用到的必要，它就是一个资源。资源可以是实体(例如手机号码)，也可以只是一个抽象概念(例如联系集) 。下面是一些资源的例子：
- 用户的手机号码
- 学生的学籍信息
- 用户与学生之前的依赖关系
- 用户所发布的任务
- 用户所完成的订单

## URL 的设计
前面提到，在服务端被引用的任何事物都是一个资源，而每一个 URL 就代表一种资源。那么，如何设计一个简洁明了、易于理解的 URL 就显得尤为重要。

RESTful 的核心思想就是，客户端发出的数据操作指令都是"动词 + 宾语"的结构。比如`GET /users`，`GET`是动词，`/users`是宾语。

### 动词
标准的 HTTP 请求动词有以下5个：
- GET : 获取资源
- POST : 创建资源
- PUT : 更新资源，客户端需要提供资源的所有属性
- PATCH : 更新资源的部分属性(很少用)
- DELETE : 删除资源

### 宾语
宾语就是 API 的 URL，是 HTTP 动词作用的对象。它应该是名词，不能是动词。比如，/users这个 URL 就是正确的，而下面的 URL 不是名词，所以都是错误的。
- /getAllUsers
- /createNewUser
- /deleteUser

下面我们可以使用一些技巧使得 URL 更符合规范：
- 使用 '_' 或 '-' 连接符让URL可读性更好

URL 上过长的无意义的数字或字符串会大大减少 URL 的可读性，所以现在越来越多的网站使用 '_' 或 '-' 来分隔一些单词，让 URL 看上去更为人性化，如`/orders-translate-reward-plan`。

- 使用 '/' 来表示资源的层级关系

如`/orders/2019/orders-translate-reward-plan`就表示了一个层级关系，表示在所有的订单 orders 中，获取2019年下的 orders-translate-reward-plan 订单。

- 使用 '?' 用来过滤资源

分隔符 '?' 后面跟的参数被用于一些特定条件的查询，所以可以把 '?' 用于对资源的过滤。例如`/orders?state=closed`用来表示已经关闭的订单， 这种 URL 通常对应的是一些特定条件的查询结果或算法运算结果。

## 状态码
### 状态码类别
HTTP 状态码就是一个三位数，分成五个类别：
- 1xx：相关信息
- 2xx：操作成功
- 3xx：重定向
- 4xx：客户端错误
- 5xx：服务器错误

这五大类总共包含100多种状态码，覆盖了绝大部分可能遇到的情况。每一种状态码都有标准的解释，客户端只需查看状态码，就可以判断出发生了什么情况，所以服务器应该返回尽可能精确的状态码。

### 2xx 状态码
2xx 状态码表示操作成功，但是不同的方法可以返回更精确的状态码。
- GET: 200 OK，表示获取资源成功
- POST: 201 Created，表示创建新资源成功
- PUT: 200 OK，表示更新资源成功
- PATCH: 200 OK，表示更新部分资源成功
- DELETE: 204 No Content，表示资源被成功删除，该资源已不存在

### 3xx 状态码
- 303 See Other，表示参考另一个 URL。它与302和307的含义一样，也是"暂时重定向"，区别在于302和307用于 GET 请求，而303用于POST、PUT 和 DELETE 请求。收到303以后，浏览器不会自动跳转，而会让用户自己决定下一步怎么办。

### 4xx 状态码
4xx 状态码表示客户端错误，主要有下面几种：
- 400 Bad Request：服务器不理解客户端的请求，未做任何处理。
- 401 Unauthorized：用户未提供身份验证凭据，或者没有通过身份验证（令牌、用户名、密码错误）。
- 403 Forbidden：用户通过了身份验证，但是不具有访问资源所需的权限。
- 404 Not Found：所请求的资源不存在，或不可用。
- 405 Method Not Allowed：用户已经通过身份验证，但是所用的 HTTP 方法不在他的权限之内。
- 410 Gone：所请求的资源已从这个地址转移，不再可用。
- 415 Unsupported Media Type：客户端要求的返回格式不支持。比如，API 只能返回 JSON 格式，但是客户端要求返回 XML 格式。
- 422 Unprocessable Entity ：客户端上传的附件无法处理，导致请求失败。
- 429 Too Many Requests：客户端的请求次数超过限额。

### 5xx 状态码
5xx状态码表示服务端错误。一般来说，API 不会向用户透露服务器的详细信息，所以只要两个状态码就够了。
- 500 Internal Server Error：客户端请求有效，服务器处理时发生了意外。
- 503 Service Unavailable：服务器无法处理请求，一般用于网站维护状态。

## 服务器响应
API 返回的数据格式，不应该是纯文本，而应该是一个 JSON 对象，因为这样才能返回标准的结构化数据。

针对不同操作，服务器向用户返回的结果应该符合以下规范。
- GET /collection：返回资源对象的列表（数组）
- GET /collection/resource：返回单个资源对象
- POST /collection：返回新生成的资源对象
- PUT /collection/resource：返回完整的资源对象
- PATCH /collection/resource：返回完整的资源对象
- DELETE /collection/resource：返回一个空文档

## 参考链接
- [http://www.ruanyifeng.com/blog/2018/10/restful-api-best-practices.html](http://www.ruanyifeng.com/blog/2018/10/restful-api-best-practices.html)
- [https://www.runoob.com/w3cnote/restful-architecture.html](https://www.runoob.com/w3cnote/restful-architecture.html)