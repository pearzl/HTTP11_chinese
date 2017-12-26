"Accept-Encoding"头字段可以被用户代理发送以表明响应中可接受的响应内容编码（3.1.2.1节）。一个“标识”记号被用作“无编码”的代名词以进行在无编码优先时的通讯。

> ```
>      Accept-Encoding  = #( codings [ weight ] )
>      codings          = content-coding / "identity" / "*"
> ```

每个编码值**可能**给赋予一个关联的质量值标识那个编码的优先级，如5.3.1定义。Accept-Encoding字段中星号“\*”匹配任何没有在头字段中明确列出的内容编码。

例如，

> ```
>      Accept-Encoding: compress, gzip
>      Accept-Encoding:
>      Accept-Encoding: *
>      Accept-Encoding: compress;q=0.5, gzip;q=1.0
>      Accept-Encoding: gzip;q=1.0, identity; q=0.5, *;q=0
> ```

没有Accept-Encoding头字段的请求暗示用户代理内容编码没有优先级。虽然这允许服务器在响应中使用内容编码，但它不意味着用户代理能够正确的处理编码。 

服务测试对于给定表示的一个内容编码是否是可接受的使用这些规则：

1. 如果没有Accept-Encoding字段在请求中，任何内容编码都将被用户代理视为可接受的。
2. 如果表示没有内容编码，那么它默认是可接受的，除非由Accept-Encoding字段为“`identity;q=0`“或者对于”identity“没有更具体条目的”`*;q=0`“特别排除。
3. 如果表示的内容编码是Accept-Encoding中列出的一个，那么它是可接受的，除非伴随一个为0的q值。（如5.3.1节定义，q值为0表示”不可接受“）
4. 如果多个内容编码都是可接受的，那么q值最高的可接受内容编码是优先的。

带有空组合字段值的Accept-Encoding头字段暗示用户代理不想在响应中使用任何内容编码。如果一个Accept-Encoding头字段出现在请求中并且响应的可用表示没有在可接受的内容编码中列出，源服务器**应该**发送一个没有内容编码的响应。

*注意：大多数的HTTP/1.0应用程序不识别或不遵循q值关联的内容编码。这意味着q值可能不生效并且不被x-gzip或x-compress允许。*