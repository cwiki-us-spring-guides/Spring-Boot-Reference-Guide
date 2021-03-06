# 49.1 连接远程shell

远程shell默认监听端口为`2000`，默认用户名为`user`，密码为随机生成的，并且在输出日志中会显示。如果应用使用Spring Security，该shell默认使用[相同的配置](https://github.com/cwiki-us-spring-guides/Spring-Boot-Reference-Guide/tree/0047aa8098a650dde0c93f4d2e91754c83468c4b/IV.%20Spring%20Boot%20features/28.%20Security.md)。如果不是，将使用一个简单的认证策略，你可能会看到类似这样的信息：

```java
Using default password for shell access: ec03e16c-4cf4-49ee-b745-7c8255c1dd7e
```

Linux和OSX用户可以使用`ssh`连接远程shell，Windows用户可以下载并安装[PuTTY](http://www.putty.org/)。

```text
$ ssh -p 2000 user@localhost

user@localhost's password:
  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::  (v1.4.1.RELEASE) on myhost
```

输入`help`可以获取命令列表，Spring Boot提供`metrics`，`beans`，`autoconfig`和`endpoint`命令。

