# New-HypVMSnapshot

Creates a new snapshot for the specified VM item path.

## 语法

    New-HypVMSnapshot [-LiteralPath] <String> [-SnapshotName] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [[-SnapshotDescription] <String>] [<CommonParameters>]
    

## 详细说明

Use this command to create a new snapshot of a virtual machine, for a given Host Service provider path to a VM. The resulting snapshot can then be used for operations that require a snapshot to work.

## 相关命令

## 参数

| 名称                  | 说明                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | 是否必需？ | 管道输入           | 默认值                                   |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----- | -------------- | ------------------------------------- |
| LiteralPath         | Specifies the path within a hosting unit provider to the virtual machine item for which to create a new snapshot. The path specified must be in one of the following formats: <drive>:\Connections\<connection name>\<item path of vm object> 或者 <drive>:\Connections\{<connection uid>\<item path of vm object>} or <drive>:\HostingUnits\<hostingunit name>\<item path of vm object> 或者 <drive>:\HostingUnits\{<hostingunit uid>\<item path of vm object>} | true  | true (ByValue) |                                       |
| SnapshotName        | The name of the new snapshot. This is visible in the hypervisor management console.                                                                                                                                                                                                                                                                                                                                                                                      | true  | false          |                                       |
| LoggingId           | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                                                                                                                                                                   | false | false          |                                       |
| AdminAddress        | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                                                                                                                                                                                                                                                                                                                | false | false          | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |
| SnapshotDescription | The description to add to the snapshot. This is visible in the hypervisor management console.                                                                                                                                                                                                                                                                                                                                                                            | false | false          |                                       |

## 输入类型

### System.string  
You can pipe a string that contains a path to Get-HypConfigurationDataForItem

## 返回值

### System.string.  
The provider path to the newly created snapshot.

## Notes In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
InputHypervisorItemPathInvalid  
The path provided is not to an item in a sub-directory of a connection item or a hosting unit item.  
InvalidHypervisorItemPath  
No item exists with the specified path.  
InvalidHypervisorItem  
The item specified by the path exists, but is not a VM Item.  
SnapshotNameAlreadyInUse  
The specified name is already in use and will cause a name resolution clash.  
FailedToCreateSnapshot  
The snapshot creation process failed.  
HypervisorInMaintenanceMode  
The hypervisor is in maintenance mode.  
DatabaseError  
An error occurred in the service while attempting a database operation.  
DatabaseNotConfigured  
The operation could not be completed because the database for the service is not configured.  
DataStoreException  
An error occurred in the service while attempting a database operation - communication with the database failed for  
various reasons.  
CommunicationError  
An error occurred while communicating with the service.  
PermissionDenied  
The user does not have administrative rights to perform this operation.  
ExceptionThrown  
An unexpected error occurred. For more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.  
SnapshotChainTooLong  
Snapshot creation failed. Snapshot chain is too long.  
SnapshotCreationNotAuthorized  
Snapshot creation failed. User not authorized to create snapshots.

## 示例

### 示例 1

    C:\PS>New-HypVMSnapshot -LiteralPath XDHyp:\Connections\MyConnection\MyVm.vm -SnapshotName "New snapshot" -SnapshotDescription "Example snapshot"
    
                         XDHyp:\Connections\MyConnection\MyVm.vm\New snapshot.snapshot
    

Description  
\---\---\-----  
This command creates a snapshot of a VM called 'MyVm.vm' within a hypervisor connection called 'MyConnection'.