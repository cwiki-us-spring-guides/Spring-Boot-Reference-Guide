# 16. 自动配置

Spring Boot自动配置（auto-configuration）尝试根据添加的jar依赖自动配置你的Spring应用。例如，如果classpath下存在`HSQLDB`，并且你没有手动配置任何数据库连接的beans，那么Spring Boot将自动配置一个内存型（in-memory）数据库。

实现自动配置有两种可选方式，分别是将`@EnableAutoConfiguration`或`@SpringBootApplication`注解到`@Configuration`类上。

**注**：你应该只添加一个`@EnableAutoConfiguration`注解，通常建议将它添加到主配置类（primary `@Configuration`）上。

