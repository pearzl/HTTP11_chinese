“Location”头字段在一些响应中被用于指向一个和响应关联的确定的资源。关系的类型由请求方法和状态码语义的组合而定义。

> ```
>     Location = URI-reference
> ```

字段值由一个URI-reference组成。当它是相对引用（RFC3986，4.2节）的形式时，最终的值时通过针对有效请求URI的解析来计算的（RFC3986，5节）。

对201（创建）响应，Location值指向由请求创建的主要资源。对于3xx（重定向）响应，Location值指向对自动重定向请求的首选目标资源。

在一个3xx（重定向）响应中提供的Location值，如果它没有一个片段组件，用户代理**必须**处理重定向，就好像它的值继承了被用于生成请求目标的URI引用的片段组件（即，重定向继承了原始引用的片段，如果有的话）。

例如，一个由“`http://www.example.org/~tim`”URI引用生成的GET可以可能出现一个303（查看其他）响应，包含一个头字段：

> ```
>      Location: /People.html#tim
> ```

这建议用户代理重定向到“`http://www.example.org/People.html#tim`”。

同样，由“`http://www.example.org/index.html#larry`”URI引用生成的GET请求可能出现301（永久移动）响应，包含头字段：

> ```
>     Location: http://www.example.net/index.html
> ```

这建议用户代理重定向到“`http://www.example.net/index.html#larry`”，保留了原始片段标识符。  

某些情况下Location值中的片段标识符是不合适的。例如，在201（创建）响应中的Location头字段被支持提供一个URI，其特定于被创建的资源。

*注意：一些接收者试图恢复无效的URI引用的Location字段。本规范没有要求或定义这种处理，但是稳健性允许这么做。*

*注意：Content-Location头字段（4.1.4.2节）不同于Location，Content-Location指向于封闭表示对应的最具体的资源。因此一个响应包含Location和Content-Location头字段是可能的。*