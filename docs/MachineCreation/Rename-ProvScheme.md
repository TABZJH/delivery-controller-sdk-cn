# Rename-ProvScheme

Renames a provisioning scheme.

## 语法

    Rename-ProvScheme [-ProvisioningSchemeName] <String> [-NewProvisioningSchemeName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Rename-ProvScheme -ProvisioningSchemeUid <Guid> [-NewProvisioningSchemeName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Provides the ability to change the name of an existing provisioning scheme. The unique identifier for the provisioning scheme never changes after it has been created so, regardless of any name changes, the provisioning scheme can always be identified by its unique identifier.

## 相关命令

- [New-ProvScheme](New-ProvScheme.html)
- [Set-ProvScheme](Set-ProvScheme.html)
- [Get-ProvScheme](Get-ProvScheme.html)
- [Test-ProvSchemeNameAvailable](Test-ProvSchemeNameAvailable.html)

## 参数

| 名称                        | 说明                                                                                                                                                                                            | 是否必需？   | 管道输入  | 默认值                                   |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- | ----- | ------------------------------------- |
| ProvisioningSchemeName    | The current name of the provisioning scheme.                                                                                                                                                  | true    | false |                                       |
| ProvisioningSchemeUid     | The identifier for the provisioning scheme that is to be renamed.                                                                                                                             | true    | false |                                       |
| NewProvisioningSchemeName | The new name for the provisioning scheme. This must be a name that is not being used by an existing provisioning scheme, and it must not contain any of the following characters \/;:#.*?=<> | []()""' | true  | false |                               |
| PassThru                  | Defines whether or not the command returns a result showing the new state of the updated identity pool.                                                                                       | false   | false | true                                  |
| LoggingId                 | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                        | false   | false |                                       |
| AdminAddress              | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                                     | false   | false | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

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
Metadata  
The metadata for the provisioning scheme.

## Notes In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
ProvisioningSchemeNotFound  
The specified provisioning scheme could not be located.  
ProvisioningSchemeNameAlreadyExists  
A provisioning scheme with the same name as the new provisioning scheme name already exists.  
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
An unexpected error occurred. To locate more details, see the windows event logs on the controller being used or examine the XenDesktop logs.

## 示例

### 示例 1

    C:\PS>Rename-ProvScheme -provisioningSchemeName CurrentName -NewProvisioningSchemeName NewName
    

Description  
\---\---\-----  
Renames a provisioning scheme from "currentName" to "NewName".

### 示例 2

    C:\PS>Rename-ProvScheme -provisioningSchemeName CurrentName -NewProvisioningSchemeName NewName -PassThru
    
    
    ProvisioningSchemeUid  : 7585f0de-192e-4847-a6d8-22713c3a2f42
    ProvisioningSchemeName : NewName
    CpuCount               : 1
    MemoryMB               : 1024
    MasterImageVM          : /Base.vm
    MasterImageVMDate      : 17/05/2010 08:27:50
    IdentityPoolUid        : 03743136-e43b-4a87-af74-ab71686b3c16
    IdentityPoolName       : IdPool1
    HostingUnitUid         : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501
    HostingUnitName        : XenHU
    CleanOnBoot            : True
    TaskId                 : 
    Metadata               : {}
    

Description  
\---\---\-----  
Renames a provisioning scheme from "currentName" to "NewName" and displays the resulting state.