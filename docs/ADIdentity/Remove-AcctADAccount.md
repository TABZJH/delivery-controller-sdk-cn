# Remove-AcctADAccount

从标识池中删除 AD 计算机帐户。

## 语法

    Remove-AcctADAccount [-IdentityPoolName] <String> -ADAccountName <String[]> [-ADUserName <String>] [-ADPassword <SecureString>] [-RemovalOption <ADIdentityRemoveAccountOption>] [-Force] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-AcctADAccount [-IdentityPoolName] <String> -ADAccountSid <String[]> [-ADUserName <String>] [-ADPassword <SecureString>] [-RemovalOption <ADIdentityRemoveAccountOption>] [-Force] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-AcctADAccount -IdentityPoolUid <Guid> -ADAccountName <String[]> [-ADUserName <String>] [-ADPassword <SecureString>] [-RemovalOption <ADIdentityRemoveAccountOption>] [-Force] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-AcctADAccount -IdentityPoolUid <Guid> -ADAccountSid <String[]> [-ADUserName <String>] [-ADPassword <SecureString>] [-RemovalOption <ADIdentityRemoveAccountOption>] [-Force] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

用于从标识池中删除 AD 帐户。 这将从 Citrix 服务管理作用域中删除 AD 帐户。 此过程提供用于在 AD 中删除帐户（或禁用帐户）的选项（如果需要）。

使用此命令时，需要对 AD 中的帐户进行修改的所有方面都将使用运行空间正在使用的帐户进行操作。 这意味着，如果要从 AD 中删除帐户或禁用帐户，在 PowerShell 中执行操作的用户必须在 AD 中有足够的权限才能成功完成此操作。

如果指定了用于从 AD 中删除帐户或在 AD 中禁用帐户的选项，AD 操作必须成功才能从 Citrix AD Identity Service 数据库中删除帐户。 使用 Force 参数时请务必小心，因为这允许删除处于“inUse”状态的帐户，而这可能会导致计算机变为不可用。

## 相关命令

- [New-AcctADAccount](New-AcctADAccount.html)
- [Add-AcctADAccount](Add-AcctADAccount.html)
- [Repair-AcctADAccount](Repair-AcctADAccount.html)
- [Unlock-AcctADAccount](Unlock-AcctADAccount.html)
- [Update-AcctADAccount](Update-AcctADAccount.html)
- [Get-AcctADAccount](Get-AcctADAccount.html)

## 参数

| 名称               | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| IdentityPoolName | 要从中删除帐户的标识池。                                                                                                                                                           | true  | false                 |                                       |
| ADAccountName    | 要删除的 AD 帐户名称。 接受以下格式的 AD 帐户︰完全限定的 DN，例如 CN=MyComputer,OU=Computers,DC=MyDomain,DC=Com；UPN 格式，例如 MyComputer@MyDomain.Com；限定的域，例如 MyDomain\MyComputer。                  | true  | false                 |                                       |
| ADAccountSid     | 要删除的帐户的 Active Directory 帐户 SID。                                                                                                                                       | true  | true (ByPropertyName) |                                       |
| IdentityPoolUid  | 要从中删除帐户的标识池的唯一标识符。                                                                                                                                                     | true  | true (ByPropertyName) |                                       |
| ADUserName       | 具有写入权限的 Active Directoy 用户帐户的用户名。此参数仅用于云部署。                                                                                                                            | false | false                 |                                       |
| ADPassword       | 具有写入权限的 Active Directoy 用户帐户的匹配密码。此参数仅用于云部署。                                                                                                                           | false | false                 |                                       |
| RemovalOption    | 定义与 AD 帐户相关的行为。  
None - 不尝试从 AD 中删除帐户 Delete - 尝试从 AD 中删除帐户 Disable - 尝试在 AD 中禁用帐户                                                                                    | false | false                 | 无                                     |
| Force            | 指示是否可以删除标记为“in-use”的帐户。                                                                                                                                                | false | false                 |                                       |
| LoggingId        | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress     | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                              | false | false                 | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.ADIdentity.Sdk.AccountOperationSummary  
remove-AcctADAccout 命令返回包含以下参数的对象；  
SuccessfulAccountsCount <int>  
成功删除的帐户数。  
FailedAccountsCount <int>  
未删除的帐户数。  
FailedAccounts <Citrix.ADIdentity.Sdk.AccountError[]>  
未能删除的帐户列表。 每个都有以下参数：  
ADAccountName <string>  
ADAccountSid <string>  
ErrorReason <adidentitystatus>  
这可以是下列其中之一  
UnableToConvertDomain  
IdentityNotLocatedInDomain  
IdentityNotInIdentityPool  
IdentityObjectInUse  
IdentityObjectLocked  
ADServiceDatabaseError  
ADServiceDatabaseNotConfigured  
ADServiceStatusInvalidDb  
FailedToConnectToDomainController  
FailedToDisableAccountInAD  
FailedToDeleteAccountInAD  
FailedToExecuteSearchInAD  
FailedToAccessComputerAccountInAD  
DiagnosticInformtion <exception>  
任何其他错误信息

