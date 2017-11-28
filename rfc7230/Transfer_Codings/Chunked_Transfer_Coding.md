分块传输编码包装有效载荷体将其以一系列分块的形式传输，每一个分块有它字节的尺寸指示符，之后是一个包含头字段的可选尾部标记。Chunked使未知大小的内容流能够作为一系列长度分隔的缓冲区进行传输，从而使发送方能够保持连接持久性，并使接收方知道何时接收到整个消息。

> ```
>      chunked-body   = *chunk
>                       last-chunk
>                       trailer-part
>                       CRLF
>
>      chunk          = chunk-size [ chunk-ext ] CRLF
>                       chunk-data CRLF
>      chunk-size     = 1*HEXDIG
>      last-chunk     = 1*("0") [ chunk-ext ] CRLF
>
>      chunk-data     = 1*OCTET ; a sequence of chunk-size octets
> ```

chunk-size字段是一个十六进制数字的字符串指示分块数据的字节尺寸。当一个chunk-size为0的分块被接收到，可能跟随一个尾标并且最后由一个空行终止，那么分块传输就完成了。

接收者**必须**能够解析并解码分块传输编码。