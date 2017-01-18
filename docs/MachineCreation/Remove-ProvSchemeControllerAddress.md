# Remove-ProvSchemeControllerAddress

Removes metadata from a provisioning scheme.

## 语法

    Remove-ProvSchemeControllerAddress [-ProvisioningSchemeName] <String> [-ControllerAddress] <String[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-ProvSchemeControllerAddress -ProvisioningSchemeUid <Guid> -ControllerAddress <String[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Removes the specified controller addresses from the specified object. Attempting to remove an address not present writes an error record to the pipeline.

## 相关命令

- [Get-ProvScheme](Get-ProvScheme.html)
- [Add-ProvSchemeControllerAddress](Add-ProvSchemeControllerAddress.html)

## 参数

| 名称                     | 说明                                                                                                                                                                     | 是否必需？ | 管道输入                  | 默认值                                   |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| ProvisioningSchemeName | The name of the provisioning scheme from which metadata is to be removed.                                                                                              | true  | true (ByPropertyName) |                                       |
| ProvisioningSchemeUid  | The identifier of the provisioning scheme from which metadata is to be removed.                                                                                        | true  | false                 |                                       |
| ControllerAddress      | Specifies the array of DNS names to be removed from the provisioning scheme.                                                                                           | true  | true (ByPropertyName) |                                       |
| LoggingId              | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false                 |                                       |
| AdminAddress           | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                              | false | false                 | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.MachineCreation.Sdk.ProvisioningScheme  
You can pipe an object containing a parameter called 'ProvisioningSchemeName' to Remove-ProvSchemeMetadata.

## 返回值

### 

## Notes In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
ProvisioningSchemeNotFound  
The specified provisioning scheme could not be located.  
ControllerAddressNotFound  
The specified address was not associated with the provisioning scheme.  
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
An unexpected error occurred. 要查找更多详细信息，请参阅使用的控制器上的 Windows 事件日志，或检查 XenDesktop 日志。

## 示例

### 示例 1

    C:\PS>Get-ProvScheme -ProvisioningSchemeName scheme1 | Remove-ProvSchemeControllerAddress
    
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
    ControllerAddress      : {}
    

Description  
\---\---\-----  
Remove all controller addresses from the provisioning scheme with the name "scheme1".

### 示例 2

    C:\PS>Remove-ProvSchemeControllerAddress -ProvisioningSchemeUid "01a4a008-8ce8-4165-ba9c-cdf15a6b0501" -ControllerAddress (ddcA.citrix.com,ddcC.citrix2.com)
    
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
    ControllerAddress      : {ddcB.citrix.com}
    

Description  
\---\---\-----  
Remove a subset of the controller address list from the provisioning scheme with the identifier "01a4a008-8ce8-4165-ba9c-cdf15a6b0501".