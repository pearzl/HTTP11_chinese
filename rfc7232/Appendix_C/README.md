在下面收集的ABNF中，列表规则根据[RFC7230]的第1.2节进行了扩展。

> ```
>    ETag = entity-tag
>
>    HTTP-date = <HTTP-date, see [RFC7231], Section 7.1.1.1>
>
>    If-Match = "*" / ( *( "," OWS ) entity-tag *( OWS "," [ OWS
>     entity-tag ] ) )
>    If-Modified-Since = HTTP-date
>    If-None-Match = "*" / ( *( "," OWS ) entity-tag *( OWS "," [ OWS
>     entity-tag ] ) )
>    If-Unmodified-Since = HTTP-date
>
>    Last-Modified = HTTP-date
>
>    OWS = <OWS, see [RFC7230], Section 3.2.3>
>
>    entity-tag = [ weak ] opaque-tag
>    etagc = "!" / %x23-7E ; '#'-'~'
>     / obs-text
>
>    obs-text = <obs-text, see [RFC7230], Section 3.2.6>
>    opaque-tag = DQUOTE *etagc DQUOTE
>
>    weak = %x57.2F ; W/
>    
> ```

