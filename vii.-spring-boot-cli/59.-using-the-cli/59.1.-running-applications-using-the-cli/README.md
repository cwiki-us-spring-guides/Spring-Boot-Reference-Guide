# 59.1 使用CLI运行应用

你可以使用`run`命令编译和运行Groovy源代码。Spring Boot CLI完全自包含，以致于你不需要安装任何外部的Groovy。

下面是一个使用Groovy编写的"hello world" web应用：

hello.grooy

```java
@RestController
class WebApplication {

    @RequestMapping("/")
    String home() {
        "Hello World!"
    }

}
```

编译和运行应用可以输入：

```text
$ spring run hello.groovy
```

你可以使用`--`将命令行参数和"spring"命令参数区分开来，例如：

```text
$ spring run hello.groovy -- --server.port=9000
```

你可以使用`JAVA_OPTS`环境变量设置JVM命令行参数，例如：

```text
$ JAVA_OPTS=-Xmx1024m spring run hello.groovy
```

