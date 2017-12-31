426（需要升级）状态码表明服务器拒绝使用当前协议的请求，但是可能愿意在客户端升级到一个不同的协议后这么做。服务器**必须**在426响应中发送Upgrade头字段来指明被请求的协议（RFC7230，6.7节）。

例子：

> ```
>      HTTP/1.1 426 Upgrade Required
>      Upgrade: HTTP/3.0
>      Connection: Upgrade
>      Content-Length: 53
>      Content-Type: text/plain
>
>      This service requires use of the HTTP/3.0 protocol.
> ```