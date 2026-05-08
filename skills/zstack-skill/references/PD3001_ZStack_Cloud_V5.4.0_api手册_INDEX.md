# API 手册索引

> 本文件提供 ZStack Cloud API 开发手册的快速索引，帮助开发者快速定位 REST API 接口。

## 文档信息
- **文档名称**: PD3001 ZStack Cloud V5.4.0 API手册
- **产品版本**: ZStack Cloud 5.4.0
- **文档版本**: V5.4.0

## 主要章节

### 1. 引言
API 开发概述

### 2. API 使用规范
- 2.1 HTTP方法 (HTTP Verbs) - GET, POST, PUT, DELETE
- 2.2 传参方式 - URL参数、请求体
- 2.3 HTTP Headers - 认证、内容类型
- 2.4 HTTP返回码 (HTTP Status Code) - 200, 400, 500等
- 2.5 API种类 - 同步API、异步API
- 2.6 API操作 - CRUD操作
- 2.7 基本流程示例 - 完整调用示例
- 2.8 Webhook - 事件通知机制
- 2.9 查询API - QueryXXX系列
- 2.10 ZQL语法 - ZStack查询语言
- 2.11 修改API服务端口 - 自定义端口配置
- 2.12 批量API返回 - 批量操作处理

### 3. SDK使用规范
- 3.1 环境准备 - Python/Java/Go SDK安装
- 3.2 SDK使用 - 基本用法
- 3.3 SDK使用示例 - 多语言示例代码

### 4. 使用AK调用API
AccessKey认证方式

### 5. 资源中心 API 接口

## 5.1 云资源池

### 5.1.1 云主机相关接口 (VmInstance)

#### 创建类
- `CreateVmInstance` - 创建云主机
- `CreateVmInstanceFromVolume` - 从云盘创建云主机
- `CreateVmInstanceFromVolumeSnapshot` - 从快照创建云主机
- `CreateVmInstanceFromVolumeSnapshotGroup` - 从快照组创建云主机
- `CreateVmInstanceFromOvf` - 从OVF模板导入云主机
- `CloneVmInstance` - 克隆云主机

#### 删除类
- `DestroyVmInstance` - 删除云主机
- `RecoverVmInstance` - 恢复已删除云主机
- `ExpungeVmInstance` - 彻底删除云主机

#### 生命周期管理
- `StartVmInstance` - 启动云主机
- `StopVmInstance` - 停止云主机
- `RebootVmInstance` - 重启云主机
- `PauseVmInstance` - 暂停云主机
- `ResumeVmInstance` - 恢复暂停的云主机
- `ReimageVmInstance` - 重置云主机

#### 定时任务
- `CreateStartVmInstanceScheduler` - 创建启动云主机的定时任务
- `CreateStopVmInstanceScheduler` - 创建停止云主机的定时任务
- `CreateRebootVmInstanceScheduler` - 创建重启云主机的定时任务

#### 查询与信息获取
- `QueryVmInstance` - 查询云主机
- `GetVmCapabilities` - 获取云主机能力
- `GetVmsCapabilities` - 批量获取云主机能力
- `GetVirtualizerInfo` - 获取资源虚拟化软件信息
- `GetVmQga` - 获取云主机Qga
- `SetVmQga` - 设置云主机Qga
- `QueryGuestToolsState` - 获取云主机GuestTools状态
- `UpdateGuestToolsState` - 更新云主机GuestTools状态

#### 迁移
- `MigrateVm` - 热迁移云主机
- `GetVmMigrationCandidateHosts` - 获取可热迁移的物理机列表
- `GetVmStartingCandidateClustersHosts` - 获取云主机可启动目的地列表
- `GetCandidateZonesClustersHostsForCreatingVm` - 获取目的地列表

#### 网络与网卡管理
- `GetVmAttachableL3Network` - 获取云主机可加载L3网络列表
- `AttachL3NetworkToVm` - 加载L3网络到云主机
- `DetachL3NetworkFromVm` - 从云主机卸载网络
- `CreateVmNic` - 创建云主机网卡
- `DeleteVmNic` - 删除云主机网卡
- `QueryVmNic` - 查询云主机网卡
- `AttachVmNicToVm` - 加载网卡到云主机
- `ChangeVmNicState` - 修改云主机网卡状态
- `ChangeVmNicNetwork` - 修改云主机网卡三层网络
- `GetCandidateL3NetworksForChangeVmNicNetwork` - 获取网卡可挂载的三层网络
- `GetVmNicAttachedNetworkService` - 获取网卡加载的网络服务名称
- `ChangeVmNicSecurityPolicy` - 更改网卡的默认流量策略
- `UpdateVmNicMac` - 更新云主机mac地址
- `UpdateVmNicDriver` - 设置网卡型号
- `GetVmDeviceAddress` - 获取云主机设备地址

