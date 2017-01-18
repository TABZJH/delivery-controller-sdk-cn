# Get-SfDBConnection

Gets the database string for the specified data store used by the Storefront Service.

## 语法

    Get-SfDBConnection [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Returns the database connection string from the currently selected Storefront Service instance.

如果返回的字符串为空，则没有指定有效的连接字符串。在这种情况下，服务正在运行，但处于空闲状态，并等待指定一个有效的连接字符串。

The current service instance is that on the local machine, or that explicitly specified by the last usage of the -AdminAddress parameter to a Storefront SDK cmdlet.

## 相关命令

- [Get-SfServiceStatus](Get-SfServiceStatus.html)
- [Set-SfDBConnection](Set-SfDBConnection.html)
- [Test-SfDBConnection](Test-SfDBConnection.html)

## 参数

| 名称           | 说明                                                         | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### System.String

The database connection string configured for the current Storefront Service instance.## Notes If the command fails, the following errors can be returned.  
Error Codes  
\---\---\-----  
NoDBConnections  
The database connection string for the Storefront Service has not been specified.  
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

    c:\PS>Get-SfDBConnection
    
    Server=serverName\SQLEXPRESS;Initial Catalog = databaseName;  Integrated Security = True
    

Description  
\---\---\-----  
Get the database connection string for the Storefront Service.