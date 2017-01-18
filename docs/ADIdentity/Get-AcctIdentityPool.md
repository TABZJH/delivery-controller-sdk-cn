# Get-AcctIdentityPool

获取现有标识池。

## 语法

    Get-AcctIdentityPool [[-IdentityPoolName] <String>] [-IdentityPoolUid <Guid>] [-Lock <Boolean>] [-ScopeId <Guid>] [-ScopeName <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

用于查找现有标识池。

## 相关命令

- [New-AcctIdentityPool](New-AcctIdentityPool.html)
- [Remove-AcctIdentityPool](Remove-AcctIdentityPool.html)
- [Rename-AcctIdentityPool](Rename-AcctIdentityPool.html)
- [Set-AcctIdentityPool](Set-AcctIdentityPool.html)

## 参数

| 名称                     | 说明                                                        | 是否必需？ | 管道输入  | 默认值                                   |
| ---------------------- | --------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| IdentityPoolName       | 标识池的名称。                                                   | false | false |                                       |
| IdentityPoolUid        | 标识池的唯一标识符。                                                | false | false |                                       |
| Lock                   | 标识池是否处于锁定状态。                                              | false | false |                                       |
| ScopeId                | 仅获取作用域匹配指定作用域标识符的结果。                                      | false | false |                                       |
| ScopeName              | 仅获取作用域匹配指定作用域名称的结果。                                       | false | false |                                       |
| ReturnTotalRecordCount | 请参阅 about_Acct_Filtering 了解详细信息。                        | false | false | false                                 |
| MaxRecordCount         | 请参阅 about_Acct_Filtering 了解详细信息。                        | false | false | 250                                   |
| Skip                   | 请参阅 about_Acct_Filtering 了解详细信息。                        | false | false |                                       |
| SortBy                 | 请参阅 about_Acct_Filtering 了解详细信息。                        | false | false |                                       |
| Filter                 | 请参阅 about_Acct_Filtering 了解详细信息。                        | false | false |                                       |
| AdminAddress           | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

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
标识池的命名方案类型。 这可以是下列其中之一：  
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

    C:\PS>Get-AcctIdentityPool
    
    IdentityPoolName : MyPool
    IdentityPoolUid  : 22072d9e-6a8f-494b-a5bc-2ef18ca4b915
    NamingScheme     : Acc####
    NamingSchemeType : Numeric
    StartCount       : 1
    OU               :
    Domain           : mydomain.com
    Lock             : True
    
    IdentityPoolName : MyPool2
    IdentityPoolUid  : 03743136-e43b-4a87-af74-ab71686b3c16
    NamingScheme     : Test####
    NamingSchemeType : Alphabetic
    StartCount       : 1
    OU               :
    Domain           : mydomain.com
    Lock             : False
    

说明  
\---\---\-----  
获取所有标识池。

### 示例 2

    C:\PS>Get-AcctIdentityPool -IdentityPoolName M*
    
    IdentityPoolName : MyPool
    IdentityPoolUid  : 22072d9e-6a8f-494b-a5bc-2ef18ca4b915
    NamingScheme     : Acc####
    NamingSchemeType : Numeric
    StartCount       : 1
    OU               :
    Domain           : mydomain.com
    Lock             : True
    

说明  
\---\---\-----  
获取以字符“M”开头的所有标识池。