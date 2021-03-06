# 70.7 在前端代理服务器后使用

你的应用可能需要发送`302`跳转或使用指向自己的绝对路径渲染内容。当在代理服务器后面运行时，调用者需要的是代理服务器链接而不是部署应用的实际物理机器地址，通常的解决方式是代理服务器将前端地址放到headers并告诉后端服务器如何拼装链接。

如果代理添加约定的`X-Forwarded-For`和`X-Forwarded-Proto` headers（大多数都是开箱即用的），只要将`application.properties`中的`server.use-forward-headers`设置为`true`，绝对链接就能正确的渲染。

**注** 如果应用运行在Cloud Foundry或Heroku，`server.use-forward-headers`属性没指定的话默认为`true`，其他实例默认为`false`。

