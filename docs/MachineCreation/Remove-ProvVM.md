# Remove-ProvVM

Removes virtual machines.

## 语法

    Remove-ProvVM [-ProvisioningSchemeName] <String> -VMName <String[]> [-ForgetVM] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Remove-ProvVM [-ProvisioningSchemeUid] <Guid> -VMName <String[]> [-ForgetVM] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Lets you remove VMs from the Machine Creation Services and the hypervisor that they run on.

## 相关命令

- [Get-ProvVM](Get-ProvVM.html)
- [New-ProvVM](New-ProvVM.html)

## 参数

| 名称                     | 说明                                                                                                                                                                                                                    | 是否必需？ | 管道输入                           | 默认值                                  |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ------------------------------ | ------------------------------------ |
| ProvisioningSchemeName | The name of the provisioning scheme from which virtual machines will be removed.                                                                                                                                      | true  | true (ByPropertyName)          |                                      |
| ProvisioningSchemeUid  | The unique identifier for the provisioning scheme from which the virtual machines are removed.                                                                                                                        | true  | true (ByPropertyName)          |                                      |
| VMName                 | List of VM names that will be removed from the provisioning scheme.                                                                                                                                                   | true  | true (ByValue, ByPropertyName) |                                      |
| ForgetVM               | The named VMs will only be removed from the provisioning scheme database, but will remain in the hypervisor.                                                                                                          | false | false                          |                                      |
| RunAsynchronously      | Indicates whether or not the command returns before it is complete. If this is specified, the command returns an identifier for the task that was created. This task can be monitored using the get-ProvTask command. | false | false                          | false                                |
| PurgeJobOnSuccess      | Indicates that the task history is removed from the database when the task finishes. This cannot be specified for tasks that are run asynchronously.                                                                  | false | false                          |                                      |
| LoggingId              | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                | false | false                          |                                      |
| AdminAddress           | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to. You can provide this as a host name or an IP address.                                                                       | false | false                          | LocalHost。有 cmdlet 提供了某个值后，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### System.Guid  
When the RunAsynchronously identifier is specified, this GUID is returned and provides the task identifier.  
System.Management.Automation.PSCustomObject  
This object provides details of the task that was run and contains the following information:  
TaskId <guid>  
The identifier for the task that was performed.  
Active <boolean>  
Indicates whether the task is still processing or is complete.  
Host <string>  
The name of the host on which the task is running or was run.  
DateStarted <datetime>  
The date and time that the task was initiated.  
Type <Citrix.XDInterServiceTypes.JobType>  
The type of task. For new remove-VM tasks, this is always "RemoveVirtualMachine".  
Metadata <Citrix.MachineCreation.Sdk.Metadata[]>  
The list of metadata stored for the task. For new tasks, this is empty until metadata is added.  
WorkflowStatus <System.Workflow.Runtime.WorkflowStatus>  
Indicates the status of the workflow that is used to process the task.  
ProvisioningSchemeName <string>  
The name of the provisioning scheme that the task is for.  
ProvisioningSchemeUid <guid>  
The unique identifier of the provisioning scheme that the task is for.  
TaskState <Citrix.DesktopUpdateManager.SDK.ProvisionVMState>  
The state of the task. This can be any of the following:  
Processing  
Indicates that the task is in its initial state.  
LocatingResources,  
Indicates that the task is locating information from other services.  
HostingUnitNotFound  
Indicates that the required hosting unit could not be located.  
ProvisioningSchemeNotFound  
Indicates that the required provisioning scheme could not be located.  
Provisioning  
Indicates that the task is at the provisioning stage.  
IdentityPoolNotFound  
Indicates that the required identity pool could not be located.  
TaskAlreadyRunningForProvisioningScheme  
Indicates that the provisioning scheme already has another task running.  
Finalizing  
Indicates that the task is finalizing.  
Finished  
Indicates that the task is complete.  
FinishedWithErrors  
Indicates that the task is complete but there were errors. Specific details of errors are included with each failed virtual machine.  
Removing  
Indicates that the task is removing virtual machines from the hypervisor.  
Failed  
Job failed for reasons specified in TaskStateInformation.  
Canceled  
Indicates that the task was stopped by user intervention (using Stop-ProvTask)  
TaskStateInformation  
Provides more detailed information about the current task state.  
VirtualMachinesToRemoveCount <int>  
The total number of virtual machines that the task is trying to remove.  
VirtualMachinesRemovedCount <int>  
The number of virtual machines that the task has removed so far. Details of the machines that have been removed are in the RemovedVirtualMachines parameter.  
VirtualMachinesFailedCount <int>  
The number of virtual machines that the task has failed to remove. Details of the machines that failed are in the FailedVirtualMachines parameter.  
FailedVirtualMachines <Citrix.DesktopUpdateManager.SDK.VirtualMachineCreation[]>  
ADAccountName <string>  
The domain-qualified AD Account name of the machine.  
ADAccountSid <string>  
The AD account SID of the machine account.  
DiagnosticInformation <Citrix.MachineCreation.Sdk.ExceptionSurrogate[]>  
A collection of handled error states which caused the provisioning to fail.  
ExceptionType <string>  
The type of exception this object represents  
Message <string>  
The exception message  
Details <string>  
The full exception content including stack trace  
InnerException <Citrix.MachineCreation.Sdk.ExceptionSurrogate>  
Information relating to any contributing error state  
Status <string>  
StatusAdditionalInformation <string>  
VMId <string>  
The virtual machine identifier in the hypervisor.  
VMName <string>  
The display name of the virtual machine in the hypervisor.  
RemovedVirtualMachines <Citrix.DesktopUpdateManager.SDK.VirtualMachineCreation[]>  
See FailedVirtualMachines for details of the object parameters.  
ProgressEstimator  
Gives an estimate of the number of virtual machines processed, averaging over virtual machines that were both partly and completely processed.

