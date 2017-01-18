# Set-AdminAdministratorMetadata

Adds or updates metadata on the given Administrator.

## 语法

    Set-AdminAdministratorMetadata -AdministratorSid <String> -Name <String> -Value <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-AdminAdministratorMetadata -AdministratorSid <String> -Map <PSObject> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-AdminAdministratorMetadata [-AdministratorName] <String> -Name <String> -Value <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-AdminAdministratorMetadata [-AdministratorName] <String> -Map <PSObject> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-AdminAdministratorMetadata [-InputObject] <Administrator[]> -Name <String> -Value <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Set-AdminAdministratorMetadata [-InputObject] <Administrator[]> -Map <PSObject> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Provides the ability for additional custom data to be stored against given Administrator objects.

## 相关命令

- [Remove-AdminAdministratorMetadata](Remove-AdminAdministratorMetadata.html)

## 参数

| 名称                | 说明                                                                                                                                                                                             | 是否必需？  | 管道输入                           | 默认值                                   |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ | ------------------------------ | ------------------------------------- |
| AdministratorName | Name of the Administrator                                                                                                                                                                      | true   | true (ByValue, ByPropertyName) |                                       |
| InputObject       | 元数据要添加到的对象。                                                                                                                                                                                    | true   | true (ByValue)                 |                                       |
| AdministratorSid  | Sid of the Administrator                                                                                                                                                                       | true   | true (ByPropertyName)          |                                       |
| 名称                | Specifies the property name of the metadata to be added. The property must be unique for the Administrator specified. The property cannot contain any of the following characters \/;:#.*?=<> | []()"' | true                           | false |                               |
| 值                 | 指定属性的值。                                                                                                                                                                                        | true   | false                          |                                       |
| Map               | 指定属性的（名称，值）对字典。 可以是哈希表（使用 @{"name1" = "val1"; "name2" = "val2"} 创建）或字符串字典（使用 new-object“System.Collections.Generic.Dictionary[String,String]”创建）。                                              | true   | true (ByValue)                 |                                       |
| LoggingId         | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                         | false  | false                          |                                       |
| AdminAddress      | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                                     | false  | false                          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### System.Collections.Generic.Dictionary[String,String]  
Set-AdminAdministratorMetadata returns a dictionary containing the new (name, value)-pairs.  
Key <string>  
Specifies the name of the property.  
Value <string>  
Specifies the value for the property.

## Notes If the command fails, the following errors can be returned.  
Error Codes  
\---\---\-----  
InvalidParameterCombination  
The cmdlet parameters are inconsistent.  
UnknownObject  
One of the specified objects was not found.  
DatabaseError  
An error occurred in the service while attempting a database operation.  
DatabaseNotConfigured  
The operation could not be completed because the database for the service is not configured.  
DataStoreException  
An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.  
PermissionDenied  
You do not have permission to execute this command.  
AuthorizationError  
There was a problem communicating with the Citrix Delegated Administration Service.  
ConfigurationLoggingError  
The operation could not be performed because of a configuration logging error.  
CommunicationError  
There was a problem communicating with the remote service.  
ExceptionThrown  
An unexpected error occurred. For more details, see the Windows event logs on the controller or the XenDesktop logs.

## Examples

### EXAMPLE 1

    c:\PS>Set-AdminAdministratorMetadata -AdministratorSid S-1-5-21-1505241163-3345470479-1241728991-1000 -Name property -Value value
    
              Key                                       Value
              ---                                       -----
              property                                  value
    

Description  
\---\---\-----  
Add metadata with a name of 'property' and a value of 'value' to the Administrator with the identifier 'S-1-5-21-1505241163-3345470479-1241728991-1000'.