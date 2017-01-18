# Copy-AcctIdentityPool

将标识池及其关联标识复制到新 IdentityPool

## 语法

    Copy-AcctIdentityPool [-IdentityPoolName] <String> [-NewIdentityPoolName] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Copy-AcctIdentityPool -IdentityPoolUid <Guid> [-NewIdentityPoolName] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

用于复制 IdentityPool。

新 IdentityPool 将包含原始池中的所有帐户，并且将设置相同的域和 OU。命名方案将被取消设置，StartCount 将设置为 1。

## 相关命令

- [New-AcctIdentityPool](New-AcctIdentityPool.html)
- [Get-AcctIdentityPool](Get-AcctIdentityPool.html)
- [Remove-AcctIdentityPool](Remove-AcctIdentityPool.html)

## 参数

| 名称                  | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| IdentityPoolName    | 要复制的标识池的名称。                                                                                                                                                            | true  | true (ByPropertyName) |                                       |
| IdentityPoolUid     | 要复制的标识池的唯一标识符。                                                                                                                                                         | true  | false                 |                                       |
| NewIdentityPoolName | 新 IdentityPool 的名称。                                                                                                                                                    | true  | false                 |                                       |
| LoggingId           | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress        | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

## 返回值

### Citrix.ADIdentity.Sdk.IdentityPool  


此对象提供新标识池的详细信息，并包含以下信息︰  
IdentityPoolName <string>  
标识池的名称。  
IdentityPoolUid <guid>  
标识池的唯一标识符。  
NamingScheme <string>  
标识池的命名方案。  
NamingSchemeType <Citrix.XDInterServiceTypes.ADIdentityNamingScheme>  
标识池的命名方案类型。这可以是下列其中之一︰  
Numeric - 命名方案使用数字索引  
Alphabetic - 命名方案使用字母索引  
StartCount <int>  
从标识池创建标识时要使用的下一个索引。  
OU <string>  
将在其中创建从此标识池创建的帐户的 OU 的 Active Directory 标识名。  
Domain <string>  
池中帐户所属的 Active Directory 域。  
Lock <boolean>  
指示标识池是否处于锁定状态。 ## 注意 如果失败，会发生以下错误。  
错误代码  
\---\---\-----  
IdentityPoolDuplicateObjectExists  
已存在具有相同名称的标识池。  
IdentityPoolObjectNotFound  
找不到要修改的标识池。  
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
发生意外错误。要查找更多详细信息，请参阅使用的控制器上的 Windows 事件日志，或检查 XenDesktop 日志。

## 示例

### 示例 1

    <br />

说明  
\---\---\-----