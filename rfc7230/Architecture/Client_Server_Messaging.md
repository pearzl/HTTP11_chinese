HTTP是无状态请求/响应协议，通过在可靠的传输层或会话层“connection（连接）”（第6节）上交换消息（第3节）来进行操作。一个HTTP“client（客户端）”是一个为了发送一个或多个HTTP请求而与服务器建立连接的程序。一个HTTP“server（服务器）”是一个接受连接通过发送HTTP响应来服务HTTP请求的程序。

术语“client”和“server”只表示这些程序在特定连接中扮演的角色。同一个程序可能在一些连接中扮演client，而在其他连接中扮演server。术语“user agent（用户代理）”指任何发起请求的客户端程序，包括（但不限于）浏览器，爬虫（网络机器人），命令行工具，定制应用和移动应用。术语“origin server（源服务器）”指能够对给定目标的资源建立权威应答的程序。术语“sender（发送者）”和“recipient（接收者）”分别指发送或接收给定消息的任何实现。

HTTP依靠统一资源标识符（URI）标准来标明目标资源（5.1节）和资源之间的关系。消息的传递格式与Internet邮件[RFC5322]和多用途Internet邮件扩展（MIME）所使用的格式相似（有关HTTP和MIME消息之间的差异，请参阅[RFC7231]的附录A.）。



大多数HTTP通信包括用于表示由URI标识的一些资源的检索请求（GET）。在最简单的情况下可以通过一个在user agent(UA)和origin server (o)的双向连接来实现

```
	request >
UA ======================================= O
		                       < response
```

一个client以一个请求消息的格式发送HTTP请求到一个server，以一个请求行开始，包括一个方法、URI和协议版本（3.1.1节）。接着是header域包括了请求修饰符、客户端信息和表示元信息（3.2节），一个空行表示结束后header部分，最后一个消息体包含了body（如果存在的话，3.3节）。

一个服务器通过发送一个或多个HTTP响应消息来响应客户端的一个请求。每个HTTP响应消息都已包含协议版本，成功或错误代码和文本原因短语（3.1.2节）的状态行开始，后面可能跟头字段包含服务器信息、资源元数据和表示元数据（3.2节），一个表示包头部分结束的空行，最后是包含有效载荷主体（如果由的话，3.3节）的消息主体。

一个连接可能用于多个请求/响应交互，这定义在6.3节。

下面的例子说明了一个对URI为 “http://www.example.com/hello.txt” 的GET请求（RFC7231的4.3.1节）的一个典型的消息交换：

客户端请求:

> ```
> GET /hello.txt HTTP/1.1
> User-Agent: curl/7.16.3 libcurl/7.16.3 OpenSSL/0.9.7l zlib/1.2.3
> Host: www.example.com
> Accept-Language: en, mi
> ```

服务器响应：

> ```
> HTTP/1.1 200 OK
> Date: Mon, 27 Jul 2009 12:28:53 GMT
> Server: Apache
> Last-Modified: Wed, 22 Jul 2009 19:15:56 GMT
> ETag: "34aa387-d-1568eb00"
> Accept-Ranges: bytes
> Content-Length: 51
> Vary: Accept-Encoding
> Content-Type: text/plain
>
> Hello World! My payload includes a trailing CRLF.
> ```