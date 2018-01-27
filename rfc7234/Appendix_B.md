以下核心规则包含在RFC RFC347的附录B.1中：ALPHA（字母），CR（回车），CRLF（CR LF），CTL（对照），DIGIT（十进制0-9） ，DQUOTE（双引号），HEXDIG（十六进制0-9 / AF / a-f），HTAB（水平制表符），LF（换行符），OCTET（任何8位数据序列），SP（空格）和VCHAR 任何可见的US-ASCII字符）。

下面的规则定义在RFC7230中：

> ```
>      OWS           = <OWS, see [RFC7230], Section 3.2.3>
>      field-name    = <field-name, see [RFC7230], Section 3.2>
>      quoted-string = <quoted-string, see [RFC7230], Section 3.2.6>
>      token         = <token, see [RFC7230], Section 3.2.6>
>
>      port          = <port, see [RFC7230], Section 2.7>
>      pseudonym     = <pseudonym, see [RFC7230], Section 5.7.1>
>      uri-host      = <uri-host, see [RFC7230], Section 2.7>
> ```

下面的规则定义在其他部分：

> ```
>     HTTP-date     = <HTTP-date, see [RFC7231], Section 7.1.1.1>
> ```



