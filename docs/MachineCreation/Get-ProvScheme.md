# Get-ProvScheme

Gets the list of provisioning schemes.

## 语法

    Get-ProvScheme [[-ProvisioningSchemeName] <String>] [-ProvisioningSchemeUid <Guid>] [-ScopeId <Guid>] [-ScopeName <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Lets you retrieve the list of defined provisioning schemes.

## 相关命令

- [New-ProvScheme](New-ProvScheme.html)
- [Remove-ProvScheme](Remove-ProvScheme.html)
- [Add-ProvSchemeMetadata](Add-ProvSchemeMetadata.html)
- [Remove-ProvSchemeMetadata](Remove-ProvSchemeMetadata.html)
- [Add-ProvSchemeControllerAddress](Add-ProvSchemeControllerAddress.html)
- [Remove-ProvSchemeControllerAddress](Remove-ProvSchemeControllerAddress.html)

## 参数

| 名称                     | 说明                                                        | 是否必需？ | 管道输入  | 默认值                                  |
| ---------------------- | --------------------------------------------------------- | ----- | ----- | ------------------------------------ |
| ProvisioningSchemeName | The name of the provisioning scheme.                      | false | false |                                      |
| ProvisioningSchemeUid  | The unique identifier of the provisioning scheme.         | false | false |                                      |
| ScopeId                | 仅获取作用域匹配指定作用域标识符的结果。                                      | false | false |                                      |
| ScopeName              | 仅获取作用域匹配指定作用域名称的结果。                                       | false | false |                                      |
| ReturnTotalRecordCount | 请参阅 about_Prov_Filtering 了解详细信息。                        | false | false | false                                |
| MaxRecordCount         | 请参阅 about_Prov_Filtering 了解详细信息。                        | false | false | false                                |
| 跳过                     | 请参阅 about_Prov_Filtering 了解详细信息。                        | false | false |                                      |
| SortBy                 | 请参阅 about_Prov_Filtering 了解详细信息。                        | false | false |                                      |
| 过滤器                    | 请参阅 about_Prov_Filtering 了解详细信息。                        | false | false |                                      |
| AdminAddress           | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。 | false | false | LocalHost。有 cmdlet 提供了某个值后，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.MachineCreation.Sdk.ProvisioningScheme  
This object provides details of the provisioning scheme and contains the following information:  
ProvisioningSchemeUid <guid>  
The unique identifier for the provisioning scheme.  
ProvisioningSchemeName <string>  
The name of the provisioning scheme.  
CpuCount <int>  
The number of processors that VMs will be created with when using this scheme.  
MemoryMB <int>  
The maximum amount of memory that VMs will be created with when using this scheme.  
MasterImageVM <string>  
The path within the hosting unit provider to the copy of the VM snapshot that the scheme uses.  
MasterImageVMDate <datetime>  
The date and time that the copy was made of the VM snapshot used by the scheme.  
IdentityPoolUid <guid>  
The unique identifier of the identity pool (from the ADIdentity PowerShell snap-in) that the scheme uses.  
IdentityPoolName <string>  
The name of the identity pool (from the ADIdentity PowerShell snap-in) that the scheme uses.  
HostingUnitUid <guid>  
The unique identifier of the hosting unit (from the Hosting Unit PowerShell snap-in) that the scheme uses.  
HostingUnitName <string>  
The name of the hosting unit (from the Hosting Unit PowerShell snap-in) that the scheme uses.  
CleanOnBoot <boolean>  
Indicates whether the VMs that are created will be reset to a clean state on each boot.  
TaskId <guid>  
The identifier of any current task that is running for the provisioning scheme.  
Metadata <Citrix.MachineCreation.Sdk.Metadata[]>  
The metadata associated with this provisioning scheme.  
ControllerAddress <string[]>  
The DNS names of the controllers associated with this provisioning scheme for Quick Deploy purposes.  
VMMetadata <char[]>  
The opaque VM metadata block  
UsePersonalVDiskStorage <bool>  
True if the scheme will use personal vDisk storage.  
PersonalVDiskDriveLetter <char>  
The drive letter for the personal vDisk  
PersonalVDiskDriveSize <int>  
The size of the personal vDisk in GB  
ProfileUsagePercentage <double>  
The percentage of the personal vDisk to be used for profile data  
DedicatedTenancy <bool>  
Whether to use dedicated tenancy when creating machines in Cloud Hypervisors.  
CurrentMasterImageUid <guid>  
The unique identifier of the current master image used by the provisioning scheme. (See Get-ProvSchemeMasterVMImageHistory.)  
UseWriteBackCache <bool>  
True if the scheme will use the wrote back cache feature.  
WriteBackCacheDiskSize <int>  
The size of the write back cache disk if specified in GB.  
WriteBackCacheMemorySize <int>  
The size of the write back memory cache if specified in MB.  
UseFullDiskCloneProvisioning <bool>  
Indicates whether the machines are provisioned using the dedicated full disk clone feature.

## Notes In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
PartialData  
Only a subset of the available data was returned.  
CouldNotQueryDatabase  
The query to get the database was not defined.  
PermissionDenied  
The user does not have administrative rights to perform this operation.  
ConfigurationLoggingError  
The operation could not be performed because of a configuration logging error.  
CommunicationError  
An error occurred while communicating with the service.  
DatabaseNotConfigured  
The operation could not be completed because the database for the service is not configured.  
InvalidFilter  
A filtering expression was supplied that could not be interpreted for this cmdlet.  
ExceptionThrown  
An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.

## Examples

### EXAMPLE 1

    C:\PS>Get-ProvScheme
    
    
    ProvisioningSchemeUid        : 7585f0de-192e-4847-a6d8-22713c3a2f42
    ProvisioningSchemeName       : Scheme1
    CpuCount                     : 1
    MemoryMB                     : 1024
    MasterImageVM                : /Base.vm/base.snapshot
    MasterImageVMDate            : 17/05/2010 09:27:50
    IdentityPoolUid              : 03743136-e43b-4a87-af74-ab71686b3c16
    IdentityPoolName             : idPool1
    HostingUnitUid               : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501
    HostingUnitName              : HostUnit1
    CleanOnBoot                  : True
    TaskId                       : 00000000-0000-0000-0000-000000000000
    Metadata                     : {Department = Sales}
    ControllerAddress            : {}
    VMMetadata                   : {0, 1, 0, 0...}
    PersonalVDiskDriveLetter     :
    PersonalVDiskDriveSize       : 0
    UsePersonalVDiskStorage      : False
    NetworkMaps                  : {0}
    Scopes                       :
    DedicatedTenancy             : False
    GpuTypeId                    :
    ResetAdministratorPasswords  : False
    SecurityGroups               : {}
    ServiceOffering              :
    CurrentMasterImageUid        : c0571690-4f57-4476-901b-fe64d6aecb79
    UseWriteBackCache            : True
    WriteBackCacheDiskSize       : 24
    WriteBackCacheMemorySize     : 256
    UseFullDiskCloneProvisioning : False
    
    ProvisioningSchemeUid        : 43d82099-1fd7-4617-93f0-25b160813905
    ProvisioningSchemeName       : Scheme2
    CpuCount                     : 1
    MemoryMB                     : 1024
    MasterImageVM                : /Base.vm/base.snapshot
    MasterImageVMDate            : 17/05/2010 09:53:40
    IdentityPoolUid              : 03743136-e43b-4a87-af74-ab71686b3c16
    IdentityPoolName             : idPool1
    HostingUnitUid               : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501
    HostingUnitName              : HostUnit1
    CleanOnBoot                  : True
    TaskId                       : 00000000-0000-0000-0000-000000000000
    Metadata                     : {}
    ControllerAddress            : {}
    VMMetadata                   : {0, 1, 0, 0...}
    PersonalVDiskDriveLetter     :
    PersonalVDiskDriveSize       : 0
    UsePersonalVDiskStorage      : False
    NetworkMaps                  : {0}
    Scopes                       :
    DedicatedTenancy             : False
    GpuTypeId                    :
    ResetAdministratorPasswords  : False
    SecurityGroups               : {}
    ServiceOffering              :
    CurrentMasterImageUid        : 022cd6e4-34cb-3f7c-e02a-44ac404483b4
    UseWriteBackCache            : True
    WriteBackCacheDiskSize       : 24
    WriteBackCacheMemorySize     : 256
    UseFullDiskCloneProvisioning : False
    

Description  
\---\---\-----  
Returns all of the available provisioning schemes.

### EXAMPLE 2

    C:\PS>Get-ProvScheme -ProvisioningSchemeName Scheme[0-1]
    
    
    ProvisioningSchemeUid        : 7585f0de-192e-4847-a6d8-22713c3a2f42
    ProvisioningSchemeName       : Scheme1
    CpuCount                     : 1
    MemoryMB                     : 1024
    MasterImageVM                : /Base.vm/base.snapshot
    MasterImageVMDate            : 17/05/2010 09:27:50
    IdentityPoolUid              : 03743136-e43b-4a87-af74-ab71686b3c16
    IdentityPoolName             : idPool1
    HostingUnitUid               : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501
    HostingUnitName              : HostUnit1
    CleanOnBoot                  : True
    TaskId                       : 00000000-0000-0000-0000-000000000000
    Metadata                     : {}
    ControllerAddress            : {}
    VMMetadata                   : {0, 1, 0, 0...}
    PersonalVDiskDriveLetter     :
    PersonalVDiskDriveSize       : 0
    UsePersonalVDiskStorage      : False
    NetworkMaps                  : {0}
    Scopes                       :
    DedicatedTenancy             : False
    GpuTypeId                    :
    ResetAdministratorPasswords  : False
    SecurityGroups               : {}
    ServiceOffering              :
    CurrentMasterImageUid        : c0571690-4f57-4476-901b-fe64d6aecb79
    UseWriteBackCache            : True
    WriteBackCacheDiskSize       : 24
    WriteBackCacheMemorySize     : 256
    UseFullDiskCloneProvisioning : False
    

Description  
\---\---\-----  
Returns all of the provisioning schemes that have the name 'Scheme0' or 'Scheme1'.