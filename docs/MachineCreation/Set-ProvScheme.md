# Set-ProvScheme

Changes the parameter values for a provisioning scheme.

## 语法

    Set-ProvScheme [-ProvisioningSchemeName] <String> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CustomProperties <String>] [-ServiceOffering <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-ProvScheme [-ProvisioningSchemeName] <String> -IdentityPoolName <String> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CustomProperties <String>] [-ServiceOffering <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-ProvScheme [-ProvisioningSchemeName] <String> -IdentityPoolUid <Guid> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CustomProperties <String>] [-ServiceOffering <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-ProvScheme -ProvisioningSchemeUid <Guid> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CustomProperties <String>] [-ServiceOffering <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-ProvScheme -ProvisioningSchemeUid <Guid> -IdentityPoolName <String> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CustomProperties <String>] [-ServiceOffering <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-ProvScheme -ProvisioningSchemeUid <Guid> -IdentityPoolUid <Guid> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CustomProperties <String>] [-ServiceOffering <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Provides the ability to update the parameters of an existing provisioning scheme.

This allows the following parameters to be updated:

Number of CPUs that will be used for VMs created from the provisioning scheme. Maximum amount of memory that will be used for VMs created from the provisioning scheme.

To change the name of the provisioning scheme see Rename-ProvScheme.

## 相关命令

- [New-ProvScheme](New-ProvScheme.html)
- [Remove-ProvScheme](Remove-ProvScheme.html)
- [Get-ProvScheme](Get-ProvScheme.html)
- [Rename-ProvScheme](Rename-ProvScheme.html)

## 参数

| 名称                     | 说明                                                                                                                                                                     | 是否必需？ | 管道输入  | 默认值                                   |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| ProvisioningSchemeName | The name of the provisioning scheme to be updated.                                                                                                                     | true  | false |                                       |
| IdentityPoolName       | The name of an identity pool to associate with the provisioning scheme, replacing the present one.                                                                     | true  | false |                                       |
| IdentityPoolUid        | The identifier of an identity pool to associate with the provisioning scheme, replacing the present one.                                                               | true  | false |                                       |
| ProvisioningSchemeUid  | The identifier of the provisioning scheme to be updated.                                                                                                               | true  | false |                                       |
| VMCpuCount             | The number of processors that virtual machines created from the provisioning scheme should use.                                                                        | false | false |                                       |
| VMMemoryMB             | The maximum amount of memory that virtual machines created from the provisioning scheme should use.                                                                    | false | false |                                       |
| CustomProperties       | The properties of the provisioning scheme that are specific to the target hosting infrastructure.                                                                      | false | false |                                       |
| ServiceOffering        | The name of the cloud service offering to use when creating machines.                                                                                                  | false | false |                                       |
| PassThru               | Returns the affected record. By default, this cmdlet does not generate any output.                                                                                     | false | false | False                                 |
| LoggingId              | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                       |
| AdminAddress           | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.MachineCreation.Sdk.ProvisioningScheme  
This object provides details of the provisioning scheme and contains the following information:  
ProvisioningSchemeUid  
ProvisioningSchemeName  
The name of the provisioning scheme.  
CpuCount  
The numer of processors that VMs will be created with when using this scheme.  
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
The name of the hosting unit (from the Hosting Unit PowerShell snap-in) that the new provisioning scheme will use.  
CleanOnBoot  
Indicates whether the VMs created are to be reset to a clean state on each boot.  
TaskId  
The identifier of any current task that is running for the provisioning scheme.

## Notes In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
ProvisioningSchemeNotFound  
The specified provisioning scheme could not be located.  
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
HostingUnitNotFound  
The hosting unit referenced by the provisioning scheme could not be resolved  
ExceptionThrown  
An unexpected error occurred. 要查找更多详细信息，请参阅使用的控制器上的 Windows 事件日志，或检查 XenDesktop 日志。

## 示例

### 示例 1

    C:\PS> Set-ProvScheme -ProvisioningSchemeName MyScheme -VMCpuCount 2
    

Description  
\---\---\-----  
Updates a provisioning scheme called "MyScheme" to use two processors on the VMs that are created from the provisioning scheme.