# Get-LogLowLevelOperation

Gets low level operations

## 语法

    Get-LogLowLevelOperation [-Id <Guid>] [-HighLevelOperationId <Guid>] [-StartTime <DateTime>] [-EndTime <DateTime>] [-IsSuccessful <Boolean>] [-User <String>] [-AdminMachineIP <String>] [-Text <String>] [-Source <String>] [-SourceSdk <String>] [-OperationType <OperationType>] [-TargetType <String>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Retrieves low level operations matching the specified criteria. If no parameters are specified this cmdlet returns all low level operations.

## 相关命令

- [Get-LogLowLevelOperation](Get-LogLowLevelOperation.html)

## 参数

| 名称                     | 说明                                                                                                                                                                                                                                | 是否必需？ | 管道输入                  | 默认值                                   |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| ID                     | Gets the low level operation with the specified identifier.                                                                                                                                                                       | false | true (ByPropertyName) |                                       |
| HighLevelOperationId   | Gets low level operations for the high level operation with the specified identifier.                                                                                                                                             | false | false                 |                                       |
| StartTime              | Gets low level operations with the specified start time                                                                                                                                                                           | false | false                 |                                       |
| EndTime                | Gets low level operations with the specified end time.                                                                                                                                                                            | false | false                 |                                       |
| IsSuccessful           | Gets low level operations with the specified success indicator.                                                                                                                                                                   | false | false                 |                                       |
| 用户                     | Gets low level operations logged by the specified administrator.                                                                                                                                                                  | false | false                 |                                       |
| AdminMachineIP         | Gets low level operations logged from the machine with the specified IP address.                                                                                                                                                  | false | false                 |                                       |
| 文本                     | Gets low level operations with the specified text                                                                                                                                                                                 | false | false                 |                                       |
| 源                      | Gets low level operations with the specified source.                                                                                                                                                                              | false | false                 |                                       |
| SourceSdk              | Gets low level operations logged from the SDK with the specified identifier.                                                                                                                                                      | false | false                 |                                       |
| OperationType          | Gets low level operations with the specified operation type. Values can be:  
o AdminActivity - to get operations which log administration activity.  
o ConfigurationChange - to get operations which log configuration changes. | false | false                 |                                       |
| TargetType             | Gets low level operations with the specified target type. The target type describes the type of object that was the target of the configuration change. For example, "Session" or "Machine".                                      | false | false                 |                                       |
| 属性                     | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                                                                                            | false | false                 |                                       |
| ReturnTotalRecordCount | 如果指定此项，cmdlet 将输出包含可用记录数的错误记录。 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Log_Filtering for details.                                                                                                                                   | false | false                 | False                                 |
| MaxRecordCount         | 指定要返回的最大记录数。                                                                                                                                                                                                                      | false | false                 | 250                                   |
| 跳过                     | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                                                                                             | false | false                 |                                       |
| SortBy                 | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                                                                                                          | false | false                 | 默认排序顺序是按名称或唯一标识符。                     |
| 过滤器                    | Gets records that match a PowerShell-style filter expression. See about_Log_Filtering for details.                                                                                                                              | false | false                 |                                       |
| AdminAddress           | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                                                                        | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.ConfigurationLogging.Sdk.LowLevelOperation

The returned LowLevelOperation object has the following properties:  
o Id - The unique identifier of the operation.  
o Text - A description of the operation.  
o HighLevelOperationId - The unique identifier of the related high level operation.  
o StartTime - The date and time that the operation started.  
o EndTime - The date and time that the operation completed. This will be null if the operation is still in progress, or if the operation never completed.  
o IsSuccessful - Indicates whether the operation completed successfully or not. This will be null if the operation is still in progress, or if the operation never completed.  
o AdminSid - The identifier of the administrator who performed the operation.  
o AdminMachineIP - The IP address of the machine that the operation was performed on.  
o Source - The name of the XenDesktop service that the operation was performed on; for example, "MachineCreation", "DelegatedAdmin".  
o SourceSdk - The identifier of the XenDesktop service SDK through which the operation was performed; for example, "Prov", "Admin".  
o OperationType - The operation type. This can be 'AdminActivity' or 'ConfigurationChange'.  
o TargetTypes - Identifies the type of objects that were affected by the operation. For example, "Catalog" or "Desktop","Machine".  
o Parameters - The names and values of the parameters that were supplied for the operation.  
o Details - A collection of OperationDetail objects containing specific information about each object affected by the operation.  
Each OperationDetail object in the 'Details' collection has the following properties:  
o TargetUid - The unique identifier of the target object affected by the operation.  
o TargetName - The name of the target object affected by the operation.  
o TargetType - The type of the target object.  
o Text - The description of operation performed on the target object.  
o StartTime - The date and time that the operation started.  
o EndTime - The date and time that the operation completed. This will be null if the operation is still in progress, or if the operation never completed.  
o IsSuccessful - Indicates whether the operation completed successfully or not. This will be null if the operation is still in progress, or if the operation didn't complete.  
The following properties will be set if the operation changed a property on the object:  
o PropertyName - The name of the changed property.  
o NewValue - The new property value.  
o PreviousValue - The previous property value.  
o AddValue - If the object property contains a set of values, this specifies the new value which was added to the set.  
o RemoveValue- If the object property contains a set of values, this specifies the value which was removed from the set.

## 示例

### 示例 1

    C:\PS> Get-LogLowLevelOperation
    

Description  
\---\---\-----  
Get all low level operations

### 示例 2

    C:\PS> Get-LogLowLevelOperation -OperationType ConfigurationChange
    

Description  
\---\---\-----  
Get low level operations which log configuration changes.

### 示例 3

    C:\PS> Get-LogLowLevelOperation -OperationType AdminActivity
    

Description  
\---\---\-----  
Get low level operations which log administration activities.

### 示例 4

    C:\PS> Get-LogLowLevelOperation -Filter{ StartTime -ge "2013-02-27 09:00:00" -and EndTime -le "2013-02-27 18:00:00"}
    

Description  
\---\---\-----  
Use advanced filtering to get low level operations with a start time on or after "2013-02-27 09:00:00" and an end time on or before "2013-02-27 18:00:00".

### EXAMPLE 5

    C:\PS> Get-LogLowLevelOperation -EndTime $null
    C:\PS> Get-LogLowLevelOperation -IsSuccessful $null
    

Description  
\---\---\-----  
Either of these commands will get low level operations which have not yet been completed.

### EXAMPLE 6

    C:\PS> Get-LogLowLevelOperation -User "DOMAIN\UserName"
    

Description  
\---\---\-----  
Get low level operations performed by user "DOMAIN\UserName".