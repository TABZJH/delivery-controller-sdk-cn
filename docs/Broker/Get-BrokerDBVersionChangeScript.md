# Get-BrokerDBVersionChangeScript

Gets an SQL service schema update script for the Citrix Broker Service.

## 语法

    Get-BrokerDBVersionChangeScript -DatabaseName <String> -TargetVersion <Version> [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Gets an SQL script that can be used to update the current Citrix Broker Service database schema. An update can be an upgrade or downgrade.

A script can be obtained to update the current service schema to any version that is reachable by applying available schema update packages that have been uploaded by the Citrix Broker Service.

通常情况下，这种机制用于将当前服务架构更新到较新版本，但它也可用于还原以前应用的更新。

可以使用 SQL Server SQLCMD 实用程序或通过将脚本复制到 SQL Server Management Studio (SSMS) 查询窗口并执行查询来运行获取的 SQL 脚本。 如果使用 SSMS，必须以“SQLCMD 模式”执行查询。

The schema update packages used to generate update scripts are stored in the database; because of this, any Citrix Broker Service in the site can be used to obtain a schema update script.

数据库中有更新软件包并不表示更新已实际应用于服务架构。 此外，应用更新并不删除关联的更新软件包。

使用更新脚本时务必小心。 Citrix 建议尽可能使用 Studio 执行服务架构升级，而不是手动通过 SDK 升级。 尝试更新之前应备份数据库。 The database script may also require exclusive use of the schema, in which case all Citrix Broker Services must be shutdown before applying the update.

Once an update has been applied to the service schema, any existing Citrix Broker Services that are incompatible with the updated schema will cease to operate. The service state, as reported by Get-BrokerServiceStatus, provides information about the service compatibility (e.g. DBNewerVersionThanService).

## 相关命令

- [Get-BrokerInstalledDBVersion](Get-BrokerInstalledDBVersion.html)
- [Get-BrokerServiceStatus](Get-BrokerServiceStatus.html)
- [Get-BrokerDBSchema](Get-BrokerDBSchema.html)

## 参数

| 名称            | 说明                                                                                                                                                 | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| DatabaseName  | The name of the database containing the Citrix Broker Service schema to be updated.                                                                | true  | false |                                                                                        |
| TargetVersion | 更新的所需目标服务架构版本。这是应用更新脚本后获取的服务架构版本。                                                                                                                  | true  | false |                                                                                        |
| AdminAddress  | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### System.Management.Automation.PSObject

The Get-BrokerDBVersionChangeScript cmdlet returns a PSObject containing a script that can be used to update the Citrix Broker Service database schema. The object has the following properties:  
-- Script  
The raw text of the SQL script to apply the update.  
-- CanUndo  
If true, indicates that after the update has been applied, a script to revert from the updated schema to the schema state prior to the update can be obtained. Because Get-BrokerDBVersionChangeScript gets only update scripts relating to the current schema version, a script to revert an update can be obtained only after the update has been applied.  
-- NeedExclusiveAccess  
If true, indicates that the update requires exclusive access to the Citrix Broker Service's schema while the update is applied; all Citrix Broker Services must be shutdown during the update.## Notes The PSObject returned by this cmdlet contains the following properties:  
-- Script The raw text of the SQL script to apply the update, or null in the case when no upgrade path to the specified target version exists.  
-- NeedExclusiveAccess Indicates whether all services in the service group must be shut down during the update or not.  
-- CanUndo Indicates whether the generated script allows the updated schema to be reverted to the state prior to the update.  
Scripts to update the schema version are stored in the database so any service in the service group can obtain these scripts. 使用更新脚本时务必非常小心。 Citrix 建议在尝试升级架构之前备份数据库。 Database update scripts may require exclusive use of the schema and so may not be able to execute while any Broker services are running. 但这取决于要执行的特定更新程序。  
执行架构更新后，需要以前版本的架构的服务可能会停止运行。 The ServiceState parameter reported by the Get-BrokerServiceStatus command provides information about service compatibility. For example, if the schema has been upgraded to a more recent version that a service cannot use, the service reports "DBNewerVersionThanService".  
If the command fails, the following errors can be returned.  
Error Codes  
\---\---\-----  
NoOp  
The operation was successful but had no effect.  
NoDBConnections  
The database connection string for the Broker Service has not been specified.  
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

    C:\PS> $update = Get-BrokerDBVersionChangeScript -DatabaseName MyDb -TargetVersion 1.0.75.0
              C:\PS> $update.Script > update_75.sql
    

说明  
\---\---\-----  
获取用于将当前架构更新到版本 1.0.75.0 的 SQL 更新脚本。生成的 update_75.sql 脚本适合直接用于 SQL Server SQLCMD 实用程序。