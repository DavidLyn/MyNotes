## 参考连接
+ [RESTful API 设计规范整理](https://www.jianshu.com/p/d25ae353797f)

---
# HTTP 请求规范

+ GET（SELECT）：查询; 从服务器取出资源（一项或多项）
+ POST（CREATE）：新增; 在服务器新建一个资源
+ PUT（UPDATE）：覆盖,全部更新 ; 在服务器更新资源（客户端提供改变后的完整资源）
+ PATCH（UPDATE）：更新; 在服务器更新资源（客户端提供改变的属性）
+ DELETE（DELETE）：删除; 从服务器删除资源

---
# HTTP 状态码

## 状态码范围

### 1xx 信息，请求收到，继续处理。API 不需要 1xx 状态码
### 2xx 成功，行为被成功地接受、理解和采纳

200状态码表示操作成功，但是不同的方法可以返回更精确的状态码

```
# GET: 200 OK
# POST: 201 Created
# PUT: 200 OK
# PATCH: 200 OK
# DELETE: 204 No Content
```

上面代码中，POST 返回 201 状态码，表示生成了新的资源；DELETE 返回 204 状态码，表示资源已经不存在

此外，202 Accepted 状态码表示服务器已经收到请求，但还未进行处理，会在未来再处理，通常用于异步操作。下面是一个例子

```
HTTP/1.1 202 Accepted

{
  "task": {
    "href": "/api/company/job-management/jobs/2130040",
    "id": "2130040"
  }
}
```

### 3xx 重定向，为了完成请求，必须进一步执行的动作

API 用不到 301 状态码（永久重定向）和 302 状态码（暂时重定向，307 也是这个含义），因为它们可以由应用级别返回，浏览器会直接跳转，API 级别可以不考虑这两种情况

API 用到的 3xx 状态码，主要是 303 See Other，表示参考另一个 URL。它与 302 和 307 的含义一样，也是"暂时重定向"，区别在于 302 和 307 用于 GET 请求，而 303 用于 POST、 PUT和 DELETE 请求。收到 303 以后，浏览器不会自动跳转，而会让用户自己决定下一步怎么办

下面是一个例子:

```
HTTP/1.1 303 See Other
Location: /api/orders/12345
```

### 4xx 客户端错误，请求包含语法错误或者请求无法实现。范围保留用于响应客户端做出的错误，例如，他们提供不良数据或要求不存在的东西。这些请求应该是幂等的，而不是更改服务器的状态

4xx状态码表示客户端错误，主要有下面几种

+ 400 Bad Request： 服务器不理解客户端的请求，未做任何处理
+ 401 Unauthorized： 用户未提供身份验证凭据，或者没有通过身份验证
+ 403 Forbidden： 用户通过了身份验证，但是不具有访问资源所需的权限
+ 404 Not Found： 所请求的资源不存在，或不可用
+ 405 Method Not Allowed： 用户已经通过身份验证，但是所用的 HTTP 方法不在他的权限之内
+ 410 Gone： 所请求的资源已从这个地址转移，不再可用
+ 415 Unsupported Media Type： 客户端要求的返回格式不支持。比如，API 只能返回 JSON 格式，但是客户端要求返回 XML 格式
+ 422 Unprocessable Entity ： 客户端上传的附件无法处理，导致请求失败
+ 429 Too Many Requests： 客户端的请求次数超过限额


### 5xx 范围的状态码是保留给服务器端错误用的。这些错误常常是从底层的函数抛出来的，甚至开发人员也通常没法处理，发送这类状态码的目的以确保客户端获得某种响应。当收到5xx响应时，客户端不可能知道服务器的状态，所以这类状态码是要尽可能的避免

5xx状态码表示服务端错误。一般来说，API 不会向用户透露服务器的详细信息，所以只要两个状态码就够了

+ 500 Internal Server Error： 客户端请求有效，服务器处理时发生了意外
+ 503 Service Unavailable： 服务器无法处理请求，一般用于网站维护状态

## 服务器向用户返回的状态码和提示信息

+ 200 OK - [GET]：服务器成功返回用户请求的数据，该操作是幂等的（Idempotent）
+ 201 CREATED - [POST/PUT/PATCH]：用户新建或修改数据成功
+ 202 Accepted - [*]：表示一个请求已经进入后台排队（异步任务）
+ 204 NO CONTENT - [DELETE]：用户删除数据成功
+ 400 INVALID REQUEST - [POST/PUT/PATCH]：用户发出的请求有错误，服务器没有进行新建或修改数据的操作，该操作是幂等的
+ 401 Unauthorized - [*]：表示用户没有权限（令牌、用户名、密码错误）
+ 403 Forbidden - [*] 表示用户得到授权（与401错误相对），但是访问是被禁止的
+ 404 NOT FOUND - [*]：用户发出的请求针对的是不存在的记录，服务器没有进行操作，该操作是幂等的
+ 406 Not Acceptable - [GET]：用户请求的格式不可得（比如用户请求JSON格式，但是只有XML格式）
+ 410 Gone -[GET]：用户请求的资源被永久删除，且不会再得到的
+ 422 Unprocesable entity - [POST/PUT/PATCH] 当创建一个对象时，发生一个验证错误
+ 500 INTERNAL SERVER ERROR - [*]：服务器发生错误，用户将无法判断发出的请求是否成功
+ 502 网关错误
+ 503 Service Unavailable 服务端当前无法处理请求
+ 504 网关超时

---
# URL 规范

## 域名

+ API 与用户的通信协议，总是使用 HTTPs 协议
+ 应该尽量将API部署在专用域名之下  https://api.example.com
+ 项目 API 比较简单的放在主域名下 https://example.com/api/

## 版本

+ 应该将 API 的版本号放入 URL

```
https://api.example.com/v1/
https://example.com/api/v1/
```

## 命名

+ 网址中不能有动词，只能有名词，而且所用的名词往往与数据库的表格名对应
+ 数据库中的表都是同种记录的"集合"（collection），所以 API 中的名词也应该使用复数
+ 尽量不要用大写，单词间使用下划线'_'
+ url 层级大于或等于三层，则使用`?`带参数

```
GET         /zoos：列出所有动物园
POST        /zoos：新建一个动物园
GET         /zoos/ID：获取某个指定动物园的信息
PUT         /zoos/ID：更新某个指定动物园的信息（提供该动物园的全部信息）
PATCH       /zoos/ID：更新某个指定动物园的信息（提供该动物园的部分信息）
DELETE      /zoos/ID：删除某个动物园
GET         /zoos/ID/animals：列出某个指定动物园的所有动物
DELETE      /zoos/ID/animals/ID：删除某个指定动物园的指定动物
DELETE      /zoos/ID/animals?id=：删除某个指定动物园的指定动物
```

+ 避免多级 URL

资源需要多级分类，因此很容易写出多级的 URL，比如获取某个作者的某一类文章

```
# GET /authors/12/categories/2
```

更好的做法是，除了第一级，其他级别都用查询字符串表达

```
# GET /authors/12?categories=2
```

查询已发布的文章。你可能会设计成下面的 URL

```
# GET /articles/published
```

查询字符串的写法明显更好

```
# GET /articles?published=true
```

---
# 返回数据规范

+ 客户端错误，状态码是 4xx，就应该向用户返回出错信息
+ 错误代码根据 “状态码&错误码” 的方式返回

```
{
    status:400,
    error_code:40006
    error: "Invalid API key"
}
```

+ 错误码参考

> [新浪错误码](https://open.weibo.com/wiki/Error_code)
> 
> [微信错误码](https://developers.weixin.qq.com/doc/oplatform/Return_codes/Return_code_descriptions.html)
> 
> [豆瓣restful api 状态和错误码 -- 值得参考](https://www.cnblogs.com/yangchunlong/p/8063732.html)

