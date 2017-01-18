# Remove-AppLibAppDiskScope

Remove the specified AppDisk(s) from the given scope(s).

## 语法

    Remove-AppLibAppDiskScope [-Scope] <String[]> -InputObject <AppDisk[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-AppLibAppDiskScope [-Scope] <String[]> -AppDiskUid <Guid[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-AppLibAppDiskScope [-Scope] <String[]> -AppDiskName <String[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

The Remove-AppLibAppDiskScope command is used to remove one or more AppDisk objects from the given scope(s).

此 cmdlet 有多个参数集，允许您以不同方式标识 AppDisk 对象： - 可以在 InputObject 参数中通过管道传送 AppDisk 对象或由 InputObject 参数指定 AppDisk 对象 - AppDiskUid 参数按 AppDiskUid 指定对象 - AppDiskName 参数按 AppDiskName 指定对象（支持通配符）

To remove a AppDisk from a scope you need permission to change the scopes of the AppDisk.

If the AppDisk is not in a specified scope, that scope will be silently ignored.

## 相关命令

- [Add-AppLibAppDiskScope](Add-AppLibAppDiskScope.html)
- [Get-AppLibScopedObject](Get-AppLibScopedObject.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                           | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ------------------------------ | ------------------------------------- |
| 作用域          | 指定要从其删除对象的作用域。                                                                                                                                                         | true  | false                          |                                       |
| InputObject  | Specifies the AppDisk objects to be removed.                                                                                                                           | true  | true (ByValue, ByPropertyName) |                                       |
| AppDiskUid   | Specifies the AppDisk objects to be removed by AppDiskUid.                                                                                                             | true  | true (ByValue, ByPropertyName) |                                       |
| AppDiskName  | Specifies the AppDisk objects to be removed by AppDiskName.                                                                                                            | true  | true (ByValue, ByPropertyName) |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                          |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

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

    c:\PS>Remove-AppLibAppDiskScope Finance -AppDiskUid 6702C5D0-C073-4080-A0EE-EC74CB537C52
    

Description  
\---\---\-----  
Removes a single AppDisk from the 'Finance' scope.

### 示例 2

    c:\PS>Remove-AppLibAppDiskScope Finance,Marketing -AppDiskUid 6702C5D0-C073-4080-A0EE-EC74CB537C52
    

Description  
\---\---\-----  
Removes a single AppDisk from multiple scopes.

### 示例 3

    c:\PS>Get-AppLibAppDisk | Remove-AppLibAppDiskScope Finance
    

Description  
\---\---\-----  
Removes all visible AppDisk objects from the 'Finance' scope.

### 示例 4

    c:\PS>Remove-AppLibAppDiskScope Finance -AppDiskName A*
    

Description  
\---\---\-----  
Removes AppDisk objects with a name starting with an 'A' from the 'Finance' scope.