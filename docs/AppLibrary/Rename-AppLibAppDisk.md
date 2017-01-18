# Rename-AppLibAppDisk

Renames a AppDisk.

## 语法

    Rename-AppLibAppDisk [-AppDiskName] <String> [-NewAppDiskName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Rename-AppLibAppDisk -AppDiskUid <Guid> [-NewAppDiskName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Provides the ability to change the name of an existing AppDisk. The unique identifier for the AppDisk never changes after it has been created so, regardless of any name changes, the AppDisk can always be identified by its unique identifier.

## 相关命令

- [New-AppLibAppDisk](New-AppLibAppDisk.html)
- [Set-AppLibAppDisk](Set-AppLibAppDisk.html)
- [Get-AppLibAppDisk](Get-AppLibAppDisk.html)
- [Test-AppLibAppDiskNameAvailable](Test-AppLibAppDiskNameAvailable.html)

## 参数

| 名称             | 说明                                                                                                                                                                     | 是否必需？   | 管道输入  | 默认值                                   |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- | ----- | ------------------------------------- |
| AppDiskName    | The current name of the AppDisk.                                                                                                                                       | true    | false |                                       |
| AppDiskUid     | The identifier for the AppDisk that is to be renamed.                                                                                                                  | true    | false |                                       |
| NewAppDiskName | The new name for the AppDisk. This must be a name that is not being used by an existing AppDisk, and it must not contain any of the following characters \/;:#.*?=<>  | []()""' | true  | false |                               |
| PassThru       | Defines whether or not the command returns a result showing the new state of the updated AppDisk.                                                                      | false   | false | true                                  |
| LoggingId      | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false   | false |                                       |
| AdminAddress   | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                              | false   | false | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

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
AppDiskNameAlreadyExists  
A AppDisk with the same name as the new AppDisk name already exists.  
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

    C:\PS>Rename-AppLibAppDisk -AppDiskName CurrentName -NewAppDiskName NewName
    

Description  
\---\---\-----  
Renames a AppDisk from "currentName" to "NewName".

### EXAMPLE 2

    C:\PS>Rename-AppLibAppDisk -AppDiskName CurrentName -NewAppDiskName NewName -PassThru
    
    
              AppDiskUid             : 7585f0de-192e-4847-a6d8-22713c3a2f42
              AppDiskName            : NewName
              Description                 : Microsoft Office 2013
              MasterStorageID             : 03743136-e43b-4a87-af74-ab71686b3c16
              MasterDiskID                : c0571690-4f57-4476-901b-fe64d6aecb79
              HostingUnitUid              : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501
              HostingUnitName             : HostUnit1
              TaskId                      : 00000000-0000-0000-0000-000000000000
              DiskLocalUid                : 4F8323D9-6978-4CA0-8231-22F9185C71B6
              DiskLocalVersion            : DDA81A28-6BF4-41E1-A120-67F72C164DF6
              Scopes                      :
    

Description  
\---\---\-----  
Renames a AppDisk from "currentName" to "NewName" and displays the resulting state.