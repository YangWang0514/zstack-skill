---
name: zstack-skill
description: ZStack Cloud 运维助手。快速查询 ZStack CLI 命令、CTL 系统管理命令和 REST API 调用方法。提供准确的命令示例和参数说明。使用场景包括：云主机管理（创建/启动/停止/迁移）、云盘操作、网络配置、存储管理、系统运维（查看状态/启停服务/配置修改）、API开发（REST API/SDK调用）等。
---

# ZStack Cloud 运维助手 Skill

## 启动前更新检查

在处理用户问题前，优先尝试运行本 skill 内置的更新检查脚本：

```bash
python3 skills/zstack-skill/bin/zstack-skill-update-check
```

该检查最多每 24 小时访问一次 GitHub 上的 `VERSION` 文件。检查失败时静默跳过，继续正常回答用户的 ZStack 问题。

如果脚本提示有新版本，只提醒用户手动执行：

```text
/plugin update zstack-skill
/reload-plugins
```

不要静默更新插件，也不要声称当前会话会自动加载更新后的 skill。

这是一个专门用于 ZStack Cloud 云平台运维的技能，帮助用户快速查找和使用：

1. **CLI 命令** (`zstack-cli`) - 云资源的命令行管理
2. **CTL 命令** (`zstack-ctl`) - 系统管理和配置
3. **REST API** - 开发接口调用

## 用户问题分类

当用户提问时，首先识别问题类型：

| 类型 | 关键词示例 | 处理方式 | 索引文件 |
|------|-----------|---------|---------|
| CLI命令 | `zstack-cli`, 创建云主机, 查询云盘, 创建网络 | 查阅 CLI 命令手册 | `CLI_INDEX.md` |
| CTL命令 | `zstack-ctl`, 启动服务, 配置, 重启, 查看状态 | 查阅 CTL 命令手册 | `CTL_INDEX.md` |
| API调用 | API, SDK, 调用接口, 开发, HTTP | 查阅 API 手册 | `API_INDEX.md` |

## 文档索引

所有文档都位于 `references/` 目录下：

### CLI 命令手册
- **文档**: `PD2401_ZStack_Cloud_V5.4.0_CLI命令使用手册.md`
- **索引**: `PD2401_ZStack_Cloud_V5.4.0_CLI命令使用手册_INDEX.md`
- **版本**: V5.4.0

### CTL 命令手册
- **文档**: `PD2501_ZStack_Cloud_V5.5.0_CTL命令使用手册.md`
- **索引**: `PD2501_ZStack_Cloud_V5.5.0_CTL命令使用手册_INDEX.md`
- **版本**: V5.5.0

### API 开发手册
- **文档**: `PD3001_ZStack_Cloud_V5.4.0_api手册.md`
- **索引**: `PD3001_ZStack_Cloud_V5.4.0_api手册_INDEX.md`
- **版本**: V5.4.0

## 工作流程

### 第一步：读取索引文件

当用户询问时，首先读取对应的索引文件以快速定位内容：

```bash
# CLI 命令相关
Read references/PD2401_ZStack_Cloud_V5.4.0_CLI命令使用手册_INDEX.md

# CTL 命令相关
Read references/PD2501_ZStack_Cloud_V5.5.0_CTL命令使用手册_INDEX.md

# API 开发相关
Read references/PD3001_ZStack_Cloud_V5.4.0_api手册_INDEX.md
```

### 第二步：在文档中搜索

使用 Grep 工具在完整文档中搜索具体内容：

```bash
# 搜索 CLI 命令详情
Grep "CreateVmInstance" references/PD2401_ZStack_Cloud_V5.4.0_CLI命令使用手册.md

# 搜索 CTL 命令详情
Grep "zstack-ctl status" references/PD2501_ZStack_Cloud_V5.5.0_CTL命令使用手册.md

# 搜索 API 接口详情
Grep "CreateVmInstance" references/PD3001_ZStack_Cloud_V5.4.0_api手册.md
```

