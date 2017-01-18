# Get-HypXenServerAddress

Gets all the available addresses for a XenServer hypervisor connection.

## 语法

    Get-HypXenServerAddress [-LiteralPath] <String> [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Use this cmdlet to retrieve all the available hypervisor connection addresses that can be used to connect to the same XenServer pool. When used in conjunction with Add-HypHypervisorAddress, you can easily populate a connection with all the addresses that can be used to provide full failover support for a XenServer connection.

If the addresses are https addresses, the command uses the certificates installed on the XenServers to provide suitable https addresses where possible. Only servers that can be resolved are returned.

## 相关命令

- [Add-HypHypervisorConnectionAddress](Add-HypHypervisorConnectionAddress.html)

## 参数

| 名称           | 说明                                                                                                                                                                                                                                                                                    | 是否必需？ | 管道输入           | 默认值                                   |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------- |
| LiteralPath  | Specifies the path within a Host Service provider to the hypervisor connection item to which to add the address. The path specified must be in one of the following formats: <drive>:\Connections\<hypervisorconnectionname> 或者 <drive>:\Connections\{HHypervisorConnection Uid>} | true  | true (ByValue) |                                       |
| AdminAddress | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                                                                                                                             | false | false          | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### System.string  
Get-HypXenServerAddress returns a list of strings containing the available address.

## Notes For this to work as required with https connections, the certificates installed on the XenServers must be trusted by all controllers. Typically this means having the root certificate for the certificate trust chain installed on all controllers. Wildcard certificates are not supported for this operation.  
In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
InputConnectionsPathInvalid  
The path provided is not to an item in a sub-directory of a hosting unit item.  
HypervisorConnectionNotXenServer  
The hypervisor connection to which the path refers is not for a Citrix XenServer hypervisor.  
HypervisorConnectionObjectNotFound  
The hypervisor connection at the path specified cannot be located.  
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
InvalidFilter  
A filtering expression was supplied that could not be interpreted for this cmdlet.  
ExceptionThrown  
An unexpected error occurred. For more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.

## 示例

### 示例 1

    c:\PS>Get-HypXenServerAddress -LiteralPath XDHyp:\Connections\MyConnection
    
    https:\\myserver.com
    https:\\myServer1.com
    

Description  
\---\---\-----  
Gets the available addresses for the connection "MyConnection".

### 示例 2

    c:\PS>Get-HypXenServerAddress -LiteralPath XDHyp:\Connections\MyConnection | Add-HypHypervisorConnectionAddress -LiteralPath XDHyp:\Connections\MyConnectionPath
    

Description  
\---\---\-----  
Adds all the available addresses for the XenServer pool in "MyConnection" to the hypervisor connection.