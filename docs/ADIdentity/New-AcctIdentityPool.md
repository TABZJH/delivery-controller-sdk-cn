# New-AcctIdentityPool

创建新标识池。

## 语法

    New-AcctIdentityPool -IdentityPoolName <String> [-NamingScheme <String>] [-NamingSchemeType <ADIdentityNamingScheme>] [-OU <String>] [-Domain <String>] [-AllowUnicode] [-StartCount <Int32>] [-Scope <String[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

用于创建可用于存储 AD 计算机帐户的标识池。

如果标识池要用于创建新帐户，必须指定命名方案、命名方案类型和域。

每个标识池都关联到单个域。 标识池中的所有标识都属于同一个域。 如果没有通过参数在此命令中指定域，则将在向其导入帐户时设置域。

## 相关命令

- [Remove-AcctIdentityPool](Remove-AcctIdentityPool.html)
- [Rename-AcctIdentityPool](Rename-AcctIdentityPool.html)
- [Set-AcctIdentityPool](Set-AcctIdentityPool.html)
- [Test-AcctIdentityPoolNameAvailable](Test-AcctIdentityPoolNameAvailable.html)
- [New-AcctADAccount](New-AcctADAccount.html)

## 参数

| 名称               | 说明                                                                                                                                                                                                                                                                                                                                          | 是否必需？                                                                                                                                                                                                                  | 管道输入  | 默认值                                   |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ------------------------------------- |
| IdentityPoolName | 标识池的名称。不得包含以下任意字符：\ /;: #*？ = <>                                                                                                                                                                                                                                                                                                           | []()""'                                                                                                                                                                                                                | true  | false |                               |
| NamingScheme     | 定义标识池中创建的 AD 帐户的模板名称。 方案可以包含固定字符和由“#”字符定义的可变部分。 只能定义一个可变区。 “#”字符数定义可变区的最小长度。 例如，命名方案 H#### 可以创建名为 H0001、H0002（对于数字方案类型）或 HAAAA、HAAAB（对于字母类型）的帐户。  
Citrix 建议定义不会与 AD 中已有的帐户冲突的命名方案；如果发生冲突，帐户创建将失败。  
有效计算机名称的组成存在限制：最小名称长度：2 (DNS) 最大名称长度：15 字节 (NetBIOS) 计算机名称中不允许有以下字符：反斜线 (\) 斜线标记 (/) 冒号 (:) 星号 (*) 问号 (?) 引号 (") 小于号 (<) 大于号 (>) 竖线 ( | ) 逗号 (,) 波浪线 (~) 感叹号 (!) 电子邮件符号 (@) 数字符号 (#) 美元符号 ($) 百分号 (%) 补注号 (^) 和号 (&) 单引号 (') 圆括号 (()) 大括号 ({}) 下划线 (_) 以下名称已保留，不得在命名方案结尾处使用：-GATEWAY -GW -TAC 名称不得以句点开头 (NetBIOS)。 名称不得完全由数字组成 (NetBIOS)。 名称不得包含空白或空格字符 (DNS)。 | false | false |                               |
| NamingSchemeType | 命名方案的类型。这可以是 Numeric 或 Alphabetic。此项定义将创建的 AD 帐户名称的可变部分的格式。                                                                                                                                                                                                                                                                                 | false                                                                                                                                                                                                                  | false | Numeric                               |
| OU               | 将在其中创建计算机帐户的 OU。 如果未指定，则在 AD 指定的默认帐户容器中创建帐户。 这是开箱即用的 AD 安装的 “计算机”容器。 OU 必须是有效的 AD 容器，并且属于为池指定的域；                                                                                                                                                                                                                                            | false                                                                                                                                                                                                                  | false |                                       |
| Domain           | 池的 AD 域名。以 FQDN 格式指定此项；例如 MyDomain.com。                                                                                                                                                                                                                                                                                                     | false                                                                                                                                                                                                                  | false |                                       |
| AllowUnicode     | 允许命名方案有非字母数字字符。                                                                                                                                                                                                                                                                                                                             | false                                                                                                                                                                                                                  | false |                                       |
| StartCount       | 定义如果为标识池创建新 AD 帐户，将使用的下一个数字。                                                                                                                                                                                                                                                                                                                | false                                                                                                                                                                                                                  | false |                                       |
| Scope            | 要应用于新标识池的管理作用域。                                                                                                                                                                                                                                                                                                                             | false                                                                                                                                                                                                                  | false |                                       |
| LoggingId        | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                                      | false                                                                                                                                                                                                                  | false |                                       |
| AdminAddress     | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                                                                                                                                                                                   | false                                                                                                                                                                                                                  | false | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

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
IdentityPoolOUInvalid  
标识池 OU 无效，因为它不存在。   
IdentityPoolOUOfWrongDomain  
标识池 OU 无效，因为它引用了不是为池指定的域。  
InvalidIdentityPoolParameterCombination  
由以下任何一个验证错误导致：  
* 如果指定了 OU，则还必须指定域。  
* 如果指定了 NamingScheme、NamingSchemeType 和 Domain 其中任何一个，它们必须全部存在。  
NamingSchemeIllegalComputerName  
提供的命名方案无效。  
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

    c:\PS>New-AcctIdentityPool -IdentityPoolName MyPool -NamingScheme Acc#### -Domain MyDomain.com -NamingSchemeType Numeric
    
    
    IdentityPoolName : MyPool
    IdentityPoolUid  : 22072d9e-6a8f-494b-a5bc-2ef18ca4b915
    NamingScheme     : Acc####
    NamingSchemeType : Numeric
    StartCount       : 1
    OU               :
    Domain           : MyDomain.com
    Lock             : False
    

说明  
\---\---\-----  
在名为“MyDomain.com” 的域中，使用格式为 Acc#### 的数字方案，创建可以从其创建帐户的新标识池。 将根据此标识池定义创建的第一个帐户是 Acc0001。  
新 AD 帐户都可以导入该池，但必须从域“MyDomain.com”导入。