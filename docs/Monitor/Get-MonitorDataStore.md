# Get-MonitorDataStore

Gets details for each of the Monitor data stores.

## 语法

    Get-MonitorDataStore [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Returns an object for each of the Monitor data stores describing the connection string, data store name, db type, provider, schema name, and DB status.

A database connection must be configured in order for this command to be used if the service has a secondary data store. This is not required for the site data store.

## 相关命令

- [Reset-MonitorDataStore](Reset-MonitorDataStore.html)

## 参数

| 名称           | 说明                                                         | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.Monitor.Sdk.DataStoreConfiguration

An object describing the connection string, data store name, database type, provider, schema name and database status.## Notes If the command fails, the following errors can be returned.  
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

    c:\PS>Get-MonitorDataStore
    
    ConnectionString : Server=.\SQLEXPRESS;Initial Catalog = databaseName; Integrated Security = True
    DataStore        : Site
    DatabaseType     : SqlServer
    Provider         : MSSQL
    SchemaName       : MonitorSiteSchema
    Status           : OK
    
    ConnectionString :
    DataStore        : Secondary
    DatabaseType     : SqlServer
    Provider         : MSSQL
    SchemaName       : MonitorSecondarySchema
    Status           : DBUnconfigured
    

Description  
\---\---\-----  
Get the database connection string for the Monitor Service.