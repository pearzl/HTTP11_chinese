“Proxy-Authenticate”头字段由至少一个表明质询方案和对这个有效请求URI（RFC7230，5.5节）适用于代理的参数的质询组成。代理**必须**在它生成的407响应中发送至少一个Proxy-Authenticate头字段。

> ```
>      Proxy-Authenticate = 1#challenge
> ```

与WWW-Authenticate不同，Proxy-Authenticate头字段只作用于响应链上的下一个出站客户端。这是因为只有选择给定代理的客户端由可能具有认证的必要凭证。但是，当相同的管理域中使用多个代理时，如大型企业网络中的官方和区域缓存代理，对于认证凭证来说由用户代理生成以及通过层次结构直到被消耗是很常见的。于是，在这样的配置下，它将会出现就好像Proxy-Authenticate被转发一样。因为每个代理都会发送相同的质询集。

注意对WWW-Authenticate的解析注意事项也同样应用于这个字段；产看4.1节了解详细信息。