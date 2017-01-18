# Add-HypHypervisorConnectionAddress

Add a connection address to a hypervisor connection.

## 语法

    Add-HypHypervisorConnectionAddress [-LiteralPath] <String> [-HypervisorAddress] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Use this command to add addresses by which a hypervisor can be contacted. All addresses added to a single hypervisor connection are assumed to be equivalent (i.e. they all result in the ability to communicate with the same hypervisors). The hypervisor that the addresses reference is stored at the point of creation of the hypervisor connection. Once this is done, to be valid, all addresses must resolve to this hypervisor.

The addresses required are; XenServer - The address of the XenServer machines (must all reference the same XenServer pool). VMWare vSphere/ESX - The address of a vCenter Server. Microsoft SCVMM/Hyper-V - the address of an SCVMM server.

## 相关命令

- [Remove-HypHypervisorConnectionAddress](Remove-HypHypervisorConnectionAddress.html)
- [Get-HypXenServerAddress](Get-HypXenServerAddress.html)

## 参数

| 名称                | 说明                                                                                                                                                                                                                                                                                                    | 是否必需？ | 管道输入           | 默认值                                   |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------- |
| LiteralPath       | Specifies the path within a Host Service provider to the hypervisor connection item to which to add the address. The path specified must be in one of the following formats; <drive>:\Connections\<hypervisorconnectionname> 或者 <drive>:\Connections\{HypervisorConnection Uid>}                  | true  | false          |                                       |
| HypervisorAddress | Specifies the address to be used. The address will be validated and the hypervisor must be contactable at the address supplied.  
XenServer (ConnectionType = XenServer) The address being added must reference the same XenServer pool referenced by any existing addresses for the same connection. | true  | true (ByValue) |                                       |
| LoggingId         | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                | false | false          |                                       |
| AdminAddress      | Specifies the address of a XenDesktop controller to which the PowerShell snap-in connects. You can provide this as a host name or an IP address.                                                                                                                                                      | false | false          | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.Host.Sdk.HypervisorConnection  
Add-HypHypervisorConnectionAddress returns an object containing the new definition of the hypervisor connection.  
HypervisorConnectionUid <guid>  
Specifies the unique identifier for the hypervisor connection.  
HypervisorConnectionName <string>  
Specifies the name of the hypervisor connection.  
ConnectionType <Citrix.XDInterServiceTypes.ConnectionType>  
Specifies the connection type of the connection.  
XenServer - A Citrix XenServer hypervisor  
SCVMM - A Microsoft SCVMM/Hyper-V hypervisor  
vCenter - A VMWare vSphere/ESX hypervisor  
Custom - A 3rd party hypervisor  
HypervisorAddress <string[]>  
A list of addresses that can be used to communicate with the hypervisor.  
UserName <string>  
The user name that is used when connecting to the hypervisor.  
Persistent <boolean>  
Indicates whether the connection is stored in the database or is a temporary connection only with the same lifetime as the current Powershell session.  
PlugInId <string>  
The Citrix identifier for the Citrix Machine Management plug-in.  
Revision <guid>  
Identifier for the current version of the hypervisor connection. This value changes every time a property of the hypervisor connection is updated.  
SupportsPvsVMs <boolean>  
Indicates whether or not the connection can be used as part of a hosting unit and therefore used by the Citrix XenDesktop Machine Creation Service to create virtual machines. Only the built-in supported hypervisor connection types can be used for this (i.e. XenServer, SCVMM and vCenter).  
Metadata <Citrix.Host.Sdk.Metadata[]>  
A list of key value pairs that can store additional information relating to the hosting unit.

## Notes The address format must be valid for the hypervisor connection. The rules that are applied are as below: XenServer (HypervisorConnection Type = XenServer)  
http:\\<ip address>  
or http:\\<server name>  
or https:\\<server name>  
Note: To use multiple addresses to the same XenServer pool to provide failover functionality, all XenServers in the pool must have a shared block storage device. If the use of https connections and failover is required, the certificates on the servers must be trusted by all of the controllers (typically this means having a root certificate installed).  
Note: If XenServers are moved to new XenServer pools after being added to a hypervisor connection, unpredictable results can occur. Once a XenServer is assigned to a hypervisor connection, it must not be moved to a new XenServer pool.  
In the case of failure the following errors can result.  
Error Codes  
\---\---\-----  
InputConnectionsPathInvalid  
The path provided is not to an item in a sub directory of a hosting unit item.  
HypervisorConnectionAddressForeignKeyObjectDoesNotExist  
The hypervisor connection to which the address is to be added could not be located.  
ConnectionAddressInvalid  
The address could not be used to contact a hypervisor or the validation rules have not been met.  
HypervisorConnectionAddressDuplicateObjectExists  
The address specified is already part of the hypervisor connection.  
HypervisorInMaintenanceMode  
The hypervisor for the connection is in maintenance mode.  
DatabaseError  
An error occurred in the service while attempting a database operation.  
DatabaseNotConfigured  
The operation could not be completed because the database for the service is not configured.  
DataStoreException  
An error occurred in the service while attempting a database operation - communication with the database failed for  
various reasons.  
CommunicationError  
An error occurred while communicating with the service.  
PermissionDenied  
The user does not have administrative rights to perform this operation.  
ExceptionThrown  
An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.

## Examples

### EXAMPLE 1

    c:\PS>Add-HypHypervisorConnectionAddress -LiteralPath XDHyp:\Connections\MyConnection -HypervisorAddress http:\\myserver.com
    
    PSPath                   : Citrix.HostingUnitService.Admin.V1.0\Citrix.Hypervisor::XDHyp:\Connections\MyConnection 
    PSParentPath             : Citrix.HostingUnitService.Admin.V1.0\Citrix.Hypervisor::XDHyp:\Connections
    PSChildName              : MyConnection 
    PSDrive                  : XDHyp
    PSProvider               : Citrix.HostingUnitService.Admin.V1.0\Citrix.Hypervisor
    PSIsContainer            : True
    HypervisorConnectionUid  : 85581f42-c5da-4976-970c-ebc3448ea1e3
    HypervisorConnectionName : MyConnection 
    ConnectionType           : XenServer
    HypervisorAddress        : {http:\\myserver2.com,http:\\myserver.com}
    UserName                 : root
    Persistent               : False
    PluginId                 : XenFactory
    SupportsPvsVMs           : True
    Revision                 : 4c95c857-c54d-4f92-abef-0cce32c02502
    Metadata                 :
    

Description  
\---\---\-----  
Add the address 'http:\\myserver.com' to the hypervisor connection called "MyConnection".