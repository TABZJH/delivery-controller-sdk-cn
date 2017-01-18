# Test-EnvTestDBConnection

Tests whether a database is suitable for use by the Citrix EnvTest Service.

## 语法

    Test-EnvTestDBConnection [-DBConnection] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Tests whether the database specified in the given connection string is suitable for use by the currently selected Citrix EnvTest Service instance.

服务会尝试联系指定的数据库，并返回指示数据库是否可联系并可用的状态。 测试不影响当前以任何方式建立的服务实例到另一个数据库的任何连接。 测试的连接字符串不会记录。

仅支持在连接字符串中使用 Windows 身份验证；如果连接字符串包含 SQL 身份验证凭据，总是会因为无效而被拒绝。

The current service instance is that on the local machine, or that explicitly specified by the last usage of the -AdminAddress parameter to a EnvTest SDK cmdlet.

## 相关命令

- [Get-EnvTestServiceStatus](Get-EnvTestServiceStatus.html)
- [Get-EnvTestDBConnection](Get-EnvTestDBConnection.html)
- [Set-EnvTestDBConnection](Set-EnvTestDBConnection.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| DBConnection | Specifies the database connection string to be tested by the currently selected Citrix EnvTest Service instance.                                                       | true  | false |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.Fma.Sdk.Utilities.Service.ServiceStatusInfo

The Test-EnvTestDBConnection cmdlet returns an object of type ServiceStatusInfo describing the changes to the system that would result from using the specified connection string with the Set-EnvTestDBConnection cmdlet. The actual state of the system is not changed.  
The returned ServiceStatusInfo object has two properties: ServiceStatus, which gives the status of the selected EnvTest Service instance that would result from adopting the connection string, and ExtraInfo, which is a dictionary providing extra diagnostics information for the database identified by the connection string.  
Possible ServiceStatus values are:  
-- OK:  
The Set-EnvTestDBConnection command would succeed if it were executed with the supplied connection string.  
-- DBUnconfigured:  
No database connection string is set for the service instance.  
-- DBRejectedConnection:  
The database rejected the logon attempt from the EnvTest Service instance. This may be because the service attempted to log on with invalid credentials or because a database has not been installed in the specified location.  
-- InvalidDBConfigured:  
The specified database does not exist, is not visible to the EnvTest Service instance, or the service's schema within the database is invalid.  
-- DBNotFound:  
The specified database could not be located with the given connection string.  
-- DBNewerVersionThanService:  
The EnvTest Service instance is older than, and incompatible with, the service's schema in the database. The service instance needs upgrading.  
-- DBOlderVersionThanService:  
The EnvTest Service instance is newer than, and incompatible with, the service's schema in the database. The database schema needs upgrading.  
-- DBVersionChangeInProgress:  
A database schema upgrade is currently in progress.  
-- PendingFailure:  
Connectivity between the EnvTest Service instance and the database has been lost. This may be a transitory network error, but may indicate a loss of connectivity that requires administrator intervention.  
-- Failed:  
Connectivity between the EnvTest Service instance and the database has been lost for an extended period of time, or has failed due to a configuration problem. 服务实例与数据库之间的连接不可用时，服务实例无法运行。  
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

    C:\PS>Test-EnvTestDBConnection "Server=dbserver\SQLEXPRESS;Database=XDDB;Trusted_Connection=True"
    

说明  
\---\---\-----  
测试服务实例是否可以使用名为 XDDB 的数据库，该数据库在名为 dbserver 的计算机上运行的 SQL Server Express 数据库上。 需要集成 Windows 身份验证。

### 示例 2

    c:\PS>Test-EnvTestDBConnection -DBConnection "Invalid Connection String"
    
              Invalid database connection string format.
    

Description  
\---\---\-----  
Tests an invalid database connection string for the EnvTest Service.