# Add-HypMetadata

Adds metadata to a hypervisor connection or a hosting unit.

## 语法

    Add-HypMetadata [-LiteralPath] <String> [-Property] <String> [-Value] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Use this command to store additional custom data against a hosting unit or hypervisor connection. This data is not used by the Machine Creation Service, and is provided only for consumers of the services to store any data that may be required for their operations. The metadata is returned along with the hypervisor connection or hosting unit that it is assigned to.

## 相关命令

- [Remove-HypMetadata](Remove-HypMetadata.html)

## 参数

| 名称           | 说明                                                                                                                                                                                                                                                                                                                                                                             | 是否必需？   | 管道输入           | 默认值                                   |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------- | -------------- | ------------------------------------- |
| LiteralPath  | Specifies the path within a hosting unit provider to the hosting unit or hypervisor connection item to which to add the metadata. The path specified must be in one of the following formats: <drive>:\HostingUnits\<hostingunitname> 或者 <drive>:\HostingUnits\{<hostingunit uid> 或者 <drive>:\Connections\<connection name> 或者 <drive>:\Connections\{<connection uid>} | true    | true (ByValue) |                                       |
| 属性           | Specifies the property name of the metadata to be added. The property must be unique for the item specified by the path.  
The property cannot contain any of the following characters \/;:#.*?=<>                                                                                                                                                                            | []()""' | true           | false |                               |
| 值            | 指定属性的值。                                                                                                                                                                                                                                                                                                                                                                        | true    | false          |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                                                                                                                                                                         | false   | false          |                                       |
| AdminAddress | Specifies the address of a XenDesktop controller to which the PowerShell snap-in connects. You can provide this as a host name or an IP address.                                                                                                                                                                                                                               | false   | false          | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### System.string  
You can pipe a string the contains a path to Add-HypMetadata (Path parameter).

## 返回值

### Citrix.Host.Sdk.Metadata  
Add-HypMetadata returns an object containing the new definition of the metadata.  
Property <string>  
Specifies the property of the metadata.  
Value <string>  
Specifies the value of the metadata.

## Notes In the case of failure, the following errors can result.  
Error Codes  
\---\---\-----  
InvalidPath  
The path provided is not in the required format.  
HostingUnitMetadataForeignKeyObjectDoesNotExist  
The hosting unit supplied in the path does not exist.  
HypervisorConnectionMetadataForeignKeyObjectDoesNotExist  
The hypervisor connection supplied in the path does not exist.  
HostingUnitMetadataDuplicateObjectExists  
Metadata for the specified hosting unit item already exists with the same property name.  
HypervisorConnectionMetadataDuplicateObjectExists  
Metadata for the specified hypervisor connection item already exists with the same property name.  
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
An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.

## Examples

### EXAMPLE 1

    c:\PS>Add-HypMetadata -LiteralPath XDHyp:\Connections\MyConnection -Property MyProperty -Value MyValue
    
    Property                                                    Value
    --------                                                    -----
    MyProperty                                                  MyValue
    

Description  
\---\---\-----  
The command adds the metadata with the property name of "MyProperty" and value of "MyValue" to the hypervisor connection item called "MyConnection".

### EXAMPLE 2

    c:\PS>dir xdhyp\connections\Citrix* | Add-HypMetadata -Property MyProperty -Value MyValue
    
    Property                                                    Value
    --------                                                    -----
    MyProperty                                                  MyValue
    MyProperty                                                  MyValue
    MyProperty                                                  MyValue
    

Description  
\---\---\-----  
The command adds the metadata with the property name of "MyProperty" and value of "MyValue" to all the hypervisor connection items that begin with the string "Citrix".