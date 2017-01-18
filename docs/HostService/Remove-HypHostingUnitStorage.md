# Remove-HypHostingUnitStorage

Removes storage from a hosting unit.

## 语法

    Remove-HypHostingUnitStorage [-LiteralPath] <String> [-StoragePath <String>] [-StorageType <StorageType>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Use this command to remove storage locations from a hosting unit. This does not remove the storage from the hypervisor, only the reference to the storage for the Host Service. After removal, the storage is no longer used to store hard disks (when creating new virtual machines with the Machine Creation Service). The hard disks located already on the storage remain in place and virtual machines that have been created already continue to use the storage until they are removed from the deployment. Do not use this command if the connection for the hosting unit is in maintenance mode. If the storage location to be removed no longer exists on the hypervisor for the hosting unit, you must supply a fully qualified path to the storage location.

## 相关命令

- [Add-HypHostingUnitStorage](Add-HypHostingUnitStorage.html)
- [Set-HypHostingUnitStorage](Set-HypHostingUnitStorage.html)
- [New-Item](New-Item.html)
- [Add-HypMetadata](Add-HypMetadata.html)

## 参数

| 名称           | 说明                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | 是否必需？ | 管道输入           | 默认值                                   |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------- |
| LiteralPath  | Specifies the path to the hosting unit which defines the storage. The path must be in one of the following formats: <drive>:\HostingUnits\<hostingunitname> 或者 <drive>:\HostingUnits\{<hostingunit uid>}                                                                                                                                                                                                                                                            | true  | false          |                                       |
| StoragePath  | Specifies the path in the hosting unit provider of the storage to remove. If StoragePath is not specified, all storage is removed from the hosting unit. The path must be in one of the following formats: <drive>:\Connections\<connectionname>\MyStorage.storage or <drive>:\Connections\{<connection uid>}\MyStorage.storage or <drive>:\HostingUnits\<hostingunitname>\MyStorage.storage or <drive>:\HostingUnits\{<hostingunit uid>}\MyStorage.storage | false | true (ByValue) |                                       |
| StorageType  | Specifies the type of storage in StoragePath. Supported storage types are: OSStorage PersonalvDiskStorage TemporaryStorage                                                                                                                                                                                                                                                                                                                                              | false | false          | OSStorage                             |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                                                                                                                                                                  | false | false          |                                       |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to. This can be a host name or an IP address.                                                                                                                                                                                                                                                                                                                                     | false | false          | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### System.string  
You can pipe a string that contains a path to Remove-HypHostingUnitStorage (StoragePath parameter).

## 返回值

### Citrix.XDPowerShell.HostingUnit  
Remove-HypHostingUnitStorage returns an object containing the new definition of the hosting unit.  
HostingUnitUid <guid>  
Specifies the unique identifier for the hosting unit.  
HostingUnitName <string>  
Specifies the name of the hosting unit.  
HypervisorConnection <Citrix.XDPowerShell.HypervisorConnection>  
Specifies the connection that the hosting unit uses to access a hypervisor.  
RootId <string>  
Identifies, to the hypervisor, the root of the hosting unit.  
RootPath <string>  
The hosting unit provider path that represents the root of the hosting unit.  
Storage <Citrix.XDPowerShell.Storage[]>  
The list of storage items that the hosting unit can use.  
PersonalvDiskStorage <Citrix.XDPowerShell.Storage[]>  
The list of storage items that the hosting unit can use for storing personal data.  
VMTaggingEnabled <boolean>  
Specifies whether or not the metadata in the hypervisor can be used to store information about the XenDesktop Machine Creation Service.  
NetworkId <string>  
The hypervisor's internal identifier that represents the network specified for the hosting unit.  
NetworkPath <string>  
The hosting unit provider path to the network specified for the hosting unit.  
AdditionalStorage  
The list of additional storage items that the hosting unit can use.  
Metadata <Citrix.XDPowerShell.Metadata[]>  
A list of key value pairs that can store additional information about the hosting unit.

## Notes After storage is removed, it is the administrator's responsibility to maintain its contents. The Citrix XenDesktop Machine Creation Service does not attempt to clean up any data that is stored in the storage location.  
If all storage is removed from the hosting unit, other features of the Machine Creation Service stops functioning until some storage is added again.  
In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
HostingUnitsPathInvalid  
The path provided is not to an item in a subdirectory of a hosting unit item.  
HostingUnitStorageObjectToDeleteDoesNotExist  
The storage path specified is not part of the hosting unit.  
HypervisorInMaintenanceMode  
The hypervisor for the connection is in maintenance mode.  
DatabaseError  
An error occurred in the service while attempting a database operation.  
DatabaseNotConfigured  
The operation could not be completed because the database for the service is not configured.  
DataStoreException  
An error occurred in the service while attempting a database operation. Communication with the database failed for  
for various reasons.  
CommunicationError  
An error occurred while communicating with the service.  
PermissionDenied  
The user does not have administrative rights to perform this operation.  
ExceptionThrown  
An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.

## Examples

### EXAMPLE 1

    c:\PS>Remove-HypHostingUnitStorage -LiteralPath XDHyp:\HostingUnits\MyHostingUnit -StoragePath 'XDHyp:\HostingUnits\MyHostingUnits\newStorage.storage'
    

Description  
\---\---\-----  
The command removes the OS storage location called "newStorage.storage" from the hosting unit called "MyHostingUnit"

### EXAMPLE 2

    c:\PS>Get-ChildItem XDHYP:\HostingUnits\Host\*.storage | Remove-HypHostingUnitStorage XDHYP:\HostingUnits\Host1
    

Description  
\---\---\-----  
The command removes all OS storage from all hosting units called "Host1".

### EXAMPLE 3

    c:\PS>Get-ChildItem XDHYP:\HostingUnits\Host\*.storage | Remove-HypHostingUnitStorage -StorageType PersonalvDiskStorage
    

Description  
\---\---\-----  
The command removes all PersonalvDisk storage from all hosting units called "Host1".