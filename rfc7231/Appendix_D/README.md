在下面收集的ABNF中，列表规则根据[RFC7230]的第1.2节进行了扩展。

> ```
>    Accept = [ ( "," / ( media-range [ accept-params ] ) ) *( OWS "," [
>     OWS ( media-range [ accept-params ] ) ] ) ]
>    Accept-Charset = *( "," OWS ) ( ( charset / "*" ) [ weight ] ) *( OWS
>     "," [ OWS ( ( charset / "*" ) [ weight ] ) ] )
>    Accept-Encoding = [ ( "," / ( codings [ weight ] ) ) *( OWS "," [ OWS
>     ( codings [ weight ] ) ] ) ]
>    Accept-Language = *( "," OWS ) ( language-range [ weight ] ) *( OWS
>     "," [ OWS ( language-range [ weight ] ) ] )
>    Allow = [ ( "," / method ) *( OWS "," [ OWS method ] ) ]
>
>    BWS = <BWS, see [RFC7230], Section 3.2.3>
>
>    Content-Encoding = *( "," OWS ) content-coding *( OWS "," [ OWS
>     content-coding ] )
>    Content-Language = *( "," OWS ) language-tag *( OWS "," [ OWS
>     language-tag ] )
>    Content-Location = absolute-URI / partial-URI
>    Content-Type = media-type
>
>    Date = HTTP-date
>
>    Expect = "100-continue"
>
>    From = mailbox
>
>    GMT = %x47.4D.54 ; GMT
>
>    HTTP-date = IMF-fixdate / obs-date
>
>    IMF-fixdate = day-name "," SP date1 SP time-of-day SP GMT
>
>    Location = URI-reference
>
>    Max-Forwards = 1*DIGIT
>
>    OWS = <OWS, see [RFC7230], Section 3.2.3>
>
>    RWS = <RWS, see [RFC7230], Section 3.2.3>
>    Referer = absolute-URI / partial-URI
>    Retry-After = HTTP-date / delay-seconds
>    
>    Server = product *( RWS ( product / comment ) )
>
>    URI-reference = <URI-reference, see [RFC7230], Section 2.7>
>    User-Agent = product *( RWS ( product / comment ) )
>
>    Vary = "*" / ( *( "," OWS ) field-name *( OWS "," [ OWS field-name ]
>     ) )
>
>    absolute-URI = <absolute-URI, see [RFC7230], Section 2.7>
>    accept-ext = OWS ";" OWS token [ "=" ( token / quoted-string ) ]
>    accept-params = weight *accept-ext
>    asctime-date = day-name SP date3 SP time-of-day SP year
>
>    charset = token
>    codings = content-coding / "identity" / "*"
>    comment = <comment, see [RFC7230], Section 3.2.6>
>    content-coding = token
>
>    date1 = day SP month SP year
>    date2 = day "-" month "-" 2DIGIT
>    date3 = month SP ( 2DIGIT / ( SP DIGIT ) )
>    day = 2DIGIT
>    day-name = %x4D.6F.6E ; Mon
>     / %x54.75.65 ; Tue
>     / %x57.65.64 ; Wed
>     / %x54.68.75 ; Thu
>     / %x46.72.69 ; Fri
>     / %x53.61.74 ; Sat
>     / %x53.75.6E ; Sun
>    day-name-l = %x4D.6F.6E.64.61.79 ; Monday
>     / %x54.75.65.73.64.61.79 ; Tuesday
>     / %x57.65.64.6E.65.73.64.61.79 ; Wednesday
>     / %x54.68.75.72.73.64.61.79 ; Thursday
>     / %x46.72.69.64.61.79 ; Friday
>     / %x53.61.74.75.72.64.61.79 ; Saturday
>     / %x53.75.6E.64.61.79 ; Sunday
>    delay-seconds = 1*DIGIT
>
>    field-name = <comment, see [RFC7230], Section 3.2>
>
>    hour = 2DIGIT
>
>    language-range = <language-range, see [RFC4647], Section 2.1>
>    language-tag = <Language-Tag, see [RFC5646], Section 2.1>
>
>    mailbox = <mailbox, see [RFC5322], Section 3.4>
>    media-range = ( "*/*" / ( type "/*" ) / ( type "/" subtype ) ) *( OWS
>     ";" OWS parameter )
>    media-type = type "/" subtype *( OWS ";" OWS parameter )
>    method = token
>    minute = 2DIGIT
>    month = %x4A.61.6E ; Jan
>     / %x46.65.62 ; Feb
>     / %x4D.61.72 ; Mar
>     / %x41.70.72 ; Apr
>     / %x4D.61.79 ; May
>     / %x4A.75.6E ; Jun
>     / %x4A.75.6C ; Jul
>     / %x41.75.67 ; Aug
>     / %x53.65.70 ; Sep
>     / %x4F.63.74 ; Oct
>     / %x4E.6F.76 ; Nov
>     / %x44.65.63 ; Dec
>
>    obs-date = rfc850-date / asctime-date
>
>    parameter = token "=" ( token / quoted-string )
>    partial-URI = <partial-URI, see [RFC7230], Section 2.7>
>    product = token [ "/" product-version ]
>    product-version = token
>    quoted-string = <quoted-string, see [RFC7230], Section 3.2.6>
>    qvalue = ( "0" [ "." *3DIGIT ] ) / ( "1" [ "." *3"0" ] )
>
>    rfc850-date = day-name-l "," SP date2 SP time-of-day SP GMT
>
>    second = 2DIGIT
>    subtype = token
>
>    time-of-day = hour ":" minute ":" second
>    token = <token, see [RFC7230], Section 3.2.6>
>    type = token
>
>    weight = OWS ";" OWS "q=" qvalue
>
>    year = 4DIGIT
> ```
>
> 