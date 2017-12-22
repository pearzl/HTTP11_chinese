请求方法令牌是请求语义的主要来源；它指示客户端发起这个请求的目的和客户端期望的作为成功结果的内容。

当一些头字段在请求中（第5节）出现时，如果他们的语义与方法没有产生冲突，请求方法语义可以进一步细化。例如，客户端可以发送条件请求头字段（5.2节）使得在目标资源（RFC7232）的当前状态下被请求的目标动作有条件。

> ```
>      method = token
> ```

HTTP本来就被设计为可以用作分布式对象系统的接口。请求方法被设想为目标资源的应用语义，与对一个确定的对象调用定义的方法进行语义应用相同。方法令牌是区分大小写的，因为他可能被用作一个基于对象系统的带有区分大小写方法名的网关。

不像分布式对象，HTTP中标准化的请求方法不是资源专用的，因为统一接口提供了更好的可见度和基于网络系统的重用。一旦定义，当一个标准化的方法应用到任何资源时应该有相同的语义，但每个资源自己确定是否实现了这些语义。

本协议定义了一些在HTTP中普遍被使用的标准方法，由下表列出。依照惯例，标准方法被定义为全部都是US-ASCII大写字符。

> ```
>    +---------+-------------------------------------------------+-------+
>    | Method  | Description                                     | Sec.  |
>    +---------+-------------------------------------------------+-------+
>    | GET     | Transfer a current representation of the target | 4.3.1 |
>    |         | resource.                                       |       |
>    | HEAD    | Same as GET, but only transfer the status line  | 4.3.2 |
>    |         | and header section.                             |       |
>    | POST    | Perform resource-specific processing on the     | 4.3.3 |
>    |         | request payload.                                |       |
>    | PUT     | Replace all current representations of the      | 4.3.4 |
>    |         | target resource with the request payload.       |       |
>    | DELETE  | Remove all current representations of the       | 4.3.5 |
>    |         | target resource.                                |       |
>    | CONNECT | Establish a tunnel to the server identified by  | 4.3.6 |
>    |         | the target resource.                            |       |
>    | OPTIONS | Describe the communication options for the      | 4.3.7 |
>    |         | target resource.                                |       |
>    | TRACE   | Perform a message loop-back test along the path | 4.3.8 |
>    |         | to the target resource.                         |       |
>    +---------+-------------------------------------------------+-------+
> ```

所有通用目的的服务器必须支持GET和HEAD。所有其他方法都是可选的。

超出本协议范围之外的额外方法已经被标准化来在HTTP中使用。所有的这种方法应该被注册在“超文本转移协议（HTTP）方法注册表”中由INAN保持，如8.1节定义。

一个目标资源允许的方法的集合可以在Allow头字段中被列出（7.4.1节）。然而，被允许的方法集合可以动态改变。当一个源服务器没有实现或者无法识别的请求方法被接收到时，源服务器**应该**响应501（未实现）状态码。当一个源服务器知道但是不被目标资源允许的请求方法被接收到时，源服务器**应该**响应405（方法不被允许）状态码。