# Add-AppLibAppDiskScope

将指定的 AppDisk 添加到给定作用域。

## 语法

    Add-AppLibAppDiskScope [-Scope] <String[]> -InputObject <AppDisk[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Add-AppLibAppDiskScope [-Scope] <String[]> -AppDiskUid <Guid[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Add-AppLibAppDiskScope [-Scope] <String[]> -AppDiskName <String[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Add-AppLibAppDiskScope 命令用于将一个或多个 AppDisk 对象与给定作用域关联。

此 cmdlet 有多个参数集，允许您以不同方式标识 AppDisk 对象： - 可以在 InputObject 参数中通过管道传送 AppDisk 对象或由 InputObject 参数指定 AppDisk 对象 - AppDiskUid 参数按 AppDiskUid 指定对象 - AppDiskName 参数按 AppDiskName 指定对象（支持通配符）

要将 AppDisk 添加到作用域，您需要更改 AppDisk 作用域的权限以及将对象添加到您指定的所有作用域的权限。

如果 AppDisk 已在一个作用域中，将默认忽略该作用域。

## 相关命令

- [Remove-AppLibAppDiskScope](Remove-AppLibAppDiskScope.html)
- [Get-AppLibScopedObject](Get-AppLibScopedObject.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                           | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ------------------------------ | ------------------------------------- |
| Scope        | 指定要将对象添加到作用域。                                                                                                                                                          | true  | false                          |                                       |
| InputObject  | 指定要添加的 AppDisk 对象。                                                                                                                                                     | true  | true (ByValue, ByPropertyName) |                                       |
| AppDiskUid   | 指定要通过 AppDiskUid 添加的 AppDisk 对象。                                                                                                                                       | true  | true (ByValue, ByPropertyName) |                                       |
| AppDiskName  | 指定要通过 AppDiskName 添加的 AppDisk 对象。                                                                                                                                      | true  | true (ByValue, ByPropertyName) |                                       |
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

    c:\PS>Add-AppLibAppDiskScope Finance -AppDiskUid 6702C5D0-C073-4080-A0EE-EC74CB537C52
    

说明  
\---\---\-----  
将单个 AppDisk 添加到“Finance”作用域。

### 示例 2

    c:\PS>Add-AppLibAppDiskScope Finance,Marketing -AppDiskUid 6702C5D0-C073-4080-A0EE-EC74CB537C52
    

说明  
\---\---\-----  
将单个 AppDisk 添加到多个作用域。

### 示例 3

    c:\PS>Get-AppLibAppDisk | Add-AppLibAppDiskScope Finance
    

说明  
\---\---\-----  
将所有可见 AppDisk 对象添加到“Finance”作用域。

### 示例 4

    c:\PS>Add-AppLibAppDiskScope Finance -AppDiskName A*
    

说明  
\---\---\-----  
将名称以“A”开头的 AppDisk 对象添加到“Finance”作用域。