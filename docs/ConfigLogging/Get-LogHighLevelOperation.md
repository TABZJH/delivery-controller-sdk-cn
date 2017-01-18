# Get-LogHighLevelOperation

Gets high level operations

## 语法

    Get-LogHighLevelOperation [-Id <Guid>] [-Text <String>] [-StartTime <DateTime>] [-Source <String>] [-EndTime <DateTime>] [-IsSuccessful <Boolean>] [-User <String>] [-AdminMachineIP <String>] [-OperationType <OperationType>] [-TargetType <String>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Retrieves high level operations matching the specified criteria. If no parameters are specified this cmdlet returns all high level operations.

## 相关命令

- [Start-LogHighLevelOperation](Start-LogHighLevelOperation.html)
- [Stop-LogHighLevelOperation](Stop-LogHighLevelOperation.html)
- [Get-LogLowLevelOperation](Get-LogLowLevelOperation.html)

## 参数

| 名称                     | 说明                                                                                                                                                                                                                                 | 是否必需？ | 管道输入                  | 默认值                                   |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| ID                     | Gets the high level operation with the specified identifier.                                                                                                                                                                       | false | true (ByPropertyName) |                                       |
| 文本                     | Gets high level operations with the specified text                                                                                                                                                                                 | false | false                 |                                       |
| StartTime              | Gets high level operations with the specified start time                                                                                                                                                                           | false | false                 |                                       |
| 源                      | Gets high level operations with the specified source.                                                                                                                                                                              | false | false                 |                                       |
| EndTime                | Gets high level operations with the specified end time.                                                                                                                                                                            | false | false                 |                                       |
| IsSuccessful           | Gets high level operations with the specified success indicator.                                                                                                                                                                   | false | false                 |                                       |
| 用户                     | Gets high level operations logged by the specified user.                                                                                                                                                                           | false | false                 |                                       |
| AdminMachineIP         | Gets high level operations logged from the machine with the specified IP address.                                                                                                                                                  | false | false                 |                                       |
| OperationType          | Gets high level operations with the specified operation type. Values can be:  
o AdminActivity - to get operations which log administration activity.  
o ConfigurationChange - to get operations which log configuration changes. | false | false                 |                                       |
| TargetType             | Gets high level operations with the specified target type. The target type describes the type of object that was the target of the configuration change. For example, "Session" or "Machine".                                      | false | false                 |                                       |
| 属性                     | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                                                                                                                                             | false | false                 |                                       |
| ReturnTotalRecordCount | 如果指定此项，cmdlet 将输出包含可用记录数的错误记录。 此错误记录是附加信息，并不影响写入输出管道的对象。 See about_Log_Filtering for details.                                                                                                                                    | false | false                 | False                                 |
| MaxRecordCount         | 指定要返回的最大记录数。                                                                                                                                                                                                                       | false | false                 | 250                                   |
| 跳过                     | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                                                                                                                                              | false | false                 |                                       |
| SortBy                 | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。                                                                                                                                           | false | false                 | 默认排序顺序是按名称或唯一标识符。                     |
| 过滤器                    | Gets records that match a PowerShell-style filter expression. See about_Log_Filtering for details.                                                                                                                               | false | false                 |                                       |
| AdminAddress           | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                                                                         | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.ConfigurationLogging.Sdk.HighLevelOperation

The returned HighLevelOperation object has the following properties:  
o Id - The unique identifier of the operation.  
o Text - A description of the operation.  
o StartTime - The date and time that the operation started.  
o EndTime - The date and time that the operation completed. This will be null if the operation is still in progress, or if the operation never completed.  
o IsSuccessful - Indicates whether the operation completed successfully or not. This will be null if the operation is still in progress, or if the operation never completed.  
o User - The identifier of the administrator who performed the operation.  
o AdminMachineIP - The IP address of the machine that the operation was initiated from.  
o Source - Identifies the XenDesktop console, or custom script, where the operation was initiated from. For example, "Desktop Studio", "Desktop Director", "My custom script".  
o OperationType - The operation type. This can be 'AdminActivity' or 'ConfigurationChange'.  
o TargetTypes - Identifies the type of objects that were affected by the operation. For example, "Catalog" or "Desktop","Machine".  
o Parameters - The names and values of the parameters that were supplied for the operation.

## 示例

### 示例 1

    C:\PS> Get-LogHighLevelOperation
    

Description  
\---\---\-----  
Get all high level operations

### 示例 2

    C:\PS> Get-LogHighLevelOperation -OperationType ConfigurationChange
    

Description  
\---\---\-----  
Get high level operations which log configuration changes.

### 示例 3

    C:\PS> Get-LogHighLevelOperation -OperationType AdminActivity
    

Description  
\---\---\-----  
Get high level operations which log administration activities.

### 示例 4

    C:\PS> Get-LogHighLevelOperation -Filter{ StartTime -ge "2013-02-27 09:00:00" -and EndTime -le "2013-02-27 18:00:00"}
    

Description  
\---\---\-----  
Use advanced filtering to get high level operations with a start time on or after "2013-02-27 09:00:00" and an end time on or before "2013-02-27 18:00:00".

### EXAMPLE 5

    C:\PS> Get-LogHighLevelOperation -EndTime $null
    C:\PS> Get-LogHighLevelOperation -IsSuccessful $null
    

Description  
\---\---\-----  
Either of these commands will get high level operations which have not yet been completed.

### EXAMPLE 6

    C:\PS> Get-LogHighLevelOperation -User "DOMAIN\UserName"
    

Description  
\---\---\-----  
Get high level operations performed by user "DOMAIN\UserName".