## Notes Only one long-running task for each provisioning scheme can be processed at a time.  
This task still operates if the hosting unit or VMs in the hypervisor are missing. This removes the data from the Citrix Machine Creation Services, but the VMs remain in the hypervisor.  
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
An error occurred in the service while attempting a database operation. Communication with the database failed for  
for various reasons.  
WorkflowHostUnavailable  
The task could not be started because the database connection is inactive.  
CommunicationError  
An error occurred while communicating with the service.  
InvalidParameterCombination  
Both PurgeJobOnSuccess and RunAsynchronously were specified. When running asynchronously, the cmdlet terminates before the job does, so it cannot clean up the completed job.  
PermissionDenied  
The user does not have administrative rights to perform this operation.  
ConfigurationLoggingError  
The operation could not be performed because of a configuration logging error  
ExceptionThrown  
An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.  
The cmdlet is associated with a task of type RemoveVirtualMachine, and while active will move through the following operations (CurrentOperation field)  
ValidatingInputs  
RemovingVirtualMachines

## Examples

### EXAMPLE 1

    c:\PS>,(Get-ProvVM -ProvisioningSchemeName XenPS) | Remove-ProvVM XenPS
    
    TaskId                       : cfb506a5-cc7e-4a49-ac7b-dd960029d0d3
    Active                       : False
    Host                         : DDC
    DateStarted                  : 10/10/2012 16:39:45
    Metadata                     : {}
    WorkflowStatus               : Completed
    ProvisioningSchemeUid        : e1afc8fb-3f52-42ea-9a17-305fdb0b6ee4
    ProvisioningSchemeName       : XenPS
    TaskState                    : Finished
    TaskStateInformation         :
    VirtualMachinesToRemoveCount : 2
    RemovedVirtualMachines       : {XD\IP0001$, XD\IP0002$}
    FailedVirtualMachines        : {}
    VirtualMachinesRemovedCount  : 2
    VirtualMachinesFailedCount   : 0
    ProgressEstimator            : 2
    Type                         : RemoveVirtualMachine
    Status                       : Finished
    CurrentOperation             :
    TaskProgress                 : 100
    TaskExpectedCompletion       : 10/10/2012 16:39:50
    LastUpdateTime               : 10/10/2012 16:39:50
    ActiveElapsedTime            : 5
    DateFinished                 : 10/10/2012 16:39:50
    TerminatingError             :
    

Description  
\---\---\-----  
Remove all VMs from provisioning scheme XenPS