#### 媒体类型

HTTP在Content-Type（3.1.1.5节）和Accept（5.3.2节）头字段中使用网络媒体类型（RFC2046）以提供开放和可扩展的数据类型和类型协商。媒体类型定义了数据格式和如何根据它接受到的数据内容进行处理的各种处理模型。

> ```
>     media-type = type "/" subtype *( OWS ";" OWS parameter )
>     type       = token
>     subtype    = token 
> ```

type/subtype**可以**以`名称=值`对的形式跟随参数。

> ```
>   parameter      = token "=" ( token / quoted-string )
> ```

type, subtype, parameter的名称标识符不区分大小写。参数值可能是也可能不是区分大小写的，这取决于参数名的语义。一个参数的存在或者缺失对于一个媒体类型的处理可能是意义重大的，这取决于它在媒体类型注册表中的定义。

与令牌生产器匹配的参数值可以作为令牌或带引号的字符串传送。带引号和不带引号的值是相等的。例如，下面的几个例子是完全等价的，但是从一致性考虑第一个更好：

> ```
>     text/html;charset=utf-8
>     text/html;charset=UTF-8
>     Text/HTML;Charset="utf-8"
>     text/html; charset="utf-8"
> ```

网络媒体类型应该通过BCP13定义的程序以IANA进行注册。

*注意：不同于其他头字段的构造，媒体类型参数在等号两边不允许空白（甚至是“坏”空白）*


#### 字符集

HTTP使用字符集的名称来识别或协商文本表示形式（RFC6365）的字符编码方案。字符集通过不区分大小写的令牌来识别。

> ```
>    charset = token
> ```

字符集的名称应该通过RFC2978定义的程序注册到IANA“字符集合”注册表中。


#### 规范化和文本默认值








