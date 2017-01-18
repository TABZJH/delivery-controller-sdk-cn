# Get-BrokerInstalledDbVersion

Gets a list of all available database schema versions for the Broker Service.

## 语法

    Get-BrokerInstalledDbVersion [-Upgrade] [-Downgrade] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Gets the current version number of the Citrix Broker Service database schema when called with no parameters.

如果调用时使用 -Upgrade 参数，则获取升级可以执行到的服务架构版本号。

如果调用时使用 -Downgrade 参数，则获取降级可以执行到的服务架构版本号。

The SQL scripts to perform schema upgrades and downgrades can be obtained using the Get-BrokerDBVersionChangeScript cmdlet. Citrix 建议尽可能使用 Studio 执行服务架构升级，而不是手动通过 SDK 升级。

一次只能提供 -Upgrade 参数或 -Downgrade 参数之一。

## 相关命令

- [Get-BrokerDBVersionChangeScript](Get-BrokerDBVersionChangeScript.html)
- [Get-BrokerDBSchema](Get-BrokerDBSchema.html)

## 参数

| 名称           | 说明                                                                                                                                                 | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| 升级           | 指定只应返回当前数据库版本可以更新到的架构版本。                                                                                                                           | false | false |                                                                                        |
| Downgrade    | 指定只应返回当前数据库版本可以还原到的架构版本。                                                                                                                           | false | false |                                                                                        |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### System.Version

Get-BrokerInstalledDBVersion returns database schema version numbers as requested.## Notes If the command fails, the following errors can be returned.  
Error Codes  
\---\---\-----  
InvalidParameterCombination  
Both the Upgrade and Downgrade flags were specified.  
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

    C:\PS>Get-BrokerInstalledDBVersion
    

Description  
\---\---\-----  
Gets the current Citrix Broker Service database schema version number.

### 示例 2

    C:\PS>Get-BrokerInstalledDBVersion -Upgrade
    

Description  
\---\---\-----  
Get the versions of the Broker Service database schema for which upgrade scripts are supplied.