大多数HTTP头字段值被定义为使用常见的语法组件（标记，带引号的字符串和注解）以空白或制定的界定字符分隔。界定符被从US-ASCII中不允许在标记中使用的字符集中选取得。

> ```
>     token          = 1*tchar
>
>      tchar          = "!" / "#" / "$" / "%" / "&" / "'" / "*"
>                     / "+" / "-" / "." / "^" / "_" / "`" / "|" / "~"
>                     / DIGIT / ALPHA
>                     ; any VCHAR, except delimiters
> ```

如果文本中的字符串使用一堆引号括起来，那么将其解析为一个值。

> ```
>      quoted-string  = DQUOTE *( qdtext / quoted-pair ) DQUOTE
>      qdtext         = HTAB / SP /%x21 / %x23-5B / %x5D-7E / obs-text
>      obs-text       = %x80-FF
> ```

在一些HTTP头字段中可以包括注解，以括号包围。注解只允许在字段值的定义中包含注解（“comment”）部分的字段中使用。

> ```
>      comment        = "(" *( ctext / quoted-pair / comment ) ")"
>      ctext          = HTAB / SP / %x21-27 / %x2A-5B / %x5D-7E / obs-text
> ```

反斜杠八位字节（“\”）可以用作引用字符串和注释结构中的单字节引用机制。 处理引用字符串值的收件人**必须**处理引用对，就好像它被反斜杠后面的八位字节所取代。

> ```
>    quoted-pair    = "\" ( HTAB / SP / VCHAR / obs-text )
> ```

发送者**不应该**在带引号的字符串中生成引号对，除非需要引用在该字符串中出现的DQUOTE和反斜线八位字节。发送者**不应该**在注释中生成引号对，除非需要在该注释中引用括号[“（”和“）”]和反斜杠八位字节。

