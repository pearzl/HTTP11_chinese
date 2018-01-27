“WWW-Authenticate”头字段表明认证方案和参数适用于目标资源。

> ```
> WWW-Authenticate = 1#challenge
> ```

生成401响应的服务器**必须**发送一个包含至少一个质询的WWW-Authenticate头字段。服务器**可以**在其他响应消息中生成WWW-Authenticate头字段以表明提供的凭证（或与凭证不同）可能影响响应。

转发响应的代理**不得**修改任何在那个响应中的WWW-Authenticate字段。

建议用户代理在分析字段值的时候要格外小心，因为它可能包含不止一个质询，每个质询都可能包含一个逗号分隔的认证参数列表。进一步，头字段自己也会出现多次。

例如：

> ```
>     WWW-Authenticate: Newauth realm="apps", type=1, title="Login to \"apps\"", Basic realm="simple"
> ```

这个头字段包含两个质询；一个是“Newauth”方案带有一个“app”的域值以及两个额外的参数“type”和“title”，另一个是“Basic”方案带有一个“simple”的域值。

*注意：质询语法生成器也使用列表语法。因此，一个逗号的序列，空白和逗号可以被视为应用于前面的质询或质询列表中的一个空条目。实践中，这个歧义没有影响头字段值中的语义，因此它是无害的。*