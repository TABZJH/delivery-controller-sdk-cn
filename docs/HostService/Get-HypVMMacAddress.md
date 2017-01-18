# Get-HypVMMacAddress

Retrieves a list the MAC addresses for the VMs in the specified connection.

## 语法

    Get-HypVMMacAddress [-LiteralPath] <String> [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Use this command to obtain a list of MAC addresses of all the virtual machines in the specified connection.

## 相关命令

- [Get-Item](Get-Item.html)

## 参数

| 名称           | 说明                                                                                                                                                                                                                                                                     | 是否必需？ | 管道输入           | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------- |
| LiteralPath  | The path to a connection item in the hosting provider. Paths to anything other than a connection item will result in an error being returned. The path can be provided as either <drive>:\connections\<connection name> 或者 <drive:>\connections\{<connection uid>} | true  | true (ByValue) |                                       |
| AdminAddress | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                                                                                                              | false | false          | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### System.string  
You can pipe a string that contains a path to Get-HypConfigurationDataForItem

## 返回值

### Citrix.Host.Sdk.HypervisorVMObject  
Get-HypVMMMacAddress returns an object containing the following properties.  
MacAddress <string> - specifies the MAC address of the VM.  
VMId <string> - specifies the identifier for the VM as defined in the hypervisor hosting it.

## Notes The path must refer to a connection item. Hosting unit items are not valid.  
In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
InputConnectionsPathInvalid  
If the path is not provided in an expected format, an InputConnectionsPathInvalid error results.  
HypervisorConnectionObjectNotFound  
The hypervisor connection object specified cannot be found.  
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

## Examples

### EXAMPLE 1

    C:\PS>Get-HypVMMacAddress -LiteralPath XDHyp:\Connections\MyConnection
    
    MacAddress                              VMId
    ----------                              ----
    52:b0:1c:ed:60:fa                       f3395d2a-a196-41c2-e37d-764acf871599
    62:6f:f0:40:d5:af                       5f4457b0-cc3c-f806-8ca7-5f57e4bdf2d1
    4e:a5:9f:00:b2:0c                       3115177b-85a9-d8ee-d0f9-0c7437483c09
    

Description  
\---\---\-----  
This command gets the MAC addresses for the connection called "MyConnection".

### EXAMPLE 2

    XDHyp:\Connections\MyConnection>Get-HypVMMacAddress -Path .
    
    MacAddress                              VMId
    ----------                              ----
    52:b0:1c:ed:60:fa                       f3395d2a-a196-41c2-e37d-764acf871599
    62:6f:f0:40:d5:af                       5f4457b0-cc3c-f806-8ca7-5f57e4bdf2d1
    4e:a5:9f:00:b2:0c                       3115177b-85a9-d8ee-d0f9-0c7437483c09
    

Description  
\---\---\-----  
This command gets the MAC addresses for the connection at the current directory. The dot (.) represents the current location (not its contents).

### EXAMPLE 3

    C:\PS>Get-HypVMMacAddress -LiteralPath Xdhyp:\connections\"{268c66db-9b8c-47f6-9265-42326dbff006}"
    

Description  
\---\---\-----  
This command gets the MAC addresses for the connection that has a ConnectionUid of 268c66db-9b8c-47f6-9265-42326dbff006.