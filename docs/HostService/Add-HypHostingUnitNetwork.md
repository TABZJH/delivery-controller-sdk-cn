# Add-HypHostingUnitNetwork

Makes additional hypervisor networks available for use in a HostingUnit.

## 语法

    Add-HypHostingUnitNetwork [-LiteralPath] <String> [-NetworkPath] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Use this command to extend the set of hypervisor networks that are made available through the HostingUnit to the Citrix Machine Creation Service. When new machines are created, their virtual NICs can be associated only with networks that are in this set. This command cannot be used if the connection for the hosting unit is in maintenance mode.

## 相关命令

- [New-Item](New-Item.html)
- [Add-HypMetadata](Add-HypMetadata.html)
- [remove-HypHostingUnitNetwork](remove-HypHostingUnitNetwork.html)

## 参数

| 名称           | 说明                                                                                                                                                                                                                                                                                                                                                                   | 是否必需？ | 管道输入           | 默认值                                  |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------ |
| LiteralPath  | Specifies the path to the hosting unit to which the network will be added. The path must be in one of the following formats: <drive>:\HostingUnits\<hostingunitname> 或者 <drive>:\HostingUnits\{<hostingunit uid>}                                                                                                                                                | true  | false          |                                      |
| NetworkPath  | Specifies the path to the network that will be added. The path must be in one of the following formats: <drive>:\Connections\<connectionname>\MyNetwork.network or <drive>:\Connections\{<connection uid>}\MyNetwork.network or <drive>:\HostingUnits\<hostingunitname>\MyNetwork.network or <drive>:\HostingUnits\{<hostingunit uid>}\MyNetwork.network | true  | true (ByValue) |                                      |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                                                               | false | false          |                                      |
| AdminAddress | Specifies the address of a XenDesktop controller to which the PowerShell snap-in connects. This can be a host name or an IP address.                                                                                                                                                                                                                                 | false | false          | LocalHost。有 cmdlet 提供了某个值后，此值将变为默认值。 |

## 输入类型

### System.string  
You can pipe a string that contains a path to Add-HypHostingUnitNetwork (NetworkPath parameter).

## 返回值

### Citrix.Host.Sdk.HostingUnit  
Add-HypHostingUnitNetwork returns an object containing the new definition of the hosting unit.  
HostingUnitUid <guid>  
Specifies the unique identifier for the hosting unit.  
HostingUnitName <string>  
Specifies the name of the hosting unit.  
HypervisorConnection <Citrix.Host.Sdk.HypervisorConnection>  
Specifies the connection that the hosting unit uses to access a hypervisor.  
RootId <string>  
Identifies, to the hypervisor, the root of the hosting unit.  
RootPath <string>  
The hosting unit provider path that represents the root of the hosting unit.  
Storage <Citrix.Host.Sdk.Storage[]>  
The list of storage items that the hosting unit can use.  
PersonalvDiskStorage <Citrix.XDPowerShell.Storage[]>  
The list of storage items that the hosting unit can use for storing personal data.  
VMTaggingEnabled <boolean>  
Specifies whether or not the metadata in the hypervisor can be used to store information about the XenDesktop Machine Creation Service.  
NetworkId <string>  
The hypervisor's internal identifier that represents the default network specified for the hosting unit.  
NetworkPath <string>  
The hosting unit provider path to the default network specified for the hosting unit.  
Metadata <Citrix.Host.Sdk.Metadata[]>  
A list of key value pairs that can store additional information about the hosting unit.  
PermittedNetworks <Citrix.Host.Sdk.Network[]>  
A full list of the hypervisor networks that are exposed for use in the hosting unit.

## Notes The network path must be valid for the hosting unit. The rules that are applied are as follows: XenServer (HypervisorConnection Type = XenServer)  
NA  
VMWare vSphere/ESX (HypervisorConnection Type = vCenter)  
The network path must be directly contained in the root path item of the hosting unit.  
Microsoft SCVMM/Hyper-v (HypervisorConnection Type = SCVMM)  
NA  
In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
HostingUnitsPathInvalid  
The path provided is not to an item in a subdirectory of a hosting unit item.  
HostingUnitNetworkPathInvalid  
The specified path is invalid.  
HostingUnitNetworkPathInvalid  
The network path cannot be found or is invalid. See notes above about validity.  
HostingUnitNetworkDuplicateObjectExists  
The specified network path is already part of the hosting unit.  
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

    c:\PS>Add-HypHostingUnitNetwork -LiteralPath XDHyp:\HostingUnits\MyHostingUnit -NetworkPath 'XDHyp:\HostingUnits\MyHostingUnits\newNetwork.network'
    
              HostingUnitUid       : bcd3d649-86d1-4aa8-8ec2-d322b6a2c457
              HostingUnitName      : MyHostingUnit
              HypervisorConnection : MyConnection
              RootPath             : /
              RootId               :
              NetworkPath          : /Network 0.network
              NetworkId            : ab47080b-ca15-771a-c8dc-6ad9650158f1
              Storage              : {/Local storage.storage}
              PersonalvDiskStorage : {}
              VMTaggingEnabled     : True
              Metadata             : {}
              PermittedNetworks    : {/Network 0.network, /newNetwork.network}
    

Description  
\---\---\-----  
The command adds a new network called "newNetwork.network" to the hosting unit called "MyHostingUnit".

### EXAMPLE 2

    XDHyp:\HostingUnits\MyHostingUnit>Add-HypHostingUnitNetwork -LiteralPath . -NetworkPath 'XDHyp:\HostingUnits\MyHostingUnits\newNetwork.network'
    
              HostingUnitUid       : bcd3d649-86d1-4aa8-8ec2-d322b6a2c457
              HostingUnitName      : MyHostingUnit
              HypervisorConnection : MyConnection
              RootPath             : /
              RootId               :
              NetworkPath          : /Network 0.network
              NetworkId            : ab47080b-ca15-771a-c8dc-6ad9650158f1
              Storage              : {/Local storage.storage}
              PersonalvDiskStorage : {}
              VMTaggingEnabled     : True
              Metadata             : {}
              PermittedNetworks    : {/Network 0.network, /newNetwork.network}
    

Description  
\---\---\-----  
The command adds a new network called "newNetwork.network" to the current directory. The dot (.) represents the current location (not its contents).

### EXAMPLE 3

    XDHyp:\HostingUnits\MyHostingUnit>dir *.network | Add-HypHostingUnitNetwork -LiteralPath XDHyp:\HostingUnits\MyHostingUnit
    

Description  
\---\---\-----  
The command adds all of the networks that are available in the hosting unit to the specified hosting unit.

### EXAMPLE 4

    c:\PS>Add-HypHostingUnitNetwork -LiteralPath XDHyp:\HostingUnits\MyHostingUnit -NetworkPath 'XDHyp:\HostingUnits\MyHostingUnits\newNetwork.network'
    
              HostingUnitUid       : bcd3d649-86d1-4aa8-8ec2-d322b6a2c457
              HostingUnitName      : MyHostingUnit
              HypervisorConnection : MyConnection
              RootPath             : /
              RootId               :
              NetworkPath          : /Network 0.network
              NetworkId            : ab47080b-ca15-771a-c8dc-6ad9650158f1
              Storage              : {/Local storage.storage}
              PersonalvDiskStorage : {}
              VMTaggingEnabled     : True
              Metadata             : {}
              PermittedNetworks    : {/Network 0.network, /newNetwork.network}
    

Description  
\---\---\-----  
The command adds a new network location called "newNetwork.network" to the hosting unit called "MyHostingUnit".