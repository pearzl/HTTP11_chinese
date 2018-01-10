“Accept-Ranges”头字段允许一个服务器表明它支持对目标资源的范围请求。

> ```
>      Accept-Ranges     = acceptable-ranges
>      acceptable-ranges = 1#range-unit / "none"
> ```

支持对给定目标资源进行范围请求的源服务器**可能**发送

> ```
>      Accept-Ranges: bytes
> ```

以表明什么范围单元被支持。客户端**可能**对涉及到的资源没有收到这个头字段的时候生成范围请求。范围单元被定义在第2节。

对目标资源不支持任何范围请求的服务器**可能**发送

> ```
>      Accept-Ranges: none
> ```

以告知客户端不要尝试范围请求。