# Set-ProvDBConnection

Configures a database connection for the MachineCreation Service.

## 语法

    Set-ProvDBConnection [-DBConnection] <String> [-Force] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Specifies the database connection string for use by the currently selected Citrix MachineCreation Service instance.

服务会记录连接字符串并尝试联系指定的数据库。 如果最初无法联系数据库，服务将以一定的时间间隔重试连接，直到成功与数据库建立了联系。

如果已记录一个数据库连接字符串，则不能为服务设置新的数据库连接字符串。 必须先将连接字符串设置为 $null。 此操作会导致服务重置并回到空闲状态，此时可以设置新的连接字符串。

成功为服务设置数据库连接字符串后，cmdlet 将返回“OK”状态。如果数据库连接字符串设置为 $null，则返回“DBUnconfigured”状态。

语法无效的连接字符串不会记录。

仅支持在连接字符串中使用 Windows 身份验证；如果连接字符串包含 SQL 身份验证凭据，总是会因为无效而被拒绝。

The current service instance is that on the local machine, or that explicitly specified by the last usage of the -AdminAddress parameter to a MachineCreation SDK cmdlet.

## 相关命令

- [Get-ProvServiceStatus](Get-ProvServiceStatus.html)
- [Get-ProvDBConnection](Get-ProvDBConnection.html)
- [Test-ProvDBConnection](Test-ProvDBConnection.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| DBConnection | Specifies the database connection string to be used by the MachineCreation Service. Passing in $null will clear any existing database connection configured.           | true  | false |                                       |
| Force        | 如果存在，允许在联系数据库或其他服务出现问题时，本地管理员可以将连接字符串设置为 null。                                                                                                                         | false | false | false                                 |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### Citrix.Fma.Sdk.Utilities.Service.ServiceStatusInfo

The Set-ProvDBConnection cmdlet returns an object describing the status of the MachineCreation Service together with extra diagnostics information. Possible values are:  
-- OK:  
The MachineCreation Service instance is configured with a valid database and service schema. The service is operational.  
-- DBUnconfigured:  
No database connection string is set for the MachineCreation Service instance.  
-- DBRejectedConnection:  
The database rejected the logon attempt from the MachineCreation Service. This may be because the service attempted to log on with invalid credentials or because a database has not been installed in the specified location.  
-- InvalidDBConfigured:  
The specified database does not exist, is not visible to the MachineCreation Service instance, or the service's schema within the database is invalid.  
-- DBNotFound:  
The specified database could not be located with the configured connection string.  
-- DBNewerVersionThanService:  
The version of the MachineCreation Service currently in use is newer than, and incompatible with, the version of the MachineCreation Service schema on the database. Upgrade the MachineCreation Service to a more recent version.  
-- DBOlderVersionThanService:  
The version of the MachineCreation Service schema on the database is newer than, and incompatible with, the version of the MachineCreation Service currently in use. Upgrade the database schema to a more recent version.  
-- DBVersionChangeInProgress:  
A database schema upgrade is in progress.  
-- PendingFailure:  
Connectivity between the MachineCreation Service instance and the database has been lost. This may be a transitory network error, but may indicate a loss of connectivity that requires administrator intervention.  
-- Failed:  
Connectivity between the MachineCreation Service instance and the database has been lost for an extended period of time, or has failed due to a configuration problem. The service instance cannot operate while its connection to the database is unavailable.  
-- Unknown:  
The status of the MachineCreation Service cannot be determined.## Notes If the command fails, the following errors can be returned.  
Error Codes  
\---\---\-----  
InvalidDBConnectionString  
The database connection string has an invalid format.  
DatabaseConnectionDetailsAlreadyConfigured  
There was already a database connection configured. 设置了配置后，只能将其设置为 $null。  
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

    C:\PS>Set-ProvDBConnection "Server=dbserver\SQLEXPRESS;Database=XDDB;Trusted_Connection=True"
    

说明  
\---\---\-----  
配置服务实例以使用名为 XDDB 的数据库，该数据库在名为 dbserver 的计算机上运行的 SQL Server Express 数据库上。 需要集成 Windows 身份验证。

### 示例 2

    C:\PS>Set-ProvDBConnection -DBConnection $null
    

说明  
\---\---\-----  
重置服务实例的数据库连接字符串。 服务实例重置并回到空闲状态，直到指定有效的新数据库连接字符串。

### 示例 3

    c:\PS>Set-ProvDBConnection -DBConnection "Server=serverName\SQLEXPRESS;Initial Catalog = databaseName;  Integrated Security = True"
              OK
    

Description  
\---\---\-----  
Configures a database connection string for the MachineCreation Service.

### 示例 4

    c:\PS>Set-ProvDBConnection -DBConnection "Invalid Connection String"
    
              Invalid database connection string format.
    

Description  
\---\---\-----  
Configures an invalid database connection string for the MachineCreation Service.