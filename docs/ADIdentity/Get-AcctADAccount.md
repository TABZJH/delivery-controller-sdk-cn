# Get-AcctADAccount

获取 AD Identity Service 中存储的 AD 帐户。

## 语法

    Get-AcctADAccount [-IdentityPoolName <String>] [-ADAccountSid <String>] [-Domain <String>] [-State <ADIdentityState>] [-Lock <Boolean>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
    
    Get-AcctADAccount [-IdentityPoolUid <Guid>] [-ADAccountSid <String>] [-Domain <String>] [-State <ADIdentityState>] [-Lock <Boolean>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

用于查找 AD Identity Service 中存储的 AD 帐户及查看帐户状态。

## 相关命令

- [New-AcctADAccount](New-AcctADAccount.html)
- [Add-AcctADAccount](Add-AcctADAccount.html)
- [Remove-AcctADAccount](Remove-AcctADAccount.html)
- [Unlock-AcctADAccount](Unlock-AcctADAccount.html)
- [Update-AcctADAccount](Update-AcctADAccount.html)
- [Repair-AcctADAccount](Repair-AcctADAccount.html)

## 参数

| 名称                     | 说明                                                        | 是否必需？ | 管道输入                  | 默认值                                   |
| ---------------------- | --------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| ADAccountSid           | 帐户的 AD 帐户 SID。                                            | false | false                 |                                       |
| Domain                 | 帐户的域（这采用 dns 格式）。                                         | false | false                 |                                       |
| State                  | AD Identity Service 中存储的 AD 帐户标识的当前状态。                    | false | false                 |                                       |
| Lock                   | 指示帐户在 AD Identity Service 中是否处于锁定状态。                      | false | false                 |                                       |
| ReturnTotalRecordCount | 请参阅 about_Acct_Filtering 了解详细信息。                        | false | false                 | false                                 |
| MaxRecordCount         | 请参阅 about_Acct_Filtering 了解详细信息。                        | false | false                 | 250                                   |
| Skip                   | 请参阅 about_Acct_Filtering 了解详细信息。                        | false | false                 |                                       |
| SortBy                 | 请参阅 about_Acct_Filtering 了解详细信息。                        | false | false                 |                                       |
| Filter                 | 请参阅 about_Acct_Filtering 了解详细信息。                        | false | false                 |                                       |
| AdminAddress           | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false                 | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |
| IdentityPoolName       | 帐户注册到的标识池的名称。                                             | false | true (ByPropertyName) |                                       |
| IdentityPoolUid        | 帐户注册到的标识池的唯一标识符。                                          | false | false                 |                                       |

## 输入类型

### 

## 返回值

### Citrix.ADIdentity.Sdk.IdentityInPool  
Get-AcctADAccount 返回包含以下参数的对象  
ADAccountSid <string>  
检索的帐户的 AD 帐户 SID。  
ADAccountName <string>  
检索的帐户的 AD 帐户名称。  
Domain <string>  
导入帐户的域。  
State <Citrix.XDInterServiceTypes.ADIdentityState>  
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
IdentityPoolName <System.String>  
包含标识池的名称。  
IdentityPoolUid <System.Guid>  
标识包含标识池的 GUID。

## 注意 如果失败，会发生以下错误。  
错误代码  
\---\---\-----  
PartialData  
仅返回了一部分可用数据。  
CouldNotQueryDatabase  
未定义获取数据库所需的查询。  
PermissionDenied  
用户没有执行此操作的管理权限。  
ConfigurationLoggingError  
由于配置日志记录错误，无法执行操作  
CommunicationError  
与服务通信时发生错误。  
DatabaseNotConfigured  
由于未配置用于服务的数据库，无法完成操作。  
InvalidFilter  
无法为此 cmdlet 解释提供的过滤表达式。  
ExceptionThrown  
发生意外错误。 要查找更多详细信息，请参阅使用的控制器上的 Windows 事件日志，或检查 XenDesktop 日志。

## 示例

### 示例 1

    C:\>Get-AcctADAccount
    

说明  
\---\---\-----  
返回已在 AD Identity Service 中注册的所有 AD 帐户。

### 示例 2

    C:\>Get-AcctADAccount -IdentityPoolName MyPool -Lock $false
    

说明  
\---\---\-----  
返回已在 AD Identity Service 中注册、位于名为“MyPool”的标识池中且还被锁定的所有 AD 帐户。

### EXAMPLE 3

    C:\>Get-AcctADAccount -Filter {IdentityPoolName -Like "p*" -or IdentityPoolName -eq "MyPool"}
    

说明  
\---\---\-----  
返回已在 AD Identity Service 中注册、位于名为“MyPool”的标识池中或位于名称以“p”开头的标识池中的所有 AD 帐户。 有关此命令的高级过滤方面的完整详细信息，请参阅 about_Acct_Filtering。