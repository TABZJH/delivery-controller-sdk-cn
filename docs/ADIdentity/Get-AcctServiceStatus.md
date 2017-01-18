# Get-AcctServiceStatus

获取控制器上 ADIdentity Service 的当前状态。

## 语法

    Get-AcctServiceStatus [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

用于确定控制器上 ADIdentity Service 的状态。不需要在使用此命令之前配置服务的数据库连接。

## 相关命令

- [Set-AcctDBConnection](Set-AcctDBConnection.html)
- [Test-AcctDBConnection](Test-AcctDBConnection.html)
- [Get-AcctDBConnection](Get-AcctDBConnection.html)
- [Get-AcctDBSchema](Get-AcctDBSchema.html)

## 参数

| 名称           | 说明                                                         | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Fma.Sdk.Utilities.Service.ServiceStatusInfo

Get-AcctServiceStatus 命令返回包含 ADIdentity Service 状态的对象以及额外的诊断信息。  
OK  
ADIdentity Service 正在运行，并连接到一个包含有效架构的数据库。  
DBUnconfigured  
ADIdentity Service 没有配置数据库连接。  
DBRejectedConnection  
数据库已拒绝来自 ADIdentity Service 的登录尝试。 这可能是因为服务曾尝试使用无效凭据登录，或者因为尚未在指定位置安装数据库。  
InvalidDBConfigured  
数据库中缺少预期存储过程。 这可能是因为 ADIdentity Service 架构未添加到数据库。  
DBNotFound  
使用配置的连接字符串找不到指定的数据库。  
DBMissingOptionalFeature  
ADIdentity 已连接到有效的数据库，但不具备实现最佳性能所需的完整功能。 建议升级数据库。  
DBMissingMandatoryFeature  
ADIdentity 已连接到有效的数据库，但不具备所需的完整功能，因此，ADIdentity 无法运行。 需要升级数据库。  
DBNewerVersionThanService  
当前正在使用的 ADIdentity Service 版本与数据库中的 ADIdentity Service 架构版本不兼容。 请将 ADIdentity Service 升级到较新版本。  
DBOlderVersionThanService  
数据库中的 ADIdentity Service 架构版本与当前正在使用的 ADIdentity Service 版本不兼容。 请将数据库架构升级到较新版本。  
DBVersionChangeInProgress  
当前正在升级数据库架构。  
PendingFailure  
ADIdentity Service 与数据库之间的连接已断开。 这可能是暂时性的网络错误，但可能指示出现需要管理员干预的连接断开情况。  
Failed  
ADIdentity 与数据库之间的连接已断开很长一段时间，或者由于配置问题失败。 与数据库的连接不可用时，ADIdentity Service 无法运行。  
Unknown  
(0) 无法确定服务状态。## 注意 如果命令失败，会返回以下错误。  
错误代码  
\---\---\-----  
DatabaseError  
尝试执行数据库操作时，服务发生错误。  
DatabaseNotConfigured  
由于未配置用于服务的数据库，无法完成操作。  
DataStoreException  
尝试执行数据库操作时，服务发生错误 - 由于各种原因，无法与数据库通信。  
PermissionDenied  
您没有执行此命令的权限。  
AuthorizationError  
与 Citrix Delegated Administration Service 通信时出现问题。  
CommunicationError  
与远程服务通信时出现问题。  
ExceptionThrown  
发生意外错误。 有关更多详细信息，请参阅控制器上的 Windows 事件日志或 XenDesktop 日志。

## 示例

### 示例 1

    C:\PS>Get-AcctServiceStatus
    
    DBUnconfigured
    

说明  
\---\---\-----  
获取 ADIdentity Service 的当前状态。