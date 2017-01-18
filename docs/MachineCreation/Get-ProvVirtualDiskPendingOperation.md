# Get-ProvVirtualDiskPendingOperation

Gets the operations queued for Virtual Disks.

## 语法

    Get-ProvVirtualDiskPendingOperation [-Id <Guid>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Provides the ability to obtain a list of the operations queued for Virtual Disks.

## 相关命令

- [Get-ProvVirtualDisk](Get-ProvVirtualDisk.html)

## 参数

| 名称                     | 说明                                                                                                    | 是否必需？ | 管道输入  | 默认值                                   |
| ---------------------- | ----------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| ID                     | The identifier for the operation                                                                      | false | false |                                       |
| ReturnTotalRecordCount | 如果指定此项，cmdlet 将输出包含可用记录数的错误记录。 此错误记录是附加信息，并不影响写入输出管道的对象。 请参阅 about_Prov_Filtering 了解详细信息。           | false | false | False                                 |
| MaxRecordCount         | 指定要返回的最大记录数。                                                                                          | false | false | 250                                   |
| 跳过                     | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                                 | false | false |                                       |
| SortBy                 | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。              | false | false | 默认排序顺序是按名称或唯一标识符。                     |
| 过滤器                    | Gets records that match a PowerShell-style filter expression. See about_Prov_Filtering for details. | false | false |                                       |
| AdminAddress           | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                            | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.MachineCreation.Sdk.PendingVirtualDiskOperation

The object has the following properties:  
OperationId <guid> The unique identifier of the operation VirtualDiskId <guid> The unique identifier for the virtual disk StorageId <string> The storage location on the hypervisor where the disk resides InProgress <boolean> Whether the operation is in progress Progress <int> Percentage progress indication IsPriority <boolean> Whether the operation is high priority OperationType <string> The kind of operation. Currently the only valid value is "Replicate" TimeLastQueued <datetime> The date and time the operation was last queued for action LastErrorReported <string> The last reported error, if any Retries <int> The number of times the operation has been retried.## Notes In the case of failure, the following errors can result.  
错误代码  
\---\---\-----  
PartialData  
只返回了一部分可用数据。  
CouldNotQueryDatabase  
未定义获取数据库所需的查询。  
PermissionDenied  
用户没有执行此操作的管理权限。  
ConfigurationLoggingError  
由于配置日志记录错误，无法执行操作  
CommunicationError  
与服务通信时发生错误。  
DatabaseNotConfigured  
由于未配置用于服务的数据库，无法完成操作。  
InvalidFilter  
无法为此 cmdlet 解释提供的过滤表达式。  
ExceptionThrown  
发生意外错误。要查找更多详细信息，请参阅使用的控制器上的 Windows 事件日志，或检查 XenDesktop 日志。

## 示例

### 示例 1

    C:\PS>Get-ProvVirtualDiskPendingOperation -Id "33ad07a7-edd7-589b-716a-86cad4739f5e"
    
              OperationId             : 33ad07a7-edd7-589b-716a-86cad4739f5e
              VirtualDiskId           : 5135a865-ba49-4e5f-87f2-2d65ee7a4e51
              StorageId               : a830de93-ddc5-b763-dc1a-35580a31401c
              InProgress              : False
              Progress                : 100
              IsPriority              : False
              OperationType           : Replicate
              TimeLastQueued          : 08/12/2012 09:35:30
              LastErrorReported       :
              Retries                 : 1
    

Description  
\---\---\-----  
Gets the operation '33ad07a7-edd7-589b-716a-86cad4739f5e'.