下面列出的状态码被定义在本协议，RFC7232第4节，RFC7233第4节和RFC7235第三节。这里列出的原因短语只是建议——他们可以被本地等价物替代而不影响协议。

默认被定义为可缓存的状态码（例如，本协议中的200, 203, 204, 206, 300, 301, 404, 405, 410, 414,和501）的响应可以被使用检查过期的缓存复用，除非方法定义表明不可缓存或带有明确的缓存控制（RFC7234）；所有其他状态码默认都是不可缓存的。

> ```
>    +------+-------------------------------+--------------------------+
>    | Code | Reason-Phrase                 | Defined in...            |
>    +------+-------------------------------+--------------------------+
>    | 100  | Continue                      | Section 6.2.1            |
>    | 101  | Switching Protocols           | Section 6.2.2            |
>    | 200  | OK                            | Section 6.3.1            |
>    | 201  | Created                       | Section 6.3.2            |
>    | 202  | Accepted                      | Section 6.3.3            |
>    | 203  | Non-Authoritative Information | Section 6.3.4            |
>    | 204  | No Content                    | Section 6.3.5            |
>    | 205  | Reset Content                 | Section 6.3.6            |
>    | 206  | Partial Content               | Section 4.1 of [RFC7233] |
>    | 300  | Multiple Choices              | Section 6.4.1            |
>    | 301  | Moved Permanently             | Section 6.4.2            |
>    | 302  | Found                         | Section 6.4.3            |
>    | 303  | See Other                     | Section 6.4.4            |
>    | 304  | Not Modified                  | Section 4.1 of [RFC7232] |
>    | 305  | Use Proxy                     | Section 6.4.5            |
>    | 307  | Temporary Redirect            | Section 6.4.7            |
>    | 400  | Bad Request                   | Section 6.5.1            |
>    | 401  | Unauthorized                  | Section 3.1 of [RFC7235] |
>    | 402  | Payment Required              | Section 6.5.2            |
>    | 403  | Forbidden                     | Section 6.5.3            |
>    | 404  | Not Found                     | Section 6.5.4            |
>    | 405  | Method Not Allowed            | Section 6.5.5            |
>    | 406  | Not Acceptable                | Section 6.5.6            |
>    | 407  | Proxy Authentication Required | Section 3.2 of [RFC7235] |
>    | 408  | Request Timeout               | Section 6.5.7            |
>    | 409  | Conflict                      | Section 6.5.8            |
>    | 410  | Gone                          | Section 6.5.9            |
>    | 411  | Length Required               | Section 6.5.10           |
>    | 412  | Precondition Failed           | Section 4.2 of [RFC7232] |
>    | 413  | Payload Too Large             | Section 6.5.11           |
>    | 414  | URI Too Long                  | Section 6.5.12           |
>    | 415  | Unsupported Media Type        | Section 6.5.13           |
>    | 416  | Range Not Satisfiable         | Section 4.4 of [RFC7233] |
>    | 417  | Expectation Failed            | Section 6.5.14           |
>    | 426  | Upgrade Required              | Section 6.5.15           |
>    | 500  | Internal Server Error         | Section 6.6.1            |
>    | 501  | Not Implemented               | Section 6.6.2            |
>    | 502  | Bad Gateway                   | Section 6.6.3            |
>    | 503  | Service Unavailable           | Section 6.6.4            |
>    | 504  | Gateway Timeout               | Section 6.6.5            |
>    | 505  | HTTP Version Not Supported    | Section 6.6.6            |
>    +------+-------------------------------+--------------------------+
> ```

注意，这个清单并不完整，它不包括其他协议中定义的扩展状态码。完整的状态码清单由IANA保留。查看8.2节了解细节。