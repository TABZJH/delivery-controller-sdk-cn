# Get-BrokerDBConnection

Gets the database connection string for the specified data store used by the Broker Service.

## 语法

    Get-BrokerDBConnection [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Gets the database connection string from the currently selected Broker Service instance.

如果返回的字符串为空，则没有指定有效的连接字符串。在这种情况下，服务正在运行，但处于空闲状态，并等待指定一个有效的连接字符串。

The current service instance is the one on the local machine, or the one most recently specified using the -AdminAddress parameter of a Broker SDK cmdlet.

## 相关命令

- [Set-BrokerDBConnection](Set-BrokerDBConnection.html)
- [Get-BrokerServiceStatus](Get-BrokerServiceStatus.html)
- [Test-BrokerDBConnection](Test-BrokerDBConnection.html)

## 参数

| 名称           | 说明                                                                                                                                                 | 是否必需？ | 管道输入  | 默认值                                                                                    |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | -------------------------------------------------------------------------------------- |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### System.String

The database connection string configured for the current Broker Service instance.## Notes If the command fails, the following errors can be returned.  
Error Codes  
\---\---\-----  
NoDBConnections  
The database connection string for the Broker Service has not been specified.  
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

    C:\PS> Get-BrokerDBConnection -AdminAddress controller1.mydomain.net
    

Description  
\---\---\-----  
Gets the database connection string in use by the Broker Service instance running on controller "controller1.mydomain.net".