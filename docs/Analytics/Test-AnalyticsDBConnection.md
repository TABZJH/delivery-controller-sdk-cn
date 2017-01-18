# Test-AnalyticsDBConnection

测试数据库是否适合由 Citrix Analytics Service 使用。

## 语法

    Test-AnalyticsDBConnection [-DBConnection] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

测试给定连接字符串中指定的数据库是否适合由当前所选 Citrix Analytics Service 实例使用。

服务会尝试联系指定的数据库，并返回指示数据库是否可联系并可用的状态。 测试不影响当前以任何方式建立的服务实例到另一个数据库的任何连接。 测试的连接字符串不会记录。

仅支持在连接字符串中使用 Windows 身份验证；如果连接字符串包含 SQL 身份验证凭据，总是会因为无效而被拒绝。

当前服务实例在本地计算机上，或由最后一次使用的 -AdminAddress 参数显式指定给 Analytics SDK cmdlet。

## 相关命令

- [Get-AnalyticsServiceStatus](Get-AnalyticsServiceStatus.html)
- [Get-AnalyticsDBConnection](Get-AnalyticsDBConnection.html)
- [Set-AnalyticsDBConnection](Set-AnalyticsDBConnection.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| DBConnection | 指定由当前所选 Citrix Analytics Service 实例测试的数据库连接字符串。                                                                                                                        | true  | false |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.Fma.Sdk.Utilities.Service.ServiceStatusInfo

Test-AnalyticsDBConnection 返回类型为 ServiceStatusInfo 的对象，该对象描述由于在 Set-AnalyticsDBConnection cmdlet 中使用指定的连接字符串而导致系统发生的变化。 系统的实际状态不会变化。  
返回的 ServiceStatusInfo 对象有两个属性：ServiceStatus（提供由于采用连接字符串而产生的所选 Analytics Service 实例状态）和 ExtraInfo（提供连接字符串所标识的数据库的额外诊断信息的字典）。  
可能的 ServiceStatus 值包括：  
-- OK：  
如果使用提供的连接字符串执行 Set-AnalyticsDBConnection 命令，它会成功。  
-- DBUnconfigured：  
没有为服务实例设置数据库连接字符串。  
-- DBRejectedConnection：  
数据库拒绝了来自 Analytics Service 实例的登录尝试。 这可能是因为服务曾尝试使用无效凭据登录，或者因为尚未在指定位置安装数据库。  
-- InvalidDBConfigured：  
指定的数据库不存在、对 Analytics Service 实例不可见或数据库中的服务架构无效。  
-- DBNotFound：  
使用配置的连接字符串找不到指定的数据库。  
-- DBNewerVersionThanService：  
Analytics Service 实例早于数据库中的服务架构，并与其不兼容。 服务实例需要升级。  
-- DBOlderVersionThanService：  
Analytics Service 实例高于数据库中的服务架构，并与其不兼容。 数据库架构需要升级。  
-- DBVersionChangeInProgress：  
当前正在升级数据库架构。  
-- PendingFailure：  
Analytics Service 实例与数据库之间的连接已断开。 这可能是暂时性的网络错误，但可能指示出现需要管理员干预的连接断开情况。  
-- Failed：  
Analytics Service 实例与数据库之间的连接已断开很长一段时间，或者由于配置问题失败。 服务实例与数据库之间的连接不可用时，服务实例无法运行。  
-- Unknown：  
无法确定服务状态。  
ExtraInfo 字典至少包含以下键及其关联的字符串值：  
-- Server.Version：  
数据库服务器版本号。  
-- Server.IsClustered：  
如果数据库服务器已加入群集，则为“True”；否则为“False”。  
-- Database.Status：  
数据库的状态。 正常运行时，值为“Normal”。  
-- Database.RecoveryModel：  
数据库的恢复模式（例如“Simple”）。  
-- Database.LastBackupDate：  
此数据库上次备份日期。  
-- Database.IsReadCommittedSnapshotOn：  
如果启用了 READ_COMMITTED_SNAPSHOT 数据库选项，则为“True”；否则为“False”。  
-- Database.Collation：  
数据库的排序顺序（例如“Latin1_General_100_CI_AS_KS”）。  
-- Database.IsMirroringEnabled：  
如果数据库已镜像，则为“True”；否则为“False”。  
-- Database.AvailabilityGroupName：  
数据库所属可用组的名称。  
请注意，对应的值始终是字符串。 因此，要测试布尔值，必须使用类似如下的语句  
if ($info["Server.IsClustered"] == "True")  
而不只是  
if ($info["Server.IsClustered"]) ## 注意 如果命令失败，会返回以下错误。  
错误代码  
\---\---\-----  
InvalidDBConnectionString  
数据库连接字符串格式无效。  
PermissionDenied  
您没有执行此命令的权限。  
AuthorizationError  
与 Citrix Delegated Administration Service 通信时出现问题。  
ConfigurationLoggingError  
由于配置日志记录错误，无法执行操作。  
CommunicationError  
与远程服务通信时出现问题。  
ExceptionThrown  
发生意外错误。 有关更多详细信息，请参阅控制器上的 Windows 事件日志或 XenDesktop 日志。

## 示例

### 示例 1

    C:\PS>Test-AnalyticsDBConnection "Server=dbserver\SQLEXPRESS;Database=XDDB;Trusted_Connection=True"
    

说明  
\---\---\-----  
测试服务实例是否可以使用名为 XDDB 的数据库，该数据库在名为 dbserver 的计算机上运行的 SQL Server Express 数据库上。 需要集成 Windows 身份验证。

### 示例 2

    c:\PS>Test-AnalyticsDBConnection -DBConnection "Invalid Connection String"
    
              Invalid database connection string format.
    

说明  
\---\---\-----  
测试 Analytics Service 的数据库连接字符串无效。