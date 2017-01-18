# New-AcctADAccount

在指定的标识池中创建 AD 计算机帐户。

## 语法

    New-AcctADAccount [-IdentityPoolName] <String> -Count <Int32> [-StartCount <Int32>] [-ADUserName <String>] [-ADPassword <SecureString>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    New-AcctADAccount [-IdentityPoolName] <String> -ADAccountName <String[]> [-ADUserName <String>] [-ADPassword <SecureString>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    New-AcctADAccount -IdentityPoolUid <Guid> -Count <Int32> [-StartCount <Int32>] [-ADUserName <String>] [-ADPassword <SecureString>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    New-AcctADAccount -IdentityPoolUid <Guid> -ADAccountName <String[]> [-ADUserName <String>] [-ADPassword <SecureString>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

用于在已有的标识池中创建新 AD 计算机帐户并注册它们。

创建帐户时使用标识池中存储的信息。这提供帐户名称（通过命名方案属性和起始计数）、域和 OU。

用于此命令的运行空间必须在 Active Directory 中有足够的权限，才能创建新计算机帐户。

AD 帐户名称将填充索引以使用标识池命名方案中指定的所有空间 （例如，“acc###”将变为“acc001”）。 但如果索引溢出可用空间，cmdlet 将扩展格式以使用下一个增量数字（例如，如果索引是无法置于三个“#”占位符的 10000，“acc###”将变为“acc1000”）。 如果此扩展的名称超过 15 个字符名称限制，则不会创建帐户。

任何时候一个特定标识池一次只能运行一个创建过程。 如果正在执行一个帐户创建过程时尝试开始另一个帐户创建过程，将返回错误。

## 相关命令

- [Add-AcctADAccount](Add-AcctADAccount.html)
- [Remove-AcctADAccount](Remove-AcctADAccount.html)
- [Get-AcctADAccount](Get-AcctADAccount.html)
- [Repair-AcctADAccount](Repair-AcctADAccount.html)
- [Unlock-AcctADAccount](Unlock-AcctADAccount.html)
- [Update-AcctADAccount](Update-AcctADAccount.html)

## 参数

| 名称               | 说明                                                                                                                                                                     | 是否必需？ | 管道输入  | 默认值                                   |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| IdentityPoolName | 要在其中创建帐户的标识池的名称。                                                                                                                                                       | true  | false |                                       |
| Count            | 要创建的帐户数。                                                                                                                                                               | true  | false |                                       |
| ADAccountName    | 要创建的 AD 帐户名称。这些都只是简单的计算机帐户名称，例如 MyVM001。                                                                                                                               | true  | false |                                       |
| IdentityPoolUid  | 要在其中创建帐户的标识池的唯一标识符。                                                                                                                                                    | true  | false |                                       |
| StartCount       | 创建过程的起始索引。                                                                                                                                                             | false | false |                                       |
| ADUserName       | 具有写入权限的 Active Directoy 用户帐户的用户名。此参数仅用于云部署。                                                                                                                            | false | false |                                       |
| ADPassword       | 具有写入权限的 Active Directoy 用户帐户的匹配密码。此参数仅用于云部署。                                                                                                                           | false | false |                                       |
| LoggingId        | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                       |
| AdminAddress     | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                              | false | false | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.ADIdentity.Sdk.AccountOperationDetailedSummary  
Add-AcctADAccount 返回包含以下参数的对象；  
SuccessfulAccountsCount <int>  
成功添加的帐户数。  
FailedAccountsCount <int>  
未添加的帐户数。  
FailedAccounts <Citrix.ADIdentity.Sdk.AccountError[]>  
未能添加的帐户列表。 每个都有以下参数；  
ADAccountName <string>  
ADAccountSid <string>  
ErrorReason <string>  
这可以是下列其中之一  
IdentityDuplicateObjectExists  
已存在具有相同 SID 的标识。  
ADServiceDatabaseError  
尝试执行数据库操作时，服务发生错误。  
ADServiceDatabaseNotConfigured  
由于未配置用于服务的数据库，无法完成操作。  
ADServiceStatusInvalidDb  
尝试执行数据库操作时，服务发生错误 - 由于  
各种原因，无法与数据库通信。  
FailedToConnectToDomainController  
联系 Active Directory 失败。  
FailedToGetOrganizationUnitInAD  
无法访问 Active Directory 中的 OU。  
FailedToGetDefaultComputerContainerInAD  
无法访问 Active Directory 中的默认计算机容器。  
FailedToCreateComputerAccountInAD  
无法在 Active Directory 中创建计算机帐户。  
FailedToAccessComputerAccountInAD  
无法读取 Active Directory 中新建的计算机帐户。  
FailedToGetSidFromAD  
无法获取 Active Directory 中创建的帐户的 SID。  
FailedToSetSamAccountNameInAD  
无法为 Active Directory 中创建的帐户设置 SIM 帐户名称。  
FailedToSetUserAccountControlInAD  
无法为 Active Directory 中创建的帐户设置用户帐户控制器属性。  
FailedToSaveChangeInAD  
无法保存对 Active Directory 中创建的计算机帐户所做更改。  
FailedToSetPasswordInAD  
无法为 Active Directory 中创建的计算机帐户设置密码。  
FailedToEnableAccountInAD  
无法启用 Active Directory 中的新建计算机帐户。  
ComputerNameAlreadyInUseInAD  
计算机要创建的计算机名称已在 Active Directory 中使用。  
FailedToGetDistinguishedNameInAD  
无法获取 Active Directory 中创建的计算机帐户的标识名。  
FailedToSetDnsHostNameInAD  
无法为 Active Directory 中创建的计算机帐户设置 DNS 主机名属性。  
FailedToSetDisplayNameInAD  
无法为 Active Directory 中创建的计算机帐户设置 DisplayName 属性。  
FailedToWriteServicePrincipalNameInAD  
无法为 Active Directory 中创建的计算机帐户设置 ServicePrincipalName 属性。  
DiagnosticInformtion <exception>  
任何其他错误信息  
SuccessfulAccounts <Citrix.ADIdentity.Sdk.Identity[]>  
成功添加的帐户列表。 每个对象  
都提供标识的详细信息，并包含以下信息：  
ADAccountSID <string>  
标识的 SID。  
ADAccountName <string>  
标识的帐户名称。  
Domain <string>  
在其中创建了帐户的域名。  
State <string>  
AD 帐户的当前状态。 这可以是下列其中之一︰  
Error  
帐户在 AD 中处于已锁定或已禁用状态。  
Available  
帐户在 AD 中并可供其他 Machine Creation Services 使用。  
InUse  
帐户在 AD 中并正在被其他 Machine Creation Services 使用。  
Tainted  
帐户在 AD 中并不再被其他 Machine Creation Services 使用。 但不再知道其密码，因此在没有“修复”帐户的情况下，无法重用。 请参阅 repair-AcctADAccount 了解详细信息。  
Lock <boolean>  
指示标识池是否处于锁定状态。

## 注意 如果失败，会发生以下错误。  
错误代码  
\---\---\-----  
NamingSchemeNotSpecifiedForIdentityPool  
指定的标识池中没有定义命名方案。  
IdentityPoolObjectNotFound  
未找到指定的标识池。  
IdentityPoolAlreadyLocked  
指定的标识池处于锁定状态。  
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

    c:\PS>New-AcctADAccount -IdentityPoolName MyPool -Count 2 -OutVariable result
    
              SuccessfulAccounts                SuccessfulAccountsCount       FailedAccountsCount    FailedAccounts
              ------------------                -----------------------       -------------------    --------------
              {MyDomain\ACC001, MyDomain\ACC002} 2                            0                      {}
    
              $result[0].SuccessfulAccounts
    
              ADAccountSid  : S-1-5-21-1315084875-1285793635-2418178940-2684
              ADAccountName : MyDomain\ACC001
              Domain        : MyDomain.com
              State         : Available
              Lock          : False
    
              ADAccountSid  : S-1-5-21-1315084875-1285793635-2418178940-2685
              ADAccountName : MyDomain\ACC002
              Domain        : MyDomain.com
              State         : Available
              Lock          : False
    

说明  
\---\---\-----  
在名为“MyPool”的标识池中创建两个新 AD 帐户并注册它们。

### EXAMPLE 2

    c:\PS>New-AcctADAccount -IdentityPoolName MyPool -Count 2 -StartCount 50 -OutVariable result
    
              SuccessfulAccounts                SuccessfulAccountsCount       FailedAccountsCount    FailedAccounts
              ------------------                -----------------------       -------------------    --------------
              {MyDomain\ACC050, MyDomain\ACC051} 2                            0                      {}
    
              $result[0].SuccessfulAccounts
    
              ADAccountSid  : S-1-5-21-1315084875-1285793635-2418178940-2686
              ADAccountName : MyDomain\ACC050
              Domain        : MyDomain.com
              State         : Available
              Lock          : False
    
              ADAccountSid  : S-1-5-21-1315084875-1285793635-2418178940-2687
              ADAccountName : MyDomain\ACC051
              Domain        : MyDomain.com
              State         : Available
              Lock          : False
    

说明  
\---\---\-----  
在名为“MyPool”的标识池中从索引 50 开始创建两个新 AD 帐户并注册它们。