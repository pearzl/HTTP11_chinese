以下核心规则包含在RFC RFC347的附录B.1中：ALPHA（字母），CR（回车），CRLF（CR LF），CTL（对照），DIGIT（十进制0-9） ，DQUOTE（双引号），HEXDIG（十六进制0-9 / AF / af），HTAB（水平制表符），LF（换行符），OCTET（任何8位数据序列），SP（空格）和VCHAR 任何可见的US-ASCII字符）。

请注意，从令牌派生的所有规则都将不区分大小写，如范围单位和可接受的范围。

下列规则定义在RFC7230：

> ```
>      OWS        = <OWS, see [RFC7230], Section 3.2.3>
>      token      = <token, see [RFC7230], Section 3.2.6>
> ```

下列规则定义在其他部分：

> ```
>      HTTP-date  = <HTTP-date, see [RFC7231], Section 7.1.1.1>
>      entity-tag = <entity-tag, see [RFC7232], Section 2.3>
> ```

