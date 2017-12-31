#### 日期/时间 格式

1995年以前，有三种不同的格式普遍用户服务器通讯时间戳。为了与旧实现兼容，这里定义了所有的三种。首选的格式是一个固定长度的单区域的被互联网消息格式（RFC5322）使用的时间和日期规范的子集。

> ```
>     HTTP-date    = IMF-fixdate / obs-date
> ```

首选格式的一个例子是

> ```
>      Sun, 06 Nov 1994 08:49:37 GMT    ; IMF-fixdate
> ```

两种过时的时间格式是

> ```
>      Sunday, 06-Nov-94 08:49:37 GMT   ; obsolete RFC 850 format
>      Sun Nov  6 08:49:37 1994         ; ANSI C's asctime() format
> ```

解析在HTTP头字段中的时间戳接收者**必须**接收所有的三种HTTP日志格式。当发送者生成一个包含一个或多个定义为HTTP-data的时间戳头字段时，发送者**必须**以IMF-fixdate格式生成这些时间戳。

HTTP-date值表示时间作为协调世界时（UTC）的一个实例。前两种格式通过格林尼治标准时间的三个字母缩写“GMT”，即UTC名称的前身表示UTC；asctime格式中的值被假设为UTC的。从本地时钟生成HTTP-date的发送者应该使用NTP（RFC5905）或一些类似的协议来将它的始终与UTC进行同步。

首选格式：

> ```
>      IMF-fixdate  = day-name "," SP date1 SP time-of-day SP GMT
>      ; fixed length/zone/capitalization subset of the format
>      ; see Section 3.3 of [RFC5322]
>
>      day-name     = %x4D.6F.6E ; "Mon", case-sensitive
>                   / %x54.75.65 ; "Tue", case-sensitive
>                   / %x57.65.64 ; "Wed", case-sensitive
>                   / %x54.68.75 ; "Thu", case-sensitive
>                   / %x46.72.69 ; "Fri", case-sensitive
>                   / %x53.61.74 ; "Sat", case-sensitive
>                   / %x53.75.6E ; "Sun", case-sensitive
>                   
>      date1        = day SP month SP year
>                   ; e.g., 02 Jun 1982
>
>      day          = 2DIGIT
>      month        = %x4A.61.6E ; "Jan", case-sensitive
>                   / %x46.65.62 ; "Feb", case-sensitive
>                   / %x4D.61.72 ; "Mar", case-sensitive
>                   / %x41.70.72 ; "Apr", case-sensitive
>                   / %x4D.61.79 ; "May", case-sensitive
>                   / %x4A.75.6E ; "Jun", case-sensitive
>                   / %x4A.75.6C ; "Jul", case-sensitive
>                   / %x41.75.67 ; "Aug", case-sensitive
>                   / %x53.65.70 ; "Sep", case-sensitive
>                   / %x4F.63.74 ; "Oct", case-sensitive
>                   / %x4E.6F.76 ; "Nov", case-sensitive
>                   / %x44.65.63 ; "Dec", case-sensitive
>      year         = 4DIGIT
>
>      GMT          = %x47.4D.54 ; "GMT", case-sensitive
>
>      time-of-day  = hour ":" minute ":" second
>                   ; 00:00:00 - 23:59:60 (leap second)
>
>      hour         = 2DIGIT
>      minute       = 2DIGIT
>      second       = 2DIGIT
>
> ```

过时格式：

> ```
>      obs-date     = rfc850-date / asctime-date
>
>      rfc850-date  = day-name-l "," SP date2 SP time-of-day SP GMT
>      date2        = day "-" month "-" 2DIGIT
>                   ; e.g., 02-Jun-82
>
>      day-name-l   = %x4D.6F.6E.64.61.79    ; "Monday", case-sensitive
>             / %x54.75.65.73.64.61.79       ; "Tuesday", case-sensitive
>             / %x57.65.64.6E.65.73.64.61.79 ; "Wednesday", case-sensitive
>             / %x54.68.75.72.73.64.61.79    ; "Thursday", case-sensitive
>             / %x46.72.69.64.61.79          ; "Friday", case-sensitive
>             / %x53.61.74.75.72.64.61.79    ; "Saturday", case-sensitive
>             / %x53.75.6E.64.61.79          ; "Sunday", case-sensitive
>
>
>      asctime-date = day-name SP date3 SP time-of-day SP year
>      date3        = month SP ( 2DIGIT / ( SP 1DIGIT ))
>                   ; e.g., Jun  2
> ```

HTTP-date时区分大小写的。发送者**不得**在HTTP-date中生成处语法中明确包含的SP之外的额外空白。day-name，day，motn，year，和time-of-day的语义与互联网消息格式构造器中对应名字的定义相同（RFC5322，3.3节）。

rfc850-date格式的时间戳值（它使用两个数字年份）接收者**必须**解析一个数字在过去50年来似乎是过去最近两位数字相同的最近一年的时间戳。

时间戳值的接收者被鼓励在解析时间戳时要健壮，除非字段定义进行限制。例如，消息有时被从一个非HTTP的资源通过HTTP转发，这个非HTTP资源可能生成任何定义在互联网消息格式中的时间和日期规范。

*注意：日期/时间戳格式的HTTP要求仅适用于协议流内的使用。实现不被要求对用户表示和请求日志等使用这些格式。*



#### Date

“Date”头字段表示消息被生成时的日期和时间，与定义在RFC5322的3.6.1节的起源日志字段（orig-date）有相同的语义。字段值是一个HTTP-date，如7.1.1.1节定义。

> ```
>     Date = HTTP-date
> ```

一个例子

> ```
>      Date: Tue, 15 Nov 1994 08:12:31 GMT
> ```

当Date头字段被生成，发送者**应该**发送方应该生成其字段值，作为消息生成日期和时间的最佳可用近似值。理论上，日期应该表示在负载体被生成前的一刻。实践中，日期可以在整个消息构成期间的任何时间被生成。

如果源服务器不能提供一个合理的协调时间时的当前近似实例，它**不得**发送Date头字段。如果响应是1xx（信息）或5xx（服务器错误）类的状态码，服务器**可以**发送Date头字段。源服务器**必须**在所有其他情况下发送Date头字段。

带有时钟的，接收了一个没有Date头字段的响应消息的接收者**必须**记录它被接收到的时间，并且如果他被缓存或者被转发到下游**必须**添加一个对应的Date头字段到消息的头部分。

用户代理**可能**在一个请求中发送Date头字段，虽然一般不会这么做，除非他被信任去传递有用的信息给服务器。例如，如果服务器被期望基于用户代理和服务器时间的差异去调整用户请求的解释，定制的HTTP应用可能传递一个Date。