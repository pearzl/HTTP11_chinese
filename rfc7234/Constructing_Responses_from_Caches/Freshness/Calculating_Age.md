Age头字段用来传达一个预估的响应消息存在于缓存的年龄。Age字段值是从响应被生成或从源服务器校验的秒数的缓存的估计值。本质上，Age值是一些时间的总和，即响应被留在从源服务器开始沿着的每个缓存的时间，加上沿着网络路径中转的时间总和。

下列的数据被用于年龄计算：

- age_value

  “age_value”表示Age头字段的值（5.1节），以适合于算术运算的形式，如果不可用则是0。

- date_value

  “date_value”表示Date头字段的值，以适合于算术运算的形式。查看RFC7231，7.1.1.2节了解Date头字段的定义和没有这个头的响应的相关要求。

- now

  “now”表示“在执行计算的主机上的当前时钟值”。一个主机应该使用NTP（RFC5905）或类似的协议来同步它的时钟到协调时间。

- request_time

   导致已存储响应的请求被完成的时候，主机的当前时钟值。

- response_time

  响应被接收到的时候，主机上的时钟值。

响应的年龄可以以两个完全独立的方法计算得到：

1. “apparent_age”：response_time减去date_value，如果本地时钟是与源服务器的时钟同步的。如果结构是负的，那么结果用0替代。
2. “corrected_age_value”：如果所有的缓存路径上的实现都是HTTP/1.1。缓存**必须**相对于请求被发起的时间解析这个值，而不是响应被接收端哦的时间。

> ```
>      apparent_age = max(0, response_time - date_value);
>
>      response_delay = response_time - request_time;
>      corrected_age_value = age_value + response_delay;
> ```

组合成

> ```
>      corrected_initial_age = max(apparent_age, corrected_age_value);
> ```

已存储响应的current_age可以被通过添加一系列时间（以秒为单位）来计算，因为已存储响应是持续与源服务器校验到corrected_initial_age。

> ```
>      resident_time = now - response_time;
>      current_age = corrected_initial_age + resident_time;
> ```

