# 46. 端点

执行器端点（endpoints）可用于监控应用及与应用进行交互，Spring Boot包含很多内置的端点，你也可以添加自己的。例如，`health`端点提供了应用的基本健康信息。 端点暴露的方式取决于你采用的技术类型，大部分应用选择HTTP监控，端点的ID映射到一个URL。例如，`health`端点默认映射到`/health`。

下面的端点都是可用的：

| ID | 描述 | 是否敏感 |
| :--- | :--- | :--- |
| `actuator` | 为其他端点提供基于超文本的导航页面，需要添加Spring HATEOAS依赖 | true |
| `autoconfig` | 显示一个自动配置类的报告，该报告展示所有自动配置候选者及它们被应用或未被应用的原因 | true |
| `beans` | 显示一个应用中所有Spring Beans的完整列表 | true |
| `configprops` | 显示一个所有`@ConfigurationProperties`的集合列表 | true |
| `dump` | 执行一个线程转储 | true |
| `env` | 暴露来自Spring `ConfigurableEnvironment`的属性 | true |
| `flyway` | 显示数据库迁移路径，如果有的话 | true |
| `health` | 展示应用的健康信息（当使用一个未认证连接访问时显示一个简单的'status'，使用认证连接访问则显示全部信息详情） | false |
| `info` | 显示任意的应用信息 | false |
| `liquibase` | 展示任何Liquibase数据库迁移路径，如果有的话 | true |
| `metrics` | 展示当前应用的'metrics'信息 | true |
| `mappings` | 显示一个所有`@RequestMapping`路径的集合列表 | true |
| `shutdown` | 允许应用以优雅的方式关闭（默认情况下不启用） | true |
| `trace` | 显示trace信息（默认为最新的100条HTTP请求） | true |

如果使用Spring MVC，你还可以使用以下端点：

| ID | 描述 | 是否敏感 |
| :--- | :--- | :--- |
| `docs` | 展示Actuator的文档，包括示例请求和响应，需添加`spring-boot-actuator-docs`依赖 | false |
| `heapdump` | 返回一个GZip压缩的`hprof`堆转储文件 | true |
| `jolokia` | 通过HTTP暴露JMX beans（依赖Jolokia） | true |
| `logfile` | 返回日志文件内容（如果设置`logging.file`或`logging.path`属性），支持使用HTTP `Range`头接收日志文件内容的部分信息 |  |

**注**：根据端点暴露的方式，`sensitive`属性可用做安全提示，例如，在使用HTTP访问敏感（sensitive）端点时需要提供用户名/密码（如果没有启用web安全，可能会简化为禁止访问该端点）。