#### QoS管理
- `SetNicQos` - 设置云主机网卡限速
- `GetNicQos` - 获取云主机网卡限速
- `DeleteNicQos` - 取消云主机网卡限速

#### 存储管理
- `GetVmAttachableDataVolume` - 获取云主机可加载云盘列表
- `GetCandidatePrimaryStoragesForCreatingVm` - 获取创建云主机时可选择的主存储

#### ISO管理
- `GetCandidateIsoForAttachingVm` - 获取云主机可加载ISO列表
- `GetCandidateVmForAttachingIso` - 获取ISO可加载云主机列表
- `AttachIsoToVmInstance` - 加载ISO到云主机
- `DetachIsoFromVmInstance` - 卸载云主机上的ISO

#### CDROM管理
- `CreateVmCdRom` - 为云主机创建CDROM
- `DeleteVmCdRom` - 删除CDROM
- `UpdateVmCdRom` - 修改CDROM
- `SetVmInstanceDefaultCdRom` - 设置云主机默认CDROM
- `QueryVmCdRom` - 查询CDROM清单

#### 访问与认证
- `SetVmSshKey` - 设置云主机SSH Key
- `GetVmSshKey` - 获取云主机SSH Key
- `DeleteVmSshKey` - 删除云主机SSH Key
- `ChangeVmPassword` - 变更云主机密码
- `SetVmConsolePassword` - 设置云主机控制台密码
- `GetVmConsolePassword` - 获取云主机控制台密码
- `DeleteVmConsolePassword` - 删除云主机控制台密码
- `GetVmConsoleAddress` - 获取云主机控制台地址和访问协议
- `GetVmRDP` - 获取云主机RDP开关状态
- `SetVmRDP` - 设置云主机RDP开关状态

#### 高级配置
- `SetVmHostname` - 设置云主机Hostname
- `GetVmHostname` - 获取云主机Hostname
- `DeleteVmHostname` - 删除云主机Hostname
- `GetVmBootOrder` - 获取云主机启动设备列表
- `SetVmBootOrder` - 指定云主机启动设备
- `SetVmStaticIp` - 指定云主机IP
- `DeleteVmStaticIp` - 删除云主机指定IP
- `UpdateVmInstance` - 更新云主机信息
- `SetVmClockTrack` - 设置云主机时钟同步
- `SyncVmClock` - 立即同步云主机时钟
- `SetVmInstanceHaLevel` - 设置云主机高可用级别
- `GetVmInstanceHaLevel` - 获取云主机高可用级别
- `DeleteVmInstanceHaLevel` - 取消云主机高可用
- `GetVmMonitorNumber` - 获取云主机支持的屏幕数
- `SetVmMonitorNumber` - 设置云主机支持的屏幕数
- `ChangeVmImage` - 修改云主机根云盘
- `GetImageCandidatesForVmToChange` - 获取候选镜像列表
- `SetVmCleanTraffic` - 设置云主机防IP欺骗启用状态
- `UpdateVmPriority` - 更改云主机优先级级别
- `SetVmQxlMemory` - 设置云主机显存
- `SetVmSoundType` - 设置云主机虚拟声卡类型
- `GetSpiceCertificates` - 获取spice的CA证书
- `AttachGuestToolsIsoToVm` - 为云主机加载增强工具镜像
- `GetLatestGuestToolsForVm` - 获取云主机可用的最新增强工具
- `GetVmGuestToolsInfo` - 获取云主机内部增强工具的信息
- `GetVmInstanceFirstBootDevice` - 获取云主机第一启动项
- `UpdateVmNetworkConfig` - 同步云主机网络配置

#### NUMA与性能
- `SetVmNuma` - 设置云主机vNUMA
- `GetVmNuma` - 获取VM Numa开关状态
- `GetVmvNUMATopology` - 查询云主机的vNUMA拓扑信息
- `SetVmEmulatorPinning` - 设置云主机Emulator Pinning功能
- `GetVmEmulatorPinning` - 获取VM Emulator Pin在物理机的cpu上
- `QueryVmSchedHistory` - 查询虚拟机调度历史

