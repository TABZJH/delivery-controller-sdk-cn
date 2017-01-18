# Add-AcctADAccount

从 Active Directory 导入 Active Directory 计算机帐户以用于 AD Identity Service。

## 语法

    Add-AcctADAccount [-IdentityPoolName] <String> -ADAccountName <String[]> [-Password <String>] [-SecurePassword <SecureString>] [-ADUserName <String>] [-ADPassword <SecureString>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Add-AcctADAccount -IdentityPoolUid <Guid> -ADAccountName <String[]> [-Password <String>] [-SecurePassword <SecureString>] [-ADUserName <String>] [-ADPassword <SecureString>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

用于提供 Active Directory 中已有的 Active Directory 计算机帐户，以供 Citrix AD Identity Service 和其他 Citrix Machine Creation Services 使用。

使用此命令时，需要对 Active Directory 中的帐户进行修改的所有方面都将使用 PowerShell 运行空间正在使用的帐户进行操作。 这意味着，如果需要重置帐户密码，在 PowerShell 中执行操作的用户必须在 Active Directory 中有足够权限，此操作才能成功完成。

以下规则应用于 Active Directory 帐户的导入；如果提供了当前帐户密码，cmdlet 将尝试更改密码，以便只有 Citrix Identity Service 知道密码。 这使用密码更改操作，不需要 AD 帐户管理权限。 如果未提供当前密码，cmdlet 将尝试重置 Active Directory 帐户密码，以便只有 Citrix Identity Service 知道密码。 这要求 cmdlet 在 Active Directory 中具有足够权限，才能进行帐户密码重置。 在 Active Directory 中处于已禁用或已锁定状态的导入帐户，导入时，帐户标记为错误状态。 如果帐户要导入到的标识池没有设置域，则假设为导入到标识池的第一个帐户的域。

## 相关命令

- [New-AcctADAccount](New-AcctADAccount.html)
- [Remove-AcctADAccount](Remove-AcctADAccount.html)
- [Repair-AcctADAccount](Repair-AcctADAccount.html)
- [Get-AcctADAccount](Get-AcctADAccount.html)
- [Update-AcctADAccount](Update-AcctADAccount.html)
- [Unlock-AcctADAccount](Unlock-AcctADAccount.html)

## 参数

| 名称               | 说明                                                                                                                                                                                   | 是否必需？ | 管道输入                  | 默认值                                   |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----- | --------------------- | ------------------------------------- |
| IdentityPoolName | 要向其中添加导入帐户的标识池的名称。                                                                                                                                                                   | true  | true (ByPropertyName) |                                       |
| ADAccountName    | 要导入的 Active Directory 帐户名称。  
接受以下格式的 Active Directory 帐户︰ 完全限定的 DN，例如 CN=MyComputer,OU=Computers,DC=MyDomain,DC=Com；UPN 格式，例如 MyComputer@MyDomain.Com；限定的域，例如 MyDomain\MyComputer。 | true  | false                 |                                       |
| IdentityPoolUid  | 要将导入帐户添加到其中的标识池的唯一标识符。                                                                                                                                                               | true  | true (ByPropertyName) |                                       |
| Password         | 计算机帐户的当前密码。                                                                                                                                                                          | false | false                 |                                       |
| SecurePassword   | 帐户的当前密码（在一个安全字符串类中提供） 。                                                                                                                                                              | false | false                 |                                       |
| ADUserName       | 具有写入权限的 Active Directoy 用户帐户的用户名。此参数仅用于云部署。                                                                                                                                          | false | false                 |                                       |
| ADPassword       | 具有写入权限的 Active Directoy 用户帐户的匹配密码。此参数仅用于云部署。                                                                                                                                         | false | false                 |                                       |
| LoggingId        | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。               | false | false                 |                                       |
| AdminAddress     | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                            | false | false                 | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.ADIdentity.Sdk.AccountOperationDetailedSummary  
Add-AcctADAccount 返回包含以下参数的对象；  
SuccessfulAccountsCount <int>  
成功添加的帐户数  
FailedAccountsCount <int>  
未添加的帐户数。  
FailedAccounts <Citrix.XDPowerShell.AccountError[]>  
未能添加的帐户列表。 每个都具有以下属性；  
ADAccountName <string>  
ADAccountSid <string>  
ErrorReason <adidentitystatus>  
这可以是下列其中之一  
UnableToConvertDomain  
UnableToAccessAccountProperties  
IdentityNotLocatedInDomain  
UnableToAccessAccountProperties  
IdentityDuplicateObjectExists  
IdentityObjectLocked  
IdentityObjectInUse  
FailedToConnectToDomainController  
FailedToExecuteSearchInAD  
FailedToAccessComputerAccountInAD  
FailedToSetPasswordInAD  
FailedToChangePasswordInAD  
ADServiceDatabaseError  
ADServiceDatabaseNotConfigured  
ADServiceStatusInvalidDb  
DiagnosticInformtion <exception>  
任何其他错误信息  
SuccessfulAccounts <Citrix.ADIdentity.Sdk.Identity[]>  
成功添加的帐户列表。 每个都具有以下属性；  
ADAccountSid <string>  
导入帐户的 AD 帐户 SID。  
ADAccountName <string>  
导入帐户的 AD 帐户名称。  
Domain <string>  
导入帐户的域。  
State <Citrix.ADIdentity.Sdk.ADIdentityState>  
帐户的状态。 这可以是：  
Available  
帐户未使用。  
InUse  
帐户正在使用中。  
Error  
帐户处于错误状态（即，帐户在 AD 中处于已锁定或已禁用状态）。  
Tainted  
帐户不再使用，但不再知道其密码。  
Lock<boolean>  
帐户处于锁定状态（在不属于 AD 的数据库中）。

## 注意 为了在以编程方式使用命令时维护最高安全性，Citrix 建议使用“SecurePassword”属性，而不是“Password”属性。  
如果失败，会发生以下错误。  
错误代码  
\---\---\-----  
IdentityPoolAlreadyLocked  
指定的标识池已被另一个操作锁定。  
IdentityPoolNotFound  
未找到指定的标识池。  
IdentityDuplicateObjectExists  
标识池已存在指定的 AD 帐户。  
PermissionDenied  
用户没有执行此操作的管理权限。  
ConfigurationLoggingError  
由于配置日志记录错误，无法执行操作  
DatabaseError  
尝试执行数据库操作时，服务发生错误。  
DatabaseNotConfigured  
由于未配置用于服务的数据库，无法完成操作。  
ServiceStatusInvalidDb  
尝试执行数据库操作时，服务发生错误 - 由于各种原因，无法与数据库通信。  
CommunicationError  
与服务通信时发生错误。  
ExceptionThrown  
发生意外错误。 要查找更多详细信息，请参阅使用的控制器上的 Windows 事件日志，或检查 XenDesktop 日志。

## 示例

### 示例 1

    C:\PS>Add-AcctADAccount -IdentityPoolName MyPool -ADAccountName "Domain\account","Domain\account2" -OutVariable result
    
      SuccessfulAccounts                SuccessfulAccountsCount       FailedAccountsCount    FailedAccounts
      ------------------                -----------------------       -------------------    --------------
      {domain\account, domain\account2} 2                            0                      {}
    
              $result[0].SuccessfulAccounts
    
              ADAccountSid  : S-1-5-21-1315084875-1285793635-2418178940-2644
              ADAccountName : domain\account
              Domain        : Domain.com
              State         : Available
              Lock          : False
    
              ADAccountSid  : S-1-5-21-1315084875-1285793635-2418178940-2645
              ADAccountName : domain\account2
              Domain        : Domain.com
              State         : Available
              Lock          : False
    

说明  
\---\---\-----  
将 AD 中的两个帐户（account 和 account2）导入名为“MyPool”的标识池