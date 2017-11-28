分块编码允许每个分块为了提供每个分块元数据，中期消息的控制信息，或者随机的消息体尺寸的缘故包括零个或多个分块扩展，其紧跟在chunk-size后面。

> ```
>      chunk-ext      = *( ";" chunk-ext-name [ "=" chunk-ext-val ] )
>
>      chunk-ext-name = token
>      chunk-ext-val  = token / quoted-string
> ```

