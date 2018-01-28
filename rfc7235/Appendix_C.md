在下面收集的ABNF中，列表规则根据[RFC7230]的第1.2节进行了扩展。

> ```
>
>    Authorization = credentials
>
>    BWS = <BWS, see [RFC7230], Section 3.2.3>
>
>    OWS = <OWS, see [RFC7230], Section 3.2.3>
>
>    Proxy-Authenticate = *( "," OWS ) challenge *( OWS "," [ OWS
>     challenge ] )
>    Proxy-Authorization = credentials
>
>    WWW-Authenticate = *( "," OWS ) challenge *( OWS "," [ OWS challenge
>     ] )
>
>    auth-param = token BWS "=" BWS ( token / quoted-string )
>    auth-scheme = token
>
>    challenge = auth-scheme [ 1*SP ( token68 / [ ( "," / auth-param ) *(
>     OWS "," [ OWS auth-param ] ) ] ) ]
>    credentials = auth-scheme [ 1*SP ( token68 / [ ( "," / auth-param )
>     *( OWS "," [ OWS auth-param ] ) ] ) ]
>
>    quoted-string = <quoted-string, see [RFC7230], Section 3.2.6>
>
>    token = <token, see [RFC7230], Section 3.2.6>
>    token68 = 1*( ALPHA / DIGIT / "-" / "." / "_" / "~" / "+" / "/" )
>     *"="
>
> ```
>
> 