# 20.2 自动重启

如果应用使用`spring-boot-devtools`，则只要classpath下的文件有变动，它就会自动重启。这在使用IDE时非常有用，因为可以很快得到代码改变的反馈。默认情况下，classpath下任何指向文件夹的实体都会被监控，注意一些资源的修改比如静态assets，视图模板不需要重启应用。

**触发重启** 由于DevTools监控classpath下的资源，所以唯一触发重启的方式就是更新classpath。引起classpath更新的方式依赖于你使用的IDE，在Eclipse里，保存一个修改的文件将引起classpath更新，并触发重启。在IntelliJ IDEA中，构建工程（Build → Make Project）有同样效果。

**注** 你也可以通过支持的构建工具（比如，Maven和Gradle）启动应用，只要开启fork功能，因为DevTools需要一个隔离的应用类加载器执行正确的操作。Gradle默认支持该行为，按照以下配置可强制Maven插件fork进程：

```text
<build>
    <plugins>
        <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
            <configuration>
                <fork>true</fork>
            </configuration>
        </plugin>
    </plugins>
</build>
```

自动重启跟LiveReload可以一起很好的工作，具体参考[下面章节](http://docs.spring.io/spring-boot/docs/current-SNAPSHOT/reference/htmlsingle/#using-boot-devtools-livereload)。如果你使用JRebel，自动重启将禁用以支持动态类加载，其他devtools特性，比如LiveReload，属性覆盖仍旧可以使用。

DevTools依赖应用上下文的shutdown钩子来关闭处于重启过程的应用，如果禁用shutdown钩子（`SpringApplication.setRegisterShutdownHook(false)`），它将不能正常工作。

当判定classpath下实体的改变是否会触发重启时，DevTools自动忽略以下工程：`spring-boot`，`spring-boot-devtools`，`spring-boot-autoconfigure`，`spring-boot-actuator`和`spring-boot-starter`。

**Restart vs Reload** Spring Boot提供的重启技术是通过使用两个类加载器实现的。没有变化的类（比如那些第三方jars）会加载进一个基础（basic）classloader，正在开发的类会加载进一个重启（restart）classloader。当应用重启时，restart类加载器会被丢弃，并创建一个新的。这种方式意味着应用重启通常比冷启动（cold starts）快很多，因为基础类加载器已经可用，并且populated（意思是基础类加载器加载的类比较多？）。

如果发现重启对于你的应用来说不够快，或遇到类加载的问题，那你可以考虑reload技术，比如[JRebel](http://zeroturnaround.com/software/jrebel/)，这些技术是通过重写它们加载过的类实现的。[Spring Loaded](https://github.com/spring-projects/spring-loaded)提供了另一种选择，然而很多框架不支持它，也得不到商业支持。

