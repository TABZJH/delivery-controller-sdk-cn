# Remove-AppLibAppVPackage

Removes an App-V package from the library that is holding it

## 语法

    Remove-AppLibAppVPackage [-Uid] <Int32> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Provides the ability to remove an App-V package from the library that is holding it.

Removing a package from a library does not remove the whole reference to the package from the library, but rather marks it as not existing. Re-adding the package later will restore the reference. This cmdlet should only be used for removing packages from the manual library.

## 相关命令

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                           | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ------------------------------ | ------------------------------------- |
| UID          | The App Library's internal unique identifier of the App-V package.                                                                                                     | true  | true (ByValue, ByPropertyName) |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                          |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 无

## Notes If the command fails, the following errors can result.  
Error Codes  
\---\---\-----  
UnknownObject  
No desktop group was found for the given uid. DatabaseError  
An error occurred in the service while attempting a database operation. DatabaseNotConfigured  
The operation could not be completed because the database for the service is not configured. DataStoreException  
An error occurred in the service while attempting a database operation - communication with the database failed for various reasons. PermissionDenied  
You do not have permission to execute this command. AuthorizationError  
There was a problem communicating with the Citrix Delegated Administration Service. CommunicationError  
There was a problem communicating with the remote service. ExceptionThrown  
An unexpected error occurred. 有关更多详细信息，请参阅控制器上的 Windows 事件日志或 XenDesktop 日志。

## 示例

### 示例 1

    Remove-AppLibAppVPackage -Uid 5
    

Description  
\---\---\-----  
Removes the specified package from the library that holds it by marking it as non- existing.