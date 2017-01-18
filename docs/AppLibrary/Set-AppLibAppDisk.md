# Set-AppLibAppDisk

Changes the parameter values for an AppDisk.

## 语法

    Set-AppLibAppDisk [-AppDiskName] <String> [-Description <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-AppLibAppDisk -AppDiskUid <Guid> [-Description <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Provides the ability to update the parameters of an existing AppDisk.

This allows the following parameters to be updated:

Description of the AppDisk.

To change the name of the AppDisk see Rename-AppLibAppDisk.

## 相关命令

- [Get-AppLibAppDisk](Get-AppLibAppDisk.html)
- [Rename-AppLibAppDisk](Rename-AppLibAppDisk.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？ | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| AppDiskName  | The name of the AppDisk to be updated.                                                                                                                                 | true  | false |                                       |
| AppDiskUid   | The identifier of the AppDisk to be updated.                                                                                                                           | true  | false |                                       |
| 说明           | The description to apply; may be empty.                                                                                                                                | false | false |                                       |
| PassThru     | Returns the affected record. By default, this cmdlet does not generate any output.                                                                                     | false | false | False                                 |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false | false |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.AppLibrary.Sdk.AppDisk  
This object provides details of the AppDisk and contains the following information:  
AppDiskUid <guid>  
The unique identifier for the AppDisk.  
AppDiskName <string>  
The name of the AppDisk.  
Description <string>  
A description of the AppDisk.  
HostingUnitUid <guid>  
The unique identifier of the hosting unit (from the Hosting Unit PowerShell snap-in) that the scheme uses.  
HostingUnitName <string>  
The name of the hosting unit (from the Hosting Unit PowerShell snap-in) that the scheme uses.  
VirtualDiskID <datetime>  
The MCS disk identifier for the AppDisk.  
TaskId <guid>  
The identifier of any current task that is running for the AppDisk.  
DiskLocalUid <guid>  
The AppDNA identifier for the disk.  
DiskLocalVersion <guid>  
The AppDNA version specifier for the disk.  
Scopes <ScopeReference[]>  
The Delegated Administration scopes in which the AppDisk falls  
Task <Task<  
The state of any current task that is running for the AppDisk.  
State <appdiskstate>  
The overall lifecycle state of the AppDisk  
StateString <string>  
The overall lifecycle state of the AppDisk as a string  
AppDNAState <appdnastate>  
The AppDNA lifecycle state of the AppDisk  
AppDNAStateString <string>  
The AppDNA lifecycle state of the AppDisk as a string  
NewVersionCreationInProgress <bool>  
A value indicating whether a new version of this AppDisk is currently being created

## Notes In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
AppDiskNotFound  
The specified AppDisk could not be located.  
DatabaseError  
An error occurred in the service while attempting a database operation.  
DatabaseNotConfigured  
The operation could not be completed because the database for the service is not configured.  
ServiceStatusInvalidDb  
An error occurred in the service while attempting a database operation - communication with the database failed  
for various reasons.  
CommunicationError  
An error occurred while communicating with the service.  
PermissionDenied  
The user does not have administrative rights to perform this operation.  
ConfigurationLoggingError  
The operation could not be performed because of a configuration logging error  
ExceptionThrown  
An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.

## Examples

### EXAMPLE 1

    C:\PS> Set-AppLibAppDisk -AppDiskName MyDisk -Description "Experimental"
    

Description  
\---\---\-----  
Updates as AppDisk called "MyDisk" to have the description "Experimental".