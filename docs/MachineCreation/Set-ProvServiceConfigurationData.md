# Set-ProvServiceConfigurationData

Sets the value for the given key in the service configuration data.

## 语法

    Set-ProvServiceConfigurationData [-Name] <String> -Value <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Provides the ability for additional custom data to be stored for the MachineCreation Service.

## 相关命令

- [Remove-ProvServiceConfigurationData](Remove-ProvServiceConfigurationData.html)
- [Get-ProvServiceConfigurationData](Get-ProvServiceConfigurationData.html)

## 参数

| 名称           | 说明                                                                                                                                                                     | 是否必需？   | 管道输入  | 默认值                                   |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- | ----- | ------------------------------------- |
| 名称           | Specifies the key name of the metadata to be added. The key must be unique.  
The Name cannot contain any of the following characters \/;:#.*?=<>                     | []()""' | true  | false |                               |
| 值            | Specifies the value for the name. If the name already exists, its value is updated.                                                                                    | true    | false |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。 | false   | false |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                             | false   | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.MachineCreation.Sdk.ServiceConfigurationData

Set-ProvServiceConfigurationData returns an object containing the new definition of the configuration.  
名称 <string>  
Specifies the name for the item of data.  
值 <string>  
Specifies the value of the data.## Notes In the case of failure the following errors can be produced.  
错误代码  
\---\---\-----  
DatabaseError  
尝试执行数据库操作时，服务发生错误。  
DatabaseNotConfigured  
由于未配置用于服务的数据库，无法完成操作。  
DataStoreException  
尝试执行数据库操作时，服务发生错误 - 由于各种原因，无法与数据库通信。  
PermissionDenied  
您没有执行此命令的权限。  
AuthorizationError  
与 Citrix Delegated Administration Service 通信时出现问题。  
ConfigurationLoggingError  
The operation could not be performed because of a configuration logging error.  
CommunicationError  
与服务通信时发生错误。  
ExceptionThrown  
An unexpected error occurred. To locate more details see the Windows event logs on the controller being used, or examine the XenDesktop logs.

## 示例

### 示例 1

    C:\PS>Set-ProvServiceConfigurationData -Name "customProperty1" -Value "value2"
    
    Name                            Value
    --------                        -----
    customProperty1                 value2
    

Description  
\---\---\-----  
Set data with a name of 'customProperty1' and value of 'value2' to the service configuration.