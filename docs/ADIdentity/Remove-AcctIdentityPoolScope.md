# Remove-AcctIdentityPoolScope

从给定作用域中删除指定的 IdentityPool。

## 语法

    Remove-AcctIdentityPoolScope [-Scope] <String[]> -InputObject <IdentityPool[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-AcctIdentityPoolScope [-Scope] <String[]> -IdentityPoolUid <Guid[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-AcctIdentityPoolScope [-Scope] <String[]> -IdentityPoolName <String[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Remove-AcctIdentityPoolScope 命令用于从给定作用域中删除一个或多个 IdentityPool 对象。

此 cmdlet 有多个参数集，允许您以不同方式标识 IdentityPool 对象： - 可以在 InputObject 参数中通过管道传送 IdentityPool 对象或由 InputObject 参数指定 IdentityPool 对象 - IdentityPoolUid 参数按 IdentityPoolUid 指定对象 - IdentityPoolName 参数按 IdentityPoolName 指定对象（支持通配符）

要从作用域中删除 IdentityPool，您需要更改 IdentityPool 作用域的权限。

如果 IdentityPool 不在指定的作用域中，将默认忽略该作用域。

## 相关命令

- [Add-AcctIdentityPoolScope](Add-AcctIdentityPoolScope.html)
- [Get-AcctScopedObject](Get-AcctScopedObject.html)

## 参数

| 名称               | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                           | 默认值                                   |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ------------------------------ | ------------------------------------- |
| Scope            | 指定要从其删除对象的作用域。                                                                                                                                                         | true  | false                          |                                       |
| InputObject      | 指定要删除的 IdentityPool 对象。                                                                                                                                                | true  | true (ByValue, ByPropertyName) |                                       |
| IdentityPoolUid  | 指定要按 IdentityPoolUid 删除的 IdentityPool 对象。                                                                                                                              | true  | true (ByValue, ByPropertyName) |                                       |
| IdentityPoolName | 指定要按 IdentityPoolName 删除的 IdentityPool 对象。                                                                                                                             | true  | true (ByValue, ByPropertyName) |                                       |
| LoggingId        | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                          |                                       |
| AdminAddress     | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 无

## 注意 如果命令失败，会返回以下错误。  
错误代码  
\---\---\-----  
UnknownObject  
未找到其中一个指定的对象。  
ScopeNotFound  
未找到其中一个指定的作用域。  
DatabaseError  
尝试执行数据库操作时，服务发生错误。  
DatabaseNotConfigured  
由于未配置用于服务的数据库，无法完成操作。  
DataStoreException  
尝试执行数据库操作时，服务发生错误 - 由于各种原因，无法与数据库通信。  
PermissionDenied  
您没有权限使用指定对象或作用域执行此命令。  
AuthorizationError  
与 Citrix Delegated Administration Service 通信时出现问题。  
ConfigurationLoggingError  
由于配置日志记录错误，无法执行操作。  
CommunicationError  
与远程服务通信时出现问题。  
ExceptionThrown  
发生意外错误。 有关更多详细信息，请参阅控制器上的 Windows 事件日志或 XenDesktop 日志。

## 示例

### 示例 1

    c:\PS>Remove-AcctIdentityPoolScope Finance -IdentityPoolUid 6702C5D0-C073-4080-A0EE-EC74CB537C52
    

说明  
\---\---\-----  
从“Finance”作用域中删除单个 IdentityPool。

### 示例 2

    c:\PS>Remove-AcctIdentityPoolScope Finance,Marketing -IdentityPoolUid 6702C5D0-C073-4080-A0EE-EC74CB537C52
    

说明  
\---\---\-----  
从多个作用域中删除单个 IdentityPool。

### 示例 3

    c:\PS>Get-AcctIdentityPool | Remove-AcctIdentityPoolScope Finance
    

说明  
\---\---\-----  
从“Finance”作用域中删除所有可见 IdentityPool 对象。

### 示例 4

    c:\PS>Remove-AcctIdentityPoolScope Finance -IdentityPoolName A*
    

说明  
\---\---\-----  
从“Finance”作用域中删除名称以“A”开头的 IdentityPool 对象。