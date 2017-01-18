# Test-BrokerDBConnection

Tests whether a database is suitable for use by the Citrix Broker Service.

## 语法

    Test-BrokerDBConnection [-DBConnection] <String> [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Tests whether the database specified in the given connection string is suitable for use by the currently selected Citrix Broker Service instance.

服务会尝试联系指定的数据库，并返回指示数据库是否可联系并可用的状态。 测试不影响当前以任何方式建立的服务实例到另一个数据库的任何连接。 测试的连接字符串不会记录。

仅支持在连接字符串中使用 Windows 身份验证；如果连接字符串包含 SQL 身份验证凭据，总是会因为无效而被拒绝。

The current service instance is the one on the local machine, or the one most recently specified using the -AdminAddress parameter of a Broker SDK cmdlet.

## 相关命令

- [Get-BrokerServiceStatus](Get-BrokerServiceStatus.html)
- [Get-BrokerDBConnection](Get-BrokerDBConnection.html)
- [Set-BrokerDBConnection](Set-BrokerDBConnection.html)

## 参数

| 名称           | 说明                                                                                                                                                 | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| DBConnection | Specifies the database connection string to be tested by the currently selected Citrix Broker Service instance.                                    | true  | false |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 

## 返回值

### Citrix.Fma.Sdk.Utilities.Service.ServiceStatusInfo

The Test-BrokerDBConnection cmdlet returns an object describing the status of the selected Broker Service instance that would result if the connection string were used with the Set-BrokerDBConnection cmdlet together with extra diagnostics information for the specified connection string. The actual current status of the service is not changed. Possible diagnostic values are:  
-- OK:  
The Set-BrokerDBConnection command would succeed if it were executed with the supplied connection string.  
-- DBUnconfigured:  
No database connection string is set for the service instance.  
-- DBRejectedConnection:  
The database rejected the logon attempt from the Broker Service instance. This may be because the service attempted to log on with invalid credentials or because a database has not been installed in the specified location.  
-- InvalidDBConfigured:  
The specified database does not exist, is not visible to the Broker Service instance, or the service's schema within the database is invalid.  
-- DBNotFound:  
The specified database could not be located with the given connection string.  
-- DBNewerVersionThanService:  
The Broker Service instance is older than, and incompatible with, the service's schema in the database. The service instance needs upgrading.  
-- DBOlderVersionThanService:  
The Broker Service instance is newer than, and incompatible with, the service's schema in the database. The database schema needs upgrading.  
-- DBVersionChangeInProgress:  
A database schema upgrade is currently in progress.  
-- PendingFailure:  
Connectivity between the Broker Service instance and the database has been lost. This may be a transitory network error, but may indicate a loss of connectivity that requires administrator intervention.  
-- Failed:  
Connectivity between the Broker Service instance and the database has been lost for an extended period of time, or has failed due to a configuration problem. The service instance cannot operate while its connection to the database is unavailable.  
-- Unknown:  
Service status cannot be determined.## Notes If the command fails, the following errors can be returned.  
Error Codes  
\---\---\-----  
InvalidDBConnectionString  
The database connection string has an invalid format.  
PermissionDenied  
You do not have permission to execute this command.  
AuthorizationError  
There was a problem communicating with the Citrix Delegated Administration Service.  
ConfigurationLoggingError  
The operation could not be performed because of a configuration logging error.  
CommunicationError  
There was a problem communicating with the remote service.  
ExceptionThrown  
An unexpected error occurred. 有关更多详细信息，请参阅控制器上的 Windows 事件日志或 XenDesktop 日志。

## 示例

### 示例 1

    C:\PS>Test-BrokerDBConnection "Server=dbserver\SQLEXPRESS;Database=XDDB;Trusted_Connection=True"
    

说明  
\---\---\-----  
测试服务实例是否可以使用名为 XDDB 的数据库，该数据库在名为 dbserver 的计算机上运行的 SQL Server Express 数据库上。 需要集成 Windows 身份验证。