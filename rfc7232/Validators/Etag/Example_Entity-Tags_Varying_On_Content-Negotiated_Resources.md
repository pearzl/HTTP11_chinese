考虑一个需要内容协商的资源（RFC7231，3.4节），在GET请求的响应中发送的表示基于请求头字段Accept-Encoding而变化（RFC7231，5.3.4节）：

> ```
>    >> Request:
>
>      GET /index HTTP/1.1
>      Host: www.example.com
>      Accept-Encoding: gzip
> ```

在这种情况下，相应可能会也可能不会使用gzip内容编码，如果没有使用，响应可能看起来是这样：

> ```
>    >> Response:
>
>      HTTP/1.1 200 OK
>      Date: Fri, 26 Mar 2010 00:05:00 GMT
>      ETag: "123-a"
>      Content-Length: 70
>      Vary: Accept-Encoding
>      Content-Type: text/plain
>
>      Hello World!
>      Hello World!
>      Hello World!
>      Hello World!
>      Hello World!
>
> ```

使用gzip内容编码的替代表示将是：

> ```
>    >> Response:
>
>      HTTP/1.1 200 OK
>      Date: Fri, 26 Mar 2010 00:05:00 GMT
>      ETag: "123-b"
>      Content-Length: 43
>      Vary: Accept-Encoding
>      Content-Type: text/plain
>      Content-Encoding: gzip
>
>      ...binary data...
>
> ```

*注意：内容编码是表示数据的一个属性，所以一个内容编码表示的强实体标签必须与未编码的表示区分开以防止在缓存更新和范围请求时的潜在冲突。在对比中，转移编码（RFC7230，第4节）只用于消息转移期间不会造成不同的实体标签。*