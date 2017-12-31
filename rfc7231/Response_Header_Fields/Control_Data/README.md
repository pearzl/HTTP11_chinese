响应头字段可以提供补充状态码，缓存指令，或指示客户端接下来去哪的控制数据。

> ```
>    +-------------------+--------------------------+
>    | Header Field Name | Defined in...            |
>    +-------------------+--------------------------+
>    | Age               | Section 5.1 of [RFC7234] |
>    | Cache-Control     | Section 5.2 of [RFC7234] |
>    | Expires           | Section 5.3 of [RFC7234] |
>    | Date              | Section 7.1.1.2          |
>    | Location          | Section 7.1.2            |
>    | Retry-After       | Section 7.1.3            |
>    | Vary              | Section 7.1.4            |
>    | Warning           | Section 5.5 of [RFC7234] |
>    +-------------------+--------------------------+
> ```