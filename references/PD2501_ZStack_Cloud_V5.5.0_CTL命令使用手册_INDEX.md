# CTL 命令手册索引

> 本文件提供 CTL 命令手册的快速索引，帮助快速定位系统管理命令。

## 文档信息
- **文档名称**: zstack-ctl 命令使用手册
- **产品版本**: ZStack Cloud 5.5.0
- **文档版本**: V5.5.0

## CTL 命令简介
CTL 是 ZStack Cloud 独有的系统命令，可以帮助用户完成多种系统设置。CTL 下有多条子命令，帮助用户简化安装操作和环境配置。

## 命令分类

## 2. CTL 基础命令

### 2.1 status
**描述**: 显示指定节点上 ZStack Cloud 状态和信息
```
zstack-ctl status
zstack-ctl status --host 192.168.0.10
```

### 2.2 start
**描述**: 启动 ZStack Cloud 相关服务，包括管理节点和 UI 服务
```
zstack-ctl start
zstack-ctl start --daemon
```

### 2.3 stop
**描述**: 停止 ZStack Cloud 相关服务
```
zstack-ctl stop
```

### 2.4 start_ui
**描述**: 启动 ZStack Cloud 的 UI 服务

### 2.5 stop_ui
**描述**: 停止 ZStack Cloud 的 UI 服务

### 2.6 start_node
**描述**: 启动管理节点

### 2.7 stop_node
**描述**: 停止管理节点

### 2.8 restart_node
**描述**: 重启管理节点

### 2.9 configured_collect_log
**描述**: 配置收集日志

### 2.10 dump_mysql
**描述**: 导出 MySQL 数据

### 2.11 change_ip
**描述**: 修改 IP 地址

### 2.12 show_configuration
**描述**: 显示配置信息
```
zstack-ctl show_configuration
```

### 2.13 configure
**描述**: 修改配置
```
zstack-ctl configure
```

### 2.14 show_ui_config
**描述**: 显示 UI 配置

### 2.15 config_ui
**描述**: 配置 UI

### 2.16 ui_status
**描述**: 查看 UI 状态

### 2.17 install_license
**描述**: 安装许可证

### 2.18 reset_password
**描述**: 重置密码

### 2.19 change_mysql_password
**描述**: 修改 MySQL 密码

## 3. CTL 高级命令

### 3.1 install_management_node
**描述**: 安装管理节点

### 3.2 upgrade_management_node
**描述**: 升级管理节点

### 3.3 rollback_management_node
**描述**: 回滚管理节点

### 3.4 taillog
**描述**: 查看日志
```
zstack-ctl taillog
```

### 3.5 install_ui
**描述**: 安装 UI

### 3.6 install_db
**描述**: 安装数据库

### 3.7 upgrade_db
**描述**: 升级数据库

### 3.8 deploydb
**描述**: 部署数据库

### 3.9 rollback_db
**描述**: 回滚数据库

### 3.10 clear_license
**描述**: 清除许可证

### 3.11 restore_config
**描述**: 恢复配置

### 3.12 save_config
**描述**: 保存配置

### 3.13 set_deployment
**描述**: 设置部署模式

### 3.14 start_vdi
**描述**: 启动 VDI 服务

### 3.15 stop_vdi
**描述**: 停止 VDI 服务

### 3.16 vdi_status
**描述**: 查看 VDI 状态

### 3.17 setenv
**描述**: 设置环境变量
```
zstack-ctl setenv <KEY>=<VALUE>
```

### 3.18 unsetenv
**描述**: 删除环境变量
```
zstack-ctl unsetenv <KEY>
```

### 3.19 mysql_restrict_connection
**描述**: 限制 MySQL 连接

### 3.20 getenv
**描述**: 获取环境变量
```
zstack-ctl getenv <KEY>
```

### 3.21 bootstrap
**描述**: 初始化系统

### 3.22 upgrade_ctl
**描述**: 升级 CTL 工具

## 使用场景指南

### 日常运维
- `zstack-ctl status` - 查看系统状态
- `zstack-ctl taillog` - 查看日志排查问题
- `zstack-ctl show_configuration` - 查看当前配置

### 服务管理
- `zstack-ctl start` / `zstack-ctl stop` - 启动/停止服务
- `zstack-ctl restart_node` - 重启管理节点

### 配置修改
- `zstack-ctl configure` - 修改系统配置
- `zstack-ctl config_ui` - 修改 UI 配置
- `zstack-ctl setenv` / `zstack-ctl unsetenv` - 管理环境变量

### 系统维护
- `zstack-ctl upgrade_management_node` - 升级管理节点
- `zstack-ctl dump_mysql` - 备份数据库
- `zstack-ctl restore_config` - 恢复配置

### 故障排查
- `zstack-ctl status --host <IP>` - 查看远程节点状态
- `zstack-ctl taillog` - 实时查看日志
- `zstack-ctl mysql_restrict_connection` - 限制数据库连接
