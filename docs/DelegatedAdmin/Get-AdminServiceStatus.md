# Get-AdminServiceStatus

Gets the current status of the DelegatedAdmin Service on the controller.

## 语法

    Get-AdminServiceStatus [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Enables the status of the DelegatedAdmin Service on the controller to be determined. The database connection to the service does not need to be configured before using this command.

## 相关命令

- [Set-AdminDBConnection](Set-AdminDBConnection.html)
- [Test-AdminDBConnection](Test-AdminDBConnection.html)
- [Get-AdminDBConnection](Get-AdminDBConnection.html)
- [Get-AdminDBSchema](Get-AdminDBSchema.html)

## 参数

| 名称           | 说明                                                         | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Fma.Sdk.Utilities.Service.ServiceStatusInfo

The Get-AdminServiceStatus command returns an object containing the status of the DelegatedAdmin Service together with extra diagnostics information.  
OK  
The DelegatedAdmin Service is running and is connected to a database containing a valid schema.  
DBUnconfigured  
The DelegatedAdmin Service does not have a database connection configured.  
DBRejectedConnection  
The database rejected the logon attempt from the DelegatedAdmin Service. 这可能是因为服务曾尝试使用无效凭据登录，或者因为尚未在指定位置安装数据库。  
InvalidDBConfigured  
数据库中缺少预期存储过程。 This may be because the DelegatedAdmin Service schema has not been added to the database.  
DBNotFound  
The specified database could not be located with the configured connection string.  
DBMissingOptionalFeature  
The DelegatedAdmin is connected to a database that is valid, but it does not have the full functionality required for optimal performance. Upgrading the database is advisable.  
DBMissingMandatoryFeature  
The DelegatedAdmin is connected to a database that is valid, but it does not have the full functionality required so the DelegatedAdmin cannot function. Upgrading the database is required.  
DBNewerVersionThanService  
The version of the DelegatedAdmin Service currently in use is incompatible with the version of the DelegatedAdmin Service schema on the database. Upgrade the DelegatedAdmin Service to a more recent version.  
DBOlderVersionThanService  
The version of the DelegatedAdmin Service schema on the database is incompatible with the version of the DelegatedAdmin Service currently in use. Upgrade the database schema to a more recent version.  
DBVersionChangeInProgress  
A database schema upgrade is currently in progress.  
PendingFailure  
Connectivity between the DelegatedAdmin Service and the database has been lost. This may be a transitory network error, but may indicate a loss of connectivity that requires administrator intervention.  
Failed  
Connectivity between the DelegatedAdmin and the database has been lost for an extended period of time, or has failed due to a configuration problem. The DelegatedAdmin service cannot operate while its connection to the database is unavailable.  
Unknown  
(0) The service status cannot be determined.## Notes If the command fails, the following errors can be returned.  
Error Codes  
\---\---\-----  
DatabaseError  
An error occurred in the service while attempting a database operation.  
DatabaseNotConfigured  
The operation could not be completed because the database for the service is not configured.  
DataStoreException  
An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.  
PermissionDenied  
You do not have permission to execute this command.  
AuthorizationError  
There was a problem communicating with the Citrix Delegated Administration Service.  
CommunicationError  
There was a problem communicating with the remote service.  
ExceptionThrown  
An unexpected error occurred. 有关更多详细信息，请参阅控制器上的 Windows 事件日志或 XenDesktop 日志。

## 示例

### 示例 1

    C:\PS>Get-AdminServiceStatus
    
    DBUnconfigured
    

Description  
\---\---\-----  
Get the current status of the DelegatedAdmin Service.