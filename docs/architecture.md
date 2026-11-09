# 项目架构

## 技术选型

| 区域 | 技术 | 版本 |
|---|---|---|
| 客户端 | Unity + C# | 2022.3.62f3 |
| 服务端 | [ASP.NET Core](https://learn.microsoft.com/aspnet/core/) | 待确定 |
| 数据库 | [PostgreSQL](https://www.postgresql.org/docs/) | 待确定 |

## 目录职责

- `src/client/`：训练场景、鼠标输入、训练状态、指标采集、界面、网络通信和本地持久化。目录按 Unity 工程约定组织。
- `src/server/Api/`：HTTP 接口、控制器和中间件。
- `src/server/Application/`：用户、训练 session、成绩、排行榜和标准配置用例。
- `src/server/Domain/`：核心领域实体、规则和值对象。
- `src/server/Infrastructure/`：数据库、认证、网络及配置适配。
- `src/shared/Contracts/`：客户端与服务端通信所需的稳定契约，不放置任一端的业务实现。
- `tests/`：客户端、服务端单元测试和集成测试。
- `deploy/`：本地开发与部署配置。
- `tools/`：项目开发辅助工具。

## 依赖边界

- 客户端通过服务端 API 访问云端数据，不直接连接 PostgreSQL。
- 服务端不依赖 Unity 类型、场景对象或客户端程序集。
- `shared/` 只承载跨端协议契约；训练和服务端业务规则分别归属各自模块。
- 服务端初期按模块化单体组织。新增服务或基础设施以明确需求和可验证收益为依据。

## 初始化与版本约束

- Unity 工程已使用 `2022.3.62f3` 初始化。后续打开和修改客户端时使用该版本；升级版本应同步更新 `ProjectSettings/ProjectVersion.txt` 并验证项目。
- ASP.NET Core 目标框架和 PostgreSQL 版本在服务端工程初始化前确定，并记录于本文件。
- 数据库迁移、容器编排和 CI 配置在相应实现与运行方式确定后加入。

## 技术参考

- Microsoft Learn：[ASP.NET Core 文档](https://learn.microsoft.com/aspnet/core/)，用于服务端 Web API 与应用开发参考。
- PostgreSQL：[官方文档](https://www.postgresql.org/docs/)与[项目介绍](https://www.postgresql.org/about/)，用于数据库能力、配置和版本资料参考。
