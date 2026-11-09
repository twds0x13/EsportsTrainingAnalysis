# 服务端

采用 ASP.NET Core 与 PostgreSQL 的模块化单体方案。目标框架版本待服务端工程初始化前确定。

```text
Api/             HTTP 接口与中间件
Application/     用户、session、成绩、排行榜和标准配置用例
Domain/          核心领域模型与规则
Infrastructure/  持久化、认证、网络和配置适配
```

正式项目文件和解决方案将在确定目标框架及依赖版本后生成。
