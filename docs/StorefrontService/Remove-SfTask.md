# Remove-SfTask

Removes from the database completed tasks for the Storefront Service.

## 语法

    Remove-SfTask [-TaskId] <Guid> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Enables completed tasks that have run within the Storefront Service to be removed from the database.

## 相关命令

- [Get-SfTask](Get-SfTask.html)
- [Add-SfTaskMetadata](Add-SfTaskMetadata.html)
- [Remove-SfTaskMetadata](Remove-SfTaskMetadata.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| TaskId       | Specifies the identifier for the task to be removed.                                                                                                                   | true  | true (ByPropertyName) |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### System.Management.Automation.PSObject

Objects containing the TaskId parameter can be piped to the Remove-SfTask command.

## 返回值

### 

## Notes If the command fails, the following errors can be returned.  
Error Codes  
\---\---\-----  
DatabaseError  
An error occurred in the service while attempting a database operation.  
DatabaseNotConfigured  
The operation could not be completed because the database for the service is not configured.  
ServiceStatusInvalidDb  
An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.  
PermissionDenied  
You do not have permission to execute this command.  
AuthorizationError  
There was a problem communicating with the Citrix Delegated Administration service.  
OperationDeniedByConfigurationLoggingError  
The operation could not be performed because of a configuration logging error.  
CommunicationError  
There was a problem communicating with the remote service.  
ExceptionThrown  
An unexpected error occurred. 有关更多详细信息，请参阅控制器上的 Windows 事件日志或 XenDesktop 日志。

## 示例

### 示例 1

    <br />

说明  
\---\---\-----