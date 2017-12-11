HTTP头字段在<http://www.iana.org/assignments/message-headers/>维护的“消息头”注册表中注册。

本文档定义了下列HTTP头字段，所以“永久消息标题字段名称”注册表已经被更新（参阅BCP90）。

> ```
>    +-------------------+----------+----------+---------------+
>    | Header Field Name | Protocol | Status   | Reference     |
>    +-------------------+----------+----------+---------------+
>    | Connection        | http     | standard | Section 6.1   |
>    | Content-Length    | http     | standard | Section 3.3.2 |
>    | Host              | http     | standard | Section 5.4   |
>    | TE                | http     | standard | Section 4.3   |
>    | Trailer           | http     | standard | Section 4.4   |
>    | Transfer-Encoding | http     | standard | Section 3.3.1 |
>    | Upgrade           | http     | standard | Section 6.7   |
>    | Via               | http     | standard | Section 5.7.1 |
>    +-------------------+----------+----------+---------------+
> ```

还有，头字段名“Close”已经被注册用于“保留”，因为使用这个名字作为HTTP头字段可能与Connection头字段（6.1节）的“close”连接选项冲突。

> ```
>    +-------------------+----------+----------+-------------+
>    | Header Field Name | Protocol | Status   | Reference   |
>    +-------------------+----------+----------+-------------+
>    | Close             | http     | reserved | Section 8.1 |
>    +-------------------+----------+----------+-------------+
> ```

变更控制者是：“IETF（iesg@ietf.org） - 互联网工程任务组”。