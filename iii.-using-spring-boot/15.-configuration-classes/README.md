# 15. 配置类

Spring Boot提倡基于Java的配置。尽管你可以使用XML源调用`SpringApplication.run()`，不过还是建议你使用`@Configuration`类作为主要配置源。通常定义了`main`方法的类也是使用`@Configuration`注解的一个很好的替补。

**注**：虽然网络上有很多使用XML配置的Spring示例，但你应该尽可能的使用基于Java的配置，搜索查看`enable*`注解就是一个好的开端。

