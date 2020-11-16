# 不常用的HTTP状态码
根据 MDN 的记载，[HTTP](https://developer.mozilla.org/zh-CN/docs/Web/HTTP)状态码有54种。
我们熟悉且常用的 `HTTP状态码`有 20x, 30x, 40x, 50x 等。这里回顾下他们各自代表的含义。
## 200 - OK
表示请求被成功处理，服务器响应有效负载。 不同请求方式对于请求成功的意义不同：

1. GET：已经取得资源，并将资源添加到消息体中；
2. POST：响应的消息体中包含此次请求的结果；
3. HEAD：响应的消息体为头部信息；
4. TRACE：响应的消息体中包含了服务器接收到的请求信息；

## 201 - Created
表示请求已经被成功处理，并且创建了新的资源。新的资源在应答返回之前已经被创建。同时新增的资源会在应答消息体中返回。其中POST, PUT方法的成功返回都可以用201来表示。注意：`服务器必须在返回201状态代码之前创建资源`。

## 202 - Accept `不常用`
表示服务器已经接收到请求，但是尚未进行处理。服务器对于请求的处理无法保证。无法通过 HTTP 协议给客户端发送一个请求来告知其请求的处理结果。这个状态码被设计用来`将请求交由另外一个进程或者服务器来进行处理，或者是对请求进行批处理的情形`。

## 204 - No Content `不常用`
表示请求已经被成功处理，并且在响应有效负载正文中没有要发送的内容。使用惯例是，在 PUT 请求中进行资源更新，但是不需要改变当前展示给用户的页面，那么返回 204。如果创建了资源，则返回 201 。如果有页面更新，则应改用 200 。

## 301 - 永久重定向 `不常用`
请求的资源已经被移动到了由Location头部指定的url上，是固定的不会再改变。`搜索引擎会根据该响应修正`。

## 302 - 重定向
请求的资源被暂时的转移到了Location指定的的URL上。浏览器会重定向到这个URL,`搜索引擎不会对该资源的链接进行更新`。

## 400 - Bad Request
由于语法无效，服务器无法理解该请求。

## 401 - Unauthorized 
缺乏请求的目标资源要求的凭证，可以只需验证，只要带上合法的凭证信息，例如 token。

## 403 - Forbidden
服务器有能力处理该请求，但是拒绝授权访问，该请求是长期禁止的，并且与程序逻辑有关（例如不正确密码）。

## 404 - Not Found
无法找到请求的资源。

## 405 - Method Not Allowed
服务器禁止了使用当前 HTTP 方法的请求。

## 429 - Too Many Request `不常用`
表示在一定的时间内用户发送了太多的请求，即超出了“频次限制”。 对于开放式API，通常会对请求进行`限流`(API GateWay中必备功能)。在响应中，可以提供一个  `Retry-After` 首部来提示用户需要等待多长时间之后再发送新的请求。

```
Retry-After: <delay-seconds>  单位是秒
```

## 500 - Internal Server Error
服务器处理请求时候出现错误，通过堆栈进行排查。

## 501 - Not Implemented  `不常用`
请求的方法不被服务器支持，因此无法被处理。服务器必须支持的方法只有 GET 和 HEAD。无法修复 501 错误，需要被访问的 web 服务器去修复该问题。

## 502 - Bad GateWay
作为网关或代理角色的服务器，从上游服务器（如tomcat、nginx等）中接收到的响应是无效的。502 错误通常不是客户端能够修复的，而是需要由途径的Web服务器或者代理服务器对其进行修复。

## 503 - Service Unavailable
表示服务器尚未处于可以接受请求的状态。造成这种情况的原因是由于服务器停机维护或者已超载。例如关闭/重启 tomcat 服务过程中将会出现。

## 504 - GateWay Timeout `不常用`
作为网关或者代理的服务器无法在规定的时间内获得想要的响应。

## 505 - Http Version Not Supported `不常用`
表示服务器不支持请求所使用的 HTTP 版本。

## 511 - Network Authentication Required `不常用`
表示客户端需要通过验证才能使用该网络，该状态码不是由源头服务器生成的，而是由控制网络访问的拦截代理服务器生成的。网络运营商们有时候会在准许使用网络之前要求用户进行身份验证、接受某些条款，或者进行其他形式的与用户之间的互动（例如在网络咖啡厅或者机场）。他们通常用用户设备的  MAC 地址来进行识别。

以上就是常用和不常用，但必须得知道的HTTP状态码了。