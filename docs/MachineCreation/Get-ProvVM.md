# Get-ProvVM

Gets the VMs that were created using Citrix XenDesktop Machine Creation Services.

## 语法

    Get-ProvVM [[-ProvisioningSchemeName] <String>] [-ProvisioningSchemeUid <Guid>] [-VMName <String>] [-Locked <Boolean>] [-Tag <String>] [-OutOfDate] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Provides the ability to obtain a list of the VMs that were created using Machine Creation Services.

## 相关命令

- [New-ProvVM](New-ProvVM.html)
- [Remove-ProvVM](Remove-ProvVM.html)
- [Lock-ProvVM](Lock-ProvVM.html)
- [Unlock-ProvVM](Unlock-ProvVM.html)

## 参数

| 名称                     | 说明                                                                                                                                 | 是否必需？ | 管道输入  | 默认值                                   |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| ProvisioningSchemeName | The name of the provisioning scheme.                                                                                               | false | false |                                       |
| ProvisioningSchemeUid  | The unique identifier of the provisioning scheme.                                                                                  | false | false |                                       |
| VMName                 | The name of the VM in the hypervisor context.                                                                                      | false | false |                                       |
| 已锁定                    | Indicates whether only VMs that are marked as locked are returned or not (see Lock-ProvVM and Unlock-ProvVM for details).          | false | false |                                       |
| 标记                     | The tag string that was associated with the VM when it was locked.                                                                 | false | false |                                       |
| OutOfDate              | Indicates that the image currently assigned to the VM is out of date. The image will be updated the next time the VM is restarted. | false | false |                                       |
| ReturnTotalRecordCount | 请参阅 about_Prov_Filtering 了解详细信息。                                                                                                 | false | false | false                                 |
| MaxRecordCount         | 请参阅 about_Prov_Filtering 了解详细信息。                                                                                                 | false | false | false                                 |
| 跳过                     | 请参阅 about_Prov_Filtering 了解详细信息。                                                                                                 | false | false |                                       |
| SortBy                 | 请参阅 about_Prov_Filtering 了解详细信息。                                                                                                 | false | false |                                       |
| 过滤器                    | 请参阅 about_Prov_Filtering 了解详细信息。                                                                                                 | false | false |                                       |
| AdminAddress           | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                          | false | false | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.MachineCreation.Sdk.ProvisionedVirtualMachine  
The object has the following properties:  
ADAccountSid <string>  
The SID of the AD computer account that the VM is using.  
ADAccountName <string>  
The name of the AD computer account that the VM is using.  
CpuCount <int>  
The number of processors that the VM has been allocated.  
CreationDate <datetime>  
The date and time that the VM was created.  
Domain <string>  
The Domain of the AD computer account that the VM is using.  
ImageOutOfDate <boolean>  
Indicates if the image will be updated next time the VM is started.  
Lock <boolean>  
Indicates whether the VM is locked or not.  
MemoryMB <int>  
The maximum amount of memory that VMs will be created with when using this scheme.  
ProvisioningSchemeName <string>  
The name of the provisioning scheme that the VM is part of.  
ProvisioningSchemeUid <guid>  
The unique identifier for the provisioning scheme that the VM is part of.  
Tag <string>  
Provides the string associated with a locked VM.  
VMId <string>  
The identifier for the VM (hypervisor context).  
VMName <string>  
The name of the VM (hypervisor context).  
AssignedImage <string>  
The identifier (in the hypervisor) for the hard disk image that the VM is currently assigned.  
BootedImage <string>  
The identifier (in the hypervisor) for the hard disk image with which the VM is currently started.  
HostingUnitUid <guid>  
The unique identifier for the hosting unit that was used to create the VM.  
HypervisorConnectionUid <guid>  
The unique identifier of the hypervisor connection that was used to create the VM.  
LastBootTime <datetime>  
The date and time of the last start of the VM.  
OSDiskIndex <int>  
The disk index at which the hard disk image, from which the VM is currently started, is attached (or [int]::MinValue for VMs inherited from versions of XenDesktop before 5.6)  
PersonalVDiskIndex <int>  
The disk index at which the personal vdisk is attached (defaults to [int]::MinValue for VMs without a personal vdisk)  
PersonalVDiskStorage <string>  
The identifier (in the hypervisor) for the storage on which the personal virtual disk image from which the VM is currently started is located. This is set only if the VM has a personal vDisk attached  
StorageId <string>  
The identifier (in the hypervisor) for the storage on which the hard disk image, from which the VM is currently started, is located.

