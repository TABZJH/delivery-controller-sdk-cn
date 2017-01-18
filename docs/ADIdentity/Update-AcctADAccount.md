# Update-AcctADAccount

刷新 AD Identity Service 中存储的 AD 计算机帐户状态。

## 语法

    Update-AcctADAccount [-IdentityPoolName] <String> [-AllAccounts] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Update-AcctADAccount -IdentityPoolUid <Guid> [-AllAccounts] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

用于将 AD Identity Service 中存储的 AD 帐户的状态与 AD 帐户本身同步。 默认情况下，会检查标记为“error”的所有帐户以确定帐户是否仍处于错误状态 （即已禁用或已锁定）。 如果指定“AllAccounts”选项，它将检查不是处于错误状态的帐户，并更新这些帐户的状态。

## 相关命令

- [New-AcctADAccount](New-AcctADAccount.html)
- [Add-AcctADAccount](Add-AcctADAccount.html)
- [Remove-AcctADAccount](Remove-AcctADAccount.html)
- [Repair-AcctADAccount](Repair-AcctADAccount.html)
- [Unlock-AcctADAccount](Unlock-AcctADAccount.html)
- [Get-AcctADAccount](Get-AcctADAccount.html)

## 参数

| 名称               | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| IdentityPoolName | 要刷新的帐户的标识池的名称。                                                                                                                                                         | true  | true (ByPropertyName) |                                       |
| IdentityPoolUid  | 要刷新的 AD 帐户的标识池的唯一标识符。                                                                                                                                                  | true  | false                 |                                       |
| AllAccounts      | 指示是应该刷新所有帐户还是只刷新标记为错误状态的帐户。                                                                                                                                            | false | false                 | false                                 |
| LoggingId        | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress     | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                              | false | false                 | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 

## 注意 如果失败，会发生以下错误。  
错误代码  
\---\---\-----  
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

    c:\PS>Update-AcctADAccount -IdentityPoolName MyPool
    

说明  
\---\---\-----  
检查标识池 MyPool 中当前标记为处于 Error 状态的所有帐户，并检查这些帐户现在是否可用。

### 示例 2

    c:\PS>Update-AcctADAccount -IdentityPoolName MyPool -AllAccounts
    

说明  
\---\---\-----  
检查标识池 MyPool 中根据情况标记为 Available、InUse、Tainted 或 Error 的所有帐户的状态。