## 注意 如果失败，会发生以下错误。  
错误代码  
\---\---\-----  
IdentityPoolNotFound  
未找到指定的标识池。  
IdentityPoolAlreadyLocked  
指定的标识池已被另一个操作锁定。  
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

    C:\PS>Remove-AcctADAccount -IdentityPoolName MyPool -ADAccountName "Domain\account","domain\account2"
    
    
        SuccessfulAccountsCount       FailedAccountsCount    FailedAccounts
        -----------------------       -------------------    --------------
                              2                         0    {}
    

说明  
\---\---\-----  
从名为“MyPool”的标识池中删除两个帐户（account 和 account2），同时保留 AD 帐户不动。

### 示例 2

    C:\PS>Remove-AcctADAccount -IdentityPoolName MyPool -RemovalOption Delete -ADAccountName "Domain\account","domain\account2"
    
    
        SuccessfulAccountsCount       FailedAccountsCount    FailedAccounts
        -----------------------       -------------------    --------------
                              2                         0    {}
    

说明  
\---\---\-----  
从名为“MyPool”的标识池（以及从 Active Directory）中删除两个帐户（account 和 account2）。

### 示例 3

    C:\PS>Remove-AcctADAccount -IdentityPoolName MyPool -ADAccountName "Domain\account","domain\account2" -Force
    
    
        SuccessfulAccountsCount       FailedAccountsCount    FailedAccounts
        -----------------------       -------------------    --------------
                              2                         0    {}
    

说明  
\---\---\-----  
从名为“MyPool”的标识池中删除两个帐户（account 和 account2），同时保留 AD 帐户不动。 无论帐户是否处于“inUse”状态，都会将其删除。

### 示例 4

    C:\PS>Remove-AcctADAccount -IdentityPoolName MyPool -ADAccountName "Domain\account","domain\account2" -OutVariable result
    
        SuccessfulAccountsCount       FailedAccountsCount    FailedAccounts
        -----------------------       -------------------    --------------
        1                                               1    {account2}
    
        C:\PS>$result[0].FailedAccounts
    
        ADAccountName                 ADAccountSid           ErrorReason
        -------------                 -------------          ------------
        Domain\account2               account2               IdentityObjectLocked
    

说明  
\---\---\-----  
显示两个帐户之一删除失败，以及如何找出失败原因。

### 示例 5

    C:\PS>Remove-AcctADAccount -IdentityPoolName MyPool -ADAccountSid S-1-5-21-1315084875-1285793635-2418178940-2685
    
    
        SuccessfulAccountsCount       FailedAccountsCount    FailedAccounts
        -----------------------       -------------------    --------------
        1                                               0    {}
    

说明  
\---\---\-----  
从名为“MyPool”的标识池中删除一个帐户 (S-1-5-21-1315084875-1285793635-2418178940-2685)，同时保留 AD 不动。