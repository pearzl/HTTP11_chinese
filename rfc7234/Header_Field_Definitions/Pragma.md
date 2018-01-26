“Pragma”头字段允许与HTTP/1.0的缓存向后兼容，所以客户端可以发起一个他们能够理解的“不缓存”请求（因为Cache-Control还没有呗定义，直到HTTP/1.1）。当Cache-Control头字段也出现在请求中并且能够理解，Pragma就被忽略了。

在HTTP/1.0中，Pragma被定义为接收者执行指定指令的扩展字段。本规范配齐了这个扩展以提升互操作性。

> ```
>      Pragma           = 1#pragma-directive
>      pragma-directive = "no-cache" / extension-pragma
>      extension-pragma = token [ "=" ( token / quoted-string ) ]
> ```

当Cache-Control头字段没有出现在请求中，缓存**必须**将no-cache的请求pragma指令视为就像“Cache-Control：no-cache”存在一样的效果（查看5.2.1节）。

当发送一个no-cache请求，客户端应该包括pragma和cache-control指令，除非`Cache-Control： no-cache`是故意省略的以定义HTTP/1.1缓存上的其他Cache-Control指令。例如：

> ```
>      GET / HTTP/1.1
>      Host: www.example.com
>      Cache-Control: max-age=30
>      Pragma: no-cache
> ```

这将约束HTTP/1.1缓存来提供不超过30s的响应，同时排除不理解Cache-Control的实现服务于缓存的响应。

*注意：因为响应中“Pragma: no-cache”的含义是不具体的，因此不能提供可靠的替代方案来代替“Cache-Control: no-cache”。*