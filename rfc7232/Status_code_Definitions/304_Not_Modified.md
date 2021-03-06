304（未修改）状态码表明条件GET或HEAD请求已经被接收并且如果不是条件评估为假的事实将导致200（OK）响应。换句话说，服务器没有必要转移目标资源的表示，因为这个请求表明发出条件请求的客户端已经由一个有效的表示；服务器因此重定向重定向客户端去使用已存储的表示，就像是在200响应的中携带的表示一样。

生成304响应的服务器**必须**下列头字段，他们已经在相同请求的200响应中发送过：Cache-Control，Content-Location，Date，ETag，Expires，和Vary。

因为304响应的目标是当接收者已经有一个或多个被缓存的表示时最小化信息转移，发送者**不应该**生成上面列出的字段意外的表示元数据，除非所述元数据存在用于指导缓存更新的目的（例如，如果响应没有ETag字段，Last-Modified可能有用）。

对接收到304响应的缓存的要求定义在RFC7234，4.3.4节。如果条件请求源于出站客户端，如一个用户代理他自己的缓存发送了一个条件GET请求到共享代理，那么代理**应该**转发304响应到那个客户端。

304响应不能包含消息体；它总是被头字段之后的第一个空行中断。