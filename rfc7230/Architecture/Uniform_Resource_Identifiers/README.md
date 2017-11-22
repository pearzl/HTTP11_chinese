整个HTTP使用统一资源标识符（URIs）[RFC3986]作为识别资源（[RFC7231]的第2节）的方式。URI引用用于定位请求，指示重定向和定义关系。

对"URI-reference", "absolute-URI", "relative-part", "scheme", "authority", "port", "host", "path-abempty", "segment", "query", and "fragment" 的定义采用通用URI语法。"absolute-path"规则是为可以包含一个非空的路径组件的协议元素而定义的。（这个规则与RFC3986中的path-abempty规则略有不同，它允许在引用中使用空路径，而path-absolute规则不允许“//”开头的路径。）"partial-URI"规则是为可以包含一个相对URI但不包含片段组件的协议元素而定义的。

> ```
>     URI-reference = <URI-reference, see [RFC3986], Section 4.1>
>     absolute-URI  = <absolute-URI, see [RFC3986], Section 4.3>
>     relative-part = <relative-part, see [RFC3986], Section 4.2>
>     scheme        = <scheme, see [RFC3986], Section 3.1>
>     authority     = <authority, see [RFC3986], Section 3.2>
>     uri-host      = <host, see [RFC3986], Section 3.2.2>
>     port          = <port, see [RFC3986], Section 3.2.3>
>     path-abempty  = <path-abempty, see [RFC3986], Section 3.3>
>     segment       = <segment, see [RFC3986], Section 3.3>
>     query         = <query, see [RFC3986], Section 3.4>
>     fragment      = <fragment, see [RFC3986], Section 3.5>
>
>     absolute-path = 1*( "/" segment )
>     partial-URI   = relative-part [ "?" query ]
> ```

HTTP中的每个允许URI引用的协议元素将在其ABNF生成中指示该元素是否允许任何形式的引用（URI引用），仅绝对形式的URI（absolute-URI），仅路径和可选的查询组件，或者上述的一些组合。除非另有说明，否则URI引用将相对于有效的请求URI（5.5节）进行解析。
