一旦获得入站链接，客户端会发送一个带有从目标URI派生出request-target的HTTP请求消息（第3节）。request-target有四种不同的格式，基于被请求的方法和请求是否面向一个代理。

> ```
>      request-target = origin-form
>                     / absolute-form
>                     / authority-form
>                     / asterisk-form
> ```

