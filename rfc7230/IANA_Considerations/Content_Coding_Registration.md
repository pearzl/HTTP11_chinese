IANA在<http://www.iana.org/assignments/http-parameters>维护“HTTP内容编码注册表”。

“HTTP内容编码注册表”已经被下列注册更新：

> ```
>    +------------+--------------------------------------+---------------+
>    | Name       | Description                          | Reference     |
>    +------------+--------------------------------------+---------------+
>    | compress   | UNIX "compress" data format [Welch]  | Section 4.2.1 |
>    | deflate    | "deflate" compressed data            | Section 4.2.2 |
>    |            | ([RFC1951]) inside the "zlib" data   |               |
>    |            | format ([RFC1950])                   |               |
>    | gzip       | GZIP file format [RFC1952]           | Section 4.2.3 |
>    | x-compress | Deprecated (alias for compress)      | Section 4.2.1 |
>    | x-gzip     | Deprecated (alias for gzip)          | Section 4.2.3 |
>    +------------+--------------------------------------+---------------+
>
> ```