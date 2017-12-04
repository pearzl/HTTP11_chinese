当构造一个到代理的请求时，除了CONNECT或者服务器范围的OPTIONS请求（下面将详细描述），客户端**必须**发送目标URI的绝对格式（absolute-form）作为请求目标（request-target）。

> ```
>  absolute-form  = absolute-URI
> ```

代理被要求从有效的缓存中处理该请求，如果可能的话，或者代表客户端发出相同的请求到下一个入站代理服务器或者直接到请求目标指示的源服务器。这种消息“转发”的要求被定义在5.7节。

一个绝对形式的请求行（request-line）的例子：

> ```
>  GET http://www.example.org/pub/WWW/TheProject.html HTTP/1.1
> ```

为了允许在将来的某个版本的HTTP中转换为绝对格式，服务器必须接受绝对格式的请求，即使HTTP / 1.1客户端只会将这种请求发送给代理服务器。