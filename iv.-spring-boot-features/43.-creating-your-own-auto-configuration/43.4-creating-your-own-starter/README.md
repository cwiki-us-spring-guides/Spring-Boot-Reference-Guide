# 43.4 创建自己的starter

一个完整的Spring Boot starter可能包含以下组件：

* `autoconfigure`模块，包含自动配置类的代码。
* `starter`模块，提供自动配置模块及其他有用的依赖，简而言之，添加本starter就能开始使用该library。

**注** 如果不需要将它们分离开来，你可以将自动配置代码和依赖管理放到一个单一模块中。

