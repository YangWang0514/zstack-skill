# CLI 命令手册索引

> 本文件提供 CLI 命令手册的快速索引，帮助快速定位相关命令。

## 文档信息
- **文档名称**: PD2401 ZStack Cloud V5.4.0 CLI命令使用手册
- **产品版本**: ZStack Cloud 5.4.0
- **文档版本**: V5.4.0

## 主要章节

### 1. 引言
- 概述 ZStack Cloud CLI 工具的基本概念

### 2. 系统架构
- 2.1 ZStack Cloud 功能架构
- 2.2 ZStack Cloud 资源结构

### 3. 命令行工具
- 3.1 概览
- 3.2 用法（基本语法和参数）

### 4. 查询
- 4.1 概览
- 4.2 架构（Architecture）
- 4.3 示例

## 资源中心命令分类（第5章）

### 5.1 云资源池

#### 5.1.1 云主机 (VmInstance)
**创建类**
- `CreateVmInstance` - 创建云主机
- `CreateVmInstanceFromVolume` - 从云盘创建云主机
- `CreateVmInstanceFromVolumeSnapshot` - 从快照创建云主机
- `CreateVmInstanceFromVolumeSnapshotGroup` - 从快照组创建云主机
- `CreateVmInstanceFromOvf` - 从OVF模板导入云主机
- `CloneVmInstance` - 克隆云主机

**删除类**
- `DestroyVmInstance` - 删除云主机
- `RecoverVmInstance` - 恢复已删除云主机
- `ExpungeVmInstance` - 彻底删除云主机

**生命周期管理**
- `StartVmInstance` - 启动云主机
- `StopVmInstance` - 停止云主机
- `RebootVmInstance` - 重启云主机
- `PauseVmInstance` - 暂停云主机
- `ResumeVmInstance` - 恢复暂停的云主机
- `ReimageVmInstance` - 重置云主机

**查询类**
- `QueryVmInstance` - 查询云主机
- `GetVmCapabilities` - 获取云主机能力

**迁移类**
- `MigrateVm` - 热迁移云主机
- `GetVmMigrationCandidateHosts` - 获取可热迁移的物理主机列表
- `GetVmStartingCandidateClustersHosts` - 获取VM启动目的地列表

**网络与网卡管理**
- `GetVmAttachableL3Network` - 获取云主机可加载L3网络列表
- `AttachL3NetworkToVm` - 加载L3网络到云主机
- `DetachL3NetworkFromVm` - 从云主机卸载网络
- `CreateVmNic` - 创建云主机网卡
- `DeleteVmNic` - 删除云主机网卡
- `QueryVmNic` - 查询云主机网卡
- `AttachVmNicToVm` - 加载网卡到云主机
- `ChangeVmNicState` - 修改云主机网卡状态
- `ChangeVfNicHaState` - 修改云主机VF网卡高可用状态
- `ChangeVmNicNetwork` - 修改云主机网卡三层网络
- `GetCandidateL3NetworksForChangeVmNicNetwork` - 获取网卡可挂载的三层网络
- `SetNicQos` - 设置云主机网卡限速
- `GetNicQos` - 获取云主机网卡限速
- `DeleteNicQos` - 取消云主机网卡限速
- `GetVmNicAttachedNetworkService` - 获取网卡加载的网络服务名称

**存储管理**
- `GetVmAttachableDataVolume` - 获取云主机可加载云盘列表
- `GetCandidatePrimaryStoragesForCreatingVm` - 获取创建云主机时可选择的主存储

**ISO管理**
- `GetCandidateIsoForAttachingVm` - 获取云主机可加载ISO列表
- `GetCandidateVmForAttachingIso` - 获取ISO可加载云主机列表
- `AttachIsoToVmInstance` - 加载ISO到云主机
- `DetachIsoFromVmInstance` - 卸载云主机上的ISO

**配置管理**
- `SetVmSshKey` - 设置云主机SSH Key
- `GetVmSshKey` - 获取云主机SSH Key
- `DeleteVmSshKey` - 删除云主机SSH Key
- `ChangeVmPassword` - 变更云主机密码
- `SetVmConsolePassword` - 设置云主机控制台密码
- `GetVmConsolePassword` - 获取云主机控制台密码
- `DeleteVmConsolePassword` - 删除云主机控制台密码
- `GetVmConsoleAddress` - 获取云主机控制台地址和访问协议
- `SetVmHostname` - 设置云主机Hostname
- `GetVmHostname` - 获取云主机Hostname
- `DeleteVmHostname` - 删除云主机Hostname
- `GetVmBootOrder` - 获取云主机启动设备列表
- `SetVmBootOrder` - 指定云主机启动设备
- `SetVmStaticIp` - 指定云主机IP
- `DeleteVmStaticIp` - 删除云主机指定IP

**高级配置**
- `SetVmClockTrack` - 设置云主机时钟同步
- `SyncVmClock` - 立即同步云主机时钟
- `SetVmInstanceHaLevel` - 设置云主机高可用级别
- `GetVmInstanceHaLevel` - 获取云主机高可用级别
- `DeleteVmInstanceHaLevel` - 取消云主机高可用
- `GetVmQga` - 获取云主机Qga
- `UpdateVmInstance` - 更新云主机信息

**OVF/OVA管理**
- `ExportVmOvaPackage` - 导出云主机的OVA包
- `ParseOvf` - 解析OVF模板信息

**资源分组目录**
- `CreateDirectory` - 创建资源分组目录
- `DeleteDirectory` - 删除资源分组目录
- `AddResourcesToDirectory` - 添加资源至分组目录
- `MoveResourcesToDirectory` - 移动资源至分组目录
- `RemoveResourcesFromDirectory` - 从分组目录移除资源
- `UpdateDirectory` - 更新分组目录
- `QueryDirectory` - 查询分组目录

**目的地查询**
- `GetCandidateZonesClustersHostsForCreatingVm` - 获取目的地列表
- `GetInterdependentL3NetworksImages` - 获取镜像和L3依赖

#### 5.1.2 云盘 (Volume)
- `CreateDataVolume` - 创建数据云盘
- `QueryVolume` - 查询云盘
- `ResizeDataVolume` - 扩容数据云盘
- `ResizeRootVolume` - 扩容根云盘
- 更多云盘操作...

#### 5.1.3 镜像 (Image)
- 镜像查询、创建、删除等操作

#### 5.1.4 其他云资源池资源
- 备份、快照、密钥等资源管理

### 5.2 硬件资源
- 物理机管理
- 主存储管理
- 备份存储管理

### 5.3 网络资源
- L2网络管理
- L3网络管理
- VPC网络管理
- 弹性IP管理

### 5.4 网络服务
- 防火墙管理
- 负载均衡管理
- 端口转发管理
- VPN管理

### 5.5 资源编排
- 资源编排模板管理
- 资源编排栈管理

### 5.6 裸金属管理（Plus）
- 裸金属实例管理
- 裸金属镜像管理

### 5.7 弹性裸金属管理（Plus）
- 弹性裸金属相关操作

### 5.8 VMware管理
- VMware资源管理

## 使用建议

1. **精确匹配优先**: 搜索英文 API 名称（如 `CreateVmInstance`）比中文更准确
2. **按资源分类查找**: 根据操作的资源类型（云主机、云盘、网络等）定位相关章节
3. **查询参数详情**: 每个API都包含详细的参数说明和示例
