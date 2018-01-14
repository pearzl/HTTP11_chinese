共享缓存**不得**使用带Authorization头字段请求的缓存响应来满足后续请求，除非允许这个响应被存储的缓存指令出现在响应中。

在这个规范中，下列Cache-Control响应指令有这样的效果：must-revalidate，public，和s-maxage。

注意，包含“must-revalidate”和/或“s-maxage”响应指令的缓存响应不允许被共享缓存提供。特别的，带有“max-age=0, must-revalidate”或“s-maxage=0”的响应不能在未经源服务器校验时被用于满足后续请求。