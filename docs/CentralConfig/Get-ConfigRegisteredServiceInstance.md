# Get-ConfigRegisteredServiceInstance

Gets the service instances that are registered in the directory.

## 语法

    Get-ConfigRegisteredServiceInstance [-ServiceInstanceUid <Guid>] [-ServiceGroupUid <Guid>] [-ServiceGroupName <String>] [-ServiceType <String>] [-Address <String>] [-Binding <String>] [-Version <Int32>] [-ServiceAccountSid <String>] [-InterfaceType <String>] [-Metadata <String>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Use this cmdlet to retrieve the service instances currently registered with the Configuration Service that match the parameters supplied. If no parameters are supplied, all the service instances are returned.

## 相关命令

- [Register-ConfigServiceInstance](Register-ConfigServiceInstance.html)
- [Unregister-ConfigRegisteredServiceInstance](Unregister-ConfigRegisteredServiceInstance.html)
- [Set-ConfigRegisteredServiceInstance](Set-ConfigRegisteredServiceInstance.html)

## 参数

| 名称                     | 说明                                                                                                        | 是否必需？ | 管道输入  | 默认值                                   |
| ---------------------- | --------------------------------------------------------------------------------------------------------- | ----- | ----- | ------------------------------------- |
| ServiceInstanceUid     | The unique identifier for the service instance.                                                           | false | false |                                       |
| ServiceGroupUid        | The unique identifier for the service group to which the service instance belongs.                        | false | false |                                       |
| ServiceGroupName       | The name for the service group to which the service instance belongs.                                     | false | false |                                       |
| ServiceType            | The service type for the service instance.                                                                | false | false |                                       |
| 地址                     | The connection address for the service instance.                                                          | false | false |                                       |
| Binding                | The binding for the service instance.                                                                     | false | false |                                       |
| 版本                     | The service instance version.                                                                             | false | false |                                       |
| ServiceAccountSid      | The AD account SID for the computer account that the computer hosting the service instance is running as. | false | false |                                       |
| InterfaceType          | The interface type for the service instance.                                                              | false | false |                                       |
| 元数据                    | 获取具有匹配的元数据条目的记录。  
比较的值由键名、冒号和值组成。 例如：-Metadata "abc:x*" 匹配具有键名为“abc”且值以字母“x”开头的元数据条目的记录。                 | false | false |                                       |
| 属性                     | 指定要返回的属性。这类似于通过 Select-Object 以管道传送命令输出，但在服务器上过滤属性更有效。                                                    | false | false |                                       |
| ReturnTotalRecordCount | See about_Config_Filtering for details.                                                                 | false | false | false                                 |
| MaxRecordCount         | See about_Config_Filtering for details.                                                                 | false | false | 250                                   |
| 跳过                     | See about_Config_Filtering for details.                                                                 | false | false |                                       |
| SortBy                 | See about_Config_Filtering for details.                                                                 | false | false |                                       |
| 过滤器                    | See about_Config_Filtering for details.                                                                 | false | false |                                       |
| AdminAddress           | 指定 PowerShell 管理单元与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                 | false | false | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### 

## 返回值

### Citrix.Configuration.Sdk.ServiceInstance  
This represents a service instance and has the following parameters;  
ServiceGroupUid <guid>  
The unique identifier for the service group to which the service instance belongs.  
ServiceGroupName <string>  
The name of the service group to which the service instance belongs.  
ServiceInstanceUid <guid>  
The unique identifier for the service instance.  
ServiceType <string>  
The type of the service group.  
Address <string>  
The contact address for the service instance.  
Binding <string>  
The binding to use for connections to the service instance.  
Version <int>  
The version of the service instance.  
ServiceAccount <string>  
The AD computer account for the computer that is providing the service instance.  
ServiceAccountSid <string>  
The AD computer account SID for the computer that is providing the service instance.  
InterfaceType <string>  
The interface type for the service instance.  
Metadata <Citrix.Configuration.Sdk.Metadata[]>  
The metadata for the service instance.

## Notes In the case of failure, the following errors can result.  
Error Codes \---\---\----- PartialData Only a subset of the available data was returned. CouldNotQuueryDatabase The query required to get the database was not defined. CommunicationError An error occurred while communicating with the service. DatabaseNotConfigured The operation could not be completed because the database for the service is not configured. InvalidFilter A filtering expression was supplied that could not be interpreted for this cmdlet. ExceptionThrown An unexpected error occurred. To locate more details see the Windows event logs on the controller being used, or examine the XenDesktop logs.

## Examples

### EXAMPLE 1

    C:\>Get-ConfigRegisteredServiceInstance
    
    Address            : http://MyServer.com:80/Citrix/MyContract/v1
    Binding            : wcf_HTTP_kerb
    InterfaceType      : SDK
    Metadata           : {}
    MetadataMap        : {}
    ServiceAccount     : ENG\MyAccount$
    ServiceAccountSid  : S-1-5-21-1155438255-2213498043-2452000591-1104
    ServiceGroupName   : MyService
    ServiceGroupUid    : 2b990d5a-bba9-413b-aa08-e104e67f89bc
    ServiceInstanceUid : 8dc38b5a-3fbb-457c-b326-6c41c94c18d5
    ServiceType        : MySnapIn
    Version            : 1
    
    Address            : http://MyServer.com:80/Citrix/MyContract/PeerAPI/v1
    Binding            : wcf_HTTP_kerb
    InterfaceType      : Peer
    Metadata           : {}
    MetadataMap        : {}
    ServiceAccount     : ENG\MyAccount$
    ServiceAccountSid  : S-1-5-21-1155438255-2213498043-2452000591-1104
    ServiceGroupName   : MyService
    ServiceGroupUid    : 2b990d5a-bba9-413b-aa08-e104e67f89bc
    ServiceInstanceUid : 8f822ed6-42f3-4a26-911a-a4a6a87c0ef2
    ServiceType        : MySnapIn
    Version            : 1
    
    Address            : http://MyServer.com:80/Citrix/MyContract/MyServiceEnvTestAPI/v1
    Binding            : wcf_HTTP_kerb
    InterfaceType      : EnvironmentTest
    Metadata           : {}
    MetadataMap        : {}
    ServiceAccount     : ENG\MyAccount$
    ServiceAccountSid  : S-1-5-21-1155438255-2213498043-2452000591-1104
    ServiceGroupName   : MyService
    ServiceGroupUid    : 2b990d5a-bba9-413b-aa08-e104e67f89bc
    ServiceInstanceUid : d2d40d9b-2a5d-4c5a-b9ca-a7f73cffe4f2
    ServiceType        : MySnapIn
    Version            : 1
    
    Address            : http://MyServer.com:80/Citrix/MyContract/MyServiceAPI/v1
    Binding            : wcf_HTTP_kerb
    InterfaceType      : InterService
    Metadata           : {}
    MetadataMap        : {}
    ServiceAccount     : ENG\MyAccount$
    ServiceAccountSid  : S-1-5-21-1155438255-2213498043-2452000591-1104
    ServiceGroupName   : MyService
    ServiceGroupUid    : 2b990d5a-bba9-413b-aa08-e104e67f89bc
    ServiceInstanceUid : 5d428970-2ba1-4336-b8d0-f3aa961b8983
    ServiceType        : MySnapIn
    Version            : 1
    

Description  
\---\---\-----  
Return all the service instances that are registered in the Configuration Service.

### EXAMPLE 2

    C:\>Get-ConfigRegisteredServiceInstance -InterfaceType "SDK"
    
    Address            : http://MyServer.com:80/Citrix/MyContract/v1
    Binding            : wcf_HTTP_kerb
    InterfaceType      : SDK
    Metadata           : {}
    MetadataMap        : {}
    ServiceAccount     : ENG\MyAccount$
    ServiceAccountSid  : S-1-5-21-1155438255-2213498043-2452000591-1104
    ServiceGroupName   : MyService
    ServiceGroupUid    : 2b990d5a-bba9-413b-aa08-e104e67f89bc
    ServiceInstanceUid : 8dc38b5a-3fbb-457c-b326-6c41c94c18d5
    ServiceType        : MySnapIn
    Version            : 1
    

Description  
\---\---\-----  
Return all the service instances that are registered in the Configuration Service and are of type 'SDK'.