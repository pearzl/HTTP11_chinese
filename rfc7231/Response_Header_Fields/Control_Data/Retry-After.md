服务器发送“Retry-After”头字段以表明客户端在发送后续请求之前应该等待多长时间。当发送503（服务不可用）响应是，Retry-After表示对客户端而言服务其由多长时间不可用。当发送任何3xx（重定向）响应时，Retry-After表示用户代理在发起重定向请求之前被要求等待的最小时间。

这个字段的值可以时一个HTTP-date或一个在响应被接收到以后的延时的秒数。

> ```
>      Retry-After = HTTP-date / delay-seconds
> ```

delay-seconds值是一个非负十进制整数，表示秒的时间。

> ```
>    delay-seconds  = 1*DIGIT
> ```

它的用法的两个例子

> ```
>      Retry-After: Fri, 31 Dec 1999 23:59:59 GMT
>      Retry-After: 120
> ```

在后一个例子中，延时是两分钟。