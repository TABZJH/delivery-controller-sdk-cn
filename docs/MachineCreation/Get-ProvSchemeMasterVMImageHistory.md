# Get-ProvSchemeMasterVMImageHistory

Gets the list of master VM snapshots that have been used to provide hard disks to provisioning schemes.

## 语法

    Get-ProvSchemeMasterVMImageHistory [-ProvisioningSchemeName <String>] [-ProvisioningSchemeUid <Guid>] [-MasterImageVM <String>] [-VMImageHistoryUid <Guid>] [-ImageStatus <String>] [-ShowAll] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Provides the ability to discover the master VM snapshots used to provide the hard disk image for provisioning schemes. This information includes the date and time when the image was introduced.

By default, this cmdlet returns only those snapshots that have been used previously. This information can be used to roll back a provisioning scheme to a previous image.

The ShowAll parameter may be supplied to also show the snapshot for the image currently in use, and the snapshots for any images prepared for later use.

## 相关命令

- [Publish-ProvMasterVMImage](Publish-ProvMasterVMImage.html)
- [Remove-ProvSchemeMasterVMImageHistory](Remove-ProvSchemeMasterVMImageHistory.html)

## 参数

| 名称                     | 说明                                                                                         | 是否必需？ | 管道输入  | 默认值                                  |
| ---------------------- | ------------------------------------------------------------------------------------------ | ----- | ----- | ------------------------------------ |
| ProvisioningSchemeName | The name of the provisioning scheme.                                                       | false | false |                                      |
| ProvisioningSchemeUid  | The unique identifier of the provisioning scheme.                                          | false | false |                                      |
| MasterImageVM          | The path to the snapshot item in the hosting unit PowerShell provider.                     | false | false |                                      |
| VMImageHistoryUid      | The unique identifier for the Image History item.                                          | false | false |                                      |
| ImageStatus            | The status of the provisioning scheme image.                                               | false | false |                                      |
| ShowAll                | Show all images. This includes images currently in use, and images prepared for later use. | false | false | false                                |
| ReturnTotalRecordCount | 请参阅 about_Prov_Filtering 了解详细信息。                                                         | false | false | false                                |
| MaxRecordCount         | 请参阅 about_Prov_Filtering 了解详细信息。                                                         | false | false | false                                |
| 跳过                     | 请参阅 about_Prov_Filtering 了解详细信息。                                                         | false | false |                                      |
| SortBy                 | 请参阅 about_Prov_Filtering 了解详细信息。                                                         | false | false |                                      |
| 过滤器                    | 请参阅 about_Prov_Filtering 了解详细信息。                                                         | false | false |                                      |
| AdminAddress           | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                  | false | false | LocalHost。有 cmdlet 提供了某个值后，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.MachineCreation.Sdk.VMImage  
This object represents a master VM history. It contains the following parameters:  
VMImageHistoryUid <guid>  
The unique identifier for the History item.  
ProvisioningSchemeUid <guid>  
The unique identifier for the provisioning scheme that the VM was used for.  
ProvisioningSchemeName <string>  
The name of the provisioning scheme that the VM was used for.  
MasterImageVM <string>  
The path to the Snapshot item that was used as the master VM image.  
Date <datetime>  
The date and time that the VM or snapshot was used in the provisioning scheme.  
ImageStatus <string>  
The status of the provisioning scheme image.  
MasterImageId <string>  
The unique identifier for the snapshot, as assigned by the hosting unit.  
FunctionalLevel <string>  
The FunctionalLevel of the VDA installed on the VM.

## Notes In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
PartialData  
Only a subset of the available data was returned.  
PermissionDenied  
The user does not have administrative rights to perform this operation.  
ConfigurationLoggingError  
The operation could not be performed because of a configuration logging error.  
CouldNotQueryDatabase  
The query required to get the database was not defined.  
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

    C:\PS>Get-ProvSchemeMasterVMImageHistory
    
    
    VMImageHistoryUid      : 3cba3a75-89cd-4868-989b-27feb378fec5
    ProvisioningSchemeUid  : 7585f0de-192e-4847-a6d8-22713c3a2f42
    ProvisioningSchemeName : MyScheme
    MasterImageVM          : /Base.vm/base.snapshot
    Date                   : 17/05/2010 09:27:50
    

Description  
\---\---\-----  
Gets all the hard disk images that have been used across all provisioning schemes.

### EXAMPLE 2

    C:\PS>Get-ProvSchemeMasterVMImageHistory -ProvisioningSchemeName MyScheme -masterImageVM "/BaseXp.vm/update1.snapshot" | Publish-ProvMasterVMImage
    

Description  
\---\---\-----  
Roll back the provisioning scheme to use the hard disk from the update1.snapshot for the provisioning scheme called "MyScheme".