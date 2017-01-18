# Remove-AcctIdentityPool

删除标识池。

## 语法

    Remove-AcctIdentityPool [-IdentityPoolName] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-AcctIdentityPool -IdentityPoolUid <Guid> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

用于删除标识池。必须先清空标识池中包含的任何 AD 帐户，然后才能将其删除。

## 相关命令

- [New-AcctIdentityPool](New-AcctIdentityPool.html)
- [Rename-AcctIdentityPool](Rename-AcctIdentityPool.html)
- [Set-AcctIdentityPool](Set-AcctIdentityPool.html)
- [Unlock-AcctIdentityPool](Unlock-AcctIdentityPool.html)

## 参数

| 名称               | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| IdentityPoolName | 要删除的标识池的名称。                                                                                                                                                            | true  | true (ByPropertyName) |                                       |
| IdentityPoolUid  | 要删除的标识池的唯一标识符。                                                                                                                                                         | true  | false                 |                                       |
| LoggingId        | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress     | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                              | false | false                 | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 

## 注意 如果失败，会发生以下错误。  
错误代码  
\---\---\-----  
IdentityPoolObjectNotFound  
找不到指定的标识池。  
UnableToRemoveDueToAssociatedAccounts  
标识池不为空。  
PermissionDenied  
用户没有执行此操作的管理权限。  
ConfigurationLoggingError  
由于配置日志记录错误，无法执行操作  
DatabaseError  
尝试执行数据库操作时，服务发生错误。  
DatabaseNotConfigured  
由于未配置用于服务的数据库，无法完成操作。  
ServiceStatusInvalidDb  
尝试执行数据库操作时，服务发生错误 - 由于  
各种原因，无法与数据库通信。  
CommunicationError  
与服务通信时发生错误。  
ExceptionThrown  
发生意外错误。 要查找更多详细信息，请参阅使用的控制器上的 Windows 事件日志，或检查 XenDesktop 日志。

## 示例

### 示例 1

    c:\Remove-AcctIdentityPool -IdentityPoolName MyPool
    

说明  
\---\---\-----  
删除名为“MyPool”的标识池。