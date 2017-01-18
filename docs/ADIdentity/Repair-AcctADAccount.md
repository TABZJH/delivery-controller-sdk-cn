# Repair-AcctADAccount

重置给定帐户的 Active Directory 计算机密码。

## 语法

    Repair-AcctADAccount -ADAccountName <String[]> [-Password <String>] [-SecurePassword <SecureString>] [-ADUserName <String>] [-ADPassword <SecureString>] [-Force] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Repair-AcctADAccount -ADAccountSid <String[]> [-Password <String>] [-SecurePassword <SecureString>] [-ADUserName <String>] [-ADPassword <SecureString>] [-Force] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

用于将 Active Directory 中存储的帐户密码与 AD Identity Service 中存储的密码同步。 如果成功，这将使 AD Identity Service 帐户状态被重置为“available”，以便其他 Machine Creation Services 可以使用它。

如果未使用 Password 或 SecurePassword 参数提供当前帐户密码，这就需要启动运行空间的用户在 Active Directory 中具有所需权限以重置 Active Directory 帐户密码。

如果提供了当前帐户密码，则此命令将使用不需要在 Active Directory 中具有任何提升权限的密码更改操作。

## 相关命令

- [New-AcctADAccount](New-AcctADAccount.html)
- [Add-AcctADAccount](Add-AcctADAccount.html)
- [Remove-AcctADAccount](Remove-AcctADAccount.html)
- [Unlock-AcctADAccount](Unlock-AcctADAccount.html)
- [Update-AcctADAccount](Update-AcctADAccount.html)
- [Get-AcctADAccount](Get-AcctADAccount.html)

## 参数

| 名称             | 说明                                                                                                                                                                                | 是否必需？ | 管道输入                  | 默认值                                   |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| ADAccountName  | 要修复的 Active Directory 帐户名称。 接受以下格式的 Active Directory 帐户︰完全限定的 DN，例如 CN=MyComputer,OU=Computers,DC=MyDomain,DC=Com；UPN 格式，例如 MyComputer@MyDomain.Com；限定的域，例如 MyDomain\MyComputer。 | true  | false                 |                                       |
| ADAccountSid   | 要修复的 Active Directory 帐户 SID。                                                                                                                                                     | true  | true (ByPropertyName) |                                       |
| Password       | 计算机帐户的当前密码。                                                                                                                                                                       | false | false                 |                                       |
| SecurePassword | 帐户的当前密码（在一个安全字符串类中提供） 。                                                                                                                                                           | false | false                 |                                       |
| ADUserName     | 具有写入权限的 Active Directoy 用户帐户的用户名。此参数仅用于云部署。                                                                                                                                       | false | false                 |                                       |
| ADPassword     | 具有写入权限的 Active Directoy 用户帐户的匹配密码。此参数仅用于云部署。                                                                                                                                      | false | false                 |                                       |
| Force          | 指示是否可以修复标记为“in-use”的帐户。                                                                                                                                                           | false | false                 |                                       |
| LoggingId      | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。            | false | false                 |                                       |
| AdminAddress   | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                         | false | false                 | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.ADIdentity.Sdk.AccountOperationSummary  
Repair-AcctADAccout 命令返回包含以下参数的对象：  
SuccessfulAccountsCount <int>  
已成功修复的帐户数。  
FailedAccountsCount <int>  
未修复的帐户数。  
FailedAccounts <Citrix.ADIdentity.Sdk.AccountError[]>  
未能修复的帐户列表。 每个都有以下参数：  
ADAccountName <string>  
ADAccountSid <string>  
ErrorReason <adidentitystatus>  
这可以是下列其中之一  
UnableToConvertDomain  
IdentityNotLocatedInDomain  
IdentityNotFound  
IdentityObjectInUse  
IdentityObjectLocked  
ADServiceDatabaseError  
ADServiceDatabaseNotConfigured  
ADServiceStatusInvalidDb  
FailedToConnectToDomainController  
FailedToExecuteSearchInAD  
FailedToAccessComputerAccountInAD  
FailedToSetPasswordInAD  
FailedToChangePasswordInAD  
DiagnosticInformtion <exception>  
任何其他错误信息

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

    C:\PS>Repair-AcctADAccount -ADAccountName "Domain\account","domain\account2"
    
    
              SuccessfulAccountsCount       FailedAccountsCount    FailedAccounts
              -----------------------       -------------------    --------------
                                    2                         0    {}
    

说明  
\---\---\-----