## Notes In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
PartialData  
Only a subset of the available data was returned.  
CouldNotQueryDatabase  
The query required to get the database was not defined.  
PermissionDenied  
The user does not have administrative rights to perform this operation.  
ConfigurationLoggingError  
The operation could not be performed because of a configuration logging error  
CommunicationError  
An error occurred while communicating with the service.  
DatabaseNotConfigured  
The operation could not be completed because the database for the service is not configured.  
InvalidFilter  
A filtering expression was supplied that could not be interpreted for this cmdlet.  
ExceptionThrown  
An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.

## Examples

### EXAMPLE 1

    C:\PS>Get-ProvVM -provisioningSchemeName MyScheme
    
    ADAccountName           : MYDomain\computer2$
    ADAccountSid            : S-1-5-21-3751941309-1176885247-1409628468-3179
    CpuCount                : 1
    CreationDate            : 17/05/2012 09:35:22
    Domain                  : steve.dum.local
    ImageOutOfDate          : False
    Lock                    : True
    MemoryMB                : 512
    ProvisioningSchemeName  : XenPS
    ProvisioningSchemeUid   : 5135a865-ba49-4e5f-87f2-2d65ee7a4e51
    Tag                     : Brokered
    VMId                    : a830de93-ddc5-b763-dc1a-35580a31401c
    VMName                  : IP0051
    AssignedImage           : 57fc60c3-eb9b-4d38-8646-0afceec85335
    BootedImage             : 57fc60c3-eb9b-4d38-8646-0afceec85335
    HostingUnitUid          : ea17840f-cf2d-4d80-94e0-3b752b32e0af
    HypervisorConnectionUid : 99f9f826-31fc-4453-8ca0-9ba54306c3ac
    IdentityDiskIndex       : 1
    LastBootTime            : 17/05/2012 09:35:22
    OSDiskIndex             : 0
    PersonalVDiskIndex      : -2147483648
    PersonalVDiskStorage    : 
    StorageId               : 33ad07a7-edd7-589b-716a-86cad4739f5e
    

Description  
\---\---\-----  
Gets all the Virtual Machines that were provisioned into the Provisioning Scheme called 'MyScheme'.

### EXAMPLE 2

    C:\PS>Get-ProvVM -Locked $true
    
    ADAccountName           : MYDomain\computer1$
    ADAccountSid            : S-1-5-21-3751941309-1176885247-1409628468-3178
    CpuCount                : 1
    CreationDate            : 17/05/2012 09:35:30
    Domain                  : steve.dum.local
    ImageOutOfDate          : False
    Lock                    : True
    MemoryMB                : 512
    ProvisioningSchemeName  : XenPS
    ProvisioningSchemeUid   : 5135a865-ba49-4e5f-87f2-2d65ee7a4e51
    Tag                     : Brokered
    VMId                    : a830de93-ddc5-b763-dc1a-35580a31401c
    VMName                  : IP0051
    AssignedImage           : 57fc60c3-eb9b-4d38-8646-0afceec85335
    BootedImage             : 57fc60c3-eb9b-4d38-8646-0afceec85335
    HostingUnitUid          : ea17840f-cf2d-4d80-94e0-3b752b32e0af
    HypervisorConnectionUid : 99f9f826-31fc-4453-8ca0-9ba54306c3ac
    IdentityDiskIndex       : 1
    LastBootTime            : 17/05/2012 09:35:22
    OSDiskIndex             : 0
    PersonalVDiskIndex      : -2147483648
    PersonalVDiskStorage    : 
    StorageId               : 33ad07a7-edd7-589b-716a-86cad4739f5e
    

Description  
\---\---\-----  
Gets all the Virtual Machines that were locked, regardless of which Provisioning Scheme the VM is part of.