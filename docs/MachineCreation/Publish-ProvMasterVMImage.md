# Publish-ProvMasterVMImage

Update the master image associated with the provisioning scheme.

## 语法

    Publish-ProvMasterVMImage [-ProvisioningSchemeName] <String> -MasterImageVM <String> [-VhdTemplateSource <String>] [-VhdResultDestination <String>] [-AppScanResultsFile <String>] [-FunctionalLevel <String>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-DoNotStoreOldImage] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Publish-ProvMasterVMImage -ProvisioningSchemeName <String> [-DoNotStoreOldImage] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Publish-ProvMasterVMImage -ProvisioningSchemeUid <Guid> -MasterImageVM <String> [-VhdTemplateSource <String>] [-VhdResultDestination <String>] [-AppScanResultsFile <String>] [-FunctionalLevel <String>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-DoNotStoreOldImage] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Publish-ProvMasterVMImage -ProvisioningSchemeUid <Guid> [-DoNotStoreOldImage] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Provides the ability to update the hard disk image used to provision virtual machines. If the provisioning scheme is a 'CleanOnBoot' type, then the next time that virtual machines are started, their hard disks are updated to this new image. Regardless of the 'CleanOnBoot' type, all new virtual machines created after this command will use this new hard disk image.

A background task will be created to remove the old hard disk copies. You can locate and monitor this task using the Get-ProvTask cmdlet.

A snapshot or VM template is used rather than a VM, so that the content of the hard disk for the provisioning scheme can be easily determined.

As the snapshot or VM template are specified using a path into the Citrix Host Service PowerShell Provider, the Citrix Host Service PowerShell snap-in must also be loaded for this cmdlet to be used.

The previous hard disk image path is stored into the history (see Get-ProvSchemeMasterVMImageHistory). The data stored in the history allows for a rollback to be undertaken, to revert to the previous hard disk image if required.

## 相关命令

- [Get-ProvSchemeMasterVMImageHistory](Get-ProvSchemeMasterVMImageHistory.html)
- [Get-ProvScheme](Get-ProvScheme.html)

## 参数

| 名称                     | 说明                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | 是否必需？ | 管道输入                  | 默认值                                   |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| ProvisioningSchemeName | The provisioning scheme to which the hard disk image should be updated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | true  | true (ByPropertyName) |                                       |
| MasterImageVM          | The path in the hosting unit provider to the virtual machine snapshot or VM template that will be used. This identifies the hard disk to be used and the default values for the memory and processors. This must be a path to a Snapshot or Template item in the hosting unit that the hosting unit name or hosting unit Uid refers to.  
Valid paths are of the format; XDHyp:\HostingUnits\<hostingunitname>\<path>\<vmname>.vm\<snapshotname>.snapshot XDHyp:\HostingUnits\<hostingunitname>\<path>\<templatename>.template | true  | true (ByPropertyName) |                                       |
| ProvisioningSchemeUid  | The provisioning scheme identifier to which the hard disk image should be updated.                                                                                                                                                                                                                                                                                                                                                                                                                                                      | true  | false                 |                                       |
| VhdTemplateSource      | A file path to a source VHD template to be used when performing application scanning during image preparation. The presence of this parameter in conjunction with VhdResultDestination implies that application scanning is to be performed                                                                                                                                                                                                                                                                                             | false | false                 |                                       |
| VhdResultDestination   | A file path (including file name) where the VHD disk file containing the results of application scanning should be written.                                                                                                                                                                                                                                                                                                                                                                                                             | false | false                 |                                       |
| AppScanResultsFile     | File name to which the results of application scanning should be written.                                                                                                                                                                                                                                                                                                                                                                                                                                                               | false | false                 |                                       |
| FunctionalLevel        | The FunctionalLevel of the VDA installed on the given MasterImageVM.                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | false | false                 |                                       |
| RunAsynchronously      | Indicates whether or not the cmdlet should return before it is complete. If specified, the command returns an identifier for the task that was created. You can monitor this task using the get-ProvTask cmdlet.                                                                                                                                                                                                                                                                                                                        | false | false                 | false                                 |
| PurgeJobOnSuccess      | Indicates that the task history will be removed from the database once the task has finished. This cannot be specified for tasks that are run asynchronously.                                                                                                                                                                                                                                                                                                                                                                           | false | false                 | false                                 |
| DoNotStoreOldImage     | Specifies that the current image should not be added to the image history list for the provisioning scheme. This is useful when rolling back to a previous image.                                                                                                                                                                                                                                                                                                                                                                       | false | false                 |                                       |
| LoggingId              | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                                                                                                                                                                                                                                  | false | false                 |                                       |
| AdminAddress           | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### System.Guid  
When "RunAsynchronously" is specified, this identifier is returned to provide the task identifier.  
System.Management.Automation.PSCustomObject  
This object provides details of the task run and contains the following information:  
TaskId <guid>  
The identifier for the task that was performed.  
Active <boolean>  
Indicates whether the task is still processing or is complete.  
Host <string>  
The name of the host on which the task is running or was run.  
DateStarted <datetime>  
The date and time that the task was initiated.  
Type <Citrix.XDInterServiceTypes.JobType>  
The type of the task. For new provisioning scheme tasks this is always "NewProvisioningScheme".  
Metadata <Citrix.MachineCreation.Sdk.Metadata[]>  
The list of metadata stored against the task. For new tasks this will be empty until metadata is added.  
WorkflowStatus <System.Workflow.Runtime.WorkflowStatus>  
Indicates the status of the workflow that is being used to process the task.  
ProvisioningSchemeName <string>  
The name of the provisioning scheme that the task was for.  
ProvisioningSchemeUid <guid>  
The unique identifier of the provisioning scheme that the task was for.  
MasterImage <string>  
The path (in the hosting unit provider) of the virtual machine snapshot or VM template that was used as the master image for the task.  
IdentityPoolName <string>  
The name of the identity pool (from the ADIdentity PowerShell snap-in) that the new provisioning scheme will use.  
IdentityPoolUid <guid>  
The unique identifier name of the identity pool (from the ADIdentity PowerShell snap-in) that the new provisioning scheme will use.  
HostingUnitName <string>  
The name of the hosting unit (from the Hosting Unit PowerShell snap-in) that the new provisioning scheme will use.  
HostingUnitUid  
The unique identifier of the hosting unit (from the Hosting Unit PowerShell snap-in) that the new provisioning scheme will use.  
TaskState <Citrix.DesktopUpdateManager.SDK.NewProvisioningSchemeState>  
The state of the task. This can be any of the following:  
Processing  
Indicates that the task has just begun and has not done anything yet.  
LocatingResources,  
Indicates that the workflow is locating resources from other services.  
HostingUnitNotFound  
Indicates that the task failed because the required hosting unit could not be located.  
VirtualMachineSnapshotNotFound  
Indicates that the task failed because the required snapshot or VM template could not be located.  
ConsolidatingMasterImage  
Indicates that the task is consolidating the master image.  
ReplicatingConsolidatedImageToAllStorage  
Indicates that the task is replicating the consolidated master image.  
StoringProvisioningScheme  
Indicates that the task is storing the provisioning scheme data to the database.  
Finished  
Indicates that the task has completed with no errors.  
ProvisioningSchemeAlreadyExists  
Indicates that the task failed because a provisioning scheme with the same name already exists.  
IdentityPoolNotFound  
Indicates that the task failed because the identity pool specified could not be found.  
MasterVMImageIsNotPartOfProvisioningSchemeHostingUnit,  
Indicates that the hosting unit that the master image originated from is not the same hosting unit that the provisioning scheme is defined to use.  
MasterVmImageIsNotASnapshot  
Indicates that the task failed because the master VM image path does not refer to a snapshot or a VM template item.  
ProvisioningSchemeNotFound  
Could not find a provisioning scheme with the specified name.  
TaskAlreadyRunningForProvisioningScheme  
A task for a provisioning scheme with the same name is already running.  
InvalidMasterVMConfiguration  
The VM snapshot or VM template specified as the master had an invalid configuration.  
InvalidMasterVMState  
The VM snapshot or VM template specified as the master is currently in an invalid state.  
InsufficientResources  
Indicates that the task failed because the hypervisor did not have enough resources to complete the task.  
StorageNotFound  
Indicates that no associated storage was found in the hosting unit.  
Canceled  
Indicates that the task was stopped by user intervention (using Stop-ProvTask).  
TaskStateInformation <string>  
Holds string data providing more details about the current task state.  
TaskProgress  
The progress of the task 0-100%.

