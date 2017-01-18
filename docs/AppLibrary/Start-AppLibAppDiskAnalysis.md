# Start-AppLibAppDiskAnalysis

Starts an AppDNA analysis for an AppDisk

## 语法

    Start-AppLibAppDiskAnalysis [-AppDiskName] <String> [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Start-AppLibAppDiskAnalysis -AppDiskUid <Guid> [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

AppDNA will analyse the chosen AppDisk to check for any compatability issues.

## 相关命令

- [Get-AppLibTask](Get-AppLibTask.html)
- [Get-AppLibAppDisk](Get-AppLibAppDisk.html)
- [New-AppLibAppDisk](New-AppLibAppDisk.html)
- [Test-AppLibAppDiskNameAvailable](Test-AppLibAppDiskNameAvailable.html)

## 参数

| 名称                | 说明                                                                                                                                                                                                              | 是否必需？ | 管道输入                  | 默认值                                   |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| AppDiskName       | The name of the AppDisk to analyse                                                                                                                                                                              | true  | false                 |                                       |
| AppDiskUid        | The unique identifier of the App Disk to analyse                                                                                                                                                                | true  | true (ByPropertyName) |                                       |
| RunAsynchronously | Indicates whether or not the command returns before it is complete. If specified, the command returns an identifier for the task that was created. This task can be monitored using the Get-AppLibTask command. | false | false                 | false                                 |
| PurgeJobOnSuccess | Indicates that the task history is removed from the database when the task has finished. This can only be specified for tasks that are not run asynchronously.                                                  | false | false                 |                                       |
| LoggingId         | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                          | false | false                 |                                       |
| AdminAddress      | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                                                      | false | false                 | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### System.Guid

When the RunAsynchronously identifier is specified, this GUID is returned and provides the task identifier### System.Management.Automation.PSCustomObject System.Management.Automation.PSCustomObject This object provides details of the task that was run and contains the following information:  
TaskId <guid> The identifier for the task that was performed. Active <boolean> Indicates whether the task is still processing or is complete. Host <string> The name of the host on which the task is running or was run. DateStarted <datetime> The date and time that the task was initiated. LastUpdateTime <datetime> The date and time of the last task status update DateFinished <datetime> The date and time that the task finished execution Metadata <Metadata[]> Associated key-value data TaskState <string> Where in its lifecycle the task is CurrentOperation <string> Operation specific phase of the overall "Running" task state. TerminatingError < Citrix.Fma.Sdk.ServiceCore.CommonCmdlets.TaskterminatingError> Diagnostic information in the case of a complete task failure ActiveElapsedTime <int> How many seconds of active execution the task has taken Type <string> The type of task. For this cmdlet's tasks, this is always ImportAppDisk. AppDiskName <string> The name of the AppDisk that the task was for. AppDiskUid <string> The identifier of the AppDisk that the task was for. Scopes <Citrix.Fma.Sdk.ServiceCoreScopeReference[]> The delegated administration scopes to which the AppDisk will belong. TaskStateInformation <string> Additional information about the current task state. TaskProgress <double> The progress of the task 0-100%. DiskLocalUid <guid> The identifier of the AppDisk lineage. DiskLocalVersion <guid> The identifier of the AppDisk within its lineage. RemoteTaskId <guid> The identifier of the associated disk management task on the Machine Creation Service HostingUnitName <string> The name of the associated hosting unit HostingUnitUid <guid> The indentifier of the associated hosting unit VirtualDiskId <guid> The identifier of the AppDisk stack DiskId <string> The hypervisor's identifier for the disk being imported RunAppDnaAnalysis <bool> Whether AppDNA analysis has been run ReservedMachineSid <string> Security identifier of the VM being used to perform the operation## Notes Only one long-running task for each AppDisk can be processed at a time.  
In case of failure, the following errors can result.  
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
CommunicationError  
An error occurred while communicating with the service.  
InvalidParameterCombination  
Both PurgeJobOnSuccess and RunAsynchronously were specified. When running asynchronously, the cmdlet terminates before the job does, so it cannot clean up the completed job.  
PermissionDenied  
The user does not have administrative rights to perform this operation.  
ConfigurationLoggingError  
The operation could not be performed because of a configuration logging error.  
ScopeNotFound  
One or more of the scopes nominated for the imported AppDisk do not exist.  
ExceptionThrown  
An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.