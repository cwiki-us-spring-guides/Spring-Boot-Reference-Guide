# 70.18 使用Jetty 8

Spring Boot支持Jetty 8，但默认使用的是Jetty 9.3。如果不能使用Jetty 9.3（比如因为你使用的是Java 1.6），你需要改变classpath去引用Jetty 8，还需要排除Jetty的WebSocket相关依赖。

