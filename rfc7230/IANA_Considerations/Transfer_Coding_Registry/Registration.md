“HTTP传输编码注册表”已更新，注册如下：

> ```
>    +------------+--------------------------------------+---------------+
>    | Name       | Description                          | Reference     |
>    +------------+--------------------------------------+---------------+
>    | chunked    | Transfer in a series of chunks       | Section 4.1   |
>    | compress   | UNIX "compress" data format [Welch]  | Section 4.2.1 |
>    | deflate    | "deflate" compressed data            | Section 4.2.2 |
>    |            | ([RFC1951]) inside the "zlib" data   |               |
>    |            | format ([RFC1950])                   |               |
>    | gzip       | GZIP file format [RFC1952]           | Section 4.2.3 |
>    | x-compress | Deprecated (alias for compress)      | Section 4.2.1 |
>    | x-gzip     | Deprecated (alias for gzip)          | Section 4.2.3 |
>    +------------+--------------------------------------+---------------+
> ```