# Import-AppLibAppDisk

Imports an AppDisk into the Application library service

## 语法

    Import-AppLibAppDisk -HostingUnitName <String> -HypervisorDiskId <String> -AppDiskName <String> -PreparationMachine <String> [-Scope <String[]>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-AppDiskDescription <String>] [-SkipAppDnaAnalysis] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Import-AppLibAppDisk -HostingUnitUid <Guid> -HypervisorDiskId <String> -AppDiskName <String> -PreparationMachine <String> [-Scope <String[]>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-AppDiskDescription <String>] [-SkipAppDnaAnalysis] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Lets you import a separately created AppDisk to the Application library service.

## 相关命令

- [Get-AppLibTask](Get-AppLibTask.html)
- [Get-AppLibAppDisk](Get-AppLibAppDisk.html)
- [New-AppLibAppDisk](New-AppLibAppDisk.html)
- [Test-AppLibAppDiskNameAvailable](Test-AppLibAppDiskNameAvailable.html)

## 参数

| 名称                 | 说明                                                                                                                                                                                                              | 是否必需？ | 管道输入  | 默认值                                   |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| HypervisorDiskId   | The infrastructure UID (as returned by Get-HypConfigurationDataForItem) of the disk to import.                                                                                                                  | true  | false |                                       |
| AppDiskName        | AppDisk 的名称。                                                                                                                                                                                                    | true  | false |                                       |
| PreparationMachine | The SID of the machine to use as the preparation machine for this operation. The machine must be within a valid Machine Catalog.                                                                                | true  | false |                                       |
| HostingUnitName    | The name of the hosting unit used for the AppDisk.                                                                                                                                                              | true  | false |                                       |
| HostingUnitUid     | The identifier for the hosting unit used for the AppDisk.                                                                                                                                                       | true  | false |                                       |
| 作用域                | The administration scopes to be applied to the new AppDisk.                                                                                                                                                     | false | false |                                       |
| RunAsynchronously  | Indicates whether or not the command returns before it is complete. If specified, the command returns an identifier for the task that was created. This task can be monitored using the Get-AppLibTask command. | false | false | false                                 |
| PurgeJobOnSuccess  | Indicates that the task history is removed from the database when the task has finished. This can only be specified for tasks that are not run asynchronously.                                                  | false | false |                                       |
| AppDiskDescription | The description of the AppDisk.                                                                                                                                                                                 | false | false |                                       |
| SkipAppDnaAnalysis | Indicates that AppDNA analysis of the AppDisk should be skipped.                                                                                                                                                | false | false | false                                 |
| LoggingId          | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                          | false | false |                                       |
| AdminAddress       | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                                                      | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### System.Guid

When the RunAsynchronously identifier is specified, this GUID is returned and provides the task identifier### System.Management.Automation.PSCustomObject System.Management.Automation.PSCustomObject This object provides details of the task that was run and contains the following information:  
TaskId <guid> The identifier for the task that was performed. Active <boolean> Indicates whether the task is still processing or is complete. Host <string> The name of the host on which the task is running or was run. DateStarted <datetime> The date and time that the task was initiated. LastUpdateTime <datetime> The date and time of the last task status update DateFinished <datetime> The date and time that the task finished execution Metadata <Metadata[]> Associated key-value data TaskState <string> Where in its lifecycle the task is CurrentOperation <string> Operation specific phase of the overall "Running" task state. TerminatingError < Citrix.Fma.Sdk.ServiceCore.CommonCmdlets.TaskterminatingError> Diagnostic information in the case of a complete task failure ActiveElapsedTime <int> How many seconds of active execution the task has taken Type <string> The type of task. For this cmdlet's tasks, this is always ImportAppDisk. AppDiskName <string> The name of the AppDisk that the task was for. AppDiskUid <string> The identifier of the AppDisk that the task was for. Scopes <Citrix.Fma.Sdk.ServiceCoreScopeReference[]> The delegated administration scopes to which the AppDisk will belong. TaskStateInformation <string> Additional information about the current task state. TaskProgress <double> The progress of the task 0-100%. DiskLocalUid <guid> The identifier of the AppDisk lineage. DiskLocalVersion <guid> The identifier of the AppDisk within its lineage. RemoteTaskId <guid> The identifier of the associated disk management task on the Machine Creation Service HostingUnitName <string> The name of the associated hosting unit HostingUnitUid <guid> The indentifier of the associated hosting unit VirtualDiskId <guid> The identifier of the AppDisk stack DiskId <string> The hypervisor's identifier for the disk being imported RunAppDnaAnalysis <bool> Whether AppDNA analysis has been run ReservedMachineSid <string> Security identifier of the VM being used to perform the operation## Notes Only one long-running task for each AppDisk can be processed at a time.  
In case of failure, the following errors can result.  
错误代码  
\---\---\-----  
JobCreationFailed  
The requested task could not be started.  
DatabaseError  
尝试执行数据库操作时，服务发生错误。  
DatabaseNotConfigured  
由于未配置用于服务的数据库，无法完成操作。  
ServiceStatusInvalidDb  
An error occurred in the service while attempting a database operation. Communication with the database failed  
各种原因，无法与数据库通信。  
CommunicationError  
与服务通信时发生错误。  
InvalidParameterCombination  
Both PurgeJobOnSuccess and RunAsynchronously were specified. When running asynchronously, the cmdlet terminates before the job does, so it cannot clean up the completed job.  
PermissionDenied  
用户没有执行此操作的管理权限。  
ConfigurationLoggingError  
The operation could not be performed because of a configuration logging error.  
ScopeNotFound  
One or more of the scopes nominated for the imported AppDisk do not exist.  
ExceptionThrown  
An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.

## 示例

### 示例 1

    C:\PS> Import-AppLibAppDisk -AppDiskName MyImportedAppDisk -AppDiskDescription "Imports new applications"  -HostingUnitName XenHu -PreparationMachine S-1-5-21-2316621082-1546847349-2782505528-1165
    
              TaskId                              : 90e93b9d-a225-4701-ad50-fa1546af35ac
              AppDiskName                         : MyImportedAppDisk
              AppDiskUid                          : d9ba6487-05f8-48ad-a178-1794605e2b8e
              Active                              : False
              SkipAppDnaAnalysis                  : False
              DiskLocalUid                        : 7b4c01c4-72fa-4c80-913d-c6df785f4297
              DiskLocalVersion                    : 25118c6e-a737-4fb9-b4b3-121910a73160
              DateStarted                         : 17/11/2015 08:22:22
              LastUpdateTime                      : 17/11/2015 09:10:18
              DateFinished                        : 17/11/2015 09:10:18
              Type                                : ImportAppDisk
              Metadata                            : {}
              TaskState                           : Finished
              TaskStateInformation                :
              TaskProgress                        : 100
              TerminatingError                    :
              RemoteTaskId                        : d2127904-a149-4dce-ae82-f9671a53f6fd
              HostingUnitName                     : XenHU
              HostingUnitUid                      : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501
              Host                                : MyHost
              VirtualDiskId                       : 7ce3c9a5-2888-45ba-8629-398f9e4eba7d
              CurrentOperation                    :
              ActiveElapsedTime                   : 2786
              DiskId                              : AppDiskBase
              RunAppDnaAnalysis                   : True
              ReservedMachineSid                  : S-1-5-21-2316621082-1546847349-2782505528-1165
    

Description  
\---\---\-----  
Imports a new AppDisk with the name "MyImportedAppDisk" from the one labelled "AppDiskBase" using the hosting unit "XenHu" and the preparation machine "S-1-5-21-2316621082-1546847349-2782505528-1165".