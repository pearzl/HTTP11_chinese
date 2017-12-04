request-target最普遍的格式是原始形式（origin-form）。

> ```
>     origin-form    = absolute-path [ "?" query ]
> ```

 当构造一个直接到源服务器的请求时，除了CONNECT或者服务器范围的OPTIONS请求（下面会详细说明），客户端**必须**只发送目标URI的绝对路径和查询组件作为request-target。如果目标URI的路径组建是空的，客户端**必须**在request-target的原始形式中发送“/”作为路径。Host头字段也被发送，如5.4节中定义的那样。

例如，一个客户端希望直接从源服务器取回下面标识符所确定的资源

> http://www.example.org/where?q=now

它将打开（或者重用）到主机“www.example.org”的80端口的一个TCP连接并且发送下面的行：

> ```
> GET /where?q=now HTTP/1.1
> Host: www.example.org
> ```

后面跟着其余的请求消息。