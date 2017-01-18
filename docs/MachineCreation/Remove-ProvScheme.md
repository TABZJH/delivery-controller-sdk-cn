# Remove-ProvScheme

Removes a provisioning scheme

## 语法

    Remove-ProvScheme [-ProvisioningSchemeName] <String> [-ForgetVM] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-ProvScheme -ProvisioningSchemeUid <Guid> [-ForgetVM] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Provides the ability to remove a provisioning Scheme. The provisioning scheme must not contain any VMs unless the 'ForgetVM' option is specified.

If 'ForgetVM' is not specified, a cmdlet task is created that runs in the background to remove the hard disk copies that have been created for the provisioning scheme in hypervisor storage. Use the Get-ProvTask command to monitor the progress of this task.

## 相关命令

- [Get-ProvTask](Get-ProvTask.html)
- [New-ProvScheme](New-ProvScheme.html)

## 参数

| 名称                     | 说明                                                                                                                                                                                                                                                                                                                            | 是否必需？ | 管道输入                  | 默认值                                   |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| ProvisioningSchemeName | The name of the provisioning scheme to be removed.                                                                                                                                                                                                                                                                            | true  | true (ByPropertyName) |                                       |
| ProvisioningSchemeUid  | The unique identifier for the provisioning scheme to be removed.                                                                                                                                                                                                                                                              | true  | true (ByPropertyName) |                                       |
| ForgetVM               | Indicates whether or not the VMs in the provisioning scheme should be left in the hypervisor and only the data held in the Machine Creation Services removed. If this is specified, it is up to the administrator of the hypervisor to remove the VMs and hard disk images using the tools provided by the hypervisor itself. | false | false                 |                                       |
| LoggingId              | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                        | false | false                 |                                       |
| AdminAddress           | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                                                                                                                                                                     | false | false                 | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.MachineCreation.Sdk.ProvisioningScheme  
This object provides details of the provisioning scheme and contains the following information:  
ProvisioningSchemeUid  
The unique identifier for the provisioning scheme.  
ProvisioningSchemeName  
The name of the provisioning scheme.  
CpuCount  
The number of processors that VMs will be created with when using this scheme.  
MemoryMB  
The maximum amount of memory that VMs will be created with when using this scheme.  
MasterImageVM  
The path within the hosting unit provider to the VM or snapshot of which the scheme is currently using a copy.  
MasterImageVMDate  
The date and time that the copy of the VM image was made for the scheme.  
IdentityPoolUid  
The unique identifier of the identity pool (from the ADIdentity PowerShell snap-in) that the scheme uses.  
IdentityPoolName  
The name of the identity pool (from the ADIdentity PowerShell snap-in) that the scheme uses.  
HostingUnitUid  
The unique identifier of the hosting unit (from the Hosting Unit PowerShell snap-in) that the new provisioning scheme will use.  
HostingUnitName  
The name of the hosting unit (from the hosting unit PowerShell snap-in) that the new provisioning scheme will use.  
CleanOnBoot  
Indicates whether the VMs created are to be reset to a clean state on each boot.  
TaskId  
The identifier of any current task that is running for the provisioning scheme.

## Notes If the hosting unit referenced by the provisioning scheme no longer exists (i.e. it has been removed using the Hosting Unit PowerShell snap-in), the provisioning scheme data is deleted from the database without errors. However, the hard disks associated with the provisioning scheme cannot be removed and remain in the hypervisor.  
In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
IllegalParameter  
One or more parameters are illegal or are not specified.  
ProvisioningSchemeNotFound  
The specified provisioning scheme could not be located.  
UnableToRemoveProvisioningSchemeDueToAssociatedVM  
The provisioning scheme contained VMs and the 'ForgetVM' parameter was not specified.  
DatabaseError  
An error occurred in the service while attempting a database operation.  
DatabaseNotConfigured  
The operation could not be completed because the database for the service is not configured.  
ServiceStatusInvalidDb  
An error occurred in the service while attempting a database operation - communication with the database failed for  
for various reasons.  
CommunicationError  
An error occurred while communicating with the service.  
PermissionDenied  
The user does not have administrative rights to perform this operation.  
ConfigurationLoggingError  
The operation could not be performed because of a configuration logging error  
ExceptionThrown  
An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.  
The cmdlet is associated with a task of type DisusedImageCleanUp, and while active will move through the following operations (CurrentOperation field)  
Running

## 示例

### 示例 1

    c:\PS>Remove-ProvScheme -ProvisioningSchemeName $provScheme.ProvisioningSchemeName
    

Description  
\---\---\-----  
Remove the empty provisioning scheme by name.