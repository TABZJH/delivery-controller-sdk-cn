# Remove-HypHypervisorConnectionAddress

Removes addresses from the list of available connection addresses.

## 语法

    Remove-HypHypervisorConnectionAddress [-LiteralPath] <String> [-HypervisorAddress] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Use this command to remove addresses that can be used to connect to the hypervisor specified by the hypervisor connection. If all addresses are removed, the connection cannot be used until a valid address is added to the hypervisor connection.

## 相关命令

- [Add-HypHypervisorConnectionAddress](Add-HypHypervisorConnectionAddress.html)

## 参数

| 名称                | 说明                                                                                                                                                                                                                                                          | 是否必需？ | 管道输入           | 默认值                                   |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------- |
| LiteralPath       | Specifies the path within a Host Service provider to the hosting unit item to which to add the address. The path specified must be in one of the following formats: <drive>:\HostingUnits\<hostingunitname> 或者 <drive>:\HostingUnits\{HostingUnit Uid>} | true  | false          |                                       |
| HypervisorAddress | Specifies the address to be removed. If this parameter is not provided, all addresses are removed from the hypervisor connection.                                                                                                                           | true  | true (ByValue) |                                       |
| LoggingId         | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                      | false | false          |                                       |
| AdminAddress      | Specifies the address of a XenDesktop controller to which the PowerShell snap-in connects. You can provide this as a host name or an IP address.                                                                                                            | false | false          | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### System.string  
You can pipe a string that contains a path to Remove-HypHypervisorConnectionAddress (Path parameter).

## 返回值

### 

## Notes Changes to a hypervisor connection affect all entities that reference the connection. If all addresses are removed from the connection, any other entities that reference the hypervisor connection (e.g. hosting units) cannot make new connections to the hypervisor.  
In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
InputConnectionsPathInvalid  
The path provided is not to an item in a subdirectory of a hosting unit item.  
HypervisorConnectionAddressForeignKeyObjectDoesNotExist  
The hypervisor connection to which the address is to be added could not be located.  
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
An unexpected error occurred. 要查找更多详细信息，请参阅使用的控制器上的 Windows 事件日志，或检查 XenDesktop 日志。

## 示例

### 示例 1

    c:\PS>Remove-HypHypervisorConnectionAddress -LiteralPath XDHyp:\HostingUnits\MyHypervisorConnection -HypervisorAddress 'http:\\myserver.com'
    

Description  
\---\---\-----  
The command removes the address "http:\\myserver.com" from the hypervisor connection called "MyHypervisorConnection".

### 示例 2

    c:\PS>Get-Item –Path XDHYP:\Connections\* | Remove-HypHypervisorConnectionAddress
    

Description  
\---\---\-----  
The command removes all addresses from all the hypervisor connections currently defined.