## Notes Only one long-running task per provisioning scheme can be processed at any one time.  
In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
JobCreationFailed  
The requested task could not be started.  
DatabaseError  
An error occurred in the service while attempting a database operation.  
DatabaseNotConfigured  
The operation could not be completed because the database for the service is not configured.  
ServiceStatusInvalidDb  
An error occurred in the service while attempting a database operation - communication with the database failed for  
for various reasons.  
WorkflowHostUnavailable  
The task could not be started because the database connection is inactive.  
CommunicationError  
An error occurred while communicating with the service.  
PermissionDenied  
The user does not have administrative rights to perform this operation.  
ConfigurationLoggingError  
The operation could not be performed because of a configuration logging error.  
ExceptionThrown  
An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.  
The cmdlet is associated with a task of type PublishImage, and while active will move through the following operations (CurrentOperation field)  
ValidatingInputs  
ConsolidatingMasterImage  
PreparingMasterImage  
ReplicatingMasterImage  
CommittingScheme

## Examples

### EXAMPLE 1

    c:\PS>Publish-ProvMasterVMImage -ProvisioningSchemeName MyScheme -MasterImageVM XDHyp:\H
    stingUnits\HostUnit1\RhoneCC_baseXP.vm\base.snapshot
    
    TaskId                 : 248f102f-073f-45fe-aea9-1819a6d6dd1f
    Active                 : False
    Host                   : MyHost
    DateStarted            : 17/05/2010 17:37:57
    Type                   : PublishImage
    Metadata               : {}
    WorkflowStatus         : Completed
    ProvisioningSchemeUid  : 7585f0de-192e-4847-a6d8-22713c3a2f42
    ProvisioningSchemeName : MyScheme
    MasterImage            : /RhoneCC_baseXP.vm/base.snapshot
    HostingUnitName        : HostUnit1
    HostingUnitUid         : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501
    ADIdentityPoolName     :
    ADIdentityPoolUid      : 03743136-e43b-4a87-af74-ab71686b3c16
    CurrentOperation       :
    TaskState              : Finished
    TaskStateInformation   :
    

Description  
\---\---\-----  
Updates the master hard disk image for the provisioning Scheme "MyScheme" to use the "base.snapshot" hard disk image.