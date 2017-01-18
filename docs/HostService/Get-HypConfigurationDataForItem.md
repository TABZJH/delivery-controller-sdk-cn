# Get-HypConfigurationDataForItem

Retrieves the configuration data for an item in the Host Service provider path. Note: For this release, only VM items are supported for this operation.

## 语法

    Get-HypConfigurationDataForItem [-LiteralPath] <String> [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

This command provides a mechanism for retrieving extra data about an entry in the hosting unit service provider. The referenced item must be contained within the connections directory in the provider (i.e. XDHyp:\Connections).

This mechanism is used for obtaining data that is not required frequently and/or has a high overhead associated with its retrieval (so as to maintain the responsiveness of the provider). For this release of the PowerShell snap-in, the only provider items that can be used with this operation are VM items. For a VM, this provides a mechanism to obtain the number of CPUs, the amount of Memory (in MB) and hard disk drive capacity (in GB).

## 相关命令

- [Get-Item](Get-Item.html)

## 参数

| 名称           | 说明                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | 是否必需？ | 管道输入           | 默认值                                   |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------- |
| LiteralPath  | Specifies the path within a hosting unit provider to the item for which configuration data is to be retrieved. The path specified must be in one of the following formats; <drive>:\Connections\<connection name>\<item path of vm object> 或者 <drive>:\Connections\{<connection uid>\<item path of vm object>} or <drive>:\HostingUnits\<hostingunit name>\<item path of vm object> 或者 <drive>:\HostingUnits\{<hostingunit uid>\<item path of vm object>} | true  | true (ByValue) |                                       |
| AdminAddress | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                                                                                                                                                                                                                                                                                                             | false | false          | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### System.string  
You can pipe a string that contains a path to Get-HypConfigurationDataForItem

## 返回值

### PSObject  
Get-HypConfigurationDataForItem returns a PSObject containing the properties that are appropriate for the item specified by the path.  
Properties for VM Item  
\---\---\---\---\---\---\----  
CPUCount <int>  
Specifies the number of CPUs assigned to the VM.  
MemoryMB <int>  
The amount of memory allocated to the VM.  
HardDiskSizeGB <int>  
The capacity of the primary hard drive assigned to the VM.

## Notes For this release, this cmdlet provides only configuration data for VM objects in the provider. Using a path to an item that is not a VM results in a error.  
In the case of failure the following errors can result.  
Error Codes  
\---\---\-----  
InputHypervisorItemPathInvalid  
The path provided is not to an item in a sub-directory of a connection item or a hosting unit item.  
InvalidHypervisorItemPath  
No item exists with the specified path.  
InvalidHypervisorItem  
The item specified by the path exists, but is not a VM Item.  
DatabaseError  
An error occurred in the service while attempting a database operation.  
DatabaseNotConfigured  
The operation could not be completed because the database for the service is not configured.  
DataStoreException  
An error occurred in the service while attempting a database operation - communication with the database failed for  
various reasons.  
CommunicationError  
An error occurred while communicating with the service.  
InvalidFilter  
A filtering expression was supplied that could not be interpreted for this cmdlet.  
HypervisorPermissionDenied  
The hypervisor login used does not provide authorization to access the data for this item.  
ExceptionThrown  
An unexpected error occurred. For more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.

## Examples

### EXAMPLE 1

    C:\PS>Get-HypConfigurationDataForItem -LiteralPath XDHyp:\Connections\MyConnection\MyVm.vm
    
                                  CpuCount                                MemoryMB                          HardDiskSizeGB
                                  --------                                --------                          --------------
                                         1                                    1024                                      24
    

Description  
\---\---\-----  
This command gets the configuration properties for a VM called 'MyVm.vm' within a hypervisor connection called 'MyConnection'.

### EXAMPLE 2

    XDHyp:\HostingUnits\PS>Get-HypConfigurationDataForItem -LiteralPath .\MyVm.vm
    
                                  CpuCount                                MemoryMB                          HardDiskSizeGB
                                  --------                                --------                          --------------
                                         1                                    1024                                      24
    

Description  
\---\---\-----  
This command gets the configuration properties for a VM called 'MyVm.vm' within the current directory. The dot (.) represents the current location (not its contents).

### EXAMPLE 3

    C:\PS>(Get-HypConfigurationDataForItem -LiteralPath XDHyp:\Connections\MyConnection\MyVm.vm).CPUCount
    

Description  
\---\---\-----  
This command gets the CPU count for a VM called 'MyVm.vm'. The CPUCount is just one property of the VM items. To see all properties of an item, type "(Get-HypConfigurationDataForItem <itempath>) | Get-Member".