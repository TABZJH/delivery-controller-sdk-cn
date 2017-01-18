# Unlock-AcctIdentityPool

解锁标识池。

## 语法

    Unlock-AcctIdentityPool [-IdentityPoolName] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Unlock-AcctIdentityPool -IdentityPoolUid <Guid> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

用于解锁指定的标识池。 更新标识池时（例如，在其中创建新帐户时）自动锁定标识池。 该池不得保持在锁定状态；如果发生这种情况，可以使用此命令从错误中恢复。 使用此命令时要小心，因为解锁应该处于锁定状态的标识池可能会导致发生意外行为。

## 相关命令

- [New-AcctIdentityPool](New-AcctIdentityPool.html)
- [Remove-AcctIdentityPool](Remove-AcctIdentityPool.html)
- [Set-AcctIdentityPool](Set-AcctIdentityPool.html)

## 参数

| 名称               | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| IdentityPoolName | 要解锁的标识池的名称。                                                                                                                                                            | true  | true (ByPropertyName) |                                       |
| IdentityPoolUid  | 要解锁的标识池的唯一标识符。                                                                                                                                                         | true  | false                 |                                       |
| LoggingId        | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress     | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                              | false | false                 | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.ADIdentity.Sdk.IdentityInPool  
可以通过管道将包含名为“IdentityPoolName”的参数的对象传送到 unlock-AcctIdentityPool。

## 返回值

### 

## 注意 如果失败，会发生以下错误。  
错误代码  
\---\---\-----  
IdentityPollObjectNotFound  
找不到指定的标识池。  
IdentityPoolAlreadyUnlocked  
指定的标识池未锁定。  
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

    C:\PS>Unlock-AcctIdentityPool -IdentityPool MyPool
    

说明  
\---\---\-----  
解锁名为“MyPool”的标识池。

### 示例 2

    C:\PS>Get-AcctIdentityPool -Filter {Lock -eq $true} | Unlock-AcctIdentityPool
    

说明  
\---\---\-----  
解锁所有锁定的标识池。