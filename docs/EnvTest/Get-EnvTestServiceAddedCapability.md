# Get-EnvTestServiceAddedCapability

Gets any added capabilities for the EnvTest Service on the controller.

## 语法

    Get-EnvTestServiceAddedCapability [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Enables updates to the EnvTest Service on the controller to be detected.

无需配置数据库连接，即可使用此命令。

## 相关命令

## 参数

| 名称           | 说明                                                         | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 无

不能通过管道向此 cmdlet 传送输入。

## 返回值

### System.String

包含附加功能的字符串。## 注意 如果命令失败，会返回以下错误。  
错误代码  
\---\---\-----  
DatabaseError  
尝试执行数据库操作时，服务发生错误。  
DatabaseNotConfigured  
由于未配置用于服务的数据库，无法完成操作。  
DataStoreException  
尝试执行数据库操作时，服务发生错误 - 由于各种原因，无法与数据库通信。  
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

    C:\PS>Get-EnvTestServiceAddedCapability
    

Description  
\---\---\-----  
Get the added capabilities of the EnvTest Service.