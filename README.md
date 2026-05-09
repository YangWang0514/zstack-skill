# zstack-skill

ZStack Cloud 运维助手，用于快速查询 ZStack CLI 命令、`zstack-ctl` 系统管理命令和 REST API 调用方法。

## 安装

先添加公开 marketplace：

```text
/plugin marketplace add https://github.com/YangWang0514/zstack-skill
```

再安装 skill：

```text
/plugin install zstack-skill
```

安装或更新后，请运行 `/reload-plugins` 或重启 Claude Code 后生效。

## 更新机制

`zstack-skill` 内置带缓存的版本检查脚本：`skills/zstack-skill/bin/zstack-skill-update-check`。

当 skill 被调用时，Claude 会先运行该脚本检查 GitHub 上的 `VERSION` 文件。检查最多每 24 小时执行一次；如果网络不可用或检查失败，会静默跳过，不影响 ZStack 文档查询。

发现新版本时，脚本只会提示用户手动更新，不会静默更新插件，也不会自动 reload 当前会话：

```text
/plugin update zstack-skill
/reload-plugins
```

如果当前 Claude Code 版本不支持 `/plugin update`，请先查看：

```text
/plugin help
```

然后按当前版本支持的插件管理方式重新安装或更新。

## 内容

- `skills/zstack-skill/SKILL.md`：Claude Code skill 定义
- `skills/zstack-skill/VERSION`：当前 skill 版本
- `skills/zstack-skill/bin/zstack-skill-update-check`：带缓存的更新检查脚本
- `skills/zstack-skill/references/`：ZStack Cloud CLI、CTL、API 参考文档

## 使用场景

- 查询 `zstack-cli` 云资源管理命令
- 查询 `zstack-ctl` 系统运维命令
- 查询 ZStack Cloud REST API 调用方法
