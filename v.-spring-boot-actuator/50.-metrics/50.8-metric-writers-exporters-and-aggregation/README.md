# 50.8 指标写入,导出和聚合

Spring Boot提供几个标记接口`Exporter`的实现，可用于将从内存buffers读取的指标复制到一个分析和展示它们的地方。实际上，如果提供一个实现`MetricWriter`接口（或`GaugeWriter`用于简单场景）且注解`@ExportMetricWriter`的`@Bean`，它将自动挂钩一个`Exporter`并每5秒反馈下指标更新（通过`spring.metrics.export.delay-millis`配置）。此外，你定义的所有注解`@ExportMetricReader`的`MetricReader`，它们的值将被默认exporter导出。

默认exporter是一个`MetricCopyExporter`，它会优化自己不去复制那些从上次调用以来没有变化的值（设置`spring.metrics.export.send-latest`标识可以关闭该优化）。注意Dropwizard `MetricRegistry`不支持时间戳，所以如果你使用Dropwizard指标服务，该优化是不起作用的（每次都会复制全部指标）。

通过`spring.metrics.export.*`属性可以设置导出的触发器（`delay-millis`，`includes`，`excludes`和`send-latest`），特殊`MetricWriters`的值可以通过`spring.metrics.export.triggers.<name>.*`设置，此处`<name>`是bean的名称（或匹配bean名称的表达式）。

**注** 如果关闭默认的`MetricRepository`（比如使用Dropwizard指标服务），指标的自动导出将禁用。你可以通过声明自定义类型的`MetricReader`并注解`@ExportMetricReader`来获取相同功能。

