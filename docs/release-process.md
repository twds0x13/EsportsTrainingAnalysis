# 分支、检查与发布

## 分支职责

- `dev` 是日常集成分支，容纳小规模、可独立审查的功能性更新。
- `main` 是正式发布分支，只通过 Pull Request 接收 `dev` 的变更。
- 每个功能更新保持范围清晰，包含对应验证；跨多个目标的改动拆分为多个小批次。
- PR 合并前应解决冲突，并确保检查通过。GitHub 仓库启用分支保护后，将 Actions 检查设为合并必需条件。

## 提交约定

提交信息采用 Conventional Commits 格式：

```text
<type>(optional scope): <description>
```

- `feat:` 表示面向用户的新功能，触发次版本发布。
- `fix:` 表示缺陷修复，触发修订版本发布。
- `BREAKING CHANGE:` 表示不兼容变更，触发主版本发布。
- `docs:`、`test:`、`refactor:`、`chore:` 等默认不单独触发版本发布。

建议每个小规模功能批次至少有一条准确表达变更类型的 Conventional Commit。将 `dev` 合并到 `main` 时保留这些提交；如使用 Squash Merge，PR 标题应采用 Conventional Commit 格式，以便 semantic-release 分析最终进入 `main` 的提交。

## GitHub Actions

工作流位于 `.github/workflows/`：

- PR 指向 `dev` 或 `main` 时，以及向这两个分支 push 时，运行发布配置语法检查。
- 只有 push 到 `main` 且检查成功后，才运行 semantic-release。
- semantic-release 仅监视 `main`，使用 `v<版本号>` 标签格式，根据提交信息生成版本并创建 GitHub Release。
- 发布任务使用仓库内锁定的 Node.js 依赖和 GitHub Actions 内置 `GITHUB_TOKEN`，不发布 npm 包。

当前项目尚未创建 Unity 或 .NET 测试工程，因此工作流现阶段只验证发布配置。创建客户端、服务端和集成测试后，应将相应构建与测试加入验证 job，并保持发布 job 依赖全部必需检查。

## 启用条件

仓库发布到 GitHub 后，确认默认分支为 `main`，并为 `main` 配置 Pull Request 与必需状态检查保护。确保 `dev` 分支存在，再通过 PR 合并第一批 Conventional Commits。在仓库 Actions 设置中允许工作流使用写权限；工作流通过最小化的 `GITHUB_TOKEN` 权限创建版本标签和 Release，无需个人访问令牌。

## 官方参考

- [GitHub Actions 工作流触发事件](https://docs.github.com/actions/using-workflows/events-that-trigger-workflows)
- [GitHub Actions 的 `GITHUB_TOKEN` 权限](https://docs.github.com/actions/security-guides/automatic-token-authentication)
- [semantic-release 配置](https://semantic-release.gitbook.io/semantic-release/usage/configuration)
- [semantic-release CI 配置](https://semantic-release.gitbook.io/semantic-release/usage/ci-configuration)
