# Remove-HypMetadata

Removes metadata from a hypervisor connection or hosting unit.

## 语法

    Remove-HypMetadata [-LiteralPath] <String> [-Property <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Use this command to remove custom data from a specific hosting unit or hypervisor connection. If the Property parameter is not provided, all metadata is removed from the specified item.

## 相关命令

- [Remove-HypMetadata](Remove-HypMetadata.html)

## 参数

| 名称           | 说明                                                                                                                                                                                                                                                                                                                                                                                  | 是否必需？ | 管道输入           | 默认值                                   |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------- |
| LiteralPath  | Specifies the path within a Host Service provider to the hosting unit or hypervisor connection item from which to remove the metadata. The path specified must be in one of the following formats: <drive>:\HostingUnits\<hostingunitname> 或者 <drive>:\HostingUnits\{<hostingunit uid> 或者 <drive>:\Connections\<connection name> 或者 <drive>:\Connections\{<connection uid>} | true  | true (ByValue) |                                       |
| 属性           | Specifies the property name of the metadata to be removed.                                                                                                                                                                                                                                                                                                                          | false | false          |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                                                                              | false | false          |                                       |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in will connect to. This can be provided as a host name or an IP address.                                                                                                                                                                                                                                 | false | false          | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### System.string  
You can pipe a string that contains a path to Add-HypMetadata (Path parameter).

## 返回值

### 

## Notes In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
InvalidPath  
The path provided is not in the required format.  
HostingUnitMetadataObjectToDeleteDoesNotExist  
The hosting unit supplied in the path does not exist.  
HypervisorConnectionObjectToDeleteDoesNotExist  
The hypervisor connection supplied in the path does not exist.  
MetadataContainerUndefined  
The specified path does not reference a hosting unit or a hypervisor connection.  
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

    C:\PS>Remove-HypMetadata -LiteralPath XDHyp:\Connections\MyConnection -Property MyProperty
    

Description  
\---\---\-----  
The command removes the metadata with the property "MyProperty" from the hypervisor connection called "MyConnection".

### 示例 2

    C:\PS>Remove-HypMetadata -LiteralPath XDHyp:\Connections\MyConnection
    

Description  
\---\---\-----  
The command removes all the metadata from the hypervisor connection called "MyConnection".

### 示例 3

    C:\PS>dir XDHyp:\connections | Remove-HypMetadata
    

Description  
\---\---\-----  
The command removes all the metadata from all the hypervisor connections.