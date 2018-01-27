在下面收集的ABNF中，列表规则根据[RFC7230]的第1.2节进行了扩展。

> ```
>    Age = delta-seconds
>
>    Cache-Control = *( "," OWS ) cache-directive *( OWS "," [ OWS cache-directive ] )
>
>    Expires = HTTP-date
>
>    HTTP-date = <HTTP-date, see [RFC7231], Section 7.1.1.1>
>
>    OWS = <OWS, see [RFC7230], Section 3.2.3>
>
>    Pragma = *( "," OWS ) pragma-directive *( OWS "," [ OWS pragma-directive ] )
>
>    Warning = *( "," OWS ) warning-value *( OWS "," [ OWS warning-value ] )
>
>    cache-directive = token [ "=" ( token / quoted-string ) ]
>
>    delta-seconds = 1*DIGIT
>
>    extension-pragma = token [ "=" ( token / quoted-string ) ]
>
>    field-name = <field-name, see [RFC7230], Section 3.2>
>
>    port = <port, see [RFC7230], Section 2.7>
>    pragma-directive = "no-cache" / extension-pragma
>    pseudonym = <pseudonym, see [RFC7230], Section 5.7.1>
>
>    quoted-string = <quoted-string, see [RFC7230], Section 3.2.6>
>
>    token = <token, see [RFC7230], Section 3.2.6>
>
>    uri-host = <uri-host, see [RFC7230], Section 2.7>
>
>    warn-agent = ( uri-host [ ":" port ] ) / pseudonym
>    warn-code = 3DIGIT
>    warn-date = DQUOTE HTTP-date DQUOTE
>    warn-text = quoted-string
>    warning-value = warn-code SP warn-agent SP warn-text [ SP warn-date ]
>
> ```

