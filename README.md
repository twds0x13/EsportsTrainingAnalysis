# 电竞训练分析系统

面向电竞选手与爱好者的桌面训练软件，提供固定靶、移动靶和反应靶训练，并记录可查询的原始训练数据。项目需求见 [`memory/需求文档.md`](memory/需求文档.md)，质量审查规则见 [`memory/项目质量管控.md`](memory/项目质量管控.md)。

## 技术方案

- 客户端：Unity 2022.3.62f3 + C#。
- 服务端 API：ASP.NET Core，参阅 [Microsoft Learn 官方文档](https://learn.microsoft.com/aspnet/core/)。
- 关系型数据存储：PostgreSQL，参阅[官方文档](https://www.postgresql.org/docs/)与[项目介绍](https://www.postgresql.org/about/)。
- 共享目录：仅保存跨端通信契约。

## 目录

```text
src/
  client/       Unity 客户端工程
  server/       ASP.NET Core 服务端
  shared/       跨端契约
tests/          客户端、服务端与集成测试
docs/           架构、接口和开发文档
deploy/         本地开发与部署配置
tools/          开发辅助工具
.github/        GitHub Actions 工作流
memory/         需求与项目质量规范
```

Unity 客户端工程已初始化。ASP.NET Core 与 PostgreSQL 的目标版本及服务端项目文件将在服务端工程初始化前确定。

分支、检查与 semantic-release 流程见 [`docs/release-process.md`](docs/release-process.md)。

## 许可

本仓库采用 [MIT License](LICENSE)。第三方组件及依赖仍受各自许可证约束。
