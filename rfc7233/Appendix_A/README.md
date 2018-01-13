当206响应消息包含多部分范围的内容时，他们被以媒体类型为multipart/byteranges的多部分消息体（RFC2046，5.1节）中的主体部分而发送。

multipart/byteranges媒体类型包含一个或多个主体部分，每个都有自己的Content-Type和Content-Range字段。必要的边界参数指定了用于分隔每个主体部分的边界字符串。

实现注意：

1. 额外的CRLF可能出席那会在主体的第一个边界字符串前。
2. 虽然RFC2046允许边界字符串被引用，一些已存在的实现错误地处理引用的边界字符串。
3. 一些客户端和服务器用字节范围的早期草案进行编码，其使用的媒体类型multipart/ x-byteranges几乎（单不是完全）于这个类型是兼容的。

除了名字，multipart/byteranges媒体类型不限于字节范围。下列的例子使用了一个exampleunit范围单元：

> ```
>      HTTP/1.1 206 Partial Content
>      Date: Tue, 14 Nov 1995 06:25:24 GMT
>      Last-Modified: Tue, 14 July 04:58:08 GMT
>      Content-Length: 2331785
>      Content-Type: multipart/byteranges; boundary=THIS_STRING_SEPARATES
>
>      --THIS_STRING_SEPARATES
>      Content-Type: video/example
>      Content-Range: exampleunit 1.2-4.3/25
>
>      ...the first range...
>      --THIS_STRING_SEPARATES
>      Content-Type: video/example
>      Content-Range: exampleunit 11.2-14.3/25
>
>      ...the second range
>      --THIS_STRING_SEPARATES--
> ```

