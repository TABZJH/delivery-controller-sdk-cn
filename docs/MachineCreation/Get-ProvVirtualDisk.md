# Get-ProvVirtualDisk

Gets any Virtual Disks that are known to the Machine Creation Service.

## 语法

    Get-ProvVirtualDisk [-VirtualDiskId <Guid>] [-StorageId <Guid>] [-HostingUnitUid <Guid>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Provides the ability to obtain a list of the Virtual Disks that are known to the Machine Creation Service and their locations on the storage.

## 相关命令

- [Get-ProvVirtualDiskPendingOperation](Get-ProvVirtualDiskPendingOperation.html)

## 参数

| 名称                     | 说明                                                                            | 是否必需？ | 管道输入                  | 默认值                                                                                |
| ---------------------- | ----------------------------------------------------------------------------- | ----- | --------------------- | ---------------------------------------------------------------------------------- |
| VirtualDiskId          | The identifier for the virtual disk.                                          | false | true (ByPropertyName) |                                                                                    |
| StorageId              | The identifier for the storage location on which the virtual disk is located. | false | false                 |                                                                                    |
| HostingUnitUid         | The identifier for the hosting unit used for the provisioning scheme.         | false | true (ByPropertyName) |                                                                                    |
| ReturnTotalRecordCount | 请参阅 about_Prov_Filtering 了解详细信息。                                            | false | false                 | false                                                                              |
| MaxRecordCount         | 请参阅 about_Prov_Filtering 了解详细信息。                                            | false | false                 | false                                                                              |
| 跳过                     | 请参阅 about_Prov_Filtering 了解详细信息。                                            | false | false                 |                                                                                    |
| SortBy                 | 请参阅 about_Prov_Filtering 了解详细信息。                                            | false | false                 |                                                                                    |
| 过滤器                    | 请参阅 about_Prov_Filtering 了解详细信息。                                            | false | false                 |                                                                                    |
| AdminAddress           | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                     | false | false                 | localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## 输入类型

### 

## 返回值

### Citrix.MachineCreation.Sdk.VirtualDisk

The object has the following properties:  
VirtualDiskId <guid>  
The unique identifier for the virtual disk  
HostingUnitUid <guid>  
The unique identifier for the hosting unit  
VirtualDiskType <string>  
A value indicating the type of the virtual disk (e.g. AppDisk)  
VirtualDiskLocations <Citrix.MachineCreation.Sdk.VirtualDiskLocation>  
An array of objects, with each giving the location of the virtual disk on a storage location of the hosting unit  
AllowAutomaticReplication <bool>  
A value indicating whether the virtual disk will be replicated automatically to all storage locations defined within the hosting unit## Notes In the case of failure, the following errors can result.  
错误代码  
\---\---\-----  
PartialData  
只返回了一部分可用数据。  
CouldNotQueryDatabase  
未定义获取数据库所需的查询。  
PermissionDenied  
用户没有执行此操作的管理权限。  
ConfigurationLoggingError  
由于配置日志记录错误，无法执行操作  
CommunicationError  
与服务通信时发生错误。  
DatabaseNotConfigured  
由于未配置用于服务的数据库，无法完成操作。  
InvalidFilter  
无法为此 cmdlet 解释提供的过滤表达式。  
ExceptionThrown  
发生意外错误。要查找更多详细信息，请参阅使用的控制器上的 Windows 事件日志，或检查 XenDesktop 日志。

## 示例

### 示例 1

    PS C:\> Get-ProvVirtualDisk
    
              AllowAutomaticReplication : False
              HighPriority              : False
              HostingUnitUid            : e22036f7-1026-467e-a8af-fad81f8eddf8
              VirtualDiskId             : 51a55b3a-a713-4692-ae57-15aa0c050486
              VirtualDiskLocations      : {a0788335-c0d6-428c-8168-fad6bdb48010}
              VirtualDiskType           : ControlDisk
    
              AllowAutomaticReplication : True
              HighPriority              : False
              HostingUnitUid            : e22036f7-1026-467e-a8af-fad81f8eddf8
              VirtualDiskId             : 2677e07f-b53d-4b4b-afbb-94af6461b9b1
              VirtualDiskLocations      : {21cd1a35-a5b9-4c86-81f8-f90d0c76b352}
              VirtualDiskType           : AppDisk
    
              AllowAutomaticReplication : False
              HighPriority              : False
              HostingUnitUid            : 98636b1f-eab8-419f-80ce-8e41740bc251
              VirtualDiskId             : 1b213058-f33c-40bb-85e9-b4a3cc5cb1de
              VirtualDiskLocations      : {Version=2,LsiLogicScsi,-1,,[Shared] AppDisk-VirtualDiskId-1b213058-f33c-40bb-85e9-b4a3cc5cb1de/01 Jan 2016 00-01-02.9567Z.vmdk,resgroup-116,Vmfs}
              VirtualDiskType           : AppDisk
    

Description  
\---\---\-----  
Gets all virtual disks known to MCS.

### 示例 2

    PS C:\> Get-ProvVirtualDisk -HostingUnitUid e22036f7-1026-467e-a8af-fad81f8eddf8
    
              AllowAutomaticReplication : False
              HighPriority              : False
              HostingUnitUid            : e22036f7-1026-467e-a8af-fad81f8eddf8
              VirtualDiskId             : 51a55b3a-a713-4692-ae57-15aa0c050486
              VirtualDiskLocations      : {a0788335-c0d6-428c-8168-fad6bdb48010}
              VirtualDiskType           : ControlDisk
    
              AllowAutomaticReplication : True
              HighPriority              : False
              HostingUnitUid            : e22036f7-1026-467e-a8af-fad81f8eddf8
              VirtualDiskId             : 2677e07f-b53d-4b4b-afbb-94af6461b9b1
              VirtualDiskLocations      : {21cd1a35-a5b9-4c86-81f8-f90d0c76b352}
              VirtualDiskType           : AppDisk
    

Description  
\---\---\-----  
Gets all virtual disks associated with the given hosting unit.