# 客户端

Unity + C# 桌面训练客户端，目标平台为 Windows 和 Linux。

**Unity 版本：** `2022.3.62f3`

Unity 工程已在该版本中初始化。`ProjectSettings/ProjectVersion.txt` 是版本记录的权威来源；提交 Unity 项目文件时保留该文件、`Packages/manifest.json`、`Packages/packages-lock.json`、`ProjectSettings/` 和 `Assets/` 中的资源及 `.meta` 文件。

## 规划结构

```text
Assets/
  Scenes/
  Scripts/
    Core/
    Training/FixedTarget/
    Training/MovingTarget/
    Training/ReactionTarget/
    Session/
    Input/
    UI/
    Networking/
    Persistence/
    EyeCare/
  Prefabs/
  Materials/
  Tests/
Packages/
ProjectSettings/
```

当前尚未创建训练场景。训练规则和指标计算应保持可独立测试，避免与特定场景或 UI 紧密耦合。
