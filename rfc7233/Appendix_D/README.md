```
   In the collected ABNF below, list rules are expanded as per Section 1.2 of [RFC7230].

   Accept-Ranges = acceptable-ranges

   Content-Range = byte-content-range / other-content-range

   HTTP-date = <HTTP-date, see [RFC7231], Section 7.1.1.1>

   If-Range = entity-tag / HTTP-date

   OWS = <OWS, see [RFC7230], Section 3.2.3>

   Range = byte-ranges-specifier / other-ranges-specifier

   acceptable-ranges = ( *( "," OWS ) range-unit *( OWS "," [ OWS range-unit ] ) ) / "none"

   byte-content-range = bytes-unit SP ( byte-range-resp / unsatisfied-range )
   byte-range = first-byte-pos "-" last-byte-pos
   byte-range-resp = byte-range "/" ( complete-length / "*" )
   byte-range-set = *( "," OWS ) ( byte-range-spec / suffix-byte-range-spec ) *( OWS "," [ OWS ( byte-range-spec / suffix-byte-range-spec ) ] )
   byte-range-spec = first-byte-pos "-" [ last-byte-pos ]
   byte-ranges-specifier = bytes-unit "=" byte-range-set
   bytes-unit = "bytes"

   complete-length = 1*DIGIT

   entity-tag = <entity-tag, see [RFC7232], Section 2.3>

   first-byte-pos = 1*DIGIT

   last-byte-pos = 1*DIGIT

   other-content-range = other-range-unit SP other-range-resp
   other-range-resp = *CHAR
   other-range-set = 1*VCHAR
   other-range-unit = token
   other-ranges-specifier = other-range-unit "=" other-range-set

   range-unit = bytes-unit / other-range-unit

   suffix-byte-range-spec = "-" suffix-length
      
   suffix-length = 1*DIGIT

   token = <token, see [RFC7230], Section 3.2.6>

   unsatisfied-range = "*/" complete-length

```