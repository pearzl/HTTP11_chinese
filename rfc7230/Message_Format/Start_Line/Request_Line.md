请求行以一个方法标记开始，随后跟一个空格符（SP），请求目标，另一个空格符（SP），协议版本和结尾的CRLF。

> ```
>  request-line   = method SP request-target SP HTTP-version CRLF
> ```

方法标记指示目标资源上执行的请求方法。请求方法是区分大小写的。

> ```
> method         = token
> ```

本规范定义的请求方法可以在RFC7231的第4节中找到，包括有关HTTP方法注册表的信息以及定义新方法的注意事项。

request-target标识了应用请求的目标资源，这在5.3节中定义。

接收者通常通过空白分隔将请求行分解为其组成部分（见3.5节），因为三个子组件中不允许有空格。不幸的是，一些用户代理不能正确地编码或排除超文本引用中的空白，导致那些不允许的字符被发送到request-target。

无效request-line的接收者应该响应一个400（错误请求）错误或者使用一个正确编码的request-line响应一个301（永久移动）重定向。接收者**不得**试图自动更正然后处理请求而不进行重定向，因为无效的request-line可能是故意制造的以绕过请求链中的安全过滤器。

如2.5中描述的那样，HTTP没有预先定义request-line的长度限制。服务器收到一个比它实现的任何方法都长的方法应该响应一个501（没有实现）状态码。服务器收到一个比它期望解析的任何URI都长的request-target是**必须**响应一个414（URI太长）状态码（查看RFC7231的6.5.12节）。

在实践中发现了对请求行长度的各种临时限制。建议所有的HTTP发送者和接收者支持最小8000字节的请求行长度。