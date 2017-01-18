# Register-ConfigServiceInstance

Allows the registration of a service instance.

## 语法

    Register-ConfigServiceInstance -ServiceGroupUid <Guid> -ServiceGroupName <String> -ServiceType <String> -Address <String> -Binding <String> -Version <Int32> -ServiceAccount <String> -InterfaceType <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Register-ConfigServiceInstance -ServiceGroupUid <Guid> -ServiceGroupName <String> -ServiceType <String> -Address <String> -Binding <String> -Version <Int32> -ServiceAccountSid <String> -InterfaceType <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Register-ConfigServiceInstance -ServiceInstance <ServiceInstance[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Use this cmdlet to register service instance items in the Configuration Service. Service instances can be registered either by retrieving the data directly from other services or by manually entering the details into this command.

If the service group specified by the service instance already exists, the service is added to the service group, otherwise a new service group is created to hold the service instance.

## 相关命令

- [Unregister-ConfigRegisteredServiceInstance](Unregister-ConfigRegisteredServiceInstance.html)
- [Add-ConfigRegisteredServiceInstanceMetadata](Add-ConfigRegisteredServiceInstanceMetadata.html)
- [Set-ConfigRegisteredServiceInstanceMetadata](Set-ConfigRegisteredServiceInstanceMetadata.html)
- [Remove-ConfigRegisteredServiceInstanceMetadata](Remove-ConfigRegisteredServiceInstanceMetadata.html)
- [Add-ConfigServiceGroupMetadata](Add-ConfigServiceGroupMetadata.html)
- [Set-ConfigServiceGroupMetadata](Set-ConfigServiceGroupMetadata.html)
- [Remove-ConfigServiceGroupMetadata](Remove-ConfigServiceGroupMetadata.html)

## 参数

| 名称                | 说明                                                                                                                                                 | 是否必需？ | 管道输入                  | 默认值                                   |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | --------------------- | ------------------------------------- |
| ServiceGroupUid   | The Service Group Unique Identifier                                                                                                                | true  | true (ByPropertyName) |                                       |
| ServiceGroupName  | The name of the service group                                                                                                                      | true  | true (ByPropertyName) |                                       |
| ServiceType       | The type of the service group                                                                                                                      | true  | true (ByPropertyName) |                                       |
| 地址                | The address that is used to access the service instance.                                                                                           | true  | true (ByPropertyName) |                                       |
| Binding           | The binding type that must be used to access the service instance.                                                                                 | true  | true (ByPropertyName) |                                       |
| 版本                | The version of the service instance.                                                                                                               | true  | true (ByPropertyName) |                                       |
| ServiceAccount    | The AD computer account name (domain qualified) for the computer on which the service instance is hosted.                                          | true  | true (ByPropertyName) |                                       |
| InterfaceType     | The type of interface that the service provides (i.e. SDK, InterService, Peer).                                                                    | true  | true (ByPropertyName) |                                       |
| ServiceAccountSid | The AD computer account Sid for the computer on which the service instance is hosted.                                                              | true  | true (ByPropertyName) |                                       |
| ServiceInstance   | The service instances to register.                                                                                                                 | true  | true (ByValue)        |                                       |
| LoggingId         | Specifies the logging id of the high-level operation that this cmdlet is part of.                                                                  | false | true (ByPropertyName) |                                       |
| AdminAddress      | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to. You can be provide this as a host name or an IP address. | false | false                 | LocalHost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### Citrix.Configuration.Sdk.ServiceInstance  
An object with the following parameters can be used to register a service instance.  
Address,  
ServiceGroupUid,  
ServiceGroupName,  
ServiceType,  
Binding,  
Version,  
InterfaceType.

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
Error Codes \---\---\----- ActiveDirectoryAccountResolutionFailed The account name provided could not be found in Active Directory. ServiceGroupWithSameUidExistsForDifferentServiceGroupNameOrSameUidExistsForDifferentServiceGroupNameOrServiceType The service group name or service type do not match the service group found with the specified uid. TypeAlreadyExists A different service group with the same type is registered already in the Configuration Service. DatabaseError An error occurred in the service while attempting a database operation. DatabaseNotConfigured The operation could not be completed because the database for the service is not configured. DataStoreException An error occurred in the service while attempting a database operation - communication with the database failed for various reasons. CommunicationError An error occurred while communicating with the service. ExceptionThrown An unexpected error occurred. For more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.

## Examples

### EXAMPLE 1

    C:\PS>Get-ConfigServiceInstance | Register-ConfigServiceInstance
    

Description  
\---\---\-----  
Gets the service instances for the Configuration Service and registers them.