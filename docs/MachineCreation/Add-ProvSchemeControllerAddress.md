# Add-ProvSchemeControllerAddress

Adds a list of host names (as DNS addresses) to a provisioning scheme.

## 语法

    Add-ProvSchemeControllerAddress [-ProvisioningSchemeName] <String> [-ControllerAddress] <String[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Add-ProvSchemeControllerAddress -ProvisioningSchemeUid <Guid> [-ControllerAddress] <String[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Provides the ability to associate controller hosts (and hence implicitly a set of brokers) with a specific provisioning scheme. This optional data is passed to the machines created by the Machine Creation Services, where it is used to associate the newly created machine with a broker. The list is returned along with the provisioning scheme that it is assigned to.

## 相关命令

- [Get-ProvScheme](Get-ProvScheme.html)
- [Remove-ProvSchemeControllerAddress](Remove-ProvSchemeControllerAddress.html)

## 参数

| 名称                     | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| ProvisioningSchemeName | The name for the provisioning scheme that the list of addresses is to be added to.                                                                                     | true  | true (ByPropertyName) |                                       |
| ProvisioningSchemeUid  | The unique identifier for the provisioning scheme that the list of addresses is to be added to.                                                                        | true  | false                 |                                       |
| ControllerAddress      | Specifies the array of DNS names to be added to the provisioning scheme.                                                                                               | true  | true (ByPropertyName) |                                       |
| LoggingId              | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress           | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                              | false | false                 | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.MachineCreation.Sdk.ProvisioningScheme  
You can pipe an object containing a parameter called 'ProvisioningSchemeName' to Add-ProvSchemeControllerAddress.

## 返回值

### Citrix.MachineCreation.Sdk.ProvisioningScheme  
Add-ProvSchemeControllerAddress returns the updated ProvisioningScheme object containing the union of the old and new controller address lists.  
ProvisioningSchemeUid <guid>  
The unique identifier for the provisioning scheme.  
ProvisioningSchemeName <string>  
The name of the provisioning scheme.  
CpuCount <int>  
The number of processors that VMs will be created with when using this scheme.  
MemoryMB <int>  
The maximum amount of memory that VMs will be created with when using this scheme.  
MasterImageVM <string>  
The path within the hosting unit provider to the VM or snapshot of which the scheme is currently using a copy.  
MasterImageVMDate <datetime>  
The date and time that the copy of the VM image was made for the scheme.  
IdentityPoolUid <guid>  
The unique identifier of the identity pool (from the ADIdentity PowerShell snap-in) that the scheme uses.  
IdentityPoolName <string>  
The name of the identity pool (from the ADIdentity PowerShell snap-in) that the scheme uses.  
HostingUnitUid <guid>  
The unique identifier of the hosting unit (from the Hosting Unit PowerShell snap-in) that the scheme will use.  
HostingUnitName <string>  
The name of the hosting unit (from the Hosting Unit PowerShell snap-in) that the scheme will use.  
CleanOnBoot <boolean>  
Indicates whether or not the VMs created are to be reset to a clean state on each boot.  
TaskId <guid>  
The identifier of any current task that is running for the provisioning scheme.  
Metadata <Citrix.MachineCreation.Sdk.Metadata[]>  
The metadata associated with this provisioning scheme.  
ControllerAddress <string[]>  
The DNS names of the controllers associated with this provisioning scheme for Quick Deploy purposes.

## Notes In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
ProvisioningSchemeNotFound  
The specified provisioning scheme could not be located.  
PermissionDenied  
The user does not have administrative rights to perform this operation.  
ConfigurationLoggingError  
The operation could not be performed because of a configuration logging error  
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
ExceptionThrown  
An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.

## Examples

### EXAMPLE 1

    C:\PS>Add-ProvSchemeControllerAddress -ProvisioningSchemeUid "01a4a008-8ce8-4165-ba9c-cdf15a6b0501" -ControllerAddress (ddcA.citrix.com,ddcB.citrix.com,ddcC.citrix2.com)
    
    ProvisioningSchemeUid  : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501
    ProvisioningSchemeName : Scheme2
    CpuCount               : 1
    MemoryMB               : 1024
    MasterImageVM          : Base.vm/Base.snapshot
    MasterImageVMDate      : 17/05/2010 09:53:40
    IdentityPoolUid        : 03743136-e43b-4a87-af74-ab71686b3c16
    IdentityPoolName       : idPool1
    HostingUnitUid         : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501
    HostingUnitName        : HostUnit1
    CleanOnBoot            : True
    TaskId                 : 00000000-0000-0000-0000-000000000000
    Metadata               : {}
    ControllerAddress      : {ddcA.citrix.com,ddcB.citrix.com,ddcC.citrix2.com}
    

Description  
\---\---\-----  
Add a set of controllers to the provisioning scheme with the identifier "01a4a008-8ce8-4165-ba9c-cdf15a6b0501".

### EXAMPLE 2

    C:\PS>Get-ProvScheme -ProvisioningSchemeName scheme1 | Add-ProvSchemeControllerAddress -ControllerAddress (ddcA.citrix.com,ddcB.citrix.com,ddcC.citrix2.com)
    
    ProvisioningSchemeUid  : 7585f0de-192e-4847-a6d8-22713c3a2f42
    ProvisioningSchemeName : Scheme1
    CpuCount               : 1
    MemoryMB               : 1024
    MasterImageVM          : Base.vm/Base.snapshot
    MasterImageVMDate      : 17/05/2010 09:53:40
    IdentityPoolUid        : 03743136-e43b-4a87-af74-ab71686b3c16
    IdentityPoolName       : idPool1
    HostingUnitUid         : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501
    HostingUnitName        : HostUnit1
    CleanOnBoot            : True
    TaskId                 : 00000000-0000-0000-0000-000000000000
    Metadata               : {}
    ControllerAddress      : {ddcA.citrix.com,ddcB.citrix.com,ddcC.citrix2.com}
    

Description  
\---\---\-----  
Add controller addresses to a provisioning scheme using a ProvisioningScheme object.