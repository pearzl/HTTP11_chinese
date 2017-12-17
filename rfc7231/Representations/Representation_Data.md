与HTTP消息相关联的表示数据或者作为消息的有效载荷体提供，或者由消息语义和有效请求URI来引用。表示数据采用由表示元数据头字段定义的格式和编码。

表示数据的数据类型是通过投资段Content-Type和Content-Encoding来决定的。他们定义了一个两层的有序编码模型：
> ```
>    representation-data := Content-Encoding( Content-Type( bits ) )
> ```