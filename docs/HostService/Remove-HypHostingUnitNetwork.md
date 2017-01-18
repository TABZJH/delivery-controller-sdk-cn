# Remove-HypHostingUnitNetwork

Removes networks from a hosting unit.

## 语法

    Remove-HypHostingUnitNetwork [-LiteralPath] <String> [-NetworkPath] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Use this command to remove networks from a hosting unit. This does not remove the network from the hypervisor, only the reference to the network for the Host Service. After it is removed, the network is no longer available for associating with virtual NICs (when creating new virtual machines with the Machine Creation Service). Any virtual machines that have been created already continue to use the network until they are removed from the deployment. This command cannot be used if the connection for the hosting unit is in maintenance mode. If the network to be removed no longer exists on the hypervisor for the hosting unit, you must supply a fully qualified path to the network location.

## 相关命令

- [Add-HypHostingUnitNetwork](Add-HypHostingUnitNetwork.html)

## 参数

| 名称           | 说明                                                                                                                                                                                                                                                                 | 是否必需？ | 管道输入           | 默认值                                   |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----- | -------------- | ------------------------------------- |
| LiteralPath  |                                                                                                                                                                                                                                                                    | true  | false          |                                       |
| NetworkPath  | Specifies the path in the hosting unit provider of the network to remove. The path specified must be in one of the following formats: <drive>:\Connections\<hostingunitname>\MyNetwork.network or <drive>:\Connections\{<hostingunit uid>}\MyNetwork.network | true  | true (ByValue) |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                             | false | false          |                                       |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to. This can be a host name or an IP address.                                                                                                                                | false | false          | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### System.string  
You can pipe a string that contains a path to Remove-HypHostingUnitNetwork (Path parameter).

## 返回值

### 

## Notes In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
HostingUnitsPathInvalid  
The path provided is not to an item in a subdirectory of a hosting unit item.  
HostingUnitNetworkObjectToDeleteDoesNotExist  
The network path specified is not part of the hosting unit.  
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

## 示例

### 示例 1

    c:\PS>Remove-HypHostingUnitNetwork -LiteralPath XDHyp:\HostingUnits\MyHostingUnit -NetworkPath 'XDHyp:\HostingUnits\MyHostingUnits\newNetwork.network'
    

Description  
\---\---\-----  
The command removes the network called "newNetwork.network" from the hosting unit called "MyHostingUnit"