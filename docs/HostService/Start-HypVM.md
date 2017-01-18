# Start-HypVM

Starts a VM.

## 语法

    Start-HypVM [-LiteralPath] <String> [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

This command provides a mechanism to start a VM.

## 相关命令

## 参数

| 名称           | 说明                                                                                                                                                                                                                                                                                                                                                                                                                                             | 是否必需？ | 管道输入           | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------- |
| LiteralPath  | Specifies the path within a hosting unit provider to the virtual machine item to start. The path specified must be in one of the following formats: <drive>:\Connections\<connection name>\<item path of vm object> 或者 <drive>:\Connections\{<connection uid>\<item path of vm object>} or <drive>:\HostingUnits\<hostingunit name>\<item path of vm object> 或者 <drive>:\HostingUnits\{<hostingunit uid>\<item path of vm object>} | true  | true (ByValue) |                                       |
| AdminAddress | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                                                                                                                                                                                                                                                                                      | false | false          | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### System.string  
You can pipe a string that contains a path.

## 返回值

### System.void.

## Notes In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
InputHypervisorItemPathInvalid  
The path provided is not to an item in a sub-directory of a connection item or a hosting unit item.  
InvalidHypervisorItemPath  
No item exists with the specified path.  
InvalidHypervisorItem  
The item specified by the path exists, but is not a VM Item.  
HypervisorInMaintenanceMode  
The hypervisor is in maintenance mode.  
DatabaseError  
An error occurred in the service while attempting a database operation.  
DatabaseNotConfigured  
The operation could not be completed because the database for the service is not configured.  
CommunicationError  
An error occurred while communicating with the service.  
PermissionDenied  
The user does not have administrative rights to perform this operation.  
ExceptionThrown  
An unexpected error occurred. For more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.

## 示例

### 示例 1

    C:\PS>Start-HypVM -LiteralPath XDHyp:\Connections\MyConnection\MyVm.vm
    

Description  
\---\---\-----  
This command starts a VM called 'MyVm.vm' within a hypervisor connection called 'MyConnection'.