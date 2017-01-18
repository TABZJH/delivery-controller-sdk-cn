# Get-ConfigServiceGroup

Gets the service groups that match the parameters supplied.

## 语法

    Get-ConfigServiceGroup [-ServiceGroupUid <Guid>] [-ServiceGroupName <String>] [-ServiceType <String>] [-Metadata <String>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Use this cmdlet to retrieve existing service groups that match the parameters supplied. If no parameters are supplied, all the service groups are returned.

## 相关命令

## 参数

| 名称                     | 说明                                                                                        | 是否必需？ | 管道输入  | 默认值                                   |
| ---------------------- | ----------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| ServiceGroupUid        | The unique identifier for the service group.                                              | false | false |                                       |
| ServiceGroupName       |                                                                                           | false | false |                                       |
| ServiceType            | The service type for the service group.                                                   | false | false |                                       |
| 元数据                    | 获取具有匹配的元数据条目的记录。  
比较的值由键名、冒号和值组成。 例如：-Metadata "abc:x*" 匹配具有键名为“abc”且值以字母“x”开头的元数据条目的记录。 | false | false |                                       |
| 属性                     | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                    | false | false |                                       |
| ReturnTotalRecordCount | See about_Config_Filtering for details.                                                 | false | false | false                                 |
| MaxRecordCount         | See about_Config_Filtering for details.                                                 | false | false | 250                                   |
| 跳过                     | See about_Config_Filtering for details.                                                 | false | false |                                       |
| SortBy                 | See about_Config_Filtering for details.                                                 | false | false |                                       |
| 过滤器                    | See about_Config_Filtering for details.                                                 | false | false |                                       |
| AdminAddress           | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                 | false | false | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.Configuration.Sdk.ServiceGroup  
This represents a service instance and has the following parameters;  
ServiceGroupUid <guid>  
The unique identifier for the service group.  
ServiceGroupName <string>  
The name of the service group.  
ServiceType <string>  
The type of the service group.  
Metadata <Citrix.Configuration.Sdk.Metadata[]>  
The metadata for the service group.

## Notes In the case of failure, the following errors can result.  
Error Codes \---\---\-----  
DatabaseNotConfigured The operation could not be completed because the database for the service is not configured. PartialData Only a subset of the available data was returned. CouldNotQuueryDatabase The Query required to get the database was not defined. CommunicationError An error occurred while communicating with the service. InvalidFilter A filtering expression was supplied that could not be interpreted for this cmdlet. ExceptionThrown An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.

## Examples

### EXAMPLE 1

    C:\>Get-ConfigServiceGroup
    

Description  
\---\---\-----  
Return all the service groups that are registered in the Configuration Service.

### EXAMPLE 2

    C:\>Get-ConfigRegisteredServiceInstance -ServiceType "config"
    

Description  
\---\---\-----  
Return all the service groups that are registered in the Configuration Service and are of type 'config' (i.e. the service groups for the Configuration Service).