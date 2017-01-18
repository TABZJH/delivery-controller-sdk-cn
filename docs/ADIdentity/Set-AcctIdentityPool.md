# Set-AcctIdentityPool

更新标识池的参数。

## 语法

    Set-AcctIdentityPool [-IdentityPoolName] <String> [-NamingScheme <String>] [-NamingSchemeType <ADIdentityNamingScheme>] [-OU <String>] [-Domain <String>] [-AllowUnicode] [-PassThru] [-StartCount <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-AcctIdentityPool -IdentityPoolUid <Guid> [-NamingScheme <String>] [-NamingSchemeType <ADIdentityNamingScheme>] [-OU <String>] [-Domain <String>] [-AllowUnicode] [-PassThru] [-StartCount <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

用于修改标识池的参数。

注意︰更改命名方案或命名方案类型时，索引不会重置为 0；它继续保留以避免 AD 帐户名称与现有帐户冲突。 如果需要，请在创建更多帐户时使用 New-AcctAdAccount 命令更改索引。

## 相关命令

- [New-AcctIdentityPool](New-AcctIdentityPool.html)
- [Get-AcctIdentityPool](Get-AcctIdentityPool.html)
- [Remove-AcctIdentityPool](Remove-AcctIdentityPool.html)

## 参数

| 名称               | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| IdentityPoolName | 要修改的标识池名称。                                                                                                                                                             | true  | true (ByPropertyName) |                                       |
| IdentityPoolUid  | 要更新的标识池的唯一标识符。                                                                                                                                                         | true  | false                 |                                       |
| NamingScheme     | 要用于标识池的新命名方案。                                                                                                                                                          | false | false                 |                                       |
| NamingSchemeType | 要用于标识池的新命名方案类型。可以是 Numeric 或 Alphabetic。                                                                                                                               | false | false                 |                                       |
| OU               | 要用于标识池的新 OU。 设置此项后创建的所有帐户都创建在此 AD 容器中。 这不会移动任何现有帐户。 OU 必须是有效的 AD 容器，并且属于为池指定的域。                                                                                        | false | false                 |                                       |
| Domain           | 要用于标识池的新 Active Directory 域。 所有新帐户都将创建在此域中，但这不会影响任何现有帐户。 可以采用长形式或短形式（即 domain 或 domain.com）指定域。                                                                        | false | false                 |                                       |
| AllowUnicode     | 更新命名方案中允许的字符的定义。                                                                                                                                                       | false | false                 |                                       |
| PassThru         | 定义命令是否返回标识池的新状态。                                                                                                                                                       | false | false                 | false                                 |
| StartCount       | 下一个创建操作的起始索引                                                                                                                                                           | false | false                 |                                       |
| LoggingId        | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress     | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                              | false | false                 | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.ADIdentity.Sdk.IdentityPool  
此对象提供标识池的详细信息，并包含以下信息︰  
IdentityPoolName <string>  
标识池的名称。  
IdentityPoolUid <guid>  
标识池的唯一标识符。  
NamingScheme <string>  
标识池的命名方案。  
NamingSchemeType <Citrix.XDInterServiceTypes.ADIdentityNamingScheme>  
标识池的命名方案类型。 这可以是下列其中之一︰  
Numeric - 命名方案使用数字索引  
Alphabetic - 命名方案使用字母索引  
StartCount <int>  
从标识池创建标识时要使用的下一个索引。  
OU <string>  
将在其中创建从此标识池创建的帐户的 OU 的 Active Directory 标识名。  
Domain <string>  
池中帐户所属的 Active Directory 域。  
Lock <boolean>  
指示标识池是否处于锁定状态。

## 注意 如果失败，会发生以下错误。  
错误代码  
\---\---\-----  
InvalidIdentityPoolParameterCombination  
由以下任何一个验证错误导致：  
* 如果指定了 OU，则还必须指定域。  
* 如果指定了 NamingScheme、NamingSchemeType 和 Domain 其中任何一个，它们必须全部存在。  
NamingSchemeIllegalComputerName  
提供的命名方案无效。  
UnableToConvertDomainName  
无法将域名转换为 DNS 格式。  
NamingSchemeNotEnoughCharacters  
命名方案没有指定足够的字符。  
NamingSchemeTooManyCharacters  
命名方案指定了太多的字符。  
NamingSchemeIllegalCharacter  
命名方案包含非法字符。  
NamingSchemeMayNotStartWithPeriod  
命名方案以句点 (.) 字符开头。  
NamingSchemeMayNotBeAllNumbers  
命名方案仅包含数字。  
NamingSchemeMissingNumericSpecifications  
命名方案未包含任何可变指定内容（即，没有指定“#”字符）。  
NamingSchemeHasMoreThanOneSetOfHashes  
命名方案有多个可变区（即，“#”字符被其他字符分隔开）。  
IdentityPoolDuplicateObjectExists  
已存在具有相同名称的标识池。  
IdentityPoolObjectNotFound  
找不到要修改的标识池。  
IdentityPoolOUInvalid  
标识池 OU 无效，因为它不存在。  
IdentityPoolOUOfWrongDomain  
标识池 OU 无效，因为它引用了不是为池指定的域。  
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

    C:\PS>Set-AcctIdentityPool -IdentityPoolName poolName -StartCount 100 -NamingScheme AC####
    

说明  
\---\---\-----  
更改起始计数和命名方案，以便生成的下一个帐户是 AC0100（假设帐户尚不存在）