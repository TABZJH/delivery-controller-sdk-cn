# Unlock-AcctADAccount

解锁 AD Identity Service 中的 AD 帐户。

## 语法

    Unlock-AcctADAccount -ADAccountName <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Unlock-AcctADAccount -ADAccountSid <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

用于解锁引用了指定 AD 帐户的 AD Identity Service 标识项。 Machine Creation Services (MCS) 正在处理与 AD 帐户有关的任务时，该帐户在 AD Identity Service 中标记为“locked”。 如果强制停止这些任务，尽管不再处理帐户，但帐户仍保持锁定状态。 此命令可解决此问题，但使用它时要小心，因为解锁 MCS 要求锁定的帐户可能导致 MCS 操作被取消。 仅当 MCS 已锁定帐户以用于置备操作且在未解锁帐户时此操作失败的情况下，使用此命令。

注意︰ 此命令不会对 Active Directory 中存储的帐户信息进行任何更改。

## 相关命令

- [Get-AcctADAccount](Get-AcctADAccount.html)
- [New-AcctADAccount](New-AcctADAccount.html)
- [Add-AcctADAccount](Add-AcctADAccount.html)
- [Repair-AcctADAccount](Repair-AcctADAccount.html)
- [Remove-AcctADAccount](Remove-AcctADAccount.html)
- [Update-AcctADAccount](Update-AcctADAccount.html)
- [Unlock-AcctADAccount](Unlock-AcctADAccount.html)

## 参数

| 名称            | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| ADAccountName | 要解锁的 AD 帐户名称。 接受以下格式的 AD 帐户名称︰完全限定的 DN，例如 CN=MyComputer,OU=Computers,DC=MyDomain,DC=Com；UPN 格式，例如 MyComputer@MyDomain.Com；限定的域，例如 MyDomain\MyComputer。                | true  | false                 |                                       |
| ADAccountSid  | 表示要解锁的帐户的 AD 帐户 SID。                                                                                                                                                   | true  | true (ByPropertyName) |                                       |
| LoggingId     | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress  | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                              | false | false                 | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.ADIdentity.Sdk.IdentityInPool  
可以通过管道将包含名为“ADAccountSID”的参数的对象传送到 unlock-AcctADAccount。

## 返回值

### 

## 注意 如果失败，会发生以下错误。  
错误代码  
\---\---\-----  
IdentityNotLocatedInDomain  
在 Active Directory 中找不到指定的 AD 帐户。  
IdentityObjectNotFound  
找不到标识。  
IdentityAlreadyUnlocked  
标识未锁定。  
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

    c:\PS>Unlock-AcctADAccount -ADAccountName Domain\account
    

说明  
\---\---\-----  
解锁名为“Domain\account”的 AD 帐户。

### 示例 2

    c:\PS>Get-AcctADAccount -Filter {lock -eq $true} | Unlock-AcctADAccount
    

说明  
\---\---\-----  
解锁所有锁定的 AD 帐户。