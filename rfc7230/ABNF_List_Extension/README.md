使用[RFC5234]的ABNF规则的#规则扩展来提高某些头字段值的定义中的可读性。

一个构造“#”被定义，与“*”类似，用于定义逗号分隔的元素列表。其完整形式是“`<n>#<m>element`”，表示最少`<n>`并且最多`<m>`个元素，每个元素被一个逗号（”,“）和可选的空白（OWS）分隔。

在任何使用列表结构的生产中，发送者**不得**生成空的列表元素。换句话说，发送者**必须**生成满足下列语法的列表：

> ```
> 1#element => element *( OWS "," OWS element )
> ```

以及：

> ```
> #element => [ 1#element ]
> ```

对于`n >= 1`和`m > 1`的情况：

> ```
> <n>#<m>element => element <n-1>*<m-1>( OWS "," OWS element )
> ```

为了兼容传统列表规则，接收者**必须**解析和忽略合理数量的空白元素列表，这个数量足够处理合并值的发送者产生的常见错误，但不至于被作为一种拒绝服务（dos）机制。换句话说，接收者**必须**接受满足下列语法的列表：

> ```
>      #element => [ ( "," / element ) *( OWS "," [ OWS element ] ) ]
>      1#element => *( "," OWS ) element *( OWS "," [ OWS element ] )
> ```

 空的元素对统计元素的出现没有贡献。例如，给定这些ABNF产生式：

> ```
> example-list      = 1#example-list-elmt
> example-list-elmt = token ; see Section 3.2.6
> ```

那么下面是有效的example-list（不包括双引号，他们仅为了划定界限出现）：

> ```
>    "foo,bar"
>      "foo ,bar,"
>      "foo , ,bar,charlie   "
> ```

相反，下面这些值是无效的，因为example-list的产生式要求至少一个非空元素：

> ```
>      ""
>      ","
>      ",   ,"
> ```

附录B列出了扩展列表结构后为接收者收集的ABNF。