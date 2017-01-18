# Get-AcctDBConnection

获取 ADIdentity Service 使用的指定数据存储的数据库字符串。

## 语法

    Get-AcctDBConnection [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

从当前所选 ADIdentity Service 实例返回数据库连接字符串。

如果返回的字符串为空，则没有指定有效的连接字符串。在这种情况下，服务正在运行，但处于空闲状态，并等待指定一个有效的连接字符串。

当前服务实例在本地计算机上，或由最后一次使用的 -AdminAddress 参数显式指定给 ADIdentity SDK cmdlet。

## 相关命令

- [Get-AcctServiceStatus](Get-AcctServiceStatus.html)
- [Set-AcctDBConnection](Set-AcctDBConnection.html)
- [Test-AcctDBConnection](Test-AcctDBConnection.html)

## 参数

| 名称           | 说明                                                         | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### System.String

为当前 ADIdentity Service 实例配置的数据库连接字符串。## 注意 如果命令失败，会返回以下错误。  
错误代码  
\---\---\-----  
NoDBConnections  
未指定 ADIdentity Service 的数据库连接字符串。  
PermissionDenied  
您没有执行此命令的权限。  
AuthorizationError  
与 Citrix Delegated Administration Service 通信时出现问题。  
CommunicationError  
与远程服务通信时出现问题。  
ExceptionThrown  
发生意外错误。 有关更多详细信息，请参阅控制器上的 Windows 事件日志或 XenDesktop 日志。

## 示例

### 示例 1

    c:\PS>Get-AcctDBConnection
    
    Server=serverName\SQLEXPRESS;Initial Catalog = databaseName;  Integrated Security = True
    

说明  
\---\---\-----  
获取 ADIdentity Service 的数据库连接字符串。