传输编码名称被用于指定已经、能够或者可能用于有效载体的编码转换，以确保通过网络安全传输。这与内容编码的不同之处在于，传送编码是消息的属性，而不是正在传送的表示的属性。

> ```
>      transfer-coding    = "chunked" ; Section 4.1
>                         / "compress" ; Section 4.2.1
>                         / "deflate" ; Section 4.2.2
>                         / "gzip" ; Section 4.2.3
>                         / transfer-extension
>      transfer-extension = token *( OWS ";" OWS transfer-parameter )
>
> ```

参数采用名称或者名称=值对的形式。

> ```
>  transfer-parameter = token BWS "=" BWS ( token / quoted-string )
> ```

传输编码的名字是不区分大小写的，并且应该在HTTP传输编码注册除进行注册，这在8.4节定义。他们被用于TE（4.3节）和Transfer-Encoding（3.3.1节）头字段。