# Unlock-AppLibAppDisk

Unlocks an AppDisk.

## 语法

    Unlock-AppLibAppDisk [-AppDiskName] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Unlock-AppLibAppDisk -AppDiskUid <Guid> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Provides the ability to unlockan AppDisk that has the Id of a failed Task still associated with it. This allows another long-running task to operate on that scheme. The cmdlet will not unlock a scheme with a task still marked as being active. Use Stop-AppLibTask to stop any active task first.

## 相关命令

- [Get-AppLibAppDiske](Get-AppLibAppDiske.html)
- [Stop-AppLibTask](Stop-AppLibTask.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| AppDiskName  | AppDisk 的名称。                                                                                                                                                           | true  | true (ByPropertyName) |                                       |
| AppDiskUid   | AppDisk 的唯一标识符。                                                                                                                                                        | true  | false                 |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                              | false | false                 | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 

## Notes In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
AppDiskNotFound  
The specified provisioning scheme could not be located.  
NoOp  
The specified provisioning scheme had no task object associated.  
TaskActive  
The task object associated with the provisioning scheme is still active.  
DatabaseError  
An error occurred in the service while attempting a database operation.  
CouldNotQuueryDatabase  
The query required to get the database was not defined.  
CommunicationError  
An error occurred while communicating with the service.  
InvalidFilter  
A filtering expression was supplied that could not be interpreted for this cmdlet.  
PermissionDenied  
The user does not have administrative rights to perform this operation.  
ConfigurationLoggingError  
The operation could not be performed because of a configuration logging error  
ExceptionThrown  
An unexpected error occurred. 要查找更多详细信息，请参阅使用的控制器上的 Windows 事件日志，或检查 XenDesktop 日志。

## 示例

### 示例 1

    C:\PS>Unlock-AppLibAppDisk -AppDiskName MyDisk
    

Description  
\---\---\-----  
Unlocks the AppDisk 'MyDisk'.