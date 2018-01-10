由于表示数据以8位字节序列的形式在负载中转移，字节范围对任何可通过HTTP转移的表示都是有意义的子结构（RFC7231，第3节）。“byte”范围单位被定义用于表示数据字节序列的子范围。

> ```
>     bytes-unit       = "bytes"
> ```

一个字节范围请求可以指定一个单独的字节范围或一个表示内的一组范围。

> ```
>      byte-ranges-specifier = bytes-unit "=" byte-range-set
>      byte-range-set  = 1#( byte-range-spec / suffix-byte-range-spec )
>      byte-range-spec = first-byte-pos "-" [ last-byte-pos ]
>      first-byte-pos  = 1*DIGIT
>      last-byte-pos   = 1*DIGIT
> ```

`byte-range-spec`中的`first-byt-pos`值给出了范围中第一个字节的字节偏移量。`last-byte-pos`值给出了范围中最后一个字节的字节偏移；也就是说，被指定的字节是被包括的。字节偏移从零开始。

`byte-ranges-specifier`值的例子：

- 第一个500个字节（字节偏移0-499，包括）：

  ```byte=0-499```

- 第二个500个字节（字节偏移500-999，包括）：

  ```bytes=500-999```

如果`last-byte-post`值出现了并小于`first-byte-pos`，那么`byte-range-spec`是无效的。

客户端可以在不知道被选表示大小的情况下限制被请求字节的数量。如果`last-byte-pos`值缺失或者它的值大于等于表示数据的当前长度，那么字节范围被解释为表示的余下部分（即，服务器以比被选表示的当前长度小一的值替换`last-byte-pos`值）。

客户端可以使用`suffix-byte-range-spec`来请求被选表示的最后N个字节。

> ```
>      suffix-byte-range-spec = "-" suffix-length
>      suffix-length = 1*DIGIT
> ```

如果被选表示比指定的`suffix-length`短，那么就使用整个表示。

额外的例子，假定一个长度为10000的表示：

- 最后500个字节（字节偏移9500-9999，包括）：

  ```bytes=-500``` 或者```bytes=9500-```

- 第一个和最后一个字节（字节0和9999）：

  ```bytes=0-0,-1```

- 其他有效（但不规范）的第二个500字节格式（字节偏移500-999，包括）：

  ```
  bytes=500-600,601-999
  bytes=500-700,601-999
  ```

如果一个有效的`byte-range-set`包括至少一个带有`first-byte-post`且其值小于表示的当前长度的`byte-range-spec`，或至少一个带有非零`suffix-length`的`suffix-byte-range-spec`，那么`byte-range-set`是可满足的。否则，`byte-range-set`是不满足的。

在字节范围语法中，`first-byte-pos`，`last-byte-pos`和`suffix-leng`被表示为字节十进制数。因为没有预定义的负载体限制，接收者**必须**能够预料大的十进制数，并避免因整数转换溢出的系欸错误。