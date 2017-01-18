# Get-SfTask

Gets the task history for the Storefront Service.

## 语法

    Get-SfTask [[-TaskId] <Guid>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Returns a list of tasks that have run or are currently running within the Storefront Service.

## 相关命令

- [Remove-SfTask](Remove-SfTask.html)
- [Add-SfTaskMetadata](Add-SfTaskMetadata.html)
- [Remove-SfTaskMetadata](Remove-SfTaskMetadata.html)

## 参数

| 名称                     | 说明                                                                                                  | 是否必需？ | 管道输入  | 默认值                                   |
| ---------------------- | --------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| TaskId                 | Specifies the task identifier to be returned.                                                       | false | false |                                       |
| ReturnTotalRecordCount | 如果指定此项，cmdlet 将输出包含可用记录数的错误记录。 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Sf_Filtering for details.      | false | false | False                                 |
| MaxRecordCount         | 指定要返回的最大记录数。                                                                                        | false | false | 250                                   |
| 跳过                     | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                               | false | false |                                       |
| SortBy                 | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。            | false | false | 默认排序顺序是按名称或唯一标识符。                     |
| 过滤器                    | Gets records that match a PowerShell-style filter expression. See about_Sf_Filtering for details. | false | false |                                       |
| AdminAddress           | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                          | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### 

## Notes If the command fails, the following errors can be returned.  
Error Codes  
\---\---\-----  
UnknownObject  
One of the specified objects was not found.  
PartialData  
Only a subset of the available data was returned.  
InvalidFilter  
A filtering expression was supplied that could not be interpreted for this cmdlet.  
CouldNotQueryDatabase  
The query required to get the database was not defined.  
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
CommunicationError  
There was a problem communicating with the remote service.  
ExceptionThrown  
An unexpected error occurred. 有关更多详细信息，请参阅控制器上的 Windows 事件日志或 XenDesktop 日志。

## 示例

### 示例 1

    <br />

说明  
\---\---\-----