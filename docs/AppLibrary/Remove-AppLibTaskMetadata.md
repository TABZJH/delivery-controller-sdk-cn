# Remove-AppLibTaskMetadata

Removes metadata from the given Task.

## 语法

    Remove-AppLibTaskMetadata [-TaskId] <Guid> -Name <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-AppLibTaskMetadata [-TaskId] <Guid> -Map <PSObject> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-AppLibTaskMetadata [-InputObject] <Task[]> -Name <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-AppLibTaskMetadata [-InputObject] <Task[]> -Map <PSObject> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Provides the ability to remove metadata from the given Task.

## 相关命令

- [Add-AppLibTaskMetadata](Add-AppLibTaskMetadata.html)
- [Set-AppLibTaskMetadata](Set-AppLibTaskMetadata.html)
- [Get-AppLibTask](Get-AppLibTask.html)
- [Remove-AppLibTask](Remove-AppLibTask.html)
- [Stop-AppLibTask](Stop-AppLibTask.html)
- [Switch-AppLibTask](Switch-AppLibTask.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                           | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ------------------------------ | ------------------------------------- |
| TaskId       | 任务的 ID                                                                                                                                                                 | true  | true (ByValue, ByPropertyName) |                                       |
| InputObject  | 元数据要添加到的对象。                                                                                                                                                            | true  | true (ByValue)                 |                                       |
| 名称           | 要删除的元数据属性。                                                                                                                                                             | true  | false                          |                                       |
| Map          | 指定属性的（名称，值）对字典。 可以是哈希表（使用 @{"name1" = "val1"; "name2" = "val2"} 创建）或字符串字典（使用 new-object“System.Collections.Generic.Dictionary[String,String]”创建）。                      | true  | true (ByValue)                 |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                          |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 

## Notes If the command fails, the following errors can be returned.  
Error Codes  
\---\---\-----  
UnknownObject  
One of the specified objects was not found.  
DatabaseError  
An error occurred in the service while attempting a database operation.  
DatabaseNotConfigured  
The operation could not be completed because the database for the service is not configured.  
DataStoreException  
An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.  
PermissionDenied  
You do not have permission to execute this command.  
AuthorizationError  
There was a problem communicating with the Citrix Delegated Administration Service.  
ConfigurationLoggingError  
The operation could not be performed because of a configuration logging error.  
CommunicationError  
There was a problem communicating with the remote service.  
ExceptionThrown  
An unexpected error occurred. 有关更多详细信息，请参阅控制器上的 Windows 事件日志或 XenDesktop 日志。

## 示例

### 示例 1

    c:\PS>Get-AppLibTask | Remove-AppLibTaskMetadata
    

Description  
\---\---\-----  
Remove all metadata from all Task objects.