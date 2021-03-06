# 56. 安装Spring Boot应用

除了使用`java -jar`运行Spring Boot应用，制作在Unix系统完全可执行的应用也是可能的，这会简化常见生产环境Spring Boot应用的安装和管理。在Maven中添加以下plugin配置可以创建一个"完全可执行"jar：

```markup
<plugin>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-maven-plugin</artifactId>
    <configuration>
        <executable>true</executable>
    </configuration>
</plugin>
```

对于Gradle等价的配置如下：

```text
apply plugin: 'spring-boot'

springBoot {
    executable = true
}
```

然后输入`./my-application.jar`运行应用（`my-application`是你的artifact name）。

**注** 完全可执行jars在文件前内嵌了一个额外脚本，目前不是所有工具都能接受这种形式，所以你有时可能不能使用该技术。

**注** 默认脚本支持大多数Linux分发版本，并在CentOS和Ubuntu上测试过。其他平台，比如OS X和FreeBSD，可能需要使用自定义`embeddedLaunchScript`。

**注** 当一个完全可执行jar运行时，它会将jar的目录作为工作目录。

