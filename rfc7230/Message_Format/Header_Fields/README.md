每个头字段由以下部分组成：一个不区分大小写的字段名称，一个英文冒号（“:”），可选的前导空格，字段值，和可选的结尾空格。

> ```
>      header-field   = field-name ":" OWS field-value OWS
>
>      field-name     = token
>      field-value    = *( field-content / obs-fold )
>      field-content  = field-vchar [ 1*( SP / HTAB ) field-vchar ]
>      field-vchar    = VCHAR / obs-text
>
>      obs-fold       = CRLF 1*( SP / HTAB )
>                     ; obsolete line folding
>                     ; see Section 3.2.4
> ```

字段名标记将对应字段值标记为由那个头字段定义的语义。例如Date头字段在RFC7231中7.1.1.2节定义为包含它的消息出现的起始时间戳。