# Remove-ProvSchemeScope

Remove the specified ProvisioningScheme(s) from the given scope(s).

## 语法

    Remove-ProvSchemeScope [-Scope] <String[]> -InputObject <ProvisioningScheme[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-ProvSchemeScope [-Scope] <String[]> -ProvisioningSchemeUid <Guid[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-ProvSchemeScope [-Scope] <String[]> -ProvisioningSchemeName <String[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Remove-ProvSchemeScope command is used to remove one or more ProvisioningScheme objects from the given scope(s).

There are multiple parameter sets for this cmdlet, allowing you to identify the ProvisioningScheme objects in different ways: - ProvisioningScheme objects can be piped in or specified by the InputObject parameter - The ProvisioningSchemeUid parameter specifies objects by ProvisioningSchemeUid - The ProvisioningSchemeName parameter specifies objects by ProvisioningSchemeName (supports wildcards)

To remove a ProvisioningScheme from a scope you need permission to change the scopes of the ProvisioningScheme.

If the ProvisioningScheme is not in a specified scope, that scope will be silently ignored.

## 相关命令

- [Add-ProvSchemeScope](Add-ProvSchemeScope.html)
- [Get-ProvScopedObject](Get-ProvScopedObject.html)

## 参数

| 名称                     | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                           | 默认值                                   |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ------------------------------ | ------------------------------------- |
| 作用域                    | 指定要从其删除对象的作用域。                                                                                                                                                         | true  | false                          |                                       |
| InputObject            | Specifies the ProvisioningScheme objects to be removed.                                                                                                                | true  | true (ByValue, ByPropertyName) |                                       |
| ProvisioningSchemeUid  | Specifies the ProvisioningScheme objects to be removed by ProvisioningSchemeUid.                                                                                       | true  | true (ByValue, ByPropertyName) |                                       |
| ProvisioningSchemeName | Specifies the ProvisioningScheme objects to be removed by ProvisioningSchemeName.                                                                                      | true  | true (ByValue, ByPropertyName) |                                       |
| LoggingId              | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                          |                                       |
| AdminAddress           | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

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

    c:\PS>Remove-ProvSchemeScope Finance -ProvisioningSchemeUid 6702C5D0-C073-4080-A0EE-EC74CB537C52
    

Description  
\---\---\-----  
Removes a single ProvisioningScheme from the 'Finance' scope.

### 示例 2

    c:\PS>Remove-ProvSchemeScope Finance,Marketing -ProvisioningSchemeUid 6702C5D0-C073-4080-A0EE-EC74CB537C52
    

Description  
\---\---\-----  
Removes a single ProvisioningScheme from multiple scopes.

### 示例 3

    c:\PS>Get-ProvScheme | Remove-ProvSchemeScope Finance
    

Description  
\---\---\-----  
Removes all visible ProvisioningScheme objects from the 'Finance' scope.

### 示例 4

    c:\PS>Remove-ProvSchemeScope Finance -ProvisioningSchemeName A*
    

Description  
\---\---\-----  
Removes ProvisioningScheme objects with a name starting with an 'A' from the 'Finance' scope.