“Proxy-Authorization”头字段允许客户端对一个要求认证的代理识别它自己（或它的用户）。它的值由包含对代理和/或被请求资源的域的认证客户端认证信息的凭证组成。

> ```
>      Proxy-Authorization = credentials
> ```

域Authorization不同，Proxy-Authorization头字段只应用于要求适用Proxy-Authenticate字段认证的下一个入站代理。当一个链中使用多个代理时，Proxy-Authorization头字段被第一个期望接受凭证的入站代理消费。代理**可以**将来自客户端请求的证书中继到下一个代理，如果这是代理协作认证给定请求的机制。