### 第三步：提供完整答案

结合索引和搜索结果，提供：
1. 命令/接口的完整语法
2. 参数说明
3. 使用示例
4. 注意事项

## 常用命令快速参考

### CLI 命令 - 云主机 (VM)

| 操作 | API 名称 | 说明 |
|------|---------|------|
| 创建 | `CreateVmInstance` | 创建新云主机 |
| 查询 | `QueryVmInstance` | 查询云主机信息 |
| 启动 | `StartVmInstance` | 启动已停止的云主机 |
| 停止 | `StopVmInstance` | 停止运行中的云主机 |
| 重启 | `RebootVmInstance` | 重启云主机 |
| 删除 | `DestroyVmInstance` | 删除云主机（可恢复） |
| 迁移 | `MigrateVm` | 热迁移云主机 |

### CLI 命令 - 云盘 (Volume)

| 操作 | API 名称 | 说明 |
|------|---------|------|
| 创建 | `CreateDataVolume` | 创建数据云盘 |
| 查询 | `QueryVolume` | 查询云盘信息 |
| 扩容 | `ResizeDataVolume` / `ResizeRootVolume` | 扩展云盘容量 |
| 挂载 | `AttachDataVolumeToVm` | 挂载到云主机 |
| 卸载 | `DetachDataVolumeFromVm` | 从云主机卸载 |

### CTL 命令 - 系统管理

| 操作 | 命令 | 说明 |
|------|------|------|
| 查看状态 | `zstack-ctl status` | 查看系统状态 |
| 启动服务 | `zstack-ctl start` | 启动管理节点和UI |
| 停止服务 | `zstack-ctl stop` | 停止服务 |
| 查看配置 | `zstack-ctl show_configuration` | 显示配置信息 |
| 修改配置 | `zstack-ctl configure` | 交互式配置 |
| 查看日志 | `zstack-ctl taillog` | 实时查看日志 |

## 响应策略

1. **优先使用索引文件**: 索引文件提供了分类清晰的命令列表，快速定位相关内容
2. **关键词精确匹配**: 搜索英文 API 名称（如 `CreateVmInstance`）比中文更准确
3. **提供完整示例**: 包含命令语法、参数说明、使用示例
4. **版本注意**: CLI和API基于 V5.4.0，CTL基于 V5.5.0，注意版本兼容性
5. **多命令组合**: 复杂操作可能需要多个命令组合完成

## API 调用格式

### CLI 方式
```bash
# 基本格式
zstack-cli <API名称> <参数>=<值>

# 示例：创建云主机
zstack-cli CreateVmInstance name=vm1 instanceOfferingUuid=xxx imageUuid=xxx
```

### REST API 方式
```bash
# 基本格式
curl -X POST http://<host>:<port>/v1/<api-name> \
  -H 'Content-Type: application/json' \
  -H 'Authorization: OAuth <token>' \
  -d '{"params": {...}}'
```

### SDK 方式
支持 Python/Java/Go 等多语言 SDK，详见 API 手册第3章。

## 搜索命令

当用户询问某个功能时：

```bash
# 在 CLI 手册中搜索关键词
Grep "关键词" references/PD2401_ZStack_Cloud_V5.4.0_CLI命令使用手册.md

# 在 CTL 手册中搜索
Grep "关键词" references/PD2501_ZStack_Cloud_V5.5.0_CTL命令使用手册.md

# 在 API 手册中搜索
Grep "API名称" references/PD3001_ZStack_Cloud_V5.4.0_api手册.md
```

## 注意事项

1. **文档文件较大**: 完整文档超过 5MB，优先使用索引文件定位
2. **参数详解**: 每个API的完整参数说明在原文档中
3. **版本兼容**: 注意不同模块的版本差异
4. **权限要求**: 某些操作需要特定权限
5. **更新机制**: 更新检查只提示用户手动更新，不静默执行插件更新；更新后需要 `/reload-plugins` 或重启 Claude Code 才能生效
