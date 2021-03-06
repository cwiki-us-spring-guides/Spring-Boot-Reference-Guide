# 29.3. JPA和Spring Data

Java持久化API是一个允许你将对象映射为关系数据库的标准技术，`spring-boot-starter-data-jpa` POM提供了一种快速上手的方式，它提供以下关键依赖：

* Hibernate - 一个非常流行的JPA实现。
* Spring Data JPA - 让实现基于JPA的repositories更容易。
* Spring ORMs - Spring框架支持的核心ORM。

**注** 我们不想在这涉及太多关于JPA或Spring Data的细节。你可以参考来自[spring.io](http://spring.io/)的指南[使用JPA获取数据](http://spring.io/guides/gs/accessing-data-jpa/)，并阅读[Spring Data JPA](http://projects.spring.io/spring-data-jpa/)和[Hibernate](http://hibernate.org/orm/documentation/)的参考文档。

**注** Spring Boot默认使用Hibernate 5.0.x，如果你希望的话也可以使用4.3.x或5.2.x，具体参考[Hibernate 4](https://github.com/spring-projects/spring-boot/tree/v1.4.1.RELEASE/spring-boot-samples/spring-boot-sample-hibernate4)和[Hibernate 5.2](https://github.com/spring-projects/spring-boot/tree/v1.4.1.RELEASE/spring-boot-samples/spring-boot-sample-hibernate52)示例。

