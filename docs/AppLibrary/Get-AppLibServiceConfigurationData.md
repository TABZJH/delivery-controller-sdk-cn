# Get-AppLibServiceConfigurationData

Gets configuration data for the service.

## 语法

    Get-AppLibServiceConfigurationData [-Name <String[]>] [-Value <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Provides the ability to determine the configuration parameters for the service

## 相关命令

- [Set-AppLibServiceConfigurationData](Set-AppLibServiceConfigurationData.html)
- [Remove-AppLibServiceConfigurationData](Remove-AppLibServiceConfigurationData.html)

## 参数

| 名称                     | 说明                                                                                            | 是否必需？ | 管道输入  | 默认值                                   |
| ---------------------- | --------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| 名称                     | The Configuration data item Name .                                                            | false | false |                                       |
| 值                      | The Configuration data item value.                                                            | false | false |                                       |
| ReturnTotalRecordCount | 如果指定此项，cmdlet 将输出包含可用记录数的错误记录。 此错误记录是附加信息，并不影响写入输出管道的对象。 请参阅 about_AppLib_Filtering 了解详细信息。 | false | false | False                                 |
| MaxRecordCount         | 指定要返回的最大记录数。                                                                                  | false | false | 250                                   |
| 跳过                     | 在返回结果之前跳过指定的记录数。此外还降低由 -ReturnTotalRecordCount 返回的计数。                                         | false | false |                                       |
| SortBy                 | 按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 （可选） 在每个名称加前缀 + 或 - 来指示升序或降序排序。 如果没有前缀，则假设为升序排序。      | false | false | 默认排序顺序是按名称或唯一标识符。                     |
| 过滤器                    | 获取与 PowerShell 样式过滤表达式匹配的记录。请参阅 about_AppLib_Filtering 了解详细信息。                              | false | false |                                       |
| AdminAddress           | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                    | false | false | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.AppLibrary.Sdk.ServiceConfigurationData

This object provides details of the configuration data and contains the following information:  
名称 <string>  
The Name for the configuration item.  
值 <string>  
The value for the configuration item.## Notes In the case of failure the following errors can be produced.  
错误代码  
\---\---\-----  
UnknownObject  
未找到其中一个指定的对象。  
PartialData  
只返回了一部分可用数据。  
InvalidFilter  
无法为此 cmdlet 解释提供的过滤表达式。  
CouldNotQueryDatabase  
未定义获取数据库所需的查询。  
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
CommunicationError  
与服务通信时发生错误。  
ExceptionThrown  
An unexpected error occurred. To locate more details see the Windows event logs on the controller being used, or examine the XenDesktop logs.

## 示例

### 示例 1

    C:\PS>Get-AppLibConfiguratuionData
    
    Name                : DeltaDiskDelete.timeDelay
    Value               : 10
    

Description  
\---\---\-----  
Get the Configuration data for the service.