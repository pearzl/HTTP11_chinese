“Content-Range”头字段头字段在单部分的206响应中发送以表明封闭在消息负载中的被选表示的部分范围，在多部分的206响应的每个部分中发送以表明封闭在其中的每个主体部分的范围，以及在416响应中发送以提供关于被选表示的信息。

> ```
>      Content-Range       = byte-content-range
>                          / other-content-range
>
>      byte-content-range  = bytes-unit SP
>                            ( byte-range-resp / unsatisfied-range )
>
>      byte-range-resp     = byte-range "/" ( complete-length / "*" )
>      byte-range          = first-byte-pos "-" last-byte-pos
>      unsatisfied-range   = "*/" complete-length
>
>      complete-length     = 1*DIGIT
>
>      other-content-range = other-range-unit SP other-range-resp
>      other-range-resp    = *CHAR
> ```

如果一个206响应包含一个带有接收者无法理解的范围单元（第2节）的Content-Range头字段，接收者**不得**试图用已存储的表示来重组它。接收到这样消息的代理**应该**将它转发到下游。

对于字节范围，发送者**应该**表明表明这个范围提取处的表示的complete-length，除非完整范围是未知的或难以确定。放在complete-length处的一个星号（“\*”）表示当头字段被生成的时候，表示长度是未知的。

下列例子演示了发送者知道被选表示的complete-length是1234字节时的情况：

> ```
>      Content-Range: bytes 42-1233/1234
> ```

者时第二个例子，演示了complete-length是未知的情况：

> ```
>    Content-Range: bytes 42-1233/*
> ```

如果Content-Range字段值包含一个last-byte-pos比first-byte-pos小，或complete-length的值小于等于last-byte-po的byte-range-resp，那么它是无效的。无效Content-Range的接收者**不得**试图以已存储的表示重组接收到的内容。

对字节范围请求生成416响应的服务器**应该**以不满足的范围值发送一个Content-Range头字段，如下面的例子：

> ```
>      Content-Range: bytes */1234
> ```

Content-Range头字段对于没有明确描述其语义的状态码没有意义。对于本规范，只有206和416状态码描述了Content-Range的含义。

下面是Content-Range值的一些例子，其中被选表示总共包含1234字节：

- 前500字节：

  ```
     Content-Range: bytes 0-499/1234
  ```

- 第二个500字节：

  ```
     Content-Range: bytes 500-999/1234
  ```

- 除了前500个字节：

  ```
     Content-Range: bytes 500-1233/1234
  ```

- 最后500字节：

  ```
     Content-Range: bytes 734-1233/1234
  ```