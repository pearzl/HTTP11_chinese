权威形式（authority-form）的请求目标只被用于CONNETC请求（RFC7231的4.3.6节）。

> ```
>    authority-form = authority
> ```

当构建一个CONNECT请求来建立一个穿过一个或多个代理的隧道时，客户端**必须**仅发送目标URI的权威组建（不包含任何的用户信息和它的“@”分隔符）作为请求目标。例如，

> ```
>     CONNECT www.example.com:80 HTTP/1.1
> ```