#### 扁平化与执行
- `FlattenVmInstance` - 扁平合并云主机
- `ExecuteGuestVmCommand` - 云主机执行命令
- `UploadFileToVm` - 发送文件到云主机

#### OVF/OVA管理
- `ExportVmOvaPackage` - 导出云主机的OVA包
- `ParseOvf` - 解析OVF模板信息

#### 资源分组目录
- `CreateDirectory` - 创建资源分组目录
- `DeleteDirectory` - 删除资源分组目录
- `AddResourcesToDirectory` - 添加资源至分组目录
- `MoveResourcesToDirectory` - 移动资源至分组目录
- `RemoveResourcesFromDirectory` - 从分组目录移除资源
- `UpdateDirectory` - 更新分组目录
- `QueryDirectory` - 查询分组目录

#### 共享磁盘
- `QueryShareableVolumeVmInstanceRef` - 查询共享磁盘所挂载的云主机
- `GetInterdependentL3NetworksImages` - 获取相互依赖的镜像和L3网络

### 5.1.2 云盘相关接口 (Volume)

#### 基本操作
- `CreateDataVolume` - 创建云盘
- `CreateDataVolumeFromVolumeTemplate` - 从镜像创建云盘
- `CreateDataVolumeFromVolumeSnapshot` - 从快照创建云盘
- `DeleteDataVolume` - 删除云盘
- `ExpungeDataVolume` - 彻底删除云盘
- `RecoverDataVolume` - 恢复云盘
- `QueryVolume` - 查询云盘
- `ChangeVolumeState` - 开启或关闭云盘
- `UpdateVolume` - 修改云盘属性

#### 容量管理
- `ResizeRootVolume` - 扩展根云盘
- `ResizeDataVolume` - 扩展数据云盘
- `SyncVolumeSize` - 同步云盘大小
- `BatchSyncVolumeSize` - 批量刷新云盘容量
- `GetVolumeFormat` - 获取云盘格式
- `GetVolumeCapabilities` - 获取云盘支持的类型的能力

#### QoS管理
- `SetVolumeQoS` - 设置云盘限速
- `GetVolumeQoS` - 获取云盘限速
- `DeleteVolumeQos` - 取消云盘限速

#### IO线程
- `GetVolumeIoThreadPin` - 获取云盘IO线程绑定信息
- `SetVolumeIoThreadPin` - 设置云盘IO线程绑定

#### 挂载管理
- `GetDataVolumeAttachableVm` - 获取云盘可被加载的云主机列表
- `AttachDataVolumeToVm` - 挂载云盘到云主机上
- `DetachDataVolumeFromVm` - 从云主机上卸载云盘
- `AttachDataVolumeToHost` - 加载数据云盘到物理机
- `DetachDataVolumeFromHost` - 从物理机卸载数据云盘

#### 快照管理
- `CreateVolumeSnapshot` - 从云盘创建快照
- `QueryVolumeSnapshot` - 查询云盘快照
- `QueryVolumeSnapshotTree` - 查询快照树
- `UpdateVolumeSnapshot` - 更新云盘快照信息
- `DeleteVolumeSnapshot` - 删除云盘快照
- `RevertVolumeFromSnapshot` - 将云盘回滚至指定快照
- `GetVolumeSnapshotSize` - 获取快照容量

### 5.1.3 镜像相关接口 (Image)
- 镜像查询、创建、删除、更新等操作

### 5.1.4 其他资源接口
- 备份、快照、密钥、亲和性等资源管理

## 使用建议

### API调用方式
1. **REST API**: 通过 HTTP/HTTPS 调用
2. **SDK调用**: 支持 Python/Java/Go 等多语言SDK
3. **CLI调用**: 通过 zstack-cli 命令行工具

### 开发流程
1. 阅读 API 使用规范（第2章）
2. 选择调用方式（REST API / SDK / CLI）
3. 根据资源类型查找对应接口
4. 参考基本流程示例进行开发

### 搜索技巧
1. **英文API名优先**: 如 `CreateVmInstance` 比中文更准确
2. **按资源分类**: 云主机、云盘、网络等
3. **查看参数详情**: 每个API包含完整的请求/响应示例
